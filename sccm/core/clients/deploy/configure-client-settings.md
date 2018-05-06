---
title: Konfigurowanie ustawień klienta
titleSuffix: Configuration Manager
description: Wybierz ustawienia klienta w programie System Center Configuration Manager.
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0405769d3cfc7f77c4ab639ddc0f9ed0cd561366
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie wszystkimi ustawieniami klienta w programie System Center Configuration Manager z **administracji** > **ustawień klienta**. Aby skonfigurować ustawienia dla wszystkich użytkowników i urządzeń w danej hierarchii, do których nie są stosowane żadne ustawienia niestandardowe, należy zmodyfikować ustawienia domyślne. Jeśli chcesz zastosować inne ustawienia tylko do niektórych użytkowników lub urządzeń, należy utworzyć ustawienia niestandardowe i wdrożyć do kolekcji.  

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

10. Wyświetl kolejność niestandardowe ustawienie klienta, które zostały utworzone. W przypadku wielu niestandardowych ustawień klienta są one stosowanie zgodnie z ich liczbą porządkową. Jeżeli występują konflikty, ustawienie o najniższej liczbie porządkowej zastępuje pozostałe ustawienia. Aby zmienić liczbę porządkową, na **Home** karcie **ustawień klienta** grupy, wybierz **Przenieś element w górę** lub **Przenieś element w dół**.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) w [jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  



##  <a name="view-client-settings"></a>Wyświetl ustawienia klienta  
 Podczas wdrażania wielu ustawień klienta do tego samego urządzenia, użytkownika lub grupy użytkowników, ustalanie i łączenie ustawienia jest złożone. Aby wyświetlić ustawienia klienta:  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń** > **użytkowników** lub **kolekcje użytkowników**.  

3.  Wybierz urządzenie, użytkownika lub grupę użytkowników, a następnie z grupy **Ustawienia klienta** wybierz **Wynikowe ustawienia klienta**.  

4.  Wybierz ustawienie klienta z okienka po lewej stronie, a ustawienia są wyświetlane. W tym widoku ustawienia są tylko do odczytu. 

    > [!NOTE]  
    >  Aby wyświetlić ustawienia klienta, musi mieć dostęp do odczytu do ustawień klienta.  

    