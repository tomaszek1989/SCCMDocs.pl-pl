---
title: Wznawianie klientów
titleSuffix: Configuration Manager
description: Planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 52ee82b2-0b91-4829-89df-80a6abc0e63a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: aa5a0b30526f66add7dfb87fa988ed502cca1ee1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="plan-how-to-wake-up-clients-in-system-center-configuration-manager"></a>Planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Menedżer konfiguracji obsługuje dwa funkcji wake on technologie sieci lokalnych (LAN) do wznawiania komputerów w trybie uśpienia, jeśli chcesz zainstalować wymaganego oprogramowania, takie jak aktualizacje oprogramowania i aplikacji: tradycyjne pakiety wznawiania i polecenia włączania zasilania AMT.  

Przy użyciu ustawień klienta serwera proxy wznawiania, można uzupełnić metodę tradycyjnych pakietów wznawiania. Serwer proxy wznawiania używa protokół peer-to-peer oraz wybranych komputerów, aby sprawdzić, czy inne komputery w podsieci są wznowione oraz wznowić je w razie potrzeby. Gdy lokacja jest skonfigurowana dla funkcji Wake On LAN i klientów są skonfigurowane dla serwera proxy wznawiania, proces działa w następujący sposób:  

1.  Komputery z zainstalowanym klientem programu Configuration Manager, które nie są uśpione w podsieci, sprawdzają czy inne komputery w podsieci są wznowione. Robią to, wysyłając siebie polecenie TCP/IP ping co 5 sekund.  

2.  Jeśli nie ma odpowiedzi z innych komputerów, są one przyjęto uśpione. Komputery wznowione stają się *komputer zarządzający* podsieci.  

     Ponieważ istnieje możliwość, że komputer może nie odpowiadać z powodów innych niż jest w stanie uśpienia (na przykład jest wyłączony, odłączony od sieci lub ustawienie serwera proxy wznawiania klienta nie jest już stosowane), do komputerów będzie wysyłany pakiet wznawiania codziennie o godzinie 2: 00 czas lokalny. Nieodpowiadające komputery nie będą już uważane za uśpione i nie będą wznawiane przez serwer proxy wznawiania.  

     Do obsługi serwera proxy wznawiania, co najmniej trzy komputery muszą być w stanie aktywności dla każdej podsieci. Aby to osiągnąć, trzy komputery są wybrane w sposób niejednoznaczny jako *komputery stróżujące* podsieci. Oznacza to, że będą stale wznowione, niezależnie od ewentualnych skonfigurowanych zasad zasilania nakazujących uśpienie lub hibernację po okresie braku aktywności. Komputery stróżujące uznawać zamknięcia lub ponownego uruchomienia polecenia, na przykład w wyniku zadań konserwacji. W takim przypadku pozostałe komputery stróżujące wznawianie inny komputer w podsieci, aby podsieci w dalszym ciągu ma trzy komputery stróżujące.  

3.  Komputery zarządzające nakazują przełącznikowi do przekierowywania ruchu sieciowego dla uśpionych komputerów do siebie.  

     Przekierowywanie odbywa się przez komputer zarządzający przesyła ramkę Ethernet używającą adresu MAC uśpionego komputera jako adresu źródłowego. Dzięki temu zachowują się tak, jakby uśpiony komputer przeniósł się do tego samego portu, który komputer zarządzający znajduje się na przełącznik sieciowy. Komputer zarządzający wysyła również pakiety ARP dla uśpionych komputerów, aby zapewnić bieżące wpisy w pamięci podręcznej ARP. Komputer zarządzający będzie także odpowiadał na żądania ARP w imieniu uśpionego komputera i Odpowiedz przy użyciu adresu MAC uśpionego komputera.  

    > [!WARNING]  
    >  W trakcie tego procesu mapowanie adresu IP do MAC dla uśpionego komputera nie jest taka sama. Serwer proxy wznawiania działa informuje przełącznik sieciowy do innej karty sieciowej korzysta z portu, który został zarejestrowany przez inną kartę sieciową. Jednak to zachowanie jest nazywany niestabilnością adresu MAC i jest typowe dla standardowego działania sieci. Niektóre narzędzia monitorowania sieci szukają oznak takiego działania i można założyć, że dany element jest nieprawidłowy. W rezultacie tych narzędzi do monitorowania można generować alerty lub wyłączać porty, gdy używasz serwera proxy wznawiania.  
    >   
    >  Nie używaj serwera proxy wzbudzania, jeżeli narzędzia i usługi monitorowania sieci nie zezwalają na niestabilności adresów MAC.  

