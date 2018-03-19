---
title: "Jak zarządzać ochrona urządzeń z systemem Windows"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzać ochrona urządzeń z systemem Windows za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/20/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: 
caps.handback.revision: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 8d84d0d65db7668baa7be9bbf0ad1df869b37919
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="device-guard-management-with-configuration-manager"></a>Zarządzanie urządzeniami Guard z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

## <a name="introduction"></a>Wprowadzenie
Ochrona urządzeń to grupa funkcji systemu Windows 10, które są przeznaczone do ochrony komputerów przed złośliwym oprogramowaniem i innym oprogramowaniem niezaufanych. Uniemożliwia złośliwy kod działa przez zapewnienie, że tylko zatwierdzone kodu, który znasz, można uruchomić.

Ochrona urządzeń obejmuje zarówno oprogramowania i funkcji zabezpieczeń oparte na sprzęcie. Integralność kodu można skonfigurować jest warstwy zabezpieczeń opartych na oprogramowaniu, która wymusza jawną listę oprogramowania, które można uruchamiać na komputerze. Na własną, można skonfigurować kod integralności nie ma wymagań wstępnych sprzętu lub oprogramowania układowego. Zasady formant programu Windows Defender aplikacji wdrożone przez program Configuration Manager umożliwiają zasad integralności kodu można skonfigurować na komputerach w kolekcje docelowe, które spełniają minimalna wersja systemu Windows i SKU wymagania opisane w tym artykule. Opcjonalnie oparta na funkcji hypervisor zasad integralności kodu wdrożony za pomocą programu Configuration Manager można można włączyć ochrony za pomocą zasad grupy w stanie sprzętu.

