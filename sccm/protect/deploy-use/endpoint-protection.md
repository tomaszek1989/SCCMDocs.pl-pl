---
title: Program Endpoint Protection
titleSuffix: Configuration Manager
description: Dowiedz się, jak zarządzać zasadami ochrony przed złośliwym kodem i zabezpieczeniami zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager.
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2da4b91411822b6274da3e165ff3e43e8752dc45
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="endpoint-protection"></a>Program Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Program Endpoint Protection zarządza zasadami ochrony przed złośliwym kodem i zabezpieczeniami zapory systemu Windows dla komputerów klienckich w hierarchii programu Configuration Manager.  

> [!IMPORTANT]  
>  Możesz muszą mieć licencję na potrzeby zarządzania klientami w hierarchii programu Configuration Manager przez program Endpoint Protection.  

 Korzystając z programu Endpoint Protection z programem Configuration Manager, masz następujące korzyści:  

-   Konfigurowanie zasad ochrony przed złośliwym kodem, ustawienia zapory systemu Windows i zarządzanie nimi Windows Defender Advanced Threat Protection do wybranych grup komputerów  
-   Użyj Menedżera konfiguracji aktualizacji oprogramowania do pobrania najnowszych plików definicji ochrony przed złośliwym kodem w celu zapewnienia aktualności komputerów klienckich  
-   Wysyłanie powiadomień e-mail, użyj monitorowania w konsoli i wyświetlanie raportów. Te akcje poinformować użytkowników administracyjnych, po wykryciu złośliwego oprogramowania na komputerach klienckich.  

Począwszy od systemu Windows 10 i Windows Server 2016 komputery, usługi Windows Defender jest już zainstalowana. Dla tych systemów operacyjnych klienta zarządzania dla usługi Windows Defender jest instalowana podczas instalacji klienta programu Configuration Manager. Windows 8.1 i starszych komputerów klient programu Endpoint Protection jest instalowany z klienta programu Configuration Manager. Usługa Windows Defender i klienta programu Endpoint Protection mają następujące możliwości:  

-   wykrywanie złośliwego oprogramowania i programów szpiegujących oraz wykonywanie działań korygujących,  
-   wykrywanie programów typu rootkit i wykonywanie działań korygujących,  
-   ocena krytycznych luk w zabezpieczeniach i automatyczne aktualizowanie definicji oraz aparatu,  
-   wykrywanie luk w zabezpieczeniach sieci przy użyciu systemu Network Inspection System.  
-   Integracja z usługą ochrony chmury w celu zgłaszania złośliwego oprogramowania do firmy Microsoft. Po dołączeniu do tej usługi klienta programu Endpoint Protection lub usługa Windows Defender pobiera najnowsze definicje z Centrum ochrony przed złośliwym oprogramowaniem w przypadku wykrycia niezidentyfikowanego złośliwego oprogramowania na komputerze.  

> [!NOTE]  
>  Klient programu Endpoint Protection można zainstalować na serwerze z uruchomioną funkcją Hyper-V oraz na maszynach wirtualnych gościa z obsługiwanymi systemami operacyjnymi. Aby uniknąć nadmiernego użycia procesora CPU, akcje programu Endpoint Protection ma wbudowane losowe opóźnienie, tak aby usługi ochrony nie były uruchamiane jednocześnie.  

 Ponadto należy zarządzać ustawienia zapory systemu Windows z programem Endpoint Protection w konsoli programu Configuration Manager.  

 [Przykładowy scenariusz: Używanie programu System Center Endpoint Protection do ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](scenarios-endpoint-protection.md) programu Endpoint Protection i Zaporą systemu Windows.  


## <a name="managing-malware-with-endpoint-protection"></a>Zarządzanie ochroną przed złośliwym kodem przy użyciu programu Endpoint Protection  
 Program Endpoint Protection w programie Configuration Manager umożliwia tworzenie zasad ochrony przed złośliwym oprogramowaniem, które zawierają ustawienia konfiguracji klienta programu Endpoint Protection. Te zasady ochrony przed złośliwym kodem można wdrożyć na komputerach klienckich. Następnie monitorowania zgodności w **stan programu Endpoint Protection** węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego. Również Użyj raportów programu Endpoint Protection w **raportowania** węzła.  

 Informacje dodatkowe:  

-   [Jak utworzyć i wdrożyć zasady ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md) — tworzenie, wdrażanie i monitorowanie zasad ochrony przed złośliwym oprogramowaniem z listą ustawień, które można skonfigurować  

-   [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](monitor-endpoint-protection.md) — monitorowanie raportów działań, zainfekowanych komputerów klienckich i innych.  

