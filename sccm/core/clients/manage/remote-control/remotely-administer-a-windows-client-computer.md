---
title: Zdalne administrowanie komputerem z systemem Windows
titleSuffix: Configuration Manager
description: "Administrowanie zdalny komputer kliencki z systemem Windows przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 07/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 7cce5f2deab7ec6f5c16628dc53e4d1cb5507f37
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>Zdalne administrowanie komputerem klienckim z systemem Windows przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zanim rozpoczniesz korzystanie z funkcji zdalnego sterowania, przejrzyj informacje w następujących tematach:  

-   [Wymagania wstępne dotyczące zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

Poniżej przedstawiono trzy sposoby uruchamiania przeglądarki zdalnego sterowania:  

-   W konsoli programu Configuration Manager.  

-   W wierszu polecenia systemu Windows.  

-   W systemie Windows **Start** menu na komputerze, na którym uruchomiona jest konsola programu Configuration Manager z **programu Microsoft System Center** grupę programów.  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Zdalne administrowanie komputerem klienckim z poziomu konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń** lub **kolekcje urządzeń**.  

3.  Wybierz komputer, który chcesz zdalnie administrować, a następnie w **Home** karcie **urządzenia** grupy, wybierz **Start** > **zdalnego sterowania**.  

    > [!IMPORTANT]  
    >  Jeśli uprawnienie ustawienia klienta **Monituj użytkownika o zezwolenie na zdalne sterowanie** ma wartość **Prawda**, połączenie nie zostanie zainicjowane do momentu zaakceptowania monitu zdalnego sterowania przez użytkownika na zdalnym komputerze. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).  

4.  Po otwarciu okna **Zdalne sterowanie programu Configuration Manager** możesz zdalnie administrować komputerem klienckim. Użyj następujących opcji, aby skonfigurować połączenie:  

    > [!NOTE]  
    >  Jeśli na komputerze, na którym jest nawiązywane połączenie wiele monitorów, wyświetlanie wszystkich monitorów jest wyświetlany w oknie zdalnego sterowania.  

    -   **Plik — Połącz** -połączyć z innym komputerem. Ta opcja jest niedostępna, gdy sesja zdalnego sterowania jest aktywna.  

    -   **Plik — Rozłącz** — rozłącza aktywną sesję zdalnego sterowania, ale nie zamyka **zdalne sterowanie programu Configuration Manager** okna.  

    -   **Plik — Zakończ** — rozłącza aktywną sesję zdalnego sterowania i zamyka **zdalne sterowanie programu Configuration Manager** okna.  

        > [!NOTE]  
        >  Po rozłączeniu sesji zdalnego sterowania zawartość schowka systemu Windows na przeglądanym komputerze jest usuwana.  

    -   **Widok — pełny ekran** — maksymalizuje **zdalne sterowanie programu Configuration Manager** okna.  

        > [!NOTE]  
        >  Aby wyjść z trybu pełnego ekranu, naciśnij klawisze Ctrl+Alt+Break.  

    -   **Widok — Skaluj do rozmiaru** — skaluje ekran komputera zdalnego, aby dopasować rozmiar **zdalne sterowanie programu Configuration Manager** okna.  

    -   **Widok — Pasek stanu** — Przełącza wyświetlanie **zdalne sterowanie programu Configuration Manager** paska stanu okna.  

    -   **AKCJA — Wyślij klawisze Ctrl + Alt + Del klucza** — wysyła kombinację klawiszy Ctrl + Alt + Del do zdalnego komputera.  

    -   **Akcja — Włącz udostępnianie Schowka** — umożliwia kopiowanie i wklejanie elementów do i z komputerem zdalnym. Jeśli zmienisz tę wartość, musisz uruchomić ponownie sesję zdalnego sterowania, aby zmiany zaczęły obowiązywać.  

        > [!NOTE]  
        >  Jeśli nie chcesz Schowka udostępnianie być włączona w konsoli programu Configuration Manager na komputerze z konsolą, ustaw wartość klucza rejestru **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing** do **0**.  

    -   **Akcja — Zablokuj zdalną klawiaturę i mysz** — blokuje zdalną klawiaturę i mysz, aby uniemożliwić użytkownikowi korzystania z komputera zdalnego.  

    -   **Pomoc — informacje o zdalnym sterowaniu** -Wyświetla ithe bieżącej wersji przeglądarki.  

5.  Użytkownicy na komputerze zdalnym, można wyświetlić więcej informacji na temat sesji zdalnego sterowania, gdy użytkownik klika polecenie programu Configuration Manager**zdalnego sterowania** ikonę w obszarze powiadomień systemu Windows lub ikonę na pasku sesji zdalnego sterowania.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>Uruchamianie przeglądarki zdalnego sterowania z wiersza polecenia systemu Windows  

-   W wierszu polecenia systemu Windows wpisz *< Folder instalacji programu Configuration Manager\>***\AdminConsole\Bin\x64\CmRcViewer.exe**  

Program CmRcViewer.exe obsługuje następujące opcje wiersza polecenia:  

- *Adres* — Określa nazwę NetBIOS, w pełni kwalifikowaną nazwę (FQDN) lub adres IP komputera klienckiego, który chcesz nawiązać połączenie.
- *Nazwa serwera lokacji* — Określa nazwę serwera lokacji programu System Center Configuration Manager, do którego chcesz wysyłać komunikaty o stanie, które są powiązane z sesji zdalnego sterowania.
- **/?** — Wyświetla opcje wiersza polecenia dla przeglądarki zdalnego sterowania.  
     
**Example:CmRcViewer.exe** *< adres\>*   *< \\\Site nazwa serwera >*  
