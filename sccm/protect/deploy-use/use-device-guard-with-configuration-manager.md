---
title: Jak zarządzać ochrona urządzeń z systemem Windows
titleSuffix: Configuration Manager
description: Dowiedz się, jak zarządzać ochrona urządzeń z systemem Windows za pomocą programu System Center Configuration Manager.
ms.date: 12/19/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3750e91d96c1ca3eda1ad0ca2fc67b5f627c7a03
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="device-guard-management-with-configuration-manager"></a>Zarządzanie urządzeniami Guard z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

## <a name="introduction"></a>Wprowadzenie
Ochrona urządzeń to grupa funkcji systemu Windows 10, które są przeznaczone do ochrony komputerów przed złośliwym oprogramowaniem i innym oprogramowaniem niezaufanych. Uniemożliwia złośliwy kod działa przez zapewnienie, że tylko zatwierdzone kodu, który znasz, można uruchomić.

Ochrona urządzeń obejmuje zarówno oprogramowania i funkcji zabezpieczeń oparte na sprzęcie. Formant aplikacji systemu Windows Defender to warstwa zabezpieczeń opartych na oprogramowaniu wymusza jawną listę oprogramowania, które można uruchamiać na komputerze. Samodzielnie kontroli aplikacji nie ma wymagań wstępnych sprzętu lub oprogramowania układowego. Zasady kontroli aplikacji wdrożone przez program Configuration Manager Włącz zasad na komputerach w kolekcje docelowe, które spełniają minimalna wersja systemu Windows i SKU wymagania opisane w tym artykule. Opcjonalnie oparta na funkcji hypervisor zasad kontroli aplikacji wdrożony za pomocą programu Configuration Manager można można włączyć ochrony za pomocą zasad grupy w stanie sprzętu.

