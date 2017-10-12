---
title: "Jak zarządzać ochrona urządzeń z systemem Windows | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zarządzać ochrona urządzeń z systemem Windows za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: "13"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 4555f7a9a6b5efd0fa01e9a101ea16bae7685117
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="device-guard-management-with-configuration-manager"></a>Zarządzanie urządzeniami Guard z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

## <a name="introduction"></a>Wprowadzenie
Ochrona urządzeń to grupa funkcji systemu Windows 10, które są przeznaczone do ochrony komputerów przed złośliwym oprogramowaniem i innym oprogramowaniem niezaufanych. Uniemożliwia złośliwy kod działa przez zapewnienie, że tylko zatwierdzone kodu, który znasz, można uruchomić.

Ochrona urządzeń obejmuje zarówno oprogramowania i funkcji zabezpieczeń oparte na sprzęcie. Integralność kodu można skonfigurować jest warstwy zabezpieczeń opartych na oprogramowaniu, która wymusza jawną listę oprogramowania, które można uruchamiać na komputerze. Na własną, można skonfigurować kod integralności nie ma wymagań wstępnych sprzętu lub oprogramowania układowego. Zasady zabezpieczenia urządzeń wdrożony z programu Configuration Manager Włącz zasad integralności kodu można skonfigurować na komputerach w kolekcje docelowe, które spełniają minimalna wersja systemu Windows i SKU wymagania opisane w tym temacie. Opcjonalnie oparta na funkcji hypervisor zasad integralności kodu wdrożony za pomocą programu Configuration Manager można można włączyć ochrony za pomocą zasad grupy w stanie sprzętu.

