---
title: "Monitoruj klientów — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Uzyskać szczegółowe wskazówki dotyczące monitorowania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
caps.latest.revision: 23
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 08a4d9b29871b49e3118aef949572cef64940f96
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-in-system-center-configuration-manager"></a>Jak monitorować klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Po zainstalowaniu aplikacji klienta programu System Center Configuration Manager na komputerach z systemem Windows i urządzeń w danej lokacji można monitorować ich kondycji i aktywności w konsoli programu Configuration Manager.  

##  <a name="bkmk_about"></a> Informacje o stanie klienta  
 Menedżer konfiguracji zawiera następujące typy informacji, jak stan klienta:  

-   **Stan online klienta** — począwszy od wersji 1602 programu Configuration Manager, ten stan wskazuje, czy komputer jest online. Komputer jest traktowany jako będący w trybie online, jeśli jest połączony z przypisanym do niego punktem zarządzania.  Aby wskazać, że klient jest w trybie online, wysyła komunikaty ping podobny do punktu zarządzania. Jeśli punkt zarządzania nie odbierze komunikatu w ciągu mniej więcej 5 minut, klient jest traktowany jako będący w trybie offline.  

-   **Aktywność klienta** -ten stan wskazuje, czy klient został aktywnie interesujących z programu Configuration Manager w ciągu ostatnich 7 dni. Jeśli klient nie zażądał aktualizacji zasad, nie wysłał komunikatu z sygnałem pulsu ani nie wysłał informacji spisu sprzętu w ciągu 7 dni, jest traktowany jako nieaktywny.  

