---
title: Wymagania wstępne dotyczące migracji
titleSuffix: Configuration Manager
description: Informacje o obsługiwanych wersjach programu Configuration Manager, języków obsługiwanych lokacji źródłowej i konfiguracje wymagane do migracji.
ms.date: 5/7/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ec976930-7467-4d3c-b33c-991bf408a74a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: da35641b7e00bfdae025d2978beaa541951487da
ms.sourcegitcommit: 7198ec49d9ce68c6d55bfb9e2d537b5442a132cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2018
---
# <a name="prerequisites-for-migration-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące migracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby przeprowadzić migrację z obsługiwanej hierarchii źródłowej, musi mieć dostęp do poszczególnych odpowiednich lokacji źródłowej programu Configuration Manager i uprawnienia w lokacji docelowej programu System Center Configuration Manager do konfigurowania i uruchamiania operacji migracji.  

 Skorzystaj z informacji w poniższych sekcjach ułatwią zrozumienie wersje programu Configuration Manager, które są obsługiwane przy migracji oraz o wymaganych konfiguracjach.  

-   [Wersje programu Configuration Manager obsługujące migrację](#BKMK_SupportedMigrationVersions)  

-   [Języki lokacji źródłowej obsługiwane na potrzeby migracji](#BKMK_SorceSiteLanguage)  

-   [Konfiguracje wymagane do migracji](#BKMK_Required_Configurations)  

##  <a name="BKMK_SupportedMigrationVersions"></a> Wersje programu Configuration Manager obsługujące migrację  
 Można migrować danych z hierarchii źródłowej, która używa dowolnej z następujących wersji programu Configuration Manager:  

-   Program Configuration Manager 2007 z dodatkiem SP2 (na potrzeby migracji programu Configuration Manager 2007 R2 ani R3 w lokacji źródłowej nie są jest brany pod uwagę. Tak długo, jak działa lokacji źródłowej z dodatkiem SP2, lokacje z zainstalowanym dodatkiem R2 lub R3 są obsługiwane przez migrację do programu System Center Configuration Manager).  

-   System Center 2012 Configuration Manager SP2 lub System Center 2012 R2 Configuration Manager SP1.  

    > [!TIP]  
    >  Oprócz migracji możesz użyć uaktualnienie w miejscu lokacji z programem System Center 2012 Configuration Manager do programu System Center Configuration Manager.  

-   Hierarchii programu System Center Configuration Manager lub starszej wersji programu System Center Configuration Manager.  

  Na przykład jeśli masz hierarchii docelowej programu System Center Configuration Manager 1606, można użyć migracji można skopiować danych z hierarchii źródłowej, na którym działa wersja 1606 lub 1602. Nie można jednak migracji danych z hierarchii źródłowej, która używa 1610.  


##  <a name="BKMK_SorceSiteLanguage"></a> Języki lokacji źródłowej obsługiwane na potrzeby migracji  
 W przypadku migracji danych między hierarchiami programu Configuration Manager, dane są przechowywane w hierarchii docelowej w formacie niezależnym od języka programu System Center Configuration Manager. Ponieważ programu Configuration Manager 2007 nie przechowuje danych w formacie niezależnym od języka, proces migracji muszą być konwertowane obiekty do tego formatu podczas migracji z programu Configuration Manager 2007. W związku z tym migracja obsługuje tylko Lokacje źródłowe programu Configuration Manager 2007, które są zainstalowane z następującymi językami:  

-   angielski  

-   francuski  

-   niemiecki  

-   japoński  

-   koreański  

-   rosyjski  

-   Chiński uproszczony  

-   chiński tradycyjny  

Podczas migracji danych z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, nie istnieją żadne ograniczenia dotyczące języka lokacji źródłowej. Obiekty w bazie danych lokacji źródłowej mają już format niezależny od języka.  

##  <a name="BKMK_Required_Configurations"></a> Konfiguracje wymagane do migracji  
Dostępne są następujące konfiguracje wymagane do migracji i operacje migracji:  

-   **Aby skonfigurować, uruchomić i monitorować migrację w konsoli programu Configuration Manager:**  

     W lokacji docelowej konto musi mieć w ramach administracji opartej na rolach przypisaną rolę zabezpieczeń **Administrator infrastruktury**. Ta rola zabezpieczeń przydziela uprawnienia do zarządzania wszystkimi operacjami migracji, co dotyczy między innymi tworzenia, czyszczenia i monitorowania zadań migracji oraz udostępniania i uaktualniania punktów dystrybucji.  

-   **Gromadzenie danych:**  

     Aby włączyć w lokacji docelowej zbieranie danych, należy skonfigurować następujące dwa konta dostępu do lokacji źródłowej przeznaczone do użytku z każdą lokacją źródłową:  

    -   **Konto lokacji źródłowej:** To konto jest używane do dostępu do dostawcy programu SMS lokacji źródłowej.  

        -   Dla lokacji źródłowej programu Configuration Manager 2007 SP2 to konto wymaga **odczytu** uprawnienia do wszystkich obiektów lokacji źródłowej.  

        -   Dla lokacji źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, to konto wymaga **odczytu** uprawnienia do wszystkich obiektów lokacji źródłowej, to uprawnienie można przyznać za pośrednictwem administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

    -   **Konto bazy danych lokacji źródłowej:** To konto jest używane do dostępu do bazy danych programu SQL Server lokacji źródłowej i wymaga **Connect**, **Execute**, i **wybierz** uprawnień do bazy danych lokacji źródłowej.  

    Te konta można skonfigurować podczas konfigurowania nowej hierarchii źródłowej, zbierania danych dla dodatkowej lokacji źródłowej oraz podczas ponownego konfigurowania poświadczeń dla lokacji źródłowej. Konta te mogą korzystać z kont użytkowników domeny. Można również wskazać konto komputera lokacji najwyższego poziomu w hierarchii docelowej.  

    > [!IMPORTANT]  
    >  Jeśli używasz konta komputera programu Configuration Manager jako konta dostępu, upewnij się, że to konto jest członkiem grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się w lokacji źródłowej.  

    Podczas zbierania danych są używane następujące protokoły sieciowe i porty:  

    -   NetBIOS/SMB — 445 (TCP)  

    -   RPC (WMI) — 135 (TCP)  

    -   SQL Server — porty TCP używane zarówno przez bazę danych lokacji źródłowej, jak i docelowej.  

-   **Migracja aktualizacji oprogramowania:**  

     Przed migracją aktualizacji oprogramowania należy skonfigurować hierarchię docelową z punktem aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [Planowanie migracji aktualizacji oprogramowania](../../core/migration/planning-for-the-migration-of-objects.md#Plan_migrate_Software_updates).  

-   **Współużytkowane punkty dystrybucji:**  

     Aby pomyślnie współużytkować jakiekolwiek punkty dystrybucji z lokacji źródłowej, co najmniej jedna lokacja główna lub centralna lokacja administracyjna w hierarchii docelowej musi mieć takie same numery portów do obsługi żądań klientów, jak lokacja źródłowa. Aby uzyskać więcej informacji na temat portów żądań klientów, zobacz [Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-communication-ports.md).  

     W przypadku każdej lokacji źródłowej współużytkowane są tylko te punkty dystrybucji, które zostały zainstalowane na serwerze systemu lokacji skonfigurowanym z nazwą FQDN.  

     Ponadto, aby współużytkować punkt dystrybucji z lokacji źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager **konto lokacji źródłowej** (który uzyskuje dostęp do dostawcy programu SMS dla serwera lokacji źródłowej), musi mieć **Modyfikuj** uprawnień do **lokacji** w lokacji źródłowej. Uprawnienie to można przyznać za pośrednictwem administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  


-   **Uaktualnianie lub ponowne przypisywanie punktów dystrybucji:**  

     **Konto dostępu do lokacji źródłowej** skonfigurowane do zbierania danych od dostawcy programu SMS lokacji źródłowej musi mieć przypisane następujące uprawnienia:  

    -   Aby uaktualnić punkt dystrybucji programu Configuration Manager 2007, konto wymaga **odczytu**, **Execute**, i **usunąć** uprawnień do **lokacji** klasy na serwerze lokacji Manager2007 konfiguracji można pomyślnie usunąć punkt dystrybucji z lokacji źródłowej Manager2007 konfiguracji  

    -   Do ponownego przypisania punktu dystrybucji programu System Center 2012 Configuration Manager lub System Center Configuration Manager, konto musi mieć **Modyfikuj** uprawnienia do **lokacji** w lokacji źródłowej. Uprawnienie to można przyznać za pośrednictwem administracji opartej na rolach. Aby uzyskać informacje o korzystaniu z funkcji administracji opartej na rolach, zobacz [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

     Aby pomyślnie uaktualnić lub ponownie przypisać punkt dystrybucji do nowej hierarchii, porty skonfigurowane do obsługi żądań klientów w lokacji zarządzającej punktem dystrybucji w hierarchii źródłowej muszą być takie same porty, jak porty skonfigurowane do obsługi żądań klientów w lokacji docelowej, która ma zarządzać punktem dystrybucji. Aby uzyskać więcej informacji na temat portów żądań klientów, zobacz [Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-communication-ports.md).  
