---
title: "Funkcje i możliwości | Dokumentacja firmy Microsoft"
description: "Informacje o najważniejszych funkcjach zarządzania programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 53b27dcb5c8bb670556fe4cee9e990619a9a63e9
ms.openlocfilehash: 4691f43dccdf73936107f4635321897b9779bead
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>Funkcje i możliwości programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Poniżej przedstawiono najważniejszych funkcjach zarządzania programu System Center Configuration Manager. Każda możliwość ma oddzielne wymagania wstępne i możliwości, które chcesz użyć mogą mieć wpływ projektowania i implementacji hierarchii programu Configuration Manager. Na przykład do wdrażania oprogramowania na urządzeniach w hierarchii, należy zainstalować rolę systemu lokacji punktu dystrybucji.  

 Aby uzyskać więcej informacji o sposobie planowania i wykonywania instalacji programu Configuration Manager do obsługi tych funkcji zarządzania w środowisku, zobacz [Przygotuj System Center Configuration Manager](../../../core/plan-design/get-ready.md).  

 **Zarządzanie aplikacjami**  

 Obejmują zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie aplikacji oraz zarządzanie nimi na różnych typach zarządzanych urządzeń. Ponadto program Configuration Manager zawiera można za pomocą narzędzi, które pomagają chronić dane firmy w aplikacjach użytkownika. Zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management).

 **Dostęp do zasobów firmy**  

 Obejmują zestaw narzędzi i zasobów, dzięki którym można umożliwić użytkownikom w organizacji dostęp do danych i aplikacji z lokalizacji zdalnych. Narzędzia te zawierają sieci Wi-Fi profile sieci VPN profile, profile certyfikatów i dostępu warunkowego do programu Exchange i SharePoint online. Zobacz [ochrony danych i lokacji infrastruktury z System Center Configuration Manager](../../../protect/understand/protect-data-and-site-infrastructure.md) i [zarządzanie dostępem do usług w programie System Center Configuration Manager](../../../protect/deploy-use/manage-access-to-services.md).  

 **Ustawienia zgodności**  

 Zawiera zestaw narzędzi i zasobów ułatwiających do oceny, śledzenia i rozwiązywania problemów ze zgodnością konfiguracji urządzeń klienckich w przedsiębiorstwie. Można użyć ustawień zgodności i skonfigurować zakres funkcji i ustawień zabezpieczeń na urządzeniach, którymi można zarządzać. Zobacz [zapewnienia zgodności urządzenia z System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

 **Program Program Endpoint Protection**  

 Obejmuje zarządzanie bezpieczeństwem, oprogramowaniem chroniącym przed złośliwym kodem oraz zaporą systemu Windows w komputerach przedsiębiorstwa. Zobacz [ochrony punktu końcowego programu System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

 **Spis**  

 Zawiera zestaw narzędzi do identyfikacji i monitorowania zasobów:  

-   **Spis sprzętu**: Zbiera szczegółowe informacje o urządzeniach w przedsiębiorstwie. Zobacz [wprowadzenie do spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md).  

-   **Spis oprogramowania**: Zbiera i raportuje informacje o plikach, które są przechowywane na komputerach klienckich w organizacji. Zobacz [wprowadzenie do spisu oprogramowania System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-software-inventory.md).  

-   **Analiza zasobów**: Zawiera narzędzia do zbierania danych o zapasach oraz monitorowania wykorzystania licencji na oprogramowanie w przedsiębiorstwie. Zobacz [wprowadzenie do analizy zasobów programu System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

**Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune**  

 Do zarządzania systemem iOS, Android (w tym Samsung KNOX Standard), Windows Phone i urządzeń z systemem Windows przy użyciu usługi Microsoft Intune za pośrednictwem Internetu, można użyć programu Configuration Manager.

 Mimo że używasz usługi Intune zadania zarządzania są wykonywane za pomocą usługi połączenia roli systemu lokacji punktu dostępne za pośrednictwem konsoli programu Configuration Manager. Zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) za pomocą programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

 **Zarządzanie urządzeniami przenośnymi lokalnego**  

 Rejestruje i zarządza komputerami i urządzeniami przenośnymi przy użyciu funkcji infrastruktury i zarządzania programu Configuration Manager lokalnych wbudowane platformy urządzeń (a nie oddzielnie zainstalowanego klienta programu Configuration Manager). Obecnie obsługuje zarządzanie urządzeniami z systemem Windows 10 Enterprise i Windows 10 Mobile. Zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Wdrożenie systemu operacyjnego**  

 Obejmuje narzędzia do tworzenia obrazów systemu operacyjnego: Można następnie użyć tych obrazów do wdrażania systemów operacyjnych na komputerach, za pomocą środowiska PXE rozruchu lub nośnika rozruchowego, takich jak zestaw dysków CD, DVD lub USB dyski flash. Należy zauważyć, że dotyczy to komputerów, które są zarządzane przez program Configuration Manager, a także komputerach niezarządzanych. Zobacz [wprowadzenie do wdrażania systemu operacyjnego w programie System Center Configuration Manager](../../../osd/understand/introduction-to-operating-system-deployment.md).  

 **Zarządzanie energią**  

 Obejmuje zestaw narzędzi i zasobów ułatwiających zarządzanie poborem mocy przez klientów w przedsiębiorstwie i monitorowanie go. Zobacz [wprowadzenie do zarządzania zużyciem energii w programie System Center Configuration Manager](../../../core/clients/manage/power/introduction-to-power-management.md).  

 **Zapytania**  

 Obejmuje narzędzia do pobierania informacji o zasobach w hierarchii oraz danych o zapasach i komunikatów o stanie. Można następnie użyć tych informacji do tworzenia raportów i definiowania kolekcji urządzeń lub użytkowników w celu wdrożenia oprogramowania oraz konfiguracji ustawień. Zobacz [wprowadzenie do kwerend w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md).  

 **Profile połączenia zdalnego**  

 Zawiera zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie ustawień połączeń zdalnych na urządzeniach w organizacji. Wdrażając te ustawienia, można zminimalizować nakład pracy wymagany przez użytkowników w celu połączenia ich komputerów w sieci firmowej. Zobacz [Praca z profili połączenia zdalnego w programie System Center Configuration Manager](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

 **Elementy konfiguracji profilów i danych użytkownika**  

 Elementy danych użytkownika i profili konfiguracji w programie Configuration Manager zawiera ustawienia, które mogą zarządzać przekierowania folderu, plikami trybu offline i profilów mobilnych na komputerach z systemem Windows 8 i nowszym dla użytkowników w hierarchii. Zobacz [Praca z użytkownika profilów i danych elementów konfiguracji w programie System Center Configuration Manager](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

 **Zdalne sterowanie**  

 Zawiera narzędzia do zdalnego zarządzania klientami z konsoli programu Configuration Manager. Zobacz [wprowadzenie do zdalnego sterowania w programie System Center Configuration Manager](../../../core/clients/manage/remote-control/introduction-to-remote-control.md).  

 **Raportowanie**  

 Zawiera zestaw narzędzi i zasobów, które ułatwiają korzystanie z zaawansowanych możliwości raportowania usług SQL Server Reporting Services z konsoli programu Configuration Manager. Zobacz [wprowadzenie do raportowania w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md).  

 **Pomiar użytkowania oprogramowania**  

 Zawiera narzędzia do monitorowania i zbierania danych o użytkowaniu oprogramowania z klientów programu Configuration Manager. Zobacz [Monitorowanie użycia aplikacji za pomocą funkcji pomiaru użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

 **Aktualizacje oprogramowania**  

 Obejmuje zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie aktualizacji oprogramowania w przedsiębiorstwie. Zobacz [aktualizuje wprowadzenie do oprogramowania System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).  

