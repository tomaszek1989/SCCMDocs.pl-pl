---
title: "Znajdź nazwę rodziny pakietu (PFN) dla sieci VPN dla aplikacji | Dokumentacja firmy Microsoft"
description: "Zapoznaj się z dwóch sposobów, aby znaleźć nazwę rodziny pakietu, dzięki czemu można skonfigurować sieci VPN dla aplikacji."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: 3
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: ce50645155ecb14a82d8b982aa69c0f87dd15fbf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Znajdź nazwę rodziny pakietu (PFN) dla sieci VPN dla aplikacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Istnieją dwa sposoby, aby znaleźć PFN, dzięki czemu można skonfigurować sieci VPN dla aplikacji.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Znajdź PFN dla aplikacji, która jest zainstalowana na komputerze z systemem Windows 10

Jeśli korzystasz z aplikacji jest już zainstalowany na komputerze z systemem Windows 10, można użyć [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) polecenia cmdlet środowiska PowerShell w celu uzyskania PFN.

Składnia Get-AppxPackage jest:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Może być konieczne uruchamiania programu PowerShell jako administrator, aby pobrać PFN

Na przykład, aby uzyskać informacje na temat uniwersalnych aplikacji instalowanych przy użyciu komputera `Get-AppxPackage`.

Aby uzyskać informacje o aplikacji, należy znać nazwę lub część nazwy, należy użyć `Get-AppxPackage *<app_name>`. Należy zwrócić uwagę na znaki wieloznaczne, szczególnie przydatne, jeśli nie masz pewności pełnej nazwy aplikacji. Na przykład uzyskać informacje dotyczące programu OneNote, użyj `Get-AppxPackage *OneNote`.


Poniżej przedstawiono informacje pobierane dla programu OneNote:

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



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Znajdź PFN, jeśli aplikacja nie jest zainstalowana na komputerze

1.    Przejdź do https://www.microsoft.com/en-us/store/apps
2.    Wprowadź nazwę aplikacji na pasku wyszukiwania. W naszym przykładzie wyszukiwanie programu OneNote.
3.    Kliknij łącza do aplikacji. Należy zauważyć, że adres URL, którego można uzyskać dostęp ma szereg litery na końcu. W naszym przykładzie adres URL wygląda następująco:`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.    Wklej następujący adres URL w innej karty `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, zastąpienie `<app id>` z identyfikatorem aplikacji uzyskany z https://www.microsoft.com/en-us/store/apps - tej serii litery na końcu adresu URL w kroku 3. W naszym przykładzie przykład programu OneNote, można wkleić: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

W krawędzi jest wyświetlane żądane informacje; w programie Internet Explorer kliknij polecenie **Otwórz** Aby wyświetlić informacje. Wartość PFN jest podana w pierwszym wierszu. Oto jak wyniki wyglądać w naszym przykładzie:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`

