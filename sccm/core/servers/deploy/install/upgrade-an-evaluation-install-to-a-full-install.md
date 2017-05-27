---
title: Uaktualnienie instaluje oceny | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak uaktualnienie instalacji wersji ewaluacyjnej do pełnej instalacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d1bf0fdc3e735eb31492476fd46f008620150c0b
ms.openlocfilehash: 8f951805c2fc25059965c15c94934c0f8546735c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>Uaktualnienie instalacji wersji ewaluacyjnej programu System Center Configuration Manager do pełnej instalacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zainstalowaniu programu System Center Configuration Manager w wersji próbnej, po upływie 180 dni konsola programu Configuration Manager staje się tylko do odczytu do momentu aktywowania produktu na **Obsługa lokacji** w Instalatorze. W dowolnym momencie przed lub po upływie 180-dniowego okresu masz możliwość uaktualnienie instalacji wersji ewaluacyjnej do pełnej instalacji.  

> [!NOTE]  
>  Po podłączeniu konsoli programu Configuration Manager do instalacji programu Configuration Manager w wersji ewaluacyjnej na pasku tytułowym konsoli wyświetlana liczba dni pozostałych do wygaśnięcia wersji próbnej. Liczba dni nie będzie odświeżana automatycznie i aktualizuje tylko podczas tworzenia nowego połączenia z lokacją.  

 Można uaktualnić następujące witryny, które uruchom instalację w wersji ewaluacyjnej:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  

Ponieważ Lokacje dodatkowe nie są traktowane jako instalacje wersji ewaluacyjnej, nie ma potrzeby modyfikowania lokacji dodatkowej po uaktualnieniu lokacji głównej nadrzędnej do pełnej instalacji.  

Wymagania wstępne dotyczące uaktualniania do wersji licencjonowanej wersji ewaluacyjnej:  

-   Musi mieć prawidłowy produktu do użycia podczas uaktualniania.  
-   Konto musi mieć **administratora** praw na komputerze, na którym zainstalowano lokację.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>Aby uaktualnić wersję ewaluacyjną programu Configuration Manager do wersji licencjonowanej  

1.  Na serwerze lokacji Uruchom **Setup.exe** (Instalator programu Configuration Manager) z folderu instalacyjnego programu Configuration Manager (**%path%\BIN\X64**). Należy uruchomić kopię Instalatora zlokalizowaną na serwerze lokacji w folderze programu Configuration Manager, ponieważ opcje obsługi lokacji nie są dostępne po uruchomieniu Instalatora z nośnika instalacyjnego.  
2.  Na **przed rozpoczęciem** wybierz opcję **dalej**.  
3.  Na **wprowadzenie** wybierz opcję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie wybierz **dalej**.  
4.  Na **Obsługa lokacji** wybierz opcję **uaktualnienia wersji ewaluacyjnej do wersji licencjonowanej**, wprowadź prawidłowy klucz produktu, a następnie wybierz **dalej**.  
5.  Na **postanowień licencyjnych dotyczących oprogramowania Microsoft** strony, przeczytaj i zaakceptuj postanowienia licencyjne, a następnie wybierz **dalej**.  
6.  Na **konfiguracji** wybierz opcję **Zamknij** aby zakończyć pracę kreatora.  

    > [!NOTE]  
    >  Na pasku tytułu konsoli programu Configuration Manager, który pozostanie połączony z lokacją, do której należy uaktualnić może wskazywać, że witryna jest nadal wersji ewaluacyjnej do momentu ponownego podłączenia konsoli do lokacji.  

