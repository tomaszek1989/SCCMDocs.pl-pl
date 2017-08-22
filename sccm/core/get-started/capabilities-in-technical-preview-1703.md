---
title: Funkcje w wersji zapoznawczej Technical Preview 1703 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1703."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e801f8c-d331-41ee-8f27-908448fc0951
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: bb1b96a56db68dcea22270855b899ba3a90afd0d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1703 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1703. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Wdrażanie aplikacji dla systemu iOS zakupionymi zbiorczo do kolekcji urządzeń

Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od aplikacji możliwość obsługi urządzenia licencjonowania odpowiednią licencję będzie wymagana, wdrażając go w następujący sposób:

|||||
|-|-|-|-|
|Wersja programu Configuration Manager|Aplikacja obsługuje licencjonowania urządzeń?|Typ kolekcji wdrażania|Oświadczeniem licencji|
|Wcześniejsza niż 1702|Tak|Użytkownik|Licencja użytkownika|
|Wcześniejsza niż 1702|Nie|Użytkownik|Licencja użytkownika|
|Wcześniejsza niż 1702|Tak|Urządzenie|Licencja użytkownika|
|Wcześniejsza niż 1702|Nie|Urządzenie|Licencja użytkownika|
|1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Tak|Urządzenie|Licencja urządzenia|
|1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

Aby uzyskać więcej informacji o aplikacji dla systemu iOS zakupionymi zbiorczo, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

## <a name="direct-links-to-applications-in-software-center"></a>Linki bezpośrednie do aplikacji w programie Software Center

Teraz możesz zapewnić użytkownikom końcowym bezpośredniego łącza do aplikacji w programie Software Center. Oznacza to, że ich już przed należy otworzyć programu Software Center i Wyszukaj aplikację można go zainstalować. Jest dostępna tylko w przypadku programu Configuration Manager aplikacji, nie pakietów i programów i sekwencji zadań.

### <a name="try-it-out"></a>Podczas próby                 

Użyj następującego formatu adresu URL, aby otworzyć Centrum oprogramowania do konkretnej aplikacji:

**Softwarecenter:SoftwareId =*identyfikator aplikacji***

### <a name="how-to-get-the-application-identifier-of-an-application"></a>Jak uzyskać identyfikator aplikacji dla aplikacji.

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2.  W obszarze roboczym Biblioteka oprogramowania rozwiń **Zarządzanie aplikacjami**, a następnie kliknij przycisk **aplikacji**.
3.  W **aplikacji** wyświetlić, kliknij prawym przyciskiem myszy jeden z nagłówków kolumn, a następnie, na liście, wybierz **Unikatowy identyfikator elementu konfiguracji**. Zobaczysz, że Unikatowy identyfikator każdego aplikacji jest teraz wyświetlane na liście.
4.  Uwaga **Unikatowy identyfikator elementu konfiguracji** z aplikacji, którą chcesz udostępnić łącze do, na przykład: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**
5.  Następnie usunąć wszelkie tekst, w tym przypadku następujący identyfikator GUID, aplikacji **/2**. Pozostawia identyfikator aplikacji.
6.  Na koniec na zakończenie tworzenia łącza, należy poprzedzić go z **Softwarecenter:SoftwareID =**. W powyższym przykładzie odczyta końcowe łącza: **Softwarecenter:SoftwareId = ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

Za pomocą tego łącza, użytkownicy końcowi mogą otworzyć programu Software Center bezpośrednio do wskazanej aplikacji.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>Certyfikaty PFX dla komputerów klienckich programu Configuration Manager systemu Windows

Teraz można wdrożyć profile certyfikatów PFX zaimportowane do programu Configuration Manager komputery klienckie z systemem Windows 10.

### <a name="try-it-out"></a>Podczas próby

Postępuj zgodnie z instrukcjami w [jak tworzyć profile certyfikatów PFX](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) do zaimportowania profilu PFX, wdrażanie profilu, a następnie sprawdź, czy certyfikat został zainstalowany dla użytkownika docelowego.



## <a name="configure-azure-services-wizard"></a>Konfiguracja usług Azure — Kreator
Wersja zapoznawcza Technical preview 1703 wprowadza **Konfigurowanie usług Azure** kreatora. Ten kreator zapewnia typowych konfiguracji zastępujący poszczególnych przepływy pracy, aby skonfigurować usługi w chmurze, których korzystasz z programu Configuration Manager. Jest to zrobić za pomocą **aplikacji sieci web Azure** zapewnienie Szczegóły subskrypcji i konfiguracji, które należy wprowadzić w przeciwnym razie zawsze należy skonfigurować nowego składnika programu Configuration Manager lub usługi platformy Azure.

Technical preview 1703 tylko Sklepu Windows dla firm (WSfB) jest skonfigurowany za pomocą tego kreatora.  Inne usługi w chmurze są skonfigurowane przy użyciu ich oddzielne przepływów pracy.

