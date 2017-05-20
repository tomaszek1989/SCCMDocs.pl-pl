---
title: Tworzenie aplikacji systemu iOS | Dokumentacja firmy Microsoft
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji na urządzeniach z systemem iOS."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 349fcf335e7faddbcbd2ffe0ece7e711465f28df
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji systemu iOS z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje wymagane do wdrożenia oprogramowania na urządzeniu. Typu wdrożenia zawiera również zasady określające czas i sposób wdrożenia oprogramowania.  

 Możesz tworzyć aplikacje przy użyciu następujących metod:  

-   Automatyczne utworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Importowanie aplikacji z pliku.  

Zobacz [Uruchom Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) kroki wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy uwzględnić następujące kwestie, podczas tworzenia i wdrażania aplikacji na urządzeniach z systemem iOS.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Program Configuration Manager obsługuje wdrażanie następujących typów aplikacji:  

|Typ urządzenia|Obsługiwane pliki|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> W System Center Configuration Manager nie trzeba określić plik listy właściwości (.plist), podczas importowania aplikacji dla systemu iOS.|  

 Obsługiwane są następujące akcje wdrażania:  

|Typ urządzenia|Obsługiwane akcje|  
|-----------------|-----------------------|  
|iOS|**Dostępne**, **wymagane**. Użytkownik musi wyrazić zgodę na instalacji i dezinstalacji.

> [!IMPORTANT]  
>  Obecnie użytkownicy końcowi nie mogą instalować aplikacji firmowych za pomocą aplikacji Portal firmy usługi Microsoft Intune dla systemu iOS. Jest to spowodowane istnieją ograniczenia, które znajdują się w aplikacji opublikowanych w sklepie iOS App Store (patrz wytyczne przeglądu sklepu aplikacji, sekcja 2). Użytkownicy mogą instalować aplikacje firmowe (w tym aplikacje zarządzane i pakiety aplikacji biznesowych ze sklepu App Store) przez przejście na urządzeniu do portalu usługi Intune w sieci Web (portal.manage.microsoft.com). Aby uzyskać więcej informacji na temat możliwości zarządzania mobilnego, które są włączone za pomocą aplikacji Portal firmy usługi Intune, zobacz [zarejestrowane możliwości zarządzania urządzeniami w programie Microsoft Intune](https://technet.microsoft.com/library/dn600287.aspx).  

