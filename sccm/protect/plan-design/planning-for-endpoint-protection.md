---
title: "Planowanie ochrony punktu końcowego | Dokumentacja firmy Microsoft"
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: 16
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 6c4273dae99ec8db2cf827f463b973e876d0d35b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>Planowanie programu Endpoint Protection w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Endpoint Protection w programie System Center Configuration Manager umożliwia zarządzanie zasadami ochrony przed złośliwym oprogramowaniem i zabezpieczeń zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager.  

> [!IMPORTANT]  
>  Użytkownik musi posiadać uprawnienia do programu Endpoint Protection można użyć do zarządzania klientami w hierarchii programu Configuration Manager.  

Korzystając z programu Endpoint Protection z programu Configuration Manager, masz następujące korzyści:  

-   Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem, ustawienia zapory systemu Windows i zarządzanie zaawansowane zagrożenia ochrony programu Windows Defender do wybranych grup komputerów  

-   Użyj Menedżera konfiguracji aktualizacji oprogramowania w celu pobrania najnowszych plików definicji ochrony przed złośliwym oprogramowaniem w celu zapewnienia aktualności komputerów klienckich  

-   Wysyłanie powiadomień e-mail, korzystanie z monitorowania w konsoli i wyświetlanie raportów w celu informowania użytkowników administracyjnych na bieżąco o wykryciu złośliwego oprogramowania na komputerach klienckich  

Komputery z systemem Windows 10 nie wymagają żadnych dodatkowych klienta do zarządzania ochrony punktu końcowego. Windows 8.1 i starszych komputerów Endpoint Protection instaluje klienta oprócz klienta programu Configuration Manager. Klient programu Endpoint Protection zapewnia następujące możliwości:  

-   wykrywanie złośliwego oprogramowania i programów szpiegujących oraz wykonywanie działań korygujących,  

-   wykrywanie programów typu rootkit i wykonywanie działań korygujących,  

-   ocena krytycznych luk w zabezpieczeniach i automatyczne aktualizowanie definicji oraz aparatu,  

-   wykrywanie luk w zabezpieczeniach sieci przy użyciu systemu Network Inspection System.  

-   Integracja z usługą ochrony chmury, aby zgłosić złośliwego oprogramowania firmy Microsoft. Po dołączeniu tej usługi Windows Defender lub klienta programu Endpoint Protection można pobrać najnowszych definicji z Centrum ochrony przed złośliwym oprogramowaniem wykryciu niezidentyfikowane złośliwego oprogramowania na komputerze.  

> [!NOTE]  
>  Klient programu Endpoint Protection można zainstalować na serwerze z uruchomioną funkcją Hyper-V i maszynach wirtualnych gościa z obsługiwanych systemów operacyjnych. Aby uniknąć nadmiernego wykorzystania Procesora, akcji Endpoint Protection ma wbudowane, losowego opóźnienia, aby usługi nie są uruchamiane jednocześnie.  

  Ponadto program Endpoint Protection w programie Configuration Manager umożliwia do zarządzania ustawieniami Zapory systemu Windows w konsoli programu Configuration Manager.  

 [Przykładowy scenariusz: Za pomocą programu System Center Endpoint Protection w celu ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](../deploy-use/scenarios-endpoint-protection.md) pokazuje, jak może skonfigurować i zarządzać Endpoint Protection i zapory systemu Windows.  

## <a name="managing-malware-with-endpoint-protection"></a>Zarządzanie ochroną przed złośliwym kodem przy użyciu programu Endpoint Protection  

Endpoint Protection w programie Configuration Manager służy do tworzenia zasad ochrony przed złośliwym oprogramowaniem, które zawierają ustawienia konfiguracji klienta Endpoint Protection. Można wdrożyć na komputerach klienckich tych zasad ochrony przed złośliwym oprogramowaniem i Monitoruj je w **stanu ochrony punktu końcowego** w węźle **monitorowanie** obszaru roboczego, lub za pomocą raportów programu Configuration Manager.  

 Informacje dodatkowe:  

-   [Tworzenie i wdrażanie zasad ochrony przed złośliwym oprogramowaniem Endpoint Protection w programie System Center Configuration Manager](../deploy-use/endpoint-antimalware-policies.md) — tworzenie, wdrażanie i monitorować zasady ochrony przed złośliwym oprogramowaniem z listą ustawień, które można skonfigurować  

-   [Monitorować program Endpoint Protection w programie System Center Configuration Manager](../deploy-use/monitor-endpoint-protection.md) -monitorowania raporty aktywności, komputery klienckie zainfekowane i inne.   