Aby dowiedzieć się więcej na temat ochrony urządzeń, przeczytaj [przewodnik wdrażania ochrony urządzeń](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

## <a name="using-device-guard-with-configuration-manager"></a>Przy użyciu ochrony urządzeń z programem Configuration Manager

Aby wdrożyć zasady formant programu Windows Defender aplikacji, które można skonfigurować tryb, w którym ochrony urządzeń jest uruchamiany na komputerach w kolekcji, można użyć programu Configuration Manager. 

Można skonfigurować jeden z następujących trybów:

1.  **Wymuszanie włączone** — tylko zaufane, można uruchamiać pliki wykonywalne.
2.  **Tylko inspekcja** — Zezwalaj na uruchamianie wszystkich plików wykonywalnych, ale dziennika niezaufanych plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń lokalnego klienta.

>[!TIP]
>W tej wersji programu Configuration Manager ochrony urządzeń to funkcja wersji wstępnej. Aby ją włączyć, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

## <a name="what-can-run-when-you-deploy-a-windows-defender-application-control-policy"></a>Co można uruchomić podczas wdrażania zasad formant programu Windows Defender aplikacji?

Ochrona urządzeń z systemem Windows umożliwia zdecydowanie kontrolować, jakie można uruchamiać na zarządzanych komputerach. Ta funkcja może być przydatne dla komputerów w działach wysokim poziomie zabezpieczeń, jeśli jest to niezbędne, że nie można uruchomić niechcianego oprogramowania.

Podczas wdrażania zasad, zwykle można uruchomić następujące pliki wykonywalne:

- Składniki systemu Windows
- Centrum deweloperów sprzętu sterowniki (podpisów laboratoria jakości sprzętu dla systemu Windows)
- Aplikacje ze Sklepu Windows
- Klient programu Configuration Manager 
- Całe oprogramowanie wdrożone za pomocą programu Configuration Manager, że komputery instalują po przetworzeniu zasad formant programu Windows Defender aplikacji. 
- Aktualizacje składników systemu windows z:
    - Usługi Windows Update
    - Windows Update dla firm
    - Windows Server Update Services
    - Menedżer konfiguracji

>[!IMPORTANT]
>Te elementy nie dołączaj nazwy programów, które jest *nie* aktualizuje wbudowane w system Windows automatycznie aktualizuje oprogramowanie internet lub innych firm, czy są one zainstalowane za pomocą jednego z mechanizmów aktualizacji już wspomniano, lub z Internetu. Tylko zmiany oprogramowania, które są wdrażane jednak uruchomić klienta programu Configuration Manager.

## <a name="before-you-start"></a>Przed rozpoczęciem

Przed skonfigurowaniem lub wdrożenie zasad sterowania aplikacji programu Windows Defender, przeczytaj następujące informacje:

- Zarządzanie urządzeniami Guard to funkcja wersji wstępnej programu Configuration Manager i może ulec zmianie.
- Do użycia z programem Configuration Manager ochrony urządzeń, komputerów zarządzanych za musi działać system Windows 10 Enterprise w wersji 1703 lub nowszej.
- Po pomyślnym przetwarzania zasad na komputerze klienckim programu Configuration Manager jest skonfigurowany jako zarządzane Instalatora na tym komputerze klienckim, a oprogramowania wdrażanego za pomocą programu SCCM po procesami zasad jest automatycznie zaufany. Oprogramowanie zainstalowane przez zarządzane konfiguracji przed procesami zasad formant programu Windows Defender aplikacji nie jest automatycznie zaufany.
- Komputery klienckie musi mieć łączność z ich kontrolera domeny, aby formant programu Windows Defender aplikacji zasad, aby pomyślnie przetworzone.
- Domyślny harmonogram oceny zgodności zasad kontroli aplikacji Defender systemu Windows, można skonfigurować podczas wdrażania, jest każdy dzień. Jeśli problemy podczas przetwarzania zasad, może być korzystne skonfigurować harmonogram oceny zgodności na jest krótszy, na przykład co godzinę. Ten harmonogram Określa, jak często klienci ponowną próbę przetworzyć zasady formant programu Windows Defender aplikacji po awarii.
- Niezależnie od trybu wymuszania z wybranej, podczas wdrażania zasad formant programu Windows Defender aplikacji, klienta, które komputery nie mogą uruchamiać aplikacji HTML z HTA rozszerzenia.

## <a name="how-to-create-a-windows-defender-application-control-policy"></a>Tworzenie zasad formant programu Windows Defender aplikacji
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasad kontroli aplikacji Defender Windows**.
3.  Na **Home** karcie **Utwórz** kliknij przycisk **zasady tworzenia kontroli aplikacji systemu Windows Defender**.
4.  Na **ogólne** strony **zasad tworzenia kontrolki aplikacji systemu Windows Defender kreatora**, określ następujące ustawienia:
    - **Nazwa** — wprowadź unikatową nazwę dla tych zasad formant programu Windows Defender aplikacji. 
    - **Opis elementu** — Opcjonalnie wprowadź opis zasad, który ułatwia ich identyfikację w konsoli programu Configuration Manager.
    - **Tryb wymuszania** — wybierz jedną z następujących metod wymuszania dla ochrony urządzeń na komputerze klienckim.
        - **Włączone wymuszania** — tylko Zezwalaj, mogą uruchamiać pliki wykonywalne zaufanych.
        - **Tylko inspekcja** — Zezwalaj na uruchamianie wszystkich plików wykonywalnych, ale dziennika niezaufanych plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń lokalnego klienta.
5.  Na **dołączenia** karcie **zasad tworzenia kontrolki aplikacji systemu Windows Defender kreatora**, kliknij przycisk **Dodaj** Jeśli chcesz opcjonalnie Dodaj zaufanie dla określonych plików lub folderów na komputerach. 
6.  W **Dodawanie zaufanego pliku lub folderu** okna dialogowego wprowadź informacje o pliku lub folderu, który ma zostać zaufania. Można określić ścieżkę lokalną pliku lub folderu lub połączyć do zdalnego urządzenia, do którego masz uprawnienia do połączenia i określ ścieżkę pliku lub folderu na tym urządzeniu.
Po dodaniu zaufania dla określonych plików, folderów w zasadach formant programu Windows Defender aplikacji można wykonywać następujące czynności:
    - Rozwiązać problemy za pomocą zachowań zarządzanych Instalatora
    - Zaufanie aplikacji z biznesowych, których nie można wdrożyć z programu Configuration Manager
    - Zaufanie aplikacji, które są objęte obrazu wdrożenia systemu operacyjnego. 
7.  Kliknij przycisk **dalej**, następnie Zakończ pracę kreatora.

>[!IMPORTANT]
>Włączenie zaufanych plików lub folderów jest obsługiwana tylko na komputerach klienckich z wersją 1706 lub nowszego klienta programu Configuration Manager. Wszystkie reguły dołączania znajdują się w zasadach formant programu Windows Defender aplikacji, a następnie wdrożony zasady klienta komputera z systemem starszej wersji klienta programu Configuration Manager, zasady zakończy się niepowodzeniem do zastosowania. Uaktualnianie starszych klientów rozwiąże ten problem. Nadal można stosować zasady, które nie zawierają żadnych reguł dołączania dotyczące starszych wersji klienta programu Configuration Manager.

## <a name="how-to-deploy-a-windows-defender-application-control-policy"></a>Wdrażanie zasad formant programu Windows Defender aplikacji
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **zasad kontroli aplikacji Defender Windows**.
3.  Z listy zasad, który chcesz wdrożyć, wybierz, a następnie na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.
4.  W **zasady wdrażania systemu Windows Defender aplikacji kontroli** oknie dialogowym wybierz kolekcję, do której chcesz wdrożyć zasady. Następnie skonfiguruj harmonogram podczas oceny zasad przez klientów. Na koniec wybierz, czy klient może służyć do oceny zasad poza skonfigurowanymi oknami obsługi.
5.  Gdy skończysz, kliknij przycisk **OK** Aby wdrożyć zasady. 

### <a name="restarting-the-device-after-deploying-the-policy"></a>Ponowne uruchomienie urządzenia po wdrożeniu zasad

Po przetworzeniu zasad na komputerze klienckim, ponowne uruchomienie zaplanowano na tym komputerze klienckim zgodnie z **ustawień klienta** dla **ponowne uruchomienie komputera**. Aby zastosować zasady nie jest wymagane ponowne uruchomienie, ale jest wartość domyślna. Jeśli chcesz wyłączyć zostanie ponownie uruchomiony, wykonaj następujące kroki:

1. Otwórz **utworzyć zasady usługi Windows Defender aplikacji** kreatora.
2. Na **ogólne** Usuń zaznaczenie pola wyboru dla **wymusić ponowne uruchomienie urządzenia, można wymusić te zasady dla wszystkich procesów**.
3. Kliknij przycisk **dalej** aż kreator zakończy pracę.



## <a name="how-to-monitor-a-windows-defender-application-control-policy"></a>Jak monitorować zasady formant programu Windows Defender aplikacji

Skorzystaj z informacji w [monitorować ustawienia zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings) artykuł, aby ułatwić sobie monitorowanie, że wdrożone zasady zostały zastosowane do wszystkich komputerów poprawnie.

Do monitorowania przetwarzanie zasad formant programu Windows Defender aplikacji, użyj następującego pliku dziennika na komputerach klienckich:

**%Windir%\CCM\Logs\DeviceGuardHandler.log**

Aby zweryfikować określonym oprogramowaniem blokowane lub inspekcji, zobacz następujące dzienników zdarzeń klienta lokalnego:

1.  W przypadku zablokowania i inspekcji plików wykonywalnych, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **integralności kodu** > **Operational**.
2.  Blokowanie i inspekcja Instalatora systemu Windows i pliki skryptów, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **zasad ograniczeń oprogramowania** > **MSI i skrypt**.

## <a name="automatically-let-software-run-if-it-is-trusted-by-intelligent-security-graph"></a>Automatyczne przekazywanie oprogramowania uruchomienia, jeśli jest zaufany przez inteligentnego wykres zabezpieczeń

Możesz pozwolić, aby urządzenia zablokowany, uruchom oprogramowanie z dobrej reputacji określone przez inteligentnego wykres zabezpieczeń (ISG) firmy Microsoft. Obejmuje ISG [Windows Defender SmartScreen](https://docs.microsoft.com/windows/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) i innych usług firmy Microsoft. Urządzenia musi być uruchomiony system Windows Defender Smartscreen dla tego oprogramowania jako zaufane.

1. Otwórz **utworzyć zasady usługi Windows Defender aplikacji** kreatora.
2. Na **dołączenia** strony, pole wyboru dla **autoryzować oprogramowania, który jest zaufany przez inteligentnego wykres zabezpieczeń**.
3. W zaufane plików lub folder pole Dodaj pliki i foldery, które mają być zaufane.
4. Kliknij przycisk **dalej** aż kreator zakończy pracę.



## <a name="security-and-privacy-information-for-device-guard"></a>Informacje dotyczące ochrony urządzeń zabezpieczeń i prywatności

- W tej wersji wstępnej, zasady nie są wdrażane formant programu Windows Defender aplikacji z trybu wymuszania **tylko do inspekcji** w środowisku produkcyjnym. W tym trybie ma na celu ułatwić testowanie możliwości w laboratorium tylko ustawienie.
- Urządzenia, które mają zasad wdrożonych w **tylko do inspekcji** lub **włączone wymuszania** tryb, który nie został uruchomiony ponownie do wymuszania zasad są narażone na niezaufanym oprogramowaniem.
W takim przypadku oprogramowanie mogą nadal mogą być uruchamiane, nawet jeśli urządzenie zostanie uruchomione ponownie, lub otrzymuje zasady w **włączone wymuszania** tryb.
- Aby upewnić się, że formant programu Windows Defender aplikacji zasad jest skuteczne, Przygotuj urządzenie w środowisku laboratoryjnym. Następnie Wdróż **włączone wymuszania** zasad, a na koniec ponownie uruchomić urządzenie, zanim przekażesz urządzenia do użytkownika końcowego.
- Nie należy wdrażać zasady z **włączone wymuszania**, a następnie wdrożyć zasady z **tylko do inspekcji** do tego samego urządzenia. Ta konfiguracja może spowodować niezaufanych oprogramowania może działać.
- Korzystając z programu Configuration Manager umożliwia integralności kodu można skonfigurować na kliencie komputerów przy użyciu zasad formant programu Windows Defender aplikacji, zasady nie zapobiega użytkowników z uprawnieniami administratora lokalnego z obejściem aplikacji systemu Windows Defender Zasady kontroli lub wykonywania w przeciwnym razie niezaufanych oprogramowania. 
- Jest jedynym sposobem, aby uniemożliwić użytkownikom z uprawnieniami administratora lokalnego z wyłączeniem integralności kodu można skonfigurować do wdrażania zasad binarne podpisem. To wdrożenie jest możliwe za pośrednictwem zasad grupy, ale obecnie nieobsługiwane w programie Configuration Manager.
- Ustawienie konfiguracji programu Configuration Manager jako zarządzane Instalatora na komputerach klienckich używane są zasady funkcji AppLocker. Zasady ograniczeń oprogramowania jest używany tylko do identyfikowania instalatorów zarządzane i wszystkie wymuszania sytuacji z integralności kodu można skonfigurować. 




