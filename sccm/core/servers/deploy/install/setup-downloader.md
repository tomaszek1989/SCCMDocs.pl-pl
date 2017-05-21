---
title: "Narzędzie pobierania Instalatora | Dokumentacja firmy Microsoft"
description: "Więcej informacji o tej aplikacji autonomicznej mające na celu zapewnienie, że instalacji lokacji korzysta z bieżącej wersji plików instalacyjnych klucza."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bda87fc5-2e4c-4992-98a4-01770365038c
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34e24deb90a39bf655a2e24d16cdbe07528e6193
ms.openlocfilehash: b72148ecc16141843178cbd220fe021fab8be992
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="setup-downloader-for-system-center-configuration-manager"></a>Narzędzie pobierania Instalatora programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed uruchomieniem Instalatora w celu instalacji lub uaktualnienia lokacji programu System Center Configuration Manager, można użyć narzędzia pobierania Instalatora aplikacji autonomicznej z wersji Menedżera konfiguracji, który chcesz zainstalować, aby pobrać zaktualizowane pliki Instalatora.  

Użycie zaktualizowane pliki Instalatora gwarantuje, że instalacji lokacji korzysta z bieżącej wersji plików instalacyjnych klucza. W oveview:   
-   Korzystając z narzędzia pobierania Instalatora do pobierania plików przed uruchomieniem programu instalacyjnego, określ folderu zawierającego pliki.  
-   Konto używane do uruchamiania narzędzia pobierania Instalatora musi mieć **Pełna kontrola** uprawnień do folderu pobierania.  
-   Po uruchomieniu Instalatora w celu instalacji lub uaktualnienia lokacji można kierować do użycia tego lokalną kopię plików, które zostały wcześniej pobrane. Pozwala to uniknąć konieczności połączyć się z firmą Microsoft, podczas uruchamiania witryny instalacji lub uaktualniania formularza ustawień.  
-   Dla instalacji kolejnych lokacji lub uaktualnień, można użyć tego samego lokalną kopię plików instalacyjnych.  

Następujące pliki są pobierane przez narzędzie pobierania Instalatora:  
-   Pliki redystrybucyjne wymagań wstępnych  
-   Pakiety językowe  
-   Najnowsze aktualizacje produktu dla instalacji  

Dostępne są dwie opcje uruchamiania narzędzia pobierania Instalatora:
- Uruchom aplikację z interfejsem użytkownika
- Dla opcji wiersza polecenia należy uruchomić aplikację w wierszu polecenia


## <a name="run-setup-downloader-with-the-user-interface"></a>Uruchom Narzędzie pobierania Instalatora z interfejsem użytkownika  

1.  Na komputerze, który ma dostęp do Internetu, otwórz Eksploratora Windows i przejdź do  **&lt;Nośnikinstalacyjnyprogramuconfigmgr\>\SMSSETUP\BIN\X64**.  

2.  Aby otworzyć narzędzie pobierania Instalatora, kliknij dwukrotnie **Setupdl.exe**.   

3. Określ ścieżkę do folderu, który będzie obsługiwać zaktualizowane pliki instalacyjne, a następnie kliknij **pobrać**. Narzędzie pobierania Instalatora sprawdzi pliki znajdujące się aktualnie w folderze pobierania. Pobiera on tylko pliki, których brakuje lub które są nowsze od istniejących plików. Narzędzie pobierania Instalatora tworzy podfoldery dla każdej pobieranej wersji językowej i innych wymaganych podfolderów.  

4.  Aby przejrzeć wyniki pobierania, otwórz **ConfigMgrSetup.log** pliku w katalogu głównym dysku C.  .  

## <a name="run-setup-downloader-from-a-command-prompt"></a>Uruchom Narzędzie pobierania Instalatora z wiersza polecenia  

1.  W oknie wiersza polecenia, przejdź do  **&lt;* nośnika instalacyjnego programu Configuration Manager*\>\SMSSETUP\BIN\X64**.   

2.  Aby otworzyć narzędzie pobierania Instalatora, uruchom **Setupdl.exe**.

    Można użyć następujących opcji wiersza polecenia z **Setupdl.exe**:   

    -   **/ SPRAWDŹ**: Użyj tej opcji, aby sprawdzić pliki w folderze pobierania, w tym pliki językowe. Przejrzyj plik ConfigMgrSetup.log w katalogu głównym dysku C, aby uzyskać listę plików, które są nieaktualne. Po wybraniu tej opcji są pobierane żadne pliki.  

    -   **/ VERIFYLANG**: Użyj tej opcji, aby sprawdzić pliki językowe w folderze pobierania. Przejrzyj plik ConfigMgrSetup.log w katalogu głównym dysku C, lista plików języków, które są nieaktualne.

    -   **/LANG**: Tej opcji należy użyć, aby pobrać pliki językowe do folderu pobierania.  

    -   **/NOUI**: Tej opcji należy użyć, aby uruchomić Narzędzie pobierania Instalatora bez wyświetlania interfejsu użytkownika. Tej opcji należy określić **Pobierz ścieżkę** jako część polecenia w wierszu polecenia.  

    -   **&lt;Ścieżkapobierania\>**: Można określić ścieżkę do folderu pobierania, aby automatycznie rozpocząć weryfikację lub pobieranie plików. Należy podać ścieżkę pobierania, korzystając z **/noui** opcji. Jeśli nie określisz ścieżkę pobierania, należy określić ścieżkę po uruchomieniu narzędzia pobierania Instalatora. Narzędzie pobierania Instalatora tworzy folder, jeśli nie istnieje.  

    Przykład polecenia:

    -   **setupd &lt;Ścieżkapobierania\>**  

        -   Narzędzie pobierania Instalatora zostanie uruchomiony, weryfikuje pliki w folderze pobierania i pobiera tylko pliki, których brakuje lub nowsze wersje od istniejących plików, która ma.     

    -   **setupdl /VERIFY &lt;Ścieżkapobierania\>**  

        -   Narzędzie pobierania Instalatora zostanie uruchomione i sprawdzi pliki w folderze pobierania.  

    -   **setupdl/noui &lt;Ścieżkapobierania\>**  

        -   Narzędzie pobierania Instalatora zostanie uruchomiony, weryfikuje pliki w folderze pobierania i pobiera tylko pliki, których brakuje lub które są nowsze od istniejących plików.  

    -   **setupdl/Lang &lt;Ścieżkapobierania\>**  

        -   Narzędzie pobierania Instalatora zostanie uruchomiony, sprawdzi pliki językowe w folderze pobierania i pobiera pliki językowe których brakuje lub które są nowsze od istniejących plików.  

    -   **setupdl /VERIFY**  

        -   Uruchamia narzędzie pobierania Instalatora, a następnie należy określić ścieżkę do folderu pobierania. Następnie po kliknięciu **Sprawdź**, narzędzie pobierania Instalatora weryfikuje pliki w folderze pobierania.  

3.  Aby przejrzeć wyniki pobierania, otwórz **ConfigMgrSetup.log** pliku w katalogu głównym dysku C.

