---
title: "Wdrażanie klientów Windows | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 83878b71b876c725920b228190000fc849a063db
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed zainstalowaniem klientów programu Configuration Manager, upewnij się, że wszystkie [wymagania wstępne](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) są spełnione i że ukończono wszystkie wymagane konfiguracje wdrożeniowe.   

##  <a name="BKMK_ClientPush"></a>Jak instalować klientów za pomocą wypychania klienta  

Instalację wypychaną klienta można skonfigurować dla całej lokacji, a wtedy instalacja klienta zostanie automatycznie uruchomiona na komputerach odnalezionych w skonfigurowanych granicach lokacji, o ile te granice są skonfigurowane jako grupa granic. Można też zainicjować instalację wypychaną klienta, uruchamiając kreatora instalacji wypychanej klienta dla określonej kolekcji lub zasobu wchodzącego w skład kolekcji.  

Umożliwia także Kreatora instalacji wypychanej klienta do zainstalowania klienta programu Configuration Manager do [kwerendy](../../../core/servers/manage/queries-technical-reference.md) wyników. Aby instalacja się powiodła, jednym z elementów zwróconych przez zapytanie musi być atrybut **ResourceID** z klasy **zasób systemowy**.   

Jeżeli serwer lokacji nie można skontaktować się z komputerem klienta lub rozpocząć procesu instalacji, będzie automatycznie powtarzać próbę instalacji co godzinę przez okres do 7 dni.  

Aby pomóc sobie w śledzeniu procesu instalacji klienta, przed instalacją klientów można zainstalować system lokacji rezerwowego punktu stanu. Rezerwowy punkt stanu po zainstalowaniu zostaje automatycznie przypisany do klientów podczas ich instalowania metodą instalacji wypychanej klienta. Aby śledzić postęp instalacji klienta, można przeglądać raporty z wdrażania i przypisywania klienta. 

Pliki dziennika klienta więcej szczegółowych informacji o rozwiązywaniu problemów i nie wymagają rezerwowego punktu stanu. Na przykład w pliku CCM.log na serwerze lokacji są rejestrowane wszelkie problemy łączności z komputerem, jakie zdarzają się serwerowi lokacji, podczas gdy w pliku CCMSetup.log na kliencie jest rejestrowany proces instalacji.  

> [!IMPORTANT]  
>  Aby wypychanie klienta zakończyło się powodzeniem, należy się upewnić, że wszystkie wymagania wstępne zostały spełnione. Są one wymienione w sekcji "Zależności metod instalacji" w [wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md).  

### <a name="to-configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>Aby skonfigurować dla danej lokacji automatyczne stosowanie wypychania klienta do odnalezionych komputerów

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację wypychaną klienta całej lokacji.  

4.  Na **Home** w karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **instalacji wypychanej klienta**.  

5.  Na **ogólne** na karcie **właściwości instalacji wypychanej klienta** okno dialogowe, wybierz opcję **włączysz instalację wypychaną klienta w całej lokacji automatyczne**. Wybierz typy systemów, do których program Configuration Manager ma wypychać oprogramowanie klienta.  

6.  Wybierz, czy chcesz zainstalować klienta na kontrolerach domeny.  

7.  Na **kont** Określ co najmniej jednego konta dla programu Configuration Manager do użycia podczas łączenia się z komputerem, do zainstalowania oprogramowania klienta. Kliknij przycisk **Utwórz** ikony, wprowadź **nazwa użytkownika** i **hasło** (nie więcej niż 38 znaków), potwierdź hasło, a następnie kliknij przycisk **OK**. Należy określić co najmniej jedno konto instalacji klienta w trybie wypychania, które musi mieć prawa administratora lokalnego na każdym komputerze, na którym chcesz zainstalować klienta. Jeśli nie określisz konto instalacji wypychanej klienta programu Configuration Manager próbuje użyć konta komputera systemu lokacji, co powoduje wypychanie klienta między domenami zakończyło się niepowodzeniem.  

    
    > [!NOTE]  
    >  Jeśli planujesz użyć metody instalacji wypychanej klienta z lokacji dodatkowej, konto musi zostać określone w tej lokacji dodatkowej, która inicjuje wypychanie klienta.  
    >   
    >  Aby uzyskać więcej informacji o koncie instalacji wypychanej klienta Zobacz następną procedurę, "Aby użyć Kreatora instalacji wypychanej klienta".  

8.  Ukończ **właściwości instalacji** kartę.

     [Właściwości instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md) określono na tej karcie są publikowane w usługach domenowych w usłudze Active Directory, jeśli schemat został rozszerzony dla programu Configuration Manager i odczytywane przez instalacje klientów po uruchomieniu programu CCMSetup bez właściwości instalacji.  

    > [!NOTE]  
    >  Jeśli włączysz instalację wypychaną klienta w lokacji dodatkowej, upewnij się, że właściwość SMSSITECODE jest ustawiona na nazwę lokacji programu Configuration Manager nadrzędnej lokacji głównej. Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, należy również wybrać tę wartość AUTO, aby automatycznie znajdować prawidłowe przypisanie lokacji.  

### <a name="to-use-the-client-push-installation-wizard"></a>Aby użyć kreatora instalacji wypychanej klienta

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację wypychaną klienta całej lokacji.  

