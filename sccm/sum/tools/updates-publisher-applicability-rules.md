---
title: Zasady stosowania | Dokumentacja firmy Microsoft
description: "Zarządzanie zasady stosowania dla programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 2925abda07abaa46ad56b9b433ce003c22aede5e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-applicability-rules-in-updates-publisher"></a>Zarządzanie zasady stosowania w Updates Publisher

*Dotyczy: System Center Updates Publisher*

Z programem Updates Publisher reguły stosowania zdefiniować wymagania, które muszą zostać spełnione przed urządzenia można zainstalować aktualizacji. Zasady są również używane do ustalenia, jeśli na komputerze jest zainstalowana aktualizacja. Reguły stosowania, która jest złożony z wielu części, jest określana zgodnie z zasadą ustawić.

Pakiety aktualizacji należy używać reguły stosowania.

## <a name="overview-of-applicability-rules"></a>Omówienie zasady stosowania
Zarządzanie zasady stosowania z **roboczym reguły**. Podczas tworzenia reguły określasz co najmniej jeden warunek. Jeśli określono wiele warunków, można skonfigurować relacje między warunków, więc są one obliczane sekwencyjnie lub łączone w logicznej **i** lub **lub** instrukcje.

Na przykład Oto zestaw reguł, który zawiera trzy zasady. Pierwsza reguła sprawdza, czy *mój_plik* plik istnieje, a drugi i trzeci reguły Sprawdź, czy język systemu operacyjnego jest angielski i japoński.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

Wszystkie aktualizacje wymagają co najmniej jedną regułę możliwości zastosowania. Aktualizacje, które należy zaimportować już zostały zastosowane reguły stosowania, a podczas tworzenia własnych aktualizacji, należy dodać co najmniej jedną regułę do nich. Można zmodyfikować, a następnie rozwiń węzeł z regułami dla dowolnej aktualizacji w aktualizacji wydawcy.

Widok reguły zostały utworzone, w **roboczym reguły**, wybierz regułę z **zapisanych reguł** listy. Poszczególne warunki i operacje logiczne dla tej reguły są wyświetlane w **zasady stosowania** konsoli. Reguły dla aktualizacji, które można zaimportować tylko można wyświetlać i modyfikować podczas edycji tej aktualizacji.

W dwóch miejscach w Updates Publisher, można utworzyć reguły:

-   W **roboczym reguły** tworzenia i **zapisać** zestawów reguł, której następnie można później. Podczas edytowania lub tworzenia aktualizacji można wybrać **zapisane zasadę** jako **reguły typu**, a następnie wybierz z listy z zestawów reguł wstępnie utworzone.

-   Można również utworzyć nowe reguły w czasie który tworzenia lub edytowania aktualizacji. Reguły utworzone w ten sposób nie są zapisywane do użycia w przyszłości.

## <a name="create-applicability-rule"></a>Tworzenie reguły stosowania
Następujące informacje są podobne jak utworzyć zasady za pomocą [Kreatora tworzenia aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard). Jednak w przeciwieństwie do kreatora, należy zapisać swoje zestawów reguł do użytku w przyszłości.

1.  W **roboczym reguły**, wybierz **Utwórz** otworzyć **Utwórz regułę** kreatora.

2.  Określ nazwę reguły, a następnie kliknij przycisk ![nową regułę](media/newrule.png). Spowoduje to otwarcie **stosowania reguły** strony, gdzie można skonfigurować reguły.

3.  Dla **reguły typu,** wybierz jedną z następujących czynności. Różne opcje, które należy skonfigurować dla każdego typu:

    -   **Plik** — ta zasada umożliwia mieć urządzenia pliku z właściwościami, które spełniają jeden lub więcej kryteriów, określ przed tej aktualizacji można zastosować.

    -   **Rejestr —** ten typ umożliwia określenie szczegółów rejestru, które muszą być obecne przed urządzenie kwalifikuje się do zainstalowania tej aktualizacji.

    -   **System —** zasada używa szczegóły systemu do ustalenia możliwości zastosowania. Można wybrać Definiowanie wersji systemu Windows, Windows języka, architektury procesora lub określ kwerendę usługi WMI do identyfikowania urządzeń systemu operacyjnego.

    -   **Instalator systemu Windows —** ta reguła służy do określenia stosowania oparte na zainstalowany. Poprawka MSI lub Instalatora systemu Windows (. MSP). Można również określić, czy określone składniki lub funkcje są instalowane w ramach zapotrzebowania.

       > [!IMPORTANT]   
       > Na zarządzanych deices, usługa Windows Update Agent nie może wykryć pakiety instalacji systemu Windows, które są zainstalowane dla poszczególnych użytkowników. Korzystając z tego typu reguły, należy skonfigurować zasady stosowania dodatkowych, takich jak wartości klucza rejestru lub wersje plików, tak aby pakiet Instalatora Windows może prawidłowo wykrył niezależnie od konkretnego użytkownika lub całego systemu.

    -   **Zapisano regułę —** ta opcja pozwala znaleźć i używać reguł, które wcześniej skonfigurowane i zapisane.

4.  Nadal można dodawać i konfigurować dodatkowe zasady zgodnie z potrzebami.

5.  Za pomocą przycisków operacji logicznej do zamówienia i grupowania różnych zasad, aby utworzyć bardziej złożoną Sprawdzanie wymagań wstępnych.

6.  Po zakończeniu zestaw reguł, kliknij przycisk **OK** go zapisać. Teraz zestaw reguł jest wyświetlana w **zapisanych reguł** listy.

## <a name="edit-applicability-rule-sets"></a>Edytowanie zestawów reguł stosowania
Aby edytować regułę stosowania w **roboczym reguły** Wybierz reguły są zapisywane w **zapisanych reguł** , a następnie wybierz **edytować** na Wstążce. Spowoduje to otwarcie **Edytuj regułę** kreatora.

**Edytuj regułę** Kreator wyświetla bieżące zasady zestawu reguł. Edytowanie reguł w taki sam sposób jak używasz **Utwórz regułę** kreatora, aby utworzyć nowe reguły. Ten kreator służy do zmiany nazwy zestawu reguł, usunąć zasady, zmienić kolejność reguł i relacje lub dodawanie nowych zasad.

Po wprowadzeniu zmian kliknij **OK** Aby zapisać zmiany i zamknąć kreatora.

Więcej informacji o korzystaniu z kreatora reguły można znaleźć w temacie **krok 7**, strony stosowania z [Kreatora tworzenia aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard).

## <a name="delete-applicability-rules"></a>Usuń zasady stosowania
Aby usunąć regułę stosowania zapisane w **roboczym reguły** wybierz regułę lub zestaw reguł z **zapisanych reguł** , a następnie wybierz **usunąć** na Wstążce. Spowoduje to usunięcie zapisanych reguła lub zestaw reguł z Updates Publisher.

Aby usunąć reguły z określonej aktualizacji, należy najpierw [edytować aktualizację](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles).

