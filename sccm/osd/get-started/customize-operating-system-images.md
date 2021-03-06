---
title: 'Dostosowanie obrazów systemu operacyjnego '
titleSuffix: Configuration Manager
description: Aby dostosować obraz systemu operacyjnego, należy użyć sekwencji zadań do przechwytywania i kompilacji, konfiguracja ręczna lub obie te grupy.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 95033a9b-ff13-4b70-b1de-bcb25bcb6024
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b9a3f4583944f0818f74930753bad99e3408a928
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="customize-operating-system-images-with-system-center-configuration-manager"></a>Dostosowanie obrazów systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Obrazy systemu operacyjnego w programie System Center Configuration Manager to pliki WIM, stanowiące skompresowaną kolekcję plików i folderów, które są wymagane do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze odniesienia. Niestandardowy obraz systemu operacyjnego jest tworzony na komputerze odniesienia skonfigurowanym przy użyciu wszystkich wymaganych plików systemu operacyjnego, plików obsługi, aktualizacji oprogramowania, narzędzi i innych aplikacji. Następnie jest z niego przechwytywany. Zakres ręcznego konfigurowania komputera odniesienia zależy od użytkownika. Konfigurację komputera odniesienia można całkowicie zautomatyzować, korzystając z sekwencji zadań tworzenia i przechwytywania. Można ręcznie skonfigurować określone aspekty komputera odniesienia, a następnie skonfigurować pozostałe, korzystając z sekwencji zadań. Inna możliwość to ręczne skonfigurowanie komputera odniesienia bez użycia sekwencji zadań. Poniższe sekcje umożliwiają dostosowanie systemu operacyjnego.

##  <a name="BKMK_PrepareReferenceComputer"></a> Przygotuj się do komputera odniesienia  
 Przed przechwyceniem obrazu systemu operacyjnego z komputera odniesienia należy uwzględnić kilka kwestii.  

###  <a name="BKMK_RefComputerDecide"></a> Wybieranie konfiguracji automatycznej lub ręcznej  
 Poniżej przedstawiono zalety i wady zautomatyzowanej oraz ręcznej konfiguracji komputera odniesienia.  

#### <a name="automated-configuration"></a>Konfiguracja zautomatyzowana  
 **Zalety**  

-   Konfiguracja może być całkowicie nienadzorowana, co eliminuje konieczność obecności administratora lub użytkownika.  

-   Sekwencji zadań można użyć ponownie do bezpiecznego powtórzenia konfiguracji dodatkowych komputerów odniesienia.  

-   Sekwencję zadań można zmodyfikować w celu uwzględnienia różnic między komputerami odniesienia bez konieczności ponownego tworzenia całej sekwencji zadań.  

 **Wady**  

-   Pierwsze utworzenie i przetestowanie sekwencji zadań może zająć dużo czasu.  

-   Jeżeli wymagania dotyczące komputera odniesienia znacznie się zmienią, ponowne utworzenie i przetestowanie sekwencji zadań może zająć dużo czasu.  

#### <a name="manual-configuration"></a>Konfiguracja ręczna  
 **Zalety**  

-   Nie jest konieczne tworzenie sekwencji zadań ani jej testowanie i rozwiązywanie problemów.  

-   Możesz zainstalować bezpośrednio z dysków CD bez umieszczania wszystkich pakietów oprogramowania (w tym systemu Windows), w pakiecie programu Configuration Manager.  

 **Wady**  

-   Dokładność konfiguracji komputera odniesienia zależy od administratora lub użytkownika, który konfiguruje komputer.  

-   Należy dokładnie sprawdzić i przetestować konfigurację komputera odniesienia.  

-   Tej metody konfiguracji nie można użyć ponownie.  

-   Cały proces wymaga aktywnego udziału użytkownika.  

###  <a name="BKMK_RefComputerConsiderations"></a> Uwagi dotyczące komputera odniesienia  
 Poniżej zawarto podstawowe elementy, które należy uwzględnić podczas konfigurowania komputera odniesienia.  

-   **Wdrażany system operacyjny**  

     Na komputerze odniesienia musi być zainstalowany system operacyjny, który ma zostać wdrożony na komputerach docelowych. Aby uzyskać więcej informacji o systemach operacyjnych, które można wdrożyć, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Odpowiedni dodatek service pack**  

     Na komputerze odniesienia musi być zainstalowany system operacyjny, który ma zostać wdrożony na komputerach docelowych.  

-   **Odpowiednie aktualizacje oprogramowania**  

     Należy zainstalować wszystkie aplikacje, które mają zostać uwzględnione w obrazie systemu operacyjnego przechwytywanego z komputera odniesienia. Aplikacje można także zainstalować po wdrożeniu przechwyconego obrazu systemu operacyjnego na komputerach docelowych.  

-   **Członkostwo w grupie roboczej**  

     Komputer odniesienia musi być skonfigurowany jako członek grupy roboczej.  

