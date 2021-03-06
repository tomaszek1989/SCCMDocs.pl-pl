---
title: Zmienić urzędu zarządzania urządzeniami Przenośnymi do usługi Intune
titleSuffix: Configuration Manager
description: Dowiedz się, jak zmienić urząd zarządzania urządzeniami Przenośnymi z programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune.
author: aczechowski
manager: dougeby
ms.date: 12/05/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: be503ec9-5324-4f7c-bcf5-77204328e99c
ms.openlocfilehash: b295dad503b801ff9d04767f75c1688107016d0b
ms.sourcegitcommit: 493cc42f05b9388ef872e466e5a75d569642b9fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569684"
---
# <a name="change-your-mdm-authority-to-intune-standalone"></a>Zmień urzędu zarządzania urządzeniami Przenośnymi autonomicznej usługi Intune.

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Możesz zmienić dzierżawy usługi Microsoft Intune istniejące skonfigurowane z konsoli programu Configuration Manager (hybrydowego zarządzania urządzeniami Przenośnymi) do autonomicznej usługi Intune. Zmiana urząd zarządzania urządzeniami Przenośnymi na poziomie dzierżawy usługi Intune jest ostatnią fazę procesu w celu [migracji hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune](migrate-hybridmdm-to-intunesa.md) w konfiguracji opartej tylko na chmurze.    

> [!Important]    
> Aby zmienić urzędu zarządzania urządzeniami Przenośnymi bez pierwszy migracji użytkowników hybrydowego zarządzania urządzeniami Przenośnymi usługi Intune, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](change-mdm-authority.md).

W tym artykule wyjaśniono, jak zmienić dzierżawy usługi Microsoft Intune istniejące skonfigurowane z konsoli programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune i przyjęto założenie, że już zostały wykonane następujące kroki:
- Używane [narzędzia importu danych Intune](migrate-import-data.md) do importowania obiektów programu Configuration Manager do usługi Intune. 
- [Przygotowywania migracji użytkownika usługi Intune](migrate-prepare-intune.md) zapewnienie użytkownikom i ich urządzenia będą nadal zarządzane po ich migracji.
- [Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi)](migrate-mixed-authority.md) do rozpoczęcia zarządzania urządzeniami użytkowników w portalu Azure.


## <a name="users-and-devices-that-have-not-been-migrated"></a>Użytkowników i urządzeń, które nie zostały poddane migracji
Już zmigrowane w przypadku wielu użytkowników i przetestować funkcje usługi Intune, aby upewnić się, że elementy działają zgodnie z oczekiwaniami. W związku z tym zasady, profile, aplikacje, itp., zostały skonfigurowane w usłudze Intune i przetestowano obiektów na urządzeniach. Nie powinno być nie nowe konfiguracje wymagane dla zasad na poziomie dzierżawy po zmianie urzędu zarządzania urządzeniami Przenośnymi. Jednak dla użytkowników i urządzeń, które nie zostały już uprzednio zmigrowane, przejrzyj następujące informacje o tym, czego można oczekiwać po zmianie urzędu zarządzania urządzeniami Przenośnymi:    
- Istnieje prawdopodobieństwo, przejście czas (maksymalnie osiem godzin) przed urządzenie sprawdza i synchronizuje się z usługą.
- Urządzenia muszą połączyć z usługą po zmianie tak, aby ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi (autonomicznej usługi Intune) Zastąp istniejące ustawienia na urządzeniu.
- Niektóre z podstawowych ustawień (takich jak profile) z poprzednich urząd zarządzania urządzeniami Przenośnymi (rozwiązanie hybrydowe) pozostają na urządzeniu do siedmiu dni. 
- Urządzenia, które nie mają skojarzonych użytkowników (zazwyczaj gdy masz iOS Device Enrollment Program lub scenariusze rejestracji zbiorczej) nie są migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. Dla tych urządzeń należy się z działem pomocy technicznej, aby uzyskać pomoc przenieść je do nowego urzędu zarządzania urządzeniami Przenośnymi.

## <a name="prerequisites"></a>Wymagania wstępne
Przejrzyj następujące informacje w celu przygotowania do zmiany urząd zarządzania urządzeniami Przenośnymi:
- Musi mieć Configuration Manager w wersji 1610 lub wyższą, aby zmienić urząd zarządzania urządzeniami Przenośnymi, które mają być dostępne.
- Upewnij się, że wszyscy użytkownicy, którzy są obecnie zarządzane przez hybrydowego zarządzania urządzeniami Przenośnymi ma licencję usługi Intune/EMS do nich przypisane przed zmianą urzędu zarządzania urządzeniami Przenośnymi. Licencja gwarantuje, że użytkownik i ich urządzenia są zarządzane przez autonomicznej usługi Intune po zmianie urzędu zarządzania urządzeniami Przenośnymi. Aby uzyskać więcej informacji, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Upewnij się, że konto użytkownika Administrator ma przypisanej licencji usługi Intune/EMS.

## <a name="change-the-mdm-authority-to-intune"></a>Zmienić urząd zarządzania urządzeniami Przenośnymi do usługi Intune
Użyj poniższej procedury można zmienić urząd zarządzania urządzeniami Przenośnymi na poziomie dzierżawy do usługi Intune.

1.  W konsoli programu Configuration Manager, przejdź do **administracji** &gt; **omówienie** &gt; **usługi w chmurze** &gt; **subskrypcję usługi Microsoft Intune**i usuń istniejącą subskrypcję usługi Intune.
2.  Wybierz **zmiany urzędu zarządzania urządzeniami Przenośnymi w usłudze Microsoft Intune**, a następnie kliknij przycisk **dalej**.

    ![Usuń subskrypcję Microsoft Intune w oknie dialogowym](media/mdm-change-delete-subscription.png)
