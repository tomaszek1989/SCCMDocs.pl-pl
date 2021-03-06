---
title: Integracja z usługą Windows Update dla Firm w systemie Windows 10
titleSuffix: Configuration Manager
description: Windows Update dla firm umożliwia aktualności urządzeń z systemem Windows 10 w organizacji dla urządzeń połączonych z usługi Windows Update.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.openlocfilehash: 07616a1c03c0383e9001418043dc6cd7ec117c1d
ms.sourcegitcommit: 493cc42f05b9388ef872e466e5a75d569642b9fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703489"
---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Integracja z usługą Windows Update dla Firm w systemie Windows 10

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Usługi Windows Update dla firm (WUfB) pozwala na aktualizowanie urządzenia z systemem Windows 10 w organizacji zawsze zawiera najnowsze zabezpieczenia i funkcje systemu Windows, gdy te urządzenia łączą się bezpośrednio z usługą Windows Update (WU). Programu Configuration Manager może odróżnić komputerów z systemem Windows 10, które używają usług WUfB usług WSUS dotyczące pobierania aktualizacji oprogramowania.  

 Niektóre funkcje programu Configuration Manager nie są już dostępne w przypadku klientów programu Configuration Manager są skonfigurowani do uzyskiwania aktualizacji z usługi WU, która obejmuje usługę WUfB oraz niejawnych testerów systemu Windows:  

-   Raportowanie zgodności z usługą Windows Update:  

    -   Menedżer konfiguracji będzie otrzymywał powiadomień o aktualizacji, które są publikowane w usłudze Windows Update. Wyświetli klientów programu Configuration Manager, konfiguracja zakłada otrzymywanie aktualizacji z usługi WU **nieznany** dla tych aktualizacji w konsoli programu Configuration Manager.  

    -   Rozwiązywanie problemów z ogólny stan zgodności jest trudne ponieważ **nieznany** było w stanie tylko w przypadku klientów, którzy nie zgłosili stanu skanowanie z powrotem z usług WSUS. Teraz obejmuje również klientów programu Configuration Manager, którzy otrzymują aktualizacje z usługi WU.  

    -   Dostęp warunkowy (dla zasobów firmy) na podstawie stanu zgodności aktualizacji nie będzie działać zgodnie z oczekiwaniami w przypadku klientów, którzy otrzymują aktualizacje z usługi WU, ponieważ nigdy nie będą one spełnia zgodności z programu Configuration Manager.  

    -   Zgodność z aktualizacjami definicji jest zgłaszana w ramach raportowania ogólnej zgodności z aktualizacjami i nie będzie działać zgodnie z oczekiwaniami.  Zgodność aktualizacji definicji jest również częścią oceny dostępu warunkowego  

-   Ogólne raportowanie programu Endpoint Protection dla programu Defender na podstawie stanu zgodności aktualizacji nie będzie zwracać prawidłowych wyników z powodu brakujących danych skanowania.  

-   Menedżer konfiguracji nie będzie wdrażać aktualizacji firmy Microsoft, takich jak Office, IE i Visual Studio do klientów, które są podłączone do usługi WUfB w celu odbierania aktualizacji.  

-   Nie będzie mógł wdrożyć 3 aktualizacji firm opublikowany w katalogu WSUS i zarządzane za pomocą programu Configuration Manager do klientów, które są podłączone do usługi WUfB w celu otrzymywania aktualizacji programu Configuration Manager.  

-   Wdrożenie pełnego klienta programu Configuration Manager, który wykorzystuje infrastrukturę aktualizacji oprogramowania nie będzie działać dla klientów, które są podłączone do usługi WUfB w celu odbierania aktualizacji.  

## <a name="identify-clients-that-use-wufb-for-windows-10-updates"></a>Identyfikacja klientów używających usług WUfB dla systemu Windows 10 aktualizacji  
 Poniższa procedura umożliwia zidentyfikowanie klientów, którzy używają usług WUfB w celu uzyskania aktualizacji i uaktualnień systemu Windows 10. Następnie skonfiguruj tych klientów, aby przestały używać usług WSUS, aby pobrać aktualizacje i wdrożyć agenta klienta ustawienie wyłączania przepływu pracy aktualizacji oprogramowania dla tych klientów.  

 **Wymagania wstępne**  

