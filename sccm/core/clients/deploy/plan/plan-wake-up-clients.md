---
title: "Wznawianie klientów | Dokumentacja firmy Microsoft"
description: "Planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52ee82b2-0b91-4829-89df-80a6abc0e63a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 20f595a5b0634a627dff9ba6feeb848754615f2c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="plan-how-to-wake-up-clients-in-system-center-configuration-manager"></a>Planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Program Configuration Manager obsługuje dwa funkcji wake on technologii sieci lokalnej (LAN) do wznawiania działania komputerów w trybie uśpienia, gdy chcesz zainstalować wymaganego oprogramowania, takie jak aktualizacje oprogramowania i aplikacji: tradycyjnymi pakietami wznawiania i polecenia włączania zasilania AMT.  

Metoda tradycyjnych pakietów wznawiania można uzupełnić ustawieniami klienta serwera proxy wznawiania. Serwera proxy wznawiania używa protokołu do równorzędnego oraz wybranych komputerów, aby sprawdzić, czy inne komputery w podsieci są wznowione oraz wznowić je w razie potrzeby. Lokacja została skonfigurowana dla funkcji Wake On LAN i klientów są skonfigurowane dla serwera proxy wznawiania, proces odbywa się w następujący sposób:  

1.  Komputery z zainstalowanym klientem programu Configuration Manager i które nie są uśpione w podsieci, sprawdzają czy inne komputery w podsieci są wznowione. Robią to, wysyłając wzajemnie polecenie TCP/IP ping co 5 sekund.  

2.  Nie ma odpowiedzi z innymi komputerami, są uznane za uśpione. Komputery wznowione stają się *komputer zarządzający* podsieci.  

     Ponieważ istnieje możliwość, że komputer może nie odpowiadać z powodów innych niż jest w stanie uśpienia (na przykład jest wyłączony, odłączony od sieci lub ustawienie serwera proxy wznawiania klienta nie jest już stosowane), do komputerów będzie wysyłany pakiet wznawiania codziennie o godzinie 2: 00 czas lokalny. Nieodpowiadające komputery nie będą już uważane za uśpione i nie będą wznawiane przez serwer proxy wznawiania.  

     Do obsługi serwera proxy wznawiania, co najmniej trzech komputerach musi być wznowione dla każdej podsieci. Aby to osiągnąć, trzy komputery zostaną wybrane niejednoznaczne za *komputery stróżujące* podsieci. Oznacza to, że będą stale wznowione, niezależnie od ewentualnych skonfigurowanych zasad zasilania nakazujących uśpienie lub hibernację po okresie braku aktywności. Komputery stróżujące wykonują wyłączenia lub ponownego uruchomienia polecenia, na przykład w wyniku zadań konserwacji. W takim przypadku pozostałe komputery stróżujące wznawiania działania inny komputer w podsieci, dzięki czemu w podsieci zawsze będą trzy komputery stróżujące.  

3.  Komputery zarządzające nakazują przełącznikowi sieciowemu przekierowywanie ruchu sieciowego skierowanego do uśpionych komputerów do siebie.  

     Przekierowanie odbywa się przez komputer zarządzający przesyła ramkę Ethernet używającą adresu MAC uśpionego komputera jako adresu źródłowego. Dzięki temu zachowują się tak, jakby uśpiony komputer przeniósł się do portu zajmowanego przez komputer zarządzający na przełącznik sieci. Komputer zarządzający wysyła również ARP pakietów do uśpionych komputerów, aby zapewnić bieżące wpis w pamięci podręcznej ARP. Komputer zarządzający będzie także odpowiadał na żądania ARP w imieniu uśpionego komputera przy użyciu adresu MAC uśpionego komputera.  

    > [!WARNING]  
    >  W trakcie tego procesu mapowanie adresu IP do MAC dla tego komputera nie ulegnie zmianie. Serwer proxy wznawiania działa przełącznik sieci informuje, że do innej karty sieciowej używającej portu zarejestrowanego przez inną kartę sieciową. Jednak to zachowanie nazywane jest niestabilnością adresu MAC i nie jest typowe dla standardowego działania sieci. Niektóre narzędzia monitorowania sieci szukają oznak takiego działania i mogą zauważyć że wystąpił problem. W związku z tym tych narzędzi monitorowania może generować alerty lub wyłączać porty w przypadku użycia serwera proxy wznawiania.  
    >   
    >  Nie należy używać serwera proxy wznawiania, jeśli narzędzia i usługi monitorowania sieci nie zezwalają na niestabilności adresów MAC.  

