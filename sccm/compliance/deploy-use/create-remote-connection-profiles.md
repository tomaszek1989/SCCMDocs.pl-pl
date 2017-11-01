---
title: "Tworzenie profili połączenia zdalnego"
titleSuffix: Configuration Manager
description: "Użyj profili połączenia zdalnego programu System Center Configuration Manager, aby umożliwić użytkownikom połączenie zdalne z komputerami roboczymi."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c6eabc4-5dda-4682-b03e-3a450e6ef65a
caps.latest.revision: "8"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 8ca0b961f075f41984d6dbba7321c375940a8622
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="remote-connection-profiles-in-system-center-configuration-manager"></a>Profile połączenia zdalnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Używany System Center Configuration Manager profili połączenia zdalnego umożliwiają użytkownikom zdalne połączenia z komputerami roboczymi, gdy nie są połączeni z domeną lub jeśli ich komputery osobiste łączą się przez Internet.  

 Użytkownicy mogą łączyć się ze swoimi komputerami roboczymi za pomocą urządzeń następujących typów:  

-   Komputery z systemem Microsoft Windows  

-   Urządzenia z systemem iOS  

-   Urządzenia z systemem Android  

Profile połączenia zdalnego umożliwiają wdrażanie ustawień programu Podłączanie pulpitu zdalnego dla użytkowników w hierarchii programu Configuration Manager. Użytkownicy mogą następnie skorzystać z portalu firmy w celu uzyskania dostępu do swoich podstawowych komputerów roboczych poprzez funkcję pulpitu zdalnego przy użyciu ustawień programu Podłączanie pulpitu zdalnego udostępnionych przez portal firmy.  

Aby użytkownicy mogli się łączyć ze swoimi komputerami roboczymi przy użyciu portalu firmy, wymagana jest usługa Microsoft Intune. Jeśli usługa Intune nie jest używana, użytkownicy mogą w dalszym ciągu korzystać z informacji znajdujących się w profilu połączenia zdalnego w celu nawiązania połączenia ze swoimi komputerami roboczymi, korzystając z funkcji pulpitu zdalnego przez połączenie VPN.  

> [!IMPORTANT]  
>  Po określeniu ustawień profilu połączenia zdalnego przy użyciu konsoli programu Configuration Manager, ustawienia są przechowywane w lokalnych zasadach komputera klienckiego. Te ustawienia mogą zastąpić ustawienia pulpitu zdalnego skonfigurowane przez inną aplikację. Ponadto jeśli używasz zasad grupy systemu Windows do konfigurowania ustawień pulpitu zdalnego, określonym w zasadach grupy zastępują ustawienia skonfigurowane za pomocą programu Configuration Manager.  

 Po zainstalowaniu programu Configuration Manager nową grupę zabezpieczeń, **połączenie komputera zdalnego**, zostanie utworzona. Ta grupa jest wypełniana podczas wdrażania profilu połączenia zdalnego zawierającego użytkowników podstawowych komputera, na którym jest wdrażany profil. Wprawdzie administrator lokalny może dodać nazwy użytkowników do tej grupy, ale ci użytkownicy zostaną usunięci z grupy podczas następnego sprawdzania profili połączenia zdalnego pod kątem zgodności.  

 Jeśli użytkownik zostanie dodany ręcznie do tej grupy, będzie on mógł inicjować połączenia zdalne, ale informacje o połączeniu nie zostaną opublikowane w portalu firmy.  

 Jeśli ręcznie usunąć z grupy użytkownika, który został dodany przez program Configuration Manager, Configuration Manager zostanie automatycznie skoryguje tę zmianę, dodając użytkownika z powrotem po następnym profilu połączenia zdalnego pod kątem zgodności.  

