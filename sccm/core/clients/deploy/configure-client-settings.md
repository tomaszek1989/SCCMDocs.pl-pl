---
title: "Konfigurowanie ustawień klienta | Dokumentacja firmy Microsoft"
description: Wybierz ustawienia klienta w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 478d562bfb7fdb3921a4278741ff096e81e6092a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarządzanie wszystkimi ustawieniami klienta w programie System Center Configuration Manager z **Administracja** > **ustawień klienta**. Aby skonfigurować ustawienia dla wszystkich użytkowników i urządzeń w danej hierarchii, do których nie są stosowane żadne ustawienia niestandardowe, należy zmodyfikować ustawienia domyślne. Aby zastosować inne ustawienia tylko do niektórych użytkowników lub urządzeń, należy utworzyć ustawienia niestandardowe i wdrożyć je do kolekcji.  

Aby uzyskać informacje o poszczególnych ustawieniach klienta, zobacz [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  Aby zarządzać klientami w celu oceny, śledzenia i rozwiązywania problemów ze zgodnością konfiguracji urządzeń, można również używać elementów konfiguracji. Aby uzyskać więcej informacji, zobacz [zapewnienia zgodności urządzenia z System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>Skonfiguruj domyślne ustawienia klienta    

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

3.  Na **Home** , wybierz **właściwości**.  

4.  Wyświetl i skonfiguruj ustawienia klienta dla każdej grupy ustawień w okienku nawigacji.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobierania zasad dla pojedynczego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) w [jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Tworzenie i wdrażanie niestandardowych ustawień klienta  
Wdrożenie tych ustawień niestandardowych powoduje, że zastępują one ustawienia domyślne klientów. Przed przystąpieniem do tej procedury upewnij się, że masz kolekcję zawierającą użytkowników lub urządzenia, dla których te ustawienia niestandardowe klienta są wymagane.  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta**.  

3.  Na **Home** karcie w **Utwórz** grupy, wybierz **Tworzenie niestandardowych ustawień klienta**, a następnie wybierz opcję:  

    -   **Utwórz niestandardowe ustawienia urządzenia klienckiego**  

    -   **Utwórz niestandardowe ustawienia użytkownika klienta**  

4.  Określ unikatowy opis nazwy i opcji.  

5.  Zaznacz jedno lub więcej pól wyboru wyświetlających grupy ustawień.  

6.  W okienku nawigacji wybierz poszczególne grupy ustawień i skonfiguruj dostępne ustawienia, a następnie kliknij przycisk **OK**.   

8.  Wybierz niestandardowe ustawienie utworzony klienta. Na **Home** w karcie **ustawień klienta** grupy, wybierz **Wdróż**.  

9. W **Wybieranie kolekcji** okno dialogowe, wybierz odpowiednią kolekcję, a następnie wybierz **OK**. Wybraną kolekcję możesz zweryfikować, klikając kartę **Wdrożenia** w okienku szczegółów.  

10. Wyświetl kolejność niestandardowego ustawienia klienta, które zostało przed chwilą utworzone. W przypadku wielu niestandardowych ustawień klienta są one stosowanie zgodnie z ich liczbą porządkową. Jeżeli występują konflikty, ustawienie o najniższej liczbie porządkowej zastępuje pozostałe ustawienia. Aby zmienić liczbę porządkową, na **Home** w karcie **ustawień klienta** grupy, wybierz **Przenieś element w górę** lub **Przenieś element w dół**.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobierania zasad dla pojedynczego klienta, zobacz [inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) w [jak zarządzać klientami w programie System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

##  <a name="view-client-settings"></a>Wyświetl ustawienia klienta  
 Jeśli do tego samego urządzenia, użytkownika lub grupy użytkowników wdrożono wiele ustawień klienta, ustalanie i łączenie priorytetów może być skomplikowane. Aby wyświetlić ustawienia klienta:  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń** > **użytkowników** lub **kolekcji użytkowników**.  

3.  Wybierz urządzenie, użytkownika lub grupę użytkowników, a następnie z grupy **Ustawienia klienta** wybierz **Wynikowe ustawienia klienta**.  

4.  Wybierz ustawienie klienta z okienka po lewej stronie, a ustawienia są wyświetlane. W tym widoku ustawienia są tylko do odczytu. 

    > [!NOTE]  
    >  Aby wyświetlić ustawienia klienta, musi mieć dostępu do odczytu ustawień klienta.  

    
