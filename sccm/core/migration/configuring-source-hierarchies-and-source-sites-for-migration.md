---
title: "Hierarchie źródłowe migracji | Dokumentacja firmy Microsoft"
description: "Konfigurowanie hierarchii źródłowej i lokacji źródłowych dane można migrować do środowiska programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 80c43ab93ee5a2de6bf8d7993dfd46f0005d2df8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby umożliwić migrację danych do środowiska programu System Center Configuration Manager, należy skonfigurować obsługiwanej hierarchii źródłowej programu Configuration Manager i co najmniej jednej lokacji źródłowej w tej hierarchii, która zawiera dane przeznaczone do migracji.  

> [!NOTE]  
>  Operacje migracji są uruchamiane w lokacji najwyższego poziomu w hierarchii docelowej. Konfigurowania migracji, korzystając z konsoli programu Configuration Manager, który jest podłączony do głównej lokacji podrzędnej, należy poczekać na replikację konfiguracji do centralnej lokacji administracyjnej, start i stan są następnie replikowane do lokacji głównej, z którym nawiązano połączenie.  

 Określ hierarchię źródłową, a następnie dodaj dodatkowe Lokacje źródłowe, użyj informacji i procedur w poniższych sekcjach. Po zakończeniu tych procedur, można utworzyć zadania migracji i rozpocząć migrację danych z hierarchii źródłowej do hierarchii docelowej.  

