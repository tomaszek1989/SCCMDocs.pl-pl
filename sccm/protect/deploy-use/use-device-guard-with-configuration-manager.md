---
title: "Jak zarządzać strażnik urządzenia systemu Windows | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać programu System Center Configuration Manager do zarządzania strażnik urządzeń systemu Windows."
ms.custom: na
ms.date: 04/14/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 49599f529bb409f40caf9057989762e759f1c0ac
ms.openlocfilehash: 113dddb2939fedf24e8d489ff4443bd5e3e72c65
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---


# <a name="device-guard-management-with-configuration-manager"></a>Zarządzanie urządzeniami ochronę za pomocą programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

## <a name="introduction"></a>Wprowadzenie
Strażnik urządzenia systemu Windows jest grupy funkcji systemu Windows 10, opracowane w celu ochrony komputerów przed złośliwym oprogramowaniem i innym oprogramowaniem niezaufanych. Uruchamianie poprzez zapewnienie, że może działać tylko zatwierdzone kod, który znasz, zapobiega złośliwy kod.

Strażnik urządzeń obejmuje sprzętu i oprogramowania na podstawie funkcji zabezpieczeń. Integralności kodu można konfigurować to warstwa zabezpieczeń oparte na oprogramowanie wymusza jawną listę oprogramowania, które można uruchamiać na komputerze. Na własną, można skonfigurować kod integralności nie ma wymagań wstępnych sprzęt lub oprogramowanie układowe. Zasady zabezpieczenia urządzenia wdrożony za pomocą programu Configuration Manager Włącz można skonfigurować zasad integralności kodu na komputerach w kolekcji docelowych, które spełniają wymogi SKU opisane poniżej i minimalnej wersji systemu Windows. Opcjonalnie opartej na funkcji hypervisor ochrony integralności kodu, który zasad wdrożonych za pośrednictwem programu Configuration Manager można włączyć za pomocą zasad grupy dla zaawansowanego sprzętu.