-   [Jak zarządzać zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-firewall.md) — korygowanie złośliwego oprogramowania znalezionego na komputerach klienckich  


## <a name="managing-windows-firewall-with-endpoint-protection"></a>Zarządzanie Zaporą systemu Windows przy użyciu programu Endpoint Protection  
 Program Endpoint Protection w programie Configuration Manager udostępnia podstawowe możliwości zarządzania Zaporą systemu Windows na komputerach klienckich. Dla każdego profilu sieciowego można skonfigurować następujące ustawienia:  

-   Włącz lub wyłącz Zaporę systemu Windows.  

-   Blokuj połączenia przychodzące łącznie z programami znajdującymi się na liście dozwolonych programów.  

-   Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program.  

> [!NOTE]  
>  Program Endpoint Protection obsługuje tylko zarządzanie Zaporą systemu Windows.  


 Aby uzyskać więcej informacji, zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection](create-windows-firewall-policies.md).  


## <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender Advanced Threat Protection

Program Endpoint Protection zarządza i monitoruje Windows Defender Advanced Threat Protection (ATP). Usługa Windows Defender ATP ułatwia przedsiębiorstwom wykrywania, badanie i odpowiadać na zaawansowanych ataków w sieci firmowej. Aby uzyskać więcej informacji, zobacz [Windows Defender Advanced Threat Protection](windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Przepływ pracy w programie Endpoint Protection  
 Użyj poniższym diagramie, aby ułatwić zrozumienie przepływu pracy do implementacji programu Endpoint Protection w hierarchii programu Configuration Manager.  

 ![Przepływ pracy w programie Endpoint Protection](../media/Endpoint-Protection-Workflow.gif)  

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Klient programu Endpoint Protection dla komputerów Mac i serwerów z systemem Linux  
 System Center Endpoint Protection zawiera klienta programu Endpoint Protection dla systemu Linux i komputerów Mac. Tacy klienci nie są dostarczane z programem Configuration Manager; Zamiast tego należy pobrać następujące produkty z [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

-   System Center Endpoint Protection dla komputerów Mac  

-   System Center Endpoint Protection dla systemu Linux  


> [!IMPORTANT]  
>  Użytkownik musi być klientem licencjonowania zbiorowego firmy Microsoft, aby móc pobrać pliki instalacyjne programu Endpoint Protection dla systemu Linux i komputerów Mac.  

 Tymi produktami nie można zarządzać za pomocą konsoli programu Configuration Manager. Jednak z plikami instalacyjnymi jest dostarczany pakiet administracyjny programu System Center Operations Manager, który umożliwia zarządzanie klientem dla systemu Linux przy użyciu programu Operations Manager.  

### <a name="how-to-get-the-endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Jak uzyskać klienta programu Endpoint Protection dla komputerów Mac i serwerów z systemem Linux

Wykonaj następujące kroki, aby pobrać plik obrazu zawierającego oprogramowanie klienta programu Endpoint Protection i dokumentację dla komputerów Mac i serwerów z systemem Linux.
1. Zaloguj się do [Microsoft wolumin licencjonowania Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).
2. Wybierz **pliki do pobrania i klucze** kartę w górnej części strony.
3. Filtr produktu **programu System Center Endpoint Protection (wersji current branch)**.
4. Kliknij łącze, aby **Pobierz**
5. Kliknij przycisk **Kontynuuj**. Powinny pojawić kilka plików, w tym o nazwie: **System Center Endpoint Protection (bieżącej gałęzi — wersja 1606) dla systemu operacyjnego Linux i wielu języków systemu operacyjnego dla komputerów Macintosh 32/64-bitowy 1878 MB ISO**.
6. Aby pobrać plik, kliknij ikonę strzałki. Nazwa pliku jest **SW_DVD5_Sys_Ctr_Endpnt_Prtctn_1606_MultiLang_-3_EptProt_Lin_Mac_MLF_X21-67050. ISO**.

Aktualizacja 2018 stycznia (X21 67050) obejmuje następujące wersje:

- System Center Endpoint Protection dla komputerów Mac 4.5.32.0 (obsługę 10.13 Sierra wysokiej macOS)
- System Center Endpoint Protection dla systemu Linux 4.5.20.0 

 Aby uzyskać więcej informacji o sposobie instalowania i zarządzania klientami programu Endpoint Protection dla komputerów z systemami Linux i komputerów Mac należy użyć zawiera dokumentacja dostarczona z tymi produktami. Niniejsza dokumentacja produktu jest w **dokumentacji** folderu. Plik ISO.
