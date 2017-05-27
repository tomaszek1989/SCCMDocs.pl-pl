---
title: "Zarządzanie pakietami uaktualnienia systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie zarządzania pakietami uaktualnienia systemu operacyjnego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: 5fef04f26b12bced073332fd1f7b4e7c7bd7d398
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>Zarządzanie pakietami uaktualnień systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Pakiet uaktualnienia w programie System Center Configuration Manager zawiera pliki źródłowe Instalatora systemu Windows, które są używane do uaktualniania istniejącego systemu operacyjnego na komputerze. Użyj następujących sekcji Zarządzanie pakietami uaktualnienia systemu operacyjnego w programie Configuration Manager.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Dodawanie pakietów uaktualnień systemu operacyjnego do programu Configuration Manager  
 Przed użyciem pakiet uaktualnienia systemu operacyjnego, należy dodać pakiet do lokacji programu Configuration Manager. Aby dodać pakiet aktualizacji systemu operacyjnego, należy wykonać poniższą procedurę.  

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
 Dystrybuowanie obrazów systemu operacyjnego do punktów dystrybucji przebiega tak samo jak w przypadku zawartości innego typu. W większości przypadków przed wdrożeniem systemu operacyjnego musisz przeprowadzić dystrybucję obrazu systemu operacyjnego do co najmniej jednego punktu dystrybucji. Aby zapoznać się z procedurą dystrybucji obrazu systemu operacyjnego, zobacz temat [Dystrybucja zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Stosowanie aktualizacji oprogramowania do pakietów uaktualnień systemu operacyjnego  
 Począwszy od programu Configuration Manager w wersji 1602, można stosować nowe aktualizacje oprogramowania do obrazu systemu operacyjnego w pakiecie uaktualnienia systemu operacyjnego. Przed zainstalowaniem aktualizacji oprogramowania do pakiet uaktualniający, który musi mieć oprogramowanie aktualizacji infrastruktury, w miejscu, pomyślnie zsynchronizowane aktualizacje oprogramowania i pobrać aktualizacje oprogramowania do biblioteki zawartości na serwerze lokacji. Aby uzyskać więcej informacji, zobacz [wdrażania aktualizacji oprogramowania](../../sum/deploy-use/deploy-software-updates.md).  

 Odpowiednie aktualizacje oprogramowania można stosować do pakietu uaktualnienia zgodnie z zaplanowanym harmonogramem. Zgodnie z harmonogramem określonym przez użytkownika programu Configuration Manager dotyczą aktualizacji oprogramowania, które można wybrać pakiet uaktualnienia systemu operacyjnego, a następnie opcjonalnie dystrybuuje zaktualizowany pakiet uaktualniający do punktów dystrybucji. Informacje o pakiecie uaktualnienia systemu operacyjnego, w tym informacje o aktualizacjach oprogramowania zastosowanych podczas importu, są przechowywane w bazie danych lokacji. W bazie danych lokacji są także przechowywane informacje o aktualizacjach oprogramowania zastosowanych do pakietu uaktualnienia od jego pierwszego dodania. Po uruchomieniu kreatora w celu zastosowania aktualizacji oprogramowania do pakietu uaktualnienia obrazu systemu operacyjnego kreator pobiera listę dostępnych do wyboru aktualizacji, które nie zostały jeszcze zastosowane do pakietu uaktualnienia. Dotyczy aktualizacji oprogramowania pakiet uaktualnienia systemu operacyjnego i kopiuje aktualizacje oprogramowania z biblioteki zawartości na serwerze lokacji programu Configuration Manager.  

 Aby zastosować aktualizację oprogramowania do pakietu uaktualnienia systemu operacyjnego, należy wykonać poniższą procedurę.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>Aby zastosować aktualizacje oprogramowania do pakietów uaktualnienia obrazu systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Pakiety uaktualnień systemu operacyjnego**.  

3.  Wybierz pakiet uaktualnienia obrazu systemu operacyjnego, do którego mają zostać zastosowane aktualizacje oprogramowania.  

4.  Na karcie **Narzędzia główne** w grupie **Pakiety uaktualnień systemu operacyjnego** kliknij polecenie **Zaplanuj aktualizacje** , aby uruchomić kreatora.  

5.  Na stronie **Wybierz aktualizacje** wybierz aktualizacje oprogramowania, które mają zostać zastosowane do obrazu systemu operacyjnego, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Ustawianie harmonogramu** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Harmonogram**: Wybierz harmonogram stosowania aktualizacji oprogramowania do obrazu systemu operacyjnego.  

    2.  **Kontynuuj przy błędzie**:  Wybierz tę opcję, aby kontynuować stosowanie aktualizacji oprogramowania do obrazu nawet po wystąpieniu błędu.  

    3.  **Rozpraszanie obrazu do punktów dystrybucji**: Wybierz tę opcję, aby zaktualizować obraz systemu operacyjnego na punktach dystrybucji po zastosowaniu aktualizacji oprogramowania.  

7.  Na stronie **Podsumowanie** sprawdź informacje, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Ukończenie** sprawdź, czy aktualizacje oprogramowania zostały pomyślnie zastosowane do obrazu systemu operacyjnego.  

