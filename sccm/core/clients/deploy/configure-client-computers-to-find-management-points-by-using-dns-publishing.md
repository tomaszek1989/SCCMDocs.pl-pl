---
title: Konfigurowanie publikowania DNS punktów zarządzania znajdowanie klientów
titleSuffix: Configuration Manager
description: Ustaw komputery klienckie pod kątem wyszukiwania punktów zarządzania przy użyciu publikowania DNS w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 03cec407-0f9f-454f-a360-b005af738d29
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3735e2cc8ac2f7e4a5c05b49783cad3981a04930
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-client-computers-to-find-management-points-by-using-dns-publishing-in-system-center-configuration-manager"></a>Jak skonfigurować komputery klienckie pod kątem wyszukiwania punktów zarządzania przy użyciu publikowania DNS w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Klienci w programie System Center Configuration Manager muszą lokalizować punkt zarządzania, aby dokończyć przypisanie lokacji i jako proces w toku ma pozostać zarządzane. Najbezpieczniejszą metodę odnajdywania punktów zarządzania zapewniają klientom w intranecie usługi domenowe Active Directory. Jeśli jednak klienci nie mogą używać metody lokalizowania usługi (na przykład nie został rozszerzony schemat usługi Active Directory lub klienci znajdują się w grupie roboczej), jako preferowaną metodę lokalizowania usługi należy używać publikowania DNS.  

> [!NOTE]  
>  W przypadku zainstalowania klienta z systemem Linux i UNIX należy określić punkt zarządzania, który ma być używany jako pierwszy punkt kontaktu. Aby uzyskać informacje o sposobie instalowania klienta dla systemów Linux i UNIX, zobacz [jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

 Przed użyciem publikowania DNS dla punktów zarządzania należy się upewnić, że serwery DNS w intranecie mają rekordy zasobów lokalizowania usługi (SRV RR) oraz odpowiednie rekordy zasobów hosta (A lub AAA) dla punktów zarządzania lokacji. Rekordy zasobów lokalizacji usługi mogą być tworzone automatycznie przez program Configuration Manager lub ręcznie, administrator systemu DNS, który tworzy rekordy w systemie DNS.  

 Aby uzyskać więcej informacji o funkcji publikowania DNS jako metody lokalizacji usługi dla klientów programu Configuration Manager, zobacz [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

 Domyślnie klienci wyszukują punkty zarządzania w systemie DNS w swojej domenie DNS. Jednak w przypadku żadnych punktów zarządzania publikowanych w domenie klientów ręcznie musi skonfigurować klientów z sufiksu DNS punktu zarządzania. Sufiks DNS można skonfigurować na kliencie podczas instalacji klienta lub po niej:  

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
