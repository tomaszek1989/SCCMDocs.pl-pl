---
title: "Nowości w przewodniku 2013 zestawu MDT"
titleSuffix: Microsoft Deployment Toolkit
description: "Więcej informacji na temat programu Microsoft Deployment Toolkit 2013. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 17466fa9-1a26-4dd8-a36f-c0c68fa1984c
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fd207a77bad880a37cf04abc159aac6689a99afe
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="whats-new-in-microsoft-deployment-toolkit-mdt-2013-guide"></a>What's new in Microsoft Deployment Toolkit (MDT) 2013 przewodnik
Program Microsoft Deployment Toolkit (MDT) 2013 jest następnej wersji akcelerator rozwiązań firmy Microsoft dla systemu operacyjnego i wdrażania aplikacji. Przewodnik ten ma na celu opisano zmiany w zestawie MDT 2013 z zestawem MDT 2012 Update 1.  

 W tym przewodniku szczegółowo omówiono w wersji 2013 zestawu MDT oraz założono znajomość poprzednich pojęcia wersji zestawu MDT, funkcje i możliwości.  

> [!NOTE]   
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

## <a name="whats-new-in-this-release"></a>Nowości w tej wersji  
 Zestaw MDT zawiera kilka ulepszeń, które dodaje nowe funkcje i zwiększa użytkowników z zestawu MDT. Ponadto w tej wersji zestawu MDT zawiera wiele ulepszeń małe i poprawki, które nie są wymienione poniżej.  

### <a name="support-for-upgrading-from-previous-versions-of-mdt"></a>Obsługa uaktualniania z poprzednich wersji zestawu mdt  
 Zestaw MDT obsługuje uaktualnianie z zestawu MDT 2012 Update 1.  

> [!NOTE]   
>  Utwórz kopię zapasową istniejącej infrastruktury MDT przed próbą uaktualnienia.  

### <a name="support-for-windows-81-and-windows-server-2012-r2"></a>Obsługa Windows 8.1 i Windows Server 2012 R2  
 Zestaw MDT służy do wdrażania systemów operacyjnych Windows 8.1 i Windows Server 2012 R2 przy użyciu metody wdrożenia LTI, ZTI i UDI. Role i funkcje właściwe dla Windows 8.1 i Windows Server 2012 R2 są dostępne na liście roli.  

### <a name="support-for-the-windows-adk-for-windows-81"></a>Obsługa systemu Windows ADK dla Windows 8.1  
 Zestaw MDT obsługuje Windows ADK dla Windows 8.1 do wdrażania systemów operacyjnych. Zestaw ADK systemu Windows na Windows 8.1 zawiera narzędzia wdrażania takich jak narzędzia Deployment Image Servicing and Management (DISM), środowisko preinstalacji systemu Windows (Windows PE) i narzędzia migracji stanu użytkowników (USMT).  

### <a name="support-for-system-center-2012-r2-configuration-manager"></a>Obsługa programu System Center 2012 R2 Configuration Manager  
 ZTI i UDI metody wdrażania w zestawie MDT integrację z programem System Center 2012 R2 Configuration Manager, w tym nowe funkcje, takie jak wiele kont dostępu do sieci.  

### <a name="improved-deployment-to-x86-based-computers-that-use-the-uefi-standard"></a>Ulepszone wdrażanie na komputerach z systemem x86 używające standardu UEFI  
 Unified Extensible Firmware Interface (UEFI) to specyfikacja interfejsu oprogramowania między systemu operacyjnego i oprogramowania układowego platformy. UEFI nie zastępuje bezpieczniejsze starsze system podstawowych operacji wejścia/wyjścia (BIOS) oprogramowania układowego interfejsie w niektórych komputerów osobistych, które są narażone na złośliwego oprogramowania, które wykonuje ataków, podczas rozruchu lub włączenie automatycznego testu procesów.  

 Domyślnie zestaw MDT tworzy partycje odpowiednie do obsługi komputerów z interfejsem UEFI. Zestaw MDT obsługuje wersje 2.0 do 2.3.1 UEFI. Z interfejsem UEFI 2.3.1 jest nowsza wersja UEFI, który będzie używany na komputerach zgodne z logo systemu Windows 8.  

 Aby uzyskać więcej informacji na temat obsługi interfejsu UEFI w zestawie MDT, zobacz sekcję "Wdrożenia do komputerów z interfejsem UEFI", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

## <a name="whats-been-removed-from-this-release"></a>Co to jest zostały usunięte w tej wersji?  
 Tej wersji zestawu MDT nie obejmuje następujące funkcje, które były dostępne w poprzednich wersjach zestawu mdt:  

-   Wdrażanie systemu Windows 8.1 Preview  

-   Wdrażanie systemu Windows Server 2012 R2 Preview  

-   ZTI z  

    -   System Center Configuration Manager 2007  

    -   System Center 2012 Configuration Manager  

    -   System Center 2012 Configuration Manager SP1  

    -   System Center 2012 R2 Configuration Manager Preview  

-   Korzystanie z systemu Windows ADK dla systemu Windows 8  

-   Korzystanie z zestawu Windows AIK dla systemu Windows 7  

-   Wdrażanie systemu Windows XP lub Windows Server 2003  

-   Wdrażanie systemu Windows Vista lub Windows Server 2008  

-   Out-of-box obiektów zasad grupy (GPO) z Menedżera zgodności zabezpieczeń (SCM). Narzędzia i obiektów zasad grupy muszą być zainstalowane z programem SCM przed ich użyciem w zestawie MDT.  

## <a name="operating-system-support-in-this-release"></a>Obsługa systemu operacyjnego w tej wersji  
W poniższej tabeli wymieniono obsługi systemu operacyjnego tego LTI i wdrożenia ZTI Podaj w tej wersji zestawu MDT.  

|||||  
|-|-|-|-|  
|System operacyjny|LTI|ZTI|UDI|  
|Windows 8.1|●|●|●|  
|Windows Server 2012 R2|●|●||  
|Windows 8|●|●|●|  
|Windows Server 2012|●|●||  
|Windows 7|●|●|●|  
|Windows Server 2008 R2|●|●||  
|Windows PE w wersji 5.0|●|●|●|  

 ● = obsługiwane  

## <a name="windows-adk-support"></a>Obsługa systemu Windows ADK  
 W poniższej tabeli wymieniono pomocy technicznej Windows ADK i zestaw Windows AIK, zapewniających wdrożenia LTI, ZTI i UDI w zestawie MDT.  

|||||  
|-|-|-|-|  
|Zestaw Windows ADK|LTI|ZTI|UDI|  
|Windows ADK dla Windows 8.1|●|●|●|  

 ● = obsługiwane  

## <a name="microsoft-net-framework-and-windows-powershell-support"></a>Microsoft .NET Framework i obsługa programu Windows PowerShell  
W poniższej tabeli wymieniono wersje programu Microsoft .NET Framework i programu Windows PowerShell są obsługiwane przez zestaw MDT przez wersję systemu operacyjnego Windows.  


||||  
|-|-|-|  
|Wersja systemu Windows|.NET|PowerShell|  
|Windows 8.1|4.0|3.0|  
|Windows Server 2012 R2|4.0|3.0|  
|Windows 8|4.0|3.0|  
|Windows Server 2012|4.0|3.0|  
|Windows 7|3.5 z dodatkiem SP1|2.0|  
|Windows Server 2008 R2|3.5 z dodatkiem SP1|2.0|
