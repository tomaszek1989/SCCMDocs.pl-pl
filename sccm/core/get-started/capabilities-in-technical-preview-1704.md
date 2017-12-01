---
title: Funkcje w wersji zapoznawczej Technical Preview 1704
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1704."
ms.custom: na
ms.date: 4/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: 9151d2e60bbdc3ac4c34bde17f02fc956cb005b1
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1704 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1704. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>Konfigurowanie aplikacji systemu Android przy użyciu zasad konfiguracji aplikacji
Zasady konfiguracji aplikacji w programie System Center Configuration Manager (program Configuration Manager) można użyć do dystrybucji ustawień, które mogą być wymagane, jeśli użytkownik uruchamia aplikację w systemie Android pracy urządzeń. Zasady konfiguracji aplikacji systemu android są dostępne tylko na urządzeniach z systemem Android do pracy i dotyczą zatwierdzonych aplikacji w sklepie Play pracy magazynu.

### <a name="try-it-out"></a>Podczas próby                 

W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **zasady konfiguracji aplikacji** i wybierz polecenie **Tworzenie zasad konfiguracji aplikacji**. Na **ogólne** strony kreatora, możesz teraz **wybierz typ zasad konfiguracji**. Określ platformy docelowej zasady konfiguracji aplikacji: **Zasady konfiguracji dla systemu Android dla aplikacji służbowych**. Można następnie **Określ pary nazwa-wartość** lub **przejdź do pliku JSON listy właściwości**. Nowe zasady konfiguracji aplikacji jest wyświetlany w obszarze **Biblioteka oprogramowania** obszaru roboczego w **zasady konfiguracji aplikacji** węzła. Aby skojarzyć zasady konfiguracji aplikacji z wdrożeniem systemu android dla aplikacji do pracy, Wdróż aplikację w zwykły sposób za pomocą procedury w [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications) tematu.

## <a name="hardware-inventory-collects-secure-boot-information"></a>Spisu sprzętu zbiera informacje Bezpieczny rozruch
Spis sprzętu teraz zbiera informacje o czy Bezpieczny rozruch jest włączony na komputerach klienckich. Te informacje są przechowywane w **SMS_Firmware** klasy (wprowadzonych w wersji 1702) i włączone w sprzętu, spisu domyślnie. Aby uzyskać więcej informacji dotyczących zapasów sprzętu, zobacz [jak skonfigurować spis sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Dodaj do sekwencji zadań sekwencje zadań podrzędnych
W tej wersji można dodać nowy krok sekwencji zadań uruchamiana innej sekwencji zadań, która tworzy relacji nadrzędny/podrzędny między sekwencji zadań. Dzięki temu można utworzyć więcej sekwencje zadań moduły, które można użyć ponownie.  

Należy rozważyć dodanie sekwencji zadań podrzędnych do sekwencji zadań:

- Sekwencje zadań nadrzędnych i podrzędnych skutecznie są połączone w jedną zasadę, która działa na kliencie.
- Dodaj sekwencję zadań podrzędnych, który jest elementem nadrzędnym innego sekwencji zadań nie jest obsługiwane.
- Środowisko jest globalnego. Na przykład jeśli zmiennej jest ustawiany przez sekwencję zadań nadrzędny i następnie zmienić przez sekwencję zadań podrzędnych, pozostaje zmiennej zmienić przenoszenie do przodu. Podobnie jeśli sekwencja zadań podrzędnych tworzy nową zmienną, zmienna jest dostępne dla pozostałych kroków w sekwencji zadań nadrzędnej.
- Komunikaty o stanie są wysyłane na normalny dla operacji sekwencji pojedyncze zadanie.
- Sekwencje zadań tworzyć wpisy w pliku smsts.log w nowy dziennik wpisów, dzięki któremu można wyczyścić podczas sekwencji zadań podrzędnych rozpoczyna się.
- W wersji Technical Preview programu Configuration Manager, wersja 1704, sekwencje zadań podrzędnych odwołuje się do dowolnego pakietu i uruchomienia sekwencji zadań nadrzędnego z Centrum oprogramowania klienta nie będzie zawierał zawartość pakietu po uruchomieniu sekwencji zadań podrzędnych. W tym scenariuszu, należy uruchomić z nośnika sekwencji zadań (rozruchu środowiska PXE, nośnika itp.).  

    Jeśli sekwencja zadań podrzędnych używa kroków, takich jak **Uruchom wiersz polecenia** (bez żadnych odwołanie pakietu), **Format**, **funkcji BitLocker**itp., a następnie sekwencja zadań będzie uruchamiana pomyślnie w programie Software Center.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Możesz dodać sekwencję zadań podrzędnych do sekwencji zadań
1. W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i kliknij przycisk **uruchamiania sekwencji zadań**.
2. Kliknij przycisk **Przeglądaj** do wybierania sekwencji zadań podrzędnych.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>Załaduj ponownie obrazy rozruchowe z bieżącej wersji systemu Windows PE
Po uruchomieniu **Aktualizuj punkty dystrybucji** na wybranego obrazu rozruchowego, teraz możesz ponownie załadować najnowszą wersję środowiska Windows PE (w katalogu instalacyjnym zestawu Windows ADK) do obrazu rozruchowego. **Ogólne** kreatora zawiera informacje o wersji zestawu Windows ADK na serwerze lokacji, wersja zestawu Windows ADK, w którym użyto środowiska Windows PE w obrazie rozruchowym i wersja klienta programu Configuration Manager. Można użyć te informacje ułatwiające podjęcie decyzji o ponowne załadowanie obrazu rozruchowego. Ponadto nową kolumnę (**wersji klienta**) został dodany podczas wyświetlania obrazów rozruchowych w **obrazów rozruchowych** węzeł, aby wiedzieć, jakiej wersji klienta programu Configuration Manager korzysta z każdego obrazu rozruchowego.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>Aby ponownie załadować obraz rozruchowy w bieżącej wersji systemu Windows PE

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **obrazów rozruchowych**.
2. Wybierz obraz rozruchowy, a następnie kliknij przycisk **Aktualizuj punkty dystrybucji**.
3. Na **ogólne** strony kreatora wybierz pozycję **Załaduj obraz rozruchowy przy użyciu bieżącej wersji systemu Windows PE z zainstalowany zestaw Windows ADK**.

## <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadzono następujące ulepszenia do wdrożenia systemu operacyjnego, będące wynikiem swoją opinię głosu użytkownika.

- [Nowy **wersji systemu operacyjnego** kolumny obrazów systemu operacyjnego](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): Dodano nową kolumnę o nazwie **wersji systemu operacyjnego** Aby wyświetlić wersję systemu operacyjnego dla obrazu, podczas wyświetlania informacji w **obrazów systemu operacyjnego** i **pakiety uaktualnień systemu operacyjnego** węzłów. Tylko wersję indeks pierwszego w. WIM jest wyświetlany. Przejdź do **szczegóły** kartę obraz, aby przejrzeć wersje systemu operacyjnego dla innych indeksów.

- [Bardziej efektywne rejestrowanie w Smsts.log](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): Począwszy od tej wersji, firma Microsoft nie są już zapisywania wpisów w pliku smsts.log CCM_CIVersionInfo.PolicyID informacji. Przed tą wersją może istnieć wiele wpisów z tymi informacjami, dokonujący twardych można znaleźć więcej informacji w pliku dziennika.
