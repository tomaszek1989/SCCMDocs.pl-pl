---
title: Skonfiguruj bramę zarządzania w chmurze
titleSuffix: Configuraton Manager
description: Użyj proces ten krok po kroku dotyczące konfigurowania bramy zarządzania chmury (CMG).
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.openlocfilehash: 04c1b262704ec6458bd9773c28c43a50d8fc0840
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Konfigurowanie bramy zarządzania w chmurze programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*  

Proces ten obejmuje kroki wymagane do skonfigurowania bramy zarządzania chmury (CMG). 

> [!Tip]
> Ta funkcja została wprowadzona w wersji 1610 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1802, ta funkcja nie jest już funkcji wersji wstępnej.



## <a name="before-you-begin"></a>Przed rozpoczęciem

Rozpocznij od przeczytania artykułu [planowanie brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway). Użyj tego artykułu, aby określić CMG projektu. 

Poniższa lista kontrolna umożliwia upewnij się, że masz niezbędne informacje i wymagania wstępne, aby utworzyć CMG:  

- Środowisko Azure do użycia. Na przykład w chmurze publicznej Azure lub instytucji rządowych Stanów Zjednoczonych chmury Azure.  

- Potrzebne są co najmniej jednego certyfikatu dla CMG, w zależności od projektu. Aby uzyskać więcej informacji, zobacz [certyfikatów dla bramy zarządzania chmury](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).  

- Począwszy od wersji 1802, wybierz, czy używasz **wdrożenia usługi Azure Resource Manager** lub **wdrożenia usługi klasycznego**. Aby uzyskać więcej informacji, zobacz [usługi Azure Resource Manager](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager). Wdrożenia usługi Azure Resource Manager CMG niezbędne są następujące wymagania:  

    - Integracja z [usługi Azure AD](/sccm/core/servers/deploy/configure/azure-services-wizard) dla **chmury zarządzania**. Odnajdowanie użytkowników usługi Azure AD nie jest wymagane.  

    - Administrator subskrypcji musi się zalogować.  

- Wdrożenia klasycznego usługi programu CMG są potrzebne następujące wymagania:  

    - Identyfikator subskrypcji platformy Azure  

    - Certyfikat zarządzania platformy Azure  

- Globalnie unikatowej nazwy dla usługi. Ta nazwa jest z [certyfikatu uwierzytelniania serwera CMG](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate).  

- Region platformy Azure dla tego wdrożenia CMG.  

- Jak wiele wystąpień maszyn wirtualnych należy na skalowalność i nadmiarowość.  



## <a name="set-up-a-cmg"></a>Konfigurowanie CMG

Tę procedurę należy wykonać w lokacji najwyższego poziomu. Ta witryna jest autonomiczną lokacją główną lub centralną lokację administracyjną.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **brama zarządzania chmury**.  

2. Kliknij przycisk **Tworzenie bramy zarządzania chmury** na Wstążce.  

3. Począwszy od wersji 1802, na stronie Ogólne kreatora, należy najpierw wybrać metodę wdrażania CMG **wdrożenia usługi Azure Resource Manager** lub **wdrożenia usługi Classic**.  

    1. Aby uzyskać **wdrożenia usługi Azure Resource Manager**: Kliknij przycisk **Zaloguj** do uwierzytelniania przy użyciu konta administratora subskrypcji platformy Azure. Kreator automatycznego wypełniania pozostałe pola z informacjami przechowywanymi w wymagań wstępnych integracji usługi Azure AD. Jeśli masz wiele subskrypcji, wybierz **identyfikator subskrypcji** żądaną subskrypcji do użycia.  

    2. Dla **wdrożenia usługi klasycznego**, *i wersje programu Configuration Manager 1706 i 1710*: Wprowadź Azure **identyfikator subskrypcji**. Następnie kliknij przycisk **Przeglądaj** i wybierz. Plik PFX certyfikatu zarządzania platformy Azure. 

4. Określ **środowiska platformy Azure** dla tego CMG. Opcji na liście rozwijanej mogą się różnić w zależności od metody wdrażania.  

5. Kliknij przycisk **Dalej**. Poczekaj jako lokacji testuje połączenie na platformie Azure.  

4. Na stronie ustawień kreatora, najpierw kliknij **Przeglądaj** i wybierz. Plik PFX CMG certyfikatu uwierzytelniania serwera. Nazwy na podstawie tego certyfikatu wypełnia wymaganych **nazwa FQDN usługi** i **nazwa usługi** pola.  

   > [!NOTE]  
   > Począwszy od wersji 1802 certyfikatu uwierzytelniania serwera CMG obsługuje symboli wieloznacznych. Jeśli używany jest certyfikat wieloznaczny, Zastąp gwiazdkę (\*) w **nazwa FQDN usługi** pole z żądaną nazwą hosta dla CMG.  
   <!--491233-->  

