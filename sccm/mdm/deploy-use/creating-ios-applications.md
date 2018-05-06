---
title: Tworzenie aplikacji systemu iOS
titleSuffix: Configuration Manager
description: Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem iOS.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 985a8177602bd32da0b6134eeddb564a44749d65
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji systemu iOS z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje wymagane do wdrożenia oprogramowania na urządzeniu. Typ wdrożenia ma również zasady określające, kiedy i jak oprogramowanie zostanie wdrożone.  

 Aplikacje można utworzyć przy użyciu następujących metod:  

-   Automatyczne tworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Zaimportowanie aplikacji z pliku.  

Zobacz [uruchomić Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) dla czynności wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy pamiętać przedstawione poniżej zagadnienia, podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem iOS.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Program Configuration Manager obsługuje wdrażanie następujących typów aplikacji:  

|Typ urządzenia|Obsługiwane pliki|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> W programie System Center Configuration Manager, nie trzeba określać pliku listy (.plist) właściwości podczas importowania aplikacji dla systemu iOS.|  

 Obsługiwane są następujące akcje wdrażania:  

|Typ urządzenia|Obsługiwane akcje|  
|-----------------|-----------------------|  
|iOS|**Dostępne**, **wymagane**. Użytkownik musi wyrazić zgodę do instalacji i dezinstalacji.

> [!IMPORTANT]  
>  Obecnie użytkownicy końcowi nie mogą instalować aplikacji firmowych za pomocą aplikacji Portal firmy usługi Microsoft Intune dla systemu iOS. Jest to, ponieważ istnieją ograniczenia, które są dotyczącymi aplikacji opublikowanych w sklepie iOS App Store (zobacz wytyczne przeglądu sklepu aplikacji, sekcja 2). Użytkownicy mogą instalować aplikacje firmowe (w tym aplikacje zarządzane i pakiety aplikacji biznesowych ze sklepu App Store) przez przejście na urządzeniu do portalu usługi Intune w sieci Web (portal.manage.microsoft.com). Aby uzyskać więcej informacji na temat możliwości zarządzania mobilnej, które są włączone przez aplikacji Portal firmy usługi Intune, zobacz [zarejestrowane możliwości zarządzania urządzeniami w programie Microsoft Intune](https://technet.microsoft.com/library/dn600287.aspx).  
