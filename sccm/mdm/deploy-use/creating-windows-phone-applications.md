---
title: Tworzenie aplikacji Windows Phone
titleSuffix: Configuration Manager
description: Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla urządzeń Windows Phone.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c755db47c9d3acb9c858ecb5bed14bb36055663b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-windows-phone-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji Windows Phone w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje wymagane do wdrożenia oprogramowania na urządzeniu. Typ wdrożenia ma również zasady określające, kiedy i jak oprogramowanie zostanie wdrożone.  

 Aplikacje można utworzyć przy użyciu następujących metod:  

-   Automatyczne tworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Zaimportowanie aplikacji z pliku.  

Zobacz [uruchomić Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) dla czynności wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy pamiętać przedstawione poniżej zagadnienia, podczas tworzenia i wdrażania aplikacji dla urządzeń Windows Phone.  

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

## <a name="steps-to-deploy-the-latest-windows-phone-company-portal-app-with-supersedence"></a>Procedura wdrażania najnowszej aplikacji portalu firmy w Windows Phone przez zastępowanie  
 Poniższa tabela zawiera procedurę, dokładne opisy i dodatkowe informacje dotyczące tworzenia i wdrażania najnowszej aplikacji portalu firmy dla systemu Windows Phone 8.  

|Krok|Więcej informacji|  
|----------|----------------------|  
|**Krok 1.** Pobierz najnowszą wersję aplikacji portalu firmy.|Pobierz [aplikację portalu firmy dla urządzeń Windows Phone 8](http://go.microsoft.com/fwlink/?LinkId=268440).|  
|**Krok 2.** Podpisanie aplikacji portalu firmy certyfikatem firmy Symantec.|Aby uzyskać informacje dotyczące sposobu podpisywania aplikacji portalu firmy, zobacz [Konfigurowanie systemu Windows 10 Mobile i Windows Phone hybrydowego zarządzania urządzeniami w programie System Center Configuration Manager i Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Krok 3.** Utwórz nową aplikację do najnowszej wersji aplikacji portal firmy i określ relację zastępowania.|Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md) i [korygowanie i zastępowanie aplikacji](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Krok 4.** Dodaj aplikację do kreatora subskrypcji usługi Microsoft Intune.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie systemu Windows 10 Mobile i Windows Phone hybrydowego zarządzania urządzeniami w programie System Center Configuration Manager i Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Krok 5.** Usuń wdrożenie, które zostało automatycznie utworzone po dodaniu aplikacji portalu firmy do kreatora subskrypcji usługi Microsoft Intune.|Subskrypcję Microsoft Intune utworzyła automatyczne wdrożenie tej aplikacji, ponieważ to wdrożenie nie obsługuje zastępowania.|  
|**Krok 6.** Utwórz nowe wdrożenie aplikacji. Na **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**, sprawdź **automatyczne uaktualnianie dowolnej wersji tej aplikacji zastąpione**.|Utwórz nowe wdrożenie z zastępowaniem za pomocą aplikacji utworzonej z relacją zastępowania.|  
|**Krok 7 (opcjonalny):** Domyślnie zastępujące aplikacje instalować na urządzeniach po 7 dniach. Firma wdrażania aplikacji portalu wcześniej do wcześniej zarejestrowane urządzenia, zmień **Zaplanuj ponowną ocenę dla wdrożeń** ustawienie niższą wartość.<br /><br /> Jeśli ustawisz tę wartość na mniejszą wartość niż domyślne go może negatywnie wpłynąć na wydajność sieci i klientów komputerów.|Brak dodatkowych informacji.|  