4.  Gdy komputer zarządzający dostrzeże nowe żądanie połączenia TCP uśpionego komputera i żądania do portu, na którym uśpiony komputer prowadził nasłuchiwanie przed uśpieniem, komputer zarządzający wysyła pakiet wznawiania do tego komputera, a następnie wstrzyma przekierowywanie ruchu dla tego komputera.  

5.  Uśpiony komputer otrzyma pakiet wznawiania i wznowi się. Wysyłający komputer automatycznie ponowi próbę połączenia i ten czas komputer jest w stanie aktywności i mogą odpowiadać.  

 Serwer proxy wznawiania ma następujące wymagania wstępne i ograniczenia:  

> [!IMPORTANT]  
>  Jeśli infrastrukturą i usługami sieciowymi zajmuje się odrębny zespół, powiadomienia, a także włączyć prowadzonej ewaluacji i testowaniu. Na przykład w sieci, która używa 802.1 X kontroli dostępu do sieci, serwer proxy wznawiania nie będzie działać i może zakłócać funkcjonowanie sieci. Ponadto serwer proxy wznawiania może powodować niektóre narzędzia do generowania alertów w sytuacji wykrycia ruch do innych komputerów wznawiania monitorowania sieci.  

-   Obsługiwani klienci są systemu Windows 7, Windows 8, Windows Server 2008 R2, Windows Server 2012.  

-   Systemy operacyjne gościa na maszynie wirtualnej nie są obsługiwane.  

-   Klienci musi być włączona dla serwera proxy wznawiania przy użyciu ustawień klienta. Działanie serwera proxy wznawiania nie jest uzależnione od spisu sprzętu, klienty nie zgłaszają zainstalowania usługi serwera proxy wznawiania, chyba że są one włączone spisu sprzętu i przesłały przynajmniej jednego takiego spisu.  

-   Sieć kart (i ewentualnie systemu BIOS) musi być włączona i skonfigurowana dla pakietów wznawiania. Jeśli karta sieciowa nie została skonfigurowana dla pakietów wznawiania lub to ustawienie jest wyłączone, Configuration Manager automatycznie skonfigurować i włączyć dla komputera, po odebraniu ustawienia, aby włączyć serwer proxy wznawiania klienta.  

-   Jeśli komputer ma więcej niż jedną kartę sieciową, która karta będzie używana dla serwera proxy wznawiania; nie można skonfigurować Wybór jest deterministyczna. Wybrana karta zostanie jednak zapisana w SleepAgent_ < domena\> @SYSTEM_0.log pliku.  

-   Sieć musi zezwalać na żądania echa protokołu ICMP (przynajmniej w obrębie podsieci). Nie można skonfigurować 5-sekundowego interwału, który służy do wysyłania ICMP poleceń ping.  

-   Komunikacja będzie przebiegała bez szyfrowania i uwierzytelniania, a protokół IPsec nie jest obsługiwany.  

-   Następujące konfiguracje sieciowe nie są obsługiwane:  

    -   Standard 802.1 X z funkcją uwierzytelniania portu  

    -   Sieci bezprzewodowe  

    -   Przełączniki sieciowe wiążące adresy MAC z określonymi portami  

    -   Sieci obsługujące wyłącznie protokół IPv6  

    -   Dzierżawy DHCP wygasające przed upływem 24 godzin  

Jeśli chcesz wznawiania zaplanowaną instalacją oprogramowania na komputerach, należy skonfigurować każdej lokacji głównej pakietów wznawiania.  

 Aby użyć serwera proxy wznawiania, należy wdrożyć ustawienia klienta serwera proxy wznawiania zarządzania energią oprócz skonfigurowania lokacji głównej.  

Należy również postanowić, czy używać pakietów emisji skierowanych do podsieci lub pakietów emisji pojedynczej oraz jakiego numeru portu UDP. Domyślnie tradycyjne pakiety wznawiania są przesyłane przy użyciu portu 9 UDP, jednak aby zwiększyć poziom zabezpieczeń, można wybrać alternatywny port dla lokacji, jeśli to jest on obsługiwany przez pośredniczące routery i zapory.  

