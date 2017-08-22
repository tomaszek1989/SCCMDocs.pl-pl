---
title: "Utworzyć podrzędne elementy konfiguracji | Dokumentacja firmy Microsoft"
description: "Utworzyć podrzędne elementy konfiguracji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>Jak utworzyć podrzędne elementy konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podrzędne elementy konfiguracji w programie System Center Configuration Manager to kopie elementów konfiguracji, które pozostają w relacji do oryginalnego elementu konfiguracji, w tym dziedziczą oryginalną konfigurację z nadrzędnego elementu konfiguracji.  

Podczas przeglądania właściwości podrzędnego elementu konfiguracji w konsoli programu Configuration Manager, nie można edytować dziedziczone obiekty i ustawienia oraz ich kryteria weryfikacji. Można natomiast dodawać, a następnie edytować dodatkowe kryteria weryfikacji do podrzędnego elementu konfiguracji, a nowe obiekty i ustawienia można również dodawać do podrzędnego elementu konfiguracji.
Typowym celem tworzenia i edytowania podrzędnego elementu konfiguracji jest uściślić oryginalnego elementu konfiguracji w celu spełnienia wymagań biznesowych.  

> [!NOTE]  
>  Podrzędne elementy konfiguracji można tworzyć tylko na podstawie elementów konfiguracji typu **Serwery i komputery z systemem Windows (niestandardowe)**.  

## <a name="to-create-a-child-configuration-item"></a>Aby utworzyć podrzędny element konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **elementy konfiguracji**.  

3.  Na liście **Elementy konfiguracji** wybierz element konfiguracji, dla którego chcesz utworzyć podrzędny element konfiguracji, a następnie na karcie **Narzędzia główne** w grupie **Element konfiguracji** kliknij pozycję **Utwórz podrzędny element konfiguracji**.  

4.  Na stronie **Ogólne** **Kreatora tworzenia podrzędnego elementu konfiguracji**można wybrać określoną poprawkę nadrzędnego elementu konfiguracji do użycia podczas tworzenia elementu podrzędnego. Pozostałe kroki tego kreatora są identyczne z tymi, które umożliwiają utworzenie standardowego elementu konfiguracji. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych elementów konfiguracji dla komputerów stacjonarnych i serwerów z systemem Windows](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md).  

5.  Ukończ pracę kreatora. Nowy podrzędny element konfiguracji zostanie wyświetlony na liście **Elementy konfiguracji** .  
