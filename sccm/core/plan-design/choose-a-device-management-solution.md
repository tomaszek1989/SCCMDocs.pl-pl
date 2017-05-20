---
title: "Wybierz rozwiązanie do zarządzania urządzeniami — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat rozwiązania, które oferuje System Center Configuration Manager do zarządzania komputerami, serwerów i urządzeń."
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: 14
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3eb48942c1259d2aa1b3c200fad73b39b11c0b8c
ms.openlocfilehash: 9989ea1bf4cb74a6286ebae9de7614ed622de5b6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>Wybieranie rozwiązania do zarządzania urządzeniami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager (znanej także jako ConfgMgr lub SCCM) oferuje różne rozwiązania do zarządzania komputerami, serwerów i urządzeń. Można wybrać rozwiązanie, które jest odpowiednie dla Ciebie na podstawie platformy urządzeń, których potrzebujesz do zarządzania i funkcje zarządzania, które są potrzebne.  


##  <a name="overview-of-device-management-solutions"></a>Przegląd rozwiązań do zarządzania urządzeniami  
 W tym artykule omówiono cztery rozwiązań do zarządzania urządzeniami: aplikacja klienta programu Configuration Manager, lokalną infrastrukturę programu Configuration Manager, Microsoft Intune i programu Exchange. Artykuł zawiera z dwóch tabel, które porównać rozwiązań zarządzania oparty na [obsługiwane platformy urządzeń przenośnych](#compare-device-management-solutions-based-on-supported-mobile-device-platforms), a drugi na podstawie [funkcje zarządzania](#compare-mobile-device-management-solutions-based-on-management-functionality).


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Zarządzanie urządzeniami przy użyciu klienta programu Configuration Manager  

Ta opcja, która wymaga instalacji aplikacji klienta programu Configuration Manager na urządzeniach, zawiera większość funkcji związanych z zarządzaniem komputerami, serwerów i inne urządzenia w danym środowisku. Aby uzyskać więcej informacji, zobacz [metody instalacji klienta w programie System Center Configuration Manager](/sccm/core/clients/deploy/plan/client-installation-methods).  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>Zarządzanie urządzeniami przy użyciu infrastruktury lokalnej programu Configuration Manager  

Ta opcja używa funkcji zarządzania urządzeniami wbudowane systemy operacyjne niektórych platformach urządzeń. Gdy nie w pełni funkcjonalne jak zarządzanie oparte na kliencie, zarządzania urządzeniami przenośnymi lokalnie zapewnia jaśniejsze podejście dotykowego do zarządzania przy użyciu lokalnych zasobów programu Configuration Manager dotrzeć do urządzeń i zarządzanie nimi. Należy zauważyć, że ta opcja jest obecnie obsługiwana tylko przez komputery z systemem Windows 10 i Windows 10 Mobile urządzeń.  

Aby uzyskać więcej informacji, zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>Zarządzanie urządzeniami w usłudze Microsoft Intune (hybrydowy)  

Ta opcja używa Microsoft Intune rejestrować urządzeń i zarządzanie nimi, zamiast używać zasobów lokalnych programu Configuration Manager. Mimo że Intune zarządza urządzeniami, dostęp do zadań zarządzania w konsoli programu Configuration Manager. Ta opcja obsługuje wszystkie systemy operacyjne głównych urządzeń przenośnych, włącznie z systemem Windows 10 Mobile, Windows Phone, iOS, Mac OS X i Android. Umożliwia także zarządzanie komputerami z systemem Windows 8.1 i Windows 10 w organizacji.  

Aby uzyskać więcej informacji, zobacz [Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune](../../mdm/understand/hybrid-mobile-device-management.md).  

###  <a name="manage-devices-with-microsoft-exchange"></a>Zarządzanie urządzeniami za pomocą programu Microsoft Exchange  

Ta opcja połączyć z wieloma serwerami programu Exchange dla programu Configuration Manager przy użyciu łącznika serwera Exchange. Umożliwia to scentralizowanie zarządzania urządzeniami, które można nawiązać połączenia z programem Exchange ActiveSync. Można skonfigurować funkcje zarządzania urządzeniami przenośnymi programu Exchange, takich jak czyszczenie urządzenia zdalnego i sterowania ustawienia w przypadku wielu serwerów programu Exchange z konsoli programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

Można użyć tych rozwiązań do zarządzania urządzeniami, samodzielnie lub w połączeniu ze sobą. Na przykład można użyć metody zarządzania oparte na kliencie do zarządzania komputerami i serwerami w organizacji, a również używać usługi Intune do zarządzania urządzeniami przenośnymi. Przez łączenie podejścia w ten sposób obejmują wszystkie Twoje potrzeby zarządzania urządzeniami z poziomu konsoli programu Configuration Manager.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>Porównaj rozwiązań do zarządzania urządzeniami oparte na platformach obsługiwanych urządzeń przenośnych  

|Platforma|Za pomocą klienta programu Configuration Manager|Menedżer konfiguracji w usłudze Microsoft Intune (hybrydowy)|Na\-lokalnych zarządzania urządzeniami przenośnymi|Menedżer konfiguracji programu Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||Tak||Tak|  
|iOS||Tak||Tak|  
|Mac OS X|Tak|||Tak|  
|UNIX/Linux|Tak|||Tak|  
|Windows 10|Tak|Tak|Tak|Tak|  
|Windows 10 Mobile||Tak|Tak|Tak|  
|Windows (poprzednie wersje)|Tak|Tak||Tak|  
|Windows CE|Tak (za pomocą starszego klient urządzenia przenośnego)|||Tak|  
|Windows Embedded|Tak||||  
|Windows Phone||Tak||Tak|  
|Windows Server|Tak|||Tak|  

 Aby uzyskać pełną listę obsługiwanych platform, zobacz [obsługiwanych systemów operacyjnych dla urządzeń i klientów dla programu System Center Configuration Manager](configs\supported-operating-systems-for-clients-and-devices.md).

##  <a name="bkmk_comp2"></a> Porównanie rozwiązań do zarządzania urządzeniami przenośnymi w oparciu o funkcje zarządzania  

|Funkcje zarządzania|Za pomocą klienta programu Configuration Manager|Menedżer konfiguracji w usłudze Microsoft Intune (hybrydowy)|Na\-lokalnych zarządzania urządzeniami przenośnymi|Menedżer konfiguracji programu Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Zabezpieczenie infrastruktury kluczy publicznych (PKI) między urządzeniem przenośnym a Configuration Manager (używa wzajemnego uwierzytelniania oraz protokołu SSL szyfrowania przekazywanych danych)|Tak|Tak|Tak||  
|Instalacja klienta|Tak||||  
|Obsługa w sieci Internet|Tak||||  
|Odnajdywanie|Tak|||Tak|  
|Spis sprzętu|Tak|Tak|Tak|Tak|  
|Zapasy oprogramowania|Tak|||Tak|  
|Ustawienia|Tak|Tak|Tak|Tak|  
|Wdrażanie oprogramowania|Tak|Tak|Tak||  
|Monitorowanie z rezerwowym punktem stanu|Tak||||  
|Połączenia z punktami zarządzania|Tak||Tak||  
|Połączenia z punktami dystrybucji|Tak||Tak||  
|Blok z programu Configuration Manager|Tak|Tak|Tak||  
|Kwarantanna i blokowanie w programie Exchange Server (i programu Configuration Manager)||||Tak|  
|Zdalne czyszczenie| |Tak|Tak|Tak|  