4.  Na **Home** kartę > **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **instalacji wypychanej klienta**.  

5.  Ukończ **właściwości instalacji** kartę.  

     [Właściwości instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md) określono na tej karcie są publikowane w usługach domenowych w usłudze Active Directory, jeśli schemat został rozszerzony dla programu Configuration Manager i odczytywane przez instalacje klientów po uruchomieniu programu CCMSetup bez właściwości instalacji.  

6.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

7.  W obszarze roboczym **Zasoby i zgodność** zaznacz jeden lub więcej komputerów albo kolekcję komputerów.  

8.  Na karcie **Narzędzia główne** wykonaj jedną z poniższych czynności:  

    -   Jeśli chcesz zainstalować klienta na jednym lub większej liczby komputerów w **urządzenia** grupy, wybierz **instaluj klienta**.  

    -   Jeśli chcesz zainstalować klienta w kolekcji komputerów, w **kolekcji** grupy, wybierz **instaluj klienta**.  

9. Na **przed rozpoczęciem** strony **Kreatora instalacji klienta**, przejrzyj informacje, a następnie wybierz **dalej**.  

10. Ukończ **opcje instalacji** strony.  

11. Przejrzyj ustawienia instalacji, po czym zamknij kreatora.  

> [!NOTE]  
>  Możesz używać tego kreatora do instalowania klientów nawet jeśli dana lokacja nie została skonfigurowana do wypychania klienta.  

##  <a name="BKMK_ClientSUP"></a>Jak instalować klientów z instalacją opartą na aktualizacji oprogramowania  
 Instalacja klienta oparta na aktualizacji oprogramowania publikuje klienta do punktu aktualizacji oprogramowania jako aktualizację oprogramowania. Ta metoda instalacji po raz pierwszy lub uaktualnienia.  

 Jeśli na komputerze jest zainstalowany klient, Configuration Manager udostępnia klienta z zasadami klienta, który zawiera nazwę serwera punktu aktualizacji oprogramowania i numer portu, z którego ma pobrać aktualizacje oprogramowania.   

> [!IMPORTANT]  
>  Aby wykonywać instalację opartą na aktualizacji oprogramowania, należy używać tego samego serwera usług Windows Server Update Services (WSUS) dla instalacji klienta i aktualizacji oprogramowania. Serwer ten musi być aktywnym punktem aktualizacji oprogramowania w lokacji głównej. Aby uzyskać więcej informacji, zobacz [zainstalować punkt aktualizacji oprogramowania](../../../sum/get-started/install-a-software-update-point.md).  

Jeśli komputer nie ma zainstalowanego klienta programu Configuration Manager, należy skonfigurować i przypisać obiekt zasad grupy (GPO) w usługach domenowych Active Directory do określenia nazwy serwera punktu aktualizacji oprogramowania.  

Do instalacji klienta opartej na aktualizacji oprogramowania nie można dodawać właściwości wiersza polecenia. Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, komputery klienckie automatycznie zapytania usług domenowych Active Directory właściwości instalacji podczas instalacji.  

