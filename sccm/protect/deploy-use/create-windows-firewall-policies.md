---
title: Zasady zapory systemu Windows dla programu Endpoint Protection | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak utworzyć i wdrożyć zasady zapory dla programu Endpoint Protection w programie System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ecdfad1-6305-45a8-ae75-3f33b967cb8f
caps.latest.revision: "5"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: acd75a8b22d050970b8c1176f725ddb4445633aa
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-and-deploy-windows-firewall-policies-for-endpoint-protection-in-system-center-configuration-manager"></a>Tworzenie i wdrażanie zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zasady zapory dla programu Endpoint Protection w programie System Center 2012 Configuration Manager umożliwiają wykonywanie podstawowych konfiguracji zapory systemu Windows i zadania konserwacji na komputerach klienckich w hierarchii. Zasady Zapory systemu Windows umożliwiają wykonywanie następujących zadań:  

-   kontrolowanie, czy Zapora systemu Windows jest włączona, czy wyłączona;  

-   kontrolowanie, czy komputery klienckie mogą przyjmować połączenia przychodzące;  

-   kontrolowanie, czy użytkownicy będą powiadamiani, gdy Zapora systemu Windows zablokuje nowy program.  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasady zapory systemu Windows**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz zasady Zapory systemu Windows**.  

4.  Na stronie **Ogólne** **Kreatora tworzenia zasad Zapory systemu Windows**podaj nazwę i opcjonalny opis dla zasad zapory, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Ustawienia profilu** kreatora skonfiguruj następujące ustawienia dla każdego profilu sieciowego:  

    > [!IMPORTANT]  
    >  Jeśli chcesz wdrożyć zasady Zapory systemu Windows na komputerach z systemem Windows Server 2008 i Windows Vista Service Pack 1, musisz najpierw zainstalować na nich [poprawkę KB971800](http://go.microsoft.com/fwlink/p/?LinkId=231239) .  

    > [!NOTE]  
    >  Aby uzyskać więcej informacji o profilach sieciowych, zobacz dokumentację systemu Windows.  

    -   **Włączanie Zapory systemu Windows**  

        > [!NOTE]  
        >  Jeśli pozycja **Włącz Zaporę systemu Windows** jest wyłączona, pozostałe ustawienia na tej stronie kreatora są niedostępne.  

    -   **Blokuj wszystkie połączenia przychodzące łącznie z programami znajdującymi się na liście dozwolonych programów**  

    -   **Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program**  

6.  Zapoznaj się z czynnościami do wykonania na stronie **Podsumowanie** kreatora, a następnie ukończ jego pracę.  

7.  Sprawdź, czy nowe zasady Zapory systemu Windows są wyświetlane na liście **Zasady Zapory systemu Windows** .  

##  <a name="BKMK_Assign"></a> Aby wdrożyć zasady Zapory systemu Windows  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasady zapory systemu Windows**.  

3.  Na liście **Zasady Zapory systemu Windows** wybierz zasady Zapory systemu Windows, które chcesz wdrożyć.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

5.  W oknie dialogowym **Wdrażanie zasad Zapory systemu Windows** określ kolekcję, do której chcesz przypisać zasady Zapory systemu Windows, a następnie określ harmonogram przypisania. Zasady Zapory systemu Windows oceniają zgodność przy użyciu tego harmonogramu i ustawień Zapory systemu Windows na klientach w celu takiego ich skonfigurowania, aby były zgodne z zasadami Zapory systemu Windows.  

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie zasad Zapory systemu Windows** i wdrożyć zasady Zapory systemu Windows.  

    > [!IMPORTANT]  
    >  Po wdrożeniu zasad Zapory systemu Windows w kolekcji zostaną one zastosowane dla komputerów w losowej kolejności w ciągu 2-godzinnego okresu, aby uniknąć przeciążenia sieci.
