---
title: "Zarządzanie aktualizacjami Office 365 ProPlus | Dokumentacja firmy Microsoft"
description: "Menedżer konfiguracji synchronizuje aktualizacje klienta usługi Office 365 z katalogu programu WSUS na serwerze lokacji, aby udostępnić aktualizacje dostępne do wdrażania na klientach."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 016580dc6ee3c5268833db941d42416a976d201c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-office-365-proplus-with-configuration-manager"></a>Zarządzanie usługą Office 365 ProPlus z programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Configuration Manager synchronizuje aktualizacje klientów usługi Office 365 i udostępnia je do wdrażania na klientach z zainstalowane usługi Office 365. Począwszy od programu Configuration Manager 1610 wersji, można przejrzeć informacje o kliencie usługi Office 365 z poziomu pulpitu nawigacyjnego zarządzania klientami usługi Office 365.

Począwszy od 1602 wersji programu Configuration Manager, Configuration Manager ma możliwość zarządzania aktualizacji klienta usługi Office 365 za pomocą przepływu pracy zarządzania aktualizacji oprogramowania. Gdy firma Microsoft publikuje nową aktualizację klienta usługi Office 365 w sieci dostarczania zawartości (CDN) pakietu Office, publikuje również pakiet aktualizacji w programie Windows Server Update Services (WSUS). Po synchronizacji aktualizację klienta usługi Office 365 z katalogu programu WSUS na serwerze lokacji programu Configuration Manager aktualizacja jest dostępna do wdrożenia na klientach.

Począwszy od wersji 1702, można uruchomić Instalatora pakietu Office 365 z poziomu pulpitu nawigacyjnego Office 365 klienta zarządzania początkowego aplikacji 365 Office zainstalować środowisko łatwiejsze. Kreator umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z sieci dostarczania zawartości (CDN) i tworzenie i wdrażanie aplikacji skryptu, z zawartością.

## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klientami usługi Office 365  
Począwszy od programu Configuration Manager w wersji 1610 pulpit nawigacyjny zarządzania klientami usługi Office 365 są dostępne w konsoli programu Configuration Manager. Aby wyświetlić pulpit nawigacyjny, przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365**.

Na pulpicie nawigacyjnym wykresy dla następujących elementów:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     
Aby uzyskać więcej informacji, zobacz [kanały przegląd aktualizacji dla Office 365 ProPlus](https://technet.microsoft.com/library/mt455210.aspx).
<!--- - Automatic deployment rules with Office 365 apps (have Office 365 Client selected in the set of available products). --->

<!---You can take the following actions on the dashboard:
- --->

W górnej części pulpitu nawigacyjnego, należy użyć **kolekcji** ustawienie listy rozwijanej do filtrowania danych pulpitu nawigacyjnego przez elementy członkowskie określonej kolekcji.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Wyświetlanie danych w pulpicie nawigacyjnym zarządzania klientami usługi Office 365
Dane, które jest wyświetlane na pulpicie nawigacyjnym zarządzania klientami usługi Office 365 pochodzi z spisu sprzętu. Spis sprzętu musi być włączona i należy wybrać **Office 365 ProPlus konfiguracje** klasę spisu sprzętu, zanim dane są wyświetlane na pulpicie nawigacyjnym.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Aby wyświetlić dane w pulpicie nawigacyjnym zarządzania klientami usługi Office 365
1. Włącz spis sprzętu, jeśli nie jest jeszcze włączona. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie spisu sprzętu](\sccm\core\clients\manage\configure-hardware-inventory).
2. W konsoli programu Configuration Manager, przejdź do **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  
3. Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  
4. W oknie dialogowym **Domyślne ustawienia klienta** kliknij pozycję **Spis sprzętu**.  
5. Na liście **Ustawienia urządzenia** kliknij pozycję **Ustaw klasy**.  
6. W **klasy spisu sprzętu** okno dialogowe, wybierz opcję **Office 365 ProPlus konfiguracje**.  
7.  Kliknij przycisk **OK** , aby zapisać zmiany i zamknąć okno dialogowe **Klasy spisu sprzętu** .  
Pulpit nawigacyjny zarządzania klientami usługi Office 365 rozpocznie wyświetlanie danych podaną spisu sprzętu.

