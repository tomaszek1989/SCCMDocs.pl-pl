---
title: "Zaplanuj i skonfiguruj ustawienia zgodności | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o wymaganiach wstępnych oraz zadań konfiguracyjnych do pracy z ustawieniami zgodności w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: d26ac3de58d2f0ef447725e63fc2d8adda6ea06c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-and-configure-compliance-settings-in-system-center-configuration-manager"></a>Planowanie i konfigurowanie ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed rozpoczęciem pracy z ustawień zgodności programu System Center Configuration Manager, istnieje kilka wymagań wstępnych, musisz wiedzieć o, a niektóre zadania konfiguracji, które będą potrzebne do wykonania.  

## <a name="prerequisites-for-compliance-settings"></a>Wymagania wstępne dotyczące ustawień zgodności  

|Wymaganie wstępne|Więcej informacji|  
|------------------|----------------------|  
|Klienci programu Configuration Manager systemu Windows musi być włączona i skonfigurowana do oceny zgodności.|Zob.|  
|Jeśli chcesz uruchamiać raporty, musisz skonfigurować raportowanie dla danej lokacji.|[Raportowanie programu System Center Configuration Manager](../../core/servers/manage/reporting.md)|  
|Wymagane uprawnienia zabezpieczeń.|**Menedżer ustawień zgodności** obejmuje rola zabezpieczeń wystarczających uprawnień do zarządzania ustawieniami zgodności, elementy konfiguracji profilów i danych użytkownika i profili połączenia zdalnego.<br /><br /> [Konfigurowanie administracji opartej na rolach](../../core/servers/deploy/configure/configure-role-based-administration.md)|  

##  <a name="enable-and-configure-compliance-settings-for-windows-pcs-only"></a>Włącz i skonfiguruj ustawienia zgodności (dla tylko komputery z systemem Windows)  

Poniżej przedstawiono procedurę konfigurowania domyślnych ustawień klienta dotyczących ustawień zgodności, która dotyczy wszystkich komputerów w hierarchii. Jeśli te ustawienia mają być stosowane tylko dla niektórych komputerów, utwórz niestandardowe ustawienie klienta urządzenia i przypisz je do kolekcji zawierającej komputery, na których chcesz użyć ustawień zgodności. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień urządzenia, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).  

> [!TIP]  
>  Inne typy urządzeń nie wymagają określonej konfiguracji w celu oceny ustawień zgodności.  

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **ustawień klienta** > **ustawienia domyślne**.  
2.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  
3.  W oknie dialogowym **Ustawienia domyślne** kliknij pozycję **Ustawienia zgodności**.  
4.  Skonfiguruj następujące ustawienia klienta dla ustawień zgodności:
    - **Włącz ocenę zgodności na komputerach klienckich** -wartość **True** Jeśli chcesz dokonać oceny zgodności na urządzeniach klienckich.
    - **Zaplanuj ocenę zgodności** -kliknij **harmonogram** Jeśli chcesz zmodyfikować domyślny harmonogram oceny zgodności na urządzeniach klienckich.
    - **Włącz dane użytkownika i profile** — Włącz tę opcję, jeśli chcesz utworzyć i wdrożyć elementy konfiguracji profilów i danych użytkowników na komputerach z systemem Windows. Aby uzyskać szczegółowe informacje, zobacz [tworzenia elementów konfiguracji profilów i danych użytkownika](/sccm/compliance/deploy-use/create-remote-connection-profiles).
5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia domyślne** .  

Komputery klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta.  

