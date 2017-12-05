---
title: "Narzędzie pobierania Instalatora"
titleSuffix: Configuration Manager
description: "Więcej informacji o tej aplikacji autonomicznej, mające na celu zapewnienie, że instalacji lokacji są używane bieżące wersje najważniejszych plików instalacyjnych."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bda87fc5-2e4c-4992-98a4-01770365038c
caps.latest.revision: "3"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: dec591ac845b6c54421197099e56d7a4a86783ae
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="setup-downloader-for-system-center-configuration-manager"></a>Narzędzie pobierania Instalatora programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed uruchomieniem Instalatora w celu instalacji lub uaktualnienia lokacji programu System Center Configuration Manager, można użyć narzędzia pobierania Instalatora aplikacji autonomicznej z wersji Menedżera konfiguracji, który chcesz zainstalować, aby pobrać zaktualizowane pliki Instalatora.  

Użycie zaktualizowanych plików Instalatora gwarantuje, że instalacji lokacji są używane bieżące wersje najważniejszych plików instalacyjnych. W oveview:   
-   Podczas pobierania plików przed rozpoczęciem instalacji za pomocą narzędzia pobierania Instalatora należy określić folder zawierający pliki.  
-   Konto używane do uruchamiania narzędzia pobierania Instalatora musi mieć **Pełna kontrola** uprawnienia do folderu pobierania.  
-   Po uruchomieniu Instalatora w celu instalacji lub uaktualnienia lokacji możesz określić, aby użyta ta lokalna kopia plików, które zostały wcześniej pobrane. Zapobiega to Instalatora nawiązywaniu połączenia z firmą Microsoft, po rozpoczęciu instalacji lub uaktualniania lokacji.  
-   Można użyć tej samej lokalnej kopii plików instalacyjnych dla kolejnych instalacji lub uaktualnień.  

Następujące pliki są pobierane przez narzędzie pobierania Instalatora:  
-   Pliki redystrybucyjne wymagań wstępnych  
-   Pakiety językowe  
-   Najnowsze aktualizacje produktu do instalacji  

Masz dwie opcje uruchamiania narzędzia pobierania Instalatora:
- Uruchom aplikację przy użyciu interfejsu użytkownika
- Dla opcji wiersza polecenia, uruchom aplikację w wierszu polecenia


## <a name="run-setup-downloader-with-the-user-interface"></a>Uruchom Narzędzie pobierania Instalatora z interfejsem użytkownika  

1.  Na komputerze, który ma dostęp do Internetu, otwórz Eksploratora Windows i przejdź do  **&lt;Nośnik_instalacyjny_programu_configmgr\>\SMSSETUP\BIN\X64**.  

2.  Aby otworzyć narzędzie pobierania Instalatora, kliknij dwukrotnie **Setupdl.exe**.   

3. Określ ścieżkę do folderu, który będzie obsługiwać zaktualizowane pliki instalacyjne, a następnie kliknij **Pobierz**. Narzędzie pobierania Instalatora weryfikuje pliki, które aktualnie znajdują się w folderze pobierania. Pobiera tylko te pliki, które nie istnieją lub są nowsze niż istniejące pliki. Narzędzie pobierania Instalatora tworzy podfolderów pobieranej wersji językowej i innych wymaganych podfolderów.  

4.  Aby przejrzeć wyniki pobierania, otwórz **ConfigMgrSetup.log** pliku w katalogu głównym dysku C.  .  

## <a name="run-setup-downloader-from-a-command-prompt"></a>Uruchom Narzędzie pobierania Instalatora z wiersza polecenia  

1.  W oknie wiersza polecenia, przejdź do  **&lt;* nośnika instalacyjnego programu Configuration Manager*\>\SMSSETUP\BIN\X64**.   

2.  Aby otworzyć narzędzie pobierania Instalatora, należy uruchomić **Setupdl.exe**.

    Korzystając z poniższych opcji wiersza polecenia z **Setupdl.exe**:   

    -   **/ SPRAWDŹ**: Użyj tej opcji, aby zweryfikować pliki w folderze pobierania, w tym pliki językowe. Przejrzyj plik ConfigMgrSetup.log w katalogu głównym dysku C, aby uzyskać listę plików, które są nieaktualne. Po wybraniu tej opcji są pobierane żadne pliki.  

    -   **/ VERIFYLANG**: Użyj tej opcji, aby zweryfikować pliki językowe w folderze pobierania. Przejrzyj plik ConfigMgrSetup.log w katalogu głównym dysku C, aby uzyskać listę plików językowych w starszych wersjach.

    -   **/ LANG**: Użyj tej opcji, aby pobrać pliki językowe do folderu pobierania.  

    -   **/ NOUI**: Użyj tej opcji, aby uruchomić Narzędzie pobierania Instalatora bez wyświetlania interfejsu użytkownika. Tej opcji należy określić **ścieżkę pobierania** jako część polecenia w wierszu polecenia.  

    -   **&lt;Ścieżka_pobierania\>**: Można określić ścieżkę do folderu pobierania, aby automatycznie rozpocząć weryfikację lub pobieranie. Należy określić ścieżkę pobierania, korzystając z **/noui** opcji. Jeśli ścieżka pobierania nie jest określony, należy określić ścieżkę po uruchomieniu narzędzia pobierania Instalatora. Narzędzie pobierania Instalatora tworzy folder, jeśli nie istnieje.  

    Przykładowe polecenia:

    -   **setupd &lt;Ścieżka_pobierania\>**  

        -   Narzędzie pobierania Instalatora uruchamia, zweryfikuje pliki w określonym folderze pobierania i następnie pobiera tylko te pliki, które nie istnieją lub nowsze wersje od istniejących plików, która ma.     

    -   **setupdl/verify &lt;Ścieżka_pobierania\>**  

        -   Narzędzie pobierania Instalatora zostanie uruchomione i zweryfikuje pliki w określonym folderze pobierania.  

    -   **setupdl/noui &lt;Ścieżka_pobierania\>**  

        -   Narzędzie pobierania Instalatora uruchamia, zweryfikuje pliki w określonym folderze pobierania i następnie pobiera tylko te pliki, które nie istnieją lub są nowsze niż istniejące pliki.  

    -   **setupdl/Lang &lt;Ścieżka_pobierania\>**  

        -   Narzędzie pobierania Instalatora rozpoczyna się, zweryfikuje pliki językowe w określonym folderze pobierania, a następnie pobierze pliki językowe brakujące lub są nowsze niż istniejące pliki.  

    -   **setupdl/verify**  

        -   Uruchamia narzędzie do pobierania Instalatora, a następnie należy określić ścieżkę do folderu pobierania. Następnie po kliknięciu **Sprawdź**, narzędzie pobierania Instalatora weryfikuje pliki w folderze pobierania.  

3.  Aby przejrzeć wyniki pobierania, otwórz **ConfigMgrSetup.log** pliku w katalogu głównym dysku C.