-   **Narzędzie Sysprep**  

     Narzędzie Przygotowanie Systemu (Sysprep) to technologia, której można użyć z innymi narzędziami wdrażania w celu instalacji systemów operacyjnych Windows na nowych urządzeniach. Program Sysprep przygotowuje komputer do utworzenia obrazu dysku lub dostawy do klienta przez skonfigurowanie komputera w celu utworzenia nowego identyfikatora zabezpieczeń (SID) komputera po jego ponownym uruchomieniu. Ponadto program Sysprep usuwa ustawienia oraz dane specyficzne dla użytkownika i komputera, których nie należy kopiować na komputer docelowy.  

     Narzędzie Sysprep można ręcznie zastosować na komputerze odniesienia, uruchamiając następujące polecenie:  

     `Sysprep /quiet /generalize /reboot`  

     Opcja /generalize powoduje, że program Sysprep usuwa dane specyficzne dla systemu z instalacji systemu Windows. Informacje specyficzne dla systemu obejmują dzienniki zdarzeń, unikatowe identyfikatory zabezpieczeń (SID) i inne unikatowe informacje. Po usunięciu unikatowych informacji o systemie nastąpi ponowne uruchomienie komputera.  

     Działanie programu Sysprep można zautomatyzować, korzystając z sekwencji zadań [Przygotowanie systemu Windows do przechwycenia](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) lub nośnika przechwytywania.  

    > [!IMPORTANT]  
    >  Przed uruchomieniem programu Sysprep sekwencja zadań [Przygotowanie systemu Windows do przechwycenia](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) próbuje zresetować lokalne hasło administratora na komputerze odniesienia do pustej wartości. Jeżeli zasada zabezpieczeń lokalnych **Hasło musi spełniać wymagania co do złożoności** jest włączona, ta sekwencja zadań nie będzie mogła zresetować hasła administratora. W tym scenariuszu należy wyłączyć tę zasadę przed uruchomieniem sekwencji zadań.  

     Aby uzyskać więcej informacji o programie Sysprep, zobacz [Informacje techniczne dotyczące narzędzia do przygotowywania systemu (Sysprep)](http://go.microsoft.com/fwlink/?LinkId=280286).  

-   **Odpowiednie narzędzia i skrypty wymagane do skorygowania scenariuszy instalacji**  

     Odpowiednie narzędzia i skrypty wymagane do skorygowania scenariuszy instalacji  

-   **Odpowiednie dostosowanie pulpitu, takie jak tapetę, znakowanie i domyślnego profilu użytkownika**  

     Na komputerze odniesienia można skonfigurować właściwości pulpitu, które mają zostać uwzględnione przy przechwytywaniu obrazu systemu operacyjnego z komputera odniesienia. Właściwości pulpitu obejmują tapetę, znakowanie organizacji i standardowy domyślny profil użytkownika.  

##  <a name="BKMK_ManuallyBuildReference"></a> Ręcznie utworzyć komputer odniesienia  
 Użyj następującej procedury, aby ręcznie utworzyć komputer odniesienia.  

> [!NOTE]  
>  Jeśli komputer odniesienia jest tworzony ręcznie, możesz przechwycić obraz systemu operacyjnego przy użyciu nośnika przechwytywania. Aby uzyskać więcej informacji, zobacz [Tworzenie nośnika przechwytywania](../deploy-use/create-capture-media.md).  

#### <a name="to-manually-build-the-reference-computer"></a>Aby ręcznie utworzyć komputer odniesienia  

1.  Zidentyfikuj komputer, który będzie używany jako komputer referencyjny.  

2.  Skonfiguruj komputer referencyjny przy użyciu odpowiedniego systemu operacyjnego i dowolnego innego oprogramowania, które jest wymagane do utworzenia obrazu systemu operacyjnego w celu wdrożenia.  

    > [!WARNING]  
    >  Zainstaluj co najmniej odpowiedni system operacyjny i dodatek Service Pack, sterowniki pomocnicze i wymagane aktualizacje oprogramowania.  

3.  Skonfiguruj komputer referencyjny jako element członkowski grupy roboczej.  

4.  Zresetuj hasło administratora lokalnego na komputerze referencyjnym, aby hasło miało pustą wartość.  

5.  Uruchom program Sysprep przy użyciu polecenia: **sysprep /quiet /generalize /reboot**. Opcja /generalize powoduje, że program Sysprep usuwa dane specyficzne dla systemu z instalacji systemu Windows. Informacje specyficzne dla systemu obejmują dzienniki zdarzeń, unikatowe identyfikatory zabezpieczeń (SID) i inne unikatowe informacje. Po usunięciu unikatowych informacji o systemie nastąpi ponowne uruchomienie komputera.  

 Po przygotowaniu komputera odniesienia należy użyć sekwencji zadań do przechwycenia z niego obrazu systemu operacyjnego.  Szczegółowe kroki przedstawiono w temacie [Przechwytywanie obrazu systemu operacyjnego z istniejącego komputera odniesienia](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_CaptureExistingRefComputer).  

##  <a name="BKMK_UseTSToBuildReference"></a> Za pomocą sekwencji zadań do utworzenia komputera odniesienia  
 Proces tworzenia komputera odniesienia można zautomatyzować, używając sekwencji zadań wdrażającej system operacyjny, sterowniki, aplikacje itd.  Użyj kroków poniżej, aby utworzyć komputer odniesienia, a następnie przechwycić obraz systemu operacyjnego z komputera odniesienia.  

-   Użyj sekwencji zadań, aby utworzyć i przechwycić obraz systemu operacyjnego z komputera odniesienia.  Szczegółowe kroki przedstawiono w temacie [Tworzenie i przechwytywanie komputera odniesienia przy użyciu sekwencji zadań](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_BuildCaptureTS).  
