---
title: "Gotowość do uaktualnienia | System Center Configuration Manager"
description: "Integracja z programem Configuration Manager gotowości do uaktualnienia. Dane zgodności z uaktualnieniem dostępu w konsoli administracyjnej. Urządzenia docelowe dla uaktualnienia lub korygowania."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 7/31/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: b1f4cd4a6f19a02d2b2dc3f9a841aeeb2a1403dd
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Integracja gotowości do uaktualnienia z programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Gotowości do uaktualnienia (dawniej uaktualnienia Analytics) umożliwia ocenę i analizowania gotowości urządzenia z systemem Windows 10. Integracja z programem Configuration Manager dostępu do danych zgodności z uaktualnieniem klienta w konsoli administracyjnej programu Configuration Manager gotowości do uaktualnienia. Jesteś w stanie na urządzenia docelowe dla uaktualnienia lub korygowanie z listy urządzeń.

Gotowości do uaktualnienia to rozwiązanie pakiet zarządzania Operations (OMS) firmy Microsoft. Więcej o uaktualnienie gotowości w [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Konfigurowanie klientów

Istnieje kilka kroków konfiguracji, które należy wykonać, aby upewnić się, że klientów można udostępniać danych gotowości do uaktualnienia:

-  Skonfiguruj ustawienia klienta telemetrii w sposób opisany w [telemetrii Konfigurowanie systemu Windows w Twojej organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).
-  Zainstaluj KB/s, opisanego w * wdrażanie zgodności aktualizacji i powiązane KB/s * sekcji [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

    > [!NOTE]
    > Można pobrać skryptu można zautomatyzować wiele zadań instalacji klienta. Zobacz *Uruchom skrypt wdrażania gotowości do uaktualnienia* sekcji [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness) informacji o skrypcie.

## <a name="connect-to-upgrade-readiness"></a>Nawiązać gotowości do uaktualnienia

### <a name="prerequisites"></a>Wymagania wstępne

Począwszy od wersji Current Branch 1706, Kreator usług Azure jest używana w celu uproszczenia procesu konfigurowania usług platformy Azure, których korzystasz z programu Configuration Manager. Aby można było używać kreatora, musisz skonfigurować aplikację sieci web platformy Azure. Aby uzyskać więcej informacji zobacz, [Kreator usług Azure](/sccm/core/servers/deploy/configureazure-services-wizard).

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Kreator Azure do utworzenia połączenia

1.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, a następnie kliknij przycisk **usług Azure**.
2.  Na **Home** karcie **usług Azure** kliknij przycisk **Konfigurowanie usług Azure**.
3.  Wprowadź przyjazną nazwę, na stronie usług Azure. Możesz również wpisać opis. Następnie wybierz **uaktualnienia łącznik gotowości** i kliknij przycisk **dalej**.
4.  Określ środowisku platformy Azure na stronie aplikacji. Kliknij przycisk **Przeglądaj** do konfigurowania aplikacji serwera.
5.  Kliknij przycisk **importu** do nawiązania połączenia aplikacji sieci Web na platformie Azure.
    -  Typ **nazwa dzierżawy usługi Azure AD**.
    -  Typ **Identyfikatora dzierżawy usługi Azure AD**.
    -  Typ **Nazwa aplikacji**.
    -  Typ **identyfikator klienta**.
    -  Typ **klucz tajny**.
    -  Wybierz datę **wygaśnięcia klucz tajny** daty.
    -  Wpisz dowolny adres URL dla **aplikacji identyfikator URI**.
    -  Kliknij przycisk **Sprawdź**, a następnie kliknij przycisk **OK**.

6.  Na stronie konfiguracji, należy określić połączenie gotowości do uaktualnienia. Wybierz następujące wartości:  
    -  Subskrypcje platformy Azure
    -  Grupy zasobów platformy Azure
    -  Obszar roboczy w module analiz systemu Windows
8.  Kliknij przycisk **Dalej**. Możesz przejrzeć połączenia, na stronie podsumowania. 

## <a name="complete-upgrade-readiness-tasks"></a>Wykonywanie zadań uaktualniania gotowości  

Po utworzeniu już połączenia, należy wykonać te zadania, zgodnie z opisem w [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).  

1. Dodaj usługę UpgradeReadiness z obszarem roboczym pakietu OMS.  
2. Generowanie komercyjnych identyfikatora.  
3. Subskrybuj gotowości do uaktualnienia.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>Użyj skryptu wdrażania gotowości do uaktualnienia  

Można zautomatyzować wiele zadań uaktualniania gotowości i rozwiązywanie problemów z danych udostępnianie problemy dotyczące programu Microsoft **skrypt wdrożenia uaktualnienia gotowości**.  
Skrypt wdrożenia uaktualnienia gotowości wykonuje następujące czynności:  

- Ustawia komercyjnych klucza Identyfikatora + CommercialDataOptIn + RequestAllAppraiserVersions kluczy.  
- Sprawdza, czy komputery użytkownik może wysyłać dane do firmy Microsoft.  
- Sprawdza, czy komputer ma oczekuje na ponowne uruchomienie.   
- Sprawdza, czy najnowszą wersję KB pakietu 10.0.x zainstalowano (wymaga 10.0.14913 lub kolejnych wersjach).  
- U możliwia powoduje włączenie trybu informacji pełnej do rozwiązywania problemów.  
- Powoduje zainicjowanie zbierania danych telemetrii, wymagającym firmy Microsoft do oceny gotowości do uaktualnienia danej organizacji.  
- Po włączeniu są wyświetlane w oknie cmd postępu skryptu. To zapewnia wgląd w problemów (powodzenie lub Niepowodzenie dla każdego kroku) i/lub zapisuje w pliku dziennika.  

## <a name="to-run-the-upgrade-readiness-deployment-script"></a>Aby uruchomić skrypt wdrożenia gotowości do uaktualnienia:  

1. Pobierz [skrypt wdrożenia uaktualnienia gotowości](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409) i wyodrębniać UpgradeReadiness.zip. Pliki w **diagnostyki** folderu są wymagane tylko wtedy, gdy planujesz uruchamianie skryptu w trybie awaryjnym.  
2. Edytowanie tych parametrów w RunConfig.bat:  
- Lokalizacja przechowywania informacji dziennika. Przykład: % SystemDrive%\URDiagnostics. Informacje dziennika można przechowywać na zdalnym udziale plików lub katalogiem lokalnym. Jeśli skrypt jest zablokowany z tworzenia dla podanej ścieżki pliku dziennika, tworzy pliki dziennika na dysku z katalogu systemu Windows.  
- Komercyjnych identyfikator klucza.  
- Domyślnie skrypt wysyła informacje dziennika do konsoli i pliku dziennika. Aby zmienić domyślne zachowanie, użyj jednej z następujących opcji:  
    - logMode = 0 dziennik, aby tylko konsoli  
    - logMode = 1 dziennik do pliku i konsoli  
    - logMode = 2 dziennik do pliku tylko  
    - Do rozwiązywania problemów, należy ustawić **isVerboseLogging** do **$true** do generowania informacji dziennika, która może pomóc w diagnozowaniu problemów. Domyślnie **isVerboseLogging** ustawiono **$false**. Upewnij się, że folder diagnostycznych jest zainstalowany w tym samym katalogu co skrypt, który chcesz użyć w tym trybie.  
    - Powiadom użytkowników w przypadku konieczności ponownego uruchomienia komputera. To jest domyślnie wyłączone.  

3. Po zakończeniu edycji parametrów w RunConfig.bat, uruchom skrypt jako administrator.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Wyświetl właściwości Microsoft gotowości uaktualnienia w programie Configuration Manager  

1.  W konsoli programu Configuration Manager, przejdź do **usługi w chmurze**, a następnie wybierz **łącznik OMS** otworzyć **właściwości połączenia OMS** strony.  

2.  Na tej stronie istnieją dwie karty:
  * **Usługi Azure Active Directory** karcie pokazuje Twojej **dzierżawy**, **identyfikator klienta**, **wygaśnięcia klucza tajnego klienta**, i umożliwia **Sprawdź** Twojego **klucza tajnego klienta** Jeśli wygasł.
  * **Gotowości do uaktualnienia** karcie pokazuje Twojej **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.

## <a name="view-and-use-the-upgrade-information"></a>Wyświetlanie i używanie informacje o uaktualnianiu

Po gotowości do uaktualnienia został zintegrowany z programem Configuration Manager, możesz wyświetlić analizy gotowości do uaktualnienia klientów i podjąć odpowiednie działania.

1. W konsoli programu Configuration Manager wybierz **monitorowanie** > **omówienie** > **gotowości do uaktualnienia**.
2. Przejrzyj dane, w tym stan gotowości do uaktualnienia i odsetek urządzeń z systemem Windows, które są raportowania danych telemetrycznych.
3. Można filtrować pulpit nawigacyjny, aby wyświetlić dane dla urządzenia w określonej kolekcji.
4. Możesz wyświetlić stan gotowości danego urządzenia i tworzenie kolekcji dynamicznych dla tych urządzeń, tak, aby uaktualnić tych urządzeń, jeśli jest to gotowe lub podjąć działania w celu dostosowania ich do stanu gotowości.

## <a name="create-a-connection-to-upgrade-readiness-1702-and-earlier"></a>Utwórz połączenie gotowości do uaktualnienia (1702 i starsze)

Przed 1706 gałęzi programu Configuration Manager, aby utworzyć połączenie do uaktualnienia gotowości wymagane następujące kroki.

### <a name="prerequisites"></a>Wymagania wstępne

- Aby dodać połączenie, najpierw należy skonfigurować środowiska programu Configuration Manager [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/). Po dodaniu połączenia ze środowiskiem go spowoduje także zainstalowanie programu Microsoft Monitoring Agent na komputerze, na którym działa ta rola systemu lokacji.
- Zarejestruj programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web" oraz możliwość uzyskania [identyfikator klienta z tej rejestracji](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania w usłudze Azure Active Directory.
- W portalu Azure, podaj aplikacji sieci web w zarejestrowany z uprawnieniami do OMS, zgodnie z opisem w [Podaj programu Configuration Manager z uprawnieniami do OMS](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > Podczas konfigurowania uprawnień dostępu OMS, należy wybrać **współautora** roli i przypisz mu uprawnienia do grupy zasobów w zarejestrowany aplikacji.

### <a name="create-the-connection"></a>Utwórz połączenie

1.  W konsoli programu Configuration Manager wybierz **administracji** > **usługi w chmurze** > **uaktualnienia łącznik gotowości** > **utworzyć połączenie uaktualnienia Analytics** można uruchomić **dodać uaktualnienia Kreator połączenia Analytics**.
3.  Na **usługi Azure Active Directory** ekranu, podaj **dzierżawy**, **identyfikator klienta**, i **klucza tajnego klienta**, a następnie wybierz pozycję **dalej**.
4.  Na **gotowości do uaktualnienia** ekranu, podać ustawienia połączenia, wypełniając Twojej **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.
5.  Sprawdź ustawienia połączenia w **Podsumowanie** ekranu, a następnie wybierz **dalej**.

    > [!NOTE]
    > Należy połączyć gotowości do uaktualnienia lokacji najwyższego poziomu w hierarchii. Jeśli możesz połączyć uaktualnienia gotowości do autonomicznej lokacji głównej, a następnie dodać centralną lokację administracyjną do środowiska, należy usunąć i Utwórz ponownie połączenie OMS w nowej hierarchii.