Jeżeli schemat usługi Active Directory nie został rozszerzony, to można użyć zasad grupy do udostępnienia ustawień instalacji klienta komputerom w danej lokacji. Te ustawienia są automatycznie stosowane do wszelkich instalacji klienta opartych na aktualizacji oprogramowania. Więcej informacji znajduje się w tematach [Jak udostępniać właściwości instalacji klienta (Zasady grupy i instalacja klienta oparta na aktualizacji oprogramowania)](#BKMK_Provision) oraz [Jak przypisywać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

Użyj punktu poniższe procedury dotyczą konfigurowania komputerów bez klienta programu Configuration Manager do korzystania z aktualizacji oprogramowania dla instalacji klienta i oprogramowania, aktualizacji i publikacji klienta punktu aktualizacji oprogramowania do oprogramowania.  

> [!NOTE]  
>  Jeśli komputery znajdują się w stanie oczekiwania na ponowne uruchomienie po wcześniejszej instalacji oprogramowania, instalacja klienta w ramach aktualizacji oprogramowania może spowodować ponowne uruchomienie komputera.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>Skonfiguruj obiekt zasad grupy w usługach domenowych Active Directory do określania punktu aktualizacji oprogramowania dla aktualizacji oprogramowania i instalacji klienta:  

1.  Użyj konsoli zarządzania zasadami grupy, aby otworzyć nowy lub istniejący obiekt zasad grupy.  

2.  W konsoli rozwiń **konfiguracji komputera**, rozwiń węzeł **Szablony administracyjne**, rozwiń węzeł **składniki systemu Windows**, a następnie wybierz **usługi Windows Update**.  

3.  Otwórz właściwości ustawienia **Określ lokalizację intranetową usługi aktualizującej firmy Microsoft**, a następnie wybierz **włączone**.  

4.  W polu **Ustaw intranetową usługę aktualizującą do wykrywania aktualizacji**, określ nazwę i port serwera punktu aktualizacji oprogramowania:  

    -   Jeśli system lokacji programu Configuration Manager jest skonfigurowany do używania w pełni kwalifikowaną nazwę domeny (FQDN), użyj formatu FQDN.  

    -   Jeśli system lokacji programu Configuration Manager nie jest skonfigurowany do używania nazwy FQDN, należy użyć krótkiej nazwy formatu.  

    > [!NOTE]  
    >  Aby określić numer portu, zobacz [Określanie ustawień portów używanych przez program WSUS w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

     Przykład: **http://server1.contoso.com:8530**  

5.  W polu **Ustaw serwer statystyk intranetowych**, określ nazwę serwera statystyk intranetowych. Nie musi być taka sama jak serwer punktu aktualizacji oprogramowania i format nie musi odpowiadać, jeśli jest tym samym serwerze.  

6.  Przypisz obiekt zasad grupy do komputerów, na których chcesz zainstalować klienta i odbierać aktualizacje oprogramowania.  

### <a name="to-publish-the-configuration-manager-client-to-the-software-update-point"></a>Aby opublikować klienta programu Configuration Manager w punkcie aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować instalację klienta opartą na aktualizacji oprogramowania.  

4.  Na **Home** w karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta**, a następnie wybierz **instalacja klienta**.  

5.  Wybierz **Włącz instalację klienta opartą na aktualizacji oprogramowania**.  

6.  Jeśli oprogramowanie klienckie na serwerze lokacji programu Configuration Manager jest wersją nowszą niż punkt, który oprogramowania aktualizacji **Wykryto nowszą wersję klienta pakietu** zostanie otwarte okno dialogowe. Kliknij przycisk **tak** Aby opublikować najnowszą wersję.  

    > [!NOTE]  
    >  Jeśli oprogramowanie klienta nie został wcześniej publikowane punkt aktualizacji oprogramowania, to okno będzie puste.  

Aktualizacja oprogramowania dla klienta programu Configuration Manager nie jest aktualizowana automatycznie wraz z pojawieniem się nowej wersji. W przypadku uaktualnienia lokacji obejmującej nową wersję klienta należy powtórzyć powyższą procedurę, w kroku 6 klikając przycisk **Tak**.  

##  <a name="BKMK_ClientGP"></a>Jak instalować klientów za pomocą zasad grupy  
 Zasady grupy w usługach domenowych w usłudze Active Directory służy do opublikowania lub przypisania klienta programu Configuration Manager do zainstalowania na komputerach w przedsiębiorstwie. Klient zostanie zainstalowany podczas uruchamiania komputera. Przy użyciu zasad grupy klient jest wyświetlany w Panelu sterowania **Dodaj lub usuń programy** użytkownika do zainstalowania.  

 Instalacje oparte na zasadach grupy należy wykonywać za pomocą pakietu Instalatora Windows (CCMSetup.msi). Ten plik znajduje się w folderze  **&lt;katalogu instalacyjnego programu ConfigMgr\>\bin\i386** na serwerze lokacji programu Configuration Manager. Nie można dodać właściwości do tego pliku, aby zmodyfikować zachowanie podczas instalacji.  

> [!IMPORTANT]  
>  Musi mieć uprawnienia administratora, aby uzyskać dostęp do plików instalacyjnych klienta.  

-   Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager i **opublikować tę witrynę w usługach domenowych w usłudze Active Directory** wybrano **zaawansowane** na karcie **właściwości lokacji** okno dialogowe, komputery klienckie będą automatycznie przeszukiwać usług domenowych Active Directory właściwości instalacji. Więcej informacji o publikowanych właściwościach instalacji znajduje się w temacie [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

-   Jeśli schemat usługi Active Directory nie został rozszerzony, służy procedury w tym temacie do zapisania właściwości instalacji w rejestrze komputerów: [Jak udostępniać właściwości instalacji klienta (instalacja klienta oparta na aktualizacji oprogramowania i zasadami grupy)](#BKMK_Provision). Te właściwości instalacji będzie służyć podczas instalowania klienta.  

Informacje o sposobach używania zasad grupy w usługach domenowych Active Directory do instalowania oprogramowania znajdują się w dokumentacji systemu Windows Server.  

##  <a name="BKMK_Manual"></a>Jak ręcznie instalować klientów  
 Można ręcznie zainstalować oprogramowanie klienta na komputerach w przedsiębiorstwie za pomocą programu CCMSetup.exe. Ten program i towarzyszące mu pliki można znaleźć w **klienta** folderu folder instalacji programu Configuration Manager na serwerze lokacji i w punktach zarządzania w danej lokacji. Ten folder jest udostępniany w sieci jako  

 \\\\*&lt;Nazwa serwera witryny\>*\SMS_*&lt;kod lokacji\>*\Client\  

 gdzie  *&lt;nazwa serwera lokacji\>*  jest nazwą jednego z serwerów obsługujących punkt zarządzania i  *&lt;kod lokacji\>*  jest kod dla lokacji głównej klienta będzie znajdować się.  Aby uruchomić program CCMSetup.exe z wiersza polecenia na komputerze klienckim, musisz zamapować dysk sieciowy do tej lokalizacji, a następnie uruchomić to polecenie.  

> [!IMPORTANT]  
>  Musi mieć uprawnienia administratora, aby uzyskać dostęp do plików instalacyjnych klienta.  

 CCMSetup.exe kopiuje wszelkie niezbędne wymagania wstępne na komputerze klienckim i wywołuje pakiet Instalatora Windows (Client.msi) w celu instalacji klienta. Pliku Client.msi nie można modyfikować bezpośrednio.  

 Aby zmodyfikować zachowanie instalacji klienta, w wierszu polecenia można określić właściwości dla programów CCMSetup.exe i Client.msi. Upewnij się, że możesz określić właściwości programu CCMSetup (właściwości rozpoczynające się od  **/** ) należy określić przed właściwościami programu Client.msi. Na przykład:  

```  
CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01  
```  
a klient zostanie zainstalowany z użyciem następujących właściwości:  

|Właściwość|Opis|  
|--------------|-----------------|  
|**smsmp01**|Ta właściwość programu CCMSetup określa, aby punkt zarządzania SMSMP01 pobierał wymagane pliki instalacyjne klienta.|  
|**/logon**|Ta właściwość programu CCMSetup Określa, że instalacja powinna zostać przerwana w przypadku istniejącego klienta programu Configuration Manager znajduje się na komputerze.|  
|**SMSSITECODE = AUTO**|Ta właściwość programu Client.msi Określa, że klient próbuje lokalizować kod lokacji programu Configuration Manager do użycia, na przykład za pomocą usług domenowych w usłudze Active Directory.|  
|**FSP = SMSFP01**|Ta właściwość programu Client.msi określa, że do odbierania komunikatów o stanie wysyłanych z komputera klienckiego będzie używany punkt stanu przełączania awaryjnego o nazwie SMSFP01.|  

 Aby uzyskać szczegółowe informacje na temat wszystkich właściwości programu CCMSetup.exe, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md)  

### <a name="examples"></a>Przykłady
 Poniższe przykłady dotyczą klientów usługi Active Directory w intranecie. Użyj następujących wartości reprezentujących różne aspekty lokacji:  

 **MPSERVER** = serwer obsługujący punkt zarządzania   
**FSPSERVER** = serwer obsługujący rezerwowy punkt stanu  
**ABC** = kod lokacji  
**contoso.com** = nazwa domeny  

 Wszystkie serwery systemu lokacji są skonfigurowane przy użyciu intranetowej nazwy FQDN, a lokacja jest opublikowana w lesie usługi Active Directory klienta.  

 Na komputerze klienckim, zaloguj się jako administrator lokalny, zamapuj dysk (z:) na\\\MPSERVER\SMS_ABC\Client, przełącz się na dysku z wiersza polecenia, a następnie uruchom jedno z następujących poleceń.  

 **Przykład 1:**  

```  
CCMSetup.exe  
```  
W tym przykładzie instaluje klienta bez dodatkowych właściwości, dzięki czemu jest automatycznie konfigurowany za pomocą właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory. Na przykład na kliencie jest automatycznie konfigurowane kod lokacji (wymaga lokalizacji sieciowej klienta mają zostać uwzględnione w grupie granic skonfigurowanej dla przypisania klienta), punkt zarządzania, rezerwowy punkt stanu, oraz czy klient musi komunikować się tylko przy użyciu protokołu HTTPS. Więcej informacji na temat właściwości instalacji klienta, które można automatycznie skonfigurować dla klientów usługi Active Directory, znajduje się w temacie [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 **Przykład 2:**  

```  
CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com  
```  
Ten przykład przedstawia przesłonięcie automatycznej konfiguracji zapewnianej usług domenowych w usłudze Active Directory, i nie wymaga uwzględnienia lokalizacji sieciowej klienta w grupie granic skonfigurowanej dla przypisania klienta. Zamiast tego instalacja określa lokację, intranetowy punkt zarządzania i internetowy punkt zarządzania, rezerwowy punkt stanu akceptujący połączenia z Internetu oraz użycie certyfikatu PKI klienta (jeśli jest dostępny) o najdłuższym okresie ważności.  

##  <a name="BKMK_ClientLogonScript"></a>Jak instalować klientów za pomocą skryptów logowania  
 Program Configuration Manager obsługuje skrypty logowania do zainstalowania oprogramowania klienta programu Configuration Manager. Pliku programu **CCMSetup.exe** można użyć w skrypcie logowania do wyzwolenia instalacji klienta.  

 Instalacja skryptu logowania wykorzystuje takie same metody, jak ręczna instalacja klienta. W wierszu polecenia programu CCMSetup.exe można podać właściwość instalacji **/logon**, która uniemożliwi instalację klienta, jeśli dowolna z wersji klienta już istnieje na komputerze. W ten sposób można zapobiec przeprowadzaniu ponownej instalacji przy każdym uruchomieniu skryptu logowania.  

 Jeśli zostanie określone żadne źródło instalacji korzystające **/Source** właściwości i żaden punkt zarządzania, z którego będzie można uzyskać instalację jest określony za pomocą **/MP** właściwości CCMSetup.exe mogą zlokalizować punkt zarządzania, wyszukując usługi domenowe Active Directory, jeśli schemat został rozszerzony dla programu Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory. Alternatywnie klient może zlokalizować punkt zarządzania za pomocą usługi DNS lub WINS.  

##  <a name="BKMK_ClientApp"></a>Jak instalować klientów za pomocą pakietu i programu  
 Program Configuration Manager służy do tworzenia i wdrażania pakietu oraz programu aktualizującego oprogramowanie klienckie na wybranych komputerach w hierarchii. Plik definicji pakietu, który wypełnia właściwości pakietu najczęściej używanymi wartościami jest dostarczany z programem Configuration Manager. Zachowanie klienta można dostosować, wprowadzając dodatkowe właściwości w wierszu poleceń.  

> [!NOTE]  
>  Nie można uaktualnić klientów programu Configuration Manager 2007 przy użyciu tej metody. Zamiast tego należy skorzystać z automatycznego uaktualnienia, które automatycznie utworzy i wdroży pakiet zawierający najnowszą wersję klienta. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md).  
>   
>  Aby uzyskać więcej informacji o sposobach migracji ze starszych wersji klienta programu Configuration Manager, zobacz [Planowanie strategii migracji klienta w programie System Center Configuration Manager](../../../core/migration/planning-a-client-migration-strategy.md).  

 
###<a name="to-create-a-package-and-program-for-the-client-software"></a>Aby utworzyć pakiet i program dla oprogramowania klienckiego  

Poniższa procedura umożliwia utworzenie pakietu programu Configuration Manager i programu, można wdrożyć na komputerach klienckich programu Configuration Manager do uaktualnienia oprogramowania klienta.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **pakiety**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz pakiet z definicji**.  

4.  Na **definicji pakietu** w kreatorze Wybierz **Microsoft** z **wydawcy** listy rozwijanej, a następnie wybierz **uaktualnienie klienta programu Configuration Manager** z **pakiet definicji** listy.  

5.  Na **pliki źródłowe** wybierz opcję **zawsze uzyskiwać pliki z folderu źródłowego**.  

6.  Na **Folder źródłowy** wybierz opcję **ścieżka sieciowa (Nazwa UNC)** i wprowadź ścieżkę sieciową do komputera i folderu zawierającego pliki instalacyjne klienta.  

    > [!NOTE]  
    >  Komputer, na którym uruchomione wdrożenie programu Configuration Manager musi mieć dostęp do folderu sieciowego, który można określić, w przeciwnym razie instalacja zakończy się niepowodzeniem.  

    Aby zmienić dowolne z właściwości instalacji klienta, można zmodyfikować parametry wiersza polecenia programu CCMSetup.exe na karcie **Ogólne** w oknie dialogowym **Uaktualnienie dyskretne agenta programu Configuration Manager — Właściwości**. Domyślne właściwości instalacji to **/noservice SMSSITECODE=AUTO**.  

9. Pakiet należy rozpowszechnić do wszystkich punktów dystrybucji, które mają hostować pakiet uaktualnienia klienta. Następnie można wdrożyć pakiet do kolekcji komputerów zawierających klientów, które chcesz uaktualnić.  

## <a name="how-to-install-clients-to-intune-mdm-managed-windows-devices"></a>Jak zainstalować klientów na urządzeniach Windows Intune MDM zarządzanych

Pliki instalacyjne klienta można wdrożyć na komputerach, które są zarejestrowane w usłudze Microsoft Intune. 

Aby upewnić się, że urządzenie pozostanie w stanie zarządzanym po zainstalowaniu oprogramowania klienckiego, urządzenie musi być w sieci firmowej i w obrębie granicy lokacji programu Configuration Manager. 

> [!NOTE]
> Po zainstalowaniu oprogramowania klienckiego, urządzenie zostanie wyrejestrowane z usługi Intune.

### <a name="to-install-clients-with-intune"></a>Aby zainstalować klienta za pomocą usługi Intune:

1. W usłudze Intune [Utwórz aplikację](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) zawierający plik instalacyjny klienta programu Configuration Manager **ccmsetup.msi**.

2. W wydawca oprogramowania usługi Intune należy użyć poniższych parametrów wiersza polecenia:

  **CCMSETUPCMD = "/ MP:&lt;nazwę FQDN punktu zarządzania > SMSMP =&lt;nazwę FQDN punktu zarządzania > SMSSITECODE =&lt;kod lokacji > DNSSUFFIX =&lt;sufiks DNS punktu zarządzania >"**

3. [Wdróż aplikację](/intune/deploy-use/deploy-apps-in-microsoft-intune) do zarejestrowanych komputerów z systemem Windows.

##  <a name="BKMK_ClientImage"></a>Jak instalować klientów przy użyciu obrazu komputera  
Istnieje możliwość wstępnej instalacji oprogramowania klienta programu Configuration Manager na głównym komputerze obrazu używanego do obrazu innych komputerów.   

### <a name="to-prepare-the-client-computer-for-imaging"></a>Aby przygotować komputer kliencki do tworzenia obrazu  

1.  Ręczne instalowanie oprogramowania klienta programu Configuration Manager na głównym komputerze obrazu. Więcej informacji znajduje się w temacie [Jak ręcznie instalować klientów programu Configuration Manager](#BKMK_Manual).  

    > [!IMPORTANT]  
    >  Nie należy określać kodu lokacji programu Configuration Manager dla klienta we właściwościach wiersza polecenia programu CCMSetup.exe.  

2.  W wierszu polecenia wpisz tekst **net stop ccmexec**, aby upewnić się, że usługa **Host agenta programu SMS** (Ccmexec.exe) nie jest uruchomiona na głównym komputerze obrazu.  

3.  Usuń wszystkie certyfikaty przechowywane w magazynie komputera lokalnego na głównym komputerze obrazu.  Jeśli przykładowo są używane certyfikaty infrastruktury klucza publicznego (PKI), przed utworzeniem obrazu komputera należy usunąć certyfikaty z magazynu **Osobisty** **Komputera** i **Użytkownika**.

4.  Jeśli klienci będą instalowani w innej hierarchii programu Configuration Manager niż główny komputer obrazu, Usuń zaufany klucz główny z głównego komputera obrazu.  
    > [!NOTE]  
    >  Jeśli klienci nie będą mogli wysłać kwerendy do usług Active Directory Domain Services w celu zlokalizowania punktu zarządzania, użyją zaufanego klucza głównego w celu określenia zaufanych punktów zarządzania. Jeśli wszyscy klienci, których obraz został utworzony, zostaną wdrożeni do tej samej hierarchii, co komputer główny, zaufany klucz główny należy pozostawić na miejscu. Jeśli klienci zostaną wdrożeni w różnych hierarchiach, należy usunąć zaufany klucz główny i udostępnić tym klientom nowy zaufany klucz główny. Aby uzyskać więcej informacji, zobacz [Planowanie zaufanego klucza głównego](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK). 

5.  Użyj oprogramowania do tworzenia obrazu, aby przechwycić obraz komputera głównego.  

6.  Wdróż obraz na komputerach docelowych.  

##  <a name="BKMK_ClientWorkgroup"></a>Jak zainstalować klientów na komputerach grupy roboczej  
 Program Configuration Manager obsługuje instalację klienta dla komputerów w grupach roboczych. Klientów na komputerach grupy roboczej można zainstalować, korzystając z metody podanej w sekcji [Jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual).  

 Wymagania wstępne:  

-   Na każdym komputerze grupy roboczej należy zainstalować klienta ręczne. Podczas instalacji zalogowany użytkownik musi mieć prawa administratora lokalnego.  

-   Aby uzyskać dostęp do zasobów w domenie serwera lokacji programu Configuration Manager, należy skonfigurować konto dostępu do sieci dla lokacji. To konto można określić jako właściwość składnika dystrybucji oprogramowania. Aby uzyskać więcej informacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

 Ograniczenia:  

-   Klienci grupy roboczej nie mogą lokalizować punktów zarządzania z usług Active Directory Domain Services i zamiast tego muszą używać serwera DNS, WINS lub innego punktu zarządzania.  

-   Roaming globalny nie jest obsługiwany, ponieważ klienci nie mogą wysyłać kwerend do usług domenowych w usłudze Active Directory w celu uzyskania informacji o lokacji.  

-   Metody odnajdywania w usłudze Active Directory nie mogą odnajdywać komputerów grup roboczych.  

-   Nie można wdrożyć oprogramowania na kontach użytkowników komputerów grupy roboczej.  

-   Nie można użyć metody instalacji wypychanej klienta w celu zainstalowania klientów na komputerach grupy roboczej.  

-   Klienci grupy roboczej nie może korzystać z protokołu Kerberos do uwierzytelniania i może wymagać ręcznego zatwierdzania.  

-   Klienta grupy roboczej nie można skonfigurować jako punktu dystrybucji. Program Configuration Manager wymaga, aby komputery punktu dystrybucji były członkami domeny.  

### <a name="to-install-the-client-on-workgroup-computers"></a>Aby zainstalować klienta na komputerach grupy roboczej  

Sprawdź wymagania wstępne, a następnie postępuj zgodnie z instrukcjami w sekcji [jak zainstalować klientów programu Configuration Manager ręcznie](#BKMK_Manual).  

   W tym przykładzie powoduje zainstalowanie klienta do zarządzania klientami w sieci intranet i określenie kodu lokacji oraz sufiksu DNS lokalizacji punktu zarządzania:`**CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com**`  

     

   Polecenie podane w tym przykładzie wymaga, aby klient znajdował się w lokalizacji sieciowej skonfigurowanej w grupie granic, co zapewni powodzenie automatycznego przypisywania lokacji. To polecenie dodaje rezerwowy punkt stanu do elementu FSPSERVER serwera, aby ułatwić śledzenie wdrażania klientów i identyfikację problemów dotyczących komunikacji klienta:`**CCMSetup.exe FSP=fspserver.constoso.com**`  

      

##  <a name="BKMK_ClientInternet"></a>Jak zainstalować klientów do zarządzania internetowego  
 Gdy lokacji programu Configuration Manager obsługuje klienta internetowego zarządzania dla klientów, które są czasem w sieci intranet, a czasem z Internetem, dostępne są dwie opcje instalacji klientów w intranecie:  

-   Można dodać właściwość pliku Client.msi ccmhostname =*&lt;internetowej nazwy FQDN punktu zarządzania internetowego\>*  po zainstalowaniu klienta, na przykład za pomocą ręcznej lub instalacji wypychanej klienta. Jeżeli używana jest ta metoda, należy także bezpośrednio przypisać klienta do lokacji i nie można użyć automatycznego przypisywania lokacji. Przykład tej metody konfiguracji zawiera sekcja [Jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual).  

-   Można zainstalować klienta do zarządzania klientami w sieci intranet, a następnie przypisać punkt zarządzania klientami do klienta, używając właściwości klienta programu Configuration Manager w Panelu sterowania lub za pomocą skryptu. Jeżeli stosowana jest ta metoda, można użyć automatycznego przypisania klienta. Więcej informacji zawiera sekcja [Jak skonfigurować klientów pod kątem internetowego zarządzania klientami po zainstalowaniu klienta](#BKMK_ConfigureIBCM_MP) w tym temacie.  

 Jeżeli konieczne jest zainstalowanie klientów połączonych przez Internet, ponieważ są to klienci internetowi lub wymagane jest ich zainstalowanie przed ponownym połączeniem z intranetem, należy wybrać jedną z następujących obsługiwanych metod:  

-   Udostępniają mechanizm dla tych klientów, aby tymczasowo łączyć się z Internetem z wirtualnej sieci prywatnej (VPN), a następnie zainstaluj je przy użyciu dowolnej metody instalacji odpowiedniego klienta.  

-   Użyj metody instalacji, która jest niezależna od programu Configuration Manager przykład instalując pliki źródłowe instalacji klienta na nośniku wymiennym, który można wysłać do klientów z instrukcjami instalacji. Pliki źródłowe instalacji klienta znajdują się w  *&lt;Ścieżkainstalacyjna\>*\Client folderu w punktach zarządzania i serwera lokacji programu Configuration Manager. Umieść na nośniku skrypt ręcznego kopiowania do i z folderu klienta, zainstaluj klienta, używając programu CCMSetup.exe i wszystkie odpowiednie właściwości wiersza polecenia programu CCMSetup.  

> [!NOTE]  
>  Menedżer konfiguracji nie obsługuje instalacji klienta bezpośrednio z punktu zarządzania internetowego ani z punktem aktualizacji oprogramowania internetowego.  

 Ponieważ klienci zarządzani przez Internet muszą komunikować się z internetowymi systemami lokalizacji, przed ich zainstalowaniem należy upewnić się, że mają zainstalowane certyfikaty infrastruktury klucza publicznego (PKI). Zainstalowanie tych certyfikatów niezależnie z programu Configuration Manager. Więcej informacji o wymaganiach dla certyfikatów znajduje się w temacie [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

### <a name="to-install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>Aby zainstalować klientów przez Internet, określając właściwości wiersza polecenia programu CCMSetup  

1.  Wykonaj czynności podane w sekcji [Jak instalować klientów programu Configuration Manager ręcznie](#BKMK_Manual) i zawsze dodaj następujące elementy:  

    -   Właściwość wiersza polecenia CCMSetup **/source:***&lt;ścieżkę lokalną do skopiowanych folderu klienta\>*  

    -   Właściwość wiersza polecenia **/UsePKICert** programu CCMSetup  

    -   Właściwości pliku Client.msi **CCMHOSTNAME =***&lt;punkt zarządzania FQDN internetowych\>*  

    -   Właściwości pliku Client.msi **SMSSIGNCERT =***&lt;ścieżkę lokalną do serwera lokacji wyeksportowanego certyfikatu podpisywania\>*  

    -   Właściwości pliku Client.msi **SMSSITECODE =***&lt;kod punktu zarządzania internetowego lokacji\>*  

    > [!NOTE]  
    >  Jeżeli lokacja ma więcej niż jeden internetowy punkt zarządzania, nie jest istotne, który internetowy punkt zarządzania zostanie określony dla właściwości CCMHOSTNAME. Gdy klient programu Configuration Manager łączy się określonego internetowego punktu zarządzania, punkt zarządzania wysyła klientowi listę dostępnych internetowych punktów zarządzania w lokacji, a klient losowo wybiera jeden z nich.  

2.  Jeżeli nie chcesz, aby klient sprawdzał listę odwołania certyfikatów (CRL, certificate revocation list), określ właściwość wiersza polecenia **/NoCRLCheck** programu CCMSetup.  

3.  Jeśli używasz jest internetowy rezerwowy punkt stanu, określ właściwość pliku Client.msi **FSP =***&lt;internetową nazwą FQDN internetowego rezerwowego punktu stanu\>*.  

4.  Jeżeli klient jest instalowany do zarządzania tylko przez Internet, określ właściwość **CCMALWAYSINF=1** programu Client.msi.  

5.  Sprawdź, czy masz do określenia dodatkowych właściwości wiersza polecenia programu CCMSetup. Na przykład może trzeba określić kryteria wyboru certyfikatu, jeżeli klient ma więcej niż jeden ważny certyfikat PKI. Listę dostępnych właściwości zawiera temat [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

   Przykład: `**CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1**`  

   Polecenie podane w tym przykładzie powoduje zainstalowanie plików źródłowych klienta z folderu na dysku D z ustawieniami umożliwiającymi użycie certyfikatu PKI klienta i wybór certyfikatu o najdłuższym okresie ważności do zarządzania klientami tylko przez Internet, przypisania klienta do korzystania z internetowego punktu zarządzania o nazwie SERVER1, internetowego rezerwowego punkt stanu w domenie contoso.com i przypisanie klienta do lokacji ABC.  

###  <a name="BKMK_ConfigureIBCM_MP"></a>Aby skonfigurować klientów do internetowego zarządzania klientami po zainstalowaniu klienta  
 Aby przypisać internetowy punkt zarządzania po zainstalowaniu klienta, należy użyć jednej z poniższych procedur. Pierwszy wymaga ręcznej konfiguracji i jest odpowiednia dla niewielkiej liczby klientów. Druga jest bardziej odpowiednie dla Konfigurowanie wielu klientów.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Aby skonfigurować klientów do internetowego zarządzania klientami po zainstalowaniu klienta, przypisując internetowy punkt zarządzania w oknie Właściwości programu Configuration Manager  

1.  Przejdź do apletu **Configuration Manager** w Panelu sterowania na komputerze klienckim, a następnie kliknij go dwukrotnie, aby otworzyć jego właściwości.  

2.  Na karcie **Internet** wprowadź w pełni kwalifikowaną nazwę domeny internetowego punktu zarządzania w polu tekstowym W pełni kwalifikowana nazwa domeny internetowej.  

    > [!NOTE]  
    >  Karta **Internet** jest dostępna tylko wtedy, gdy klient ma certyfikat PKI.  

3.  Wprowadź ustawienia serwera proxy, jeżeli klient będzie uzyskiwał dostęp do Internetu za pomocą serwera proxy.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>Aby skonfigurować klientów do zarządzania internetowego po instalacji klienta za pomocą skryptu  

1.  Otwórz edytor tekstu, na przykład Notatnik.  

2.  Skopiuj i Wstaw następujący tekst do pliku. Zastąp tekst *mp.contoso.com* internetową nazwą FQDN internetowego punktu zarządzania.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the Internet-Based Management Point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  Jeśli konieczne jest usunięcie określonego internetowego punktu zarządzania, aby klient nie był skonfigurowany do użycia internetowego punktu zarządzania, usuń wartość w cudzysłowie, aby wiersz miał postać **newInternetBasedManagementPointFQDN = ""**.  

4.  Zapisz plik z rozszerzeniem vbs.  

5.  Użyj programu cscript, aby uruchomić skrypt na komputerach klienckich, używając jednej z następujących metod:  

    -   Wdróż plik na istniejących klientach programu Configuration Manager, używając pakietu i programu.  

    -   Uruchom plik lokalnie na istniejących klientach programu Configuration Manager, klikając dwukrotnie plik skryptu w Eksploratorze Windows.  

 Może być ponowne uruchomienie klienta zmiany zaczęły obowiązywać.  

##  <a name="BKMK_Provision"></a>Jak udostępniać właściwości instalacji klienta (grupy zasad i oparta na aktualizacji klienta instalacja oprogramowania)  
 Zasad grupy systemu Windows można użyć do udostępnienia komputerów za pomocą właściwości instalacji klienta programu Configuration Manager. Te właściwości są przechowywane w rejestrze komputera i są odczytywane podczas instalacji oprogramowania klienckiego. Ta procedura zwykle nie jest wymagane, ale może być konieczne w niektórych scenariuszy instalacji klienta, takie jak:  

-   Używane są ustawienia zasad grupy lub metody instalacji klienta opartej na aktualizacji oprogramowania, a nie został rozszerzony schemat usługi Active Directory dla programu Configuration Manager.  

-   Wymagane jest zastąpienie właściwości instalacji klienta na określonych komputerach.  

> [!NOTE]  
>  Jeżeli jakiekolwiek właściwości instalacji są podane w wierszu polecenia programu CCMSetup.exe, właściwości instalacji udostępnione na komputerach nie będą używane.  

 Szablon administracyjny zasad grupy o nazwie ConfigMgrInstallation.adm jest dostępny na nośniku instalacyjnym programu Configuration Manager, można użyć do udostępnienia właściwości instalacji na komputerach klienckich.   

### <a name="to-configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>Aby skonfigurować i przypisać właściwości instalacji klienta za pomocą obiektu zasad grupy  

1.  Zaimportuj szablon administracyjny ConfigMgrInstallation.adm do nowego lub istniejącego obiektu zasad grupy, używając edytora, takiego jak Windows Group Policy Object Editor. Plik znajduje się w folderze **TOOLS\ConfigMgrADMTemplates** na nośniku instalacyjnym programu Configuration Manager.  

2.  Otwórz właściwości zaimportowanego ustawienia **Konfiguruj ustawienia wdrażania klienta**.  

3.  Wybierz **włączone**.  

4.  W polu **CCMSetup** wprowadź wymagane właściwości wiersza polecenia programu CCMSetup. Lista wszystkich właściwości wiersza polecenia programu CCMSetup i przykłady ich użycia znajdują się w temacie [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

5.  Przypisz obiekt zasad grupy do komputerów, które chcesz udostępnić właściwości instalacji klienta programu Configuration Manager.  

 Informacje o zasadach grupy systemu Windows zawiera dokumentacja systemu Windows Server.  

### <a name="see-also"></a>Zobacz także
[Metody instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md)
