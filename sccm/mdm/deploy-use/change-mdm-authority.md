---
title: Zmienić urzędu zarządzania urządzeniami Przenośnymi
titleSuffix: Configuration Manager
description: Dowiedz się, jak zmienić urząd zarządzania urządzeniami Przenośnymi z programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 04/11/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.openlocfilehash: e5b97ccea5bb6e52badb12f635b5bc97061ca1d1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="change-your-mdm-authority"></a>Zmienić urzędu zarządzania urządzeniami Przenośnymi
Możesz zmienić urzędu zarządzania urządzeniami Przenośnymi bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Ten artykuł zawiera kroki, aby zmienić dzierżawy usługi Microsoft Intune istniejące skonfigurowane z konsoli programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune. Po wykonaniu kroków w tym artykule urządzenia są zarządzane przez program Microsoft Intune w [portalu Azure](https://portal.azure.com). 

> [!Note]    
> Jeśli chcesz zmienić istniejącej dzierżawy Microsoft Intune, przy użyciu zestawu urzędu zarządzania urządzeniami Przenośnymi do usługi Intune, programu Configuration Manager (rozwiązanie hybrydowe), zobacz [zmienić urząd zarządzania urządzeniami Przenośnymi](https://docs.microsoft.com/intune-classic/deploy-use/change-mdm-authority).

> [!Important]    
> W tym artykule jest zmienić urzędu zarządzania urządzeniami Przenośnymi, gdy użytkownicy nie zostały wcześniej migrowane. Aby zmienić urzędu zarządzania urządzeniami Przenośnymi, po [migracji podzbiór użytkowników](migrate-hybridmdm-to-intunesa.md), zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](migrate-change-mdm-authority.md).

## <a name="key-considerations"></a>Najważniejsze kwestie związane z
Po zmianie urząd zarządzania urządzeniami Przenośnymi, należy spodziewać się czas przejścia, maksymalnie ośmiu godzin. Może upłynąć tym długo przed urządzenie sprawdza i synchronizuje się z usługą. Aby upewnić się, zarejestrowane urządzenia są nadal zarządzane i chronione po zmianie, należy skonfigurować ustawienia bezpośrednio w usłudze Intune. Należy uwzględnić następujące kwestie:
- Urządzenia muszą połączyć z usługą po zmianie tak, aby ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi (autonomicznej usługi Intune) Zastąp istniejące ustawienia na urządzeniu.
- Po zmianie urząd zarządzania urządzeniami Przenośnymi, niektóre z podstawowych ustawień (takich jak profile) z poprzednich urząd zarządzania urządzeniami Przenośnymi (rozwiązanie hybrydowe) pozostają na urządzeniu przez maksymalnie 7 dni. Zalecane jest skonfigurowanie aplikacji i ustawień (zasady, profile, aplikacje itd.) nowego urzędu zarządzania urządzeniami Przenośnymi tak szybko, jak to możliwe. Ponadto należy wdrożyć ustawienia dla grupy użytkowników, które zawierają użytkowników, którzy mają istniejących zarejestrowanych urządzeń. Gdy urządzenie łączy się z usługą po zmianie urzędu zarządzania urządzeniami Przenośnymi, odbiera nowe ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi. Wszystkie nowo docelowych zasady zastępują istniejące zasady na urządzeniu.
- Po przejściu do nowego urzędu zarządzania urządzeniami Przenośnymi, dane zgodności w [portalu Azure](https://portal.azure.com) może potrwać do tygodniu, aby dokładnie raportu. Jednak stanów zgodności w usłudze Azure Active Directory i na urządzeniu są prawidłowe. Urządzenie jest nadal chroniony.
- Urządzenia, które nie mają skojarzonych użytkowników nie są migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. To zachowanie jest zwykle gdy masz iOS Device Enrollment Program lub scenariusze rejestracji zbiorczej. Dla tych urządzeń Zadzwoń do pomocy technicznej, aby uzyskać pomoc przenieść je do nowego urzędu zarządzania urządzeniami Przenośnymi.

## <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>Przygotowanie do zmienić urząd zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune
Przejrzyj następujące informacje w celu przygotowania do zmiany urząd zarządzania urządzeniami Przenośnymi:
- Może potrwać maksymalnie osiem godzin dla urządzeń połączyć się z usługą po przejściu do nowego urzędu zarządzania urządzeniami Przenośnymi.
- Upewnij się, że wszyscy użytkownicy, którzy są obecnie zarządzane przez hybrydowego mają licencji usługi Intune/EMS do nich przypisane przed zmianą urzędu zarządzania urządzeniami Przenośnymi. Ta licencja gwarantuje, że użytkownik i ich urządzenia są zarządzane przez autonomicznej usługi Intune po zmianie urzędu zarządzania urządzeniami Przenośnymi. Aby uzyskać więcej informacji, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Upewnij się, że konto użytkownika Administrator ma przypisanej licencji usługi Intune/EMS. Upewnij się, czy konto użytkownika Administrator zalogować się do usługi Intune przed zmianą do urząd zarządzania urządzeniami Przenośnymi. Urząd zarządzania urządzeniami Przenośnymi powinien być wyświetlany **ustawiony program Configuration Manager** (hybrydowego dzierżawcy) w usłudze Intune w [portalu Azure](https://portal.azure.com) przed zmianą urzędu zarządzania urządzeniami Przenośnymi.
- Powinien istnieć bez zauważalnego wpływu użytkownikom końcowym podczas zmiany urzędu zarządzania urządzeniami Przenośnymi. 

## <a name="change-the-mdm-authority-to-intune-standalone"></a>Zmień autonomicznej usługi Intune urząd zarządzania urządzeniami Przenośnymi
Proces można zmienić urząd zarządzania urządzeniami Przenośnymi na autonomicznej usługi Intune obejmuje następujące ogólne kroki:  
- W konsoli programu Configuration Manager za pomocą **zmiany urzędu zarządzania urządzeniami Przenośnymi w usłudze Microsoft Intune** opcję, aby usunąć istniejącą subskrypcję Microsoft Intune.
- W usłudze Intune w [portalu Azure](https://portal.azure.com), konfigurowanie i wdrażanie nowych ustawień i aplikacji z nowego urzędu zarządzania urządzeniami Przenośnymi (Intune).
- Dalej urządzeń czas połączyć się z usługą, zostanie synchronizacji i zastosować nowe ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>Aby zmienić urząd zarządzania urządzeniami Przenośnymi autonomicznej usługi Intune.
1. W konsoli programu Configuration Manager, przejdź do **administracji** &gt; **omówienie** &gt; **usługi w chmurze** &gt; **subskrypcję usługi Microsoft Intune**i usuń istniejącą subskrypcję usługi Intune.
2. Wybierz **zmiany urzędu zarządzania urządzeniami Przenośnymi w usłudze Microsoft Intune**, a następnie kliknij przycisk **dalej**.
   ![Usuń Kreatora subskrypcji usługi Microsoft Intune, strona wprowadzenia](./media/mdm-change-delete-subscription.png)
3. Zaloguj się do dzierżawy usługi Intune, która pierwotnie używana po ustawieniu urzędu zarządzania urządzeniami Przenośnymi w programie Configuration Manager.
4. Kliknij przycisk **Dalej** i ukończ pracę kreatora.
5. Urząd zarządzania urządzeniami Przenośnymi ma teraz wartość **Microsoft Intune**. Subskrypcję usługi Intune nie są wyświetlane w węźle subskrypcje usługi Microsoft Intune w konsoli programu Configuration Manager. 
6. Aby sprawdzić, czy ustawiono urzędu zarządzania urządzeniami Przenośnymi, wykonaj następujące czynności:. Zaloguj się do [portalu Azure](https://portal.azure.com) przy użyciu tej samej dzierżawy usługi Intune, który został wcześniej użyty. 
    b. Wybierz **więcej usług** > **monitorowanie i zarządzanie** > **Intune** > **rejestracji urządzeń**. Urząd zarządzania urządzeniami Przenośnymi jest wyświetlany w prawym górnym rogu sekcji **omówienie** bloku. 

## <a name="next-steps"></a>Następne kroki
Po zakończeniu zmiany urzędu zarządzania urządzeniami Przenośnymi, przejrzyj poniższe kroki:
- Gdy usługi Intune wykryje, że urząd zarządzania urządzeniami Przenośnymi dzierżawy została zmieniona, wysyła powiadomienie do wszystkich zarejestrowanych urządzeń można sprawdzić i zsynchronizować z usługą. To zachowanie jest poza zaplanowanego zaewidencjonowania. W związku z tym po zmianie urząd zarządzania urządzeniami Przenośnymi dla dzierżawcy z hybrydowego do autonomicznej usługi Intune, wszystkie urządzenia, które są zasilane i w trybie online Połącz z usługą, odbierania nowego urzędu zarządzania urządzeniami Przenośnymi i są zarządzane przez autonomiczną usługę Intune. Nie ma żadnych przeszkód do zarządzania i ochrony tych urządzeń.
- Urządzenia, które są zasilane poza lub w trybie offline podczas (lub wkrótce po) Zmień urzędu zarządzania urządzeniami Przenośnymi nawiązać połączenie i synchronizacji z usługi w obszarze nowe urzędu zarządzania urządzeniami Przenośnymi, gdy są włączone i online.  
- Użytkowników można szybko zmienić nowego urzędu zarządzania urządzeniami Przenośnymi należy ręcznie uruchomić ewidencjonowania z urządzenia do usługi. Użytkownicy mogą łatwo wykonać tej akcji przy użyciu aplikacji Portal firmy i zainicjowaniu sprawdzania zgodności urządzenia.
- Aby sprawdzić, czy elementy działają prawidłowo po urządzenia mają zaewidencjonowania i zsynchronizowane z usługą po zmianie urzędu zarządzania urządzeniami Przenośnymi, wyszukaj urządzenia w [portalu Azure](https://portal.azure.com). Urządzenia, które wcześniej były zarządzane przez program Configuration Manager (rozwiązanie hybrydowe) teraz wyświetlane jako zarządzanych urządzeń w usłudze Intune.    
- Brak okres przejściowy, gdy urządzenie jest w trybie offline podczas zmiany urzędu zarządzania urządzeniami Przenośnymi i zaewidencjonowaniu tego urządzenia do usługi. Aby upewnić się, że urządzenie pozostaje chroniony i funkcjonalności w tym okresie przejściowym, następujące profile, pozostają na urządzeniu przez siedem dni (lub dopóki urządzenie łączy się z nowego urzędu zarządzania urządzeniami Przenośnymi i odbiera nowe ustawienia, które Zastąp istniejące te):
    - Profil poczty e-mail
    - Profil sieci VPN
    - Profil certyfikatu
    - Profil sieci Wi-Fi
    - Profilów konfiguracji
- Aby zastąpić ustawienia starego, upewnij się, że nowe ustawienia, które mają na celu zastąpienie istniejących ustawień ma taką samą nazwę jak poprzednie. W przeciwnym razie urządzenia mogą wystąpić nadmiarowe profile i zasady.    

  > [!TIP]   
  > Najlepszym rozwiązaniem należy utworzyć wszystkie ustawienia zarządzania i konfiguracji, a także wdrożeń później, po zakończeniu zmiany urząd zarządzania urządzeniami Przenośnymi. Pomaga to zapewnić, że urządzenia są chronione i aktywnie zarządzana w okresie przejściowym.   
-  Po zmianie urząd zarządzania urządzeniami Przenośnymi, wykonaj następujące kroki, aby sprawdzić poprawność pomyślnie zarejestrowane nowych urządzeń do nowego urzędu certyfikacji:   
    - Zarejestruj nowe urządzenie
    - Upewnij się, że nowo zarejestrowanym urządzeniu zostaną wyświetlone w [portalu Azure](https://portal.azure.com).
    - Wykonaj akcję, takie jak zdalne blokowanie z [portalu Azure](https://portal.azure.com) na urządzeniu. Jeśli ten zakończy się powodzeniem, urządzenie jest zarządzany przez nowego urzędu zarządzania urządzeniami Przenośnymi.
- Jeśli masz problemy z określonymi urządzeniami, Wyrejestrowywanie i Zarejestruj ponownie urządzeń. Ta akcja łączy do nowego urzędu certyfikacji i zarządzane tak szybko, jak to możliwe.
- Jeśli włączono [Android for Work](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client) jako hybrydowego dzierżawy, a następnie przeprowadzić migrację dzierżawy do autonomicznej usługi Intune Android dla pracy ustawienie w obszarze ograniczenia rejestracji mogą być wyświetlane jako zablokowany, a nie zezwala. Ręcznie ustaw ją na **Zezwalaj** ponowne włączenie systemu Android do pracy rejestracji.<!--512117-->