---
title: Należy zdefiniować granice
titleSuffix: Configuration Manager
description: Zrozumienie, jak zdefiniować lokalizacje sieciowe w intranecie, która może zawierać urządzeń, którymi chcesz zarządzać.
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4a9dc4d9-e114-42ec-ae2b-73bee14ab04f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1e27bce7576f6d96a8e8af95fa5df69dd39c05cd
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="define-network-locations-as-boundaries-for-system-center-configuration-manager"></a>Definiują lokalizacje sieciowe jako granic dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Granice programu Configuration Manager są lokalizacje w sieci, które zawierają urządzeń, które mają być zarządzane. Granica, w której znajduje się na urządzeniu jest odpowiednikiem lokacji usługi Active Directory lub adres IP sieci, który jest identyfikowany przez klienta Configuratoin Manager, który jest zainstalowany na urządzeniu.
 - Pojedyncze granice można tworzyć ręcznie. Jednak programu Configuration Manager nie obsługuje bezpośredniego wpisywania supersieci jako granicy. Zamiast tego można użyć typu granicy z zakresem adresów IP.
 - Można skonfigurować [odnajdywania lasu usługi Active Directory](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutForest) metodę, aby automatycznie wykrywać i tworzenie granic dla każdej podsieci IP i lokacji usługi Active Directory umożliwia odnalezienie go. Gdy funkcja odnajdywania lasu usługi Active Directory rozpozna przypisany do lokacji usługi Active Directory, programu Configuration Manager skonwertuje supersieć na granicę zakres adresów IP.  

Nie jest rzadko urządzenia do używania adresu IP, który nie został powiadomiony o administrator programu Configuration Manager. Podczas lokalizacji sieciowej, urządzenia jest wątpliwa, potwierdź urządzenie raportuje jako jego lokalizację, używając **IPCONFIG** polecenia na urządzeniu.  

Tworzona granica automatycznie otrzymuje nazwę opartą na typie i zakresie granicy. Nie można modyfikować tej nazwy. Zamiast tego można określić opis, który pomoże zidentyfikować granicę w konsoli programu Configuration Manager.  

Każda granica jest dostępne dla każdej lokacji w hierarchii. Po utworzeniu granicy można zmodyfikować jej właściwości, wykonaj następujące czynności:  
-   Dodanie granicy do jednej lub wielu grup granic.  
-   Zmiana typu lub zakresu granicy.  
-   Wyświetlenie karty **Systemy lokacji** dla granicy w celu sprawdzenia, które serwery systemu lokacji (punkty dystrybucji, punkty migracji stanu i punkty zarządzania) są skojarzone z granicą.  

## <a name="to-create-a-boundary"></a>Aby utworzyć granicę  

1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** > **granic**  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz granicę.**  

3.  Na karcie **Ogólne** okna dialogowego Utwórz granicę można określić **opis** w celu identyfikacji granicy przy użyciu przyjaznej nazwy lub odwołania.  

4.  Wybierz **typ** dla tej granicy:  

    -   Jeśli zostanie wybrana opcja **Podsieć IP**, należy określić **Identyfikator podsieci** dla tej granicy.  
        > [!TIP]  
        >  Można określić wartości **Sieć** i **Maska podsieci** , aby wartość **Identyfikator podsieci** została określona automatycznie. Wraz z granicą zapisywana jest tylko wartość Identyfikator podsieci.  

    -   Jeśli zostanie wybrana opcja **Lokacja usługi Active Directory**, należy określić lokację usługi Active Directory lub użyć przycisku **Przeglądaj** i przejść do takiej lokacji w lesie lokalnym serwera lokacji.  

        > [!IMPORTANT]  
        >  Jeśli dla granicy zostanie określona lokacja usługi Active Directory, granica będzie zawierać wszystkie podsieci IP, które są elementami członkowskimi tej lokacji usługi Active Directory. Jeśli konfiguracja lokacji usługi Active Directory zmieni się w usłudze Active Directory, ulegną zmianie także lokalizacje sieciowe objęte granicą.  

    -   Jeśli zostanie wybrana opcja **Prefiks IPv6**, należy określić wartość **Prefiks** w formacie prefiksu IPv6.  

    -   Jeśli zostanie wybrana opcja **Zakres adresów IP**, należ określić wartości **Początkowy adres IP** i **Końcowy adres IP** , które obejmują część podsieci IP lub wiele podsieci IP.    

5.  Kliknij przycisk **OK** , aby zapisać nową granicę.  

## <a name="to-configure-a-boundary"></a>Aby skonfigurować granicę  

1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** > **granic**  

2.  Wybierz granicę, którą chcesz zmodyfikować.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

4.  W oknie dialogowym **Właściwości** dla granicy wybierz kartę **Ogólne** , aby zmodyfikować ustawienia **Opis** lub **Typ** dla granicy. Można także zmienić zakres granicy, edytując jej lokalizacje sieciowe. Dla przykładu, dla granicy lokacji usługi Active Directory można określić nową nazwę lokacji usługi Active Directory.  

5.  Wybierz kartę **Systemy lokacji** , aby wyświetlić systemy lokacji skojarzone z tą granicą. Tej konfiguracji nie można zmienić we właściwościach granicy.  

    > [!TIP]  
    >  Aby serwer systemu lokacji był wyświetlany jako system lokacji dla granicy, należy skojarzyć serwer systemu lokacji jako serwer systemu lokacji dla co najmniej jednej grupy granic obejmującej tę granicę. To ustawienie jest konfigurowane na karcie **Odwołania** grupy granic.  

6.  Wybierz kartę **Grupy granic** , aby zmodyfikować członkostwo tej granicy w grupach granic:  

    -   Aby dodać granicę do jednej lub wielu grup granic, kliknij przycisk **Dodaj**, zaznacz pole wyboru przynajmniej jednej granicy, a następnie kliknij przycisk **OK**.  

    -   Aby usunąć tę granicę z grupy granic, wybierz grupę granic i kliknij przycisk **Usuń**.  

7.  Kliknij przycisk **OK** , aby zamknąć właściwości granicy i zapisać konfigurację.  