## <a name="deploy-office-365-updates-with-configuration-manager"></a>Wdrażanie aktualizacji oprogramowania Office 365 z programu Configuration Manager
W przypadku wdrażania aktualizacji oprogramowania Office 365 z programu Configuration Manager, wykonaj następujące kroki:

1.  [Weryfikacja wymagań](https://technet.microsoft.com/library/mt628083.aspx) użycia programu Configuration Manager do zarządzania aktualizacjami klienta usługi Office 365 w **wymagania dotyczące korzystania z programu Configuration Manager do zarządzania aktualizacjami klienta usługi Office 365** w temacie.  

2.  [Konfigurowanie punktów aktualizacji oprogramowania](../get-started/configure-classifications-and-products.md) Synchronizowanie klienta usługi Office 365 aktualizacji. Ustaw **aktualizacje** dla klasyfikacji i wybierz **Office 365 klienta** produktu. Może zajść konieczność synchronizacji aktualizacji oprogramowania co najmniej jeden raz przed produktu Office 365 klienta jest dostępna do wyboru. Po skonfigurowaniu punkty aktualizacji oprogramowania do używania należy zsynchronizować aktualizacje oprogramowania **aktualizacje** klasyfikacji.
3.  Umożliwia klientom usługi Office 365 otrzymywać aktualizacje programu Configuration Manager. Można to zrobić przy użyciu ustawień klienta programu Configuration Manager lub za pomocą zasad grupy. Aby włączyć klienta, użyj jednej z następujących metod:  
    - Metoda 1: Począwszy od 1606 wersji programu Configuration Manager, można użyć ustawienia zarządzania agenta klienta usługi Office 365 klienta programu Configuration Manager. Po skonfigurowaniu tego ustawienia i wdrożenia aktualizacji oprogramowania Office 365, agent klienta programu Configuration Manager komunikuje się z agentem klienta usługi Office 365, aby pobrać aktualizacje oprogramowania Office 365 z punktu dystrybucji i zainstalować je. Menedżer konfiguracji wykonuje spis ustawień pakietu Office 365 ProPlus klienta.
      1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Przegląd** > **ustawień klienta**.  

      2.  Otwórz ustawienia odpowiedniego urządzenia, aby włączyć agenta klienta. Aby uzyskać więcej informacji o domyślnych i niestandardowych ustawień klienta, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

      3.  Kliknij przycisk **aktualizacji oprogramowania** i wybierz **tak** dla **włączyć funkcję zarządzania agenta klienta programu Office 365** ustawienie.  

    - Metoda 2: [Umożliwia klientom usługi Office 365 otrzymywać aktualizacje](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient) z programu Configuration Manager za pomocą narzędzia wdrażania pakietu Office lub zasad grupy.  

4. [Wdrażanie aktualizacji oprogramowania Office 365](deploy-software-updates.md) do klientów.   

> [!Important]
> Gdy klient usługi Office 365 z więcej niż jednego języka i pobierać aktualizacje dla języków mniej aktualizacji instalacja kończy się niepowodzeniem. Na przykład załóżmy, że klient usługi Office 365, en-us i de-de. Na serwerze lokacji, należy dowload i wdrażać tylko en-us zawartości dla odpowiednich aktualizacji usługi Office 365. Gdy użytkownik uruchamia instalację tej aktualizacji z Centrum oprogramowania, aktualizacji zawiesza się podczas pobierania zawartości. Należy pobrać i wdrożyć aktualizacje w tych samych języków jako klientów usługi Office 365.  


## <a name="add-other-languages-for-office-365-update-downloads"></a>Dodaj pliki do pobrania aktualizacji innych języków dla usługi Office 365
Począwszy od programu Configuration Manager 1610 wersji, można dodać obsługę dla programu Configuration Manager do pobierania aktualizacji dla wszystkie języki obsługiwane przez usługi Office 365, niezależnie od tego, czy są obsługiwane w programie Configuration Manager.
> [!IMPORTANT]  
> Konfigurowanie dodatkowych języków aktualizacji usługi Office 365 jest to ustawienie dotyczące całej lokacji. Po dodaniu języków przy użyciu poniższej procedury w tych językach, a także języki Wybierz na stronie Wybieranie języka w kreatorach wdrażania aktualizacji oprogramowania lub pobrać aktualizacje oprogramowania zostaną pobrane wszystkie aktualizacje oprogramowania Office 365.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>Aby dodać obsługę do pobierania aktualizacji dla dodatkowych języków
Użyj poniższej procedury w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej, w którym zainstalowano rolę systemu lokacji punktu aktualizacji oprogramowania.
1. W wierszu polecenia wpisz *wbemtest* jako użytkownik administracyjny, aby otworzyć Tester oprzyrządowania Instrumentacji zarządzania Windows.
2. Kliknij przycisk **Connect**, a następnie wpisz *root\sms\site_&lt;Kod_lokacji&gt;*.
3. Kliknij przycisk **kwerendy**, a następnie uruchom następujące zapytanie: *Zaznacz &#42; z SMS_SCI_Component gdzie componentname = "SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![Kwerendy usługi WMI](..\media\1-wmiquery.png)
4. W okienku wyników kliknij dwukrotnie obiekt z kodem lokacji dla centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
5. Wybierz **właściwości** właściwości, kliknij przycisk **Edytuj właściwość**, a następnie kliknij przycisk **osadzone widoku**.
![Edytor właściwości](..\media\2-propeditor.png)
6. Począwszy od pierwszego wyniku zapytania, Otwórz każdy obiekt, dopóki nie znajdziesz z **AdditionalUpdateLanguagesForO365** dla **PropertyName** właściwości.
7. Wybierz **wartość2** i kliknij przycisk **Edytuj właściwość**.  
![Edytuj Value2 właściwość](..\media\3-queryresult.png)
8. Dodaj kolejne języki **wartość2** właściwość i kliknij przycisk **Zapisz właściwość**.  
Na przykład, pt-pt (dla portugalski — Portugalia), af-za (dla Afrikaans — Republika Południowej Afryki), nr nn (dla norweski (Nynorsk) - Norwegia), itd.  
![Dodawanie języków w Edytor właściwości](..\media\4-props.png)  
9. Kliknij przycisk **Zamknij**, kliknij przycisk **Zamknij**, kliknij przycisk **Zapisz właściwość**, kliknij przycisk **Zapisz obiekt** (po kliknięciu **Zamknij** tutaj wartości zostaną odrzucone), kliknij przycisk **Zamknij**, a następnie kliknij przycisk **zamknąć** do Zamknij Tester oprzyrządowania Intstrumentation zarządzania systemu Windows.
10. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365** > **aktualizacji pakietu Office 365**.
11. Teraz po pobraniu aktualizacji usługi Office 365 aktualizacje zostaną pobrane w języku wybrane w kreatorze i języki skonfigurowane w tej procedurze. Aby sprawdzić, czy aktualizacje są pobrane w tych językach, przejdź do źródła pakietu aktualizacji i wyszukiwanie plików z kodem języka w nazwie pliku.  
![Nazwy plików z dodatkowych języków](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Zmienić kanał aktualizacji po włączeniu klientów usługi Office 365 otrzymywać aktualizacje programu Configuration Manager
Aby zmienić kanał aktualizacji po włączeniu klientów usługi Office 365 otrzymywać aktualizacje programu Configuration Manager, można użyć zasad grupy, aby dystrybuować zmianę wartości klucza rejestru dla klientów usługi Office 365. Zmień **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** klucz rejestru, aby użyć jednej z następujących wartości:

- Bieżąca kanału:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- Odroczone kanału:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- Pierwsza wersja bieżąca kanału:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- Pierwsze wydanie odroczonego kanału:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf

## <a name="deploy-office-365-apps"></a>Wdrażanie aplikacji Office 365  
Począwszy od wersji 1702, można uruchomić Instalatora pakietu Office 365 z pulpitu nawigacyjnego zarządzania klientami usługi Office 365 do początkowego Office 365 App Instalacja oprogramowania. Kreator umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierać pliki z pakietu Office sieci dostarczania zawartości (CDN) i tworzenie i wdrażanie aplikacji skryptów, plików.

Jest to szczególnie przydatne, ponieważ aktualizacje usługi Office 365 nie są stosowane dla klientów bez zainstalowane usługi Office 365. Przed wersją 1702 do zainstalowania aplikacji Office 365 po raz pierwszy na komputerach klienckich, należy ręcznie pobrać Office 365 wdrożenia Tool (ODT) i pliki źródłowe instalacji usługi Office 365, w tym wszystkie pakiety językowe, które są potrzebne, i wygenerować Configuration.xml, określający poprawną wersję pakietu Office i kanał. Następnie należy utworzyć i wdrożyć starszej wersji pakietu lub aplikacji skryptu dla klientów w celu zainstalowania aplikacji Office 365.

> [!NOTE]
> - Komputer, który jest uruchamiany Instalator Office 365 musi mieć dostęp do Internetu.  
> - Użytkownik uruchamiający Instalatora Office 365 musi mieć **odczytu** i **zapisu** dostęp do udostępnionej lokalizacji zawartości jest podany w kreatorze.
> - Jeśli zostanie wyświetlony błąd pobierania 404, skopiuj następujące pliki do folderu temp % % użytkownika:
>    - [releasehistory.XML](http://officecdn.microsoft.com.edgesuite.net/wsus/releasehistory.cab)
>    - [o365client_32bit.XML](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  
> - Po utworzeniu i wdrażania aplikacji Office 365 za pomocą pakietu Office 365 Instalator programu Configuration Manager nie mogą zarządzać aktualizacji pakietu Office domyślnie. Aby umożliwić klientom usługi Office 365 otrzymywać aktualizacje programu Configuration Manager, zobacz [wdrażanie usługi Office 365 aktualizacji z programu Configuration Manager](#deploy-office-365-updates-with-configuration-manager).

### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Do wdrażania aplikacji Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klientami usługi Office 365
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365**.
2. Kliknij przycisk **Office 365 Instalator** w prawym górnym okienku. Zostanie otwarty Kreator instalacji klienta Office 365.
3. Na **ustawienia aplikacji** , podaj nazwę i opis aplikacji, wprowadź lokalizację pobierania plików, a następnie kliknij przycisk **dalej**. Należy zauważyć, że lokalizacja musi być określony w formie &#92; &#92; *server*&#92; *udostępnianie*.
4. Na **importowania ustawień klienta** wybierz, czy do importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML lub ręcznie określ ustawienia, a następnie kliknij przycisk **dalej**.  

    Gdy istniejący plik konfiguracyjny, wprowadź lokalizację pliku, a następnie przejdź do kroku 7. Należy zauważyć, że lokalizacja musi być określony w formie &#92; &#92; *server*&#92; *udostępnianie*&#92;* Nazwa pliku*. PLIK XML.
5. Na **produkty klienta** , Office 365 wybierz pakiet, który można użyć, wybierz aplikacje, które chcesz dołączyć, zaznacz dodatkowe produkty pakietu Office, które powinny być uwzględnione, a następnie kliknij **dalej**.
6. Na **ustawień klienta** wybierz ustawienia do uwzględnienia, a następnie kliknij przycisk **dalej**.
7. Na **wdrożenia** wybierz, czy wdrożyć aplikację, a następnie kliknij przycisk **dalej**.  
Jeśli nie wdrożyć pakiet w kreatorze, przejdź do kroku 9.
8. W pozostałej części strony kreatora należy skonfigurować, tak jak w przypadku wdrażania Typowa aplikacja. Aby uzyskać szczegółowe informacje, zobacz [tworzenia i wdrażania aplikacji](/sccm/apps/get-started/create-and-deploy-an-application).
9. Ukończ pracę kreatora.
10. Można wdrożyć lub edytować aplikację, podobnie jak dowolnej innej aplikacji w programie Configuration Manager z **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **aplikacji**.   

> [!IMPORTANT]
> Aplikacji Office 365, który można utworzyć i wdrożyć za pomocą Kreatora aplikacji Office 365 w programie Configuration Manager nie jest automatycznie zarządzane przez program Configuration Manager do momentu włączenia **włączyć funkcję zarządzania Office 365 klienta ponownie** ustawienia agenta klienta aktualizacji oprogramowania. Aby uzyskać szczegółowe informacje, zobacz [informacje o ustawieniach klienta](/sccm/core/clients/deploy/about-client-settings).

>[!NOTE]
>Po wdrożeniu aplikacji Office 365, można utworzyć reguły automatycznego wdrażania do obsługi aplikacji. Aby utworzyć regułę automatycznego wdrażania dla aplikacji usługi Office 365, kliknij przycisk **utworzyć ADR** z pulpitu nawigacyjnego zarządzania klientami usługi Office 365, a następnie wybierz **Office 365 klienta** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).

<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->

