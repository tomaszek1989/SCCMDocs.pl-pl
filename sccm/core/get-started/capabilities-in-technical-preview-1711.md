---
title: Technical Preview 1711 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1711 programu System Center Configuration Manager."
ms.custom: na
ms.date: 11/17/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e68dc12-6776-437a-9138-45cd7d4bf9cf
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: b740c422a71e625ccc110a043028cf986cdffb20
ms.sourcegitcommit: ed8b2438ef85c9160741ef61f9171be41dd1ae0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2017
---
# <a name="capabilities-in-technical-preview-1711-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1711 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1711. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Znane problemy w tej wersji Technical Preview:**
-   **Obsługa systemu Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek)**.  Począwszy od tej wersji systemu Windows, Windows media zawiera wiele wersji. Podczas konfigurowania sekwencji zadań w celu za pomocą pakietu uaktualnienia systemu operacyjnego lub obrazu systemu operacyjnego, należy wybrać [wersję, która jest obsługiwana przez program Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).
-   **Aktualizacja do nowej wersji zapoznawczej nie powiedzie się, jeśli masz serwer lokacji w trybie pasywnym**. Podczas uruchamiania wersja zapoznawcza ma [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), należy odinstalować serwer lokacji w trybie pasywnym zanim może pomyślnie zaktualizować lokację w wersji zapoznawczej do nowej wersji zapoznawczej. Zakończone aktualizacji lokacji można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku, kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-to-run-task-sequence"></a>Ulepszenia uruchomić sekwencję zadań
<!-- 1261338 -->

Tej wersji technical preview zwiększy krok Uruchom sekwencję zadań. Ulepszenia obejmują następujące elementy:

 - Obsługa wszystkich scenariuszy wdrożenia systemu operacyjnego z Centrum oprogramowania, środowiska PXE oraz nośnika.
 - Ulepszenia konsoli akcji, takich jak kopiowanie, importu, eksportu i ostrzeżenie podczas usuwania obiektu.
 - Obsługa **Utwórz wstępnie przygotowany zawartość** kreatora.
 - Integracja z weryfikację wdrożenia.
 - Krok sekwencji zadań Uruchom można teraz używać na wielu poziomach sekwencji zadań, nie tylko relacje jeden nadrzędny podrzędny. Relacje wielopoziomowe zwiększenia złożoności, dlatego należy używać ostrożnie. Te relacje nadal są sprawdzane pod kątem odwołań cyklicznych.

### <a name="try-it-out"></a>Wypróbuj  

Spróbuj wykonać następujące zadania, a następnie wyślij do nas **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:

1. W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i kliknij przycisk **uruchamiania sekwencji zadań**.
2. Kliknij przycisk **Przeglądaj** do wybierania sekwencji zadań podrzędnych.

## <a name="allow-user-interaction-when-installing-an-application----1356976---"></a>Zezwala na interakcję użytkownika podczas instalowania aplikacji<!-- 1356976 -->

W tej wersji zapoznawczej można zezwolić użytkownikowi końcowemu możliwość interakcji z instalacją aplikacji, podczas uruchamiania sekwencji zadań. Na przykład uruchomić proces instalacji, które monituje użytkownika końcowego dla różnych opcji. Niektóre instalatory aplikacji nie może mieć zignorowane monity użytkownika lub proces instalacji może wymagać tylko znane użytkownikowi wartości określonej konfiguracji. Ta funkcja umożliwia obsługę tych scenariuszy instalacji.

### <a name="try-it-out"></a>Wypróbuj

Spróbuj wykonać następujące zadania, a następnie wyślij **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:

1.  Tworzenie lub edytowanie aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji w programie System Center Configuration Manager](/sccm/apps/deploy-use/create-applications).

    a. Wybierz **środowisko użytkownika** karcie **Instalatora Windows (\*pliku msi) właściwości**.

    b. Wybierz **zainstaluj dla systemu** dla **zachowanie podczas instalowania**.

    c. Wybierz **czy użytkownik jest zalogowany** dla **Zaloguj się na wymaganie**.

    d. Wybierz **normalny** dla **widoczność programu instalacyjnego**. Możesz wybrać spośród trzech opcji: **Zminimalizowany**, **normalny**, lub **zmaksymalizowane**.

    e. Wybierz **Zezwalaj użytkownikom na interakcję z instalacją programu** pole.

2.  Tworzenia lub edytowania sekwencji zadań w celu zainstalowania aplikacji przy użyciu **zainstaluj aplikację** kroku. Aby uzyskać więcej informacji, zobacz [zainstaluj aplikację](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication) w [kroki sekwencji zadań w programie System Center Configuration Manager](/sccm/osd/understand/task-sequence-steps).

    a. Tworzenie obrazu sekwencji zadań po wykonaniu kroku Zainstaluj system Windows i program Configuration Manager.

    b. W miejscu sekwencji zadań uaktualniania w grupie przetwarzania końcowego.

3.  Wdróż sekwencję zadań do klienta.
4.  Zainstalować sekwencję zadań w programie Software Center.

Podczas postęp sekwencji zadań zostanie wyświetlony interfejs instalacji aplikacji na urządzeniu docelowym przez użytkownika końcowego. Postęp sekwencji zadań wstrzymuje zakończenia przepływu pracy instalacji aplikacji przez użytkownika końcowego.

### <a name="install-using-the-wizard"></a>Zainstaluj za pomocą Kreatora

Umożliwia także tej funkcji w przypadku wdrażania aplikacji za pomocą kreatora.

1. Tworzenie lub edytowanie aplikacji.
2. Wdrażanie aplikacji na kliencie.
3. Instalować aplikacji z Centrum oprogramowania. Powinien zostać wyświetlony interfejs instalacji aplikacji. Użytkownik końcowy należy stosować Kreatora instalacji aplikacji i aplikacja zostanie zainstalowana pomyślnie.




<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
