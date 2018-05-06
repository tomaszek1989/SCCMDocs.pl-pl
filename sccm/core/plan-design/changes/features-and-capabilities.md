---
title: Funkcje i możliwości
titleSuffix: Configuration Manager
description: Informacje o najważniejszych funkcjach zarządzania programu System Center Configuration Manager.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fadc93d1977d5d066a6c4c3884bdbaeefb2a0c90
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>Funkcje i możliwości programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniżej przedstawiono najważniejszych funkcjach zarządzania programu System Center Configuration Manager. Każda możliwość ma oddzielne wymagania wstępne i możliwości, które mają być wykorzystywane mogą mieć wpływ na projekt i implementację hierarchii programu Configuration Manager. Na przykład jeśli chcesz wdrożyć oprogramowanie na urządzeniach w hierarchii, należy zainstalować rolę systemu lokacji punktu dystrybucji.  

 Aby uzyskać więcej informacji na temat planowania i wykonywania instalacji programu Configuration Manager do obsługi tych możliwości zarządzania w środowisku, zobacz [przygotowania programu System Center Configuration Manager](../../../core/plan-design/get-ready.md).  

 **Zarządzanie aplikacjami**  

 Obejmują zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie aplikacji oraz zarządzanie nimi na różnych typach zarządzanych urządzeń. Ponadto programu Configuration Manager udostępnia narzędzia, które ułatwiają ochronę danych firmowych w aplikacjach użytkownika. Zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management).

 **Dostęp do zasobów firmy**  

 Obejmują zestaw narzędzi i zasobów, dzięki którym można umożliwić użytkownikom w organizacji dostęp do danych i aplikacji z lokalizacji zdalnych. Narzędzia te obejmują sieci Wi-Fi profile sieci VPN profile, profile certyfikatów i dostępu warunkowego do programu Exchange i SharePoint online. Zobacz [ochrona danych i infrastruktury lokacji z System Center Configuration Manager](../../../protect/understand/protect-data-and-site-infrastructure.md) i [zarządzanie dostępem do usług w programie System Center Configuration Manager](../../../protect/deploy-use/manage-access-to-services.md).  

 **Ustawienia zgodności**  

 Udostępnia zestaw narzędzi i zasobów, które mogą ułatwić do oceny, śledzenia i naprawiania zgodności konfiguracji urządzeń klienckich w przedsiębiorstwie. Ponadto można użyć ustawień zgodności można skonfigurować szereg funkcji i ustawień bezpieczeństwa na urządzeniach, którymi zarządzasz. Zobacz [zapewnianie zgodności urządzeń w programie System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

 **Program Endpoint Protection**  

 Obejmuje zarządzanie bezpieczeństwem, oprogramowaniem chroniącym przed złośliwym kodem oraz zaporą systemu Windows w komputerach przedsiębiorstwa. Zobacz [programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

 **Inventory** (Spis)  

 Udostępnia zestaw narzędzi do identyfikacji i monitorowania zasobów:  

-   **Spis sprzętu**: Zbiera szczegółowe informacje o sprzęcie urządzeń w przedsiębiorstwie. Zobacz [wprowadzenie do spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md).  

-   **Spis oprogramowania**: Zbiera i raportuje informacje o plikach, które są przechowywane na komputerach klienckich w organizacji. Zobacz [wprowadzenie do spisu oprogramowania w programie System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-software-inventory.md).  

-   **Analiza zasobów**: Udostępnia narzędzia do zbierania danych spisu oraz monitorowania użycia licencji oprogramowania w przedsiębiorstwie. Zobacz [wprowadzenie do analizy zasobów w programie System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

**Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune**  

 Można użyć programu Configuration Manager do zarządzania z systemem iOS, Android (w tym Samsung KNOX Standard), Windows Phone i urządzeń z systemem Windows przy użyciu usługi Microsoft Intune za pośrednictwem Internetu.

 Mimo że używasz usługi Intune, zadania zarządzania wykonuje się za pomocą usługi roli lokacji punktu połączenia systemu dostępne za pośrednictwem konsoli programu Configuration Manager. Zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

 **Lokalne zarządzanie urządzeniami przenośnymi**  

 Rejestruje i zarządza komputerami i urządzeniami przenośnymi za pomocą funkcji zarządzania i infrastruktury programu Configuration Manager lokalnymi wbudowanych w platformy urządzeń (zamiast polegania na zainstalowanym osobno kliencie programu Configuration Manager). Obecnie obsługuje zarządzanie urządzeniami z systemem Windows 10 Enterprise i Windows 10 Mobile. Zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Wdrożenie systemu operacyjnego**  

 Obejmuje narzędzia do tworzenia obrazów systemu operacyjnego: Można następnie użyć tych obrazów do wdrażania systemów operacyjnych na komputerach, za pomocą funkcji PXE rozruch lub nośnika rozruchowego, takich jak zestaw dysków CD, DVD lub USB flash. Należy pamiętać, że dotyczy to komputerów, które są zarządzane przez program Configuration Manager, a także komputerach niezarządzanych. Zobacz [wprowadzenie do wdrażania systemu operacyjnego w programie System Center Configuration Manager](../../../osd/understand/introduction-to-operating-system-deployment.md).  

 **Zarządzanie energią**  

 Obejmuje zestaw narzędzi i zasobów ułatwiających zarządzanie poborem mocy przez klientów w przedsiębiorstwie i monitorowanie go. Zobacz [wprowadzenie do zarządzania energią w programie System Center Configuration Manager](../../../core/clients/manage/power/introduction-to-power-management.md).  

 **Zapytania**  

 Obejmuje narzędzia do pobierania informacji o zasobach w hierarchii oraz danych o zapasach i komunikatów o stanie. Następnie można te informacje do raportowania, lub do definiowania kolekcji urządzeń lub użytkowników do wdrażania i konfigurowania ustawień oprogramowania. Zobacz [wprowadzenie do zapytań w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md).  

 **Profile połączenia zdalnego**  

 Udostępnia zestaw narzędzi i zasobów, które ułatwiają tworzenie, wdrażanie i monitorowanie ustawień połączeń zdalnych na urządzeniach w organizacji. Wdrażając te ustawienia, można zminimalizować ilość pracy wymaganej przez użytkowników do łączenia się z ich komputerami w sieci firmowej. Zobacz [Praca z profilami połączenia zdalnego w programie System Center Configuration Manager](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

 **Elementy konfiguracji danych i profilów użytkownika**  

 Elementy danych użytkownika i profilów konfiguracji w programie Configuration Manager zawiera ustawienia umożliwiające zarządzanie przekierowaniem folderu, plikami trybu offline i profilami mobilnymi na komputerach z systemem Windows 8 i nowszym w przypadku użytkowników w hierarchii. Zobacz [Praca z elementami danych użytkownika i profilów konfiguracji w programie System Center Configuration Manager](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

 **Zdalne sterowanie**  

 Udostępnia narzędzia do zdalnego zarządzania klientami z konsoli programu Configuration Manager. Zobacz [wprowadzenie do zdalnego sterowania w programie System Center Configuration Manager](../../../core/clients/manage/remote-control/introduction-to-remote-control.md).  

 **Raportowanie**  

 Udostępnia zestaw narzędzi i zasobów, które ułatwiają korzystanie z zaawansowanych możliwości raportowania programu SQL Server Reporting Services z konsoli programu Configuration Manager. Zobacz [wprowadzenie do raportowania w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md).  

 **Pomiar użytkowania oprogramowania**  

 Udostępnia narzędzia do monitorowania i zbierania danych o użytkowaniu oprogramowania z klientów programu Configuration Manager. Zobacz [Monitorowanie użycia aplikacji za pomocą funkcji pomiaru użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

 **Aktualizacje oprogramowania**  

 Obejmuje zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie aktualizacji oprogramowania w przedsiębiorstwie. Zobacz [wprowadzenie do oprogramowania aktualizacji w programie System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).  
