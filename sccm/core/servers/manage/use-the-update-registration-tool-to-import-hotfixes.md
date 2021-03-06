---
title: Narzędzie rejestracji aktualizacji
titleSuffix: Configuration Manager
description: Dowiedz się, kiedy i jak używać narzędzia rejestracji aktualizacji ręcznie zaimportować aktualizację do konsoli programu Configuration Manager.
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8cc13635-85d6-4b07-a3ec-c42188bc5c74
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d82ae79ae3466eff753e92c232b2cdd40fbcb2cb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-the-update-registration-tool-to-import-hotfixes-to-system-center-configuration-manager"></a>Używanie narzędzia rejestracji aktualizacji do importowania poprawek do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Niektóre aktualizacje programu Configuration Manager nie są dostępne z usługi w chmurze firmy Microsoft i są pobierane tylko poza pasmem. Przykładem jest ograniczona wersja poprawki rozwiązującej określony problem.   
Kiedy należy zainstalować wersji poza pasmem i nazwa pliku aktualizacji lub poprawki kończy się rozszerzeniem **update.exe**, możesz użyć **narzędzia rejestracji aktualizacji** ręcznie zaimportować aktualizację do konsoli programu Configuration Manager. Narzędzie pozwala wyodrębnić i przenieść pakiet aktualizacji do serwera lokacji i zarejestrować aktualizację za pomocą konsoli programu Configuration Manager.  

 Jeśli plik poprawki ma **.exe** rozszerzenie pliku (nie **update.exe**), zobacz [używania Instalatora poprawek do instalowania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  

> [!NOTE]  
>  W tym temacie przedstawiono ogólne wskazówki dotyczące sposobu instalacji poprawek, które aktualizują program System Center Configuration Manager. Szczegółowe informacje o konkretnej poprawki lub aktualizacji można znaleźć jego odpowiedni artykuł bazy wiedzy Knowledge Base (KB) w programie Microsoft Support.  

 **Wymagania wstępne dotyczące korzystania z narzędzia rejestracji aktualizacji:**  

-   Tylko poza pasmem aktualizacji w tym celu **. update.exe** rozszerzenia można zainstalować za pomocą tego narzędzia  

-   Narzędzie to jest autonomicznym środowiskiem z poszczególnymi aktualizacjami, które uzyskuje się bezpośrednio od firmy Microsoft  

-   Narzędzie nie ma zależności związanej z trybem punktu połączenia z usługą.  

-   Narzędzie należy uruchomić na komputerze hostującym punkt połączenia z usługą.  

-   Na komputerze, na którym działa narzędzie (komputer punktu połączenia usługi) musi być zainstalowane środowisko .NET Framework 4.52  

-   Konto używane do uruchamiania narzędzia musi mieć **administratora lokalnego** uprawnienia na komputerze, który hostuje punkt połączenia usługi (w którym narzędzie jest uruchamiane)  

-   Konto używane do uruchamiania narzędzia musi mieć **zapisu** uprawnienia do folderu na komputerze, który hostuje punkt połączenia z usługą:  **&lt;Katalog instalacyjny programu ConfigMgr\>\EasySetupPayload\offline**  

### <a name="to-use-the-update-registration-tool"></a>Aby użyć narzędzia rejestracji aktualizacji  

1.  Na komputerze hostującym punkt połączenia z usługą:  

    -   Otwórz wiersz polecenia z uprawnieniami administracyjnymi, a następnie przejdź do lokalizacji zawierającej  **&lt;produktu\>-&lt;wersji produktu\> - &lt;Identyfikator artykułu bazy wiedzy\>-ConfigMgr.Update.exe**  

2.  Uruchom następujące polecenie, aby uruchomić narzędzie rejestracji aktualizacji:  

    -   **&lt;Produkt\>-&lt;wersji produktu\>-&lt;identyfikator artykułu bazy wiedzy\>-ConfigMgr.Update.exe**  

    Po zarejestrowaniu poprawki pojawi się ona jako nowa aktualizacja w konsoli w ciągu 24 godzin.  Można przyspieszyć ten proces:

    - Otwórz konsolę programu Configuration Manager i przejdź do do **administracji** > **aktualizacje i obsługa**, a następnie kliknij przycisk **Sprawdź aktualizacje**. (Przed wersji 1702, aktualizacje i obsługa znajdowało się pod **administracji** > **usługi w chmurze**.) 

    Narzędzie rejestracji aktualizacji rejestruje swoje działania w pliku LOG na komputerze lokalnym. Plik dziennika ma taką samą nazwę jak plik .exe poprawki i jest zapisywany w **%SystemRoot%/Temp** folderu.  

     Po zarejestrowaniu aktualizacji możesz zamknąć narzędzie rejestracji aktualizacji.  

3.  Otwórz konsolę programu Configuration Manager i przejdź do **administracji** > **aktualizacje i obsługa**. Poprawki, które zostały zaimportowane, są teraz dostępne do zainstalowania. (Przed wersji 1702, aktualizacje i obsługa znajdowało się pod **administracji** > **usługi w chmurze**.)

 Aby uzyskać informacje o instalowaniu aktualizacji, zobacz [instalacja aktualizacji w konsoli programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  
