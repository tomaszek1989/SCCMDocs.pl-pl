---
title: Endpoint Protection | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak zarządzać zasadami ochrony przed złośliwym oprogramowaniem i zabezpieczeń zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager."
ms.custom: na
ms.date: 02/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
caps.latest.revision: 11
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 3c31271f3e3ae7aa45da03b3d75fd78242330646
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection"></a>Program Endpoint Protection

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Endpoint Protection w programie System Center Configuration Manager umożliwia zarządzanie zasadami ochrony przed złośliwym oprogramowaniem i zabezpieczeń zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager.  

> [!IMPORTANT]  
>  Użytkownik musi posiadać uprawnienia do programu Endpoint Protection można użyć do zarządzania klientami w hierarchii programu Configuration Manager.  

 Korzystając z programu Endpoint Protection z programu Configuration Manager, masz następujące korzyści:  

-   Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem, ustawienia zapory systemu Windows i zarządzanie zaawansowane zagrożenia ochrony programu Windows Defender do wybranych grup komputerów  
-   Użyj Menedżera konfiguracji aktualizacji oprogramowania w celu pobrania najnowszych plików definicji ochrony przed złośliwym oprogramowaniem w celu zapewnienia aktualności komputerów klienckich  
-   Wysyłanie powiadomień e-mail, korzystanie z monitorowania w konsoli i wyświetlanie raportów w celu informowania użytkowników administracyjnych na bieżąco o wykryciu złośliwego oprogramowania na komputerach klienckich  

Począwszy od systemu Windows 10 i Windows Server 2016 komputery, usługi Windows Defender jest już zainstalowana. Dla tych systemów operacyjnych klienta zarządzania dla usługi Windows Defender jest instalowane podczas instalowania klienta programu Configuration Manager. Windows 8.1 i starszych komputerach klient ochrony punktu końcowego jest instalowany z klienta programu Configuration Manager. Usługa Windows Defender i klienta programu Endpoint Protection mają następujące możliwości:  

-   wykrywanie złośliwego oprogramowania i programów szpiegujących oraz wykonywanie działań korygujących,  
-   wykrywanie programów typu rootkit i wykonywanie działań korygujących,  
-   ocena krytycznych luk w zabezpieczeniach i automatyczne aktualizowanie definicji oraz aparatu,  
-   wykrywanie luk w zabezpieczeniach sieci przy użyciu systemu Network Inspection System.  
-   Integracja z usługą ochrony chmury, aby zgłosić złośliwego oprogramowania firmy Microsoft. Po dołączeniu do tej usługi klient programu Endpoint Protection lub usługa Windows Defender może pobierać najnowsze definicje z Centrum ds. ochrony przed złośliwym oprogramowaniem w przypadku wykrycia niezidentyfikowanego złośliwego oprogramowania na komputerze.  

> [!NOTE]  
>  Klient programu Endpoint Protection można zainstalować na serwerze z uruchomioną funkcją Hyper-V i maszynach wirtualnych gościa z obsługiwanych systemów operacyjnych. Aby uniknąć nadmiernego wykorzystania Procesora, Endpoint Protection akcji ma wbudowane losowe opóźnienie, tak aby usługi ochrony nie są uruchamiane jednocześnie.  

 Ponadto program Endpoint Protection w programie Configuration Manager umożliwia do zarządzania ustawieniami Zapory systemu Windows w konsoli programu Configuration Manager.  

 [Przykładowy scenariusz: Za pomocą programu System Center Endpoint Protection w celu ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](scenarios-endpoint-protection.md) Endpoint Protection i zapory systemu Windows.  


## <a name="managing-malware-with-endpoint-protection"></a>Zarządzanie ochroną przed złośliwym kodem przy użyciu programu Endpoint Protection  
 Endpoint Protection w programie Configuration Manager służy do tworzenia zasad ochrony przed złośliwym oprogramowaniem, które zawierają ustawienia konfiguracji klienta Endpoint Protection. Można wdrożyć na komputerach klienckich tych zasad ochrony przed złośliwym oprogramowaniem i Monitoruj je w **stanu ochrony punktu końcowego** węzeł w węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego, lub za pomocą raportów programu Configuration Manager.  

 Informacje dodatkowe:  

-   [Sposób tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md) — tworzenie, wdrażanie i monitorować zasady ochrony przed złośliwym oprogramowaniem z listą ustawień, które można skonfigurować  

