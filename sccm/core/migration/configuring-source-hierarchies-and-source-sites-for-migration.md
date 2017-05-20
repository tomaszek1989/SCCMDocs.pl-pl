---
title: "Hierarchie źródłowe migracji | Dokumentacja firmy Microsoft"
description: "Konfigurowanie hierarchii źródłowych i lokacji źródłowych dane można migrować do środowiska programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c5a58d79f81ccdf19ad88dc932e3a52eac2c18ab
ms.openlocfilehash: 80c43ab93ee5a2de6bf8d7993dfd46f0005d2df8
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby umożliwić migrację danych do środowiska programu System Center Configuration Manager, należy skonfigurować obsługiwanej hierarchii źródłowej programu Configuration Manager i co najmniej jednej lokacji źródłowej w tej hierarchii, która zawiera dane przeznaczone do migracji.  

> [!NOTE]  
>  Operacje migracji są uruchamiane w lokacji najwyższego poziomu w hierarchii docelowej. Przypadku konfigurowania migracji za pomocą konsoli programu Configuration Manager, który jest podłączony do głównej lokacji podrzędnej, należy poczekać na replikację konfiguracji do centralnej lokacji administracyjnej, początek i stan są następnie replikowane do lokacji głównej, z którym nawiązano połączenie.  

 Użyj informacji i procedur w poniższych sekcjach do określania hierarchii źródłowej i dodanie dodatkowych lokacji źródłowych. Po zakończeniu tych procedur, można utworzyć zadania migracji i rozpocząć migrację danych z hierarchii źródłowej do hierarchii docelowej.  

