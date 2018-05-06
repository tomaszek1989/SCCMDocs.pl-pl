---
title: Utworzyć podrzędne elementy konfiguracji
titleSuffix: Configuration Manager
description: Utworzyć podrzędne elementy konfiguracji w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 358f2d67a5a4689927632bb1492ace1a33490451
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