-   [Określ hierarchię źródłową do migracji](#BKBM_ConfigSrcHierarchy)  

-   [Zidentyfikuj dodatkowe Lokacje źródłowe hierarchii źródłowej](#BKBM_ConfigSrcSites)  

##  <a name="BKBM_ConfigSrcHierarchy"></a>Określ hierarchię źródłową do migracji  
 Aby przeprowadzić migrację danych do hierarchii docelowej, należy określić obsługiwanej hierarchii źródłowej zawierającej dane, które chcesz migrować. Domyślnie w lokacji najwyższego poziomu tej hierarchii staje się lokację źródłową hierarchii źródłowej. W przypadku migrowania z hierarchii programu Configuration Manager 2007, następnie skonfigurowaniem dodatkowe Lokacje źródłowe do migracji danych są zbierane z początkowej lokacji źródłowej. W przypadku migrowania z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, nie trzeba skonfigurować dodatkowe Lokacje źródłowe do migracji danych z hierarchii źródłowej. Jest to spowodowane te wersje programu Configuration Manager używają udostępnionej bazy danych, która jest dostępna w lokacji najwyższego poziomu hierarchii źródłowej. Udostępnionej bazy danych ma wszystkie informacje, których można migrować.  

 Użyj poniższych procedur, aby określić hierarchię źródłową do migracji oraz zidentyfikować dodatkowe Lokacje źródłowe w hierarchii programu Configuration Manager 2007.  

 Tę procedurę należy uruchomić z konsoli programu Configuration Manager, który jest podłączony do hierarchii docelowej:  

### <a name="to-configure-a-source-hierarchy"></a>Aby skonfigurować hierarchię źródłową   

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Migracja**, a następnie kliknij przycisk **Hierarchia źródłowa**.  

3.  Na **Home** karcie **migracji** kliknij przycisk **Określ hierarchię źródłową**.  

4.  W **Określ hierarchię źródłową** okno dialogowe dla **hierarchii źródłowej**, wybierz pozycję **nowej hierarchii źródłowej**.  

5.  Aby uzyskać **serwera lokacji programu Configuration Manager najwyższego poziomu**, wprowadź nazwę lub adres IP lokacji najwyższego poziomu obsługiwanej hierarchii źródłowej.  

6.  Określ konta dostępu do lokacji źródłowej, które mają następujące uprawnienia:  

    -   Konto lokacji źródłowej: **Odczyt** uprawnienia do dostawcy programu SMS dla określonej lokacji najwyższego poziomu w hierarchii źródłowej. Współużytkowanie punktów dystrybucji i uaktualnień wymagają **Modyfikuj** i **usunąć** uprawnienia do lokacji w hierarchii źródłowej.

    -   Konto bazy danych lokacji źródłowej: **Odczyt** i **Execute** uprawnień do bazy danych programu SQL Server dla określonej lokacji najwyższego poziomu w hierarchii źródłowej.  

     Jeśli w przypadku określenia zastosowania konta komputera, Configuration Manager używa konta komputera lokacji najwyższego poziomu w hierarchii docelowej. Dla tej opcji upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się lokacja najwyższego poziomu hierarchii źródłowej.  

7.  Aby współużytkować punkty dystrybucji między hierarchiami źródłową i docelową, zaznacz **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej** pole wyboru. Jeśli udostępnianie w tej chwili punktu dystrybucji nie jest włączone, możesz to zrobić, poprzez edycję poświadczeń lokacji źródłowej po danych zbieranie zostało zakończone.  

8.  Kliknij przycisk **OK** , aby zapisać konfigurację. Spowoduje to otwarcie **Stan zbierania danych** okno dialogowe i automatyczne rozpoczęcie zbierania danych.  

9. Po zakończeniu zbierania danych kliknij przycisk **zamknąć** zamknąć **Stan zbierania danych** okna dialogowego i ukończyć konfigurację.  

##  <a name="BKBM_ConfigSrcSites"></a>Zidentyfikuj dodatkowe Lokacje źródłowe hierarchii źródłowej  
 Podczas konfigurowania obsługiwanej hierarchii źródłowej lokacja najwyższego poziomu tej hierarchii jest automatycznie konfigurowany jako lokację źródłową, a następuje automatyczne zbieranie danych z tej lokacji. Następnej akcji, które należy podjąć, zależy od wersji Menedżera konfiguracji, który jest uruchamiany w hierarchii źródłowej:  

-   Dla hierarchii źródłowej programu Configuration Manager 2007 można rozpocząć migrację z tej lokacji źródłowej lub skonfigurować dodatkowe Lokacje źródłowe z hierarchii źródłowej po zakończeniu zbierania danych w pierwotnej lokacji źródłowej. Aby przeprowadzić migrację danych, które są dostępne tylko z lokacji podrzędnej, skonfigurować dodatkowe Lokacje źródłowe hierarchii programu Configuration Manager 2007. Na przykład można skonfigurować dodatkowe Lokacje źródłowe do zbierania danych o zawartości, które chcesz migrować, gdy jest tworzony w lokacji podrzędnej w hierarchii źródłowej, a nie jest dostępna w lokacji najwyższego poziomu w hierarchii źródłowej.  

-   Dla programu System Center 2012 Configuration Manager lub System Center Configuration Manager hierarchii źródłowej jest konieczne konfigurowanie dodatkowych lokacji źródłowych. Jest to spowodowane te wersje programu Configuration Manager używają udostępnionej bazy danych, która jest dostępna w lokacji najwyższego poziomu hierarchii źródłowej. Udostępnionej bazy danych ma wszystkie informacje, które można migrować ze wszystkich lokacji w tej hierarchii źródłowej. To udostępnienie danych, które można migrować z lokacji najwyższego poziomu hierarchii źródłowej.  

Podczas konfigurowania dodatkowych lokacji źródłowych hierarchii źródłowej programu Configuration Manager 2007, należy skonfigurować dodatkowe Lokacje źródłowe hierarchii źródłowej do dołu. Należy skonfigurować lokację nadrzędną jako lokację źródłową przed skonfigurowaniem jakiejkolwiek jej lokacji podrzędnych jako lokacji źródłowych.  

Aby skonfigurować dodatkowe Lokacje źródłowe hierarchii źródłowej programu Configuration Manager 2007, należy użyć poniższej procedury:  

### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>Aby zidentyfikować dodatkowe Lokacje źródłowe w hierarchii źródłowej 

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Migracja**, a następnie kliknij przycisk **Hierarchia źródłowa**.  

3.  Wybierz lokację, która ma zostać skonfigurowana jako lokację źródłową.  

4.  Na karcie **Narzędzia główne** w grupie **Lokacja źródłowa** kliknij przycisk **Konfiguruj**.  

5.  W **poświadczenia lokacji źródłowej** okno dialogowe dla kont dostępu lokacji źródłowej, określ konta, które mają następujące uprawnienia:  

    -   Konto lokacji źródłowej: **Odczyt** uprawnienia do dostawcy programu SMS dla określonej lokacji najwyższego poziomu w hierarchii źródłowej. Współużytkowanie punktów dystrybucji i uaktualnień wymagają **Modyfikuj** i **usunąć** uprawnienia do lokacji w hierarchii źródłowej.  

    -   Konto bazy danych lokacji źródłowej: **Odczyt** i **Execute** uprawnień do bazy danych programu SQL Server dla określonej lokacji najwyższego poziomu w hierarchii źródłowej.  

    Jeśli w przypadku określenia zastosowania konta komputera, Configuration Manager używa konta komputera lokacji najwyższego poziomu w hierarchii docelowej. Dla tej opcji upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się lokacja najwyższego poziomu hierarchii źródłowej.  

6.  Aby współużytkować punkty dystrybucji między hierarchiami źródłową i docelową, zaznacz **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej** pole wyboru. Jeśli udostępnianie w tej chwili punktu dystrybucji nie jest włączone, możesz to zrobić, poprzez edycję poświadczeń lokacji źródłowej po danych zbieranie zostało zakończone.  

7. Kliknij przycisk **OK** , aby zapisać konfigurację. Spowoduje to otwarcie **Stan zbierania danych** okno dialogowe i automatyczne rozpoczęcie zbierania danych.  

8.  Po zakończeniu zbierania danych kliknij przycisk **Zamknij** w celu ukończenia konfiguracji.  
