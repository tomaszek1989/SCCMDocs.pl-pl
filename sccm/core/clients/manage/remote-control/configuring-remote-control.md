---
title: Konfigurowanie zdalnego sterowania
titleSuffix: Configuration Manager
description: Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4e4d380319704eda608930ac938232513800b81a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Ta procedura opisuje Konfigurowanie domyślnych ustawień klienta dla zdalnego sterowania. Te ustawienia mają zastosowanie do wszystkich komputerów w hierarchii. Jeśli chcesz, aby te ustawienia dotyczyły tylko niektórych komputerów, należy przypisać niestandardowe ustawienie urządzenia klienckiego do kolekcji, która zawiera te komputery. Aby uzyskać więcej informacji, a zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md). 

Aby korzystać z pomocy zdalnej lub pulpitu zdalnego, musi być zainstalowana i skonfigurowana na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Więcej informacji o instalowaniu i konfigurowaniu pomocy zdalnej lub pulpitu zdalnego można znaleźć w dokumentacji systemu Windows.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>Włączanie zdalnego sterowania i konfigurowanie ustawień klienta  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne** oknie dialogowym wybierz **narzędzia zdalnej**.  

6.  Konfigurowanie zdalnego sterowania, pomocy zdalnej i pulpitu zdalnego ustawień klienta. Aby uzyskać listę ustawień klienta narzędzi zdalnych, które można skonfigurować, zobacz [narzędzia zdalnej](../../../../core/clients/deploy/about-client-settings.md#remote-tools).  

    Możesz zmienić nazwę firmy, która jest wyświetlana w oknie dialogowym **Sterowanie zdalne programem ConfigMgr** , konfigurując wartość **Nazwa organizacji wyświetlana w Centrum oprogramowania** w ustawieniach klienta **Agent komputera** .  

 Komputery klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

#### <a name="enable-keyboard-translation"></a>Włączyć translację klawiatury

Domyślnie program Configuration Manager przesyła klucza pozycji z lokalizacji podglądu współużytkujących lokalizacji. Może stanowić problem w przypadku konfiguracji klawiatury, które różnią się w podglądzie współużytkujących. Na przykład podglądu z klawiatury w angielskiej wersji językowej wpisać "A", ale klawiatury francuskim współużytkujących zapewni "Q". Teraz istnieje możliwość konfigurowania zdalnego sterowania, aby sam znak jest przekazywany z podglądu klawiatury do udostępniających i Podgląd zamierza na typ dociera udostępniających.

Aby włączyć translację klawiatury w **zdalne sterowanie programu Configuration Manager**, wybierz **akcji**i wybierz polecenie **włączyć translację klawiatury** do przesłania klucza pozycji.

> [!NOTE]
>
> Klawisze specjalne, takie jak ~! #@ $% nie będą poprawnie tłumaczone.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>Skróty klawiaturowe przeglądarki zdalnego sterowania

|Skrót klawiaturowy|Opis|  
|-----------------------|-----------------|  
|Alt+Page Up|Przełącza między uruchomionymi programami od lewej do prawej.|  
|Alt+Page Down|Przełącza między uruchomionymi programami od prawej do lewej.|  
|Alt+Insert|Przełącza między uruchomionymi programami w takiej kolejności, w jakiej były otwierane.|  
|Alt+Home|Wyświetla menu **Start** .|  
|Ctrl+Alt+End|Wyświetla okno dialogowe Zabezpieczenia systemu Windows (Ctrl+Alt+Del).|  
|Alt+Delete|Wyświetla menu systemu Windows.|  
|Ctrl+Alt+znak minus (na klawiaturze numerycznej)|Kopiuje aktywne okno na komputerze lokalnym do Schowka komputera zdalnego.|  
|Ctrl+Alt+znak plus (na klawiaturze numerycznej)|Kopiuje cały obszar okien komputera lokalnego do Schowka komputera zdalnego.|  
