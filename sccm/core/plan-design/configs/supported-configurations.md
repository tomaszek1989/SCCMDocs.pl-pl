---
title: "Obsługiwane konfiguracje"
titleSuffix: Configuration Manager
description: "Identyfikowanie klucza konfiguracje i wymagania, planowanie, wdrażanie i obsługa funkcjonalności wdrażania programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45a10878-ff48-4318-9c6d-c014b38a4039
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 41f339c2a4be80ae247fcc0e5b2e21d3682a7cbc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="supported-configurations-for-system-center-configuration-manager"></a>Obsługiwane konfiguracje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jako rozwiązaniem w firmie System Center Configuration Manager umożliwia korzystanie z serwerów, klientów, konfiguracje sieci i dodatkowe produkty, takie jak Microsoft Intune, programu SQL Server i usługi Azure.

Informacje w tym i w następujących tematach jest pomagające w identyfikacji kluczowe konfiguracje, wymagania i ograniczenia, dzięki czemu można zaplanować, wdrażaniu i obsłudze działającego wdrożenia programu Configuration Manager.  Te informacje są specyficzne dla infrastruktury dla lokacji programu Configuration Manager, hierarchie i zarządzanych urządzeń.

Kiedy funkcja programu Configuration Manager ani funkcja wymaga konfiguracji bardziej szczegółowych informacji znajduje się w dokumentacji właściwych dla funkcji i stanowią uzupełnienie bardziej ogólne szczegóły konfiguracji.  

 Produkty i technologie, które zostały opisane w następujących tematach są obsługiwane przez program Configuration Manager. Jednak włączenie ich do tej zawartości nie oznacza to rozszerzenia obsługi dla dowolnego z tych produktów poza cykl pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza wsparcia technicznego, nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji na temat cykli wsparcia technicznego firmy Microsoft, zobacz witrynę sieci Web [Cykl wsparcia technicznego produktów firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) .  

> [!NOTE]  
>  Dla informacji na temat zasad cyklu pomocy technicznej firmy Microsoft, przejdź do witryny sieci Web firmy Microsoft obsługuje obsługuje technicznego w [Microsoft Cykl wsparcia technicznego](http://go.microsoft.com/fwlink/p/?LinkId=31976).  

 Ponadto produktów i wersji produktu, które nie są wymienione w poniższych tematach nie są obsługiwane z System Center Configuration Manager, chyba że ma zostać ogłaszane na [pakietu Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/).  W czasie zawartości w tym blogu poprzedza aktualizacji do tej części dokumentacji.


-  [Wartości dotyczące rozmiarów i skalowania](../../../core/plan-design/configs/size-and-scale-numbers.md)  
Dowiedz się więcej o liczby witryn role systemu lokacji dla lokacji i klientów lub urządzeń są obsługiwane w projektach innej hierarchii programu Configuration Manager.

-  [Wymagania wstępne dla lokacji i systemu lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)  
Informacje o konfiguracji, które są wymagane w systemie Windows Server do obsługi różnych typów lokacji i ról systemu lokacji.

-  [Obsługiwane systemy operacyjne dla serwerów systemu lokacji](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
Więcej informacji na temat systemów operacyjnych można użyć jako serwer lokacji lub serwer systemu lokacji.

-  [Obsługiwane systemy operacyjne dla klientów i urządzeń](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)  
Więcej informacji na temat systemów operacyjnych można zarządzać z Menedżera konfiguracji, w tym systemu Windows, Windows Embedded, Linux i UNIX, Mac i urządzeń przenośnych.

-  [Obsługiwane systemy operacyjne w konsoli programu](../../../core/plan-design/configs/supported-operating-systems-consoles.md)  
Dowiedz się więcej o tym, które systemy operacyjne mogą obsługiwać konsoli programu Configuration Manager, aby zapewnić punkt dostępu do zarządzania wdrożenia.  

-  [Obsługa wersji programu SQL Server](../../../core/plan-design/configs/support-for-sql-server-versions.md)  
Więcej informacji o wersjach programu SQL Server może hostować bazy danych lokacji i bazy danych raportowania, a także o konfiguracje wymagane i opcjonalne konfiguracje, które można użyć.

-  [Opcje wysokiej dostępności](../../../protect/understand/high-availability-options.md)  
Informacje na temat opcji można implementować przy projektowaniu środowiska, aby zapewnić wysoką dostępność usług dla danego wdrożenia programu Configuration Manager.

-  [Zalecany sprzęt](../../../core/plan-design/configs/recommended-hardware.md)  
Informacje o wskazówki, które pozwalają zidentyfikować odpowiedniego sprzętu i konfiguracji na potrzeby hostowania lokacji programu Configuration Manager i najważniejszych usług.

-  [Obsługa domen usługi Active Directory](../../../core/plan-design/configs/support-for-active-directory-domains.md)  
Więcej informacji o obsługiwanych konfiguracjach domeny usługi Active Directory, które program Configuration Manager wymaga i obsługuje.

-  [Obsługa funkcji systemu Windows i sieci](../../../core/plan-design/configs/support-for-windows-features-and-networks.md)  
Więcej informacji na temat obsługiwanych technologii systemu Windows (na przykład usługi BranchCache i deduplikacja danych) i ograniczenia dotyczące ich używania z programem Configuration Manager.

-  [Obsługa środowisk wirtualizacji](../../../core/plan-design/configs/support-for-virtualization-environments.md)  
Dowiedz się więcej o sposobie używania technologii obsługiwanych maszyn wirtualnych.
