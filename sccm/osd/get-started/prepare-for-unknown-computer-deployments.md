---
title: "Przygotowywanie do wdrażania nieznanych komputerów | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania systemów operacyjnych na komputerach, które nie są zarządzane przez program Configuration Manager w środowisku programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e447e34-0943-49ed-b6ba-3efebf3566c1
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 445e76950f0605da917f3d0e7e71557d969e3c2d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-for-unknown-computer-deployments-in-system-center-configuration-manager"></a>Przygotowywanie do wdrożenia na nieznanych komputerach w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do wdrażania systemów operacyjnych na nieznanych komputerach w środowisku programu System Center Configuration Manager, skorzystaj z informacji w tym temacie. Nieznany komputer to komputer, który nie jest zarządzany przez program Configuration Manager. Oznacza to, że nie ma rekordów tych komputerów w bazie danych programu Configuration Manager. Nie rozpoznano następujących komputerów:  

-   Komputer, na którym nie zainstalowano klienta programu Configuration Manager  

-   Komputer, który nie jest importowany do programu Configuration Manager  

-   Komputer, który jest nie zostały odnalezione przez program Configuration Manager  

 Systemy operacyjne można wdrażać na nieznanych komputerach przy użyciu następujących metod wdrażania:  

-   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)  

-   [Wdrażanie systemu operacyjnego przy użyciu nośnika rozruchowego](../deploy-use/create-bootable-media.md)  

-   [Użyj wstępnie przygotowanego nośnika do wdrażania systemu operacyjnego](../deploy-use/create-prestaged-media.md)  

## <a name="unknown-computer-deployment-workflow"></a>Przepływ pracy wdrożenia na nieznanym komputerze  
 Poniżej przedstawiono podstawowy przepływ pracy wdrażania systemu operacyjnego na nieznanym komputerze:  

-   Wybierz obiekt nieznanego komputera w celu użycia we wdrożeniu. System operacyjny można wdrożyć na jednym z obiektów nieznanych komputerów w kolekcji **Wszystkie nieznane komputery** . Można także dodać obiekty z kolekcji **Wszystkie nieznane komputery** do innej kolekcji. Configuration Manager udostępnia dwa obiekty nieznanych komputerów w **wszystkie nieznane komputery** kolekcji. Jeden z obiektów jest przeznaczony dla komputerów x86, a drugi dla komputerów x64.  

    > [!NOTE]  
    >  Obiekt **Nieznany komputer x86** jest przeznaczony dla komputerów, które obsługują tylko architekturę x86. Obiekt **Nieznany komputer x64** jest przeznaczony dla komputerów, które obsługują architektury x86 i x64. Mówiąc inaczej, te obiekty opisują architekturę komputera docelowego. Nie opisują one systemu operacyjnego, który ma zostać wdrożony na komputerze docelowym.  

-   Skonfiguruj punkt dystrybucji lub utwórz nośnik z włączoną obsługą środowiska PXE w celu obsługi wdrożeń na nieznanych komputerach.  

-   Wdróż sekwencję zadań w celu wdrożenia systemu operacyjnego.  

## <a name="unknown-computer-installation-process"></a>Proces instalacji nieznanego komputera  
 Po pierwszym uruchomieniu komputera, przy użyciu środowiska PXE lub nośnika, programu Configuration Manager sprawdza, czy rekord tego komputera istnieje w bazie danych programu Configuration Manager. W przypadku rekordu, programu Configuration Manager sprawdza czy sekwencji zadań wdrożonych dla tego rekordu. Jeśli nie jest rekordem, programu Configuration Manager sprawdza, czy istnieją wszystkie sekwencji zadań wdrożonych dla obiekt nieznanego komputera. W obu przypadkach programu Configuration Manager wykonuje następnie jedną z następujących czynności:  

-   Jeśli istnieje dostępna sekwencja zadań, programu Configuration Manager monituje użytkownika o uruchomienie sekwencji zadań.  

-   Jeśli istnieje wymagana sekwencja zadań, programu Configuration Manager automatycznie uruchamia sekwencję zadań.  

-   Jeśli sekwencja zadań nie została wdrożona dla rekordu, program Configuration Manager generuje błąd, o braku wdrożonej sekwencji zadań na komputerze docelowym.  

 Po uruchomieniu nieznanego komputera programu Configuration Manager rozpoznaje komputer jako nieudostępniany, a nie na nieznanym komputerze. Oznacza to, że komputer otrzyma teraz sekwencje zadań wdrożone dla obiektu nieznanego komputera. Następnie wdrożona sekwencja zadań instaluje obraz systemu operacyjnego, który musi zawierać klienta programu Configuration Manager.  

 Po zainstalowaniu klienta programu Configuration Manager, zostaje utworzony rekord komputera, a komputer zostaje wyświetlony w odpowiedniej kolekcji programu Configuration Manager. Jeśli komputer nie powiedzie się do zainstalowania obrazu systemu operacyjnego lub klienta programu Configuration Manager, tworzony jest rekord "Nieznany" dla komputera, a komputer zostaje wyświetlony w **wszystkie systemy** kolekcji.  

> [!NOTE]  
>  Podczas instalacji obrazu systemu operacyjnego sekwencja zadań może pobrać zmienne kolekcji, ale nie zmienne tego komputera.  

##  <a name="BKMK_EnablingUnknown"></a> Włączanie obsługi nieznanych komputerów  
 Korzystając z poniższych informacji, można włączyć obsługę nieznanych komputerów podczas wdrażania systemu operacyjnego przy użyciu środowiska PXE, nośnika rozruchowego i wstępnie przygotowanego nośnika.  

-   **Opcja Opcja PXE**  

     Zaznacz pole wyboru **Włącz obsługę nieznanych komputerów** na karcie **PXE** dla punktu dystrybucji z włączoną obsługą środowiska PXE. Aby uzyskać więcej informacji, zobacz [Konfigurowanie punktów dystrybucji do akceptowania żądań PXE](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).  

-   **Nośnik rozruchowy**  

     Zaznacz pole wyboru **Włącz obsługę nieznanych komputerów** na stronie **Zabezpieczenia** w Kreatorze tworzenia nośnika sekwencji zadań. Aby uzyskać więcej informacji, zobacz [Konfigurowanie punktów dystrybucji do akceptowania żądań PXE](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint) i [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE w programie System Center Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

-   **Wstępnie przygotowany nośnik**  

     Zaznacz pole wyboru **Włącz obsługę nieznanych komputerów** na stronie **Zabezpieczenia** w Kreatorze tworzenia nośnika sekwencji zadań. Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie przygotowanego nośnika w programie System Center Configuration Manager](../deploy-use/create-prestaged-media.md).  