Aby dowiedzieć się więcej na temat ochrony urządzeń, przeczytaj [przewodnik wdrażania ochrony urządzeń](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

## <a name="using-device-guard-with-configuration-manager"></a>Przy użyciu ochrony urządzeń z programem Configuration Manager

Można użyć programu Configuration Manager, aby wdrożyć zasady ochrony urządzeń, które można skonfigurować tryb, w którym ochrony urządzeń jest uruchamiany na komputerach w kolekcji. 

Można skonfigurować jeden z następujących trybów:

1.  **Wymuszanie włączone** — tylko zaufane, można uruchamiać pliki wykonywalne.
2.  **Tylko inspekcja** — Zezwalaj na uruchamianie wszystkich plików wykonywalnych, ale dziennika niezaufanych plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń lokalnego klienta.

>[!TIP]
>W tej wersji programu Configuration Manager ochrony urządzeń to funkcja wersji wstępnej. Aby ją włączyć, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

## <a name="what-can-run-when-you-deploy-a-device-guard-policy"></a>Co mogą działać po wdrożeniu zasad ochrony urządzeń?

Ochrona urządzeń z systemem Windows umożliwia zdecydowanie kontrolować, jakie można uruchamiać na zarządzanych komputerach. Ta funkcja może być przydatne dla komputerów w działach wysokim poziomie zabezpieczeń, jeśli jest to niezbędne, że nie można uruchomić niechcianego oprogramowania.

Podczas wdrażania zasad, zwykle można uruchomić następujące pliki wykonywalne:

- Składniki systemu Windows
- Centrum deweloperów sprzętu sterowniki (podpisów laboratoria jakości sprzętu dla systemu Windows)
- Aplikacje ze Sklepu Windows
- Klient programu Configuration Manager 
- Całe oprogramowanie wdrożyć za pomocą programu Configuration Manager, że komputery instalują po przetworzeniu zasad ochrony urządzeń. 
- Aktualizacje składników systemu windows z:
    - Usługi Windows Update
    - Windows Update dla firm
    - Windows Server Update Services
    - Menedżer konfiguracji

>[!IMPORTANT]
>Te elementy nie dołączaj nazwy programów, które jest *nie* aktualizuje wbudowane w system Windows automatycznie aktualizuje oprogramowanie internet lub innych firm, czy są one zainstalowane za pomocą jednego z mechanizmów aktualizacji już wspomniano, lub z Internetu. Tylko zmiany oprogramowania, które są wdrażane jednak uruchomić klienta programu Configuration Manager.

## <a name="before-you-start"></a>Przed rozpoczęciem

Przed skonfigurowaniem lub wdrażanie zasad ochrony urządzeń, przeczytaj następujące informacje:

- Zarządzanie urządzeniami Guard to funkcja wersji wstępnej programu Configuration Manager i może ulec zmianie.
- Do użycia z programem Configuration Manager ochrony urządzeń, komputerów zarządzanych za musi działać system Windows 10 Enterprise w wersji 1703 lub nowszej.
- Po pomyślnym przetwarzania zasad na komputerze klienckim programu Configuration Manager jest skonfigurowany jako zarządzane Instalatora na tym komputerze klienckim, a oprogramowania wdrażanego za pomocą programu SCCM po procesami zasad jest automatycznie zaufany. Oprogramowanie zainstalowane przez zarządzane konfiguracji przed procesami zasad ochrony urządzeń nie jest automatycznie zaufany.
- Komputery klienckie musi mieć łączność z ich kontrolera domeny, aby pomyślnie przetworzone zasady ochrony urządzeń.
- Domyślny harmonogram oceny zgodności dla zasad ochrony urządzeń można skonfigurować podczas wdrażania, jest codziennie. Jeśli problemy podczas przetwarzania zasad, może być korzystne skonfigurować harmonogram oceny zgodności na jest krótszy, na przykład co godzinę. Ten harmonogram Określa, jak często klienci ponowną próbę przetwarzania zasad ochrony urządzeń po awarii.
- Niezależnie od trybu wymuszania z wybranej, podczas wdrażania zasad ochrony urządzeń, komputerach nie można uruchomić aplikacji HTML z HTA rozszerzenia klienta.

## <a name="how-to-create-a-device-guard-policy"></a>Tworzenie zasad ochrony urządzeń
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasady ochrona urządzeń**.
3.  Na **Home** karcie **Utwórz** kliknij przycisk **Utwórz zasady ochrona urządzeń**.
4.  Na **ogólne** strony **urządzenia Guard Kreatora tworzenia zasad**, określ następujące ustawienia:
    - **Nazwa** — wprowadź unikatową nazwę dla tej zasady ochrony urządzeń. 
    - **Opis elementu** — Opcjonalnie wprowadź opis zasad, który ułatwia ich identyfikację w konsoli programu Configuration Manager.
    - **Tryb wymuszania** — wybierz jedną z następujących metod wymuszania dla ochrony urządzeń na komputerze klienckim.
        - **Włączone wymuszania** — tylko Zezwalaj, mogą uruchamiać pliki wykonywalne zaufanych.
        - **Tylko inspekcja** — Zezwalaj na uruchamianie wszystkich plików wykonywalnych, ale dziennika niezaufanych plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń lokalnego klienta.
5.  Na **dołączenia** karcie **urządzenia Guard Kreatora tworzenia zasad**, kliknij przycisk **Dodaj** Jeśli chcesz opcjonalnie Dodaj zaufanie dla określonych plików lub folderów na komputerach. 
6.  W **Dodawanie zaufanego pliku lub folderu** okna dialogowego wprowadź informacje o pliku lub folderu, który ma zostać zaufania. Można określić ścieżkę lokalną pliku lub folderu lub połączyć do zdalnego urządzenia, do którego masz uprawnienia do połączenia i określ ścieżkę pliku lub folderu na tym urządzeniu.
Podczas dodawania relacji zaufania dla określonych plików, folderów w zasadach ochrony urządzeń można wykonywać następujące czynności:
    - Rozwiązać problemy za pomocą zachowań zarządzanych Instalatora
    - Zaufanie aplikacji z biznesowych, których nie można wdrożyć z programu Configuration Manager
    - Zaufanie aplikacji, które są objęte obrazu wdrożenia systemu operacyjnego. 
7.  Kliknij przycisk **dalej**, następnie Zakończ pracę kreatora.

>[!IMPORTANT]
>Włączenie zaufanych plików lub folderów jest obsługiwana tylko na komputerach klienckich z wersją 1706 lub nowszego klienta programu Configuration Manager. Wszystkie reguły dołączania są uwzględnione w zasadach ochrony urządzeń, a następnie wdrożony zasady klienta komputera z systemem starszej wersji klienta programu Configuration Manager, zasady zakończy się niepowodzeniem do zastosowania. Uaktualnianie starszych klientów rozwiąże ten problem. Nadal można stosować zasady, które nie zawierają żadnych reguł dołączania dotyczące starszych wersji klienta programu Configuration Manager.

## <a name="how-to-deploy-a-device-guard-policy"></a>Jak wdrożyć zasady ochrony urządzeń
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasady ochrona urządzeń**.
3.  Z listy zasad, który chcesz wdrożyć, wybierz, a następnie na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.
4.  W **wdrażanie zasad ochrona urządzeń** oknie dialogowym wybierz kolekcję, do której chcesz wdrożyć zasady. Następnie skonfiguruj harmonogram podczas oceny zasad przez klientów. Na koniec wybierz, czy klient może służyć do oceny zasad poza skonfigurowanymi oknami obsługi.
5.  Gdy skończysz, kliknij przycisk **OK** Aby wdrożyć zasady. 

Po przetworzeniu zasad na komputerze klienckim, ponowne uruchomienie zaplanowano na tym komputerze klienckim zgodnie z **ustawień klienta** dla **ponowne uruchomienie komputera**.
Dopiero po ponownym uruchomieniu komputera klienta, zasady nie zostały wprowadzone.

## <a name="how-to-monitor-a-device-guard-policy"></a>Jak monitorować zasady ochrony urządzeń

Skorzystaj z informacji w [monitorować ustawienia zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings) tematu, aby ułatwić sobie monitorowanie, że wdrożone zasady zostały zastosowane do wszystkich komputerów poprawnie.

Aby monitorować przetwarzania zasad ochrony urządzeń, użyj następującego pliku dziennika na komputerach klienckich:

**%Windir%\CCM\Logs\DeviceGuardHandler.log**

Aby zweryfikować określonym oprogramowaniem blokowane lub inspekcji, zobacz następujące dzienników zdarzeń klienta lokalnego:

1.  W przypadku zablokowania i inspekcji plików wykonywalnych, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **integralności kodu** > **Operational**.
2.  Blokowanie i inspekcja Instalatora systemu Windows i pliki skryptów, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **zasad ograniczeń oprogramowania** > **MSI i skrypt**.

## <a name="security-and-privacy-information-for-device-guard"></a>Informacje dotyczące ochrony urządzeń zabezpieczeń i prywatności

- W tej wersji wstępnej, nie należy wdrażać zasady ochrony urządzeń z trybu wymuszania **tylko do inspekcji** w środowisku produkcyjnym. W tym trybie ma na celu ułatwić testowanie możliwości w laboratorium tylko ustawienie.
- Urządzenia, które mają zasad wdrożonych w **tylko do inspekcji** lub **włączone wymuszania** tryb, który nie został uruchomiony ponownie do wymuszania zasad są narażone na niezaufanym oprogramowaniem.
W takim przypadku oprogramowanie mogą nadal mogą być uruchamiane, nawet jeśli urządzenie zostanie uruchomione ponownie, lub otrzymuje zasady w **włączone wymuszania** tryb.
- Aby zapewnić skuteczne zasad ochrony urządzeń, Przygotuj urządzenie w środowisku laboratoryjnym. Następnie Wdróż **włączone wymuszania** zasad, a na koniec ponownie uruchomić urządzenie, zanim przekażesz urządzenia do użytkownika końcowego.
- Nie należy wdrażać zasady z **włączone wymuszania**, a następnie wdrożyć zasady z **tylko do inspekcji** do tego samego urządzenia. Ta konfiguracja może spowodować niezaufanych oprogramowania może działać.
- Korzystając z programu Configuration Manager umożliwia integralności kodu można skonfigurować na kliencie komputerów z zasadami ochrony urządzeń, zasady nie zapobiega użytkowników z uprawnieniami administratora lokalnego obchodzenia zasad ochrony urządzeń lub inny sposób wykonywania niezaufanych oprogramowania. 
- Jest jedynym sposobem, aby uniemożliwić użytkownikom z uprawnieniami administratora lokalnego z wyłączeniem integralności kodu można skonfigurować do wdrażania zasad binarne podpisem. To wdrożenie jest możliwe za pośrednictwem zasad grupy, ale obecnie nieobsługiwane w programie Configuration Manager.
- Ustawienie konfiguracji programu Configuration Manager jako zarządzane Instalatora na komputerach klienckich używane są zasady funkcji AppLocker. Zasady ograniczeń oprogramowania jest używany tylko do identyfikowania instalatorów zarządzane i wszystkie wymuszania sytuacji z integralności kodu można skonfigurować. 




