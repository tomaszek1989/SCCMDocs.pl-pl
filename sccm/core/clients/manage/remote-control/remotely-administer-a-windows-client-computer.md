---
title: Zdalne administrowanie komputerem Windows | Dokumentacja firmy Microsoft
description: "Administrowanie komputera zdalnego klienta systemu Windows za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 63113a2928c0aca292e6ca07ffe1187324801b7b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>Jak zdalnie administrować komputer kliencki systemu Windows za pomocą programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zanim rozpoczniesz korzystanie z funkcji zdalnego sterowania, przejrzyj informacje w następujących tematach:  

-   [Wymagania wstępne dotyczące zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

Poniżej przedstawiono trzy sposoby uruchamiania podglądu zdalnego sterowania:  

-   W konsoli programu Configuration Manager.  

-   W wierszu polecenia systemu Windows.  

-   W systemie Windows **Start** menu na komputerze, na którym jest uruchomiona konsola programu Configuration Manager z **programu Microsoft System Center** grupę programów.  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Zdalne administrowanie komputerem klienckim z poziomu konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń** lub **kolekcji urządzeń**.  

3.  Wybierz komputer, który chcesz zdalnie administrować i następnie w **Home** w karcie **urządzenia** grupy, wybierz **Start** > **zdalnego sterowania**.  

    > [!IMPORTANT]  
    >  Jeśli uprawnienie ustawienia klienta **Monituj użytkownika o zezwolenie na zdalne sterowanie** ma wartość **Prawda**, połączenie nie zostanie zainicjowane do momentu zaakceptowania monitu zdalnego sterowania przez użytkownika na zdalnym komputerze. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).  

4.  Po otwarciu okna **Zdalne sterowanie programu Configuration Manager** możesz zdalnie administrować komputerem klienckim. Użyj następujących opcji, aby skonfigurować połączenie:  

    > [!NOTE]  
    >  Jeśli podczas nawiązywania komputer ma wiele monitorów, wyświetlanie wszystkich monitorów jest wyświetlana w oknie zdalnego sterowania.  

    -   **Plik — połączenie** -połączyć z innym komputerem. Ta opcja jest niedostępna, gdy sesja zdalnego sterowania jest aktywna.  

    -   **Plik — rozłączyć** - rozłącza aktywnych sesji sterowania zdalnego, ale nie zamyka **zdalnego sterowania programu Configuration Manager** okna.  

    -   **Plik — zakończyć** - rozłącza aktywnych sesji sterowania zdalnego i zamyka **zdalnego sterowania programu Configuration Manager** okna.  

        > [!NOTE]  
        >  Po rozłączeniu sesji zdalnego sterowania zawartość schowka systemu Windows na przeglądanym komputerze jest usuwana.  

    -   **Widok - pełny ekran** -maksymalizuje **zdalnego sterowania programu Configuration Manager** okna.  

        > [!NOTE]  
        >  Aby wyjść z trybu pełnego ekranu, naciśnij klawisze Ctrl+Alt+Break.  

    -   **Widok - Skaluj do rozmiaru** -skaluje ekran komputera zdalnego, aby dopasować rozmiar **zdalnego sterowania programu Configuration Manager** okna.  

    -   **Widok — Pasek stanu** — Włącza lub wyłącza wyświetlanie **zdalnego sterowania programu Configuration Manager** paska stanu okna.  

    -   **AKCJA — Wyślij klawisz Ctrl + Alt + Del** -wysyła kombinację klawiszy Ctrl + Alt + Del do komputera zdalnego.  

    -   **Akcja — Włącz udostępnianie Schowka** -pozwala skopiować i wkleić elementy do i z komputera zdalnego. Jeśli zmienisz tę wartość, musisz uruchomić ponownie sesję zdalnego sterowania, aby zmiany zaczęły obowiązywać.  

        > [!NOTE]  
        >  Jeśli użytkownik nie chce Schowka udostępnianie włączenia w konsoli programu Configuration Manager na komputerze z konsolą, ustaw wartość klucza rejestru **udostępnianie Control\Clipboard HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote** do **0**.  

    -   **Akcja — blokowanie zdalnej klawiatury i myszy** -blokuje zdalnej klawiatury i myszy, aby uniemożliwić użytkownikowi korzystania z komputera zdalnego.  

    -   **Pomoc - o zdalnego sterowania** -ithe Wyświetla bieżącą wersję podglądu.  

5.  Użytkownicy na komputerze zdalnym można wyświetlić więcej informacji na temat sesji zdalnego sterowania, po kliknięciu programu Configuration Manager**zdalnego sterowania** ikonę w obszarze powiadomień systemu Windows lub ikona na pasku sesji zdalnego sterowania.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>Uruchamianie przeglądarki zdalnego sterowania z wiersza polecenia systemu Windows  

-   Wpisz w wierszu polecenia systemu Windows, *< Folder instalacji programu Configuration Manager\>***\AdminConsole\Bin\x64\CmRcViewer.exe**  

    > [!NOTE]  
    >  Program CmRcViewer.exe obsługuje następujące opcje wiersza polecenia:  
    >   
    >  -   *< adres\>*  -Określa nazwę NetBIOS, w pełni kwalifikowaną nazwę domeny (FQDN) lub adres IP komputera klienckiego, który chcesz nawiązać połączenie.  
    > -   *< nazwa serwera lokacji\>*  -Określa nazwę serwera lokacji programu System Center Configuration Manager, do którego chcesz wysyłać komunikaty o stanie, które są związane z sesji zdalnego sterowania.  
    > -   **/?** — Wyświetla opcje wiersza polecenia dla podglądu zdalnego sterowania.  
    >   
    >  **Example:CmRcViewer.exe** *< adres\>*   *< \\\Site nazwa serwera >*  

