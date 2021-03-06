---
title: Tworzenie niestandardowej sekwencji zadań
titleSuffix: Configuration Manager
description: Edytuj niestandardową sekwencję zadań programu System Center Configuration Manager możesz dodać kroki do sekwencji zadań.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e5a0e6d8066fc52bf64dd4e53eba4c4dc1c84aa6
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-custom-task-sequence-with-system-center-configuration-manager"></a>Tworzenie niestandardowej sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas tworzenia niestandardowej sekwencji zadań w programie System Center Configuration Manager zawiera ona nie kroków sekwencji zadań. Po utworzeniu sekwencji zadań należy ją edytować i dodać potrzebne kroki sekwencji zadań.  

##  <a name="BKMK_CustomTS"></a> Tworzenie niestandardowej sekwencji zadań  
 Poniższa procedura umożliwia utworzenie niestandardowej sekwencji zadań.  

#### <a name="to-create-a-custom-task-sequence"></a>Aby utworzyć niestandardową sekwencję zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** wybierz opcję **Utwórz nową niestandardową sekwencję zadań**.  

5.  Na stronie **Informacje o sekwencji zadań** określ nazwę i opis sekwencji zadań oraz opcjonalny obraz rozruchowy używany przez daną sekwencję, a następnie ukończ pracę kreatora.  

 Po zakończeniu pracy Kreatora tworzenia sekwencji zadań, programu Configuration Manager dodaje niestandardową sekwencję zadań do **sekwencje zadań** węzła. W tym momencie można edytować sekwencję zadań, aby dodać do niej kroki  

 Aby uzyskać listę dostępnych kroków sekwencji zadań, zobacz [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

 Aby uzyskać więcej informacji o sposobie edytowania sekwencji zadań, zobacz [edytowania sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 W większości przypadków sekwencje zadań będą używane do automatyzowania zadań wdrażania systemu operacyjnego, ale można utworzyć niestandardową sekwencję zadań, która umożliwi zautomatyzowanie wielu różnych zadań. Aby uzyskać więcej informacji, zobacz [tworzenia sekwencji zadań wdrożeń systemu operacyjnego](create-a-task-sequence-for-non-operating-system-deployments.md).  

 ## <a name="next-steps"></a>Następne kroki
 [Wdrożenie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)
