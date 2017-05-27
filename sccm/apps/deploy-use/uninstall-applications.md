---
title: Odinstalowywanie aplikacji | Dokumentacja firmy Microsoft
description: "Odinstaluj aplikację za pomocą programu System Center Configuration Manager"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ea3edaa-27c6-4391-9896-cd97d9c5d06d
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2d0c0bc2e4e080e6061d8d3fe6cafd264d95c42a
ms.openlocfilehash: f42fee5974567f667c015a6b0bf34d9a9a7d2dab
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="uninstall-applications-with-system-center-configuration-manager"></a>Odinstalowywanie aplikacji z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Należy wykonać następujące czynności, aby odinstalować aplikację, którą wcześniej wdrożona.

-   Określ wiersz poleceń do odinstalowania zawartości typu wdrożenia na **zawartości** strona kreatora tworzenia typu wdrożenia.  

-   Wdróż aplikację za pomocą akcji wdrażania **Odinstaluj**.  

> [!IMPORTANT]  
> Aplikacje niektórych typów nie obsługują dezinstalacji.  

 Ta lista zawiera więcej informacji na temat sposobu działania Dezinstalacja aplikacji:  

-   Po odinstalowaniu aplikacji System Center Configuration Manager (Menedżer konfiguracji), wszystkie zależne aplikacje nie są automatycznie odinstalowywane.  

-   Należy wdrożyć aplikację, która wykorzystuje akcję **Odinstaluj** do użytkownika, a aplikacja została zainstalowana dla wszystkich użytkowników komputera, dezinstalacja może się nie powieść, jeśli konto użytkownika nie ma uprawnień do odinstalowania aplikacji.  

-   Po usunięciu użytkownika lub urządzenia z kolekcji, w której jest wdrożona aplikacja, aplikacja nie zostanie automatycznie usunięta z urządzenia.  

-   W przypadku wdrożenia z celem wdrożenia **Odinstaluj** nie są sprawdzane reguły wymagań. Jeśli aplikacja jest instalowana na komputerze, na którym jest uruchamiane wdrożenie, zostanie ona odinstalowana.  

> [!IMPORTANT]  
> Przed wdrożeniem aplikacji z akcją wdrożenia **Odinstaluj**należy usunąć z kolekcji wszystkie istniejące lub symulowane wdrożenia aplikacji.  

 Aby uzyskać więcej informacji na temat tworzenia typu wdrożenia, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).  

 Aby uzyskać więcej informacji o sposobie wdrażania aplikacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).  

## <a name="uninstall-an-application"></a>Odinstalowywanie aplikacji  

1.  Skonfiguruj typ wdrożenia aplikacji z poziomu wiersza poleceń do odinstalowania za pomocą jedną z następujących metod:  

    -   Na **ogólne** strona kreatora tworzenia wdrożenia, wybierz opcję **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych**. Jeśli informacje są dostępne w plikach instalacyjnych, wiersz poleceń do odinstalowania zostaje automatycznie dodany do właściwości typu wdrożenia.  

    -   Na **zawartości** strona kreatora tworzenia typu wdrożenia w **Odinstaluj program** Określ wiersz poleceń do odinstalowania aplikacji.  

        > [!NOTE]  
        >  **Zawartości** strona jest wyświetlana tylko wtedy, gdy zostanie wybrana opcja **ręcznie określić informacje o typie wdrożenia** na **ogólne** strona kreatora tworzenia typu wdrożenia.  

    -   Na **programy** na karcie  **<* Nazwa typu wdrożenia*> okno dialogowe Właściwości ** Określ wiersz poleceń do odinstalowania aplikacji w **Odinstaluj program** pola.  

2.  Wdrażanie aplikacji, a następnie wybierz akcję wdrożenia **Odinstaluj** na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania.  

    > [!NOTE]  
    >  Po wybraniu akcji wdrożenia **Odinstaluj**cel wdrożenia zostanie automatycznie skonfigurowany jako **Wymagany**.  

