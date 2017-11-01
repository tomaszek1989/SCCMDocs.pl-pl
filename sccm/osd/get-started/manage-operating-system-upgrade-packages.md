---
title: "Zarządzanie pakietami uaktualnień systemu operacyjnego"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzać pakietami uaktualnień systemu operacyjnego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: "12"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e0996f57d7d9fbcb9926c16f718b65073c78b3bc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>Zarządzanie pakietami uaktualnień systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Pakiet uaktualnienia w programie System Center Configuration Manager zawiera pliki źródłowe Instalatora systemu Windows, które są używane do uaktualniania istniejącego systemu operacyjnego na komputerze. Użyj następujących sekcji, aby zarządzać pakietami uaktualnień systemu operacyjnego w programie Configuration Manager.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Dodawanie pakietów uaktualnień systemu operacyjnego do programu Configuration Manager  
 Przed użyciem pakietu uaktualnienia systemu operacyjnego, należy dodać pakietu do lokacji programu Configuration Manager. Aby dodać pakiet aktualizacji systemu operacyjnego, należy wykonać poniższą procedurę.  

#### <a name="to-add-an-operating-system-upgrade-package"></a>Aby dodać pakiet uaktualnienia systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Pakiety uaktualnień systemu operacyjnego**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj pakiet uaktualnienia systemu operacyjnego** , aby uruchomić Kreatora dodawania pakietu uaktualnienia systemu operacyjnego.  

4.  Na stronie **Źródło danych** określ ścieżkę sieciową do instalacyjnych plików źródłowych pakietu uaktualnienia systemu operacyjnego. Aby wskazać lokalizację instalacyjnych plików źródłowych, wpisz na przykład ścieżkę UNC **\\\serwer\ścieżka** .  

    > [!NOTE]  
    >  Pliki źródłowe instalacji obejmują plik Setup.exe oraz inne pliki i foldery służące do instalowania systemu operacyjnego.  

    > [!IMPORTANT]  
    >  Aby zapobiec niepożądanemu modyfikowaniu plików źródłowych instalacji, ogranicz dostęp do tych plików.  

5.  Na stronie **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Dalej**. Te informacje przydają się do identyfikacji, jeśli istnieje wiele instalatorów systemu operacyjnego.  

    -   **Nazwa**: Określ nazwę Instalatora systemu operacyjnego.  

    -   **Wersja**: Określ wersję Instalatora systemu operacyjnego.  

    -   **Komentarz**: Podaj krótki opis Instalatora systemu operacyjnego.  

6.  Ukończ pracę kreatora.  

 Teraz można dokonać dystrybucji instalatora systemu operacyjnego do punktów dystrybucji, do których dostęp uzyskują sekwencje zadań wdrażania.  

##  <a name="BKMK_DistributeBootImages"></a> Dystrybuowanie obrazów systemu operacyjnego do punktu dystrybucji  
 Dystrybuowanie obrazów systemu operacyjnego do punktów dystrybucji przebiega tak samo jak w przypadku zawartości innego typu. W większości przypadków przed wdrożeniem systemu operacyjnego musisz przeprowadzić dystrybucję obrazu systemu operacyjnego do co najmniej jednego punktu dystrybucji. Aby zapoznać się z procedurą dystrybucji obrazu systemu operacyjnego, zobacz temat [Dystrybucja zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Stosowanie aktualizacji oprogramowania do pakietów uaktualnień systemu operacyjnego  
 Począwszy od programu Configuration Manager w wersji 1602, można stosować nowe aktualizacje oprogramowania do obrazu systemu operacyjnego do pakietu uaktualnienia systemu operacyjnego. Przed zainstalowaniem aktualizacji oprogramowania do pakietu uaktualnienia, który musi mieć oprogramowanie aktualizacji infrastruktury w miejscu, pomyślnie zsynchronizować aktualizacje oprogramowania i pobrane aktualizacje oprogramowania do biblioteki zawartości na serwerze lokacji. Aby uzyskać więcej informacji, zobacz [wdrażania aktualizacji oprogramowania](../../sum/deploy-use/deploy-software-updates.md).  

 Odpowiednie aktualizacje oprogramowania można stosować do pakietu uaktualnienia zgodnie z zaplanowanym harmonogramem. Zgodnie z harmonogramem określonym przez użytkownika programu Configuration Manager stosuje aktualizacje oprogramowania, które należy wybrać pakiet uaktualnienia systemu operacyjnego, a następnie opcjonalnie dystrybuuje zaktualizowany pakiet uaktualnienia do punktów dystrybucji. Informacje o pakiecie uaktualnienia systemu operacyjnego, w tym informacje o aktualizacjach oprogramowania zastosowanych podczas importu, są przechowywane w bazie danych lokacji. W bazie danych lokacji są także przechowywane informacje o aktualizacjach oprogramowania zastosowanych do pakietu uaktualnienia od jego pierwszego dodania. Po uruchomieniu kreatora w celu zastosowania aktualizacji oprogramowania do pakietu uaktualnienia obrazu systemu operacyjnego kreator pobiera listę dostępnych do wyboru aktualizacji, które nie zostały jeszcze zastosowane do pakietu uaktualnienia. Configuration Manager kopiuje aktualizacje oprogramowania z biblioteki zawartości na serwerze lokacji i stosuje aktualizacje oprogramowania do pakietu uaktualnienia systemu operacyjnego.  

 Aby zastosować aktualizację oprogramowania do pakietu uaktualnienia systemu operacyjnego, należy wykonać poniższą procedurę.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>Aby zastosować aktualizacje oprogramowania do pakietów uaktualnienia obrazu systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Pakiety uaktualnień systemu operacyjnego**.  

3.  Wybierz pakiet uaktualnienia obrazu systemu operacyjnego, do którego mają zostać zastosowane aktualizacje oprogramowania.  

4.  Na karcie **Narzędzia główne** w grupie **Pakiety uaktualnień systemu operacyjnego** kliknij polecenie **Zaplanuj aktualizacje** , aby uruchomić kreatora.  

5.  Na stronie **Wybierz aktualizacje** wybierz aktualizacje oprogramowania, które mają zostać zastosowane do obrazu systemu operacyjnego, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Ustawianie harmonogramu** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Harmonogram**: Określ harmonogram stosowania aktualizacji oprogramowania do obrazu systemu operacyjnego.  

    2.  **Kontynuuj przy błędzie**:  Wybierz tę opcję, aby kontynuować stosowanie aktualizacji oprogramowania do obrazu nawet wtedy, gdy występuje błąd.  

    3.  **Dokonaj dystrybucji obrazu do punktów dystrybucji**: Wybierz tę opcję, aby zaktualizować obraz systemu operacyjnego w punktach dystrybucji po zastosowaniu aktualizacji oprogramowania.  

7.  Na stronie **Podsumowanie** sprawdź informacje, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Ukończenie** sprawdź, czy aktualizacje oprogramowania zostały pomyślnie zastosowane do obrazu systemu operacyjnego.  
