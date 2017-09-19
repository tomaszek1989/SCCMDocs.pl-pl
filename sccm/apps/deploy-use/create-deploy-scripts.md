---
title: "Tworzenie i uruchamianie skryptów w programie Configuration Manager | Dokumentacja firmy Microsoft"
description: "Tworzenie i uruchamianie skryptów na urządzeniach klienckich w programie Configuration Manager."
ms.custom: na
ms.date: 09/15/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: "14"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: e6b29cd85504742e8638a55db2f6c4ecc8ab3e55
ms.sourcegitcommit: 5ca89204716750eaaceb01bba40b35b85c7122ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2017
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie Configuration Manager, oprócz skryptów za pomocą pakietów i programów, można następujące funkcje należy wykonać następujące czynności:

- Importuj skryptów programu PowerShell dla programu Configuration Manager
- Edytowanie skryptów z poziomu konsoli programu Configuration Manager (w przypadku niepodpisanych skryptów tylko)
- Skrypty Oznacz jako zatwierdzone lub zabroniona, zwiększające bezpieczeństwo
- Uruchamianie skryptów w kolekcji komputerom klienckim z systemem Windows oraz lokalnych zarządzanych komputerów z systemem Windows. Nie można wdrożyć skrypty, zamiast tego są uruchamiane niemal natychmiast na urządzeniach klienckich.
- Zbadanie wyników zwróconych przez skrypt w konsoli programu Configuration Manager.

>[!TIP]
>W tej wersji programu Configuration Manager są funkcji wersji wstępnej. Aby włączyć skryptów, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

## <a name="prerequisites"></a>Wymagania wstępne

Aby uruchamiać skrypty programu PowerShell, klient musi działać program PowerShell w wersji 3.0 lub nowszej. Jednak jeśli po uruchomieniu skryptu zawiera funkcje z nowszej wersji programu PowerShell, klienta, na którym uruchomiono skrypt musi działać tej wersji.

Klienci programu Configuration Manager musi być uruchomiona klienta z wersji 1706 lub nowszego w celu uruchamiania skryptów.

Używać skryptów, użytkownik musi należeć do odpowiedniej roli zabezpieczeń programu Configuration Manager.

- Do zaimportowania, a także tworzenie skryptów — Twoje konto musi mieć **Utwórz** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Aby zaakceptować lub odrzucić skryptów — Twoje konto musi mieć **Zatwierdź** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Aby uruchamiać skrypty - Twoje konto musi mieć **Uruchom skrypt** uprawnienia dla **kolekcje** w **Menedżer ustawień zgodności** roli zabezpieczeń.

Aby uzyskać więcej informacji na temat ról zabezpieczeń programu Configuration Manager, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration).

Domyślnie użytkownicy nie można zatwierdzić skryptu, który one utworzone przez użytkownika. Ponieważ skrypty są wydajne, elastyczne i można wdrożyć na wielu urządzeniach, można rozdzielić role między osoby, która tworzy skrypt i osoby, które zatwierdza skryptu. Role te zapewniają dodatkowy poziom zabezpieczeń przed uruchomieniem skryptu bez nadzoru. Możesz wyłączyć ten dodatkowej zatwierdzenia, aby ułatwić testowanie.

## <a name="allow-users-to-approve-their-own-scripts"></a>Użytkownicy mogą zatwierdzać własnych skryptów

1. W konsoli programu Configuration Manager kliknij przycisk **Administracja**.
2. W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.
3. Na liście witryn, wybierz witryny, a następnie na **Home** karcie **witryny** kliknij przycisk **ustawienia hierarchii**.
4. Na **ogólne** karcie **właściwości ustawień hierarchii** okna dialogowego polu, wyczyść pole wyboru **nie zezwalaj na skryptu autorzy mogą zatwierdzać własnych skryptów**.

## <a name="import-and-edit-a-script"></a>Importowanie i edytowanie skryptu