4.  Gdy komputer zarządzający dostrzeże nowe żądanie połączenia TCP uśpionego komputera i wysyłane do portu, na którym uśpiony komputer prowadził nasłuchiwanie przed uśpieniem, komputer zarządzający wysyła pakiet wznawiania do tego komputera, a następnie wstrzyma przekierowywanie ruchu dla tego komputera.  

5.  Uśpiony komputer otrzyma pakiet wznawiania i wznowi się. Wysyłający komputer automatycznie ponowi próbę połączenia i ten czas komputer jest w stanie aktywności i mogą odpowiadać.  

 Serwer proxy wznawiania ma następujące wymagania wstępne i ograniczenia:  

> [!IMPORTANT]  
>  Jeśli masz odrębny zespół, która jest odpowiedzialna za infrastrukturę sieci i usługami sieciowymi, powiadomienia, a także włączyć prowadzonej ewaluacji i testowaniu. Na przykład w sieci, która korzysta z metodą 802.1 X kontroli dostępu do sieci, serwer proxy wznawiania nie będzie działać i może zakłócać funkcjonowanie sieci. Ponadto serwer proxy wznawiania może spowodować niektóre narzędzia do generowania alertów w sytuacji wykrycia ruch do innych komputerów wznawiania monitorowania sieci.  

-   Obsługiwani klienci są Windows 7, Windows 8, Windows Server 2008 R2, Windows Server 2012.  

-   Systemy operacyjne gościa, które są uruchamiane na maszynie wirtualnej nie są obsługiwane.  

-   Klienci musi być włączony dla serwera proxy wznawiania przy użyciu ustawień klienta. Chociaż operacji serwera proxy wznawiania nie zależy od spisu sprzętu, klienty nie zgłaszają instalacji usługi serwera proxy wznawiania, chyba że są one włączone dla spisu sprzętu i spisu sprzętu co najmniej jeden zostało przesłane.  

-   Sieci karty (i prawdopodobnie systemu BIOS) musi być włączona i skonfigurowana obsługa pakietów wznawiania. Jeśli karta sieciowa nie jest skonfigurowana dla pakietów wznawiania lub to ustawienie jest wyłączone, programu Configuration Manager automatycznie skonfiguruje i włączy je w momencie otrzymania ustawienia klienta dotyczącego włączenia obsługi serwera proxy wznawiania dla komputera.  

-   Jeśli komputer ma więcej niż jedną kartę sieciową, która karta będzie używana dla serwera proxy wznawiania; nie można skonfigurować Wybór jest deterministyczna. Wybrana karta zostanie jednak zapisana w SleepAgent_ < domena\> @SYSTEM_0.log pliku.  

-   Sieć musi zezwalać na żądania echa protokołu ICMP (przynajmniej w obrębie podsieci). Nie można skonfigurować 5-sekundowego interwału, który służy do wysyłania komunikaty ICMP ping poleceń.  

-   Komunikacja jest bez szyfrowania i uwierzytelniania i protokołu IPsec nie jest obsługiwany.  

-   Następujące konfiguracje sieciowe nie są obsługiwane:  

    -   Metodą 802.1 X z funkcją uwierzytelniania portu  

    -   Sieci bezprzewodowe  

    -   Przełączniki sieciowe wiążące adresy MAC do określonych portów  

    -   Sieci obsługujących tylko protokół IPv6  

    -   Czas trwania dzierżawy DHCP mniej niż 24 godziny  

Jeśli chcesz wznawiania komputerów dla zaplanowaną instalacją oprogramowania, należy skonfigurować każdej lokacji głównej, aby użyć pakietów wznawiania.  

 Aby użyć serwera proxy wznawiania, należy wdrożyć ustawienia klienta serwera proxy wznawiania zarządzania energią, oprócz konfigurowania lokacji głównej.  