-   [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](monitor-endpoint-protection.md) -monitorowania raporty aktywności, komputery klienckie zainfekowane i inne.  

-   [Jak zarządzać zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-firewall.md) -korygowania złośliwego oprogramowania na komputerach klienckich  


## <a name="managing-windows-firewall-with-endpoint-protection"></a>Zarządzanie Zaporą systemu Windows przy użyciu programu Endpoint Protection  
 Endpoint Protection w programie Configuration Manager umożliwia zarządzanie podstawowe Zapora systemu Windows na komputerach klienckich. Dla każdego profilu sieciowego można skonfigurować następujące ustawienia:  

-   Włącz lub wyłącz Zaporę systemu Windows.  

-   Blokuj połączenia przychodzące łącznie z programami znajdującymi się na liście dozwolonych programów.  

-   Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program.  

> [!NOTE]  
>  Program Endpoint Protection obsługuje tylko zarządzanie Zaporą systemu Windows.  


 Aby uzyskać więcej informacji dotyczących sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection, zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](create-windows-firewall-policies.md).  


## <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender zaawansowane ochroną

Począwszy od wersji 1606 programu Configuration Manager (bieżącej gałęzi), program Endpoint Protection może ułatwić zarządzanie i monitorowanie systemu Windows Defender zaawansowane zagrożenia ochrony (ATP). Program Windows Defender ATP jest nową usługę, która pomoże przedsiębiorstwa do wykrywania, badanie i reagowania na zaawansowane ataki w ich sieciach. Zobacz [zaawansowane ochroną programu Windows Defender](windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Przepływ pracy w programie Endpoint Protection  
 Użyj następujących diagram ułatwiające zrozumienie sposobu działania przepływu pracy, aby zaimplementować Endpoint Protection w hierarchii programu Configuration Manager.  

 ![Przepływ pracy w programie Endpoint Protection](../media/Endpoint-Protection-Workflow.gif)  

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Klient programu Endpoint Protection dla komputerów Mac i serwerów z systemem Linux  
 System Center Endpoint Protection zawiera klienta Endpoint Protection dla komputerów Mac i Linux. Tacy klienci nie są dostarczane z programem Configuration Manager; Zamiast tego należy pobrać następujące produkty z [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

-   Program System Center 2012 Endpoint Protection dla komputerów Mac  

-   Program System Center 2012 Endpoint Protection dla systemu Linux  


> [!IMPORTANT]  
>  Użytkownik musi być klientem licencjonowania zbiorowego firmy Microsoft, aby móc pobrać pliki instalacyjne programu Endpoint Protection dla systemu Linux i komputerów Mac.  

 Tymi produktami nie można zarządzać za pomocą konsoli programu Configuration Manager. Jednak z plikami instalacyjnymi jest dostarczany pakiet administracyjny programu System Center Operations Manager, który umożliwia zarządzanie klientem dla systemu Linux przy użyciu programu Operations Manager.  

### <a name="how-to-get-the-endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Jak uzyskać klienta ochrony punktu końcowego dla komputerów Mac i serwerów z systemem Linux

Wykonaj następujące kroki, aby pobrać plik obrazu zawierającego oprogramowanie klienta programu Endpoint Protection i dokumentacji dla komputerów Mac i serwerów z systemem Linux.
1. Logowanie do [Centrum usługi licencjonowania zbiorowego firmy Microsoft](https://www.microsoft.com/licensing/servicecenter/default.aspx).
2. Wybierz **pliki do pobrania i klucze** u góry witryny sieci Web.
3. Filtr na produktu **programu System Center Endpoint Protection (bieżącej gałęzi)**.
4. Kliknij łącze, aby **Pobierz**
5. Kliknij przycisk **Kontynuuj**. Powinny być widoczne kilka plików, w tym o nazwie: **System Center Endpoint Protection (bieżącej gałęzi — wersja 1606) dla systemu operacyjnego Linux i wersje językowe systemu operacyjnego dla komputerów Macintosh 32/64 bit 1507 MB ISO**.
6. Kliknij ikonę strzałki, aby pobrać plik. Nazwa pliku jest **SW_DVD5_Sys_Ctr_Endpnt_Prtctn_1606_MultiLang_EptProt_Lin_Mac_MLF_X21 30777. ISO**.

 Więcej informacji o sposobie instalowania i zarządzania klientami programu Endpoint Protection dla komputerów z systemem Linux i komputerów Mac zawiera dokumentacja dostarczona z tymi produktami znajdująca się w folderze **Dokumentacja** .

