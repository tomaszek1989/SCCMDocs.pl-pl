---
title: Wdrażanie klientów do systemu Windows
titleSuffix: Configuration Manager
description: Dowiedz się, jak wdrożyć klienta programu Configuration Manager na komputerach z systemem Windows.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3d7c3e9c9f2af8d612ef158897c281d422692268
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed zainstalowaniem klientów programu Configuration Manager, upewnij się, że wszystkie [wymagania wstępne](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) są na miejscu i że ukończono wszystkie wymagane konfiguracje wdrożeniowe.   



##  <a name="BKMK_ClientPush"></a> Jak zainstalować klientów z instalacji wypychanej klienta  

Można skonfigurować wypychaną instalację klienta dla lokacji. Instalacja klienta automatycznie uruchamia na komputerach, które zostały odnalezione w granicach skonfigurowanych dla lokacji, gdy te granice są skonfigurowane jako grupa granic. Można też zainicjować instalację wypychaną klienta, uruchamiając kreatora instalacji wypychanej klienta dla określonej kolekcji lub zasobu wchodzącego w skład kolekcji.  

Można również użyć Kreatora instalacji wypychanej klienta do zainstalowania klienta programu Configuration Manager w celu [zapytania](../../../core/servers/manage/queries-technical-reference.md) wyników. Aby instalacja się powiodła, jednym z elementów zwróconych przez zapytanie musi być atrybut **ResourceID** z klasy **zasób systemowy**.   

Jeśli serwer lokacji nie może skontaktować się z komputerem klienckim lub rozpocząć procesu instalacji, on automatycznie ponawia próbę instalacji co godzinę. Serwer kontynuuje ponawianie prób, przez maksymalnie 7 dni.  

Aby śledzić proces instalacji klienta, należy zainstalować rezerwowy punkt stanu przed zainstalowaniem klientów. Po zainstalowaniu rezerwowy punkt stanu, następuje automatyczne przypisanie do klientów są instalowane przez metody instalacji wypychanej klienta. Aby śledzić postęp instalacji klienta, Wyświetl raporty dotyczące wdrażania i przypisywania klienta. 

Pliki dziennika zapewniają bardziej szczegółowe informacje dotyczące rozwiązywania problemów. Pliki dziennika nie wymagają rezerwowy punkt stanu. Na przykład **CCM.log** pliku na serwerze lokacji są rejestrowane wszelkie problemy z serwera lokacji podczas łączenia się z komputerem. **CCMSetup.log** plik na komputerze klienckim rejestruje proces instalacji.  