3.  Zaloguj się do dzierżawy usługi Intune, która pierwotnie używana po ustawieniu urzędu zarządzania urządzeniami Przenośnymi w programie Configuration Manager.
4.  Kliknij przycisk **Dalej** i ukończ pracę kreatora.
5.  Urząd zarządzania urządzeniami Przenośnymi została zresetowana. Subskrypcję usługi Intune nie jest już wyświetlane w węźle subskrypcje usługi Microsoft Intune w konsoli programu Configuration Manager.
6.  Zaloguj się do [portalu Intune](https://aka.ms/IntunePortal).
7.  W bloku Microsoft Intune kliknij **rejestracji urządzeń**.
8.  W bloku omówienie rejestracji urządzenia, zobacz **urzędu zarządzania urządzeniami Przenośnymi** właściwości.

  > [!Important]    
  > Nie używaj klasycznego konsoli usługi Intune. Możesz musi zalogować się w usłudze Intune w portalu Azure.
7.  Upewnij się, że urząd MDM został zmieniony na **Microsoft Intune**. 

## <a name="next-steps"></a>Następne kroki
Po zakończeniu zmiany urzędu zarządzania urządzeniami Przenośnymi, przejrzyj następujące informacje:
- Powinien istnieć bez zauważalnego wpływu użytkownikom końcowym podczas zmiany urzędu zarządzania urządzeniami Przenośnymi. 
- Nie trzeba ponownie skonfigurować zasady na poziomie dzierżawy. 
- Po zmianie urzędu zarządzania urządzeniami Przenośnymi można edytować zasad na poziomie dzierżawy z usługi Intune w portalu Azure.
-  Po zmianie urząd zarządzania urządzeniami Przenośnymi, wykonaj następujące kroki, aby sprawdzić poprawność pomyślnie zarejestrowane nowych urządzeń do nowego urzędu certyfikacji:   
    - Zarejestruj nowe urządzenie
    - Upewnij się, że nowo zarejestrowanym urządzeniu są wyświetlane w usłudze Intune.
    - Wykonaj akcję, takie jak zdalne blokowanie za pomocą konsoli administracyjnej na urządzeniu. Jeśli ten zakończy się powodzeniem, urządzenie jest zarządzany przez nowego urzędu zarządzania urządzeniami Przenośnymi.
- Jeśli masz problemy z określonymi urządzeniami, musisz wyrejestrować i Zarejestruj ponownie urządzenia do ich podłączenie do nowego urzędu certyfikacji i zarządzanie nimi tak szybko, jak to możliwe.
- Dla użytkowników i urządzeń, które nie zostały już uprzednio zmigrowane:
    - Sprawdź, czy urządzenia są teraz wyświetlane w **urządzeń** bloku jako zarządzanych urządzeń. Te urządzenia muszą zaewidencjonować i zsynchronizować z usługą po zmianie urzędu zarządzania urządzeniami Przenośnymi, zanim zostaną one wyświetlone. 
    - Gdy usługi Intune wykryje, że urząd zarządzania urządzeniami Przenośnymi dzierżawy została zmieniona, wysyła powiadomienie do wszystkich zarejestrowanych urządzeń można sprawdzić i zsynchronizować z usługą (poza programem zaplanowanego zaewidencjonowania). W związku z tym po urząd zarządzania urządzeniami Przenośnymi dla dzierżawy została zmieniona z hybrydowego do autonomicznej usługi Intune, wszystkie urządzenia, które są zasilane i w trybie online Połącz z usługą, odbierania nowego urzędu zarządzania urządzeniami Przenośnymi i od teraz zarządzane przez autonomiczną usługę Intune. Nie ma żadnych przeszkód do zarządzania i ochrony tych urządzeń.
    - Urządzenia, które są zasilane poza lub w trybie offline podczas (lub wkrótce po) Zmień urzędu zarządzania urządzeniami Przenośnymi nawiązać połączenie i synchronizacji z usługi w obszarze nowe urzędu zarządzania urządzeniami Przenośnymi, gdy są włączone i online.  
    - Użytkowników można szybko zmienić nowego urzędu zarządzania urządzeniami Przenośnymi należy ręcznie uruchomić ewidencjonowania z urządzenia do usługi. Użytkownicy mogą łatwo zaewidencjonować przy użyciu aplikacji Portal firmy i Inicjowanie sprawdzenie zgodności urządzenia.
    - Brak okres przejściowy, gdy urządzenie jest w trybie offline podczas zmiany urzędu zarządzania urządzeniami Przenośnymi i zaewidencjonowaniu tego urządzenia do usługi. Aby upewnić się, że urządzenie pozostaje chroniony i funkcjonalności w tym okresie przejściowym, następujące profile, pozostają na urządzeniu przez siedem dni (lub dopóki urządzenie łączy się z nowego urzędu zarządzania urządzeniami Przenośnymi i odbiera nowe ustawienia, które Zastąp istniejące te):
        - Profil poczty e-mail
        - Profil sieci VPN
        - Profil certyfikatu
        - Profil sieci Wi-Fi
        - Profilów konfiguracji
    - Zadzwoń do pomocy technicznej, aby zmienić urząd zarządzania urządzeniami Przenośnymi dla urządzeń, które nie są skojarzone z użytkownikiem. 