Aby dowiedzieć się więcej na temat ochrony urządzeń, przeczytaj [przewodnik wdrażania ochrony urządzeń](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

   > [!NOTE]
   > Począwszy od systemu Windows 10 w wersji 1709, zasad integralności kodu można skonfigurować są określane jako formant programu Windows Defender aplikacji.

## <a name="using-device-guard-with-configuration-manager"></a>Przy użyciu ochrony urządzeń z programem Configuration Manager

Aby wdrożyć zasady formant programu Windows Defender aplikacji, można użyć programu Configuration Manager. Ta zasada umożliwia skonfigurowanie tryb, w którym ochrony urządzeń jest uruchamiany na komputerach w kolekcji. 

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
    - Opcjonalnie oprogramowanie z dobrej reputacji określone przez inteligentnego wykres zabezpieczeń (ISG) firmy Microsoft. ISG zawiera Windows Defender SmartScreen i innych usług firmy Microsoft. Urządzenie musi działać program Windows Defender SmartScreen i Windows 10 w wersji 1709 lub później dla tego oprogramowania jako zaufane.

>[!IMPORTANT]
>Te elementy nie dołączaj nazwy programów, które jest *nie* aktualizuje wbudowane w system Windows automatycznie aktualizuje oprogramowanie internet lub innych firm, czy są one zainstalowane za pomocą jednego z mechanizmów aktualizacji już wspomniano, lub z Internetu. Tylko zmiany oprogramowania, które są wdrażane jednak uruchomić klienta programu Configuration Manager.

## <a name="before-you-start"></a>Przed rozpoczęciem

Przed skonfigurowaniem lub wdrożenie zasad sterowania aplikacji programu Windows Defender, przeczytaj następujące informacje:

- Zarządzanie urządzeniami Guard to funkcja wersji wstępnej programu Configuration Manager i może ulec zmianie.
- Do użycia z programem Configuration Manager ochrony urządzeń, komputerów zarządzanych za musi działać system Windows 10 Enterprise w wersji 1703 lub nowszej.
- Po pomyślnym przetwarzania zasad na komputerze klienckim programu Configuration Manager jest skonfigurowany jako zarządzane Instalatora na tym komputerze klienckim. Oprogramowania wdrażanego za jego pośrednictwem po procesami zasad jest automatycznie zaufany. Oprogramowanie instalowane przez program Configuration Manager przed procesami zasad formant programu Windows Defender aplikacji nie jest automatycznie zaufany.
- Komputery klienckie musi mieć łączność z ich kontrolera domeny, aby formant programu Windows Defender aplikacji zasad, aby pomyślnie przetworzone.
- Domyślny harmonogram oceny zgodności zasad kontroli aplikacji, można skonfigurować podczas wdrażania, jest każdy dzień. Jeśli problemy podczas przetwarzania zasad, może być korzystne skonfigurować harmonogram oceny zgodności na jest krótszy, na przykład co godzinę. Ten harmonogram Określa, jak często klienci ponowną próbę przetwarzania zasad formant programu Windows Defender aplikacji, jeśli wystąpi błąd.
- Niezależnie od trybu wymuszania z wybranej, podczas wdrażania zasad formant programu Windows Defender aplikacji, klienta, które komputery nie mogą uruchamiać aplikacji HTML z HTA rozszerzenia.

## <a name="how-to-create-a-windows-defender-application-control-policy"></a>Tworzenie zasad formant programu Windows Defender aplikacji
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **formant programu Windows Defender aplikacji**.
3.  Na **Home** karcie **Utwórz** kliknij przycisk **zasady kontroli aplikacji Utwórz**.
4.  Na **ogólne** strony **zasady kontroli aplikacji utworzyć Kreator**, określ następujące ustawienia:
    - **Nazwa** — wprowadź unikatową nazwę dla tych zasad formant programu Windows Defender aplikacji. 
    - **Opis elementu** — Opcjonalnie wprowadź opis zasad, który ułatwia ich identyfikację w konsoli programu Configuration Manager.
    - **Wymuszanie ponownego uruchomienia urządzenia te zasady można wymusić dla wszystkich procesów** — po przetworzeniu zasad na komputerze klienckim, ponowne uruchomienie zaplanowano na kliencie zgodnie z **ustawień klienta** dla  **Ponowne uruchomienie komputera**.
        - Urządzenia z systemem Windows 10 w wersji 1703 lub starszym będzie automatycznie po ponownym uruchomieniu.
        - Począwszy od systemu Windows 10 w wersji 1709, aplikacje uruchomione na urządzeniu nie będzie miał nowych zasad kontroli aplikacji, stosowane dopiero po ponownym uruchomieniu. Jednak aplikacje uruchamiane po zasady podlegają nowych zasad kontroli aplikacji. 
    - **Tryb wymuszania** — wybierz jedną z następujących metod wymuszania dla ochrony urządzeń na komputerze klienckim.
        - **Włączone wymuszania** — tylko Zezwalaj, mogą uruchamiać pliki wykonywalne zaufanych.
        - **Tylko inspekcja** — Zezwalaj na uruchamianie wszystkich plików wykonywalnych, ale dziennika niezaufanych plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń lokalnego klienta.
5.  Na **dołączenia** karcie **zasady kontroli aplikacji utworzyć Kreator**, wybrać, jeśli chcesz **autoryzować oprogramowania, który jest zaufany przez inteligentnego wykres zabezpieczeń**.
6. Kliknij przycisk **Dodaj** Jeśli chcesz dodać relację zaufania dla określonych plików lub folderów na komputerach. W **Dodawanie zaufanego pliku lub folderu** okno dialogowe, można określić plik lokalny lub ścieżkę folderu zaufania. Można również określić ścieżkę pliku lub folderu na urządzeniu zdalnym, na którym użytkownik ma uprawnienia do połączenia. Po dodaniu zaufania dla określonych plików lub folderów w zasadach formant programu Windows Defender aplikacji można wykonywać następujące czynności:
    - Rozwiązać problemy za pomocą zachowań zarządzanych Instalatora
    - Zaufanie aplikacji z biznesowych, których nie można wdrożyć z programu Configuration Manager
    - Zaufanie aplikacji, które są objęte obrazu wdrożenia systemu operacyjnego. 
8.  Kliknij przycisk **dalej**, aby zakończyć pracę kreatora.

>[!IMPORTANT]
>Włączenie zaufanych plików lub folderów jest obsługiwana tylko na komputerach klienckich z wersją 1706 lub nowszego klienta programu Configuration Manager. Wszystkie reguły dołączania znajdują się w zasadach formant programu Windows Defender aplikacji, a następnie wdrożony zasady klienta komputera z systemem starszej wersji klienta programu Configuration Manager, zasady zakończy się niepowodzeniem do zastosowania. Uaktualnianie starszych klientów rozwiąże ten problem. Nadal można stosować zasady, które nie zawierają żadnych reguł dołączania dotyczące starszych wersji klienta programu Configuration Manager.

## <a name="how-to-deploy-a-windows-defender-application-control-policy"></a>Wdrażanie zasad formant programu Windows Defender aplikacji
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **programu Endpoint Protection**, a następnie kliknij przycisk **formant programu Windows Defender aplikacji**.
3.  Z listy zasad, który chcesz wdrożyć, wybierz, a następnie na **Home** karcie **wdrożenia** kliknij przycisk **wdrażanie zasad kontroli aplikacji**.
4.  W **zasady kontroli aplikacji wdrażanie** oknie dialogowym wybierz kolekcję, do której chcesz wdrożyć zasady. Następnie skonfiguruj harmonogram podczas oceny zasad przez klientów. Na koniec wybierz, czy klient może służyć do oceny zasad poza skonfigurowanymi oknami obsługi.
5.  Gdy skończysz, kliknij przycisk **OK** Aby wdrożyć zasady. 

<!--Reworked article to put this inline while working on VSO 1355092
### Restarting the device after deploying the policy

After the policy is processed on a client PC, a restart is scheduled on that client according to the **Client Settings** for **Computer Restart**. A restart is not required to apply policies, but it is the default. If you want to turn off restarts, follow these steps:

1. Open the **Create Windows Defender Application Policy** wizard.
2. On the **General** page, clear the check box for **Enforce a restart of devices so that this policy can be enforced for all processes**.
3. Click **Next** until the wizard completes.-->


## <a name="how-to-monitor-a-windows-defender-application-control-policy"></a>Jak monitorować zasady formant programu Windows Defender aplikacji

Skorzystaj z informacji w [monitorować ustawienia zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings) artykuł, aby ułatwić sobie monitorowanie, że wdrożone zasady zostały zastosowane do wszystkich komputerów poprawnie.

Do monitorowania przetwarzanie zasad formant programu Windows Defender aplikacji, użyj następującego pliku dziennika na komputerach klienckich:

**%Windir%\CCM\Logs\DeviceGuardHandler.log**

Aby zweryfikować określonym oprogramowaniem blokowane lub inspekcji, zobacz następujące dzienników zdarzeń klienta lokalnego:

1.  W przypadku zablokowania i inspekcji plików wykonywalnych, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **integralności kodu** > **Operational**.
2.  Blokowanie i inspekcja Instalatora systemu Windows i pliki skryptów, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **zasad ograniczeń oprogramowania** > **MSI i skrypt**.

<!--Reworked article to put this inline while working on VSO 1355092
## Automatically let software run if it is trusted by Intelligent Security Graph

You can let locked-down devices run software with a good reputation as determined by the Microsoft Intelligent Security Graph (ISG). The ISG includes [Windows Defender SmartScreen](https://docs.microsoft.com/windows/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) and other Microsoft services. The devices must be running Windows Defender SmartScreen for this software to be trusted.

1. Open the **Create Windows Defender Application Policy** wizard.
2. On the **Inclusions** page, check the box for **Authorize software that is trusted by the Intelligent Security Graph**.
3. Click **Next** until the wizard completes.
-->


## <a name="security-and-privacy-information-for-device-guard"></a>Informacje dotyczące ochrony urządzeń zabezpieczeń i prywatności

- W tej wersji wstępnej, zasady nie są wdrażane formant programu Windows Defender aplikacji z trybu wymuszania **tylko do inspekcji** w środowisku produkcyjnym. W tym trybie ma na celu ułatwić testowanie możliwości w laboratorium tylko ustawienie.
- Urządzenia, które mają zasad wdrożonych w **tylko do inspekcji** lub **włączone wymuszania** tryb, który nie został uruchomiony ponownie, aby wymusić zasady, są podatne na niezaufanym oprogramowaniem.
W takim przypadku oprogramowanie mogą nadal mogą być uruchamiane, nawet jeśli urządzenie zostanie uruchomione ponownie, lub otrzymuje zasady w **włączone wymuszania** tryb.
- Aby upewnić się, że formant programu Windows Defender aplikacji zasad jest skuteczne, Przygotuj urządzenie w środowisku laboratoryjnym. Następnie Wdróż **włączone wymuszania** zasad, a na koniec ponownie uruchomić urządzenie, zanim przekażesz urządzenia do użytkownika końcowego.
- Nie należy wdrażać zasady z **włączone wymuszania**, a następnie wdrożyć zasady z **tylko do inspekcji** do tego samego urządzenia. Ta konfiguracja może spowodować niezaufanych oprogramowania może działać.
- Korzystając z programu Configuration Manager pod kątem umożliwienia kontroli aplikacji systemu Windows Defender komputerom klienckim, zasady nie zapobiega użytkownicy z uprawnieniami administratora lokalnego z obchodzenia zasad kontroli aplikacji lub inny sposób wykonywania niezaufanych oprogramowania. 
- Jedynym sposobem, aby uniemożliwić użytkownikom z uprawnieniami administratora lokalnego z wyłączeniem kontroli aplikacji jest wdrażanie podpisem zasad binarnego. To wdrożenie jest możliwe za pośrednictwem zasad grupy, ale obecnie nieobsługiwane w programie Configuration Manager.
- Ustawienie konfiguracji programu Configuration Manager jako zarządzane Instalatora na komputerach klienckich używane są zasady funkcji AppLocker. Zasady ograniczeń oprogramowania jest używany tylko do identyfikowania instalatorów zarządzane i wszystkie wymuszania sytuacji z aplikacją. 




