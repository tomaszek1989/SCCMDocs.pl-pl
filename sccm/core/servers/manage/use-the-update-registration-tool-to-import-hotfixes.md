---
title: "Narzędzie rejestracji aktualizacji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, kiedy i jak ręcznie zaimportować aktualizację do konsoli programu Configuration Manager za pomocą narzędzia rejestracji aktualizacji."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cc13635-85d6-4b07-a3ec-c42188bc5c74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 35a4c201f73469fdfaa5bb8629e91886f7ae8751
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-update-registration-tool-to-import-hotfixes-to-system-center-configuration-manager"></a>Używanie narzędzia rejestracji aktualizacji do importowania poprawek do programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Niektóre aktualizacje programu Configuration Manager nie są dostępne z usługi w chmurze firmy Microsoft i są pobierane tylko poza pasmem. Przykładem jest ograniczona wersja poprawki rozwiązującej określony problem.   
Kiedy należy zainstalować wersji poza pasmem i nazwa pliku aktualizacja lub poprawka kończy się rozszerzeniem **update.exe**, można użyć **narzędzie rejestracji aktualizacji** ręcznie zaimportować aktualizację do konsoli programu Configuration Manager. Narzędzie pozwala wyodrębnić i przenieść pakiet aktualizacji do serwera lokacji i zarejestrować aktualizację za pomocą konsoli programu Configuration Manager.  

 Jeśli plik poprawki jest **.exe** rozszerzenie pliku (nie **update.exe**), zobacz [użyć instalatora poprawek do instalowania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  

> [!NOTE]  
>  W tym temacie przedstawiono ogólne wskazówki dotyczące sposobu instalacji poprawek, które aktualizują program System Center Configuration Manager. Szczegółowe informacje na temat poprawki lub aktualizacji można znaleźć jego odpowiedniego artykułu bazy wiedzy Knowledge Base (KB) w programie Microsoft Support.  

 **Wymagania wstępne dotyczące korzystania z narzędzia rejestracji aktualizacji:**  

-   W tym celu aktualizacji tylko poza pasmem **. update.exe** rozszerzenia można zainstalować przy użyciu tego narzędzia  

-   Narzędzie to jest autonomicznym z poszczególnych aktualizacji, które pojawia się bezpośrednio od firmy Microsoft  

-   Narzędzie nie ma zależności związanej z trybem punktu połączenia z usługą.  

-   Narzędzie należy uruchomić na komputerze hostującym punkt połączenia z usługą.  

-   Komputera, na którym działa (komputer punktu połączenia usługi) musi mieć 4,52 Framework .NET zainstalowana  

-   Konto używane do uruchamiania narzędzia musi mieć **administratora lokalnego** uprawnienia na komputerze, który jest hostem punktu połączenia usługi (gdzie uruchomienie narzędzia)  

-   Konto używane do uruchamiania narzędzia musi mieć **zapisu** uprawnień do folderu na komputerze, który obsługuje punkt połączenia usługi:  **&lt;Katalog instalacyjny programu ConfigMgr\>\EasySetupPayload\offline**  

### <a name="to-use-the-update-registration-tool"></a>Aby użyć narzędzia rejestracji aktualizacji  

1.  Na komputerze hostującym punkt połączenia z usługą:  

    -   Otwórz wiersz polecenia z uprawnieniami administracyjnymi, a następnie zmień katalogi na lokalizację zawierającą  **&lt;produktu\>-&lt;wersji produktu\>-&lt;identyfikator artykułu KB\>-ConfigMgr.Update.exe**  

2.  Uruchom następujące polecenie, aby uruchomić narzędzie rejestracji aktualizacji:  

    -   **&lt;Produkt\>-&lt;wersji produktu\>-&lt;identyfikator artykułu KB\>-ConfigMgr.Update.exe**  

    Po zarejestrowaniu poprawki pojawi się ona jako nowa aktualizacja w konsoli w ciągu 24 godzin.  Może przyspieszyć proces:

    - Otwórz konsolę programu Configuration Manager i przejdź do, aby **Administracja** > **aktualizacji i obsługi**, a następnie kliknij przycisk **wyszukiwanie aktualizacji**. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.) 

    Narzędzie rejestracji aktualizacji rejestruje swoje działania w pliku LOG na komputerze lokalnym. Plik dziennika ma taką samą nazwę jak plik .exe poprawki i jest zapisywany w **%SystemRoot%/Temp** folder.  

     Po zarejestrowaniu aktualizacji możesz zamknąć narzędzie rejestracji aktualizacji.  

3.  Otwórz konsolę programu Configuration Manager i przejdź do **Administracja** > **aktualizacji i obsługi**. Poprawki, które zostały zaimportowane, są teraz dostępne do zainstalowania. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.)

 Aby uzyskać informacje o instalowaniu aktualizacji, zobacz [instalowanie aktualizacji w konsoli programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  

