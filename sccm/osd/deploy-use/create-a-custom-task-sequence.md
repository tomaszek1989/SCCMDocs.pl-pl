---
title: "Utwórz niestandardową sekwencję zadań | Dokumentacja firmy Microsoft"
description: "Edytuj niestandardową sekwencję zadań w programie System Center Configuration Manager do dodawania kroków do sekwencji zadań."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 03c844084c72fc52806123d9f4c11a410a3ec775
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-custom-task-sequence-with-system-center-configuration-manager"></a>Utwórz niestandardową sekwencję zadań z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podczas tworzenia niestandardowej sekwencji zadań w programie System Center Configuration Manager zawiera nie kroków sekwencji zadań. Po utworzeniu sekwencji zadań należy ją edytować i dodać potrzebne kroki sekwencji zadań.  

##  <a name="BKMK_CustomTS"></a> Tworzenie niestandardowej sekwencji zadań  
 Poniższa procedura umożliwia utworzenie niestandardowej sekwencji zadań.  

#### <a name="to-create-a-custom-task-sequence"></a>Aby utworzyć niestandardową sekwencję zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** wybierz opcję **Utwórz nową niestandardową sekwencję zadań**.  

5.  Na stronie **Informacje o sekwencji zadań** określ nazwę i opis sekwencji zadań oraz opcjonalny obraz rozruchowy używany przez daną sekwencję, a następnie ukończ pracę kreatora.  

 Po ukończeniu Kreatora tworzenia sekwencji zadań programu Configuration Manager dodaje niestandardową sekwencję zadań do **sekwencji zadań** węzła. W tym momencie można edytować sekwencję zadań, aby dodać do niej kroki  

 Lista kroków sekwencji zadań dostępnych w temacie [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

 Aby uzyskać więcej informacji dotyczących sposobu edytowania sekwencji zadań, zobacz [edytować sekwencję zadań](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 W większości przypadków sekwencje zadań będą używane do automatyzowania zadań wdrażania systemu operacyjnego, ale można utworzyć niestandardową sekwencję zadań, która umożliwi zautomatyzowanie wielu różnych zadań. Aby uzyskać więcej informacji, zobacz [tworzenia sekwencji zadań dla wdrożeń systemu operacyjnego](create-a-task-sequence-for-non-operating-system-deployments.md).  

 ## <a name="next-steps"></a>Następne kroki
 [Wdrożenie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)

