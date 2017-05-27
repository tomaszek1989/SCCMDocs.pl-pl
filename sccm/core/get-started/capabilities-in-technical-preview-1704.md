---
title: "Możliwości w Technical Preview 1704 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, 1704 wersji."
ms.custom: na
ms.date: 4/21/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: d7caee47ca74064630e09c1bdb94187af256d4b4
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1704 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, 1704 wersji. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>Konfigurowanie aplikacji systemu Android za pomocą zasad konfiguracji aplikacji
Można użyć zasad konfiguracji aplikacji w System Center Configuration Manager (Menedżer konfiguracji) aby dystrybuować ustawień, które mogą być wymagane, gdy użytkownik uruchamia aplikację w systemie Android pracy urządzeń. Zasady konfiguracji systemu android aplikacji są dostępne tylko na urządzeniach z systemem Android do pracy i stosuje się do aplikacji zatwierdzone w grze dla sklepu pracy.

### <a name="try-it-out"></a>Wypróbuj to                 

W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **zasady konfiguracji aplikacji** i wybierz polecenie **Tworzenie zasad konfiguracji aplikacji**. Na **ogólne** strony kreatora, możesz teraz **wybierz typ zasad konfiguracji**. Określ platformy zasadom konfiguracji aplikacji: **Zasady konfiguracji dla systemu Android dla aplikacji do pracy**. Następnie możesz albo **Określ nazwę i pary wartości** lub **przejdź do pliku JSON listy właściwości**. Nowe zasady konfiguracji aplikacji jest wyświetlana w **Biblioteka oprogramowania** obszaru roboczego, w **zasady konfiguracji aplikacji** węzła. Aby skojarzyć zasady konfiguracji aplikacji z wdrażaniem systemu Android dla pracy aplikacji, wdrożenie aplikacji w zwykły sposób za pomocą procedury w [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications) tematu.

## <a name="hardware-inventory-collects-secure-boot-information"></a>Spis sprzętu zbiera informacje Bezpieczny rozruch
Spis sprzętu teraz zbiera informacje o czy Bezpieczny rozruch jest włączona na komputerach klienckich. Te informacje są przechowywane w **SMS_Firmware** klasy (wprowadzonych w wersji 1702) i włączone w sprzętu spisu domyślnie. Aby uzyskać więcej informacji na temat zapasów sprzętu, zobacz [Konfigurowanie spisu sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Dodaj sekwencji zadań podrzędnych do sekwencji zadań
W tej wersji można dodać nowej sekwencji zadań z systemem innym sekwencji zadań, co powoduje utworzenie relacji nadrzędny/podrzędny między sekwencji zadań. Dzięki temu można utworzyć więcej sekwencji zadań moduły, które można ponownie użyć.  

Dodaj sekwencji zadań podrzędnych do sekwencji zadań, Uwzględnij następujące kwestie:

- Sekwencje zadań nadrzędne i podrzędne skutecznie są łączone w jednej zasady, które klient uruchamia.
- Dodaj sekwencji zadań podrzędnych, która jest elementem nadrzędnym innego sekwencji zadań nie jest obsługiwane.
- Środowisko jest globalne. Na przykład jeśli zmienna jest zestawu nadrzędnego sekwencji zadań, a następnie zmienione przez sekwencję zadań podrzędnych, pozostanie zmiennej zmieniony przenoszenie do przodu. Podobnie jeśli sekwencja zadań podrzędnych tworzy nową zmienną, zmienna jest dostępna dla pozostałych kroków w sekwencji zadania nadrzędnego.
- Komunikaty o stanie są wysyłane na normalny pojedyncze zadanie sekwencji operacji.
- Sekwencje zadań tworzyć wpisy w pliku smsts.log z dziennikiem nowych wpisów, które go wyczyścić, jeśli sekwencja zadań podrzędnych rozpoczyna się.
- W Technical Preview dla programu Configuration Manager, wersja 1704, sekwencje zadań podrzędnych odwołuje się do dowolnego pakietu i uruchomienia sekwencji zadań nadrzędnego z Centrum oprogramowania, klient nie znajdzie zawartości pakietu podczas uruchamiania sekwencji zadań podrzędnych. W tym scenariuszu należy uruchomić z nośnika sekwencji zadań (rozruchu środowiska PXE, nośnika itp.).  

    Jeśli sekwencja zadań podrzędnych używa kroków, takich jak **Uruchom wiersz polecenia** (bez jakiegokolwiek odniesienia pakiet), **Format**, **funkcji BitLocker**itp., a następnie sekwencja zadań zostanie pomyślnie uruchomione z Centrum oprogramowania.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Aby dodać sekwencji zadań podrzędnych do sekwencji zadań
1. W edytorze sekwencji zadań, kliknij przycisk **Add**, wybierz opcję **ogólne**i kliknij przycisk **uruchamiania sekwencji zadań**.
2. Kliknij przycisk **Przeglądaj** do wybierania sekwencji zadań podrzędnych.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>Załaduj ponownie obrazy rozruchowe z bieżącą wersję środowiska Windows PE
Po uruchomieniu **Aktualizuj punkty dystrybucji** na wybranego obrazu rozruchowego, teraz można ponownie załadować najnowszą wersję środowiska Windows PE (w katalogu instalacyjnym zestawu Windows ADK) w obrazie rozruchowym. **Ogólne** strona kreatora zawiera informacje o wersji zestawu Windows zainstalowane na serwerze lokacji, wersji zestawu Windows ADK, z którego użyto środowiska Windows PE w obrazie rozruchowym, a wersja klienta programu Configuration Manager. Te informacje służą ułatwiające podjęcie decyzji o ponowne załadowanie obrazu rozruchowego. Ponadto nową kolumnę (**wersji klienta**) został dodany podczas wyświetlania obrazów rozruchowych w **obrazów rozruchowych** węzeł, aby wiedzieć, jakie wersje klienta programu Configuration Manager używa każdego obrazu rozruchowego.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>Aby ponownie załadować obraz rozruchowy z bieżącą wersją systemu Windows PE

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **obrazów rozruchowych**.
2. Wybierz obraz rozruchowy, a następnie kliknij przycisk **Aktualizuj punkty dystrybucji**.
3. Na **ogólne** w kreatorze Wybierz **obrazu rozruchowego Załaduj ponownie przy użyciu bieżącej wersji środowiska Windows PE z zainstalowany zestaw Windows ADK**.

## <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadzono następujące ulepszenia wprowadzone do wdrożenia systemu operacyjnego, będące wynikiem opinii głosu użytkownika.

- [Nowy **wersji systemu operacyjnego** kolumny obrazów systemu operacyjnego](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): Dodaliśmy nową kolumnę o nazwie **wersji systemu operacyjnego** Aby wyświetlić wersję systemu operacyjnego obrazu podczas wyświetlania informacji w **obrazów systemu operacyjnego** i **pakiety uaktualnienia systemu operacyjnego** węzłów. Tylko wersję pierwszego indeksu w. Zostanie wyświetlony WIM. Przejdź do **szczegóły** kartę obraz, aby przejrzeć wersje systemu operacyjnego dla innych indeksów.

- [Rejestrowanie bardziej wydajne w Smsts.log](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): Począwszy od tej wersji, firma Microsoft nie są już zapisywanie wpisów w pliku smsts.log CCM_CIVersionInfo.PolicyID informacji. Przed tą wersją może występować wiele wpisów z tymi informacjami, dokonujący trudno znaleźć bardziej istotne informacje w pliku dziennika.

