---
title: Usługa Windows Defender Advanced Threat Protection
titleSuffix: Configuration Manager
description: Informacje o sposobie monitorowania Windows Defender Advanced Threat Protection, nową usługę, która ułatwia przedsiębiorstwom odpowiadanie na zaawansowanych ataków i zarządzania nimi.
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
ms.openlocfilehash: 84786d741eda2be24a7deb39478e68c68adc38fe
ms.sourcegitcommit: aed99ba3c5e9482199cb3fc5c92f6f3a160cb181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="windows-defender-advanced-threat-protection"></a>Usługa Windows Defender Advanced Threat Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1606 programu Configuration Manager (wersji current branch), program Endpoint Protection może ułatwić zarządzanie i monitorowanie [Windows Defender Advanced Threat Protection (ATP)](http://aka.ms/technet-wdatp). Windows Defender ATP ułatwia przedsiębiorstwom wykrywania, badanie i odpowiadać na zaawansowanych ataków w swoich sieciach.  Zasady programu Configuration Manager lub Microsoft Intune może pomóc dołączyć i monitor zarządzanego systemu Windows 10 w wersji 1607 (kompilacja 14328) lub nowszym.

Program Windows Defender ATP jest usługą [Centrum zabezpieczeń systemu Windows Defender](https://securitycenter.windows.com). Dodawanie i wdrażanie pliku konfiguracji klienta dołączania, programu Configuration Manager można monitorować stan wdrożenia i Windows Defender ATP agent kondycji. Windows Defender ATP jest obsługiwane na komputerach z uruchomionym klientem programu Configuration Manager lub są zarządzane przez program Microsoft Intune, ale nie są obsługiwane komputery zarządzane przez MDM hybrydowe usługi Intune.

 **Wymagania wstępne**  

-   Subskrypcja usługi online Windows Defender Advanced Threat Protection  
-   Komputery klientów z systemem Windows 10, wersji 1607 i nowszych  
-   Komputery klientów uruchomiona wersja programu Configuration Manager 1610 lub nowszych agent klienta lub są zarządzane przez program Microsoft Intune

## <a name="how-to-create-an-onboarding-configuration-file"></a>Jak utworzyć plik konfiguracji dołączania  

 1.  Zaloguj się do [usługi online Windows Defender ATP](https://securitycenter.windows.com/)   

 2.  Polecenie **zarządzania punktu końcowego** elementu menu.  

 3.  Wybierz **wersji System Center Configuration Manager (wersji current branch) 1606** i kliknij przycisk **pakiet pobierania**.  

 4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość.

> [!IMPORTANT]
> Plik konfiguracji programu Windows Defender ATP zawiera poufne informacje, które powinny być zabezpieczone.

## <a name="onboard-devices-for-windows-defender-atp"></a>Urządzenia zintegrowane dla Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **omówienie** > **programu Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **utworzyć zasady usługi Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

2.  Typ **nazwa** i **opis** dla Windows Defender ATP zasad i wybierz **dołączania**. Kliknij przycisk **Dalej**.  

3.  **Przeglądaj** do pliku konfiguracji dostarczane przez dzierżawcę usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

4.  Określ próbki plików, są zbierane i udostępnione z zarządzanych urządzeń do analizy.  

    -   **Brak**   

    -   **Wszystkie typy plików**  

     Kliknij przycisk **Dalej**.  

5.  Przejrzyj podsumowanie, a następnie Zakończ pracę kreatora.  

6.  Teraz można wdrożyć zasady Windows Defender ATP na komputerach klienckich zarządzanych przez kliknięcie przycisku **Wdróż**.  

## <a name="monitor-windows-defender-atp"></a>Monitor usługi Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **monitorowanie** > **omówienie** > **zabezpieczeń** , a następnie kliknij przycisk **Windows Defender ATP**.  

2.  Przejrzyj pulpitu nawigacyjnego systemu Windows Defender Advanced Threat Protection.  

    -   **Stan wdrożenia agenta usługi Windows Defender** — liczbę i odsetek komputerów klientów zarządzanych kwalifikujących się z active został załadowany z zasad programu Windows Defender ATP  

    -   **Kondycja agenta programu Windows Defender ATP** — procent komputerów klienckich raportowanie stanu dla ich agenta Windows Defender ATP  

        -   **Dobra** — działa prawidłowo  

        -   **Nieaktywne** — żadne dane wysyłane do usługi w czasie  

        -   **Stan agenta** — nie jest uruchomiona usługa systemowa programu Agent w systemie Windows  

        -   **Nie został załadowany** — zasady zostały zastosowane, ale agent nie zgłosił dołączyć zasad  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Jak utworzyć i wdrożyć plik konfiguracji zaawansowanej  

1.  Zaloguj się do [usługi online Windows Defender ATP](https://securitycenter.windows.com/)   

2.  Polecenie **zarządzania punktu końcowego** elementu menu.  

3.  Wybierz **wersji System Center Configuration Manager (wersji current branch) 1606** i kliknij przycisk **zaawansowanej punktu końcowego**.  

4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość. Pliki zaawansowanej są ważne przez 30 dni.

5.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **omówienie** > **programu Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **utworzyć zasady usługi Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

6.  Typ **nazwa** i **opis** dla Windows Defender ATP zasad i wybierz **wynoszenia**. Kliknij przycisk **Dalej**.  

7.  **Przeglądaj** do pliku konfiguracji dostarczane przez dzierżawcę usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

8.  Przejrzyj podsumowanie, a następnie Zakończ pracę kreatora.  

9.  Teraz można wdrożyć zasady Windows Defender ATP na komputerach klienckich zarządzanych przez kliknięcie przycisku **Wdróż**.  

> [!IMPORTANT]
> Pliki konfiguracji programu Windows Defender ATP zawiera poufne informacje, które powinny być zabezpieczone.

[Zaawansowana ochrona przed zagrożeniami w usłudze Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Rozwiązywanie problemów przy dołączaniu usługi Windows Defender Advanced Threat Protection](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
