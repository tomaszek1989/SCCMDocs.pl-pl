---
title: "Atualizar e extinguir aplicações | Microsoft Docs"
description: "Rever, substituir ou desinstalar aplicações implementadas através do System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68ac8a07-8e54-4a3c-91e3-e50dc1cabf5d
caps.latest.revision: "9"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 805e04c447747b4d12350b692880dbc005bd7168
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2017
---
# <a name="update-and-retire-applications-with-system-center-configuration-manager"></a>Atualizar e extinguir aplicações com o System Center Configuration Manager

*Aplica-se a: O System Center Configuration Manager (ramo atual)*


É provável que, eventualmente, poderá ser útil efetuar alterações a uma aplicação, desinstalar uma aplicação ou substituir uma aplicação já implementada por uma nova aplicação. System Center Configuration Manager dá-lhe estas capacidades, para o ajudar a atualizar e extinguir aplicações:  

-   **Rever aplicações**. Quando fizer alterações a uma aplicação ou um tipo de implementação, o Configuration Manager mantém um histórico de alterações. Pode reverter a aplicação para uma revisão anterior em qualquer altura. Também pode ver as respetivas propriedades, restaurar uma revisão anterior de uma aplicação ou eliminar uma revisão antiga.  

  Para obter mais informações, consulte [revisões de aplicações](revise-and-supersede-applications.md#application-revisions).  

-   **Substituir aplicações**. Pode atualizar ou substituir as aplicações existentes utilizando uma relação de substituição. Se substituir uma aplicação, pode especificar um novo tipo de implementação para substituir o tipo de implementação da aplicação substituída. Além disso, pode definir se atualizar ou desinstalar a aplicação substituída antes da aplicação substituta está instalado.  

  Para obter mais informações, consulte [substituição de aplicações](revise-and-supersede-applications.md#application-supersedence).  

-   **Desinstalar aplicações**. Gestor de configuração facilita a desinstalação de uma aplicação fácil. Isto pode ser conseguido de forma silenciosa, sem qualquer intervenção do utilizador do dispositivo ou aplicação.  

  Para obter mais informações, consulte [desinstalar aplicações](uninstall-applications.md).  
