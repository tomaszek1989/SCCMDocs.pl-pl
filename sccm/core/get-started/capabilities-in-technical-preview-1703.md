---
title: "Możliwości w Technical Preview 1703 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1703."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e801f8c-d331-41ee-8f27-908448fc0951
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: bb1b96a56db68dcea22270855b899ba3a90afd0d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1703 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1703. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Wdrażanie aplikacji iOS kupionymi woluminu do kolekcji urządzeń

Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od funkcji aplikacji do obsługi urządzeń licencjonowania odpowiedniej licencji będzie wymagana podczas wdrażania, w następujący sposób:

|||||
|-|-|-|-|
|Wersja programu Configuration Manager|Aplikacja obsługuje licencjonowania urządzenia?|Typ kolekcji wdrożenia|Oświadczeniem licencji|
|Starsze niż 1702|Tak|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Nie|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Tak|Urządzenie|Licencja użytkownika|
|Starsze niż 1702|Nie|Urządzenie|Licencja użytkownika|
|1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Tak|Urządzenie|Licencję urządzenia|
|1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

Aby uzyskać więcej informacji o aplikacjach iOS kupionymi woluminu, zobacz [zarządzania aplikacjami zakupione woluminu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

## <a name="direct-links-to-applications-in-software-center"></a>Łączy bezpośrednich do aplikacji w Centrum oprogramowania

Użytkownicy końcowi mogą dostarczać teraz bezpośredniego łącza do aplikacji w Centrum oprogramowania. Oznacza to, że ich nie będzie już musi otworzyć wyszukiwania dla aplikacji i Centrum oprogramowania przed zainstalowaniem. Jest dostępna tylko dla programu Configuration Manager aplikacji, nie pakietów i programów i sekwencji zadań.

### <a name="try-it-out"></a>Wypróbuj to                 

Aby otworzyć Centrum oprogramowania w konkretnej aplikacji, należy użyć następującego formatu adresu URL:

**Softwarecenter:SoftwareId =*identyfikator aplikacji***

### <a name="how-to-get-the-application-identifier-of-an-application"></a>Jak uzyskać identyfikator aplikacji dla aplikacji.

1.    W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2.    W obszarze roboczym Biblioteka oprogramowania rozwiń listę **zarządzania aplikacjami**, a następnie kliknij przycisk **aplikacji**.
3.    W **aplikacje** wyświetlić, kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie, z listy wybierz **Unikatowy identyfikator elementu konfiguracji**. Zobaczysz, że Unikatowy identyfikator każdego aplikacji jest teraz wyświetlane na liście.
4.    Uwaga **Unikatowy identyfikator elementu konfiguracji** z aplikacji, którą chcesz udostępnić łącze do, na przykład: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**
5.    Następnie usunąć dowolny tekst, w tym przypadku po zastosowaniu identyfikatora GUID, **/2**. Pozostawia identyfikator aplikacji.
6.    Na koniec na zakończenie tworzenia łącza, należy poprzedzić go z **Softwarecenter:SoftwareID =**. W przykładzie powyżej łącze końcowego powinny wyglądać następująco: **Softwarecenter:SoftwareId = ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

Za pomocą tego łącza, użytkownicy końcowi można otworzyć programu Software Center bezpośrednio do określonej aplikacji.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>Certyfikaty PFX dla komputerów klienckich programu Configuration Manager systemu Windows

Teraz można wdrażać profile certyfikatów PFX zaimportowane do programu Configuration Manager komputerów klienckich z systemem Windows 10.

### <a name="try-it-out"></a>Wypróbuj to

Postępuj zgodnie z instrukcjami w [tworzenie profilów certyfikatów PFX](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) do zaimportowania profilu PFX, Wdróż profil, a następnie sprawdź, czy certyfikat został zainstalowany dla użytkownika docelowego.



## <a name="configure-azure-services-wizard"></a>Skonfiguruj kreatora usług Azure
Wprowadza Technical preview 1703 **Konfigurowanie usług Azure** kreatora. Ten kreator zawiera typowe środowisko konfiguracji, który zastępuje poszczególnych przepływy pracy, aby skonfigurować usługi w chmurze, których korzystasz z programu Configuration Manager. Jest to zrobić za pomocą **aplikacji sieci web platformy Azure** aby podać szczegóły subskrypcji i konfiguracji, wprowadzone w przeciwnym razie każdorazowo skonfiguruj nowy składnik programu Configuration Manager lub usługi w systemie Azure.

Podgląd techniczne 1703 tylko Sklepu Windows dla firm (WSfB) jest skonfigurowany za pomocą tego kreatora.  Inne usługi w chmurze są konfigurowane przy użyciu ich oddzielne przepływów pracy.

-    Użyj informacje w tym temacie Podgląd zastąpić kroki konfiguracji znaleźć w [Konfigurowanie Sklepu Windows dla synchronizacji Business](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#set-up-windows-store-for-business-synchronization) w temacie bieżącej gałęzi [zarządzania aplikacjami ze Sklepu Windows dla firm z programem System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

-    Aby uzyskać więcej informacji dotyczących aplikacji sieci web, zobacz [uwierzytelnianie i autoryzację w usłudze aplikacji Azure](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview), i [Omówienie aplikacji sieci Web](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview).

### <a name="prerequisites-and-planning"></a>Planowanie i wymagania wstępne
Po skonfigurowaniu połączenia między programu Configuration Manager i magazynu systemu Windows dla firmy, należy podać folder, w którym będą przechowywane zawartości aplikacji ze sklepu. Aby upewnić się, że ten folder jest zabezpieczony i że jego zawartość można wdrożyć na urządzeniach, upewnij się, że zostały spełnione następujące uprawnienia:
-    Komputer, na którym jest instalowany usługi połączenia punktu rolą systemu lokacji (lokacja najwyższego poziomu w hierarchii) musi mieć uprawnienia odczytu i zapisu do folderu określonego przy użyciu **$ komputera** konta.  

-    Autor aplikacji musi mieć uprawnienia do odczytu w podanym folderze.  

-    **$ Komputera** konto każdego komputera, który obsługuje wystąpienie dostawcy programu SMS musi mieć możliwość korzystania z tego folderu określone.

W usłudze Azure Active Directory należy zarejestrować jako narzędzia do zarządzania interfejsu API sieci Web lub aplikacji sieci web programu Configuration Manager. Spowoduje to utworzenie Identyfikatora klienta, który trzeba będzie później.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>Użyj kreatora, aby skonfigurować usługę w chmurze WSfB

1. W konsoli, przejdź do **Administracja** > **Przegląd** > **zarządzania usługami chmury** > **Azure** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure** uruchomić **kreatora usług Azure**.

2. Na **usług Azure** wybierz usługi, które chcesz skonfigurować, a następnie kliknij przycisk **dalej**. Za pomocą tej wersji zapoznawczej można skonfigurować tylko WSfB.

3. Na **ogólne** Podaj przyjazną nazwę **nazwa usługi Azure** i opcjonalny opis, a następnie kliknij przycisk **dalej**.

4. Na **aplikacji** określić środowisku platformy Azure, a następnie kliknij pozycję **Przeglądaj** otwarte okno aplikacji serwera.

5. W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**.
Aplikacje serwera są aplikacji sieci web platformy Azure, które zawierają konfiguracje dla Twojego konta platformy Azure, w tym Identyfikatora dzierżawcy, Identyfikatora klienta i klucz tajny dla klientów. Jeśli nie ma dostępnego serwera aplikacji, użyj jednej z następujących czynności:
  -    **Utwórz**: Aby utworzyć nową aplikację serwera, kliknij przycisk **Utwórz**. Podaj przyjazną nazwę dla dzierżawcy i aplikacji. Następnie po możesz zalogować się do usługi Azure, programu Configuration Manager utworzy aplikacji sieci web w usłudze Azure, w tym identyfikator klienta i klucz tajny do użytku z aplikacji sieci web. Później można wyświetlić je z portalu Azure.
  -    **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w Twojej subskrypcji platformy Azure, kliknij przycisk **importowania**. Podaj przyjazną nazwę dla dzierżawcy i aplikacji, a następnie określ identyfikator dzierżawcy, Identyfikatora klienta i klucz tajny dla aplikacji sieci web platformy Azure, które program Configuration Manager do używania. Po **Sprawdź** informacji, kliknij przycisk **OK** aby kontynuować.  </br></br>

6. Przegląd **informacji** strony i wykonać wszelkie dodatkowe kroki i konfiguracje zgodnie ze wskazówkami. Te konfiguracje są niezbędne do korzystania z usługi w programie Configuration Manager.
Na przykład, aby skonfigurować WSfB:

  1. W usłudze Azure musi zarejestrować jako interfejs API sieci Web lub aplikacji sieci web programu Configuration Manager i zapisać identyfikator klienta. Należy również określić klucz klienta do użycia przez narzędzia do zarządzania, (czyli programu Configuration Manager).

  2.    W konsoli WSfB należy skonfigurować program Configuration Manager jako narzędzie do zarządzania magazynami, włączyć obsługę trybu offline licencjonowane aplikacje i następnie zakupu co najmniej jednej aplikacji.   </br>

  Kliknij przycisk **dalej** po osiągnięciu gotowości do kontynuowania.

7. Na **konfiguracji aplikacji** ukończenia konfiguracji katalogu i język aplikacji dla tej usługi, a następnie kliknij przycisk **dalej**.
8. Po zakończeniu działania kreatora, konsoli programu Configuration Manager pokazuje, że skonfigurowano **Sklepu Windows dla firm** jako **typ usługi chmury**.

Możesz teraz użyć w pozostałej części [zawartość bieżącej gałęzi](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) do zarządzania aplikacjami z WSfB do synchronizowania, tworzenie i wdrażanie i monitorowanie Sklepu Windows dla aplikacji biznesowych.

### <a name="modify-a-cloud-service-configuration"></a>Modyfikowanie konfiguracji usługi chmury
Można wyświetlać i edytować właściwości można modyfikować konfiguracji usługi w chmurze.

W konsoli, przejdź do **Administracja** > **Przegląd** > **zarządzania usługami chmury** > **Azure** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure**, wybierz usługę chmury, a następnie wybierz **właściwości**.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwersji z systemu BIOS z interfejsem UEFI podczas uaktualnienia w miejscu
Windows 10 twórcy aktualizacji wprowadzono konwersji proste narzędzie, które automatyzuje proces na partycje dysk twardy sprzęt obsługujący UEFI i narzędzie konwersji integruje się z systemu Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Podczas tego narzędzia można połączyć z sekwencji zadań uaktualnienia systemu operacyjnego i narzędzia OEM, która konwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS z interfejsem UEFI podczas uaktualniania w miejscu do usługi Windows Update twórcy 10. Aby uzyskać szczegółowe informacje, zobacz [czynności sekwencji do zarządzania systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

## <a name="collapsible-task-sequence-groups"></a>Grupy sekwencji zadań zwijany
W tej wersji wprowadzono możliwość rozwijanie i zwijanie grup sekwencji zadań. Można rozwinąć lub zwinąć poszczególnych grup lub rozwiń lub Zwiń wszystkie grupy naraz.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>Ustawienia klienta, aby skonfigurować module analiz systemu Windows pod kątem gotowości do uaktualnienia
Począwszy od tej wersji, aby ułatwić konfigurację trzeba użyć telemetrii systemu Windows można użyć ustawień klienta urządzenia [module analiz systemu Windows](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) rozwiązań, takich jak [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) z programu Configuration Manager. Menedżer konfiguracji może pobrać danych module analiz systemu Windows, które zapewniają cenne informacje dotyczące bieżącego stanu środowiska na podstawie danych telemetrii Windows zgłaszane przez komputery klienckie. Dane telemetryczne systemu Windows jest zgłaszane przez komputery klienckie do usługi telemetrii systemu Windows, a następnie odpowiednich danych jest następnie przekazana do rozwiązania do analizowania systemu Windows, które znajdują się w jednym z obszarów roboczych usługi OMS w organizacji. Gotowość do uaktualnienia jest rozwiązaniem w module analiz systemu Windows, która ułatwia ustalenie priorytetów działań decyzje dotyczące uaktualnień systemu Windows dla zarządzanych urządzeń.

Informacje o ustawieniach telemetrii systemu Windows, zobacz [telemetrii Konfigurowanie systemu Windows w organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).

### <a name="prerequisites"></a>Wymagania wstępne
- Należy skonfigurować do korzystania z usługi chmury gotowości do uaktualnienia danej lokacji. Aby uzyskać więcej informacji, zobacz [gotowość do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics)

### <a name="configure-windows-analytics-client-settings"></a>Konfigurowanie ustawień klienta w module analiz systemu Windows
Aby skonfigurować module analiz systemu Windows, w konsoli programu Configuration Manager przejdź do **Administracja** > **ustawień klienta**, kliknij dwukrotnie **Tworzenie niestandardowych klienta ustawień urządzenia** , a następnie sprawdź **module analiz systemu Windows**.  

Następnie należy skonfigurować następujące po przejściu do **module analiz systemu Windows** karta Ustawienia:
- **Identyfikator komercyjnych**  
Komercyjne klucza Identyfikatora mapuje informacji z urządzeń, którymi zarządzasz do obszaru roboczego usługi OMS, który jest hostem danych organizacji w module analiz systemu Windows. Jeśli została już skonfigurowana komercyjnych klucz ID do użycia z gotowości do uaktualnienia, użyj tego identyfikatora. Jeśli nie masz jeszcze komercyjnych klucza Identyfikatora, zobacz [wygenerować klucz komercyjnych identyfikator]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

- Ustaw **poziom Telemetrii dla urządzeń z systemem Windows 10**   
Informacje o co to są zbierane przez każdy poziom telemetrii systemu Windows 10, zobacz [telemetrii Konfigurowanie systemu Windows w organizacji]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

- Wybierz do **wyrazić zgodę na zbieranie danych handlowych na urządzeniach z systemem Windows 7, 8 i 8.1**   
Dla podczas można zdecydować się na informacje o danych zbierane z tych systemów operacyjnych, zobacz Pobierz [zdarzenia telemetrii appraiser systemu Windows 7, Windows 8 i Windows 8.1 i pola](https://go.microsoft.com/fwlink/?LinkID=822965) plik pdf firmy Microsoft.

- **Konfigurowanie zbierania danych Internet Explorer** na urządzeniach z systemem Windows 8.1 lub starszym zbierania danych w programie Internet Explorer można zezwolić uaktualniania gotowości do wykrywania niezgodności aplikacji sieci web, które może uniemożliwić płynne uaktualnienia do systemu Windows 10. Zbieranie danych w programie Internet Explorer można włączyć na na podstawie strefy internet. Aby uzyskać więcej informacji dotyczących stref internet, zobacz [o strefy zabezpieczeń adresów URL](https://msdn.microsoft.com/en-us/library/ms537183(v=vs.85).aspx).
