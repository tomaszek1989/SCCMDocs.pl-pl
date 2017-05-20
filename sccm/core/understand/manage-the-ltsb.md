---
title: "Zarządzanie LTSB | Dokumentacja firmy Microsoft"
description: "Różnice zarządzania dla LTSB programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 9c6f349ead906532a7a58df74609de976769e251
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>Zarządzanie długoterminowej obsługi gałęzi programu Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Kiedy używasz długoterminowe obsługi gałęzi (LTSB) programu System Center Configuration Manager, następujące mogą ułatwić zrozumienie ważne zmiany, które mają wpływ na sposób zarządzania infrastrukturą.

Ponieważ LTSB jest równoważne do wersji bieżącej gałęzi 1606 (z kilkoma wyjątkami, takich jak integracji usługi Intune i funkcje związane z chmury), większość zadań jest używany w przypadku planowania, wdrażania, konfiguracji i codziennego zarządzania są takie same.

Na przykład LTSB obsługuje taką samą liczbę witryn, typów lokacji, klientów i ogólna infrastruktura, jako bieżącej gałęzi. W związku z tym należy użyć wskazówek znalezionych w lokacji i hierarchii tematy dotyczące planowania i projektowania dla bieżącej gałęzi. Podobnie dla funkcji z LTSB, które są obsługiwane przez oba gałęzi, takich jak aktualizacje oprogramowania lub wdrożenie systemu operacyjnego, należy użyć wskazówek w sekcji dokumentacji bieżącej gałęzi z ostrzeżenia o nie mają dostępu do funkcji zmiany wprowadzone od wersji 1606 bieżącej gałęzi.

Poniższe sekcje zawierają informacje o zarządzanie zadania, które nie są podobne.

## <a name="updates-and-servicing"></a>Obsługa
Tylko krytyczne aktualizacje zabezpieczeń są udostępniane jako aktualizacji w konsoli w LTSB.  

Informacje o regularne aktualizacje dla późniejszych wersji bieżącej gałęzi są widoczne w konsoli, ale nie były dostępne dla LTSB. Te nie zostaną pobrane i nie może zostać zainstalowana.

Do obsługi aktualizacji w konsoli dla poprawki zabezpieczeń krytyczne, lokacji LTSB wymaga użycia [punkt połączenia usługi](/sccm/core/servers/deploy/configure/about-the-service-connection-point). Ta rola systemu lokacji można skonfigurować w trybie offline lub online, co jest wykonywane dla bieżącej gałęzi. LTSB zbiera i przesyła te same dane telemetryczne i użycia co bieżącej gałęzi.

LTSB obsługuje stosowania poprawek Instalatora i narzędzie do rejestracji aktualizacji opisane dla bieżącej gałęzi.

Ogólne informacje o aktualizacji i obsługę, zobacz [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates).


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>Zmiany dotyczące rozszerzania lokacji i dysku CD. Najnowsze folderu
Po uruchomieniu LTSB i rozszerzanej autonomicznej lokacji głównej przez zainstalowanie nowej witryny Administracja centralna, należy użyć ustawienia i pliki źródłowe z nośnika linii bazowej 1606 wersji. Dla bieżącej gałęzi uruchom Instalatora i użyć plików źródłowych z dysku CD. Najnowszy folder.

Mimo że rozszerzenia lokacji nie uruchamia Instalatora z dysku CD. Najnowszy folder, będziesz nadal używać dysku CD. Najnowsze folderu odzyskiwania lokacji i zainstalować nowe podrzędnej lokacji głównej podczas pierwszej lokacji LTSB został witryny administracji centralnej.

Aby uzyskać więcej informacji na temat rozszerzania lokacji, zobacz [rozszerzyć autonomiczną lokację główną](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site). Aby uzyskać więcej informacji o dysku CD. Najnowszy folder, zobacz [CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder).


## <a name="recovery"></a>Odzyskiwanie
Podczas odzyskiwania lokacji, należy przywrócić witryny lub bazy danych lokacji do jego oryginalnej gałęzi. Nie można odzyskać bazy danych lokacji bieżącej gałęzi do instalacji LTSB lub na odwrót.