-   Klienci z systemem Windows 10 Desktop Pro lub Windows 10 Enterprise Edition w wersji 1511 lub nowszej  

-   Usługi[Windows Update dla Firm](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) są wdrożone, a klienci używają usług WUfB w celu uzyskiwania aktualizacji i uaktualnień systemu Windows 10.  

#### <a name="to-identify-clients-that-use-wufb"></a>Aby zidentyfikować klientów, którzy używają usług WUfB  

1.  Wyłącz usługi Windows Update Agent, aby nie skanowała usług WSUS, jeśli został wcześniej włączony. Aby wskazać, czy komputer jest skanowane WSUS lub usługi Windows Update można ustawić następujący klucz rejestru.  Gdy wartość jest równa 2, go nie są skanowane usług WSUS.  
    - **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer**

2.  Istnieje nowy atrybut **UseWUServer**w obszarze **usługi Windows Update** węzła w Eksploratorze zasobów programu Configuration Manager.  

3.  Na podstawie atrybutu **UseWUServer** utwórz kolekcję dla wszystkich komputerów połączonych za pośrednictwem usługi Windows Update dla Firm w celu uzyskiwania aktualizacji i uaktualnień.  

4.  Utwórz ustawienie, aby wyłączyć przepływ pracy aktualizacji oprogramowania agenta klienta. Wdróż ustawienie w kolekcji komputerów połączonych bezpośrednio do usługi WUfB.  

5.  Komputery, które są zarządzane za pośrednictwem usług WUfB spowoduje wyświetlenie **nieznany** status zgodności i nie będą uwzględniane jako część ogólnej procent zgodności.  

## <a name="configure-windows-update-for-business-deferral-policies"></a>Konfigurowanie usługi Windows Update dla zasad wykluczenia biznesowych
<!-- 1290890 -->
Począwszy od programu Configuration Manager 1706 wersji, można skonfigurować zasady odroczenia urządzeń aktualizacje funkcji systemu Windows 10 lub jakości aktualizacji dla systemu Windows 10 zarządzane bezpośrednio przez usługę Windows Update dla firm. Zasadami odroczenia można zarządzać w nowym **Windows Update dla firm, zasady** węźle **Biblioteka oprogramowania** > **obsługi systemu Windows 10**.

