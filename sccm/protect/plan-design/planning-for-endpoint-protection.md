---
title: Planowanie programu Endpoint Protection | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: "16"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 6c4273dae99ec8db2cf827f463b973e876d0d35b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>Planowanie programu Endpoint Protection w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Program Endpoint Protection w programie System Center Configuration Manager umożliwia zarządzanie zasadami ochrony przed złośliwym kodem i zabezpieczeniami zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager.  

> [!IMPORTANT]  
>  Możesz muszą mieć licencję na potrzeby zarządzania klientami w hierarchii programu Configuration Manager przez program Endpoint Protection.  

Korzystając z programu Endpoint Protection z programem Configuration Manager, masz następujące korzyści:  

-   Konfigurowanie zasad ochrony przed złośliwym kodem, ustawienia zapory systemu Windows i zarządzanie nimi Windows Defender Advanced Threat Protection do wybranych grup komputerów  

-   Użyj Menedżera konfiguracji aktualizacji oprogramowania do pobrania najnowszych plików definicji ochrony przed złośliwym kodem w celu zapewnienia aktualności komputerów klienckich  

-   Wysyłanie powiadomień e-mail, korzystanie z monitorowania w konsoli i wyświetlanie raportów w celu informowania użytkowników administracyjnych na bieżąco o wykryciu złośliwego oprogramowania na komputerach klienckich  

Komputery z systemem Windows 10 nie wymagają żadnych dodatkowych klienta dla zarządzania ochroną punktu końcowego. Windows 8.1 i starszych komputerach program Endpoint Protection instaluje własnego klienta oprócz klienta programu Configuration Manager. Klient programu Endpoint Protection zapewnia następujące możliwości:  

-   wykrywanie złośliwego oprogramowania i programów szpiegujących oraz wykonywanie działań korygujących,  

-   wykrywanie programów typu rootkit i wykonywanie działań korygujących,  

-   ocena krytycznych luk w zabezpieczeniach i automatyczne aktualizowanie definicji oraz aparatu,  

-   wykrywanie luk w zabezpieczeniach sieci przy użyciu systemu Network Inspection System.  

-   Integracja z usługą ochrony chmury w celu zgłaszania złośliwego oprogramowania do firmy Microsoft. Po dołączeniu do tej usługi, usługa Windows Defender lub klienta programu Endpoint Protection można pobrać najnowsze definicje z Centrum ochrony przed złośliwym oprogramowaniem w przypadku wykrycia niezidentyfikowanego złośliwego oprogramowania na komputerze.  

> [!NOTE]  
>  Klient programu Endpoint Protection można zainstalować na serwerze z uruchomioną funkcją Hyper-V oraz na maszynach wirtualnych gościa z obsługiwanymi systemami operacyjnymi. Aby uniknąć nadmiernego użycia procesora CPU, akcje programu Endpoint Protection mieć wbudowanego, losowego opóźnienia, tak aby usługi nie były uruchamiane jednocześnie.  

  Ponadto program Endpoint Protection w programie Configuration Manager umożliwia zarządzanie ustawieniami Zapory systemu Windows w konsoli programu Configuration Manager.  

 [Przykładowy scenariusz: Używanie programu System Center Endpoint Protection do ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](../deploy-use/scenarios-endpoint-protection.md) pokazuje, jak może skonfigurować i zarządzać programem Endpoint Protection i Zaporą systemu Windows.  

## <a name="managing-malware-with-endpoint-protection"></a>Zarządzanie ochroną przed złośliwym kodem przy użyciu programu Endpoint Protection  

Program Endpoint Protection w programie Configuration Manager umożliwia tworzenie zasad ochrony przed złośliwym oprogramowaniem, które zawierają ustawienia konfiguracji klienta programu Endpoint Protection. Następnie można wdrożyć te zasady ochrony przed złośliwym kodem na komputerach klienckich i monitorować je w **stan programu Endpoint Protection** w węźle **monitorowanie** obszaru roboczego, lub za pomocą raportów programu Configuration Manager.  

 Informacje dodatkowe:  

-   [Tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](../deploy-use/endpoint-antimalware-policies.md) — tworzenie, wdrażanie i monitorowanie zasad ochrony przed złośliwym oprogramowaniem z listą ustawień, które można skonfigurować  

-   [Monitorowanie programu Endpoint Protection w programie System Center Configuration Manager](../deploy-use/monitor-endpoint-protection.md) — monitorowanie raportów działań, zainfekowanych komputerów klienckich i innych.   

