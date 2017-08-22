---
title: "Metody instalacji klientów | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej metod instalacji klienta programu System Center Configuration Manager."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: "9"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: edca31249cc2bb3e0c67265962815c82e3f4711e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>Metody instalacji klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można użyć różnych metod do zainstalowania oprogramowania klienta programu Configuration Manager. Można użyć jednej metody lub kombinacji metod. W tym temacie można znaleźć dotyczące każdej z metod, aby dowiedzieć się, które będzie najlepiej w Twojej organizacji.  

## <a name="client-push-installation"></a>Wypychana instalacja klienta  

 **Obsługiwana platforma kliencka:** Systemu Windows  

 **Zalety**  

-   Można jej użyć do instalacji klienta na jednym komputerze, kolekcji komputerów lub w celu obsługi wyników kwerendy.  

-   Można jej użyć do automatycznej instalacji klientów na wszystkich wykrytych komputerach.  

-   Automatycznie wykorzystuje właściwości instalacji klienta zdefiniowane na karcie **Klient** w oknie dialogowym **Właściwości instalacji klienta w trybie push**.  

 **Wady**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku wypychania w dużych kolekcjach.  

-   Można używać tylko na komputerach, które zostały odnalezione przez program Configuration Manager.  

-   Nie można jej użyć do instalacji klientów w grupie roboczej.  

-   Należy określić konto instalacji wypychanej klienta z prawami administracyjnymi do danego komputera.  

-   W Zaporze systemu Windows na komputerze klienckim należy skonfigurować wyjątki, aby umożliwić dokończenie instalacji wypychanej klientów.  

-   Instalacji wypychanej klientów nie można anulować. Użycie tej metody instalacji klientów dla lokacji programu Configuration Manager próbuje zainstalować klienta na wszystkich wykrytych zasobach i ponawia zakończą się niepowodzeniem przez okres do 7 dni.  

 Aby uzyskać więcej informacji na temat tej metody instalacji, zobacz [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="software-update-point-based-installation"></a>Instalacja oparta na punkcie aktualizacji oprogramowania  
 **Obsługiwana platforma kliencka:** Systemu Windows  

 **Zalety:**  

-   Umożliwia wykorzystanie istniejącej infrastruktury aktualizacji oprogramowania do zarządzania oprogramowaniem na klientach.  

-   Umożliwia automatyczną instalację oprogramowania klienta na nowych komputerach, jeżeli program Windows Server Update Services (WSUS) i ustawienia zasad grupy w usługach domenowych w usłudze Active Directory są skonfigurowane prawidłowo.  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach domenowych w usłudze Active Directory.  

-   Ponownie zainstaluje oprogramowanie klienta, jeżeli zostanie usunięte.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

 **Wady:**  

-   Warunkiem wstępnym jest działająca infrastruktura aktualizacji oprogramowania.  

-   Musi korzystać z tego samego serwera w celu instalacji klienta i aktualizacji oprogramowania, a serwer musi znajdować się w lokacji głównej.  

-   Aby zainstalować nowych klientów, należy skonfigurować obiekt zasad grupy (GPO) w usługach Active Directory Domain Services, używając aktywnego punktu aktualizacji oprogramowania i portu klienta.  

-   Jeżeli schemat usługi Active Directory nie zostanie rozszerzony dla programu Configuration Manager, należy użyć ustawień zasad grupy do udostępnienia na komputerach właściwości instalacji klienta.  

 Aby uzyskać więcej informacji na temat tej metody instalacji, zobacz [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="group-policy-installation"></a>Instalacja zasad grupy  
 **Obsługiwana platforma kliencka:** Systemu Windows  

 **Zalety:**  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach domenowych w usłudze Active Directory.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

 **Wady:**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku instalowania dużej liczby klientów.  

-   Jeżeli schemat usługi Active Directory nie zostanie rozszerzony dla programu Configuration Manager, należy użyć ustawień zasad grupy w celu dodania właściwości instalacji klienta komputerom w lokacji.  

 Aby uzyskać więcej informacji na temat tej metody instalacji, zobacz [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="logon-script-installation"></a>Instalacja skryptu logowania  
 **Obsługiwana platforma kliencka:** Systemu Windows  

 **Zalety:**  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady:**  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku instalowania dużej liczby klientów w krótkim czasie.  

-   Instalacja na wszystkich komputerach klienckich może potrwać długo, jeżeli użytkownicy nie logują się często do sieci.  

 Aby uzyskać więcej informacji na temat tej metody instalacji, zobacz [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

## <a name="manual-installation"></a>Instalacja ręczna  
 **Obsługiwana platforma kliencka:** Windows, UNIX/Linux, Mac OS X  

 **Zalety:**  

-   Nie ma konieczności odnajdywania komputerów przed zainstalowaniem klienta.  

-   Może być przydatna do celów testowych.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

 **Wady:**  

-   Brak automatyzacji, dlatego jest czasochłonna.  

 Aby uzyskać więcej informacji na temat sposobu ręcznej instalacji klienta na każdej platformie, zobacz następujące tematy:  

-   [Jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

-   [Jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)  

-   [Jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  
