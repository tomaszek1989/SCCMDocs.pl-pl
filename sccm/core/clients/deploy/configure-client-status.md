---
title: Skonfiguruj Stan klienta | Dokumentacja firmy Microsoft
description: Wybierz ustawienia stanu klienta w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2275ba2-c83d-43e7-90ed-418963a707fe
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 060d63ab8bce9c3bb39d2db404580b9f59416d33
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-status-in-system-center-configuration-manager"></a>Jak skonfigurować stan klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed rozpoczęciem monitorowania stanu klienta programu System Center Configuration Manager i korygowanie znalezionych problemów, należy skonfigurować lokację do określania parametrów, które są używane do oznaczania klientów jako nieaktywnych i skonfigurować opcje powiadamiania w przypadku gdy aktywność klienta spadnie poniżej określonego progu. Można także wyłączyć komputery z automatycznego korygowania stanu klienta znalezionych problemów związanych.  

##  <a name="BKMK_1"></a>Aby skonfigurować stan klienta  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, kliknij przycisk **stanu klienta**, a następnie w **Home** karcie w **stanu klienta** , kliknij przycisk **ustawienia stanu klienta**.  

3.  W **właściwości ustawień stanu klienta** okna dialogowego określ poniższe wartości, aby ustalić aktywność klienta:  

    > [!NOTE]  
    >  Jeśli żadne ustawienia nie zostaną osiągnięte, klient zostanie oznaczony jako nieaktywny.  

    -   **Żądania zasady klienta w następujące dni:** Określ liczbę dni od momentu, gdy klient zażądał zasad. Domyślna wartość to **7** dni.  

    -   **Odnajdywanie pulsu w następujące dni:** Określ liczbę dni od momentu, gdy komputer kliencki wysłał rekord odnajdywania pulsu do bazy danych lokacji. Domyślna wartość to **7** dni.  

    -   **Spis sprzętu w następujące dni:** Określ liczbę dni, ponieważ komputer kliencki wysłał rekord spisu sprzętu do bazy danych lokacji. Domyślna wartość to **7** dni.  

    -   **Zapasy oprogramowania w następujące dni:** Określ liczbę dni, ponieważ komputer kliencki wysłał rekord spisu oprogramowania do bazy danych lokacji. Domyślna wartość to **7** dni.  

    -   **Komunikaty o stanie w następujące dni:** Określ liczbę dni, ponieważ komputer kliencki wysłał komunikaty o stanie do bazy danych lokacji. Domyślna wartość to **7** dni.  

4.  W **właściwości ustawień stanu klienta** okna dialogowego określ poniższą wartość, aby określić, jak długo są przechowywane dane historii stanu klienta:  

    -   **Zachowaj historię stanu klienta przez następującą liczbę dni:** Określ, jak długo ma historię stanu klienta ma pozostawać w bazie danych lokacji. Wartość domyślna to **31** dni.  

5.  Kliknij przycisk **OK** Aby zapisać właściwości i zamknąć **właściwości ustawień stanu klienta** okno dialogowe.  

##  <a name="BKMK_Schedule"></a>Aby skonfigurować harmonogram dla stanu klienta  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, kliknij przycisk **stanu klienta**, a następnie w **Home** karcie w **stanu klienta** , kliknij przycisk **Zaplanuj aktualizację stanu klienta**.  

3.  W **Zaplanuj aktualizację stanu klienta** okna dialogowego Skonfiguruj interwał, w którym mają stan klienta do aktualizacji, a następnie kliknij przycisk OK.  

    > [!NOTE]  
    >  Jeśli harmonogram aktualizacji stanu klienta zostanie zmieniony, aktualizacja nie zostanie zastosowana do momentu następnej zaplanowanej aktualizacji stanu klienta (w przypadku wcześniej skonfigurowany zgodnie z harmonogramem).  

##  <a name="BKMK_2"></a>Aby skonfigurować alerty dla stanu klienta  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.  

3.  Na liście **Kolekcje urządzeń** wybierz kolekcję, dla której chcesz skonfigurować alerty, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

    > [!NOTE]  
    >  Nie można skonfigurować alertów dla kolekcji użytkowników.  

4.  Na **alerty** na karcie  *&lt;kolekcji nazwa\>***właściwości** okno dialogowe, kliknij przycisk **Dodaj**.  

    > [!NOTE]  
    >  Karta **Alerty** jest widoczna tylko w przypadku, gdy rola zabezpieczeń, z którą została skojarzony użytkownik, ma uprawnienia do alertów.  

5.  W oknie dialogowym **Dodaj nowe alerty kolekcji** wybierz alerty, które mają być generowane, gdy progi stanu klienta spadną poniżej określonej wartości, a następnie kliknij przycisk **OK**.  

6.  Z listy **Warunki** na karcie **Alerty** wybierz poszczególne alerty stanu klienta, a następnie określ poniższe informacje.  

    -   **Nazwa alertu** — zaakceptuj nazwę domyślną lub wprowadź nową nazwę alertu.  

    -   **Ważność alertu** — z listy rozwijanej wybierz poziom alertu, który będzie wyświetlany w konsoli programu Configuration Manager.  

    -   **Zgłoś alert** — Określ procentowy próg alertu.  

7.  Kliknij przycisk **OK** zamknąć  *&lt;kolekcji nazwa\>***właściwości** okno dialogowe.  

##  <a name="BKMK_3"></a>Aby wykluczyć komputery z automatycznego korygowania  

1.  Otwórz Edytor rejestru na komputerze klienckim, dla której chcesz wyłączyć automatyczne korygowanie.  

    > [!WARNING]  
    >  Korzystanie z Edytora rejestru może spowodować poważne problemy, które mogą wymagać ponownego zainstalowania systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.  

2.  Przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\CCM\CcmEval\NotifyOnly**.  

3.  Wprowadź jedną z następujących wartości dla tego klucza rejestru:  

    -   **TRUE** — komputer kliencki nie będzie automatycznie korygował żadnych znalezionych problemów. Jednak użytkownik będzie nadal otrzymywać alerty w **monitorowanie** obszaru roboczego o wszystkich problemach z tym klientem.  

    -   **FALSE** — komputer kliencki będzie automatycznie korygował problemy zostały znalezione i będzie otrzymywać alerty w **monitorowanie** obszaru roboczego. To jest ustawienie domyślne.  

4.  Zamknij Edytor rejestru.  

 Można także zainstalowanie klientów przy użyciu programu CCMSetup **NotifyOnly** właściwości instalacji, aby wykluczyć je z automatycznego korygowania. Aby uzyskać więcej informacji na temat tej właściwości instalacji klienta, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

