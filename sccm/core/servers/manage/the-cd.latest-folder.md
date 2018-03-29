---
title: Folder CD.Latest
titleSuffix: Configuration Manager
description: Więcej informacji na temat nowy proces aktualizacji, który dostarcza aktualizacje produktu z poziomu konsoli programu Configuration Manager.
ms.custom: na
ms.date: 03/28/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 86b6393a6719895357d34fe8e562f3d0c967ad06
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="the-cdlatest-folder-for-system-center-configuration-manager"></a>Folder CD.Latest programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager wprowadzono nowy proces aktualizacji, który dostarcza aktualizacje produktu z poziomu konsoli programu Configuration Manager. Do obsługi tej nowej metody aktualizacji programu Configuration Manager, tworzony jest nowy folder o nazwie **dysku CD. Najnowsze** zawierający kopię plików instalacyjnych programu Configuration Manager do zaktualizowanej wersji lokacji.  

Dysk CD. Najnowszy folder zawiera folder o nazwie **Redist** zawierającą pakiet redystrybucyjny pliki, które Instalator pliki do pobrania i zastosowania. Te pliki są dopasowane do wersji plików programu Configuration Manager znajdujących się w folderze CD.Latest. Po uruchomieniu Instalatora z folderu CD.Latest musisz użyć plików dopasowanych do wersji Instalatora. W tym celu możesz przekierować Instalatora w celu pobrania nowych i bieżących plików od firmy Microsoft lub użycia plików z folderu Redist znajdującego się w folderze CD.Latest.

Jednak nośnika linii bazowej, takie jak wersji linii bazowej 1802, który wydane w ramach marca 2018 nie obejmuje folderu redystrybucyjnego. Nie będzie można utworzyć folderu Redist, aż do zainstalowania aktualizacji w konsoli. W międzyczasie użyj folderu Redist, które zostały użyte podczas instalowania lokacji z nośnika linii bazowej.  

> [!TIP]
> Upewnij się, że pliki redystrybucyjne, którego używasz są aktualne. Jeśli pliki redystrybucyjne nie zostały ostatnio pobrany, zaplanuj instalację to zrobić przez firmę Microsoft.   

 Następujące scenariusze są związane z tworzeniem lub aktualizowaniem folderu CD.Latest na serwerze centralnej lokacji administracyjnej lub lokacji głównej:  

-   Instalowania aktualizacji lub poprawki z poziomu konsoli programu Configuration Manager: Folder jest tworzony lub aktualizowany w folderze instalacyjnym programu Configuration Manager.  

-   Możesz uruchomić wbudowanego zadania tworzenia kopii zapasowej programu Configuration Manager: Folder jest tworzony lub aktualizowany w lokalizacji wskazanego folderu kopii zapasowej.  

-  Dysk CD. Najnowszy folder jest tworzony podczas instalowania nowej lokacji za pomocą nośnika linii bazowej (np. wersja 1802).

Pliki źródłowe z folderu CD.Latest są obsługiwane w następujących przypadkach:  

1.  **Tworzenie kopii zapasowej i odzyskiwanie:** Aby odzyskać lokację, należy użyć plików źródłowych z dysku CD. Najnowszy folder zgodnej z lokacją. Po uruchomieniu kopii zapasowej lokacji przy użyciu witryny wbudowanego zadania tworzenia kopii zapasowej dysku CD. Najnowszy folder wchodzi w skład kopii zapasowej.

    -   **Podczas ponownego instalowania lokacji w ramach odzyskiwania lokacji** jest ona instalowana z folderu CD.Latest zawartego w kopii zapasowej. To powoduje zainstalowanie lokacji przy użyciu wersji plików zgodnych z kopią zapasową lokacji i bazą danych lokacji.  Jeśli nie masz dostępu poprawny dysk CD. Najnowszą wersję folderu, możesz uzyskać dysku CD. Najnowszy folder o poprawne wersje plików instalacji lokacji w środowisku laboratoryjnym, a następnie zaktualizować zgodna z wersją z tej lokacji, do której chcesz odzyskać.

        > [!IMPORTANT]  
        >  Jeśli nie masz poprawnego folderu CD.Latest z dostępną zawartością, nie możesz odzyskać lokacji, a lokacja wymaga ponownego zainstalowania.  

    -   Jeśli nie masz folderu CD.Latest, ale masz działającą podrzędną lokację główną lub centralną lokację administracyjną, możesz użyć tej lokacji jako lokacji odniesienia w procesie odzyskiwania lokacji.  

2.  **Aby zainstalować podrzędną lokację główną:** Jeśli chcesz zainstalować nową podrzędną lokację główną lokacji administracji centralnej, który ma zainstalowany co najmniej jednej aktualizacji w konsoli, należy użyć Instalatora i plików źródłowych z dysku CD. Najnowszy folder z centralnej lokacji administracyjnej. Gdy Instalator zostaje uruchomiony z kopii folderu CD.Latest z centralnej lokacji administracyjnej, używa plików źródłowych instalacji, które są zgodne z wersją centralnej lokacji administracyjnej. Aby uzyskać więcej informacji, zobacz [Use the Setup Wizard to install sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (Instalowanie lokacji za pomocą Kreatora instalacji).  

3.  **Aby rozszerzyć autonomiczną lokację główną:** Jeśli rozszerzasz autonomiczną lokację główną, instalując nową centralną lokację administracyjną, musisz użyć Instalatora i plików źródłowych z dysku CD. Najnowszy folder z lokacji głównej w celu zainstalowania nowej centralnej lokacji administracyjnej. W przypadku uruchomienia z kopii folderu CD.Latest z lokacji głównej zostaną użyte pliki źródłowe instalacji, które są zgodne z wersją lokacji głównej. Aby uzyskać więcej informacji, zobacz sekcję [Expand a stand-alone primary site](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) (Rozszerzanie autonomicznej lokacji głównej) w temacie [Use the Setup Wizard to install sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (Instalowanie lokacji za pomocą Kreatora instalacji)

> [!IMPORTANT]  
>  Zaktualizowane pliki źródłowe folderu CD.Latest nie są obsługiwane w następujących przypadkach:  
>   
>  -   Instalowanie nowej lokacji do nowej hierarchii  
>  -   Uaktualnianie lokacji programu Microsoft System Center 2012 Configuration Manager do programu System Center Configuration Manager
>  -   Instalowanie klienta programu Configuration Manager
>  -   Instalowanie konsoli administracyjnej programu Configuration Manager