Należy również postanowić, czy używać pakietów emisji skierowanych do podsieci lub pakietów emisji pojedynczej i jakiego numeru portu UDP. Domyślnie tradycyjne pakiety wznawiania są przesyłane przy użyciu portu 9 UDP, ale aby zwiększyć poziom bezpieczeństwa, można wybrać alternatywny port dla witryny, jeśli to jest on obsługiwany przez pośredniczące routery i zapory.  

### <a name="choose-between-unicast-and-subnet-directed-broadcast-for-wake-on-lan"></a>Wybór między emisją pojedynczą i emisją kierowaną do podsieci na potrzeby funkcji Wake on LAN  
 W przypadku wybrania wznawiania komputerów, wysyłając tradycyjnych pakietów wznawiania należy zdecydować, czy do przesyłania pakietów emisji pojedynczej lub podsieci emisji skierowanej. Jeśli używasz serwera proxy wznawiania, należy wybrać opcję pakietów emisji pojedynczej. W przeciwnym razie użyj poniższej tabeli, aby ułatwić określenie, którą metodę transmisji należy wybrać.  

|Metoda transmisji|Zalety|Wadą|  
|-------------------------|---------------|------------------|  
|Emisji pojedynczej|Rozwiązanie bardziej bezpieczne niż emisje skierowane do podsieci, ponieważ pakiet jest wysyłany bezpośrednio do komputera zamiast do wszystkich komputerów w podsieci.<br /><br /> Nie może wymagać ponownego skonfigurowania routerów (może być konieczne konfigurowanie pamięci podręcznej ARP).<br /><br /> Wykorzystuje mniej przepustowości sieci niż transmisje skierowane do podsieci.<br /><br /> Obsługiwana za pomocą protokołów IPv4 i IPv6.|Pakiety wznawiania nie zostanie znaleziony komputerów docelowych, które zostały zmienione adres podsieci po ostatnim zaplanowanym spisie sprzętu.<br /><br /> Przełączniki mogą muszą być skonfigurowane do przekazywania pakietów UDP.<br /><br /> Niektóre karty sieciowe mogą nie reagować na wznawiania pakietów w trybie uśpienia wszystkie stany w przypadku używania emisji pojedynczej jako metody transmisji.|  
|Emisją kierowaną do podsieci|Wyższy poziom skuteczności w porównaniu z emisją pojedynczą, jeśli masz komputery, które zmieniają się często adresy IP w tej samej podsieci.<br /><br /> Nie ponownej konfiguracji przełącznika jest wymagane.<br /><br /> Wysoki poziom zgodności z kartami sieciowymi we wszystkich stanach uśpienia, ponieważ emisje skierowane do podsieci były oryginalną metodę transmisji wysyłania pakietów wznawiania.|Mniej bezpieczna niż przy użyciu emisji pojedynczej, ponieważ osoba atakująca może wysyłać ciągłe strumienie żądań echa protokołu ICMP ze sfałszowanego adresu źródłowego na adres ukierunkowanej emisji. W rezultacie wszystkie hosty będą odpowiadać na adres źródłowy. Jeśli Konfiguracja routerów zezwala na emisje skierowane do podsieci, ze względów bezpieczeństwa zaleca się dodatkowej konfiguracji:<br /><br /> -Skonfiguruj routery, aby zezwalały na emisje skierowane tylko do adresu IP z programu Configuration Manager serwer lokacji przy użyciu określonego numeru portu UDP.<br />-Konfigurowanie programu Configuration Manager do używania określonego z systemem innym niż domyślny numer portu.<br /><br /> Może wymagać ponownego skonfigurowania wszystkich pośredniczących routerów, aby włączyć emisje skierowane do podsieci.<br /><br /> Wykorzystuje więcej przepustowości w porównaniu z emisjami pojedynczymi.<br /><br /> Obsługiwane przez protokół IPv4. Protokół IPv6 nie jest obsługiwany.|  

> [!WARNING]  
>  Istnieją zagrożenia bezpieczeństwa związane z emisje skierowane do podsieci: Osoba atakująca może wysyłać ciągłe strumienie żądań echa protokołu komunikatu sterowania Internetem (ICMP) ze sfałszowanego adresu źródłowego na adres ukierunkowanej emisji, co będzie powodować, że wszystkie hosty będą odpowiadać na adres źródłowy. Tego typu odmowa usługi jest popularnie określany atak smurf i mu zazwyczaj zapobiec, nie włączając funkcji emisji skierowanej do podsieci.
