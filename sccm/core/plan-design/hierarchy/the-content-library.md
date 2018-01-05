---
title: "Biblioteka zawartości"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat biblioteki zawartości, który używa programu System Center Configuration Manager do redukowania łącznego rozmiaru zawartości rozproszonego."
ms.custom: na
ms.date: 2/14/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: "4"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 9951a6562a86fbbf7f705989724d2d8c9c36cca0
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="the-content-library-in-system-center-configuration-manager"></a>Biblioteka zawartości w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Biblioteka zawartości jest magazynem jednego wystąpienia zawartości, który używa programu System Center Configuration Manager do redukowania łącznego rozmiaru połączonej treści zawartości, którą można dystrybuować. Biblioteka zawartości przechowuje wszystkie pliki zawartości obejmujące aktualizacje oprogramowania, aplikacje, wdrożenia systemu operacyjnego i tak dalej.

 - Kopia biblioteki zawartości jest automatycznie utworzona i przechowywana na każdym **serwera lokacji** i w każdym **punktu dystrybucji**.

 - Przed programu Configuration Manager pobierze pliki zawartości na serwerze lokacji lub skopiuje pliki do punktów dystrybucji, Configuration Manager weryfikuje, czy każdy plik zawartości jest już w bibliotece zawartości.
 - Jeżeli plik zawartości jest dostępny, Configuration Manager nie kopiuje plik i skojarza istniejący plik zawartości z aplikacją lub pakietem.

Na komputerach z zainstalowanym punktem dystrybucji można skonfigurować:

- Jeden lub więcej dysków na których ma zostać utworzona biblioteka zawartości.
- Priorytet dla każdego dysku, którego używasz.

Po programu Configuration Manager skopiuje pliki zawartości, są kopiowane je na dysk z najwyższym priorytetem do momentu zawierał mniej niż minimalna ilość wolnego miejsca, który określisz.
- Ustawienia dysku konfiguruje się podczas instalacji punktu dystrybucji.
- Nie można skonfigurować ustawień stacji we właściwościach punktu dystrybucji, po zakończeniu instalacji.


Aby uzyskać więcej informacji o sposobie konfigurowania ustawień dysku punktu dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


>  [!IMPORTANT]  
>  Do przenoszenia biblioteki zawartości w innej lokalizacji w punkcie dystrybucji po zakończeniu instalacji, użyj **narzędzia do przenoszenia biblioteki zawartości** w System Center 2012 R2 Configuration Manager Toolkit. Możesz pobrać zestaw narzędzi z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

## <a name="about-the-content-library-on-the-central-administration-site"></a>Informacje o bibliotece zawartości w centralnej lokacji administracyjnej  
 Domyślnie program Configuration Manager tworzy bibliotekę zawartości w centralnej lokacji administracyjnej, po zainstalowaniu lokacji. Biblioteka zawartości znajduje się na dysku serwera lokacji, który ma najwięcej wolnego miejsca na dysku. Punkt dystrybucji nie można zainstalować w centralnej lokacji administracyjnej, nie można ustalić ich priorytety dysków używanych przez biblioteki zawartości. Podobnie do biblioteki zawartości na innych serwerach lokacji i w punktach dystrybucji, gdy na dysku zawierającym bibliotekę zawartości zabraknie dostępnego miejsca na dysku, Biblioteka zawartości zostanie automatycznie rozszerzony do następnego dostępnego dysku.  

 Configuration Manager korzysta z biblioteki zawartości w centralnej lokacji administracyjnej w następujących scenariuszach:  

-   Podczas tworzenia zawartości w witrynie Administracja centralna.  

-   Podczas migrowania zawartości z innej lokacji programu Configuration Manager i przypisywania centralnej lokacji administracyjnej jako lokacji służącej do zarządzania tą zawartością.  

> [!NOTE]  
>  Podczas tworzenia zawartości w lokacji głównej, a następnie dystrybucji jej do innej lokacji głównej lub lokacji dodatkowej poniżej innej lokacji głównej, centralna lokacja administracyjna tymczasowo przechowuje tą zawartość w skrzynce odbiorczej harmonogramu w witrynie Administracja centralna, ale nie dodaje jej do biblioteki zawartości.  

 Aby zarządzać biblioteki zawartości w centralnej lokacji administracyjnej, należy użyć następujących opcji:  

-   Aby zapobiec biblioteki zawartości są zainstalowane na określonym dysku, Utwórz pusty plik o nazwie **no_sms_on_drive.sms**, a następnie skopiować go do folderu głównego dysku przed utworzeniem biblioteki zawartości.  

-   Po utworzeniu biblioteki zawartości, należy użyć **narzędzia do przenoszenia biblioteki zawartości** z System Center 2012 R2 Configuration Manager Toolkit można zarządzać jej lokalizacją biblioteki zawartości. Możesz pobrać zestaw narzędzi z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  