> [!IMPORTANT]  
>  Jeśli relacja koligacji urządzenia użytkownika między użytkownikiem urządzeniem ulegnie zmianie (na przykład komputer łączy się z użytkownikiem, przestanie być urządzeniem podstawowym użytkownika programu Configuration Manager wyłączy profil połączenia zdalnego i ustawienia zapory systemu Windows, aby uniemożliwić połączenia z komputerem.  

## <a name="prerequisites"></a>Wymagania wstępne  

### <a name="external-dependencies"></a>Zależności zewnętrzne  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Serwer bramy usługi pulpitu zdalnego.|Aby umożliwić użytkownikom połączenie z Internetem spoza domeny firmowej, należy zainstalować i skonfigurować serwer bramy usługi pulpitu zdalnego.<br /><br /> Jeżeli ustawieniami pulpitu zdalnego lub usług terminalowych zarządza inna aplikacja lub ustawienia zasad grupy, profile połączenia zdalnego mogą nie działać prawidłowo. Po wdrożeniu profili połączenia zdalnego z konsoli programu Configuration Manager, jego ustawienia są przechowywane w lokalnych zasadach komputera klienckiego. Te ustawienia mogą zastąpić ustawienia pulpitu zdalnego skonfigurowane przez inną aplikację. Ponadto jeżeli ustawienia zasad grupy są używane do konfigurowania ustawień pulpitu zdalnego, ustawienia określone w ustawieniach zasad grupy zastępują ustawienia skonfigurowane przez program Configuration Manager.<br /><br /> Więcej informacji o sposobie instalowania i konfigurowania serwera bramy usługi pulpitu zdalnego znajduje się w dokumentacji systemu Windows Server.|  
|Jeżeli na komputerze klienckim działa zapora oparta na hoście, musi włączyć program Mstsc.exe.|Podczas konfigurowania profilu połączenia zdalnego należy włączyć ustawienie **Zezwalaj na wyjątek zapory systemu Windows dla połączeń w domenach systemu Windows i sieciach prywatnych** . Jeśli to ustawienie jest włączone, programu Configuration Manager automatycznie konfiguruje Zaporę systemu Windows w celu włączenia programu Mstsc.exe. Jeżeli jednak na komputerach klienckich działa inna zapora oparta na hoście, należy ręcznie skonfigurować zależność tej zapory.<br /><br /> Ustawienia zasad grupy, które konfigurują Zaporę systemu Windows, mogą zastąpić konfigurację ustawioną w programie Configuration Manager. Jeżeli zasady grupy są używane do konfigurowania Zapory systemu Windows, należy upewnić się, że ich ustawienia nie blokują programu Mstsc.exe.|  

### <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Programu Configuration Manager musi być podłączony do Microsoft Intune (nazywane Konfiguracja hybrydowa).|Aby uzyskać więcej informacji o podłączaniu programu Configuration Manager w usłudze Microsoft Intune Zobacz Zarządzanie urządzeniami przenośnymi za pomocą programu Configuration Manager i Microsoft Intune.|  
|Aby użytkownik mógł się połączyć z komputerem roboczym w sieci firmowej, musi on być jego urządzeniem podstawowym.|Aby uzyskać więcej informacji o koligacji urządzenia użytkownika, zobacz [łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity).|  
|Do zarządzania profilami połączenia zdalnego należy przyznać określone uprawnienia zabezpieczeń.|Rola zabezpieczeń **Menedżer ustawień zgodności** zawiera uprawnienia wymagane do zarządzania profilami połączenia zdalnego. Aby uzyskać więcej informacji, zobacz artykuł <br />[Konfigurowanie administracji opartej na rolach](/sccm/core/servers/deploy/configure/configure-role-based-administration).|  

## <a name="security-and-privacy-considerations-for-remote-connection-profiles"></a>Zagadnienia dotyczące bezpieczeństwa i ochrony prywatności w profilach połączenia zdalnego  

### <a name="security-considerations"></a>Zagadnienia dotyczące bezpieczeństwa  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Należy określić koligację urządzenia użytkownika zamiast zezwalać użytkownikom na identyfikację ich urządzenia podstawowego. Ponadto nie należy włączać konfiguracji opartej na użyciu.|Ponieważ przed wdrożeniem profilu połączenia zdalnego konieczne jest włączenie opcji **Zezwalaj na połączenie zdalne wszystkich głównych użytkowników komputera roboczego** , należy zawsze ręcznie określić koligację urządzenia użytkownika. Nie należy traktować jako wiarygodnych informacji zebranych od użytkowników lub z urządzeń. Jeżeli po wdrożeniu profili połączenia zdalnego zaufany użytkownik administracyjny nie określi koligacji urządzenia użytkownika, nieautoryzowani użytkownicy mogą uzyskać podniesione uprawnienia, a następnie połączyć się zdalnie z komputerami.<br /><br /> Po włączeniu konfiguracji opartej na użyciu te informacje są zbierane za pomocą komunikatów stanu, dla których programu Configuration Manager nie ma zabezpieczeń. Aby ułatwić uniknięcie tego zagrożenia, należy użyć podpisywania bloku komunikatów serwera (SMB) lub zabezpieczeń protokołu internetowego (IPsec) między komputerami klienckimi a punktem zarządzania.|  
|Należy ograniczyć lokalne prawa administracyjne na komputerze serwera lokacji.|Użytkownik, który ma lokalne prawa administracyjne na serwerze lokacji można ręcznie dodać członków do grupy zabezpieczeń połączenie zdalne z Komputerem, który programu Configuration Manager automatycznie tworzy i obsługuje. Może to spowodować podniesienie uprawnień, ponieważ członkowie dodani do tej grupy uzyskują uprawnienia do funkcji Pulpit zdalny.|  

### <a name="privacy-considerations"></a>Zagadnienia dotyczące ochrony prywatności  

-   Jeżeli użytkownik zainicjuje połączenie z komputerem roboczym z portalu firmy, pobierany jest plik z rozszerzeniem rdp lub wsrdp zawierający nazwę urządzenia i nazwę serwera bramy usług pulpitu zdalnego wymagane do zainicjowania sesji pulpitu zdalnego. Rozszerzenie pliku zależy od systemu operacyjnego urządzenia. Przykładowo w systemach operacyjnych Windows 7 i Windows 8 używany jest plik rdp, a w systemie Windows 8.1 używany jest plik wsrdp.  

-   Użytkownik może otworzyć lub zapisać plik rdp. W przypadku otwarcia pliku rdp może on zostać zapisany w pamięci podręcznej przeglądarki sieci Web, w zależności od ustawień przechowywania skonfigurowanych w przeglądarce. W przypadku zapisania pliku nie jest on przechowywany w pamięci podręcznej przeglądarki. Plik pozostaje zapisany do momentu ręcznego usunięcia go przez użytkownika.  

-   Plik wsrdp jest pobierany i automatycznie zapisywany lokalnie. Jest on zastępowany przy następnym uruchomieniu przez użytkownika sesji pulpitu zdalnego.  

-   Przed skonfigurowaniem profili połączenia zdalnego należy uwzględnić wymagania dotyczące poufności.  


## <a name="create-a-remote-connection-profile"></a>Utwórz profil połączenia zdalnego

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **profile połączenia zdalnego**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz profil połączenia zdalnego**.  

4.  Na stronie **Ogólne** **Kreatora tworzenia profilu połączenia zdalnego**określ nazwę i opcjonalny opis profilu przy użyciu maksymalnie 256 znaków dla każdego z tych elementów.  

5.  Na **profilu** strony ustawień, określ następujące ustawienia dla profilu połączenia zdalnego:  

    -   **Pełna nazwa i port serwera bramy usług pulpitu zdalnego (opcjonalnie)** — określ nazwę serwera bramy usług pulpitu zdalnego używanego do nawiązywania połączeń.  

        > [!NOTE]  
        >  Menedżer konfiguracji nie obsługuje międzynarodowych nazw domen podczas wprowadzania serwera w tym polu.  
        >   
        >  Nazwa serwera nie może być dłuższa niż 256 znaków i może zawierać tylko małe litery, wielkie litery, cyfry oraz półpauzę **–** i podkreślenie **_** , oddzielone kropkami.  

    -   **Zezwalaj na połączenia tylko z komputerów, na których działa usługa Pulpit zdalny z uwierzytelnieniem na poziomie sieci**  

6.  Dla wszystkich poniższych ustawień połączenia wybierz opcję **Włączone** lub **Wyłączone** :  

    -   **Zezwalaj na połączenia zdalne z komputerami roboczymi**  

    -   **Zezwalaj na połączenie zdalne wszystkich głównych użytkowników komputera roboczego**  

    -   **Zezwalaj na wyjątek zapory systemu Windows dla połączeń w domenach systemu Windows i sieciach prywatnych**  

    > [!IMPORTANT]  
    >  Przed zamknięciem tej strony kreatora wszystkie trzy ustawienia muszą być skonfigurowane tak samo.  

7.  Na **Podsumowanie** Przejrzyj akcje wykonywane, a następnie Zakończ pracę kreatora.  

 Nowy profil połączenia zdalnego zostanie wyświetlony w węźle **Profile połączenia zdalnego** w obszarze roboczym **Zasoby i zgodność** .  

Wdróż profil połączenia zdalnego  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **profile połączenia zdalnego**.  

3.  Na liście **Profile połączenia zdalnego** wybierz profil połączenia zdalnego, który chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

4.  W oknie dialogowym **Wdróż profil połączenia zdalnego** określ następujące informacje:  

    -   **Kolekcja** — kliknij przycisk **Przeglądaj** , aby wybrać kolekcję urządzeń, w której chcesz wdrożyć profil połączenia zdalnego.  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** -Włącz to, aby automatycznie korygować profil połączenia zdalnego, gdy okaże się niezgodny na urządzeniu, na przykład, jeśli nie występuje.  

    -   **Zezwalaj na korygowanie poza oknem obsługi** — Jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz profil połączenia zdalnego, Włącz tę opcję, aby umożliwić programowi Configuration Manager korygować profil połączenia zdalnego poza oknem obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).  

    -   **Wygeneruj alert** — włącz tę opcję, aby skonfigurować alert generowany, jeśli zgodność profilu połączenia zdalnego do danego dnia i godziny będzie mniejsza niż określony procent. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

    -   **Określ harmonogram oceny zgodności dla tej linii bazowej konfiguracji** — określ harmonogram oceny profilu połączenia zdalnego wdrożonego na urządzeniach. Może to być harmonogram prosty lub niestandardowy.  

    > [!TIP]  
    >  Jeśli urządzenie opuści kolekcję, do której został wdrożony profil połączenia zdalnego, ustawienia tego profilu zostaną wyłączone w urządzeniu. Aby jednak ten proces odbył się prawidłowo, powinien już być wdrożony co najmniej jeden element konfiguracji lub plan bazowy konfiguracji zawierający element konfiguracji z używanej lokacji.  
    >   
    >  Klienci oceniają profile według urządzeń po zalogowaniu się użytkownika.  
    >   
    >  Jeśli dwa profile połączenia zdalnego zostaną wdrożone do tej samej kolekcji urządzeń, przy czym w jednym profilu zaznaczono pole opcji **Koryguj niezgodne reguły, jeśli są obsługiwane** , w drugim profilu nie zaznaczono pola tej opcji, a te dwa profile zawierają różne ustawienia połączenia, wówczas profil z niezaznaczonym polem może przesłonić ustawienia w drugim profilu. Ten typ wdrożenia profilu połączenia zdalnego nie jest obsługiwany przez program Configuration Manager.  

