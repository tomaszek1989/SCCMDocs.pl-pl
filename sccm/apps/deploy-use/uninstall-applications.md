---
title: Odinstalowywanie aplikacji
titleSuffix: Configuration Manager
description: Odinstaluj aplikację za pomocą programu System Center Configuration Manager
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 0ea3edaa-27c6-4391-9896-cd97d9c5d06d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7587fa6d96d6f8737921c9e5edae992cdd0ea614
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="uninstall-applications-with-system-center-configuration-manager"></a>Odinstalowywanie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Należy wykonać następujące czynności, aby odinstalować aplikację, którą wcześniej wdrożona.

-   Określ wiersz poleceń do odinstalowania zawartości typu wdrożenia na **zawartości** strony kreatora tworzenia typu wdrożenia.  

-   Wdróż aplikację za pomocą akcji wdrażania **Odinstaluj**.  

> [!IMPORTANT]  
> Aplikacje niektórych typów nie obsługują dezinstalacji.  

 Ta lista zawiera więcej informacji na temat działania Dezinstalacja aplikacji:  

-   Podczas dezinstalacji aplikacji programu System Center Configuration Manager (program Configuration Manager), wszystkie zależne aplikacje nie są automatycznie odinstalowywane.  

-   Jeśli wdrożyć aplikację, która wykorzystuje akcję **Odinstaluj** do użytkownika, a aplikacja została zainstalowana dla wszystkich użytkowników komputera, dezinstalacja może się nie powieść, jeśli konto użytkownika nie ma uprawnień umożliwiających odinstalowanie aplikacji.  

-   Usunięcie użytkownika lub urządzenia z kolekcji, która została wdrożona aplikacja, aplikacja nie zostanie automatycznie usunięta z urządzenia.  

-   W przypadku wdrożenia z celem wdrożenia **Odinstaluj** nie są sprawdzane reguły wymagań. Jeśli aplikacja jest instalowana na komputerze, na którym jest uruchamiane wdrożenie, zostanie ona odinstalowana.  

> [!IMPORTANT]  
> Przed wdrożeniem aplikacji z akcją wdrożenia **Odinstaluj**należy usunąć z kolekcji wszystkie istniejące lub symulowane wdrożenia aplikacji.  

 Aby uzyskać więcej informacji o sposobie tworzenia typu wdrożenia, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).  

 Aby uzyskać więcej informacji na temat sposobu wdrażania aplikacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).  

## <a name="uninstall-an-application"></a>Odinstalowywanie aplikacji  

1.  Skonfiguruj typ wdrożenia aplikacji z poziomu wiersza poleceń do odinstalowania za pomocą jedną z następujących metod:  

    -   Na **ogólne** strony kreatora tworzenia wdrożenia, wybierz opcję **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych**. Jeśli informacje są dostępne w plikach instalacyjnych, wiersz poleceń do odinstalowania zostaje automatycznie dodany do właściwości typu wdrożenia.  

    -   Na **zawartości** strony kreatora tworzenia typu wdrożenia w **program dezinstalacyjny** Określ wiersz poleceń do odinstalowania aplikacji.  

        > [!NOTE]  
        >  **Zawartości** strona jest wyświetlana tylko wtedy, gdy zostanie wybrana opcja **ręcznie określ informacje o typie wdrożenia** na **ogólne** strony kreatora tworzenia typu wdrożenia.  

    -   Na **programy** karcie  **< *Nazwa typu wdrożenia*> właściwości** oknie dialogowym Określ wiersz poleceń do odinstalowania aplikacji w  **Program dezinstalacyjny** pola.  

2.  Wdrażanie aplikacji, a następnie wybierz akcję wdrożenia **Odinstaluj** na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania.  

    > [!NOTE]  
    >  Po wybraniu akcji wdrożenia **Odinstaluj**cel wdrożenia zostanie automatycznie skonfigurowany jako **Wymagany**.  
