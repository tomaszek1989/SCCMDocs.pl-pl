---
title: Metody instalacji klientów
titleSuffix: Configuration Manager
description: Więcej informacji na temat metody instalowania klienta programu Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 38f7d428149f4a4ac2b0bcb604031eca60a0fae5
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>Metody instalacji klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można użyć różnych metod do zainstalowania oprogramowania klienta programu Configuration Manager. Użyj jednej metody lub kombinacji metod. W tym artykule opisano każdej metody, dzięki czemu możliwe, które z nich działa najlepiej w danej organizacji.  

## <a name="client-push-installation"></a>Wypychana instalacja klienta  

**Obsługiwana platforma kliencka**: Windows  

#### <a name="advantages"></a>Zalety  

-   Można jej użyć do instalacji klienta na jednym komputerze, kolekcji komputerów lub w celu obsługi wyników kwerendy.  

-   Można jej użyć do automatycznej instalacji klientów na wszystkich wykrytych komputerach.  

-   Automatycznie wykorzystuje właściwości instalacji klienta zdefiniowane na karcie **Klient** w oknie dialogowym **Właściwości instalacji klienta w trybie push**.  

#### <a name="disadvantages"></a>Wady  

-   Może spowodować duże zwiększenie ruchu sieciowego w przypadku wypychania w dużych kolekcjach.  

-   Można używać tylko na komputerach, które zostały odnalezione przez program Configuration Manager.  

-   Nie można użyć do instalacji klientów w grupie roboczej.  

-   Należy określić konto instalacji wypychanej klienta z prawami administracyjnymi do danego komputera.  

-   Zapora systemu Windows musi być skonfigurowany z wyjątków na komputerach klienckich.   

-   Nie można anulować instalacji wypychanej klienta. Program Configuration Manager próbuje zainstalować klienta na wszystkich wykrytych zasobach. Wszelkie błędy ponowną przez maksymalnie 7 dni.  

Aby uzyskać więcej informacji, zobacz [jak instalować klientów z wypychaniem klienta](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush).  



## <a name="software-update-point-based-installation"></a>Instalacja oparta na punkcie aktualizacji oprogramowania  

**Obsługiwana platforma kliencka**: Windows  

#### <a name="advantages"></a>Zalety  

-   Umożliwia wykorzystanie istniejącej infrastruktury aktualizacji oprogramowania do zarządzania oprogramowaniem na klientach.  

-   Gdy system Windows Server Update Services (WSUS) i ustawienia zasad grupy w usługach domenowych w usłudze Active Directory są skonfigurowane poprawnie, go automatycznie zainstalować oprogramowanie klienckie na nowych komputerach.  

-   Nie wymaga komputerów, które mają zostać wykryte, aby można było zainstalować klienta.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach Active Directory Domain Services.  

-   Jeśli klient zostanie usunięty, ta metoda zainstaluje go ponownie.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

#### <a name="disadvantages"></a>Wady  

-   Warunkiem wstępnym jest działająca infrastruktura aktualizacji oprogramowania.  

-   Należy użyć tego samego serwera dla instalacji klienta i aktualizacji oprogramowania. Ten serwer musi znajdować się w lokacji głównej.  

-   Aby zainstalować nowych klientów, należy skonfigurować obiekt zasad grupy w usługach domenowych w usłudze Active Directory z aktywnym punktem aktualizacji oprogramowania i portu klienta.  

-   Jeśli schemat usługi Active Directory nie jest rozszerzony dla programu Configuration Manager, należy użyć ustawień zasad grupy w celu udostępniania komputerów z właściwości instalacji klienta.  

Aby uzyskać więcej informacji, zobacz [jak instalować klientów z instalacją opartą na aktualizacji oprogramowania](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientSUP).  



## <a name="group-policy-installation"></a>Instalacja zasad grupy  

**Obsługiwana platforma kliencka**: Windows  

#### <a name="advantages"></a>Zalety  

-   Nie wymaga komputerów, które mają zostać wykryte, aby można było zainstalować klienta.  

-   Można jej użyć do instalacji nowych klientów lub uaktualnień.  

-   Komputery mogą odczytać właściwości instalacji klienta, które zostały opublikowane w usługach Active Directory Domain Services.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

#### <a name="disadvantages"></a>Wady  

-   W przypadku instalowania dużej liczby klientów może spowodować duże zwiększenie ruchu sieciowego.  

-   Jeśli schemat usługi Active Directory nie jest rozszerzony dla programu Configuration Manager, musi użyć ustawień zasad grupy do dodania właściwości instalacji klienta komputerom w lokacji.  

Aby uzyskać więcej informacji, zobacz [jak instalować klientów przy użyciu zasad grupy](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientGP).  



## <a name="logon-script-installation"></a>Instalacja skryptu logowania  

**Obsługiwana platforma kliencka**: Windows  

#### <a name="advantages"></a>Zalety  

-   Nie wymaga komputerów, które mają zostać wykryte, aby można było zainstalować klienta.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

#### <a name="disadvantages"></a>Wady  

-   Duża liczba klientów są instalowane w krótkim czasie, może spowodować duże zwiększenie ruchu sieciowego.  

-   Jeśli użytkownicy nie logują się często do sieci, może potrwać długo, aby zainstalować na wszystkich komputerach klienckich.  

Aby uzyskać więcej informacji, zobacz [jak instalować klientów za pomocą skryptów logowania](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientLogonScript).  



## <a name="manual-installation"></a>Instalacja ręczna  

**Obsługiwana platforma kliencka**: Windows, UNIX/Linux, Mac OS X  

#### <a name="advantages"></a>Zalety  

-   Nie wymaga komputerów, które mają zostać wykryte, aby można było zainstalować klienta.  

-   Może być przydatna do celów testowych.  

-   Obsługa przy użyciu właściwości wiersza polecenia programu CCMSetup.  

#### <a name="disadvantages"></a>Wady  

-   Brak automatyzacji, dlatego jest czasochłonna.  

Aby uzyskać więcej informacji na temat sposobu ręcznej instalacji klienta na każdej platformie, zobacz następujące artykuły:  

-   [Jak wdrażać klientów na komputerach z systemem Windows](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)  

-   [Jak wdrażać klientów na serwerach z systemami UNIX i Linux](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)  

-   [Jak wdrażać klientów na komputerach Mac](/sccm/core/clients/deploy/deploy-clients-to-macs)  



## <a name="microsoft-intune-mdm-installation"></a>Instalacja programu Microsoft Intune MDM

**Obsługiwane platformy klienta**: Windows 10

#### <a name="advantages"></a>Zalety  

-   Nie wymaga komputerów, które mają zostać wykryte, aby można było zainstalować klienta.  

-   Nie wymaga konfigurowania i konserwacji konta instalacji dla danego komputera klienckiego.  

-   Można użyć nowoczesnego uwierzytelniania w usłudze Azure Active Directory.  

-   Można zainstalować i przypisywania komputerów w Internecie.  

-   Można zautomatyzować z AutoPilot systemu Windows i Microsoft Intune do zarządzania wspólnej.  

#### <a name="disadvantages"></a>Wady  

-   Wymaga dodatkowych technologii poza programu Configuration Manager.  

-   Wymaga urządzenia mają dostęp do Internetu, nawet jeśli nie jest oparty na Internecie.  

Aby uzyskać więcej informacji zobacz następujące artykuły:  

-   [Jak zainstalować klientów na urządzeniach zarządzanych Intune zarządzanie urządzeniami Przenośnymi z systemem Windows](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#bkmk_mdm)  

-   [Zainstaluj i przypisz przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