-   Użyj informacje w tym temacie Podgląd, aby zamienić czynności konfiguracyjne znajdują [— konfiguracja Sklepu Windows dla firm synchronizacji](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#set-up-windows-store-for-business-synchronization) tematu Current Branch [Zarządzanie aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

-   Aby uzyskać więcej informacji dotyczących aplikacji sieci web, zobacz [uwierzytelnianie i autoryzację w usłudze Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview), i [Omówienie aplikacji sieci Web](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview).

### <a name="prerequisites-and-planning"></a>Wymagania wstępne i planowania
Po skonfigurowaniu połączenia programu Configuration Manager i w Sklepie Windows dla firm, należy podać folder, w której będą przechowywane zawartości aplikacji ze sklepu. Aby upewnić się, że ten folder jest bezpieczne i że jego zawartość można wdrożyć na urządzeniach, upewnij się, że zostały spełnione następujące uprawnienia:
-   Komputer, na którym należy zainstalować usługi roli lokacji punktu połączenia systemu (lokacji najwyższego poziomu w hierarchii) musi mieć uprawnienia odczytu i zapisu do folderu, należy określić podczas używania **komputera$** konta.  

-   Autor aplikacji musi mieć uprawnienia do odczytu w podanym folderze.  

-   **Komputera$** konta poszczególnych komputerów, który hostuje wystąpienie dostawcy programu SMS musi mieć możliwość użycia określonego folderu.

W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzie do zarządzania interfejsu API sieci Web lub aplikacji sieci web. Spowoduje to utworzenie Identyfikatora klienta, który będzie potrzebny później.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>Użyj kreatora, aby skonfigurować usługę w chmurze WSfB

1. W konsoli przejdź do **administracji** > **omówienie** > **zarządzania usługami w chmurze** > **Azure** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure** uruchomić **Kreator usług Azure**.

2. Na **usług Azure** wybierz usługi, które chcesz skonfigurować, a następnie kliknij przycisk **dalej**. W tej wersji zapoznawczej można skonfigurować tylko WSfB.

3. Na **ogólne** Podaj przyjazną nazwę dla **nazwy usługi Azure** i opcjonalny opis, a następnie kliknij przycisk **dalej**.

4. Na **aplikacji** , określ środowisku platformy Azure, a następnie kliknij przycisk **Przeglądaj** można otworzyć okna aplikacji serwera.

5. W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**.
Aplikacje serwera są aplikacjami sieci web platformy Azure, które zawierają konfiguracje dla konta platformy Azure, w tym Identyfikatora dzierżawy, identyfikator klienta i klucz tajny dla klientów. Jeśli nie ma dostępnego serwera aplikacji, użyj jednej z następujących czynności:
  - **Utwórz**: Aby utworzyć nową aplikację serwera, kliknij przycisk **Utwórz**. Podaj przyjazną nazwę dla aplikacji i dzierżawcy. Następnie po możesz zalogować się do platformy Azure, programu Configuration Manager utworzy aplikacji sieci web na platformie Azure, w tym identyfikator klienta i klucz tajny do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.
  - **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po **Sprawdź** informacji, kliknij przycisk **OK** aby kontynuować.  </br></br>

6. Przegląd **informacji** strony i wykonać wszelkie dodatkowe kroki i konfiguracje, zgodnie z instrukcją. Te konfiguracje są niezbędne do korzystania z usługi z programem Configuration Manager.
Na przykład, aby skonfigurować WSfB:

  1. Na platformie Azure musisz zarejestrować programu Configuration Manager jako interfejs API sieci Web lub aplikacji sieci web i zarejestrować identyfikator klienta. Możesz również określić klucz klienta do użycia przez narzędzie do zarządzania (czyli programu Configuration Manager).

  2.    W konsoli WSfB musi skonfigurować programu Configuration Manager jako narzędzie do zarządzania magazynami, umożliwia obsługę aplikacji licencjonowanych w trybie offline, a następnie Kup co najmniej jedną aplikację.   </br>

  Kliknij przycisk **dalej** po osiągnięciu gotowości kontynuować.

7. Na **konfiguracji aplikacji** ukończenia konfiguracji katalogu i język aplikacji dla tej usługi, a następnie kliknij przycisk **dalej**.
8. Po zakończeniu działania kreatora, konsoli programu Configuration Manager pokazuje, że skonfigurowano **Sklep Windows dla firm** jako **typu usługi w chmurze**.

Teraz można używać w pozostałej części [zawartość bieżącej gałęzi](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) do zarządzania aplikacjami z WSfB do synchronizowania, tworzenie i wdrażanie i monitorowanie Sklepu Windows dla aplikacji biznesowych.

### <a name="modify-a-cloud-service-configuration"></a>Modyfikowanie konfiguracji usługi chmury
Można wyświetlić i edytować właściwości usługi chmury, aby zmodyfikować konfigurację.

W konsoli przejdź do **administracji** > **omówienie** > **zarządzania usługami w chmurze** > **Azure** > **usług Azure**, a następnie wybierz pozycję **Konfigurowanie usług Azure**, wybierz usługę w chmurze, a następnie wybierz pozycję **właściwości**.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu
Windows 10 twórców aktualizacji wprowadzono narzędzie konwersji proste automatyzuje proces ponownego podziału dysku twardego z obsługą interfejsu UEFI sprzętu i integruje narzędzia konwersji system Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Połączenie to narzędzie z sekwencji zadań uaktualniania systemu operacyjnego i narzędzie OEM, który konwertuje oprogramowanie układowe BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS na UEFI podczas uaktualniania w miejscu do systemu Windows 10 twórców aktualizacji. Aby uzyskać więcej informacji, zobacz [zadania sekwencji kroki, aby zarządzać systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

## <a name="collapsible-task-sequence-groups"></a>Grupy sekwencji zadań zwijanej
W tej wersji wprowadzono możliwość rozwijanie i zwijanie grupy sekwencji zadań. Można rozwinąć lub zwinąć poszczególnych grup lub rozwiń lub Zwiń wszystkie grupy w jednocześnie.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>Ustawienia klienta, aby skonfigurować module analiz systemu Windows pod kątem gotowości do uaktualnienia
Począwszy od tej wersji, można użyć ustawień klienta urządzenia uproszczenie konfiguracji koniecznych do używania telemetrii Windows [module analiz systemu Windows](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) rozwiązań, takich jak [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) z programem Configuration Manager. Program Configuration Manager można pobrać danych w module analiz systemu Windows, która może zapewnić wartościowe informacje do bieżącego stanu środowiska na podstawie danych telemetrycznych Windows zgłoszonych przez komputery klienckie. Dane telemetryczne systemu Windows jest zgłoszonych przez komputery klienckie do telemetrii usługi systemu Windows, a następnie przetransferowana odpowiednie dane do rozwiązań module analiz systemu Windows, które znajdują się w jednym z obszarów roboczych OMS Twojej organizacji. Gotowości do uaktualnienia to rozwiązanie module analiz systemu Windows, które mogą pomóc ustalić ich priorytety decyzji dotyczących uaktualniania systemu Windows dla zarządzanych urządzeń.

Informacji o ustawienia telemetrii systemu Windows, temacie [telemetrii Konfigurowanie systemu Windows w Twojej organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).

### <a name="prerequisites"></a>Wymagania wstępne
- Należy skonfigurować witrynę tak, aby używać usługi w chmurze gotowości do uaktualnienia. Aby uzyskać więcej informacji, zobacz [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics)

### <a name="configure-windows-analytics-client-settings"></a>Konfigurowanie ustawień klienta w module analiz systemu Windows
Aby skonfigurować module analiz systemu Windows, w konsoli programu Configuration Manager przejdź do **administracji** > **ustawień klienta**, kliknij dwukrotnie **Tworzenie ustawień klienta urządzenia niestandardowe** , a następnie sprawdź **module analiz systemu Windows**.  

Następnie należy skonfigurować następujące po nawigowania do **module analiz systemu Windows** kartę Ustawienia:
- **Identyfikator komercyjnych**  
Klucz identyfikator komercyjnych mapuje informacje z urządzeń, które można zarządzać w obszarze roboczym pakietu OMS obsługującego danych organizacji w module analiz systemu Windows. Jeśli skonfigurowano już program komercyjnych identyfikator klucza do użycia z gotowości do uaktualnienia, używają tego identyfikatora. Jeśli nie masz jeszcze komercyjnych klucza Identyfikatora, zobacz [generowanie klucza komercyjnych identyfikator]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

- Ustaw **poziom Telemetrii dla urządzeń z systemem Windows 10**   
Aby uzyskać informacje, jakie informacje są zbierane na każdym poziomie telemetrii systemu Windows 10, zobacz [telemetrii Konfigurowanie systemu Windows w Twojej organizacji]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

- Wybierz **wyrazić zgodę na zbieranie danych komercyjnych na urządzeniach z systemem Windows 7, 8 i 8.1**   
Dla informacje o danych zbieranych z tych systemów operacyjnych po możesz zdecydować się na, zobacz Pobierz [pola i Windows 7, Windows 8 i Windows 8.1 zdarzenia telemetrii appraiser](https://go.microsoft.com/fwlink/?LinkID=822965) plik pdf firmy Microsoft.

- **Konfigurowanie zbierania danych Internet Explorer** na urządzeniach z systemem Windows 8.1 lub starszy, zbierania danych w programie Internet Explorer można zezwolić na uaktualnienie gotowości do wykrycia niezgodności aplikacji sieci web, które mogą uniemożliwić sprawnego przebiegu uaktualnienia do systemu Windows 10. Zbieranie danych z programu Internet Explorer można włączyć dla poszczególnych strefy internet. Aby uzyskać więcej informacji o strefach internetowych, zobacz [o strefach zabezpieczeń adresu URL](https://msdn.microsoft.com/en-us/library/ms537183(v=vs.85).aspx).