---
title: "Wybieranie rozwiązania do zarządzania urządzeniami — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat rozwiązania, które oferuje System Center Configuration Manager do zarządzania komputerami, serwerami i urządzeniami."
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: "14"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9989ea1bf4cb74a6286ebae9de7614ed622de5b6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>Wybieranie rozwiązania do zarządzania urządzeniami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager (znanej także jako ConfgMgr lub SCCM) udostępnia różne rozwiązania do zarządzania komputerami, serwerami i urządzeniami. Można wybrać rozwiązania, które jest odpowiednie dla Ciebie, w oparciu o platformy urządzeń, którymi trzeba zarządzać i funkcje zarządzania, które są potrzebne.  


##  <a name="overview-of-device-management-solutions"></a>Przegląd rozwiązań do zarządzania urządzeniami  
 W tym artykule opisano cztery rozwiązania do zarządzania urządzeniami: aplikacja klienta programu Configuration Manager, lokalnej infrastruktury programu Configuration Manager, Microsoft Intune i programu Exchange. Artykuł zawiera dwóch tabel, które porównanie rozwiązań do zarządzania, oparty na [obsługiwanych platform urządzeń przenośnych](#compare-device-management-solutions-based-on-supported-mobile-device-platforms)i jedną na podstawie [funkcje zarządzania](#compare-mobile-device-management-solutions-based-on-management-functionality).


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Zarządzanie urządzeniami za pomocą klienta programu Configuration Manager  

Ta opcja, która wymaga instalacji aplikacji klienta programu Configuration Manager na urządzeniach, zawiera większość funkcji związanych z zarządzaniem komputerami, serwerami i innych urządzeniach w danym środowisku. Aby uzyskać więcej informacji, zobacz [metody instalacji klientów w programie System Center Configuration Manager](/sccm/core/clients/deploy/plan/client-installation-methods).  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>Zarządzanie urządzeniami przy użyciu lokalnej infrastruktury programu Configuration Manager  

Ta opcja używa funkcji zarządzania urządzeniami, które są wbudowane w systemy operacyjne niektórych platformach urządzeń. Gdy nie tylu co Zarządzanie oparte na kliencie, lokalnego zarządzania urządzeniami przenośnymi zapewnia łagodniejsze podejście obejmujące do zarządzania przy użyciu lokalnych zasobów programu Configuration Manager do nawiązywania połączeń i zarządzania urządzeniami. Należy pamiętać, że ta opcja jest obecnie obsługiwana tylko dla urządzeń z komputerów z systemem Windows 10 i Windows 10 Mobile.  

Aby uzyskać więcej informacji, zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>Zarządzanie urządzeniami w usłudze Microsoft Intune (rozwiązanie hybrydowe)  

Ta opcja używa Microsoft Intune, aby zarejestrować urządzenia i zarządzać nimi, zamiast używać zasobów lokalnych programu Configuration Manager. Mimo że usługa Intune zarządza urządzeniami, możesz uzyskać dostęp zadań zarządzania w konsoli programu Configuration Manager. Ta opcja obsługuje wszystkie systemy operacyjne urządzeń przenośnych głównych, w tym Windows 10 Mobile, Windows Phone, iOS, Mac OS X i Android. Umożliwia także zarządzanie komputerami z systemem Windows 8.1 i Windows 10 w organizacji.  

Aby uzyskać więcej informacji, zobacz [Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune](../../mdm/understand/hybrid-mobile-device-management.md).  

###  <a name="manage-devices-with-microsoft-exchange"></a>Zarządzanie urządzeniami za pomocą programu Microsoft Exchange  

Ta opcja używa łącznika serwera Exchange do łączenia wielu serwerów programu Exchange do programu Configuration Manager. Umożliwia to scentralizowanie zarządzania urządzeniami, które można łączyć z programem Exchange ActiveSync. Możesz skonfigurować funkcje zarządzania urządzeniami przenośnymi programu Exchange, takie jak zdalne czyszczenie urządzenia i kontrola ustawień wielu serwerów programu Exchange z poziomu konsoli programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

Można użyć tych rozwiązań do zarządzania urządzeniami, samodzielnie lub w połączeniu ze sobą. Na przykład można użyć metody zarządzania opartego na kliencie, aby zarządzać komputerami i serwerami w organizacji, a także użyć usługi Intune do zarządzania urządzeniami przenośnymi. Przez łączenie podejścia w ten sposób może obejmować wszystkich Twoich potrzeb dotyczących zarządzania urządzeniami z konsoli programu Configuration Manager.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>Porównanie rozwiązań do zarządzania urządzeniami oparte na obsługiwanych platformach urządzeń przenośnych  

|Platforma|Przy użyciu klienta programu Configuration Manager|Menedżer konfiguracji w usłudze Microsoft Intune (rozwiązanie hybrydowe)|Na\-lokalnych zarządzania urządzeniami przenośnymi|Program Configuration Manager z programem Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||Tak||Tak|  
|iOS||Tak||Tak|  
|Mac OS X|Tak|||Tak|  
|UNIX/Linux|Tak|||Tak|  
|Windows 10|Tak|Tak|Tak|Tak|  
|Windows 10 Mobile||Tak|Tak|Tak|  
|Systemu Windows (poprzednie wersje)|Tak|Tak||Tak|  
|Windows CE|Tak (za pomocą starszego klient urządzenia przenośnego)|||Tak|  
|Windows Embedded|Tak||||  
|Windows Phone||Tak||Tak|  
|Windows Server|Tak|||Tak|  

 Aby uzyskać pełną listę obsługiwanych platform, zobacz [obsługiwane systemy operacyjne dla klientów i urządzeń dla programu System Center Configuration Manager](configs\supported-operating-systems-for-clients-and-devices.md).

##  <a name="bkmk_comp2"></a> Porównanie rozwiązań do zarządzania urządzeniami przenośnymi w oparciu o funkcje zarządzania  

|Funkcje zarządzania|Przy użyciu klienta programu Configuration Manager|Menedżer konfiguracji w usłudze Microsoft Intune (rozwiązanie hybrydowe)|Na\-lokalnych zarządzania urządzeniami przenośnymi|Program Configuration Manager z programem Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Zabezpieczenie infrastruktury kluczy publicznych (PKI) między urządzeniem przenośnym a Configuration Manager (używa wzajemnego uwierzytelniania i protokołu SSL szyfrowania przekazywanych danych)|Tak|Tak|Tak||  
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
|Kwarantanna i blokowanie z programem Exchange Server (i programu Configuration Manager)||||Tak|  
|Zdalne czyszczenie| |Tak|Tak|Tak|  