-   **Sprawdzanie klienta** -ten stan wskazuje wynik oceny okresowe uruchomioną na komputerze klienta programu Configuration Manager.  Proces oceny sprawdza komputer i może rozwiązać niektóre znalezione problemy. Aby uzyskać więcej informacji, zobacz [Sprawdzenia i korygowania wykonywane przez funkcję sprawdzenia klienta](#BKMK_ClientHealth).  

     Na komputerach z systemem Windows 7 sprawdzanie stanu klienta jest uruchamiane jako zaplanowane zadanie. W przypadku nowszych systemów operacyjnych sprawdzanie stanu klienta jest uruchamiane automatycznie podczas okna obsługi systemu Windows.  

     Korygowanie można skonfigurować w taki sposób, aby nie było uruchamiane na określonych komputerach, na przykład na serwerze krytycznym dla działania firmy. Ponadto jeśli istnieją dodatkowe elementy, które użytkownik chce ocenić, aby uzyskać wszechstronne rozwiązanie służące do monitorowania ogólnej kondycji, aktywności i zgodności komputerów w organizacji można użyć ustawień zgodności programu Configuration Manager. Aby uzyskać więcej informacji dotyczących ustawień zgodności, zobacz [Planowanie i konfigurowania ustawień zgodności w programie System Center Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

##  <a name="bkmk_indStatus"></a> Monitorowanie stanu poszczególnych klientów  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **urządzeń** lub wybierz kolekcję w węźle **kolekcji urządzeń**.  

     Począwszy od wersji 1602 programu Configuration Manager, na początku każdego wiersza wskazują stan online urządzenia:  

    |||  
    |-|-|  
    |![ikona stanu online dla klientów](../../../core/clients/manage/media/online-status-icon.png)|Urządzenie jest w trybie online.|  
    |![ikona stanu offline dla klientów](../../../core/clients/manage/media/offline-status-icon.png)|Urządzenie jest w trybie offline.|  
    |![ikona nieznanego stanu dla klientów](../../../core/clients/manage/media/unknown-status-icon.png)|Stan online jest nieznany.|  
    |![nie zainstalowano klienta](../../../core/clients/manage/media/client-not-installed.png)|Klient nie jest zainstalowany na urządzeniu.|  

2.  Dla bardziej szczegółowy stan online Dodaj informacje o stanie online klienta do widoku urządzenie prawym przyciskiem myszy nagłówek kolumny, a następnie klikając pola stan online, które chcesz dodać. Możesz dodać następujące kolumny  

    -   **Stan online urządzenia** wskazuje, czy klient jest obecnie w trybie online, czy offline. (To te same informacje podane przez ikony).  

    -   **Czas ostatniego stanu online** wskazuje, kiedy stan klienta zmienił się na online.  

    -   **Czas ostatniego stanu offline** wskazuje, kiedy stan klienta zmienił się na offline.  

3.  Kliknij wybranego klienta w okienku listy, aby zobaczyć więcej informacji o stanie w okienku szczegółów, między innymi informacje o aktywności klienta i sprawdzeniach klienta.  

##  <a name="bkmk_allStatus"></a> Monitorowanie stanu wszystkich klientów  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie** > **stanu klienta**. Na tej stronie konsoli możesz przejrzeć ogólne statystyki aktywności klienta i sprawdzeń klienta w lokacji.  Możesz również zmienić zakres informacji, wybierając inną kolekcję.  

2.  Aby przejść do szczegółów na temat statystyki zgłoszone, kliknij nazwę informacje w raporcie (takie jak **aktywnych klientów, które pomyślnie ukończyły sprawdzanie klienta lub nie zwróciło żadnych wyników**) i przejrzyj informacje o poszczególnych klientów.  

3.  Kliknij przycisk **aktywność klienta** aby zobaczyć wykresy przedstawiający aktywność klienta w lokacji programu Configuration Manager.  

4.  Kliknij przycisk **sprawdzanie klienta** aby zobaczyć wykresy przedstawiające stan klienta sprawdza, czy w lokacji programu Configuration Manager.  

 Użytkownik może skonfigurować alerty, które będą powiadamiać o sprawdzaniu wyników przez klientów, jeśli aktywność klienta spadnie poniżej określonego odsetka klientów w kolekcji lub korygowanie nie powiedzie się na określonym odsetku klientów. Aby uzyskać informacje na temat konfigurowania stanu klienta, zobacz [Jak skonfigurować stan klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md).  

##  <a name="BKMK_ClientHealth"></a> Sprawdzenia i korygowania wykonywane przez funkcję sprawdzenia klienta  
 Funkcja sprawdzenia klienta może wykonywać następujące sprawdzania i korygowania:  

|Sprawdzenie klienta|Akcja korygowania|Więcej informacji|  
|------------------|------------------------|----------------------|  
|Weryfikacja, czy funkcja sprawdzenia klienta była ostatnio uruchamiana.|Uruchomienie funkcji sprawdzenia klienta.|Sprawdza, czy funkcja sprawdzenia klienta została uruchomiona co najmniej raz w ciągu ostatnich trzech dni.|  
|Sprawdź, czy wymagania wstępne klienta zostały zainstalowane|Zainstaluj wymagania wstępne klienta|Sprawdź, czy wymagania wstępne klienta zostały zainstalowane. Aby zapoznać się w wymaganiami wstępnymi, odczytaj zawartość pliku ccmsetup.xml w folderze instalacyjnym klienta.|  
|Test integralności repozytorium WMI|Zainstaluj ponownie klienta programu Configuration Manager|Sprawdza, czy pozycje klienta programu Configuration Manager znajdują się w usłudze WMI.|  
|Sprawdź, czy usługa klienta jest uruchomiona.|Uruchom usługę klienta (hosta agenta programu SMS).|Brak dodatkowych informacji|  
|Test obiektów sink zdarzenia WMI.|Uruchom ponownie usługę klienta|Sprawdź, czy obiekt sink zdarzenia WMI jest utracone związane z programu Configuration Manager|  
|Sprawdź, czy istnieje usługa instrumentacji zarządzania Windows (WMI)|Brak korygowania|Brak dodatkowych informacji|  
|Sprawdź, czy usługa klienta jest poprawnie zainstalowana.|Zainstaluj ponownie klienta|Brak dodatkowych informacji|  
|Test odczytu i zapisu repozytorium WMI|Wyzeruj repozytorium WMI i zainstaluj ponownie klienta programu Configuration Manager|Skorygowanie kontroli klienta jest realizowane wyłącznie na komputerach z systemami Windows Server 2003, Windows XP (64-bitowym) i starszych.|  
|Sprawdź, czy usługa oprogramowania chroniącego przed złośliwym kodem jest uruchamiana automatycznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa oprogramowania chroniącego przed złośliwym kodem jest uruchomiona|Uruchom usługę oprogramowania chroniącego przed złośliwym kodem|Brak dodatkowych informacji|  
|Sprawdź, czy usługa Windows Update jest uruchamiana automatycznie, czy ręcznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa klienta (host agenta programu SMS) jest uruchamiana automatycznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa instrumentacji zarządzania Windows (WMI) jest uruchomiona.|Uruchom usługę instrumentacji zarządzania Windows|Brak dodatkowych informacji|  
|Sprawdź, czy baza danych CE Microsoft SQL jest w dobrej kondycji|Zainstaluj ponownie klienta programu Configuration Manager|Brak dodatkowych informacji|  
|Test integralności usługi WMI Microsoft Policy Platform|Przeprowadź naprawę usługi Microsoft Policy Platform|Brak dodatkowych informacji|  
|Sprawdź, czy usługa Microsoft Policy Platform istnieje|Przeprowadź naprawę usługi Microsoft Policy Platform|Brak dodatkowych informacji|  
|Sprawdź, czy usługa Microsoft Policy Platform jest uruchamiana ręcznie|Resetuj typ uruchamiania usługi do ręcznego|Brak dodatkowych informacji|  
|Sprawdź, czy istnieje usługa inteligentnego transferu w tle|Brak korygowania|Brak dodatkowych informacji|  
|Sprawdź, czy usługa inteligentnego transferu w tle jest uruchamiana automatycznie, czy ręcznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa inspekcji sieci jest uruchamiana ręcznie.|Resetuj typ uruchamiania usługi (jeśli jest zainstalowana) do ręcznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa instrumentacji zarządzania Windows (WMI) jest uruchamiana automatycznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa Windows Update na komputerze z systemem Windows 8 jest uruchamiana automatycznie, czy ręcznie|Resetuj typ uruchamiania usługi do ręcznego|Brak dodatkowych informacji|  
|Sprawdź, czy istnieje usługa klienta (hosta agenta programu SMS).|Brak korygowania|Brak dodatkowych informacji|  
|Sprawdź, czy usługa zdalnego sterowania programem Configuration Manager jest uruchamiana automatycznie, czy ręcznie|Resetuj typ uruchamiania usługi do automatycznego|Brak dodatkowych informacji|  
|Sprawdź, czy usługa zdalnego sterowania programem Configuration Manager jest uruchomiona|Uruchom usługę zdalnego sterowania|Brak dodatkowych informacji|  
|Sprawdź, czy dostawca WMI klienta jest w dobrej kondycji|Zrestartuj usługę instrumentacji zarządzania Windows|Skorygowanie kontroli klienta jest realizowane wyłącznie na komputerach z systemami Windows Server 2003, Windows XP (64-bitowym) i starszych.|  
|Sprawdź, czy usługa serwera proxy wzbudzania (serwer proxy programu Configuration Manager) jest uruchomiona|Uruchom usługę serwera proxy programu Configuration Manager|To sprawdzenie odbywa się tylko wtedy, gdy **zarządzania energią**: **Włącz serwer proxy wznawiania** ustawienia klienta jest ustawiona na **tak** w obsługiwanych systemach operacyjnych klienta.|  
|Sprawdź, czy usługa serwera proxy wzbudzania (serwer proxy programu Configuration Manager) jest uruchomiana automatycznie|Resetuj typ uruchamiania usługi serwera proxy programu Configuration Manager do automatycznego|To sprawdzenie odbywa się tylko wtedy, gdy **zarządzania energią**: **Włącz serwer proxy wznawiania** ustawienia klienta jest ustawiona na **tak** w obsługiwanych systemach operacyjnych klienta.|  

## <a name="client-deployment-log-files"></a>Pliki dziennika wdrożenia klienta
Aby uzyskać informacje o plikach dziennika używanych przez wdrożenie klienta i operacji zarządzania, zobacz [pliki dziennika w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs).

