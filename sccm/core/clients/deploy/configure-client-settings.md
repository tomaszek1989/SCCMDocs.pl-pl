---
title: "Konfigurowanie ustawień klienta"
titleSuffix: Configuration Manager
description: Wybierz ustawienia klienta w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: "5"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 20a8f91d10d98542f08e440bcfbc1a6f98a51932
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie wszystkimi ustawieniami klienta w programie System Center Configuration Manager z **administracji** > **ustawień klienta**. Aby skonfigurować ustawienia dla wszystkich użytkowników i urządzeń w danej hierarchii, do których nie są stosowane żadne ustawienia niestandardowe, należy zmodyfikować ustawienia domyślne. Aby zastosować inne ustawienia tylko do niektórych użytkowników lub urządzeń, należy utworzyć ustawienia niestandardowe i wdrożyć je do kolekcji.  

Aby uzyskać informacje o poszczególnych ustawieniach klienta, zobacz [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  Aby zarządzać klientami w celu oceny, śledzenia i rozwiązywania problemów ze zgodnością konfiguracji urządzeń, można również używać elementów konfiguracji. Aby uzyskać więcej informacji, zobacz [zapewnianie zgodności urządzeń w programie System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>Skonfiguruj domyślne ustawienia klienta    

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

3.  Na **Home** , wybierz pozycję **właściwości**.  

4.  Wyświetl i skonfiguruj ustawienia klienta dla każdej grupy ustawień w okienku nawigacji.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) w [jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Tworzenie i wdrażanie niestandardowych ustawień klienta  
Wdrożenie tych ustawień niestandardowych powoduje, że zastępują one ustawienia domyślne klientów. Przed przystąpieniem do tej procedury upewnij się, że masz kolekcję zawierającą użytkowników lub urządzenia, dla których te ustawienia niestandardowe klienta są wymagane.  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Tworzenie niestandardowych ustawień klienta**i wybrać opcję:  

    -   **Utwórz niestandardowe ustawienia urządzenia klienckiego**  

    -   **Utwórz niestandardowe ustawienia użytkownika klienta**  

4.  Określ unikatowy opis nazwy i opcji.  

5.  Zaznacz jedno lub więcej pól wyboru wyświetlających grupy ustawień.  

6.  W okienku nawigacji wybierz poszczególne grupy ustawień i skonfiguruj dostępne ustawienia, a następnie kliknij przycisk **OK**.   

8.  Wybierz niestandardowe ustawienie klienta, które zostały utworzone. Na **Home** karcie **ustawień klienta** grupy, wybierz **Wdróż**.  

9. W **Wybieranie kolekcji** okno dialogowe, wybierz odpowiednią kolekcję, a następnie wybierz **OK**. Wybraną kolekcję możesz zweryfikować, klikając kartę **Wdrożenia** w okienku szczegółów.  

10. Wyświetl kolejność niestandardowego ustawienia klienta, które zostało przed chwilą utworzone. W przypadku wielu niestandardowych ustawień klienta są one stosowanie zgodnie z ich liczbą porządkową. Jeżeli występują konflikty, ustawienie o najniższej liczbie porządkowej zastępuje pozostałe ustawienia. Aby zmienić liczbę porządkową, na **Home** karcie **ustawień klienta** grupy, wybierz **Przenieś element w górę** lub **Przenieś element w dół**.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) w [jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

## <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Ogranicz rozszerzony systemu Windows 10 telemetrię, aby wysyłać dane tylko istotne dla kondycji urządzenia Analytics systemu Windows
<!-- 1356148 -->

Aktualizacja 1710, można ustawić zbieranie danych telemetrii systemu Windows 10 do poziomu **rozszerzony (ograniczony)**. To ustawienie umożliwia uzyskania przydatnych wyników informacje na temat urządzeń w środowisku bez urządzenia podlegające wszystkie dane w **rozszerzony** telemetrii poziomu z systemem Windows 10 w wersji 1709 lub nowszej.

Poziom telemetria rozszerzony (ograniczony) zawiera metryki z poziomu podstawowego, jak również podzbiór danych zbieranych z **rozszerzony** poziom zastosowanie w module analiz systemu Windows. Aby uzyskać więcej informacji dotyczących poziomów telemetrii, zobacz [poziomy Telemetrii](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization#telemetry-levels).

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

2.  Na **Home** , wybierz pozycję **właściwości**.  

3.  Otwórz **usługi w chmurze**i ustaw telemetrii systemu Windows 10 **rozszerzony**.

##  <a name="view-client-settings"></a>Wyświetl ustawienia klienta  
 Jeśli do tego samego urządzenia, użytkownika lub grupy użytkowników wdrożono wiele ustawień klienta, ustalanie i łączenie priorytetów może być skomplikowane. Aby wyświetlić ustawienia klienta:  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń** > **użytkowników** lub **kolekcje użytkowników**.  

3.  Wybierz urządzenie, użytkownika lub grupę użytkowników, a następnie z grupy **Ustawienia klienta** wybierz **Wynikowe ustawienia klienta**.  

4.  Wybierz ustawienie klienta z okienka po lewej stronie, a ustawienia są wyświetlane. W tym widoku ustawienia są tylko do odczytu. 

    > [!NOTE]  
    >  Aby wyświetlić ustawienia klienta, musi mieć dostęp do odczytu do ustawień klienta.  

    