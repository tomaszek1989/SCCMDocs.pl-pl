---
title: "Zarządzanie aktualizacjami usługi Office 365 ProPlus"
titleSuffix: Configuration Manager
description: "Menedżer konfiguracji synchronizuje aktualizacje klienta usługi Office 365 z katalogu WSUS na serwerze lokacji, aby aktualizacje dostępne do wdrażania na klientach."
keywords: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.date: 12/28/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.openlocfilehash: b951e72635806c12bd0ec0dd66e382a767b99b43
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="manage-office-365-proplus-with-configuration-manager"></a>Zarządzanie usługą Office 365 ProPlus w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Menedżer konfiguracji umożliwia zarządzanie aplikacjami usługi Office 365 ProPlus w następujący sposób:

- [Pulpit nawigacyjny zarządzania klienta usługi Office 365](#office-365-client-management-dashboard): Począwszy od programu Configuration Manager 1610 wersji, można przejrzeć informacje o kliencie usługi Office 365 z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365.    

- [Wdrażanie aplikacji usługi Office 365](#deploy-office-365-apps): Począwszy od wersji 1702, można uruchomić Instalator Office 365 z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365, aby łatwiej wystąpić początkowej instalacja aplikacji Office 365. Kreator umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z sieci dostarczania zawartości (CDN) i Utwórz i wdróż aplikację skryptu z zawartością.    

- [Wdrażanie aktualizacji usługi Office 365](#deploy-office-365-updates): Począwszy od programu Configuration Manager w wersji 1602, można zarządzać aktualizacjami klienta usługi Office 365 za pomocą przepływu pracy zarządzania aktualizacjami oprogramowania. Gdy firma Microsoft publikuje nową aktualizację klienta usługi Office 365 w sieci dostarczania zawartości (CDN) pakietu Office, publikuje również pakiet aktualizacji w programie Windows Server Update Services (WSUS). Po synchronizacji aktualizacji klienta usługi Office 365 z katalogu WSUS na serwerze lokacji programu Configuration Manager aktualizacja jest dostępna do wdrażania na klientach.    

- [Dodaj pobranie aktualizacji języków dla usługi Office 365](#add-languages-for-office-365-update-downloads): Począwszy od programu Configuration Manager 1610 wersji, można dodać obsługę programu Configuration Manager mógł pobierać aktualizacje dla dowolnego języki obsługiwane przez usługi Office 365. Do obsługi języka tak długo, jak usługi Office 365 jest nie ma znaczenia Configuration Manager.  

- [Zmień kanału aktualizacji](#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager): Można użyć zasad grupy, aby dystrybuować zmianę wartości klucza rejestru klientów usługi Office 365, aby zmienić kanału aktualizacji.


## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klienta usługi Office 365  
Pulpit nawigacyjny zarządzania klienta usługi Office 365 zawiera wykresy następujące informacje:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     
  Aby uzyskać więcej informacji, zobacz [Omówienie aktualizacji kanałów dla usługi Office 365 ProPlus](https://technet.microsoft.com/library/mt455210.aspx).

Aby wyświetlić pulpit nawigacyjny zarządzania usługi Office 365 klienta w konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365**. W górnej części pulpitu nawigacyjnego, należy użyć **kolekcji** ustawienie listy rozwijanej, aby filtrować dane pulpitu nawigacyjnego przez członków określonej kolekcji.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Wyświetl dane na pulpicie nawigacyjnym zarządzania klienta usługi Office 365
Dane, które jest wyświetlane na pulpicie nawigacyjnym zarządzania klienta usługi Office 365 pochodzi ze spisu sprzętu. Włącz spis sprzętu i wybierz **Office 365 ProPlus konfiguracje** klasy spisu sprzętu dla danych do wyświetlenia na pulpicie nawigacyjnym.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Aby wyświetlić dane na pulpicie nawigacyjnym zarządzania klienta usługi Office 365
1. Włącz spis sprzętu, jeśli nie jest jeszcze włączona. Aby uzyskać więcej informacji, zobacz [Konfigurowanie spisu sprzętu](\sccm\core\clients\manage\configure-hardware-inventory).
2. W konsoli programu Configuration Manager, przejdź do **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  
3. Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  
4. W oknie dialogowym **Domyślne ustawienia klienta** kliknij pozycję **Spis sprzętu**.  
5. Na liście **Ustawienia urządzenia** kliknij pozycję **Ustaw klasy**.  
6. W **klasy spisu sprzętu** okno dialogowe, wybierz opcję **Office 365 ProPlus konfiguracje**.  
7.  Kliknij przycisk **OK** , aby zapisać zmiany i zamknąć okno dialogowe **Klasy spisu sprzętu** . <br/>Pulpit nawigacyjny zarządzania usługi Office 365 klienta zostanie uruchomiony, wyświetlanie danych zgłoszonej spisu sprzętu.

## <a name="deploy-office-365-apps"></a>Wdrażanie aplikacji usługi Office 365  
Począwszy od wersji 1702, uruchom Instalatora pakietu Office 365 z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365 początkowej instalacji aplikacji Office 365. Kreator umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i Utwórz i wdróż aplikację skryptów dla plików. Usługi Office 365 są zainstalowane na komputerach klienckich, aktualizacji usługi Office 365 nie mają zastosowania.

W poprzednich wersjach programu Configuration Manager należy wykonać następujące kroki, aby zainstalować aplikacje usługi Office 365 po raz pierwszy na klientach:
- Pobierz narzędzia wdrażania pakietu Office 365 (ODT)
- Pobierz pliki źródłowe instalacji usługi Office 365, w tym wszystkie pakiety językowe, które są potrzebne.
- Generowanie Configuration.xml, który określa poprawną wersję pakietu Office i kanału.
- Tworzenie i wdrażanie starszej wersji pakietu lub aplikacji skryptu dla klientów w celu instalowania aplikacji usługi Office 365.

### <a name="requirements"></a>Wymagania
- Komputer z uruchomioną Office 365 Instalator musi mieć dostęp do Internetu.  
- Użytkownik uruchamiający Instalatora pakietu Office 365 musi mieć **odczytu** i **zapisu** dostęp do udziału lokalizacji zawartości znajduje się w kreatorze.
- Jeśli wystąpi błąd 404 pobierania, skopiuj następujące pliki do folderu temp % % użytkownika:
  - [releasehistory.XML](http://officecdn.microsoft.com/pr/wsus/releasehistory.cab)
  - [o365client_32bit.XML](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  


### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Do wdrażania aplikacji usługi Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365**.
2. Kliknij przycisk **Office 365 Instalator** w prawym górnym okienku. Zostanie otwarty Kreator instalacji klienta Office 365.
3. Na **ustawienia aplikacji** , podaj nazwę i opis aplikacji, wprowadź lokalizację pobierania dla plików, a następnie kliknij przycisk **dalej**. Lokalizacja musi być określona jako &#92; &#92; *server*&#92; *udostępnianie*.
4. Na **importowania ustawień klienta** strony wybierz, czy do zaimportowania ustawień klienta usługi Office 365 z istniejącego pliku konfiguracji XML lub ręcznie określ ustawienia, a następnie kliknij przycisk **dalej**.  

    Jeśli masz istniejący plik konfiguracyjny wprowadź lokalizację pliku, a następnie przejdź do kroku 7. Należy określić lokalizację w postaci &#92; &#92; *serwera*&#92; *udostępnianie*&#92; *Nazwa pliku*. KOD XML.
    > [!IMPORTANT]    
    > Plik konfiguracji XML musi zawierać tylko [języki obsługiwane przez klienta usługi Office 365 ProPlus](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx).

5. Na **produktów klienta** wybierz pakiet usługi Office 365, którego używasz. Wybierz aplikacje, które chcesz dołączyć. Wybierz wszelkie dodatkowe produktów pakietu Office, które powinny być uwzględnione, a następnie kliknij **dalej**.
6. Na **ustawień klienta** wybierz ustawienia do uwzględnienia, a następnie kliknij pozycję **dalej**.
7. Na **wdrożenia** wybierz, czy wdrożyć aplikację, a następnie kliknij przycisk **dalej**. <br/>Jeśli wybierzesz nie wdrożyć pakiet w kreatorze, przejdź do kroku 9.
8. W pozostałej części strony kreatora należy skonfigurować, jak w przypadku wdrażania Typowa aplikacja. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie aplikacji](/sccm/apps/get-started/create-and-deploy-an-application).
9. Ukończ pracę kreatora.
10. Można wdrożyć lub edytowanie aplikacji z **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **aplikacji**.    

Po utworzeniu i wdrażania aplikacji usługi Office 365 za pomocą pakietu Office 365 Instalatora programu Configuration Manager nie zarządzanie aktualizacjami Office domyślnie. Aby włączyć klientów usługi Office 365 w celu otrzymywania aktualizacji programu Configuration Manager, zobacz [wdrożenia usługi Office 365 aktualizacji z programu Configuration Manager](#deploy-office-365-updates-with-configuration-manager).

>[!NOTE]
>Po wdrożeniu aplikacji usługi Office 365, można utworzyć reguły automatycznego wdrażania do obsługi aplikacji. Aby utworzyć regułę automatycznego wdrażania dla aplikacji usługi Office 365, kliknij przycisk **utworzyć regułę ADR** na pulpicie nawigacyjnym zarządzania klienta usługi Office 365. Wybierz **klienta usługi Office 365** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).


## <a name="deploy-office-365-updates"></a>Wdrażanie aktualizacji usługi Office 365
Do wdrażania aktualizacji usługi Office 365 z programem Configuration Manager, wykonaj następujące kroki:

1.  [Sprawdź wymagania](https://technet.microsoft.com/library/mt628083.aspx) dla programu Configuration Manager do zarządzania aktualizacjami klienta usługi Office 365 w **wymagania dotyczące korzystania z programu Configuration Manager do zarządzania aktualizacjami klienta usługi Office 365** sekcji tego artykułu.  

2.  [Skonfiguruj punkty aktualizacji oprogramowania](../get-started/configure-classifications-and-products.md) celu synchronizowania klienta usługi Office 365 aktualizacji. Ustaw **aktualizacje** dla klasyfikacji i wybierz **klienta usługi Office 365** dla produktu. Synchronizowanie aktualizacji oprogramowania po skonfigurowaniu punktów aktualizacji oprogramowania do używania **aktualizacje** klasyfikacji.
3.  Włącz klientów usługi Office 365 w celu otrzymywania aktualizacji programu Configuration Manager. Użyj Menedżera konfiguracji ustawień klienta lub zasad grupy klienta.   

    **Metoda 1**: Począwszy od programu Configuration Manager 1606 wersji, można użyć klienta programu Configuration Manager ustawienie do zarządzania agenta klienta usługi Office 365. Po skonfigurowaniu tego ustawienia i wdrażania aktualizacji usługi Office 365, agenta klienta programu Configuration Manager komunikuje się z agentem klienta usługi Office 365 do pobierania aktualizacji usługi Office 365 z punktu dystrybucji i zainstaluj je. Menedżer konfiguracji wykonuje spis ustawień klienta usługi Office 365 ProPlus.    

      1.  W konsoli programu Configuration Manager kliknij **administracji** > **omówienie** > **ustawień klienta**.  

      2.  Otwórz ustawienia odpowiedniego urządzenia, aby włączyć agenta klienta. Aby uzyskać więcej informacji na temat domyślne i niestandardowe ustawienia klienta, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

      3.  Kliknij przycisk **aktualizacji oprogramowania** i wybierz **tak** dla **włączyć zarządzanie agenta klienta Office 365** ustawienie.  

    **Metoda 2**: [Włącz klientów usługi Office 365 w celu otrzymywania aktualizacji](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient) z programu Configuration Manager za pomocą narzędzia wdrażania pakietu Office lub zasad grupy.  

4. [Wdrażanie aktualizacji usługi Office 365](deploy-software-updates.md) do klientów.   

> [!Important]
> Należy pobrać i wdrożyć aktualizacje w te same języki skonfigurowane dla klientów usługi Office 365. Na przykład, załóżmy, że masz klienta usługi Office 365 skonfigurowano en-us i de-de języków. Na serwerze lokacji, należy pobrać i zainstalować tylko en-us zawartości dla odpowiednich aktualizacji usługi Office 365. Gdy użytkownik uruchomi instalację z Centrum oprogramowania dla tej aktualizacji, aktualizacja zawiesza się podczas pobierania zawartości.   

## <a name="restart-behavior-and-client-notifications-for-office-365-updates"></a>Uruchom ponownie klienta i zachowanie powiadomienia o aktualizacji usługi Office 365
Podczas wdrażania aktualizacji klienta usługi Office 365, powiadomienia klienta i zachowanie ponownego uruchamiania są różne w zależności od wersji programu Configuration Manager ma. Poniższa tabela zawiera informacje na temat środowiska użytkownika końcowego po otrzymaniu przez klienta aktualizacji usługi Office 365:

|Wersja programu Configuration Manager |Środowisko użytkownika końcowego|  
|----------------|---------------------|
|Przed 1610|Ustawiono flagi ponownego uruchomienia i zainstalowaniu aktualizacji po ponownym uruchomieniu komputera.|
|1610|Aplikacje pakietu Office 365 są zamknięte bez ostrzeżenia przed zainstalowaniem aktualizacji|
|1610 z aktualizacją <br/>1702|Ustawiono flagi ponownego uruchomienia i zainstalowaniu aktualizacji po ponownym uruchomieniu komputera.|
|1706|Klient odbiera powiadomienia wyskakującego i w aplikacji, a także okno odliczania, przed zainstalowaniem aktualizacji.|

> [!Important]
> 1706 wersji programu Configuration Manager zanotuj następujące informacje:
>
>- Wyświetla ikony powiadomień w obszarze powiadomień na pasku zadań dla wymaganych aplikacji, gdzie jest ostatecznym w ciągu 48 godzin w przyszłości i zawartość aktualizacji została pobrana. 
>- Wyświetla okno odliczania dla wymaganych aplikacji, gdzie ostatecznym mieści się w przyszłości 7,5 godziny, a aktualizacja została pobrana. Użytkownika można odroczyć okno odliczania maksymalnie trzy razy przed upływem określonego terminu. Odroczone, odliczania Wyświetla ponownie po dwóch godzinach. Jeśli nie odłożyć, istnieje odliczania 30-minutowych i aktualizacji są instalowane, po wygaśnięciu odliczania.
>- Wyskakujących powiadomień nie może być wyświetlany, dopóki użytkownik kliknie ikonę w obszarze powiadomień. Ponadto jeśli w obszarze powiadomień minimalnej ilości miejsca, ikony powiadomień może nie być widoczne chyba że użytkownik otwiera lub rozwijane w obszarze powiadomień. 
>- Okno dialogowe powiadomień i odlicza czas można uruchomić, gdy użytkownik nie jest aktywnie działa na urządzeniu, na przykład, gdy urządzenie jest zablokowane przez noc, zatem możliwe jest uruchomione na urządzeniu aplikacje pakietu Office może wystąpić konieczność Zamknij, aby zainstalować aktualizację. Przed zamknięciem aplikacji, pakietu Office zapisuje dane aplikacji, aby zapobiec utracie danych. 
>- Jeśli ostatecznym znajduje się w ciągu ostatnich lub skonfigurowany do uruchomienia tak szybko, jak to możliwe, uruchomione aplikacje pakietu Office może wymusić bez powiadomienia. 
>- Jeśli użytkownik zainstaluje aktualizacji dla pakietu Office przed upływem ostatecznego terminu, Configuration Manager weryfikuje, czy aktualizacja jest zainstalowana, po osiągnięciu terminu ostatecznego. Jeśli aktualizacja nie zostanie wykryta na urządzeniu, aktualizacja jest zainstalowana. 
>- Na pasku powiadomień w aplikacji nie są wyświetlane w aplikacji pakietu Office, która jest uruchomiona, przed pobraniem aktualizacji. Po pobraniu aktualizacji w aplikacji powiadomienie będzie wyświetlane tylko w przypadku nowo otwieranych aplikacji.
>- W przypadku aktualizacji pakietu Office wyzwalane przez okno usługi lub zaplanowane dla poza godzinami pracy jest możliwe, że uruchomione aplikacje pakietu Office może wymusić Zamknij, aby zainstalować tę aktualizację bez powiadomienia. 



## <a name="add-languages-for-office-365-update-downloads"></a>Dodaj języki do pobrania aktualizacji usługi Office 365
Począwszy od programu Configuration Manager 1610 wersji, można dodać obsługę programu Configuration Manager do pobierania aktualizacji dla żadnych języków, które są obsługiwane przez usługi Office 365, niezależnie od tego, czy są obsługiwane w programie Configuration Manager.    

> [!IMPORTANT]  
> Konfigurowanie dodatkowych języków aktualizacji usługi Office 365 jest ustawienie całej lokacji. Po dodaniu języków przy użyciu poniższej procedury, wszystkie aktualizacje usługi Office 365 są pobierane w tych językach oraz języki, które wybiera się na **wybór języka** stronie kreatorów pobierania aktualizacji oprogramowania lub wdrażania aktualizacji oprogramowania.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>Aby dodać obsługę, aby pobierać aktualizacje dla innych językach
Użyj poniższej procedury w punkcie aktualizacji oprogramowania w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
1. W wierszu polecenia wpisz *wbemtest* jako użytkownik administracyjny, aby otworzyć Tester oprzyrządowania Instrumentacji zarządzania Windows.
2. Kliknij przycisk **Connect**, a następnie wpisz *root\sms\site_&lt;Kod_lokacji&gt;*.
3. Kliknij przycisk **zapytania**, a następnie uruchom następujące zapytanie: *wybierz opcję &#42; z SMS_SCI_Component gdzie NazwaSkładnika = "SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![Kwerenda WMI](..\media\1-wmiquery.png)
4. W okienku wyników kliknij dwukrotnie obiekt z kodem lokacji dla centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
5. Wybierz **właściwości** właściwości, kliknij przycisk **Edytuj właściwość**, a następnie kliknij przycisk **widoku osadzonych**.
![Edytor właściwości](..\media\2-propeditor.png)
6. Zaczynając od pierwszego wyniku zapytania, Otwórz każdy obiekt, do momentu znalezienia z **AdditionalUpdateLanguagesForO365** dla **PropertyName** właściwości.
7. Wybierz **wartość2** i kliknij przycisk **Edytuj właściwość**.  
![Edytuj Value2 właściwość](..\media\3-queryresult.png)
8. Dodaj dodatkowe języki do **wartość2** właściwości i kliknij przycisk **Zapisz właściwość**. <br/> Na przykład, pt-pt (dla portugalski — Portugalia), af-za-(dla Afrikaans — Republika Południowej Afryki), nie nn (dla norweski (Nynorsk) - Norwegia), itp.  
![Dodaj języki w edytorze właściwości](..\media\4-props.png)  
9. Kliknij przycisk **Zamknij**, kliknij przycisk **Zamknij**, kliknij przycisk **Zapisz właściwość**, kliknij przycisk **Zapisz obiekt** (po kliknięciu **Zamknij** tutaj wartości zostaną odrzucone), kliknij przycisk **Zamknij**, a następnie kliknij przycisk **zakończyć** do Zamknij Tester oprzyrządowania Instrumentacji zarządzania Windows.
10. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365** > **aktualizacji pakietu Office 365**.
11. Teraz podczas pobierania aktualizacji usługi Office 365, pobierania aktualizacji w językach, które w kreatorze i skonfigurowane w tej procedurze. Aby sprawdzić, czy w językach poprawne pobierania aktualizacji, przejdź do źródła pakietu aktualizacji i poszukaj plików z kodem języka w nazwie pliku.  
![Nazwy plików z dodatkowych języków](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Zmień kanału aktualizacji po włączeniu klientów usługi Office 365 w celu otrzymywania aktualizacji programu Configuration Manager
Aby zmienić kanału aktualizacji po włączeniu klientów usługi Office 365 otrzymywać aktualizacje programu Configuration Manager, należy użyć zasad grupy do dystrybucji zmianę wartości klucza rejestru dla klientów usługi Office 365. Zmień **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** klucz rejestru w celu użyj jednej z następujących wartości:

- Kanał co miesiąc <br/>
<i>(dawniej bieżący kanał) </i>:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- Częściowo roczna kanału <br/>
<i>(dawniej opóźnieniem kanał) </i>:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- Kanał co miesiąc (docelowe)<Br/>
 <i>(dawniej pierwszej wersji dla bieżącej kanału) </i>:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- Kanał częściowo roczna (docelowe) <br/>
<i>(dawniej pierwszej wersji dla kanału opóźnieniem) </i>:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf
<!--the channel names changed in Sept 2017- https://docs.microsoft.com/en-us/DeployOffice/overview-of-update-channels-for-office-365-proplus?ui=en-US&rs=en-US&ad=US>


<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->