1. W konsoli programu Configuration Manager kliknij **Librar oprogramowania**y.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. Na **Home** karcie **Utwórz** kliknij przycisk **Tworzenie skryptu**.
4. Na **skryptu** tworzenia **skryptu** kreatora skonfiguruj następujące ustawienia:
    - **Nazwa skryptu** — wprowadź nazwę skryptu. Mimo że można tworzyć wiele skryptów o takiej samej nazwie, przy użyciu takich samych nazwach utrudnia odnajdywania skryptów, które są potrzebne w konsoli programu Configuration Manager.
    - **Język skryptów** — obecnie są obsługiwane tylko skrypty programu PowerShell.
    - **Importuj** — importowanie skrypt programu PowerShell do konsoli. Skrypt jest wyświetlany w **skryptu** pola.
    - **Wyczyść** — usuwa bieżący skrypt pola skryptu.
    - **Skrypt** -wyświetla skrypt aktualnie zaimportowany. Skrypt w tym polu, w razie potrzeby można edytować.
5. Ukończ pracę kreatora. Nowy skrypt jest wyświetlany w **skryptu** liście ze stanem **oczekiwanie na zatwierdzenie**. Zanim można było uruchomić ten skrypt na urządzeniach klienckich, należy ją zatwierdzić.

### <a name="script-examples"></a>Przykłady skryptów

Oto przykłady ilustrujące skrypty, które można korzystać z tej funkcji.

#### <a name="create-a-folder"></a>Utwórz folder

*Nowy element "c:\scripts"-Nazwa folderu typu*


#### <a name="create-a-file"></a>Utwórz plik

*Nowy element c:\scripts\new_file.txt — Nazwa typu pliku*


## <a name="approve-or-deny-a-script"></a>Zatwierdzanie lub odrzucanie skryptu

Przed uruchomieniem skryptu, musi być zatwierdzony. Aby zatwierdzić skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. W **skryptu** wybierz skrypt, aby zaakceptować lub odrzucić, a następnie na **Home** karcie **skryptu** kliknij przycisk **Zatwierdź/Deny**.
4. W **Zatwierdź lub odmówić** okno dialogowe skryptu, **Zatwierdź**, lub **Odmów** skryptu i opcjonalnie wprowadź komentarz dotyczący decyzji. Jeśli użytkownik zezwoli na skryptu, nie można uruchomić na urządzeniach klienckich.
5. Ukończ pracę kreatora. W **skryptu** listy, zostanie wyświetlony **stan zatwierdzenia** zmiany kolumny w zależności od akcja została wykonana.

## <a name="run-a-script"></a>Uruchom skrypt
Po zatwierdzeniu skryptu mogą być uruchamiane na kolekcję, którą wybierzesz.

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W zasoby i zgodność obszar roboczy, kliknij przycisk **kolekcje urządzeń**.
3. W **kolekcje urządzeń** kliknij kolekcję urządzeń, na których chcesz uruchomić skrypt.
4. Na **Home** karcie **wszystkie systemy** kliknij przycisk **Uruchom skrypt**.
5. Na **skryptu** strony **Uruchom skrypt** kreatora wybierz skrypt z listy. Wyświetlane są tylko zatwierdzone skrypty.
6. Kliknij przycisk **dalej**, a następnie Zakończ pracę kreatora.

>[!IMPORTANT]
>Skrypt znajduje się w przedziale czasu godziny, w którym ma być uruchamiany. Jeśli nie działa on (na przykład jeśli komputer jest wyłączony) w tym okresie, należy uruchomić je ponownie.

## <a name="next-steps"></a>Następne kroki

Po uruchomieniu skryptu na urządzeniach klienckich, użyj tej procedury, aby monitorować powodzenie operacji.

1. W konsoli programu Configuration Manager kliknij **monitorowanie**.
2. W **monitorowanie** obszaru roboczego kliknij **stanu skryptu**.
3. W **stanu skryptu** listy, wyświetlania wyników dla każdego skryptu uruchomionego na urządzeniach klienckich. Kod zakończenia skryptu **0** ogół wskazuje, że skrypt został uruchomiony pomyślnie.
