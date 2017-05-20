---

title: "Przygotowanie do zarządzania aktualizacjami oprogramowania | Dokumentacja firmy Microsoft"
description: "Aby przygotować się do zarządzania aktualizacjami, wykonania tych zadań w celu wyświetlenia danych oceny zgodności w konsoli programu System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 5c34bd1ea108dffda10c30281fb9c97ba38ae1ae
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="prepare-for-software-updates-management"></a>Przygotowanie do zarządzania aktualizacjami oprogramowania

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zanim danych oceny zgodności aktualizacji oprogramowania są wyświetlane w konsoli programu System Center Configuration Manager i przed wdrożeniem aktualizacji oprogramowania na komputerach klienckich, należy wykonać kroki opisane w poniższych sekcjach.

## <a name="step-1-install-a-software-update-point"></a>Krok 1: Zainstaluj punkt aktualizacji oprogramowania  
Punkt aktualizacji oprogramowania jest wymagany w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej i w lokacjach głównych włączyć oprogramowanie oceny zgodności aktualizacji i wdrażania oprogramowania aktualizacje klientów. Punkt aktualizacji oprogramowania jest opcjonalny w lokacjach dodatkowych. Aby uzyskać szczegółowe informacje, zobacz [instalacji punktu aktualizacji oprogramowania](install-a-software-update-point.md)  

## <a name="step-2-synchronize-software-updates"></a>Krok 2: Synchronizowanie aktualizacji oprogramowania
Synchronizacja aktualizacji oprogramowania to proces pobierania metadanych aktualizacji oprogramowania, która spełnia kryteria, które można skonfigurować. Aktualizacje oprogramowania nie są wyświetlane w konsoli programu Configuration Manager, dopóki synchronizacja aktualizacji oprogramowania. Aby uzyskać szczegółowe informacje, zobacz [synchronizowanie aktualizacji oprogramowania](synchronize-software-updates.md).   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>Krok 3: Konfigurowanie klasyfikacji i produktów do zsynchronizowania
Tę konfigurację należy przeprowadzić w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Po zsynchronizowaniu aktualizacji oprogramowania po raz pierwszy, program Configuration Manager pobiera zaktualizowanej listy klasyfikacji i produktów. Teraz można wybrać nowe opcje we właściwościach składnika punktu aktualizacji oprogramowania. Po skonfigurowaniu nowych klasyfikacje i produkty Powtórz krok 2, aby rozpocząć synchronizację aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania dla nowych kryteriów. Aby uzyskać szczegółowe informacje, zobacz [skonfigurować klasyfikacje i produkty do zsynchronizowania](configure-classifications-and-products.md).

## <a name="step-4-manage-settings-for-software-updates"></a>Krok 4: Zarządzanie ustawieniami aktualizacji oprogramowania
Po zsynchronizowaniu aktualizacji oprogramowania, sprawdź ustawienia klienta programu Configuration Manager, konfiguracji zasad grupy i ustawień aktualizacji oprogramowania przed wdrożeniem aktualizacji oprogramowania. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie ustawieniami aktualizacji oprogramowania](manage-settings-for-software-updates.md).