>[!NOTE] 
>Począwszy od programu Configuration Manager 1802 wersji, można ustawić zasady odroczenia dla wewnętrznego systemu Windows. <!--507201-->Aby uzyskać więcej informacji o programie niejawnego systemu Windows, temacie [wprowadzenie do korzystania z programu niejawnego systemu Windows dla firm](https://docs.microsoft.com/windows/deployment/update/waas-windows-insider-for-business).

### <a name="prerequisites"></a>Wymagania wstępne
-   Windows 10 w wersji 1703 lub nowszy
-   Urządzenia z systemem Windows 10 zarządzane przez usługę Windows Update dla firm musi mieć połączenie z Internetem

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>Aby utworzyć Windows Update dla firm, zasady odroczenia
1. W **Biblioteka oprogramowania** > **obsługi systemu Windows 10** > **usługi Windows Update dla firm zasad**
2. Na **Home** karcie **Utwórz** grupy wybierz **tworzenia usługi Windows Update dla firm zasady** otworzyć utworzyć Windows Update dla firm Kreatora zasad.
3. Na **ogólne** Podaj nazwę i opis zasad.
4. Na **zasady odroczenia** skonfiguruj, czy mają być odroczone lub wstrzymać aktualizacje funkcji. Aktualizacje funkcji są zazwyczaj nowe funkcje w systemie Windows. Po skonfigurowaniu **gałąź gotowości poziom** ustawienie, można zdefiniować czy i jak długo ma być odroczenie odbieranie aktualizacje funkcji po ich dostępności firmy Microsoft.
    - **Gałąź gotowości poziom**: Ustaw gałąź w przypadku którego urządzenia będzie odbierać aktualizacje systemu Windows (Current Branch lub Current Branch for Business).
    - **Okres odroczenia (dni)**:  Określ liczbę dni, dla których aktualizacje funkcji zostanie opóźnione. W przypadku opóźnienia, otrzymywać te aktualizacje funkcji na okres 180 dni od ich wydania.
    - **Uruchamianie funkcji aktualizacji Wstrzymaj**: Określ, czy można wstrzymać urządzeń z otrzymywania aktualizacji funkcji na okres maksymalnie 60 dni od czasu w przypadku wstrzymania aktualizacji. Po upływie maksymalna liczba dni, automatycznie wygaśnie funkcji Wstrzymaj i urządzenia rozpocznie skanowanie aktualizacji do zastosowania aktualizacji systemu Windows. Po tym skanowanie w przypadku wstrzymania aktualizacji ponownie. Aktualizacje funkcji można wznowić, usuwając zaznaczenie pola wyboru.   
5. Określ, czy mają być odroczone lub wstrzymać aktualizacje jakości. Jakość aktualizacji są zwykle poprawki i ulepszenia istniejących funkcji systemu Windows i zwykle są publikowane pierwszy wtorek każdego miesiąca, jednak może być zwolnione w dowolnym momencie przez firmę Microsoft. Można określić, czy i jak długo ma być odroczenie pobiera jakość aktualizacje po ich dostępności.
    - **Okres odroczenia (dni)**: Określ liczbę dni, dla których aktualizacje funkcji zostanie opóźnione. W przypadku opóźnienia, otrzymywać te aktualizacje funkcji na okres 180 dni od ich wydania.
    - **Wstrzymaj aktualizacje jakości uruchamianie**: Określ, czy można wstrzymać urządzeniom otrzymywanie aktualizacji jakości przez okres do 35 dni od czasu w przypadku wstrzymania aktualizacji. Po upływie maksymalna liczba dni, automatycznie wygaśnie funkcji Wstrzymaj i urządzenia rozpocznie skanowanie aktualizacji do zastosowania aktualizacji systemu Windows. Po tym skanowanie w przypadku wstrzymania aktualizacji ponownie. Można wznowić jakości aktualizacji, usuwając zaznaczenie pola wyboru.
6. Wybierz **instalować aktualizacje z innymi Products Microsoft** Aby włączyć ustawienie zasad grupy, która odroczenia ustawienia mające zastosowanie do witryny Microsoft Update, a także aktualizacje systemu Windows.
7. Wybierz **zawierają sterowniki z witryny Windows Update** do automatycznego aktualizowania sterowników z aktualizacji systemu Windows. Jeśli wyczyścisz to ustawienie, aktualizacji sterownika nie można pobrać z witryny Windows Update.
8. Ukończ pracę kreatora, aby utworzyć nowe zasady opóźnienia.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>Do wdrażania aktualizacji systemu Windows dla firm, zasady odroczenia
1. W **Biblioteka oprogramowania** > **obsługi systemu Windows 10** > **usługi Windows Update dla firm zasad**
2. Na **Home** karcie **wdrożenia** grupy wybierz **wdrażania usługi Windows Update dla firm zasady**.
3. Skonfiguruj następujące ustawienia:
    - **Zasady konfiguracji do wdrożenia**: Wybierz usługi Windows Update dla firm zasady, którą chcesz wdrożyć.
    - **Kolekcja**: Kliknij przycisk **Przeglądaj** aby wybrać kolekcję, w której chcesz wdrożyć zasady.
    - **Koryguj niezgodne reguły, jeśli są obsługiwane**: Zaznacz, aby automatycznie korygować wszystkie reguły, które są niezgodne dla Instrumentacji zarządzania Windows (WMI), rejestru, skrypty i wszystkich ustawień dla urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager.
    - **Zezwalaj na korygowanie poza oknem obsługi**: Jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz zasady, Włącz tę opcję, aby pozwolić na korygowanie poza oknem obsługi wartości przy użyciu ustawień zgodności. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).
    - **Generuj alert**: Konfiguruje alert jest generowany, gdy zgodności linii bazowej konfiguracji jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.
    - **Opóźnienie losowe (godziny)**: Określa okno opóźnienia, aby uniknąć nadmiernego przetwarzania w usłudze rejestracji urządzeń sieciowych. Wartość domyślna to 64 godzin.
    - **Harmonogram**: Określ harmonogram oceny zgodności oceny wdrożonego profilu na komputerach klienckich. Harmonogram może być prosty lub niestandardowy. Klienci oceniają profile po zalogowaniu się użytkownika.
4.  Ukończ pracę kreatora, aby wdrożyć profil.