5.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdróż profil połączenia zdalnego** i utworzyć wdrożenie.  

## <a name="monitor-a-remote-connection-profile"></a>Monitorowanie profilu połączenia zdalnego  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Wyświetlanie wyników zgodności w konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie** > **wdrożeń**.  

3.  Z listy **Wdrożenia** wybierz wdrożenie profilu połączenia zdalnego, którego informacje o zgodności chcesz przejrzeć.  

4.  Podsumowanie informacji o zgodności wdrożenia profilu połączenia zdalnego można przejrzeć na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie profilu połączenia zdalnego, a następnie w grupie **Wdrażanie** na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan** , aby otworzyć stronę **Stan wdrożenia** .  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodne:** Zawiera informacje o zgodności profilu połączenia zdalnego na podstawie liczby uwzględnionych zasobów. Możesz dwukrotnie kliknąć zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkie urządzenia zgodne z profilem połączenia zdalnego. W okienku **Szczegóły zasobu** zostaną dodatkowo wyświetlone urządzenia zgodne z tym profilem. Dwukrotnie kliknij urządzenie na liście, aby wyświetlić dodatkowe informacje.  

        > [!IMPORTANT]  
        >  Profil połączenia zdalnego nie jest oceniany, jeśli nie dotyczy urządzenia klienckiego. Jego stan jest jednak zwracany jako zgodny.  

    -   **Błąd:** Wyświetla listę wszystkich błędów dla wdrożenia profilu połączenia zdalnego wybranej na podstawie liczby uwzględnionych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkie urządzenia generujące błędy w tym profilu. Po wybraniu urządzenia w okienku **Szczegóły zasobu** zostaną wyświetlone urządzenia, których dotyczy wybrany problem. Dwukrotnie kliknij urządzenie na liście, aby wyświetlić dodatkowe informacje o problemie.  

    -   **Niezgodne:** Wyświetla listę wszystkich niezgodnych reguł w profilu połączenia zdalnego na podstawie liczby uwzględnionych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkie urządzenia, które nie są zgodne z tym profilem. Po wybraniu urządzenia w okienku **Szczegóły zasobu** zostaną wyświetlone urządzenia, których dotyczy wybrany problem. Dwukrotnie kliknij urządzenie na liście, aby wyświetlić dodatkowe informacje o problemie.  

    -   **Nieznany:** Wyświetla listę wszystkich urządzeń, które nie zgłosiły zgodności dla wdrożenia profilu połączenia zdalnego wybrane, wraz z bieżącym stanem klienta urządzeń.  

5.  Na stronie **Stan wdrożenia** możesz przejrzeć szczegółowe informacje o zgodności wdrożonego profilu połączenia zdalnego. W węźle **Wdrożenia** jest tworzony węzeł tymczasowy, który ułatwia szybkie znalezienie tych informacji ponownie.  

### <a name="view-compliance-results-with-reports"></a>Wyświetlanie wyników zgodności przy użyciu raportów  
 Configuration Manager zawiera wbudowane raporty, które umożliwiają monitorowanie informacji o profilach połączeń zdalnych. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów **Filtr urządzenia** i **Filtr użytkownika** w raportach ustawień zgodności należy użyć symbolu wieloznacznego (%).  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](/sccm/core/servers/manage/reporting).  