5. Kliknij przycisk **Region** listy rozwijanej, aby wybrać region platformy Azure dla tego CMG.  

6. Wybierz przy użyciu wdrożenia usługi Azure Resource Manager w wersji 1802 i są **grupy zasobów** opcji. 
   1. Jeśli wybierzesz **Użyj istniejącego**, następnie wybierz istniejącą grupę zasobów z listy rozwijanej.
   2. Jeśli wybierzesz **Utwórz nowy**, wprowadź nazwę nowej grupy zasobów.

6. W **wystąpienia maszyny Wirtualnej** wprowadź liczbę maszyn wirtualnych dla tej usługi. Wartość domyślna to jeden, ale można skalować do 16 maszyn wirtualnych na CMG.  

7. Kliknij przycisk **certyfikaty** Aby dodać klienta zaufanych certyfikatów głównych. Dodaj maksymalnie dwóch zaufanych głównych urzędów certyfikacji i cztery pośrednie urzędy certyfikacji (podrzędnego).  

8. Domyślnie Kreator włącza opcję **Sprawdź odwołania certyfikatu klienta**. Listy odwołania certyfikatów (CRL) musi być publicznie opublikowana na potrzeby weryfikacji do pracy. Jeśli nie możesz opublikować listę CRL, usuń zaznaczenie tej opcji.  

9. Kliknij przycisk **Dalej**.  

10. Aby monitorować ruch CMG z progiem 14 dni, wybierz pole wyboru, aby włączyć próg alertu. Następnie należy określić próg i procent w którego zostanie wywołane na różnych poziomach alertów. Wybierz **dalej** po zakończeniu.  