-   [Określ hierarchię źródłową do migracji](#BKBM_ConfigSrcHierarchy)  

-   [Zidentyfikuj dodatkowe Lokacje źródłowe hierarchii źródłowej](#BKBM_ConfigSrcSites)  

##  <a name="BKBM_ConfigSrcHierarchy"></a>Określ hierarchię źródłową do migracji  
 Aby przeprowadzić migrację danych do hierarchii docelowej, należy określić obsługiwanej hierarchii źródłowej zawierające dane, które chcesz migrować. Domyślnie w lokacji najwyższego poziomu tej hierarchii staje się lokację źródłową hierarchii źródłowej. W przypadku migracji z hierarchii programu Configuration Manager 2007, można następnie ustawić się dodatkowe Lokacje źródłowe do migracji danych są zbierane z początkowej lokacji źródłowej. Migrację z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, nie trzeba skonfigurować dodatkowe Lokacje źródłowe do migracji danych z hierarchii źródłowej. Jest to spowodowane te wersje programu Configuration Manager używają udostępnionej bazy danych, która jest dostępna w lokacji najwyższego poziomu hierarchii źródłowej. Udostępniona baza danych zawiera wszystkie informacje, które można migrować.  

 Określ hierarchię źródłową do migracji oraz zidentyfikować dodatkowe Lokacje źródłowe w hierarchii programu Configuration Manager 2007, należy użyć poniższych procedur.  

 Uruchom tę procedurę za pomocą konsoli programu Configuration Manager, który jest podłączony do hierarchii docelowej:  

### <a name="to-configure-a-source-hierarchy"></a>Aby skonfigurować hierarchię źródłową   

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Migracja**, a następnie kliknij przycisk **Hierarchia źródłowa**.  

3.  Na **Home** w karcie **migracji** , kliknij przycisk **Określ hierarchię źródłową**.  

4.  W **Określ hierarchię źródłową** okno dialogowe dla **hierarchii źródłowej**, wybierz opcję **nowej hierarchii źródłowej**.  

5.  Dla **serwera lokacji programu Configuration Manager najwyższego poziomu**, wprowadź nazwę lub adres IP lokacji najwyższego poziomu obsługiwanej hierarchii źródłowej.  

6.  Określ konta dostępu do lokacji źródłowej, które mają następujące uprawnienia:  

    -   Konto lokacji źródłowej: **Odczytaj** uprawnienia do dostawcy programu SMS dla określonej lokacji najwyższego poziomu w hierarchii źródłowej. Współużytkowanie punktów dystrybucji i uaktualnień wymagają **Modyfikuj** i **usunąć** uprawnienia do lokacji w hierarchii źródłowej.

    -   Konto bazy danych lokacji źródłowej: **Odczytaj** i **Execute** uprawnień do bazy danych programu SQL Server dla określonej lokacji najwyższego poziomu w hierarchii źródłowej.  

     W przypadku określenia zastosowania konta komputera, programu Configuration Manager korzysta z konta komputera lokacji najwyższego poziomu w hierarchii docelowej. Dla tej opcji upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się lokacja najwyższego poziomu hierarchii źródłowej.  

7.  Aby współużytkować punkty dystrybucji między hierarchiami źródłową i docelową, zaznacz **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej** pole wyboru. Jeśli nie zostanie włączone udostępnianie w tej chwili punktu dystrybucji, można to zrobić, poprzez edycję poświadczeń lokacji źródłowej po danych Zakończono zbieranie.  

8.  Kliknij przycisk **OK** , aby zapisać konfigurację. Spowoduje to otwarcie **Stan zbierania danych** okno dialogowe i automatyczne rozpoczęcie zbierania danych.  

9. Po zakończeniu zbierania danych kliknij przycisk **zamknąć** zamknąć **Stan zbierania danych** okna dialogowego i ukończyć konfigurację.  

##  <a name="BKBM_ConfigSrcSites"></a>Zidentyfikuj dodatkowe Lokacje źródłowe hierarchii źródłowej  
 Podczas konfigurowania obsługiwanej hierarchii źródłowej lokacja najwyższego poziomu tej hierarchii jest automatycznie skonfigurowany jako lokację źródłową i następuje automatyczne zbieranie danych z tej witryny. Następnej akcji, które należy wykonać, zależy od wersji programu Configuration Manager uruchamiany w hierarchii źródłowej:  

-   W hierarchii źródłowej programu Configuration Manager 2007 można rozpocząć migrację z tej lokacji źródłowej lub skonfigurować dodatkowe Lokacje źródłowe hierarchii źródłowej po zakończeniu zbierania danych dla lokacji źródłowej. Do migracji danych, które są dostępne tylko z lokacją podrzędną, konfigurowanie dodatkowych lokacji źródłowych w hierarchii programu Configuration Manager 2007. Na przykład skonfigurować dodatkowe Lokacje źródłowe w celu zbierania danych dotyczących zawartości przeznaczonej do migracji, jeśli jest tworzony w lokacji podrzędnej w hierarchii źródłowej i jest niedostępny w lokacji najwyższego poziomu hierarchii źródłowej.  

-   Dla programu System Center 2012 Configuration Manager lub System Center Configuration Manager hierarchii źródłowej nie jest konieczne konfigurowanie dodatkowych lokacji źródłowych. Jest to spowodowane te wersje programu Configuration Manager używają udostępnionej bazy danych, która jest dostępna w lokacji najwyższego poziomu hierarchii źródłowej. Udostępniona baza danych zawiera wszystkie informacje, które można migrować ze wszystkich lokacji w tej hierarchii źródłowej. To udostępnienie danych, które można migrować z lokacji najwyższego poziomu hierarchii źródłowej.  

Podczas konfigurowania dodatkowych lokacji źródłowych hierarchii źródłowej programu Configuration Manager 2007, należy skonfigurować dodatkowe Lokacje źródłowe w hierarchii źródłowej do dołu. Przed skonfigurowaniem jakiejkolwiek jej lokacji podrzędnej jako lokacji źródłowej, należy skonfigurować lokację nadrzędną jako lokację źródłową.  

Użyj poniższej procedury, aby skonfigurować dodatkowe Lokacje źródłowe hierarchii źródłowej programu Configuration Manager 2007:  

### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>Aby zidentyfikować dodatkowe Lokacje źródłowe w hierarchii źródłowej 

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Migracja**, a następnie kliknij przycisk **Hierarchia źródłowa**.  

3.  Wybierz lokację, którą chcesz skonfigurować jako lokację źródłową.  

4.  Na karcie **Narzędzia główne** w grupie **Lokacja źródłowa** kliknij przycisk **Konfiguruj**.  

5.  W **poświadczenia lokacji źródłowej** okno dialogowe dla kont dostępu lokacji źródłowej, określ konta, które mają następujące uprawnienia:  

    -   Konto lokacji źródłowej: **Odczytaj** uprawnienia do dostawcy programu SMS dla określonej lokacji najwyższego poziomu w hierarchii źródłowej. Współużytkowanie punktów dystrybucji i uaktualnień wymagają **Modyfikuj** i **usunąć** uprawnienia do lokacji w hierarchii źródłowej.  

    -   Konto bazy danych lokacji źródłowej: **Odczytaj** i **Execute** uprawnień do bazy danych programu SQL Server dla określonej lokacji najwyższego poziomu w hierarchii źródłowej.  

    W przypadku określenia zastosowania konta komputera, programu Configuration Manager korzysta z konta komputera lokacji najwyższego poziomu w hierarchii docelowej. Dla tej opcji upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się lokacja najwyższego poziomu hierarchii źródłowej.  

6.  Aby współużytkować punkty dystrybucji między hierarchiami źródłową i docelową, zaznacz **Włącz udostępnianie punktu dystrybucji dla serwera lokacji źródłowej** pole wyboru. Jeśli nie zostanie włączone udostępnianie w tej chwili punktu dystrybucji, można to zrobić, poprzez edycję poświadczeń lokacji źródłowej po danych Zakończono zbieranie.  

7. Kliknij przycisk **OK** , aby zapisać konfigurację. Spowoduje to otwarcie **Stan zbierania danych** okno dialogowe i automatyczne rozpoczęcie zbierania danych.  

8.  Po zakończeniu zbierania danych kliknij przycisk **Zamknij** aby zakończyć konfigurację.  