-   [Zarządzanie zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia Endpoint Protection w programie System Center Configuration Manager](../deploy-use/endpoint-antimalware-firewall.md) -można zmienić priorytet zasady [ochrony przed złośliwym oprogramowaniem](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) lub [zapory](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [korygowania złośliwego oprogramowania na komputerach klienckich](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware)i innych zadań

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Zarządzanie Zaporą systemu Windows przy użyciu programu Endpoint Protection  
 Endpoint Protection w programie Configuration Manager udostępnia podstawowe zarządzania zapory systemu Windows na komputerach klienckich. Dla każdego profilu sieciowego można skonfigurować następujące ustawienia:  

-   Włącz lub wyłącz Zaporę systemu Windows.  

-   Blokuj połączenia przychodzące łącznie z programami znajdującymi się na liście dozwolonych programów.  

-   Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program.  

> [!NOTE]  
>  Program Endpoint Protection obsługuje tylko zarządzanie Zaporą systemu Windows.  

  Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection, zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](../deploy-use/create-windows-firewall-policies.md).  

## <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender zaawansowane ochroną

Począwszy od wersji 1606 programu Configuration Manager (bieżącej gałęzi), program Endpoint Protection może ułatwić zarządzanie i monitorowanie systemu Windows Defender zaawansowane zagrożenia ochrony (ATP). Program Windows Defender ATP jest nową usługę, która pomoże przedsiębiorstwa do wykrywania, badanie i reagowania na zaawansowane ataki w ich sieciach. Zobacz [zaawansowane ochroną programu Windows Defender](../deploy-use/windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Przepływ pracy w programie Endpoint Protection  
 Użyj następujących diagram ułatwiające zrozumienie sposobu działania przepływu pracy, aby zaimplementować Endpoint Protection w hierarchii programu Configuration Manager.  

 ![Przepływ pracy w programie Endpoint Protection](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Klient programu Endpoint Protection dla komputerów Mac i serwerów z systemem Linux  
 System Center obejmuje klienta Endpoint Protection dla komputerów Mac i Linux. Tacy klienci nie są dostarczane z programem Configuration Manager; Zamiast tego należy pobrać następujące produkty z [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

> [!IMPORTANT]  
>  Użytkownik musi być klientem licencjonowania zbiorowego firmy Microsoft, aby móc pobrać pliki instalacyjne programu Endpoint Protection dla systemu Linux i komputerów Mac.  

 Tymi produktami nie można zarządzać za pomocą konsoli programu Configuration Manager. Jednak z plikami instalacyjnymi jest dostarczany pakiet administracyjny programu System Center Operations Manager, który umożliwia zarządzanie klientem dla systemu Linux przy użyciu programu Operations Manager.  

 Więcej informacji o sposobie instalowania i zarządzania klientami programu Endpoint Protection dla komputerów z systemem Linux i komputerów Mac zawiera dokumentacja dostarczona z tymi produktami znajdująca się w folderze **Dokumentacja** .

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>Najlepsze rozwiązania dotyczące programu Endpoint Protection w programie Configuration Manager  
 Należy stosować następujące najlepsze rozwiązania dotyczące programu Endpoint Protection w programie System Center 2012 Configuration Manager.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection  
 Podczas konfigurowania ustawień klienta dla ochrony punktu końcowego nie używać domyślnych ustawień klienta, ponieważ mają one zastosowanie ustawień do wszystkich komputerów w hierarchii. Zamiast tego należy skonfigurować niestandardowe ustawienia klienta i przypisać te ustawienia do kolekcji komputerów w hierarchii.  

 Podczas konfigurowania niestandardowych ustawień klienta można wykonać następujące czynności:  

-   Dostosowywanie ustawień ochrony przed złośliwym kodem oraz ustawień zabezpieczeń dla różnych części organizacji.  
-   Przetestuj efekty programu Endpoint Protection na małe grupy komputerów przed wdrożeniem do całej hierarchii.  
-   Dodaj więcej klientów do kolekcji czasem faza wdrożenia klienta programu Endpoint Protection.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>Dystrybuowanie aktualizacji definicji przy użyciu aktualizacji oprogramowania  
 Jeśli używasz aktualizacje oprogramowania Configuration Manager dystrybucję aktualizacji definicji, należy rozważyć umieszczenie aktualizacji definicji pakietu, który nie zawiera inne aktualizacje oprogramowania. Umożliwia to zachowanie mniejszego rozmiaru pakietu aktualizacji definicji, dzięki czemu replikacja punktów dystrybucji może przebiegać szybciej.

