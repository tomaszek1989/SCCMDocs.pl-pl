---
title: "Przygotowanie do zarządzania aktualizacjami oprogramowania"
titleSuffix: Configuration Manager
description: "Aby przygotować się do zarządzania aktualizacjami, wykonania tych zadań do wyświetlenia danych oceny zgodności w konsoli programu System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
ms.openlocfilehash: 91c6e3654375073977a50cfffb0cf784d091ef98
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="prepare-for-software-updates-management"></a>Przygotowanie do zarządzania aktualizacjami oprogramowania

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zanim danych oceny zgodności aktualizacji oprogramowania zostanie wyświetlona w konsoli programu System Center Configuration Manager i przed wdrożeniem aktualizacji oprogramowania na komputerach klienckich, należy wykonać czynności opisane w poniższych sekcjach.

## <a name="step-1-install-a-software-update-point"></a>Krok 1. Zainstaluj punkt aktualizacji oprogramowania  
Punkt aktualizacji oprogramowania jest wymagany w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej i w lokacjach głównych umożliwiające oprogramowania ocena zgodności aktualizacji i aby wdrożyć oprogramowanie aktualizuje do klientów. Punkt aktualizacji oprogramowania jest opcjonalny w lokacjach dodatkowych. Aby uzyskać więcej informacji, zobacz [instalacji punktu aktualizacji oprogramowania](install-a-software-update-point.md)  

## <a name="step-2-synchronize-software-updates"></a>Krok 2. Synchronizowanie aktualizacji oprogramowania
Synchronizacja aktualizacji oprogramowania to proces pobierania metadanych aktualizacji oprogramowania, która spełnia kryteria, które można skonfigurować. Aktualizacje oprogramowania nie są wyświetlane w konsoli programu Configuration Manager, dopóki synchronizacja aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](synchronize-software-updates.md).   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>Krok 3. Konfigurowanie klasyfikacji i produktów do synchronizacji
Tę konfigurację należy przeprowadzić w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Po zsynchronizowaniu aktualizacji oprogramowania po raz pierwszy, programu Configuration Manager pobiera zaktualizowane listy klasyfikacji i produktów. Teraz możesz wybrać nowe opcje we właściwościach składnika punktu aktualizacji oprogramowania. Po skonfigurowaniu nowych klasyfikacji i produktów, powtórz krok 2 można uruchomić synchronizacji aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania dla nowych kryteriów. Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty do zsynchronizowania](configure-classifications-and-products.md).

## <a name="step-4-manage-settings-for-software-updates"></a>Krok 4. Zarządzanie ustawieniami aktualizacji oprogramowania
Po zsynchronizowaniu aktualizacji oprogramowania należy sprawdzić ustawienia klienta programu Configuration Manager, konfiguracji zasad grupy i ustawień aktualizacji oprogramowania przed wdrożeniem aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aktualizacji oprogramowania](manage-settings-for-software-updates.md).
