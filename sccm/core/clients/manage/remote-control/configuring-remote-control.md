---
title: Konfigurowanie zdalnego sterowania | Dokumentacja firmy Microsoft
description: Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3a386c23c81f413d7d161780bdc0ab3a5b9eccae
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Ta procedura opisuje Konfigurowanie domyślnych ustawień klienta zdalnego sterowania. Te ustawienia mają zastosowanie do wszystkich komputerów w hierarchii. Jeśli chcesz, aby te ustawienia dotyczyły tylko niektórych komputerów, należy przypisać niestandardowe ustawienie urządzenia klienckiego kolekcji, która zawiera te komputery. Aby uzyskać więcej informacji, a zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md). 

Aby korzystać z pomocy zdalnej lub pulpit zdalny, musi być zainstalowany i skonfigurowany na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Więcej informacji o instalowaniu i konfigurowaniu pomocy zdalnej lub pulpitu zdalnego można znaleźć w dokumentacji systemu Windows.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>Włączanie zdalnego sterowania i konfigurowanie ustawień klienta  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **domyślne** okno dialogowe Wybierz **narzędzi zdalnych**.  

6.  Skonfiguruj zdalne sterowanie, Pomoc zdalna i Pulpit zdalny ustawień klienta. Aby uzyskać listę ustawień klienta narzędzi zdalnych, które można skonfigurować, zobacz [narzędzi zdalnych](../../../../core/clients/deploy/about-client-settings.md#remote-tools).  

    Możesz zmienić nazwę firmy, która jest wyświetlana w oknie dialogowym **Sterowanie zdalne programem ConfigMgr** , konfigurując wartość **Nazwa organizacji wyświetlana w Centrum oprogramowania** w ustawieniach klienta **Agent komputera** .  

 Komputery klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

#### <a name="enable-keyboard-translation"></a>Włącz Translacja klawiatury

Domyślnie program Configuration Manager przesyła klucza pozycji z lokalizacji Podgląd współużytkujących lokalizacji. Może to spowodować problem dotyczący konfiguracji klawiatury, które różnią się w podglądzie współużytkujących. Na przykład podgląd z angielskiej klawiatury wpisać "A", ale klawiatura francuska współużytkujących zapewni "Q". Masz teraz opcji konfiguracji zdalnego sterowania, aby sam znak są przesyłane z klawiatury viewer do udostępniających i Podgląd zamierza na typ dociera udostępniających.

Aby włączyć funkcję tłumaczenia klawiatury w **zdalnego sterowania programu Configuration Manager**, wybierz **akcji**i wybierz polecenie **Translacja klawiatury Włącz** przesyłać pozycji klucza.

> [!NOTE]
>
> Klawisze specjalne, takie jak ~! #@ $% nie będą poprawnie tłumaczone.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>Skróty klawiaturowe podglądu zdalnego sterowania

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

