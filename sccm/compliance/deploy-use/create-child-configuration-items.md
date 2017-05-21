---
title: "Tworzenie obiektów podrzędnych elementów konfiguracji | Dokumentacja firmy Microsoft"
description: "Utwórz podrzędne elementy konfiguracji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>Jak utworzyć podrzędnych elementów konfiguracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podrzędne elementy konfiguracji w programie System Center Configuration Manager są kopiami elementy konfiguracji, które zachowują relacji do oryginalnego elementu konfiguracji, w tym dziedziczą oryginalną konfigurację z nadrzędnego elementu konfiguracji.  

Po wyświetleniu właściwości podrzędny element konfiguracji w konsoli programu Configuration Manager nie można edytować dziedziczone obiekty i ustawienia z ich kryteria sprawdzania poprawności. Można natomiast dodawać, a następnie edytować dodatkowe kryteria weryfikacji do podrzędnego elementu konfiguracji, a nowe obiekty i ustawienia można również dodawać do podrzędnego elementu konfiguracji.
Zwykle do tworzenia i edytowania podrzędny element konfiguracji ma na celu uściślić oryginalnego elementu konfiguracji w celu spełnienia wymagań biznesowych.  

> [!NOTE]  
>  Podrzędne elementy konfiguracji można tworzyć tylko na podstawie elementów konfiguracji typu **Serwery i komputery z systemem Windows (niestandardowe)**.  

## <a name="to-create-a-child-configuration-item"></a>Aby utworzyć podrzędny element konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **elementy konfiguracji**.  

3.  Na liście **Elementy konfiguracji** wybierz element konfiguracji, dla którego chcesz utworzyć podrzędny element konfiguracji, a następnie na karcie **Narzędzia główne** w grupie **Element konfiguracji** kliknij pozycję **Utwórz podrzędny element konfiguracji**.  

4.  Na stronie **Ogólne** **Kreatora tworzenia podrzędnego elementu konfiguracji**można wybrać określoną poprawkę nadrzędnego elementu konfiguracji do użycia podczas tworzenia elementu podrzędnego. Pozostałe kroki tego kreatora są identyczne z tymi, które umożliwiają utworzenie standardowego elementu konfiguracji. Aby uzyskać więcej informacji, zobacz [Tworzenie pozycji konfiguracji niestandardowej dla komputerów osobistych i serwerów z systemem Windows](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md).  

5.  Ukończ pracę kreatora. Nowy podrzędny element konfiguracji zostanie wyświetlony na liście **Elementy konfiguracji** .  

