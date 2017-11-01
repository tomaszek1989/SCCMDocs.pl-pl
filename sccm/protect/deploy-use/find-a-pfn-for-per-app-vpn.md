---
title: "Znajdowanie nazwy rodziny pakietów (PFN) dla sieci VPN dla aplikacji"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat dwa sposoby znajdowania nazwy rodziny pakietów, dzięki czemu można skonfigurować sieci VPN dla aplikacji."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: "3"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 640f44985ad45442b05f2bbf4ee1ec9c2590cba4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Znajdowanie nazwy rodziny pakietów (PFN) dla sieci VPN dla aplikacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Istnieją dwa sposoby znajdowania nazwy PFN, dzięki czemu można skonfigurować sieci VPN dla aplikacji.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Znajdowanie nazwy PFN dla aplikacji, która jest zainstalowana na komputerze z systemem Windows 10

Jeśli korzystasz z aplikacji jest już zainstalowana na komputerze z systemem Windows 10, możesz użyć [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) uzyskać nazwę PFN przy użyciu polecenia cmdlet programu PowerShell.

Get-AppxPackage składnia jest następująca:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Może być konieczne uruchomienie programu PowerShell jako administrator w celu uzyskania nazwy PFN

Na przykład, aby uzyskać informacje dotyczące wszystkich aplikacji uniwersalnych zainstalowanych na komputerze, użyj `Get-AppxPackage`.

Aby uzyskać informacje dotyczące aplikacji, musisz znać nazwę lub część nazwy, użyj `Get-AppxPackage *<app_name>`. Zwróć uwagę na użycie wieloznacznego szczególnie przydatne, jeśli nie masz pewności, jaka jest pełna nazwa aplikacji. Na przykład aby uzyskać informacje dotyczące programu OneNote, użyj `Get-AppxPackage *OneNote`.


Oto informacje uzyskane dla programu OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Znajdowanie nazwy PFN, jeśli aplikacja nie jest zainstalowany na komputerze

1.  Przejdź do https://www.microsoft.com/en-us/store/apps
2.  Wprowadź nazwę aplikacji na pasku wyszukiwania. W naszym przykładzie Wyszukaj aplikację OneNote.
3.  Kliknij łącza do wybranej aplikacji. Należy pamiętać, że adres URL zawiera serię liter na końcu. W naszym przykładzie adres URL wygląda następująco:`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Na innej karcie Wklej następujący adres URL `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, zastępując `<app id>` identyfikatorem aplikacji uzyskane z https://www.microsoft.com/en-us/store/apps — serią liter na końcu adresu URL w kroku 3. W tym przykładzie programu OneNote, należy wkleić: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

W krawędzi są wyświetlane żądane informacje; w programie Internet Explorer, kliknij przycisk **Otwórz** Aby wyświetlić informacje. Wartość PFN jest podana w pierwszym wierszu. Oto jak wyglądają wyniki w naszym przykładzie:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
