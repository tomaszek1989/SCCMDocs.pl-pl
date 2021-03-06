---
title: Konfigurowanie spisu oprogramowania
titleSuffix: Configuration Manager
description: Konfigurowanie spisu oprogramowania i wykluczyć foldery ze spisu oprogramowania w programie Configuration Manager.
ms.date: 01/03/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 346ff3254f4c1833f49bf256cbf5ad0c489d77e0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>Jak skonfigurować spis oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla spisu oprogramowania i dotyczy wszystkich komputerów w hierarchii. Jeśli chcesz zastosować te ustawienia tylko do niektórych komputerów, Utwórz niestandardowe ustawienie urządzenia klienckiego i przypisz je do kolekcji. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowych ustawień urządzenia, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).   

## <a name="to-configure-software-inventory"></a>Aby skonfigurować spis oprogramowania  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta****domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **ustawienia domyślne** oknie dialogowym wybierz **spisu oprogramowania**.  

6.  Na liście **Ustawienia urządzenia** skonfiguruj następujące wartości:  

    -   **Włącz spis oprogramowania na klientach** — z listy rozwijanej wybierz **True**.  

    -   **Harmonogram spisu, a plik kolekcji harmonogram oprogramowania** — konfiguruje interwał, w którym zbierania spisu oprogramowania i plików.   

7.  Skonfiguruj wymagane ustawienia klienta. [Spisu oprogramowania](../../../../core/clients/deploy/about-client-settings.md#software-inventory) sekcji [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) artykuł zawiera listę ustawień klienta.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

 > [!TIP]  
        >   Kod błędu 80041006 w inventoryprovider.log oznacza, że dostawca WMI jest za mało pamięci. To, że osiągnęła limit przydziału pamięci dla dostawcy i dostawca magazynu nie może kontynuować pracy.
W takim przypadku agent inwentaryzacji tworzy raport z pozycji 0, więc nie zostały zgłoszone nie elementy spisu. <br/>
Możliwe rozwiązania tego błędu jest ograniczyć zakres kolekcji spisu oprogramowania. W przypadku wystąpienia błędu po ograniczenie zakresu spisu zwiększenie [MemoryPerHost](https://blogs.technet.microsoft.com/askperf/2008/09/16/memory-and-handle-quotas-in-the-wmi-provider-service/) właściwość zdefiniowaną w [_ProviderHostQuotaConfiguration](https://msdn.microsoft.com/library/aa394671) klasy mogą zapewnić rozwiązanie.

<!--SMS.480648 include WMI Out of memory tip -->


## <a name="to-exclude-folders-from-software-inventory"></a>Aby wykluczyć foldery ze spisu oprogramowania  

1.  Używając programu Notepad.exe, utwórz pusty plik o nazwie **Skpswi.dat**.  

2.  Kliknij prawym przyciskiem myszy **Skpswi.dat** plik i kliknij przycisk **właściwości**. W oknie właściwości pliku Skpswi.dat wybierz atrybut **Ukryty** .  

3.  Umieść plik **Skpswi.dat** w folderze głównym struktury folderów lub dysku twardego klienta w celu ich wykluczenia ze spisu oprogramowania.  

> [!NOTE]  
>  Spis oprogramowania nie będzie wykonywany na dysku klienta ponownie, chyba że ten plik zostanie usunięty z dysku na komputerze klienckim.