### <a name="choose-between-unicast-and-subnet-directed-broadcast-for-wake-on-lan"></a>Wybierz między emisją pojedynczą a emisją kierowaną do podsieci dla funkcji Wake-on-LAN  
 W przypadku wybrania wznawiania komputerów przy użyciu tradycyjnych pakietów wznawiania, należy określić, czy do przekazywania pakietów emisji pojedynczej lub podsieci bezpośrednio pakietów emisji. Jeśli używasz serwera proxy wznawiania, należy wybrać opcję pakietów emisji pojedynczej. W przeciwnym razie skorzystaj z poniższej tabeli w celu określenia, którą metodę transmisji należy wybrać.  

|Metoda transmisji|Zalety|Wadą|  
|-------------------------|---------------|------------------|  
|Emisji pojedynczej|Wyższy poziom bezpieczeństwa niż emisje skierowane do podsieci, ponieważ pakiet jest wysyłany bezpośrednio do komputera zamiast do wszystkich komputerów w podsieci.<br /><br /> Może nie wymagać ponownego skonfigurowania routerów (może wystąpić konieczność skonfigurowania pamięci podręcznej ARP).<br /><br /> Powoduje mniejsze obciążenie przepustowości sieci niż transmisje skierowane do podsieci.<br /><br /> Obsługiwana za pomocą protokołów IPv4 i IPv6.|Pakiety wznawiania nie znaleźć komputerów docelowych, których adres podsieci ulegnie zmianie po ostatnim spisu sprzętu.<br /><br /> Przełączniki może wystąpić konieczność skonfigurowania do przekazywania pakietów UDP.<br /><br /> Niektóre karty sieciowe mogą nie reagować na wznawiania pakietów w trybie uśpienia wszystkie stany podczas używania emisji pojedynczej jako metody transmisji.|  
|Emisja skierowana do podsieci|Wyższy poziom skuteczności w porównaniu z emisją pojedynczą, jeśli komputery, które zmieniają się często adresy IP w tej samej podsieci.<br /><br /> Nie przełącznika jest wymagane ponowne skonfigurowanie.<br /><br /> Wysoki poziom zgodności z kartami sieciowymi we wszystkich stanach uśpienia, ponieważ emisje skierowane do podsieci stanowiły oryginalną metodę transmisji pakietów wznawiania.|Mniej bezpieczna niż przy użyciu emisji pojedynczej, ponieważ osoba atakująca może wysyłać ciągłe strumienie żądań echa ICMP ze sfałszowanego adresu źródłowego na adres ukierunkowanej emisji. W rezultacie wszystkie hosty będą odpowiadać na adres źródłowy. Jeśli Konfiguracja routerów zezwalały na emisje skierowane do podsieci, ze względów bezpieczeństwa zaleca się dodatkowej konfiguracji:<br /><br /> -Skonfiguruj routery, aby zezwalały na emisje skierowane tylko do adresu IP z programu Configuration Manager serwera lokacji przy użyciu określonego numeru portu UDP.<br />— Konfigurowanie programu Configuration Manager do używania określonego inny niż domyślny numer portu.<br /><br /> Może wymagać ponownego skonfigurowania wszystkich pośredniczących routerów, aby włączyć emisji skierowanych do podsieci.<br /><br /> Używa więcej przepustowości sieci w porównaniu z emisjami pojedynczymi.<br /><br /> Obsługiwana przez protokół IPv4. Protokół IPv6 nie jest obsługiwany.|  

> [!WARNING]  
>  Istnieją zagrożeń bezpieczeństwa związanych z emisji skierowanych do podsieci: Osoba atakująca może wysłać ciągłe strumienie żądań echa protokołu komunikatu sterowania Internetem (ICMP) ze sfałszowanego adresu źródłowego na adres ukierunkowanej emisji, co powodować, że wszystkie hosty będą odpowiadać na adres źródłowy. Tego typu "odmowa usługi" jest popularnie określany mianem "smurf Attack" i zazwyczaj zapobiec, nie włączając emisji skierowanych do podsieci.

