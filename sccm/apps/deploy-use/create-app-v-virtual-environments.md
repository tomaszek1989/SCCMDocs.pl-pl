---
title: Utwórz środowiska wirtualne App-V
titleSuffix: Configuration Manager
description: Utwórz środowiska wirtualne z programu Microsoft Application Virtualization, więc aplikacje mogą udostępniać dane ze sobą.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e04b1d5662bb67ddb14310cd136abd6fdf29855d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-app-v-virtual-environments-in-system-center-configuration-manager"></a>Utwórz środowiska wirtualne App-V w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie Microsoft Application Virtualization (App-V) aplikacje wirtualne środowisko wirtualne w programie System Center Configuration Manager (program Configuration Manager), wdrożyć mogą współużytkować ten sam system plików i rejestr na komputerach klienckich z systemem Windows. W przeciwieństwie do standardowych aplikacji wirtualnych te aplikacje mogą udostępniać dane ze sobą. Środowiska wirtualne są utworzone lub zmodyfikowane na komputerach klienckich, gdy aplikacja jest zainstalowana lub gdy następny klient oceni zainstalowane aplikacje. Aplikacjom można przypisać priorytety. Gdy wiele aplikacji próbuje zmodyfikować system plików lub wartość rejestru, pierwszeństwo ma aplikacja o najwyższym priorytecie.  

> [!IMPORTANT]  
>  Nie należy polegać na środowiska wirtualne App-V zapewniają należytej ochrony, takie jak przed złośliwym oprogramowaniem.  

 Poniższa procedura umożliwia utworzenie środowiska wirtualnego App-V w programie Configuration Manager.  

## <a name="create-an-app-v-virtual-environment"></a>Utwórz środowisko wirtualne App-V  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **środowisk wirtualnych App-V**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie środowiska wirtualnego**.  

4.  W **tworzenie środowiska wirtualnego** okna dialogowego wprowadź następujące informacje:  

    -   **Nazwa**.  Wprowadź unikatową nazwę środowiska wirtualnego (maksymalnie 128 znaków).  

    -   **Opis elementu**. (Opcjonalnie) Wprowadź opis środowiska wirtualnego.  

5.  Aby dodać nowy typ wdrożenia do środowiska wirtualnego, wybierz **Dodaj**. Musisz dodać co najmniej jeden typ wdrożenia.  

6.  W **Dodawanie aplikacji** oknie dialogowym Określ **Nazwa grupy** (maksymalnie 128 znaków). Ta nazwa będzie używana do odwoływania się do grupy aplikacji dodawanej do środowiska wirtualnego.  

7.  Wybierz **Dodaj**, wybierz aplikacje App-V 5 i typy wdrożenia, które chcesz dodać do grupy, a następnie wybierz pozycję **OK**.  

8.  W **Dodawanie aplikacji** okno dialogowe, można wybrać **Zwiększ wartość kolejności** lub **Zmniejsz wartość kolejności** można ustawić aplikacji, która ma wyższy priorytet, gdy wiele aplikacji próbuje zmodyfikować system plików lub rejestru ustawienia w tym samym środowisku wirtualnym.  

9. Aby powrócić do **tworzenie środowiska wirtualnego** oknie dialogowym wybierz **OK**.  

10. Po zakończeniu dodawania grup wybierz **OK** można utworzyć środowisko wirtualne. Nowe środowisko wirtualne jest wyświetlany w **środowisk wirtualnych App-V** węzła konsoli programu Configuration Manager. Status środowisk wirtualnych można monitorować za pomocą raportu Status środowiska wirtualnego App-V.  

    > [!NOTE]  
    >  Środowisko wirtualne jest dodane lub zmodyfikowane na komputerach klienckich, gdy aplikacja jest zainstalowana lub gdy następny klient oceni zainstalowane aplikacje.  
