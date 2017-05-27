---
title: "Gotowość do uaktualnienia | System Center Configuration Manager"
description: "Integracja z programem Configuration Manager gotowości do uaktualnienia. Dane zgodności z uaktualnieniem dostępu w konsoli administracyjnej. Urządzenia docelowego do uaktualnienia lub korygowania."
keywords: 
author: brenduns
ms.author: brenduns
manager: angerobe
ms.date: 3/1/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcbcd57b95f304f007e92ebe2b9aeefb4b579662
ms.openlocfilehash: 986d0446209f6e7eac1b681066d1b2e2305e1975
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Integracja z programem System Center Configuration Manager gotowości do uaktualnienia
Gotowości do uaktualnienia (dawniej Uaktualnij Analytics) umożliwia oceny i analizowanie gotowości urządzenia i zgodności z systemem Windows 10, aby umożliwić łatwiejsze i sprawniej uaktualnień. Integrowanie gotowości do uaktualnienia z programu Configuration Manager do uzyskiwania dostępu do danych zgodności z uaktualnieniem klienta w konsoli administracyjnej programu Configuration Manager. Następnie będzie można urządzeń docelowych, uaktualnienia lub korygowania z listy urządzeń.

Gotowość do uaktualnienia to rozwiązanie w Microsoft Operations Management Suite (usługi OMS). Więcej informacji dotyczących uaktualniania gotowości w [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Konfigurowanie klientów

Istnieje kilka kroków konfiguracji, które należy wykonać w celu zapewnienia, że klienci mogą zapewniają danych gotowości do uaktualnienia:

-  Konfigurowanie ustawień telemetrii klienta, zgodnie z opisem w [telemetrii Konfigurowanie systemu Windows w organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).
-  Zainstaluj KB/s, opisanego w * wdrażania zgodności aktualizacji i powiązane KB/s * części [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

    > [!NOTE]
    > Można pobrać skryptu, aby zautomatyzować wiele zadań instalacji klienta. Zobacz *Uruchom skrypt wdrożenia gotowości do uaktualnienia* części [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness) informacji o skrypt.

## <a name="create-a-connection-to-upgrade-readiness"></a>Utwórz połączenie z gotowości do uaktualnienia

### <a name="prerequisites"></a>Wymagania wstępne

- Aby dodać połączenie, najpierw skonfigurować środowiska programu Configuration Manager [punktem połączenia usługi](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/). Po dodaniu połączenia do środowiska, również zainstalowania programu Microsoft Monitoring Agent na komputerze, na którym działa ta rola systemu lokacji.
- Rejestrowania programu Configuration Manager jako narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web" i Uzyskaj [Identyfikatora klienta z tej rejestracji](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Utwórz klucz klienta dla narzędzia do zarządzania zarejestrowanych w usłudze Azure Active Directory.
- W portalu zarządzania Azure dostarczyć aplikacji sieci web zarejestrowanych uprawnień dostępu do usługi OMS, zgodnie z opisem w [zapewniają programu Configuration Manager z uprawnieniami do usługi OMS](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > Podczas konfigurowania uprawnień dostępu do usługi OMS, należy wybrać **współautora** roli i przypisz mu uprawnienia do grupy zasobów zarejestrowanych aplikacji.

### <a name="create-the-connection"></a>Utwórz połączenie

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **usług w chmurze** > **łącznika gotowości uaktualnienia** > **Utwórz połączenie do uaktualnienia Analytics** uruchomić **dodać uaktualnienia Kreatora połączenia Analytics**.
3.  Na **Azure Active Directory** ekranu, podaj **dzierżawy**, **Identyfikatora klienta**, i **klucz tajny klienta**, a następnie zaznacz pozycję **dalej**.
4.  Na **gotowości do uaktualnienia** ekranu, podaj ustawienia połączenia, wypełniając swoje **subskrypcji Azure**, **grupy zasobów Azure**, i **roboczym pakiet zarządzania Operations**.
5.  Sprawdź ustawienia połączenia na **Podsumowanie** ekranu, a następnie wybierz **dalej**.

    > [!NOTE]
    > Muszą łączyć gotowości do uaktualnienia lokacji najwyższego poziomu w hierarchii. Czy możesz połączyć uaktualniania gotowości do autonomicznej lokacji głównej, a następnie dodać witryny Administracja centralna w danym środowisku, należy usunąć i ponownie utwórz połączenia usługi OMS w nowej hierarchii.

### <a name="complete-upgrade-readiness-tasks"></a>Wykonywanie zadań gotowości do uaktualnienia  

Gdy połączenie został utworzony w programie Configuration Manager, należy wykonać te zadania, zgodnie z opisem w [wprowadzenie gotowości do uaktualnienia](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).  

1. Dodaj usługę UpgradeReadiness do obszaru roboczego usługi OMS.  
2. Generowanie komercyjnych identyfikatora.  
3. Subskrybuj gotowości do uaktualnienia.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>Użyj skryptu wdrażania gotowości do uaktualnienia  

Można zautomatyzować wiele zadań gotowości do uaktualnienia i rozwiązywanie problemów z danych udostępniania problemów z programem Microsoft **gotowości do uaktualnienia wdrożenia skryptu**.  
Skrypt wdrożenia gotowości do uaktualnienia wykonuje następujące czynności:  

- Ustawia komercyjnych identyfikator klucza + CommercialDataOptIn + RequestAllAppraiserVersions kluczy.  
- Sprawdza użytkowników komputerów mogą wysyłać dane do firmy Microsoft.  
- Sprawdza, czy komputer ma oczekuje na ponowne uruchomienie.   
- Sprawdza, czy KB najnowszą wersję pakietu 10.0.x jest zainstalowany (wymaga 10.0.14913 lub późniejszych wersji).  
- Jeśli włączona, włącza tryb pełnej informacji o rozwiązywaniu problemów.  
- Inicjuje zbierania danych telemetrii, wymagające oceny gotowości do uaktualnienia firmy Microsoft.  
- Jeśli włączona, wyświetla postęp skryptu w oknie cmd wgląd w przypadku problemów (powodzenie lub Niepowodzenie dla każdego kroku) i/lub zapisuje w pliku dziennika.  

### <a name="to-run-the-upgrade-readiness-deployment-script"></a>Aby uruchomić skrypt wdrożenia gotowości do uaktualnienia:  

1. Pobierz [skrypt wdrożenia gotowości do uaktualnienia](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409) i Wyodrębnij UpgradeReadiness.zip. Pliki w **diagnostyki** folderu są niezbędne tylko wtedy, gdy planujesz do uruchomienia skryptu w trybie awaryjnym.  
2. Edytuj tych parametrów w RunConfig.bat:  
- Lokalizacja przechowywania informacji dziennika. Przykład: % SystemDrive%\URDiagnostics. Informacje dziennika można przechowywać w katalogu lokalnym lub zdalnym udziale plików. Jeśli skrypt zostanie zablokowany od utworzenia pliku dziennika dla danej ścieżki, tworzy pliki dziennika na dysku z katalogu systemu Windows.  
- Komercyjne identyfikator klucza.  
- Domyślnie skrypt wysyła informacje dziennika do konsoli i pliku dziennika. Aby zmienić to zachowanie domyślne, użyj jednej z następujących opcji:  
    - logMode = 0 dziennik, aby tylko konsoli  
    - logMode = 1 dziennika do pliku i konsoli  
    - logMode = 2 dziennika tylko plików  
    - W celu rozwiązania problemu, należy ustawić **isVerboseLogging** do **$true** do generowania informacji dziennika, które mogą pomóc w diagnozowaniu problemów. Domyślnie **isVerboseLogging** jest ustawiona na **$false**. Upewnij się, że folder diagnostyki jest zainstalowany w tym samym katalogu co skrypt do użycia w tym trybie.  
    - Powiadomienie użytkowników w razie potrzeby ponownego uruchomienia komputera. To jest domyślnie wyłączona.  

3. Po zakończeniu edycji parametrów w RunConfig.bat, uruchom skrypt jako administrator.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Wyświetl właściwości Microsoft gotowości uaktualnienia w programie Configuration Manager  

1.  W konsoli programu Configuration Manager, przejdź do **usług w chmurze**, następnie wybierz **łącznika usługi OMS** otworzyć **właściwości połączenia usługi OMS** strony.  

2.  Na tej stronie istnieją dwie karty:
  * **Azure Active Directory** karcie pokazuje swoje **dzierżawy**, **Identyfikatora klienta**, **wygaśnięcia klucza tajnego klienta**, i umożliwia **Sprawdź** z **klucz tajny klienta** Jeśli wygasł.
  * **Gotowości do uaktualnienia** karcie pokazuje swoje **subskrypcji Azure**, **grupy zasobów Azure**, i **roboczym pakiet zarządzania Operations**.

## <a name="view-and-use-the-upgrade-information"></a>Wyświetlanie i używanie informacje dotyczące uaktualniania

Po gotowości do uaktualnienia zostały zintegrowane z programem Configuration Manager, można wyświetlić analizy gotowości do uaktualnienia z klientów, a następnie podjęcia działania.

1. W konsoli programu Configuration Manager wybierz **monitorowanie** > **Przegląd** > **gotowości do uaktualnienia**.
2. Sprawdź dane, w tym stan gotowości do uaktualnienia i procent urządzeń z systemem Windows, które są reporting telemetrii.
3. Można filtrować pulpitu nawigacyjnego, aby wyświetlić dane dla urządzenia w określonej kolekcji.
4. Można wyświetlić stan gotowości określonego urządzenia i tworzenie kolekcji dynamicznych dla tych urządzeń, aby uaktualnić te urządzenia, jeśli jest to gotowe, lub podjąć działania w celu dostosowania ich do stanu gotowości.