> [!IMPORTANT]  
>  Aby wypychanie klienta zakończyło się powodzeniem, należy się upewnić, że wszystkie wymagania wstępne zostały spełnione. Aby uzyskać więcej informacji, zobacz [zależności metod instalacji](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#installation-method-dependencies).  

### <a name="configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>Konfigurowanie lokacji w celu automatyczne stosowanie wypychania klienta do odnalezionych komputerów

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację wypychaną klienta w całej lokacji automatyczne.  

4.  Na **Home** karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **wypychana instalacja klienta**.  

5.  Na **ogólne** karcie **właściwości instalacji wypychanej klienta** okno dialogowe, wybierz opcję **Włącz instalację wypychaną klienta w całej lokacji automatyczne**. Wybierz typy systemów, do których programu Configuration Manager ma wypychać oprogramowanie klienta.  

6.  Określ, czy chcesz zainstalować klienta na kontrolerach domeny.  

7.  Na **kont** karcie, należy określić co najmniej jednego konta dla programu Configuration Manager do użycia podczas połączenia z komputerem docelowym. Kliknij przycisk **Utwórz** ikony, wprowadź **nazwy użytkownika** i **hasło** (nie więcej niż 38 znaków), potwierdź hasło, a następnie kliknij przycisk **OK**. Określ konto instalacji wypychanej co najmniej jednego klienta. To konto musi mieć uprawnienia administratora lokalnego na komputerze docelowym, aby zainstalować klienta. Jeśli nie określisz konta instalacji wypychanej klienta, program Configuration Manager próbuje użyć konta komputera systemu lokacji. Instalacji wypychanej klienta między domenami nie powiedzie się, korzystając z konta komputera systemu lokacji.  
    > [!NOTE]  
    >  Aby wypychania klienta z lokacji dodatkowej, określ konto w lokacji dodatkowej, która inicjuje wypychanie klienta.  
    >   
    >  Aby uzyskać więcej informacji na temat konta instalacji wypychanej klienta, zobacz następną procedurę, [użyć Kreatora instalacji wypychanej klienta](#use-the-client-push-installation-wizard).  

8.  Zakończenie **właściwości instalacji** kartę.

     Jeśli schemat jest rozszerzony dla programu Configuration Manager, lokacja publikuje w usługach domenowych w usłudze Active Directory [właściwości instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md) przez użytkownika na tej karcie. Te właściwości są odczytywane przez instalacje klienta, na których program CCMSetup jest uruchamiany bez właściwości instalacji.  

    > [!NOTE]  
    >  Jeśli włączysz instalację wypychaną klienta w lokacji dodatkowej, upewnij się, że **SMSSITECODE** właściwość jest ustawiona na nazwę lokacji programu Configuration Manager jego nadrzędnej lokacji głównej. Jeśli schemat usługi Active Directory zostanie rozszerzony dla programu Configuration Manager, można również ustawić tę właściwość auto, aby automatycznie znajdować prawidłowe przypisanie lokacji.  

### <a name="use-the-client-push-installation-wizard"></a>Użyj Kreatora instalacji wypychanej klienta

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację wypychaną klienta w całej lokacji automatyczne.  

4.  Na **Home** kartę > **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **wypychana instalacja klienta**.  

5.  Zakończenie **właściwości instalacji** kartę.  

     Jeśli schemat jest rozszerzony dla programu Configuration Manager, lokacja publikuje w usługach domenowych w usłudze Active Directory [właściwości instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md) przez użytkownika na tej karcie. Te właściwości są odczytywane przez instalacje klienta, na których program CCMSetup jest uruchamiany bez właściwości instalacji.   

6.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

7.  W obszarze roboczym **Zasoby i zgodność** zaznacz jeden lub więcej komputerów albo kolekcję komputerów.  

8.  Na **Home** karcie, wybierz jedną z następujących opcji:  

    -   Jeśli chcesz zainstalować klienta na jednym komputerze lub wielu komputerach w **urządzenia** grupy, wybierz **instaluj klienta**.  

    -   Jeśli chcesz zainstalować klienta w kolekcji komputerów, w **kolekcji** grupy, wybierz **instaluj klienta**.  

9. Na **przed rozpoczęciem** strony **Kreatora instalacji klienta**, przejrzyj informacje, a następnie wybierz **dalej**.  

10. Zakończenie **opcje instalacji** strony.  

11. Przejrzyj ustawienia instalacji, po czym zamknij kreatora.  

> [!NOTE]  
>  Kreator służy do instalowania klientów, nawet jeśli witryna sieci Web nie jest skonfigurowana do wypychania klienta.  



##  <a name="BKMK_ClientSUP"></a> Jak instalować klientów z instalacją opartą na aktualizacji oprogramowania  
 Instalacja klienta oparta na aktualizacji oprogramowania publikuje klienta do punktu aktualizacji oprogramowania jako aktualizację oprogramowania. Użyj tej metody instalacji po raz pierwszy lub uaktualnienia.  

 Jeśli na komputerze jest zainstalowany klient programu Configuration Manager, otrzymuje zasady klienta z lokacji. Ta zasada zawiera nazwę serwera punktu aktualizacji oprogramowania i numer portu, z którego można pobrać aktualizacji oprogramowania.   

> [!IMPORTANT]  
>  Aby wykonywać instalację opartą na aktualizacji oprogramowania, należy używać tego samego serwera usług Windows Server Update Services (WSUS) dla instalacji klienta i aktualizacji oprogramowania. Serwer ten musi być aktywnym punktem aktualizacji oprogramowania w lokacji głównej. Aby uzyskać więcej informacji, zobacz [instalacji punktu aktualizacji oprogramowania](../../../sum/get-started/install-a-software-update-point.md).  

Jeśli na komputerze nie ma zainstalowanego klienta programu Configuration Manager, skonfigurować i przypisać obiekt zasad grupy w usługach domenowych Active Directory do określenia nazwy serwera punktu aktualizacji oprogramowania.  

Nie można dodać właściwości wiersza polecenia instalacji klienta opartej na aktualizacji oprogramowania. Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, komputery klienckie automatycznie zapytania usług domenowych Active Directory właściwości instalacji podczas instalacji.  

Jeśli nie rozszerzono schematu usługi Active Directory, można użyć zasad grupy w celu udostępnienia ustawień instalacji klienta na komputerach w lokacji. Te ustawienia są automatycznie stosowane do wszelkich instalacji klienta opartych na aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [jak udostępniać właściwości instalacji klienta (grupy zasad i oprogramowania opartej na aktualizacji instalacji klienta)](#BKMK_Provision) i [jak przypisać klientów do lokacji](../../../core/clients/deploy/assign-clients-to-a-site.md).  

Aktualizacji na użytek poniższe procedury dotyczą konfigurowania komputerów bez klienta programu Configuration Manager do korzystania z aktualizacji oprogramowania punktu instalacji klienta i oprogramowania, a następnie opublikować klienta punktu aktualizacji oprogramowania do oprogramowania.  

> [!NOTE]  
>  Jeśli komputery znajdują się w stanie oczekiwania na ponowne uruchomienie po wcześniejszej instalacji oprogramowania, instalacja klienta w ramach aktualizacji oprogramowania może spowodować ponowne uruchomienie komputera.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>Konfigurowanie obiektów zasad grupy w usługach domenowych Active Directory do określania punktu aktualizacji oprogramowania dla aktualizacji instalacji i oprogramowania klienta:  

1.  Użyj konsoli zarządzania zasadami grupy można otworzyć obiektu zasad grupy do nowego lub istniejącego.  

2.  W konsoli rozwiń węzeł **Konfiguracja komputera**, rozwiń węzeł **Szablony administracyjne**, rozwiń węzeł **składniki systemu Windows**, a następnie wybierz pozycję **usługi Windows Update**.  

3.  Otwórz właściwości ustawienia **Określ lokalizację intranetową usługi aktualizującej firmy Microsoft**, a następnie wybierz pozycję **włączone**.  

4.  W polu **Ustaw intranetową usługę aktualizującą do wykrywania aktualizacji**, określ nazwę i port serwera punktu aktualizacji oprogramowania:  

    -   Jeśli system lokacji programu Configuration Manager jest skonfigurowany do używania w pełni kwalifikowaną nazwą domeny (FQDN), użyj formatu FQDN.  

    -   Jeśli system lokacji programu Configuration Manager nie jest skonfigurowany do używania nazwy FQDN, należy użyć formatu krótkiej nazwy.  

    > [!NOTE]  
    >  Aby określić numer portu, zobacz [jak określić ustawienia portów używane przez program WSUS](../../../sum/plan-design/plan-for-software-updates.md).  

     Przykład: **http://server1.contoso.com:8530**  

5.  W polu **Ustaw serwer statystyk intranetowych**, określ nazwę serwera statystyk intranetowych. Nie musi być taka sama jak serwera punktu aktualizacji oprogramowania. Jeśli ten sam serwer, format nie musi odpowiadać.  

6.  Przypisz obiekt zasad grupy do komputerów, na których chcesz zainstalować klienta i odbierać aktualizacje oprogramowania.  

### <a name="publish-the-configuration-manager-client-to-the-software-update-point"></a>Opublikowanie klienta programu Configuration Manager w punkcie aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację klienta opartą na aktualizacji oprogramowania.  

4.  Na **Home** karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta**, a następnie wybierz pozycję **instalacja klienta**.  

5.  Wybierz **Włącz instalację klienta opartą na aktualizacji oprogramowania**.  

6.  Jeśli oprogramowanie klienta na serwerze lokacji programu Configuration Manager jest wersją nowszą niż wersja w punkcie aktualizacji oprogramowania, **Wykryto nowszą wersję klienta pakietu** zostanie otwarte okno dialogowe. Kliknij przycisk **tak** Aby opublikować najnowszą wersję.  

    > [!NOTE]  
    >  Jeśli oprogramowanie klienckie nie został wcześniej publikowane punktu aktualizacji oprogramowania, to pole jest puste.  

Aktualizacja oprogramowania dla klienta programu Configuration Manager nie zostały zaktualizowane automatycznie po udostępnieniu nowej wersji. W przypadku uaktualnienia lokacji obejmującej nową wersję klienta, powtórz tę procedurę i kliknij przycisk **tak** kroku 6.  



##  <a name="BKMK_ClientGP"></a> Jak instalować klientów przy użyciu zasad grupy  
 Do opublikowania lub przypisania klienta programu Configuration Manager można zainstalować na komputerach w przedsiębiorstwie, można użyć zasad grupy w usługach domenowych w usłudze Active Directory. Klient jest instalowany po uruchomieniu komputera. Jeśli używasz zasad grupy klient jest wyświetlany w Panelu sterowania **Dodaj lub usuń programy** dla użytkownika do zainstalowania.  

 Pakiet Instalatora Windows (CCMSetup.msi) na użytek instalacje oparte na zasadach grupy. Ten plik znajduje się w folderze  **&lt;katalog instalacyjny programu ConfigMgr\>\bin\i386** na serwerze lokacji programu Configuration Manager. Nie można dodać właściwości do tego pliku, aby zmodyfikować zachowanie podczas instalacji.  

> [!IMPORTANT]  
>  Musi mieć uprawnienia administratora na dostęp do plików instalacji klienta.  

-   Jeśli schemat usługi Active Directory zostanie rozszerzony dla programu Configuration Manager i **opublikowania tej witryny w usługach domenowych w usłudze Active Directory** wybrano **zaawansowane** karcie **właściwości lokacji** okno dialogowe, komputery klienckie będą automatycznie przeszukiwać usług domenowych Active Directory właściwości instalacji. Aby uzyskać więcej informacji na temat właściwości instalacji, które są publikowane, zobacz [o właściwościach instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

-   Jeśli schemat usługi Active Directory nie został rozszerzony, można użyć procedury w tym temacie do zapisania właściwości instalacji w rejestrze komputerów: [Jak udostępniać właściwości instalacji klienta (grupy zasad i oprogramowania opartej na aktualizacji instalacji klienta)](#BKMK_Provision). Te właściwości instalacji są używane, gdy klient jest zainstalowany.  

Aby uzyskać informacje o sposobie używania zasad grupy w usługach domenowych w usłudze Active Directory do zainstalowania oprogramowania zapoznaj się z dokumentacją systemu Windows Server.  



##  <a name="BKMK_Manual"></a> Jak instalować klientów ręcznie  
 Można ręcznie zainstalować oprogramowanie klienta na komputerach w przedsiębiorstwie za pomocą programu CCMSetup.exe. Ten program i towarzyszące mu pliki można znaleźć w **klienta** folderu folder instalacji programu Configuration Manager na serwerze lokacji i w punktach zarządzania lokacji. Ten folder jest udostępniany w sieci jako  

 \\\\*&lt;Nazwa serwera lokacji\>*\SMS_*&lt;kod lokacji\>*\Client\  

 gdzie *&lt;nazwa serwera lokacji\>* jest nazwą jednego z serwerów obsługujących punkt zarządzania i *&lt;kod lokacji\>* jest kod lokacji głównej której przypisano klienta. Aby uruchomić program CCMSetup.exe z wiersza polecenia na komputerze klienckim, musisz zamapować dysk sieciowy do tej lokalizacji, a następnie uruchomić to polecenie.  

> [!IMPORTANT]  
>  Musi mieć uprawnienia administratora na dostęp do plików instalacji klienta.  

 CCMSetup.exe kopiuje wszystkie niezbędne wymagania wstępne dotyczące komputera klienckiego i wywołuje pakiet Instalatora Windows (Client.msi), aby zainstalować klienta. Nie można uruchamiać pliku Client.msi bezpośrednio.  

 Aby zmodyfikować zachowanie instalacji klienta, w wierszu polecenia można określić właściwości dla programów CCMSetup.exe i Client.msi. Upewnij się, że możesz określić właściwości programu CCMSetup (właściwości rozpoczynające się od **/**) należy określić przed właściwościami programu Client.msi. Na przykład:  

`CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01`    

a klient zostanie zainstalowany z użyciem następujących właściwości:  

|Właściwość|Opis|  
|--------------|-----------------|  
|**/mp:SMSMP01**|Ta właściwość programu CCMSetup określa, aby punkt zarządzania SMSMP01 pobierał wymagane pliki instalacyjne klienta.|  
|**/logon**|Ta właściwość programu CCMSetup Określa, że instalacja powinna zostać przerwana w przypadku istniejącego klienta programu Configuration Manager znajduje się na komputerze.|  
|**SMSSITECODE = AUTO**|Ta właściwość programu Client.msi Określa, że klient próbuje lokalizować kod lokacji programu Configuration Manager do użycia, przykładowo za pomocą usług domenowych w usłudze Active Directory.|  
|**FSP=SMSFP01**|Ta właściwość programu Client.msi Określa, że rezerwowy punkt stanu o nazwie SMSFP01 jest używany do odbierania komunikatów o stanie wysyłanych z komputera klienckiego.|  

 Aby uzyskać więcej informacji na temat wszystkich właściwości CCMSetup.exe, zobacz [o właściwościach instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md)  

> [!Tip]  
> Procedura instalacji klienta programu Configuration Manager na nowoczesnych urządzeń z systemem Windows 10 przy użyciu tożsamości usługi Azure AD, zobacz [zainstalować i przypisać przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Tej procedury jest przeznaczona dla klientów w intranecie lub Internecie.  


### <a name="examples"></a>Przykłady
 Te przykłady dotyczą klientów usługi Active Directory w intranecie. Korzystają z następujących wartości reprezentujących różne aspekty lokacji:  

 **MPSERVER** = serwer obsługujący punkt zarządzania   
**FSPSERVER** = serwer obsługujący rezerwowy punkt stanu  
**ABC** = kod lokacji  
**contoso.com** = nazwa domeny  

 Wszystkie serwery systemu lokacji są skonfigurowane przy użyciu intranetowej nazwy FQDN. Lokacja jest opublikowana w lesie usługi Active Directory klienta.  

 Na komputerze klienckim Zaloguj się jako administrator lokalny, zamapuj dysk (z:) na\\\MPSERVER\SMS_ABC\Client, Przełącz wiersz polecenia na dysk z, a następnie uruchom jedno z następujących poleceń:  

 **Przykład 1:**  

`CCMSetup.exe`  

W tym przykładzie powoduje zainstalowanie klienta bez dodatkowych właściwości. Klient jest automatycznie konfigurowana właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory. Jest ona automatycznie konfigurowana dla następujących ustawień: 
- Kod lokacji. To ustawienie wymaga, lokalizacji sieciowej klienta mają zostać uwzględnione w grupie granic skonfigurowanej dla przypisania klienta. 
- Punkt zarządzania
- Rezerwowy punkt stanu
- Komunikować się tylko przy użyciu protokołu HTTPS  
  
Aby uzyskać więcej informacji, zobacz [o właściwościach instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 **Przykład 2:**  

`CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com`
  
Ten przykład przedstawia przesłonięcie automatycznej konfiguracji udostępniający w usługach domenowych w usłudze Active Directory. Nie wymaga, że lokalizacja sieciowa klienta znajduje się w grupie granic skonfigurowanej dla przypisania klienta. Zamiast tego instalacja określa następujące ustawienia:
- Kod lokacji
- Intranetowy punkt zarządzania 
- Punkt zarządzania internetowego
- Rezerwowy punkt stanu akceptuje połączenia z Internetu
- Użyj klienta certyfikatu PKI (jeśli jest dostępny), która ma najdłuższym okresie ważności  



##  <a name="BKMK_ClientLogonScript"></a> Jak instalować klientów za pomocą skryptów logowania  
 Program Configuration Manager obsługuje skrypty logowania, aby zainstalować oprogramowanie klienta programu Configuration Manager. Pliku programu **CCMSetup.exe** można użyć w skrypcie logowania do wyzwolenia instalacji klienta.  

 Instalacja skryptu logowania wykorzystuje takie same metody, jak ręczna instalacja klienta. Można określić **/logon** właściwości instalacji w wierszu polecenia programu CCMSsetup.exe. Jeśli jakakolwiek wersja klienta już istnieje na komputerze, ta właściwość uniemożliwi instalację klienta. To zachowanie zapobiega miejsce w każdym uruchomieniu skryptu logowania ponownej instalacji klienta.  

 Jeśli nie zostanie określone nie źródło instalacji przez **/Source** właściwości i żaden punkt zarządzania, z którego można uzyskać instalację, jest określony przez **/MP** właściwość CCMSetup.exe klient zlokalizuje punkt zarządzania za pomocą wyszukiwania w usługach domenowych w usłudze Active Directory. Problem ten występuje tylko, jeśli schemat został rozszerzony dla programu Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory. Alternatywnie klient może zlokalizować punkt zarządzania za pomocą usługi DNS lub WINS.  



##  <a name="BKMK_ClientApp"></a> Jak instalować klientów z pakietem i programem  
 Menedżer konfiguracji można użyć do utworzenia i wdrożenia pakietu oraz programu aktualizującego oprogramowanie klienckie na wybranych komputerach w hierarchii. Plik definicji pakietu, który wypełnia właściwości pakietu najczęściej używanymi wartościami jest dostarczany z programem Configuration Manager. Zachowanie instalacji klienta można dostosować, określając dodatkowych właściwości wiersza polecenia.  

> [!NOTE]  
>  Nie można uaktualnić klientów programu Configuration Manager 2007 przy użyciu tej metody. Zamiast tego należy skorzystać z automatycznego uaktualnienia, które automatycznie utworzy i wdroży pakiet zawierający najnowszą wersję klienta. Aby uzyskać więcej informacji, zobacz [uaktualnienie klientów](../../../core/clients/manage/upgrade/upgrade-clients.md).  
>   
>  Aby uzyskać więcej informacji o migrowaniu ze starszych wersji klienta programu Configuration Manager, zobacz [Planowanie strategii migracji klientów](../../../core/migration/planning-a-client-migration-strategy.md).  

 
### <a name="create-a-package-and-program-for-the-client-software"></a>Utwórz pakiet i program dla oprogramowania klienckiego  

Poniższa procedura umożliwia utworzenie pakietu programu Configuration Manager i programu, można wdrożyć na komputerach klienckich programu Configuration Manager do uaktualnienia oprogramowania klienta.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **pakiety**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz pakiet z definicji**.  

4.  Na **definicja pakietu** strony kreatora wybierz pozycję **Microsoft** z **wydawcy** listy rozwijanej, a następnie wybierz **aktualizacji klienta Configuration Manager** z **definicja pakietu** listy.  

5.  Na **pliki źródłowe** wybierz pozycję **należy zawsze uzyskiwać pliki z folderu źródłowego**.  

6.  Na **Folder źródłowy** wybierz pozycję **ścieżka sieciowa (Nazwa UNC)**. Następnie wprowadź ścieżkę sieciową do komputera i folderu zawierającego pliki instalacyjne klienta.  

    > [!NOTE]  
    >  Komputer, na którym jest uruchomione wdrożenie programu Configuration Manager musi mieć dostęp do folderu sieciowego, który można określić, w przeciwnym razie instalacja nie powiedzie się.  

    Aby zmienić dowolne z właściwości instalacji klienta, należy zmodyfikować parametry wiersza polecenia CCMSetup.exe na **ogólne** karcie **uaktualnienie dyskretne agenta programu Configuration Manager właściwości** okna dialogowego programu pole. Domyślne właściwości instalacji to **/noservice SMSSITECODE=AUTO**.  

9. Pakiet należy rozpowszechnić do wszystkich punktów dystrybucji, które mają hostować pakiet uaktualnienia klienta. Pakiet można następnie wdrożyć do kolekcji komputerów zawierających klientów, które chcesz uaktualnić.  



## <a name="bkmk_mdm"></a>Jak zainstalować klientów na urządzeniach zarządzanych Intune zarządzanie urządzeniami Przenośnymi z systemem Windows

Pliki instalacji klienta można wdrożyć na komputerach, które są zarejestrowane w usłudze Microsoft Intune. 

Ta procedura dotyczy tradycyjnych klienta, który jest połączony z intranetem. Używa metody uwierzytelniania klienta tradycyjnych. Aby upewnić się, że urządzenie pozostaje w stanie zarządzany, po zainstalowaniu oprogramowania klienta, urządzenie musi być w intranecie i w obrębie granicy lokacji programu Configuration Manager.  

Procedura instalacji klienta programu Configuration Manager na nowoczesnych urządzeń z systemem Windows 10 przy użyciu tożsamości usługi Azure AD, zobacz [zainstalować i przypisać przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

> [!NOTE]
> Po zainstalowaniu oprogramowania klienckiego, urządzenie Wyrejestrowanie z usługi Intune.
> 
> Począwszy od wersji 1710, klienci nie wyrejestrowania z usługi Intune. Mogą oni mieć klienta programu Configuration Manager i rejestrowanie MDM, w tym samym czasie. Aby uzyskać więcej informacji, zobacz [zarządzania wspólnej](/sccm/core/clients/manage/co-management-overview).

###  <a name="install-clients-with-intune"></a>Zainstaluj klientów przy użyciu usługi Intune:

1. W usłudze Intune [Utwórz aplikację](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) zawierający plik instalacyjny klienta programu Configuration Manager **ccmsetup.msi**. Ten plik znajduje się w folderze  **&lt;katalog instalacyjny programu ConfigMgr\>\bin\i386** na serwerze lokacji programu Configuration Manager.

2. W polu wydawca oprogramowania usługi Intune wprowadź parametry wiersza polecenia. Na przykład użyć poniższego wiersza polecenia z tradycyjnego klienta w intranecie:

  `CCMSETUPCMD="/MP:&lt;FQDN of management point> SMSMP=&lt;FQDN of management point> SMSSITECODE=&lt;Your site code> DNSSUFFIX=&lt;DNS Suffix of management point>"`  

   > [!Note]  
   > W wierszu polecenia przykład do użycia z nowoczesnymi klienta systemu Windows 10 przy użyciu uwierzytelniania usługi Azure AD, zobacz [urządzenia przygotowanie systemu Windows 10 do zarządzania wspólnej](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).

3. [Wdróż aplikację](/intune/deploy-use/deploy-apps-in-microsoft-intune) na zarejestrowanych komputerach z systemem Windows.



##  <a name="BKMK_ClientImage"></a> Jak zainstalować klientów z obrazu komputera  
Istnieje możliwość wstępnej instalacji oprogramowania klienckiego programu Configuration Manager na komputerze odniesienia, który jest używany do utworzenia obrazu systemu operacyjnego.   

> [!Important]
> Korzystając z sekwencji zadań programu Configuration Manager do wdrażania obrazu systemu operacyjnego [przygotować klienta programu ConfigMgr](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) krok sekwencji zadań Usuwa całkowicie klienta programu Configuration Manager. 

### <a name="prepare-the-client-computer-for-imaging"></a>Przygotowanie komputera klienckiego do utworzenia obrazu  

1.  Ręcznie zainstaluj oprogramowanie klienta programu Configuration Manager na komputerze odniesienia. Więcej informacji znajduje się w temacie [Jak ręcznie instalować klientów programu Configuration Manager](#BKMK_Manual).  

    > [!IMPORTANT]  
    >  Nie można określić kod lokacji programu Configuration Manager dla klienta we właściwościach wiersza polecenia programu CCMSetup.exe.  

2.  W wierszu polecenia wpisz `net stop ccmexec` do upewnij się, że **hosta agenta programu SMS** usługa (Ccmexec.exe) nie jest uruchomiona na komputerze odniesienia.
3.  Usuń plik **SMSCFG. INI** z **Windows** folderu na komputerze odniesienia.  
3.  Usuń wszystkie certyfikaty, które są przechowywane w magazynie komputera lokalnego na komputerze odniesienia. Jeśli przykładowo są używane certyfikaty infrastruktury klucza publicznego (PKI), przed utworzeniem obrazu komputera należy usunąć certyfikaty z magazynu **Osobisty** **Komputera** i **Użytkownika**.

4.  Jeśli klienci są instalowani w innej hierarchii programu Configuration Manager niż komputer odniesienia, Usuń zaufany klucz główny z komputera odniesienia.  
    > [!NOTE]  
    >  Jeśli klienci nie będą mogli wysłać kwerendy do usług Active Directory Domain Services w celu zlokalizowania punktu zarządzania, użyją zaufanego klucza głównego w celu określenia zaufanych punktów zarządzania. Wszyscy klienci w których obraz został utworzony w przypadku wdrożenia w tej samej hierarchii co komputer główny, zaufany klucz główny należy pozostawić w miejscu. Jeśli klienci są wdrożone w różnych hierarchiach, Usuń zaufany klucz główny. Również udostępniać tych klientów z nowym zaufanym kluczem głównym. Aby uzyskać więcej informacji, zobacz [planowanie zaufanego klucza głównego](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK). 

5.  Użyj oprogramowania do tworzenia obrazu, aby przechwycić obraz komputera głównego.  

6.  Wdróż obraz na komputerach docelowych.  



##  <a name="BKMK_ClientWorkgroup"></a> Jak zainstalować klientów na komputerach grupy roboczej  
 Program Configuration Manager obsługuje instalacji klienta na komputerach grupy roboczej. Klientów na komputerach grupy roboczej można zainstalować, korzystając z metody podanej w sekcji [Jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual).  

 Wymagania wstępne:  

-   Na każdym komputerze grupy roboczej należy zainstalować klienta ręczne. Podczas instalacji zalogowany użytkownik musi mieć prawa administratora lokalnego.  

-   Aby uzyskać dostęp do zasobów w domenie serwera lokacji programu Configuration Manager, konto dostępu do sieci musi być skonfigurowana dla witryny. To konto można określić jako właściwość składnika dystrybucji oprogramowania. Aby uzyskać więcej informacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

 Ograniczenia:  

-   Klienci grupy roboczej nie mogą lokalizować punktów zarządzania z usług Active Directory Domain Services i zamiast tego muszą używać serwera DNS, WINS lub innego punktu zarządzania.  

-   Roaming globalny nie jest obsługiwany, ponieważ klienci nie mogą wysyłać kwerend do usług domenowych w usłudze Active Directory w celu uzyskania informacji o lokacji.  

-   Metody odnajdywania w usłudze Active Directory nie mogą odnajdywać komputerów grup roboczych.  

-   Nie można wdrożyć oprogramowania na kontach użytkowników komputerów grupy roboczej.  

-   Nie można użyć metody instalacji wypychanej klienta w celu zainstalowania klientów na komputerach grupy roboczej.  

-   Klienci grupy roboczej nie można użyć protokołu Kerberos do uwierzytelniania i może wymagać ręcznego zatwierdzania.  

-   Klienta grupy roboczej nie można skonfigurować jako punktu dystrybucji. Program Configuration Manager wymaga, aby komputery punktu dystrybucji były członkami domeny.  

### <a name="install-the-client-on-workgroup-computers"></a>Zainstaluj klienta na komputerach grupy roboczej  

Sprawdź wymagania wstępne, a następnie postępuj zgodnie z instrukcjami w sekcji [jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual).  

   Polecenie podane w tym przykładzie powoduje zainstalowanie klienta w celu zarządzania klientami przez intranet i określenie kodu lokacji oraz sufiksu DNS lokalizacji punktu zarządzania. `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com`  

     

   W tym przykładzie wymaga klient znajdował się w lokalizacji sieciowej, która jest skonfigurowana w grupie granic. To wymaganie dotyczy automatycznego przypisania lokacji powiodło się. Polecenie zawiera rezerwowy punkt stanu elementu FSPSERVER serwera. Ta właściwość umożliwia śledzenie wdrażania klientów, a do komunikacji z klientem zidentyfikować problemy. 
   `CCMSetup.exe FSP=fspserver.constoso.com`  

      

##  <a name="BKMK_ClientInternet"></a> Jak zainstalować klientów do zarządzania internetowego  
 
> [!Note]
> Ta sekcja nie ma zastosowania do klientów przy użyciu [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Aby zainstalować klientów internetowych przy użyciu bramy zarządzania chmury, zobacz [zainstalować i przypisać przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

Gdy lokacja programu Configuration Manager obsługuje [zarządzania klientami internetowymi](/sccm/core/clients/manage/plan-internet-based-client-management) dla klientów, którzy czasem w intranecie, a czasem z Internetem, dostępne są dwie opcje instalacji klientów w intranecie:  

-   Można dodać właściwość pliku Client.msi ccmhostname =*&lt;internet FQDN punktu zarządzania internetowego\>*  po zainstalowaniu klienta, na przykład za pomocą ręcznej lub instalacji wypychanej klienta. Jeżeli używana jest ta metoda, należy także bezpośrednio przypisać klienta do lokacji i nie można użyć automatycznego przypisywania lokacji. [Jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual) w tym temacie zawiera przykład tej metody konfiguracji.  

-   Można zainstalować klienta dla zarządzania klientami w sieci intranet, a następnie przypisać punkt zarządzania klientami internetowymi do klienta. Zmień punkt zarządzania za pomocą właściwości klienta programu Configuration Manager w Panelu sterowania lub za pomocą skryptu. Jeżeli stosowana jest ta metoda, można użyć automatycznego przypisania klienta. Aby uzyskać więcej informacji, zobacz [Konfigurowanie klientów do zarządzania internetowego po instalacji klienta](#BKMK_ConfigureIBCM_MP) w tym temacie.  

 Jeżeli konieczne jest zainstalowanie klientów, którzy są połączeni z Internetem, wybierz jedną z następujących obsługiwanych metod:  

-   Mechanizm umożliwiający tych klientów, aby tymczasowo łączenia się z intranetem, korzystając z sieci VPN. Następnie należy zainstalować klienta przy użyciu dowolnej metody instalacji odpowiedniego klienta.  

-   Użyj metody instalacji, która jest niezależna od programu Configuration Manager. Na przykład pakiet plików źródłowych instalacji klienta na nośniku wymiennym, który można wysłać do użytkowników z instrukcjami instalacji. Pliki źródłowe instalacji klienta znajdują się w  *&lt;Ścieżka_instalacji\>*folderu \Client na punktach serwera oraz zarządzania lokacji programu Configuration Manager. Umieść na nośniku skrypt ręcznego kopiowania do i z folderu klienta, zainstaluj klienta, używając programu CCMSetup.exe i wszystkie odpowiednie właściwości wiersza polecenia programu CCMSetup.  

> [!NOTE]  
>  Program Configuration Manager nie obsługuje instalacji klienta bezpośrednio z punktu zarządzania internetowego ani z punktu aktualizacji oprogramowania z internetowego.  

 Klienci zarządzani przez internet muszą komunikować się z systemami lokacji z Internetu. Upewnij się, że ci klienci także mają certyfikatów infrastruktury kluczy publicznych (PKI), przed zainstalowaniem klienta. Zainstaluj tych certyfikatów niezależnie z programu Configuration Manager. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI](../../../core/plan-design/network/pki-certificate-requirements.md).  

### <a name="install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>Instalowanie klientów w Internecie, określając właściwości wiersza polecenia programu CCMSetup  

1.  Postępuj zgodnie z instrukcjami w sekcji [jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual) , zawsze podając następujące:  

    -   Właściwość wiersza polecenia programu CCMSetup **/source: ***&lt;ścieżka lokalna do skopiowanego folderu klienta\>*  

    -   Właściwość wiersza polecenia **/UsePKICert** programu CCMSetup  

    -   Właściwość pliku Client.msi **CCMHOSTNAME = ***&lt;FQDN punktu zarządzania internetowego\>*  

    -   Właściwość pliku Client.msi **SMSSIGNCERT = ***&lt;ścieżka lokalna do serwera lokacji wyeksportowanego certyfikatu podpisywania\>*  

    -   Właściwość pliku Client.msi **SMSSITECODE = ***&lt;kod punktu zarządzania internetowego lokacji\>*  

    > [!NOTE]  
    >  Jeśli witryna ma więcej niż jeden punkt zarządzania internetowego, nie ma znaczenia, których punkt zarządzania internetowego, określ dla właściwości CCMHOSTNAME. Gdy klient programu Configuration Manager łączy się z określonym internetowym punktem zarządzania, punkt zarządzania wysyła klientowi w witrynie listę dostępnych internetowych punktów zarządzania. Klient losowo wybiera z listy.  

2.  Jeżeli nie chcesz, aby klient sprawdzał listę odwołania certyfikatów (CRL, certificate revocation list), określ właściwość wiersza polecenia **/NoCRLCheck** programu CCMSetup.  

3.  Jeśli używane jest internetowy rezerwowy punkt stanu, określ właściwość pliku Client.msi **FSP = ***&lt;internet FQDN internetowego rezerwowego punktu stanu\>*.  

4.  Jeśli instalujesz klienta dla zarządzania klientami tylko przez internet, określ właściwość pliku Client.msi **CCMALWAYSINF = 1**.  

5.  Sprawdź, czy masz do określenia dodatkowych właściwości wiersza polecenia programu CCMSetup. Może być konieczne na przykład określić kryteria wyboru certyfikatu, jeżeli klient ma więcej niż jeden ważny certyfikat PKI. Aby uzyskać listę dostępnych właściwości, zobacz [o właściwościach instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md).  

   Przykład:  
   `CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1`    

   W tym przykładzie powoduje zainstalowanie klienta z następujących problemów:
   - Użyj plików źródłowych z folderu na dysku D
   - Używany certyfikat PKI klienta 
   - Wybierz certyfikat o najdłuższym okresie ważności 
   - Zarządzania klientami tylko przez Internet
   - Przypisanie klienta do korzystania z punktu zarządzania internetowego o nazwie SERVER1
   - Przypisać internetowy rezerwowy punkt stanu w domenie contoso.com
   - Przypisywanie klienta do lokacji ABC  

###  <a name="BKMK_ConfigureIBCM_MP"></a>Aby skonfigurować klientów do zarządzania internetowego po instalacji klienta  
 Aby przypisać punkt zarządzania internetowego po zainstalowaniu klienta, użyj jednej z tych procedur. Pierwszy wymaga ręcznej konfiguracji i jest odpowiednia dla niewielkiej liczby klientów. Druga jest bardziej odpowiednie do konfigurowania wielu klientów.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Konfigurowanie klientów do zarządzania internetowego po instalacji klienta, przypisując punkt zarządzania internetowego we właściwościach programu Configuration Manager  

1.  Przejdź do apletu **Configuration Manager** w Panelu sterowania na komputerze klienckim, a następnie kliknij go dwukrotnie, aby otworzyć jego właściwości.  

2.  Na **Internet** wprowadź w pełni kwalifikowaną nazwę punktu zarządzania internetowego w Internecie FQDN pola tekstowego.  

    > [!NOTE]  
    >  Karta **Internet** jest dostępna tylko wtedy, gdy klient ma certyfikat PKI.  

3.  Jeśli klient uzyskuje dostęp do Internetu za pomocą serwera proxy, wprowadź ustawienia serwera proxy.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>Konfigurowanie klientów do zarządzania internetowego po instalacji klienta za pomocą skryptu  

1.  Otwórz edytor tekstu, na przykład Notatnik.  

2.  Skopiuj i wstaw poniższy przykładowy skrypt VBScript do pliku. Zastąp *mp.contoso.com* internetowej nazwy FQDN punktu zarządzania internetowego.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the internet-based management point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  Jeśli konieczne jest usunięcie określonego internetowego punktu zarządzania, aby klient nie jest skonfigurowany do użycia punktu zarządzania internetowego, usuń wartość w cudzysłowach, aby wiersz miał postać: `newInternetBasedManagementPointFQDN = ""`  

4.  Zapisz plik z rozszerzeniem vbs.  

5.  Użyj cscript.exe do uruchamiania skryptu na komputerach klienckich, używając jednej z następujących metod:  

    -   Wdróż plik na istniejących klientach programu Configuration Manager, używając pakietu i programu.  

    -   Uruchom plik lokalnie na istniejących klientach programu Configuration Manager, klikając dwukrotnie plik skryptu w Eksploratorze Windows.  

 Może być konieczne ponowne uruchomienie klienta, aby zmiany zaczęły obowiązywać.  



##  <a name="BKMK_Provision"></a> Jak udostępniać właściwości instalacji klienta (grupy zasad i oprogramowania opartej na aktualizacji instalacji klienta)  
 Można użyć zasad grupy systemu Windows w celu udostępniania komputerów z właściwości instalacji klienta programu Configuration Manager. Te właściwości są przechowywane w rejestrze komputera i są odczytywane po zainstalowaniu oprogramowania klienckiego. Ta procedura nie jest zazwyczaj wymagane, ale mogą być wymagane dla niektórych scenariuszy instalacji klienta, takich jak:  

-   Używasz zasad grupy lub metody instalacji klienta opartej na aktualizacji oprogramowania. Nie zostało to jeszcze rozszerzenia schematu usługi Active Directory dla programu Configuration Manager.  

-   Wymagane jest zastąpienie właściwości instalacji klienta na określonych komputerach.  

> [!NOTE]  
>  Jeśli wszelkie właściwości instalacji są podane w wierszu polecenia programu CCMSetup.exe, właściwości instalacji udostępnione na komputerach nie są używane.  

 Szablon administracyjny zasad grupy o nazwie ConfigMgrInstallation.adm jest dostarczony na nośniku instalacyjnym programu Configuration Manager. Ten szablon może służyć do udostępnienia na komputerach właściwości instalacji klienta.   

### <a name="configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>Skonfigurować i przypisać właściwości instalacji klienta za pomocą obiektu zasad grupy  

1.  Zaimportuj szablon administracyjny ConfigMgrInstallation.adm do nowego lub istniejącego obiektu zasad grupy, używając edytora, takie jak Windows Edytor obiektów zasad grupy. Plik znajduje się w folderze **TOOLS\ConfigMgrADMTemplates** na nośniku instalacyjnym programu Configuration Manager.  

2.  Otwórz właściwości zaimportowanego ustawienia **Konfiguruj ustawienia wdrażania klienta**.  

3.  Wybierz **włączone**.  

4.  W polu **CCMSetup** wprowadź wymagane właściwości wiersza polecenia programu CCMSetup. Aby uzyskać listę wszystkich właściwości wiersza polecenia programu CCMSetup i przykłady ich użycia, zobacz [o właściwościach instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md).  

5.  Przypisz obiekt zasad grupy do komputerów, które chcesz udostępnić właściwości instalacji klienta programu Configuration Manager.  

Aby uzyskać informacje dotyczące zasad grupy systemu Windows zapoznaj się z dokumentacją systemu Windows Server.  



## <a name="next-steps"></a>Następne kroki
Aby uzyskać więcej pomocy dotyczącej instalowania klienta programu Configuration Manager, zobacz [metody instalacji klientów](../../../core/clients/deploy/plan/client-installation-methods.md).