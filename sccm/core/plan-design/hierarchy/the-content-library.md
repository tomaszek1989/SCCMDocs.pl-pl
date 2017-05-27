---
title: "Biblioteka zawartości | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat biblioteki zawartości, korzystających z programu System Center Configuration Manager zmniejszyć ogólny rozmiar treści."
ms.custom: na
ms.date: 2/14/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d31fecdb71b498864df2bce7403a4290ea9700ae
ms.openlocfilehash: 0fa9f431c00476d71b2b08f92f914d76636d1a27
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-in-system-center-configuration-manager"></a>Biblioteka zawartości w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Biblioteka zawartości jest magazynem jednego wystąpienia zawartości, która pozwala zmniejszyć ogólną połączonych treści zawartości, którą można dystrybuować korzysta z programu System Center Configuration Manager. Biblioteka zawartości są przechowywane wszystkie pliki zawartości dla aktualizacji oprogramowania, aplikacje, wdrożenia systemu operacyjnego i tak dalej.

 - Kopię biblioteki zawartości jest automatycznie tworzyć i konserwować na każdym **serwera lokacji** i na każdym **punktu dystrybucji**.

 - Zanim program Configuration Manager pobiera pliki zawartości na serwerze lokacji lub kopiuje pliki do punktów dystrybucji, Configuration Manager sprawdza, czy każdy plik zawartości jest już w bibliotece zawartości.
 - Jeżeli plik zawartości jest dostępny, Configuration Manager nie kopiuje plików i skojarza istniejący plik zawartości z aplikacją lub pakietem.

Komputery, na którym zainstalowano punkt dystrybucji można skonfigurować:

- Jeden lub więcej dysków na których ma zostać utworzona biblioteka zawartości.
- Priorytet dla każdego dysku, którego używasz.

Po programu Configuration Manager kopiuje pliki zawartości, kopiuje je do stacji o najwyższym priorytecie dopóki przekroczona minimalna ilość wolnego miejsca.
- Ustawienia stacji konfiguruje się podczas instalacji punktu dystrybucji.
- Nie można skonfigurować ustawień stacji we właściwościach punktu dystrybucji, po zakończeniu instalacji.


Aby uzyskać więcej informacji o sposobie konfigurowania ustawień stacji w ramach punktu dystrybucji, zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


>  [!IMPORTANT]  
>  Do przenoszenia biblioteki zawartości w innej lokalizacji w punkcie dystrybucji po zakończeniu instalacji, należy użyć **narzędzia do przenoszenia biblioteki zawartości** w System Center 2012 R2 Configuration Manager Toolkit. Możesz pobrać zestaw narzędzi z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

## <a name="about-the-content-library-on-the-central-administration-site"></a>Informacje o bibliotece zawartości w witrynie Administracja centralna  
 Domyślnie program Configuration Manager tworzy bibliotekę zawartości w witrynie Administracja centralna, po zainstalowaniu lokacji. Biblioteka zawartości jest umieszczany na dysku serwera lokacji, który ma najwięcej wolnego miejsca na dysku. Nie można zainstalować punkt dystrybucji w witrynie Administracja centralna, nie można ustalić ich priorytety dysków dla biblioteki zawartości. Podobnie jak w przypadku biblioteki zawartości na innych serwerach lokacji i w punktach dystrybucji, gdy na dysku zawierającym bibliotekę zawartości zabraknie dostępnego miejsca na dysku, Biblioteka zawartości zostanie automatycznie rozszerzony do następnego dostępnego dysku.  

 Program Configuration Manager korzysta z biblioteki zawartości w witrynie Administracja centralna w następujących scenariuszach:  

-   Podczas tworzenia zawartości w witrynie Administracja centralna.  

-   Podczas migrowania zawartości z innej lokacji programu Configuration Manager i przypisywania centralnej lokacji administracyjnej jako lokacji, która zarządza tą zawartością.  

> [!NOTE]  
>  Podczas tworzenia zawartości w lokacji głównej i rozpowszechnienie go do innej lokacji głównej lub lokacji dodatkowej poniżej innej lokacji głównej witryny Administracja centralna tymczasowo przechowuje tą zawartość w skrzynce odbiorczej harmonogramu, w witrynie Administracja centralna, ale nie dodaje jej do biblioteki zawartości.  

 Aby zarządzać biblioteki zawartości w witrynie Administracja centralna, należy użyć następujących opcji:  

-   Aby zapobiec biblioteki zawartości są zainstalowane na określonym dysku, należy utworzyć pusty plik o nazwie **no_sms_on_drive.sms**, a następnie skopiuj go do folderu głównego dysku przed utworzeniem biblioteki zawartości.  

-   Po utworzeniu biblioteki zawartości za pomocą **narzędzia do przenoszenia biblioteki zawartości** z System Center 2012 R2 zestawie narzędzi Configuration Manager do zarządzania Lokalizacja biblioteki zawartości. Możesz pobrać zestaw narzędzi z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

