---
title: "Usługa Windows Defender zaawansowane ochroną | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zarządzać i monitorować zaawansowane zagrożenia ochrony programu Windows Defender, Nowa usługa, która pomaga przedsiębiorstw odpowiadanie na ataki zaawansowane."
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
caps.latest.revision: 5
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 237dc9cbccb973720a633490f096aed4bc16d183
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender zaawansowane ochroną

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1606 programu Configuration Manager (bieżącej gałęzi), program Endpoint Protection może ułatwić zarządzanie i monitorowanie zaawansowane zagrożenia ochrony programu Windows Defender (ATP. Program Windows Defender ATP jest nową usługę, która pomoże przedsiębiorstwa do wykrywania, badanie i reagowania na zaawansowane ataki w ich sieciach.  Dowiedz się więcej o [Windows Defender ATP](http://aka.ms/technet-wdatp). Zasady programu Configuration Manager może pomóc dołączeniu i monitor zarządzanego systemu Windows 10, wersja 1607 (kompilacja 14328) lub nowszy.

Program Windows Defender ATP to usługa w [Centrum zabezpieczeń systemu Windows](https://securitycenter.windows.com). Dodawanie i wdrażanie pliku konfiguracji dołączania klienta, programu Configuration Manager można monitorować stan wdrożenia i kondycja agenta programu Windows Defender ATP. Program Windows Defender ATP jest obsługiwana tylko na komputerach z uruchomionym klientem programu Configuration Manager. Zarządzanie urządzeniami przenośnymi lokalnych i komputery zarządzane MDM hybrydowe Intune nie są obsługiwane.

 **Wymagania wstępne**  

-   Subskrypcja usługi online ochrony zaawansowane zagrożenia programu Windows Defender  

-   Klienci z systemem Windows 10, wersja 1607 i nowsze  

## <a name="how-to-create-an-onboarding-configuration-file"></a>Jak utworzyć plik konfiguracji dołączania  

 1.  Zaloguj się do [usługi online Windows Defender ATP](https://securitycenter.windows.com/)   

 2.  Kliknij **punktu końcowego zarządzania** elementu menu.  

 3.  Wybierz **wersji programu System Center Configuration Manager (bieżącej gałęzi) 1606** i kliknij przycisk **pakiet**.  

 4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość.

> [!IMPORTANT]
> Plik konfiguracji systemu Windows Defender ATP zawiera poufne informacje, które powinny być zabezpieczone.

## <a name="onboard-devices-for-windows-defender-atp"></a>Urządzenia zintegrowane dla programu Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > **Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **Utwórz zasady systemu Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

2.  Typ **nazwa** i **opis** dla systemu Windows Defender ATP zasad i wybierz **dołączania**. Kliknij przycisk **Dalej**.  

3.  **Przeglądaj** do pliku konfiguracji, dostarczone przez dzierżawcy usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

4.  Określ próbki plików, które są zbierane i udostępniane z zarządzanych urządzeń do analizy.  

    -   **Brak**   

    -   **Wszystkie typy plików**  

     Kliknij przycisk **Dalej**.  

5.  Przejrzyj podsumowanie i Zakończ pracę kreatora.  

6.  Teraz można wdrożyć zasady Windows Defender ATP do komputerów klientów zarządzanych przez kliknięcie przycisku **Wdróż**.  

## <a name="monitor-windows-defender-atp"></a>Monitor systemu Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **monitorowanie** > **Przegląd** > **zabezpieczeń** , a następnie kliknij przycisk **Windows Defender ATP**.  

2.  Sprawdź pulpit nawigacyjny ochrony zaawansowane zagrożenia programu Windows Defender.  

    -   **Stan wdrożenia agenta programu Windows Defender** — liczba i procent komputerów klientów zarządzanych kwalifikujących się z aktywnego dołączono maszynę wirtualną systemu Windows Defender ATP zasad  

    -   **Kondycja agenta programu Windows Defender ATP** — procent komputerów klienckich raportowania stanu dla ich agenta programu Windows Defender ATP  

        -   **Dobra** -działa prawidłowo  

        -   **Nieaktywne** -żadne dane wysyłane do usługi w okresie  

        -   **Stan agenta** — usługa systemu dla agenta w systemie Windows nie jest uruchomiona  

        -   **Nie został załadowany** - zastosowania zasad, ale agent nie zgłosił dołączeniu zasad  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Jak utworzyć i wdrożyć plik konfiguracyjny offboarding  

1.  Zaloguj się do [usługi online Windows Defender ATP](https://securitycenter.windows.com/)   

2.  Kliknij **punktu końcowego zarządzania** elementu menu.  

3.  Wybierz **wersji programu System Center Configuration Manager (bieżącej gałęzi) 1606** i kliknij przycisk **offboarding punktu końcowego**.  

4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość. Pliki Offboarding są prawidłowe dla 30 dni.

5.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > **Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **Utwórz zasady systemu Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

6.  Typ **nazwa** i **opis** dla systemu Windows Defender ATP zasad i wybierz **Offboarding**. Kliknij przycisk **Dalej**.  

7.  **Przeglądaj** do pliku konfiguracji, dostarczone przez dzierżawcy usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

8.  Przejrzyj podsumowanie i Zakończ pracę kreatora.  

9.  Teraz można wdrożyć zasady Windows Defender ATP do komputerów klientów zarządzanych przez kliknięcie przycisku **Wdróż**.  

> [!IMPORTANT]
> Pliki konfiguracji systemu Windows Defender ATP zawiera poufne informacje, które powinny być zabezpieczone.

[Usługa Windows Defender zaawansowane ochroną](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Rozwiązywanie problemów dołączania ochrony zaawansowane zagrożenia programu Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)

