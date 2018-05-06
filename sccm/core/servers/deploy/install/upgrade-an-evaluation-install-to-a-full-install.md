---
title: Instaluje uaktualnienia wersji ewaluacyjnej
titleSuffix: Configuration Manager
description: Dowiedz się, jak uaktualnić instalację w wersji ewaluacyjnej do pełnej instalacji programu System Center Configuration Manager.
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b1bbce9f3ca7a1a6cf9c199677b33e34d9be109c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>Uaktualnienie instalacji wersji ewaluacyjnej programu System Center Configuration Manager do instalacji pełnej

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli zainstalowano System Center Configuration Manager w wersji próbnej, po upływie 180 dni konsola programu Configuration Manager staje się tylko do odczytu do momentu aktywowania produktu na **konserwacji lokacji** w Instalatorze. W dowolnym momencie przed lub po upływie 180-dniowego masz opcję, aby uaktualnić instalację w wersji ewaluacyjnej do pełnej instalacji.  

> [!NOTE]  
>  Po podłączeniu konsoli programu Configuration Manager do instalacji wersji ewaluacyjnej programu Configuration Manager na pasku tytułowym konsoli wyświetlana liczba dni pozostałych do wygaśnięcia wersji ewaluacyjnej instalacji. Liczba dni nie powoduje odświeżenia automatycznie i zaktualizuje tylko podczas tworzenia nowego połączenia z lokacją.  

 Można uaktualnić następujące lokacje z instalacją w wersji ewaluacyjnej:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  

Ponieważ Lokacje dodatkowe nie są traktowane jako instalacje wersji ewaluacyjnej, nie należy modyfikować po jego uaktualnieniu nadrzędnej lokalizacji głównej do pełnej wersji instalacji lokacji dodatkowej.  

Wymagania wstępne dotyczące uaktualniania do wersji licencjonowanej wersji ewaluacyjnej:  

-   Musi mieć prawidłową produktu do użycia podczas uaktualniania.  
-   Twoje konto musi mieć **administratora** uprawnienia na komputerze, na którym jest zainstalowana lokacja.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>Aby uaktualnić wersję ewaluacyjną programu Configuration Manager do wersji licencjonowanej  

1.  Na serwerze lokacji Uruchom **Setup.exe** (Instalator programu Configuration Manager) z folderu instalacyjnego programu Configuration Manager (**%path%\BIN\X64**). Należy uruchomić kopię Instalatora zlokalizowaną na serwerze lokacji w folderze programu Configuration Manager, ponieważ opcje konserwacji lokacji nie są dostępne po uruchomieniu Instalatora z nośnika instalacyjnego.  
2.  Na **przed rozpoczęciem** wybierz pozycję **dalej**.  
3.  Na **wprowadzenie** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie wybierz **dalej**.  
4.  Na **konserwacji lokacji** wybierz pozycję **uaktualnienia wersji ewaluacyjnej do wersji licencjonowanej**, wprowadź prawidłowy klucz produktu, a następnie wybierz **dalej**.  
5.  Na **postanowienia licencyjne dotyczące oprogramowania firmy Microsoft** strony, przeczytaj i zaakceptuj postanowienia licencyjne, a następnie wybierz **dalej**.  
6.  Na **konfiguracji** wybierz pozycję **Zamknij** aby zakończyć pracę kreatora.  

    > [!NOTE]  
    >  Na pasku tytułu konsoli programu Configuration Manager, który jest połączony z lokacją, którą można uaktualnić może wskazywać, że lokacja jest wciąż wersji ewaluacyjnej do momentu ponownego podłączenia konsoli do lokacji.  
