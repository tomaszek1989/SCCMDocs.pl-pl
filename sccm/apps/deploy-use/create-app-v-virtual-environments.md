---
title: "Utwórz środowiska wirtualne App-V | Dokumentacja firmy Microsoft"
description: "Utwórz środowiska wirtualne za pomocą Microsoft Application Virtualization, więc aplikacje mogą udostępniać danych ze sobą."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa9e87830a3a51b01fae29b564c9267ec930a60d
ms.openlocfilehash: 377ed9732fb16b062f53e78504aea394acdb7462
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-app-v-virtual-environments-in-system-center-configuration-manager"></a>Utwórz środowiska wirtualne App-V w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W programie Microsoft Application Virtualization (App-V) aplikacje wirtualne środowiska wirtualnego w System Center Configuration Manager (Menedżer konfiguracji), wdrożone mogą współużytkować ten sam system plików i rejestr na komputery klienckie z systemem Windows. W przeciwieństwie do standardowych aplikacji wirtualnych te aplikacje mogą współużytkować dane ze sobą. Środowiska wirtualne są tworzone lub zmodyfikowane na komputerach klienckich, gdy aplikacja jest zainstalowana lub gdy następny klient oceni zainstalowane aplikacje. Aplikacjom można przypisać priorytety. Gdy wiele aplikacji próbuje zmodyfikować system plików lub wartość rejestru, pierwszeństwo ma aplikacja o najwyższym priorytecie.  

> [!IMPORTANT]  
>  Nie należy polegać na środowiska wirtualne App-V w celu zapewnienia ochrony zabezpieczeń, takich jak przed złośliwym oprogramowaniem.  

 Poniższa procedura umożliwia utworzenie środowiska wirtualnego App-V w programie Configuration Manager.  

## <a name="create-an-app-v-virtual-environment"></a>Tworzenie środowiska wirtualnego App-V  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **środowisk wirtualnych App-V**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenie środowiska wirtualnego**.  

4.  W **tworzenie środowiska wirtualnego** oknie dialogowym wprowadź następujące informacje:  

    -   **Nazwa**.  Wprowadź unikatową nazwę środowiska wirtualnego (maksymalnie 128 znaków).  

    -   **Opis**. (Opcjonalnie) Wprowadź opis środowiska wirtualnego.  

5.  Aby dodać nowy typ wdrożenia do środowiska wirtualnego, wybierz **Dodaj**. Musisz dodać co najmniej jeden typ wdrożenia.  

6.  W **Dodawanie aplikacji** okna dialogowego określ **Nazwa grupy** (maksymalnie 128 znaków). Ta nazwa będzie używana do odwoływania się do grupy aplikacji dodawanej do środowiska wirtualnego.  

7.  Wybierz **Dodaj**, wybierz aplikacje App-V 5 i typy wdrożenia, które chcesz dodać do grupy, a następnie wybierz **OK**.  

8.  W **Dodawanie aplikacji** okno dialogowe, można wybrać **Zwiększ wartość kolejności** lub **Zmniejsz wartość kolejności** ustawić aplikację, która ma wyższy priorytet, gdy wiele aplikacji próbuje zmodyfikować system plików lub rejestru ustawienia w tym samym środowisku wirtualnym.  

9. Aby powrócić do **tworzenie środowiska wirtualnego** okno dialogowe Wybierz **OK**.  

10. Po zakończeniu dodawania grup kliknij **OK** do tworzenia środowisk wirtualnych. Nowe środowisko wirtualne jest wyświetlane w **środowisk wirtualnych App-V** węzeł konsoli programu Configuration Manager. Status środowisk wirtualnych można monitorować za pomocą raportu Status środowiska wirtualnego App-V.  

    > [!NOTE]  
    >  Środowisko wirtualne zostanie dodane lub zmodyfikowane na komputerach klienckich, gdy aplikacja jest instalowana lub gdy następny klient oceni zainstalowane aplikacje.  

