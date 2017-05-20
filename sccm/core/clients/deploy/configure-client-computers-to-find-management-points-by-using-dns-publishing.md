---
title: "Konfigurowanie publikowania DNS punkty zarządzania Znajdź klientów | Dokumentacja firmy Microsoft"
description: "Ustaw komputery klienckie w celu znalezienia punktów zarządzania przy użyciu publikowania DNS w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 03cec407-0f9f-454f-a360-b005af738d29
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d016ec3fe106b2d90b3c14b4f9296aed4d198644
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-computers-to-find-management-points-by-using-dns-publishing-in-system-center-configuration-manager"></a>Jak skonfigurować komputery klienckie w celu znalezienia punktów zarządzania przy użyciu publikowania DNS w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Klienci w programie System Center Configuration Manager należy znaleźć punkt zarządzania, aby dokończyć przypisanie lokacji i jako proces w toku i zarządzani. Najbezpieczniejszą metodę odnajdywania punktów zarządzania zapewniają klientom w intranecie usługi domenowe Active Directory. Jeśli jednak klienci nie mogą używać metody lokalizowania usługi (na przykład nie został rozszerzony schemat usługi Active Directory lub klienci znajdują się w grupie roboczej), jako preferowaną metodę lokalizowania usługi należy używać publikowania DNS.  

> [!NOTE]  
>  W przypadku zainstalowania klienta z systemem Linux i UNIX należy określić punkt zarządzania, który ma być używany jako pierwszy punkt kontaktu. Aby uzyskać informacje o sposobie instalowania klienta z systemem Linux i UNIX, zobacz [wdrażanie klientów do serwerów systemu UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

 Przed użyciem publikowania DNS dla punktów zarządzania należy się upewnić, że serwery DNS w intranecie mają rekordy zasobów lokalizowania usługi (SRV RR) oraz odpowiednie rekordy zasobów hosta (A lub AAA) dla punktów zarządzania lokacji. Rekordy zasobów lokalizacji usługi mogą być tworzone automatycznie przez program Configuration Manager lub ręcznie, administrator systemu DNS, który tworzy rekordy w systemie DNS.  

 Aby uzyskać więcej informacji o funkcji publikowania DNS jako metodzie lokalizowania usług dla klientów programu Configuration Manager, zobacz [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

 Domyślnie klienci wyszukują punkty zarządzania w systemie DNS w swojej domenie DNS. Jednak jeśli nie ma żadnych punktów zarządzania publikowanych w domenie klienta, należy ręcznie skonfigurować klientów za pomocą sufiksu DNS punktu zarządzania. Sufiks DNS można skonfigurować na kliencie podczas instalacji klienta lub po niej:  

-   Aby skonfigurować klientów sufiksem punktu zarządzania podczas instalacji, należy skonfigurować właściwości pliku Client.msi programu CCMSetup.  

-   Aby skonfigurować klientów sufiksem punktu zarządzania po instalacji, należy w Panelu sterowania skonfigurować **Właściwości programu Configuration Manager**.  

#### <a name="to-configure-clients-for-a-management-point-suffix-during-client-installation"></a>Aby skonfigurować klientów sufiksem punktu zarządzania podczas instalacji  

-   Zainstaluj klienta za pomocą następującej właściwości pliku Client.msi programu CCMSetup:  

    -   **DNSSUFFIX =**  *&lt;domeny punktu zarządzania\>*  

         Jeśli w lokacji jest więcej niż jeden punkt zarządzania i znajdują się one w więcej niż jednej domenie, wystarczy określić tylko jedną domenę. Jeśli klienci łączą się z punktem zarządzania w bieżącej domenie, pobierają listę dostępnych punktów zarządzania, która zawiera punkty z innych domen.  

     Aby uzyskać więcej informacji o właściwościach wiersza polecenia programu CCMSetup, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

#### <a name="to-configure-clients-for-a-management-point-suffix-after-client-installation"></a>Aby skonfigurować klientów sufiksem punktu zarządzania po instalacji  

1.  W Panelu sterowania komputera klienckiego przejdź do programu **Configuration Manager**i dwukrotnie kliknij pozycję **Właściwości**.  

2.  Na karcie **Lokacja** określ sufiks DNS punktu zarządzania, a następnie kliknij przycisk **OK**.  

     Jeśli w lokacji jest więcej niż jeden punkt zarządzania i znajdują się one w więcej niż jednej domenie, wystarczy określić tylko jedną domenę. Jeśli klienci łączą się z punktem zarządzania w bieżącej domenie, pobierają listę dostępnych punktów zarządzania, która zawiera punkty z innych domen.