11. Przejrzyj ustawienia, a następnie wybierz pozycję **dalej**. Configuration Manager rozpoczyna się ustawienie usługi. Po zamknięciu kreatora potrwa od 5 do 15 minut do udostępniania usługi całkowicie na platformie Azure. Sprawdź **stan** kolumny dla nowych CMG w celu określenia, kiedy usługa jest gotowa.  

 > [!Note]  
 > Aby rozwiązać CMG wdrożenia, użyj **CloudMgr.log** i **CMGSetup.log**. Aby uzyskać więcej informacji, zobacz [pliki dziennika](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="configure-primary-site-for-client-certificate-authentication"></a>Konfigurowanie lokacji głównej do uwierzytelniania certyfikatu klienta

Jeśli używasz [certyfikatów uwierzytelniania klienta](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate) dla klientów uwierzytelniania za pomocą CMG, wykonaj tę procedurę, aby skonfigurować lokację główną.  

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i wybierz **witryny**.  

2. Wybierz lokację główną, do której przypisano klientów internetowych i wybierz polecenie **właściwości**.  

3. Przełącz się do **komunikacji z klientem komputera** karcie arkusza właściwości lokacji głównej, sprawdź **Użyj certyfikatu klienta PKI (uwierzytelnianie) Jeśli jest dostępna**.  

4. Jeśli nie możesz opublikować listę CRL, wyłącz opcję dla **klienci sprawdzają listę odwołania certyfikatów (CRL) dla systemów lokacji**.  



## <a name="add-the-cmg-connection-point"></a>Dodawanie punktu połączenia CMG

Punkt połączenia CMG jest rola systemu lokacji do komunikowania się z CMG. Aby dodać punkt połączenia CMG, postępuj zgodnie z instrukcjami ogólne [zainstalować role systemu lokacji](/sccm/core/servers/deploy/configure/install-site-system-roles). Na stronie Wybór roli systemu w Kreatorze dodawania ról systemu lokacji wybierz **chmury punkt połączenia z bramą zarządzania**. Następnie wybierz **nazwę bramy zarządzania chmury** do który łączy tego serwera. Kreator pokazuje region dla wybranego CMG. 

> [!Important]
> CMG punkt połączenia musi mieć [certyfikat uwierzytelniania klienta](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate) w niektórych scenariuszach. 

 > [!Note]  
 > Aby rozwiązać CMG usługi kondycji, należy użyć **CMGService.log** i **SMS_Cloud_ProxyConnector.log**. Aby uzyskać więcej informacji, zobacz [pliki dziennika](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="configure-client-facing-roles-for-cmg-traffic"></a>Konfigurowanie ról po stronie klienta dla ruchu CMG

Skonfiguruj punkt i oprogramowania aktualizacji systemami lokacji punktu zarządzania do akceptowania ruchu CMG. Tę procedurę należy wykonać w lokacji głównej dla wszystkich punktów zarządzania i punkty aktualizacji oprogramowania obsługujących klientów internetowych.  

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, kliknij prawym przyciskiem myszy **serwery i role systemu lokacji**i wybierz pozycję **Punkt zarządzania** z listy.  

2. Wybierz serwer systemu lokacji, który chcesz skonfigurować CMG ruchu. Wybierz **punkt zarządzania** roli w okienku szczegółów, a następnie kliknij przycisk **właściwości** na Wstążce.  

3. W arkuszu właściwości punktu zarządzania w obszarze połączenia klienta, zaznacz pole wyboru obok pozycji **ruch bramy zarządzania chmury programu Configuration Manager umożliwia**. 
    - Zależności projektu CMG i wersji programu Configuration Manager, należy włączyć **HTTPS** opcji. Aby uzyskać więcej informacji, zobacz [Włącz punkt zarządzania dla protokołu HTTPS](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https).  

4. Kliknij przycisk **OK**.   

W razie potrzeby powtórz te kroki dla dodatkowych punktów zarządzania i punkty aktualizacji oprogramowania. 



## <a name="configure-clients-for-cmg"></a>Skonfigurować klientów CMG

Po CMG a role systemu lokacji są uruchomione, klienci uzyskują lokalizację usługi CMG automatycznie przy kolejnym żądaniu lokalizacji. Klienci muszą być w sieci intranet w celu odbierania lokalizację usługi CMG, chyba że użytkownik [Zainstaluj i przypisz przy użyciu usługi Azure AD do uwierzytelniania klientów systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Cykl sondowania żądań lokalizacji jest co 24 godziny. Jeśli nie chcesz czekać na żądanie zwykle zaplanowane lokalizacji, możesz wymusić żądanie przez ponowne uruchomienie usługi hosta agenta programu SMS (ccmexec.exe) na komputerze.  

> [!Note]
> Domyślnie wszyscy klienci otrzymają CMG zasad. Kontroli tego zachowania przy użyciu ustawienia, klienta [umożliwić klientom używanie brama zarządzania chmury](/sccm/core/clients/deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway).

Klient programu Configuration Manager automatycznie ustala, czy w intranecie lub Internecie. Jeśli klient może skontaktować się z kontrolerem domeny lub lokalnego zarządzania punktu, ustawia jego typ połączenia **aktualnie w sieci intranet**. W przeciwnym razie zmienia na **obecnie Internet**i używa lokalizację usługi CMG do komunikacji z lokacją.

>[!NOTE]
> Można wymusić klienta, aby zawsze była używana CMG niezależnie od tego, czy jest w intranecie lub Internecie. Ta konfiguracja jest przydatna do celów testowych lub dla klientów w biurach zdalnych, które mają być Wymuś użycie CMG. Na komputerze klienckim, należy ustawić następujący klucz rejestru:
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`
>
> Można również określić tego ustawienia podczas instalacji klienta, używając [CCMALWAYSINF](/sccm/core/clients/deploy/about-client-installation-properties#ccmalwaysinf) właściwości.

Aby sprawdzić, czy klienci mają zasad określania CMG, otwórz wiersz polecenia programu Windows PowerShell jako administrator na komputerze klienckim, a następnie uruchom następujące polecenie: `Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}`

To polecenie wyświetla punktów internetowego zarządzania, który zna klienta. Podczas CMG nie jest technicznie internetowego punktu zarządzania do, wydaje się tak na klientach.

 > [!Note]  
 > Aby rozwiązać CMG ruch klientów, należy użyć **CMGHttpHandler.log**, **CMGService.log**, i **SMS_Cloud_ProxyConnector.log**. Aby uzyskać więcej informacji, zobacz [pliki dziennika](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="modify-a-cmg"></a>Modyfikowanie CMG

Po utworzeniu CMG, można zmodyfikować niektóre ustawienia. Wybierz CMG w konsoli programu Configuration Manager, a następnie kliknij przycisk **właściwości**. Konfigurowane są następujące ustawienia:  

- **Ogólne**  

    - **Certyfikat zarządzania platformy Azure**: zmienić certyfikat zarządzania platformy Azure dla CMG. Ta opcja jest przydatna podczas aktualizacji certyfikatu przed jego wygaśnięciem.  

- **Ustawienia**  

    - **Plik certyfikatu**: Zmienianie certyfikatu uwierzytelniania serwera dla CMG. Ta opcja jest przydatna podczas aktualizacji certyfikatu przed jego wygaśnięciem.  

    - **Wystąpienie maszyny Wirtualnej**: Zmień liczbę maszyn wirtualnych używanych przez usługę w systemie Azure. To ustawienie umożliwia dynamiczne skalować usługę w górę lub w dół na podstawie użycia lub koszt zagadnienia.  

    - **Certyfikaty**: Dodawanie lub usuwanie zaufanych certyfikatów głównych lub pośrednich urzędów certyfikacji. Ta opcja jest przydatna podczas dodawania nowego urzędów certyfikacji lub wycofanie wygasłe certyfikaty.  

    - **Sprawdzania odwołania certyfikatu klienta**: Jeśli nie została pierwotnie włączona to ustawienie podczas tworzenia CMG, możesz je włączyć później po publikowania listy CRL.  

- **Alerty**: można ponownie skonfigurować alerty w dowolnym momencie po utworzeniu CMG. 

Bardziej znaczących zmian, takich jak następujące konfiguracje wymagają ponownego wdrażania usługi:
- Metody wdrażania klasycznego do usługi Azure Resource Manager
- Subskrypcji
- Nazwa usługi
- Prywatny, publiczny infrastruktury kluczy publicznych
- Region

Zawsze Zachowuj co najmniej jeden aktywny CMG dla klientów internetowych do otrzymania zaktualizowanej zasady. Klienci internetowi nie może komunikować się z usuniętym CMG. Klienci nie wiadomo o nowy, dopóki nie są one przekazywane do sieci intranet. Podczas tworzenia drugiego wystąpienia CMG, aby usunąć pierwszy, również utworzyć inny punkt połączenia CMG.

Klienci odświeżania zasady domyślnie co 24 godziny, więc oczekiwać co najmniej jeden dzień po utworzeniu nowego CMG przed usunięciem starego. Klienci są wyłączony lub bez połączenia z Internetem, może być konieczne będzie czekać. 

Od wersji 1802, jeśli masz istniejące CMG na metodę wdrażania klasycznego, należy wdrożyć nowe CMG przy użyciu metody wdrożenia usługi Azure Resource Manager.<!--509753--> Dostępne są dwie opcje:
- Jeśli chcesz ponownie użyć tej samej nazwy usługi:
    1. Najpierw należy usunąć klasycznego CMG, biorąc pod uwagę, aby zawsze mieć co najmniej jeden aktywny CMG dla klientów internetowych.
    2. Utwórz nowy CMG, przy użyciu wdrożenia usługi Resource Manager. Ponownie użyć tego samego certyfikatu uwierzytelniania serwera.
    3. Ponownie skonfiguruj punkt połączenia CMG, którego chcesz użyć nowego wystąpienia CMG.
- Jeśli chcesz użyć Nowa nazwa usługi:
    1. Utwórz nowy CMG, przy użyciu wdrożenia usługi Resource Manager. Użyj certyfikatu uwierzytelniania serwera.
    2. Utwórz nowy punkt połączenia CMG i łącze z nowego CMG.
    3. Poczekaj co najmniej jeden dzień w przypadku klientów internetowych do odbierania zasad dotyczących nowych CMG.
    4. Usuń CMG klasycznego.

Modyfikowanie tylko CMG z konsoli programu Configuration Manager. Wprowadzenie zmian do usługi lub podstawowej maszyn wirtualnych bezpośrednio na platformie Azure nie jest obsługiwane. Wszelkie zmiany mogą zostać utracone bez uprzedzenia. Podobnie jak w przypadku dowolnego PaaS usługi można odtworzyć maszyny wirtualne w dowolnym momencie. Te odtwarza może się zdarzyć, do obsługi sprzętu wewnętrznej bazy danych lub do stosowania aktualizacji do systemu operacyjnego maszyny Wirtualnej.

Jeśli musisz usunąć CMG także zrobić z konsoli programu Configuration Manager. Ręczne usuwanie wszystkich składników w Azure powoduje, że system jest niespójny. Ten stan pozostawia informacji oddzielone i mogą wystąpić nieoczekiwane wyniki. 



## <a name="next-steps"></a>Następne kroki

- [Monitorowanie klientów dla bramy zarządzania w chmurze](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway)
- [Często zadawane pytania dotyczące zarządzania bramy chmury](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