Aby dowiedzieć się więcej o zabezpieczenia urządzenia, przeczytaj [Podręcznik wdrażania strażnik urządzenia](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

Menedżer konfiguracji umożliwia wdrożenie zasad zabezpieczenia urządzenia, które umożliwia skonfigurowanie trybu, w którym strażnik urządzenie będzie uruchamiany na komputerach w kolekcji. 

Można skonfigurować jeden z następujących trybów:

1.    **Wymuszanie włączone** — tylko zaufane, można uruchamiać pliki wykonywalne.
2.    **Tylko inspekcja** — zezwala na wszystkie pliki wykonywalne do uruchomienia, ale niezaufanych dziennika plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń klienta lokalnego.

>[!TIP]
>W tej wersji programu Configuration Manager strażnik urządzenia jest funkcją wersji wstępnej. Aby ją włączyć, zobacz [funkcje w programie System Center Configuration Manager w wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

### <a name="what-can-run-when-you-deploy-a-device-guard-policy"></a>Co można uruchomić w przypadku wdrożenia zasad strażnik urządzenia?

Strażnik urządzenia systemu Windows umożliwia zdecydowanie kontrolę, co można uruchomić na komputerach zarządzania. Może to być szczególnie przydatne w przypadku komputerów w wysokim poziomie zabezpieczeń działów, gdzie jest istotne, czy niechciane oprogramowanie nie może być uruchamiane.

Podczas wdrażania zasad, zazwyczaj następujące pliki wykonywalne będzie mogła działać:

- Składniki systemu Windows
- Centrum deweloperów sprzętu sterowniki (podpisy laboratoria jakości sprzętu dla systemu Windows)
- Aplikacje Sklepu Windows
- Klient programu Configuration Manager 
- Całe oprogramowanie wdrożony za pomocą Menedżera konfiguracji czy komputerami zainstalować po przetworzeniu zasad zabezpieczenia urządzeń. 
- Aktualizacje składników systemu windows z:
    - Usługi Windows Update
    - Aktualizacja systemu Windows dla firm
    - Windows Server Update Services
    - Menedżer konfiguracji

>[!IMPORTANT]
>Nie należą do dowolnego oprogramowania, które jest **nie** wbudowane systemu Windows, która automatycznie aktualizacji z Internetu lub innej oprogramowania aktualizuje instalowane za pośrednictwem tych mechanizmów aktualizacji wymienionych powyżej, lub z Internetu. Tylko zmiany oprogramowania, które są wdrażane jednak klienta programu Configuration Manager będzie mogła działać.

## <a name="before-you-start"></a>Przed rozpoczęciem

Przed skonfigurowaniem lub wdrażania zasad zabezpieczenia urządzenia, należy przeczytać następujące informacje:

- Zarządzanie urządzeniami Strażnik jest funkcją wersji wstępnej programu Configuration Manager i może ulec zmianie.
- Umożliwia zabezpieczenie urządzenia, można zarządzać komputerami musi działać system Windows 10 Enterprise za pomocą aktualizacji twórcy lub nowszej.
- Po pomyślnie przetwarzania zasad na komputerze klienta programu Configuration Manager jest skonfigurowany jako Instalator zarządzane na tym komputerze klienckim, a oprogramowania wdrożonego za pośrednictwem programu SCCM po przetworzeniu zasad jest automatycznie zaufane. Oprogramowanie zainstalowane przez zarządzane konfiguracji przed przetworzeniem zasad strażnik urządzenie nie jest automatycznie zaufany.
- W tej wersji wstępnej gdy komputer klienta otrzymuje wdrożenia zasad zabezpieczenia urządzenia, jego będzie losowo czasu przetwarzania tych zasad w okresie dwóch godzin. 
- Komputery klienckie musi mieć połączenie z ich kontrolera domeny, aby zasady zabezpieczenia urządzenia, aby pomyślnie przetworzone.
- Domyślny harmonogram oceny zgodności dla zasad zabezpieczenia urządzenia, można skonfigurować podczas wdrażania, jest codziennie. Problemy podczas przetwarzania zasady są przestrzegane, może być korzystne skonfigurować harmonogram oceny zgodności, aby być krótszy, na przykład co godzinę. Ten harmonogram decyduje o tym, jak często klienci ponownie spróbuje przetworzyć zasady zabezpieczenia urządzenia, w przypadku awarii.
- Niezależnie od trybu wymuszania wybór podczas wdrażania zasad zabezpieczenia urządzenia, komputerom klienckim nie będzie mógł uruchamiać aplikacje HTML z HTA rozszerzenia.

## <a name="how-to-create-a-device-guard-policy"></a>Tworzenie zasad zabezpieczenia urządzeń
1.    W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.    W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **Endpoint Protection**, a następnie kliknij przycisk **zasady zabezpieczenia urządzenia**.
3.    Na **Home** w karcie **Utwórz** , kliknij przycisk **Utwórz zasady zabezpieczenia urządzenia**.
4.    Na **ogólne** strony **Kreatora zasad tworzenia strażnik urządzenia**, podaj następujące informacje:
    - **Nazwa** — wprowadź unikatową nazwę dla tej zasady zabezpieczenia urządzeń. 
    - **Opis** — Opcjonalnie wprowadź opis zasad, które pomagają zidentyfikować go w konsoli programu Configuration Manager.
    - **Tryb wymuszania** -wybierz jedną z następujących metod wymuszania dla strażnik urządzenia na komputerze klienta.
        - **Włączono wymuszania** — tylko Zezwalaj można uruchamiać pliki wykonywalne zaufany.
        - **Tylko inspekcja** — zezwala na wszystkie pliki wykonywalne do uruchomienia, ale niezaufanych dziennika plików wykonywalnych, które są uruchamiane w dzienniku zdarzeń klienta lokalnego.
5.    Kliknij przycisk **dalej**, następnie Zakończ pracę kreatora.

## <a name="how-to-deploy-a-device-guard-policy"></a>Wdrażanie zasad zabezpieczenia urządzeń
1.    W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2.    W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **Endpoint Protection**, a następnie kliknij przycisk **zasady zabezpieczenia urządzenia**.
3.    Na liście zasad, który chcesz wdrożyć, wybierz opcję, a następnie na **Home** w karcie **wdrożenia** , kliknij przycisk **Wdróż**.
4.    W **wdrożyć zasady strażnik urządzeń** okno dialogowe, wybierz kolekcję, do której chcesz wdrożyć zasady, skonfigurować harmonogram po klientów będzie oceniać zasady, a na koniec należy określić, czy klient może służyć do oceny zasad poza skonfigurowanymi oknami obsługi.
5.    Gdy skończysz, kliknij przycisk **OK** Aby wdrożyć zasady. 

Po przetworzeniu zasady na komputerze klienta, ponowne uruchomienie komputera zostanie zaplanowane na tym komputerze klienckim, zgodnie z **ustawień klienta** dla **ponowne uruchomienie komputera**.
**Dopiero po ponownym uruchomieniu komputera klienta, zasady nie zostaną zastosowane.**

## <a name="how-to-monitor-a-device-guard-policy"></a>Monitorowanie zasad zabezpieczenia urządzeń

Informacje zawarte w [monitorowania ustawień zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings) tematów, które pomagają monitorować wdrożone zasady, aby upewnić się, że został zastosowany do wszystkich komputerów poprawnie.

Następujący plik dziennika na komputerach klienckich należy używać do monitorowania przetwarzanie zasad strażnik urządzenia:

**%Windir%\CCM\Logs\DeviceGuardHandler.log**

Aby sprawdzić określone oprogramowanie jest zablokowane lub inspekcji, zobacz następujące dzienników zdarzeń klienta lokalnego. W Podglądzie zdarzeń odpowiedniego dzienniki są następujące:

1.    Do blokowania i inspekcji plików wykonywalnych, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **integralności kodu** > **działa**.
2.    Do blokowania i inspekcji Instalatora Windows i pliki skryptów, użyj **Dzienniki aplikacji i usług** > **Microsoft** > **Windows** > **AppLocker** > **MSI i skrypt**.

## <a name="security-and-privacy-information-for-device-guard"></a>Informacje o zabezpieczeniach i prywatności dla urządzenia strażnik

- W tej wersji wstępnej, zasady nie są wdrażane strażnik urządzenia w trybie wymuszania **inspekcji tylko** w środowisku produkcyjnym. Ten tryb jest przeznaczony do pomagają testować możliwości w laboratorium tylko ustawienie.
- Urządzenia, które są wdrożone w zasady **inspekcji tylko** tryb lub urządzenia, które są wdrożone w zasady **włączone wymuszania** tryb, który nie ma jeszcze ponownie uruchomiony do wymuszania zasad są podatne na niezaufanym oprogramowaniem.
W takiej sytuacji oprogramowania mogą w dalszym ciągu mogła być uruchamiana, nawet w przypadku ponownego uruchomienia urządzenia lub otrzymuje zasady w **włączone wymuszania** tryb.
- W celu zapewnienia skuteczności zasady zabezpieczenia urządzenia, Przygotuj urządzenie w środowisku laboratoryjnym, wdrożyć **włączone wymuszania** zasad, a następnie ponowne uruchomienie urządzenia przed udostępnieniem urządzenia do użytkownika końcowego.
- Nie należy wdrażać zasady z **włączone wymuszania**, a następnie wdrożyć zasady z **inspekcji tylko** na tym samym urządzeniu. Może to spowodować niezaufanych oprogramowania może działać.
- Gdy używasz programu Configuration Manager w celu włączenia integralności kodu można skonfigurować na kliencie komputerami za pomocą zasad zabezpieczenia urządzenia, należy pamiętać, że zasady **nie** uniemożliwić użytkownikom z uprawnieniami administratora lokalnego z obejścia zasad strażnik urządzenia lub w inny sposób wykonywania niezaufanym oprogramowaniem. 
- Jedynym sposobem, aby uniemożliwić użytkownikom z uprawnieniami administratora lokalnego z wyłączeniem integralności kodu można konfigurować jest wdrożenie podpisem zasadę binarny, która jest możliwa za pomocą zasad grupy, ale nie jest obecnie obsługiwany w programie Configuration Manager.
- Ustawianie Konfigurowanie programu Configuration Manager jako zarządzane Instalatora na komputerach klienckich używa zasady zasad ograniczeń oprogramowania. Zasady ograniczeń oprogramowania jest używany tylko do identyfikowania instalatorów zarządzane i wymuszania wszystkie konsekwencje z integralności kodu można konfigurować. 





