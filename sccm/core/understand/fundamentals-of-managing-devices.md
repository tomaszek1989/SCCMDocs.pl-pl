---
title: "Podstawy dotyczące zarządzania urządzeniami | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać programu System Center Configuration Manager do zarządzania urządzeniami."
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: 6
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 45d84122a86da880268c93ecd994250df6b76c8a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>Podstawy zarządzania urządzeniami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager można zarządzać dwie kategorie urządzeń:

-   *Klienci* są urządzeń, takich jak stacje robocze, laptopy, serwerów i urządzeń przenośnych, w którym należy zainstalować oprogramowanie klienta programu Configuration Manager. Niektóre funkcje zarządzania, takich jak spis sprzętu wymagają tego oprogramowania klienta.  

-   *Zarządzane urządzenia* mogą obejmować *klientów*, ale zwykle jest urządzenie przenośne, których nie zainstalowano oprogramowania klienckiego programu Configuration Manager. W tego rodzaju urządzenia można zarządzać za pomocą usługi Intune lub lokalnie wbudowane zarządzanie urządzeniami przenośnymi w programie Configuration Manager.

Można grupować oraz identyfikować urządzenia na podstawie użytkownika, a nie tylko od typu klienta.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Zarządzanie urządzeniami z klientem programu Configuration Manager

Istnieją dwa sposoby używania oprogramowania klienckiego programu Configuration Manager do zarządzania urządzeniem. Pierwszym sposobem jest wykrywanie urządzenia w sieci, a następnie wdrożyć oprogramowanie klienckie dla tego urządzenia. Innym sposobem jest ręcznie zainstaluj oprogramowanie klienckie na nowym komputerze, a następnie dołącz do witryny po dołączeniu sieci komputera. W celu odnalezienia urządzeń, których nie zainstalowano oprogramowania klienckiego, uruchom co najmniej jedną z metod odnajdywania wbudowane. Po wykryciu urządzenia, należy użyć jednej z kilku metod do zainstalowania oprogramowania klienta. Aby uzyskać informacje na temat korzystania z funkcji odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md).  

 Po odnajdywania urządzeń, które są obsługiwane oprogramowanie klienckie programu Configuration Manager, można użyć jednej z kilku metod do zainstalowania oprogramowania. Gdy oprogramowanie zostanie zainstalowane, a klient przypisany do lokacji głównej, możesz rozpocząć zarządzanie urządzeniem.  Typowe metody instalacji to:

 - Wypychana instalacja klienta.

 - Instalacja oparta na aktualizacji oprogramowania.

 - Zasady grupy.

 - Ręczna instalacja na komputerze.
 - W tym klienta jako część obrazu systemu operacyjnego, który można wdrożyć.  


 Po zainstalowaniu klienta możesz uprościć zadania związane z zarządzaniem urządzeniami, używając kolekcji. Kolekcje są grup urządzeń lub użytkowników, którzy tworzenia, dzięki czemu można zarządzać ich jako grupa. Na przykład można zainstalować aplikację dla urządzeń przenośnych na wszystkich urządzeniach przenośnych, które rejestruje programu Configuration Manager. Jeśli jest to możliwe, można użyć kolekcji wszystkie urządzenia przenośne.  

 Aby uzyskać więcej informacji zobacz następujące tematy:  

-   [Wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  

-   [Metody instalacji klienta w programie System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [Wprowadzenie do kolekcji w programie System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>Ustawienia klienta  
 Podczas pierwszej instalacji programu Configuration Manager, wszyscy klienci w hierarchii są konfigurowane przy użyciu domyślnych ustawień klienta, które można zmienić. Ustawienia klienta obejmują takie opcje konfiguracji:

 -  Częstotliwość komunikacji urządzeń z lokacją.

 -  Czy klient jest skonfigurowany dla aktualizacji oprogramowania i innych operacji zarządzania.

 -  Czy użytkownicy mogą rejestrować swoje urządzenia przenośne tak, że są one zarządzane przez program Configuration Manager.  

Można utworzyć niestandardowe ustawienia klienta i przypisać je do kolekcji.  Członkowie kolekcji skonfigurowano niestandardowe ustawienia, a następnie można utworzyć wielu klientów niestandardowych ustawień, które są stosowane w kolejności określonej przez użytkownika (w kolejności numerycznej).  Jeśli występują konflikty ustawień, ustawienie o najniższej liczbie porządkowej zastępuje pozostałe ustawienia.  

Na poniższym diagramie przedstawiono przykładowy sposób tworzenia i stosowania niestandardowych ustawień klienta.  

 ![Ustawienia klienta](media/ClientSettings.gif)  

 Aby dowiedzieć się więcej na temat ustawień klientów, zobacz  
                [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md) i [Informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

## <a name="managing-devices-without-the-configuration-manager-client"></a>Zarządzanie urządzeniami bez klienta programu Configuration Manager  
 Program Configuration Manager obsługuje zarządzanie niektórych urządzeń, których nie zainstalowano oprogramowania klienckiego, a nie są zarządzane przez usługę Intune. Aby uzyskać więcej informacji, zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) i [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

## <a name="user-based-management"></a>Zarządzanie oparte na użytkownika  
 Program Configuration Manager obsługuje kolekcji użytkowników w usługach domenowych w usłudze Active Directory. Podczas korzystania z kolekcji użytkownika, można zainstalować oprogramowania na wszystkich komputerach tego członków użyj kolekcji. Aby upewnić się, że wdrażania oprogramowania, zainstalowana wyłącznie na urządzeniach, które są określane jako główne urządzenie użytkownika, należy skonfigurować koligację urządzenia użytkownika. Każdy użytkownik może mieć przynajmniej jedno urządzenie podstawowe.  

 Jednym ze sposobów, czy użytkownicy mogą zarządzać wdrażaniem oprogramowania jest użycie **Centrum oprogramowania** interfejsu klienta. **Centrum oprogramowania** jest automatycznie instalowany na komputerach klienckich i jest uruchamiany z **Start** menu. **Centrum oprogramowania** pozwala użytkownikom na zarządzanie oprogramowaniem i wykonaj następujące czynności:  

-   Zainstaluj oprogramowanie.  

-   Zaplanowanie automatycznej instalacji poza godzinami pracy oprogramowania.  

-   Skonfiguruj w przypadku programu Configuration Manager może instalować oprogramowanie na urządzeniu.  

-   Konfigurowanie ustawień dostępu do zdalnego sterowania, jeśli zdalne sterowanie jest skonfigurowana w programie Configuration Manager.  

-   Skonfiguruj opcje zarządzania zasilaniem, jeśli administrator konfiguruje tę opcję.  


 Łącza w **Centrum oprogramowania** umożliwia użytkownikom łączenie się **katalogu aplikacji**, gdzie można przeglądać w poszukiwaniu, zainstalować i wysyłać żądania dotyczące oprogramowania. **Katalogu aplikacji** służy także do konfigurowania ustawień preferencji, czyszczenie urządzeń przenośnych i po jej skonfigurowaniu, określ urządzenie podstawowe koligację urządzenia użytkownika.   

 Użytkownicy mogą również uzyskać dostęp **katalogu aplikacji** za pośrednictwem przeglądarki, intranetu lub Internetu sesji.  

