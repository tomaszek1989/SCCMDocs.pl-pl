---
title: Tworzenie aplikacji Windows Phone | Dokumentacja firmy Microsoft
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji na urządzeniach Windows Phone."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 6cbf2389a72c0c384ef8e84a1755ac77b64bfc6d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-phone-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji Windows Phone z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje wymagane do wdrożenia oprogramowania na urządzeniu. Typu wdrożenia zawiera również zasady określające czas i sposób wdrożenia oprogramowania.  

 Możesz tworzyć aplikacje przy użyciu następujących metod:  

-   Automatyczne utworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Importowanie aplikacji z pliku.  

Zobacz [Uruchom Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) kroki wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy uwzględnić następujące kwestie, podczas tworzenia i wdrażania aplikacji na urządzeniach Windows Phone.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Program Configuration Manager obsługuje wdrażanie następujących typów plików aplikacji:  

|Typ urządzenia|Obsługiwane typy plików|  
|-----------------|---------------------|  
|Windows Phone 8|XAP|  
|Windows Phone 8,1|XAP, .appx, .appxbundle|
|Windows 10 Mobile|XAP, .appx, .appxbundle|

 Obsługiwane są następujące akcje wdrażania:  

|Typ urządzenia|Obsługiwane akcje|  
|-----------------|-----------------------|  
|Windows Phone 8, Windows Phone 8.1 i Windows 10 Mobile|Dostępne, Wymagane, Odinstaluj|  

## <a name="steps-to-deploy-the-latest-windows-phone-company-portal-app-with-supersedence"></a>Procedura wdrażania najnowszej aplikacji portalu firmy dla Windows Phone przez zastępowanie  
 Poniższa tabela zawiera procedurę, dokładne opisy i dodatkowe informacje dotyczące tworzenia i wdrażania najnowszej aplikacji portalu firmy dla systemu Windows Phone 8.  

|Krok|Więcej informacji|  
|----------|----------------------|  
|**Krok 1:** Pobierz najnowsze aplikacji portalu firmy.|Pobierz [aplikację portalu firmy dla urządzeń Windows Phone 8](http://go.microsoft.com/fwlink/?LinkId=268440).|  
|**Krok 2:** Podpisanie aplikacji portalu firmy certyfikatem firmy Symantec.|Aby uzyskać informacje na temat podpisywania aplikacji portalu firmy, zobacz [skonfigurować Windows Phone i Windows 10 Mobile hybrydowego zarządzania urządzeniami w programie System Center Configuration Manager i Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Krok 3:** Utwórz nową aplikację do najnowszej wersji aplikacji portalu firmy i określ relację zastępowania.|Aby uzyskać więcej informacji, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md) i [przeglądu i zastępowania aplikacji](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Krok 4:** Dodaj aplikację do kreatora subskrypcji usługi Microsoft Intune.|Aby uzyskać więcej informacji, zobacz [skonfigurować Windows Phone i Windows 10 Mobile hybrydowego zarządzania urządzeniami w programie System Center Configuration Manager i Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Krok 5.** Usuń wdrożenie, które zostało automatycznie utworzone po dodaniu aplikacji portalu firmy do kreatora subskrypcji usługi Microsoft Intune.|Subskrypcja Microsoft Intune utworzyła automatyczne wdrożenie tej aplikacji, ponieważ to wdrożenie nie obsługuje zastępowania.|  
|**Krok 6:** Utwórz nowe wdrożenie aplikacji. Na **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**, sprawdź **automatycznie uaktualniania wszelkie zastąpiony wersji tej aplikacji**.|Utwórz nowe wdrożenie z zastępowaniem za pomocą aplikacji utworzonej z relacją zastępowania.|  
|**Krok 7 (opcjonalny):** Domyślnie zastępujące aplikacje instalowane na urządzeniach po 7 dniach. Do wdrażania firmy aplikacji portalu wcześniej do wcześniej zarejestrowane urządzenia, zmień **Zaplanuj ponowną ocenę dla wdrożeń** ustawienie niższą wartość.<br /><br /> Po ustawieniu tej wartości na niższą wartość niż domyślna go może to negatywnie wpłynąć na wydajność Twojej sieci i komputerów klienckich.|Brak dodatkowych informacji.|  

