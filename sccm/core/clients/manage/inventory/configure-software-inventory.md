---
title: Konfigurowanie spisu oprogramowania | Dokumentacja firmy Microsoft
description: "Konfigurowanie spisu oprogramowania i wykluczyć foldery ze spisu oprogramowania w programie Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e60cec71c425e5e42d450cbeee366528d4b42405
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>Jak skonfigurować spis oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla spisu oprogramowania i dotyczy wszystkich komputerów w hierarchii. Jeśli chcesz zastosować te ustawienia tylko do niektórych komputerów, Utwórz niestandardowe ustawienie urządzenia klienckiego i przypisz je do kolekcji zawierającej komputery, na których chcesz używać spisu oprogramowania. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowych ustawień urządzenia, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

## <a name="to-configure-software-inventory"></a>Aby skonfigurować spis oprogramowania  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta****domyślne ustawienia klienta**.    

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **ustawienia domyślne** oknie dialogowym wybierz **spisu oprogramowania**.  

6.  Na liście **Ustawienia urządzenia** skonfiguruj następujące wartości:  

    -   **Włącz spis oprogramowania na klientach** — z listy rozwijanej wybierz **True**.  

    -   **Harmonogram spisu, a plik kolekcji harmonogram oprogramowania** — konfiguruje interwał, w którym zbierania spisu oprogramowania i plików.   

7.  Skonfiguruj wymagane ustawienia klienta. Aby uzyskać listę ustawień klienta spisu oprogramowania, które można skonfigurować, zobacz [spisu oprogramowania](../../../../core/clients/deploy/about-client-settings.md#software-inventory) sekcji [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) tematu.  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  


## <a name="to-exclude-folders-from-software-inventory"></a>Aby wykluczyć foldery ze spisu oprogramowania  

1.  Używając programu Notepad.exe, utwórz pusty plik o nazwie **Skpswi.dat**.  

2.  Kliknij prawym przyciskiem myszy plik **Skpswi.dat** , a następnie kliknij pozycję **Właściwości**. W oknie właściwości pliku Skpswi.dat wybierz atrybut **Ukryty** .  

3.  Umieść plik **Skpswi.dat** w folderze głównym struktury folderów lub dysku twardego klienta w celu ich wykluczenia ze spisu oprogramowania.  

> [!NOTE]  
>  Spis oprogramowania nie będzie wykonywany na dysku klienta ponownie, chyba że ten plik zostanie usunięty z dysku na komputerze klienckim.