-   [Zarządzanie zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia programu Endpoint Protection w programie System Center Configuration Manager](../deploy-use/endpoint-antimalware-firewall.md) — można zmienić priorytet zasad [ochrony przed złośliwym kodem](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) lub [zapory](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [korygowania złośliwego oprogramowania znalezionego na komputerach klienckich](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware)i innych zadań

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Zarządzanie Zaporą systemu Windows przy użyciu programu Endpoint Protection  
 Program Endpoint Protection w programie Configuration Manager udostępnia podstawowe możliwości zarządzania Zaporą systemu Windows na komputerach klienckich. Dla każdego profilu sieciowego można skonfigurować następujące ustawienia:  

-   Włącz lub wyłącz Zaporę systemu Windows.  

-   Blokuj połączenia przychodzące łącznie z programami znajdującymi się na liście dozwolonych programów.  

-   Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program.  

> [!NOTE]  
>  Program Endpoint Protection obsługuje tylko zarządzanie Zaporą systemu Windows.  

  Aby uzyskać więcej informacji o sposobie tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection, zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](../deploy-use/create-windows-firewall-policies.md).  

## <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender Advanced Threat Protection

Począwszy od wersji 1606 programu Configuration Manager (wersji current branch), program Endpoint Protection ułatwia zarządzanie i monitorowanie Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP to nowa usługa, która pomaga firmom wykrywania, badanie i odpowiadać na zaawansowanych ataków w swoich sieciach. Zobacz [usługa Windows Defender Advanced Threat Protection](../deploy-use/windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Przepływ pracy w programie Endpoint Protection  
 Użyj poniższym diagramie, aby ułatwić zrozumienie przepływu pracy do implementacji programu Endpoint Protection w hierarchii programu Configuration Manager.  

 ![Przepływ pracy w programie Endpoint Protection](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Klient programu Endpoint Protection dla komputerów Mac i serwerów z systemem Linux  
 Program System Center zawiera klienta programu Endpoint Protection dla systemu Linux i komputerów Mac. Tacy klienci nie są dostarczane z programem Configuration Manager; Zamiast tego należy pobrać następujące produkty z [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

> [!IMPORTANT]  
>  Użytkownik musi być klientem licencjonowania zbiorowego firmy Microsoft, aby móc pobrać pliki instalacyjne programu Endpoint Protection dla systemu Linux i komputerów Mac.  

 Tymi produktami nie można zarządzać za pomocą konsoli programu Configuration Manager. Jednak z plikami instalacyjnymi jest dostarczany pakiet administracyjny programu System Center Operations Manager, który umożliwia zarządzanie klientem dla systemu Linux przy użyciu programu Operations Manager.  

 Więcej informacji o sposobie instalowania i zarządzania klientami programu Endpoint Protection dla komputerów z systemem Linux i komputerów Mac zawiera dokumentacja dostarczona z tymi produktami znajdująca się w folderze **Dokumentacja** .

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>Najlepsze rozwiązania dotyczące programu Endpoint Protection w programie Configuration Manager  
 Należy stosować następujące najlepsze rozwiązania dotyczące programu Endpoint Protection w programie System Center 2012 Configuration Manager.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection  
 Podczas konfigurowania ustawień klienta programu Endpoint Protection nie używać domyślnych ustawień klienta, ponieważ stosują one ustawienia do wszystkich komputerów w hierarchii. Zamiast tego należy skonfigurować niestandardowe ustawienia klienta i przypisać te ustawienia do kolekcji komputerów w hierarchii.  

 Podczas konfigurowania niestandardowych ustawień klienta można wykonać następujące czynności:  

-   Dostosowywanie ustawień ochrony przed złośliwym kodem oraz ustawień zabezpieczeń dla różnych części organizacji.  
-   Testowanie skutków uruchomienia programu Endpoint Protection dla niewielkiej grupie komputerów przed wdrożeniem w całej hierarchii.  
-   Dodawanie większej liczby klientów do kolekcji w celu podziału wdrożenia klienta programu Endpoint Protection.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>Dystrybuowanie aktualizacji definicji przy użyciu aktualizacji oprogramowania  
 Jeśli używane są aktualizacje oprogramowania Configuration Manager dystrybucję aktualizacji definicji, należy rozważyć umieszczenie aktualizacji definicji w pakiecie, który nie zawiera innych aktualizacji oprogramowania. Umożliwia to zachowanie mniejszego rozmiaru pakietu aktualizacji definicji, dzięki czemu replikacja punktów dystrybucji może przebiegać szybciej.
