---
title: Konfigurowanie subskrypcji Lookout
titleSuffix: Configuration Manager
description: Dowiedz się, jak skonfigurować aplikację Lookout przed zagrożeniami przenośnych.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 85c2ae1039058f39bd96c7d0752f798504b0dd4d
ms.sourcegitcommit: 9cff0702c2cc0f214173b47ec241f7e5a40f84e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746114"
---
# <a name="set-up-your-subscription-for-lookout-mobile-threat-defense"></a>Konfigurowanie subskrypcji dla przed zagrożeniami przenośnych Lookout

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniższe kroki są wymagane do skonfigurowania Lookout przenośnych zagrożeń obrony subskrypcji:

| #        |Krok  |
| ------------- |-------------|
| 1 | [Zbieranie informacji o usłudze Azure AD](#collect-azure-ad-information) |
| 2 | [Skonfiguruj subskrypcję](#configure-your-subscription) |
| 3 | [Konfigurowanie grup rejestracji](#configure-enrollment-groups) |
| 4 | [Skonfiguruj stan synchronizacji](#configure-state-sync) |
| 5 | [Skonfiguruj informacje o błędzie raport e-mail adresatów](#configure-error-report-email-recipient-information) |
| 6 | [Skonfiguruj ustawienia rejestracji](#configure-enrollment-settings) |
| 7 | [Skonfiguruj powiadomienia e-mail](#configure-email-notifications) |
| 8 | [Skonfiguruj Klasyfikacja zagrożeń](#configure-threat-classification) |
| 9 | [Obserwowanie rejestracji](#watching-enrollment) |


> [!IMPORTANT]  
> Nie można użyć istniejącej dzierżawy Lookout Mobile punktu końcowego zabezpieczeń nie został jeszcze skojarzony z dzierżawą usługi Azure AD dla integracji z usługą Azure AD i usługi Intune. Skontaktuj się z pomocą techniczną Lookout, aby utworzyć nową dzierżawę Lookout Mobile punktu końcowego zabezpieczeń. Użyj nowej dzierżawy, aby dołączyć użytkowników usługi Azure AD.




## <a name="collect-azure-ad-information"></a>Zbieranie informacji o usłudze Azure AD
Dzierżawy Lookout mobilności punktu końcowego zabezpieczeń zostanie skojarzona z subskrypcją usługi Azure AD do integracji Lookout przy użyciu usługi Intune. Aby włączyć Twojej subskrypcji usługi obrony przenośnych zagrożeń Lookout, obsługa Lookout (enterprisesupport@lookout.com) wymaga następujących informacji:

- **Identyfikator dzierżawy usługi Azure AD**
- **Identyfikator obiektu grupy usługi Active Directory Azure** dla *pełne* Lookout dostępu do konsoli
- **Identyfikator obiektu grupy usługi Active Directory Azure** dla *ograniczeniami* Lookout dostępu do konsoli (opcjonalnie)

Wykonaj następujące kroki, aby zebrać informacje, które należy do zespołu pomocy technicznej Lookout.

1. Zaloguj się do [portalu Azure](https://portal.azure.com) i wyboru subskrypcji. 

2. Po wybraniu nazwę subskrypcji wynikowy adres URL zawiera identyfikator subskrypcji. Jeśli masz problemy znajdowanie identyfikator subskrypcji, zobacz ten [artykuł pomocy technicznej firmy Microsoft](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) dotyczące znajdowania Twojego identyfikatora subskrypcji.

3. Znajdź swój identyfikator grupy usługi Active Directory platformy Azure.  
     > [!NOTE]   
     > **Identyfikator obiektu grupy** znajduje się na **właściwości** strony grupy w bloku usługi Azure AD w portalu Azure.  

   Konsola Lookout obsługuje dwa poziomy dostępu:  

   - **Pełny dostęp:** Administrator usługi Azure AD można utworzyć grupę dla użytkowników, którzy mają pełny dostęp i opcjonalnie utworzyć grupę dla użytkowników, które będą miały ograniczony dostęp. Tylko użytkownicy w tych grupach zarejestrować się w programie **konsoli Lookout**.
   - **Ograniczony dostęp:** Użytkownicy z tej grupy będą mieć nie dostęp do wielu konfiguracji i dotyczące rejestracji modułów konsoli Lookout i mają dostęp tylko do odczytu do **zasady zabezpieczeń** modułu Lookout konsoli.  

     > [!TIP]  
     > Aby uzyskać więcej informacji dotyczących uprawnień, zobacz [ten artykuł pomocy technicznej Lookout](https://personal.support.lookout.com/hc/articles/114094105653).


4. Po po zebraniu tych informacji, skontaktuj się z obsługą Lookout (poczty e-mail: enterprisesupport@lookout.com). Obsługa lookout będzie współpracować kontakt podstawowy, aby dodać subskrypcję i Utwórz konto Lookout przedsiębiorstwa, korzystając z informacji zebranych.



## <a name="configure-your-subscription"></a>Skonfiguruj subskrypcję

1. Gdy Lookout pomocy technicznej utworzy konto Lookout przedsiębiorstwa, z ewentualnym zostanie wysłana wiadomość e-mail do głównej osoby kontaktowej w firmie z łączem do [adres url logowania](https://aad.lookout.com/les?action=consent).

2. Pierwsze logowanie do konsoli Lookout musi być przez przy użyciu konta użytkownika z rolą administratora globalnego dzierżawy usługi Azure AD rejestrowania usługi Azure AD. Później logowania nie wymaga tego poziomu uprawnień usługi Azure AD. Zostanie wyświetlona strona zgody. Wybierz **Akceptuj** do ukończenia rejestracji. Po zaakceptować i wyrazić zgodę, nastąpi przekierowanie do konsoli Lookout.

   ![Zrzut ekranu przedstawiający stronę logowania po raz pierwszy Lookout konsoli](media/lookout-initial-login.png)

3. W [konsoli Lookout](https://aad.lookout.com), z **systemu** modułu, wybierz **łączniki** , a następnie wybierz **Intune**.

   ![Zrzut ekranu konsoli Lookout, otwórz kartę łączników i wyróżnioną opcją usługi Intune](media/lookout-setup-intune-connector.png)

4. Przejdź do **łączniki** > **ustawienia połączenia** i określ **częstotliwość pulsu** w minutach.

   ![Zrzut ekranu przedstawiający kartę Ustawienia połączenia z przedstawiający częstotliwości pulsu skonfigurowanych](media/lookout-connection-settings.png)



## <a name="configure-enrollment-groups"></a>Konfigurowanie grup rejestracji
1. Najlepszym rozwiązaniem, Utwórz grupę zabezpieczeń usługi Azure AD w [portalu Azure](https://portal.azure.com) zawierający niewielkiej liczby użytkowników, aby przetestować aplikację Lookout integracji.

    > [!NOTE]  
    > Wszystkie obsługiwane Lookout, zarejestrowane w usłudze Intune urządzenia użytkowników w grupie rejestracji w usłudze Azure AD, które zostaną rozpoznane i obsługiwane są zarejestrowane i kwalifikuje się do aktywacji w konsoli Lookout od początku miesiąca.

2. W [konsoli Lookout](https://aad.lookout.com), z **systemu** modułu, wybierz **łączniki** , a następnie wybierz **zarządzania rejestracji** do zdefiniowania zestawu użytkowników, których urządzenia powinny zostać zarejestrowane w usłudze Lookout. Dodaj grupę zabezpieczeń usługi Azure AD **Nazwa wyświetlana** do rejestracji.

    ![Zrzut ekranu przedstawiający stronę rejestracji łącznika usługi Intune](media/lookout-enrollment.png)

    >[!IMPORTANT]  
    > **Nazwa wyświetlana** jest rozróżniana wielkość liter, jak pokazano w **właściwości** grupy zabezpieczeń w portalu Azure. Jak przedstawiono na ilustracji poniżej, **Nazwa wyświetlana** zabezpieczeń grupy jest camelcase, gdy tytuł jest małe litery. W konsoli dopasowania Lookout **Nazwa wyświetlana** wielkość dla grupy zabezpieczeń.
    >![Zrzut ekranu portalu Azure, usługa Azure Active Directory, strony właściwości](media/aad-group-display-name.png)

    >[!NOTE]  
    >Najlepszym rozwiązaniem jest użycie domyślnie pięć minut dla przyrost czasu do wyszukania nowych urządzeń. Bieżące ograniczenia **Lookout nie można sprawdzić poprawności nazwy wyświetlania grup:** Upewnij się, **nazwa WYŚWIETLANA** pole w portalu Azure dokładnie odpowiada grupie zabezpieczeń usługi Azure AD. **Tworzenie zagnieżdżania grup nie jest obsługiwana:**  Azure AD zabezpieczeń grupy używane w Lookout musi zawierać tylko użytkowników. Nie mogą zawierać inne grupy.

3.  Po dodaniu grupy, przy następnym otwarciu szukać aplikacji pracy na obsługiwanym urządzeniu urządzenia jest aktywowana w Lookout.

4.  Po przejściu wyniki obejmują rejestracji dodatkowe grupy użytkowników.



## <a name="configure-state-sync"></a>Skonfiguruj stan synchronizacji
W **stan synchronizacji** , należy określić typ danych, które mają być wysyłane do usługi Intune. Zarówno stan urządzenia i stan zagrożenia są wymagane do integracji usługi Intune Lookout działała prawidłowo. Te ustawienia są domyślnie włączone.



## <a name="configure-error-report-email-recipient-information"></a>Skonfiguruj informacje o błędzie raport e-mail adresatów
W **błąd zarządzania** opcji, wprowadź adres e-mail, który powinien zostać wyświetlony raportów o błędach.

![Zrzut ekranu przedstawiający stronę Zarządzanie błąd łącznika usługi Intune](media/lookout-connector-error-notifications.png)



## <a name="configure-enrollment-settings"></a>Skonfiguruj ustawienia rejestracji
W **systemu** modułu na **łączniki** Określ liczbę dni, zanim urządzenie jest uznawane za jako odłączona. Odłączone urządzenia są traktowane jako niezgodne i będą miały zablokowany dostęp do aplikacji firmowych na podstawie zasad dostępu warunkowego programu SCCM. Można określić wartości od 1 do 90 dni.

![Ustawienia rejestracji lookout](media/lookout-console-enrollment-settings.png)



## <a name="configure-email-notifications"></a>Skonfiguruj powiadomienia e-mail
Jeśli chcesz otrzymywać alerty e-mail dotyczące zagrożeń, zaloguj się do [konsoli Lookout](https://aad.lookout.com) przy użyciu konta użytkownika, na który powinny być przesyłane powiadomienia. Na **preferencje** karcie **systemu** modułu, wybierz poziomy zagrożenia, które powinien otrzymywać powiadomienia, a ustawienie dla nich wartości **ON**. Zapisz zmiany.

![Zrzut ekranu przedstawiający stronę preferencji przy użyciu konta użytkownika wyświetlane](media/lookout-email-notifications.png) Jeśli nie chcesz otrzymywać powiadomienia pocztą e-mail powiadomienia ustawiona wartość OFF i Zapisz zmiany.



## <a name="configure-threat-classification"></a>Skonfiguruj Klasyfikacja zagrożeń
Ochrona przed zagrożeniami przenośnych lookout klasyfikuje przenośnych zagrożenia różnych typów. [Lookout zagrożeń klasyfikacje](http://personal.support.lookout.com/hc/articles/114094130693) ma domyślne poziomy ryzyko związane z nimi. Te ustawienia można zmienić w dowolnym momencie ze swoimi potrzebami firmy.

![Zrzut ekranu przedstawiający stronę zasad przedstawiający zagrożeń i klasyfikacji](media/lookout-threat-classification.png)

>[!IMPORTANT]  
> Poziomów ryzyka są istotnym elementem przed zagrożeniami przenośnych. Integracja usługi Intune oblicza zgodności urządzeń zgodnie z tych poziomów ryzyka w czasie wykonywania. Administrator usługi Intune Ustawia regułę zasad, aby zidentyfikować urządzenia jako niezgodne, jeśli urządzenie ma aktywne zagrożeń i co najmniej poziom **wysokiej**, **średni**, lub **małej**. Zasady klasyfikacji zagrożeń w przed zagrożeniami przenośnych Lookout bezpośrednio dysków obliczania zgodności urządzenia w usłudze Intune.



## <a name="watching-enrollment"></a>Obserwowanie rejestracji
Po zakończeniu instalacji przed zagrożeniami przenośnych Lookout uruchamia sondowanie usługi Azure AD dla urządzeń, które odpowiadają grupy określonej rejestracji. Można znaleźć informacje o urządzeniach zarejestrowanych w module urządzeń. Stan początkowy dla urządzeń jest wyświetlany jako oczekujące. Zmiany stanu urządzenia, po zainstalowaniu aplikację Lookout for Work aplikacji otwarty i aktywowana na urządzeniu. Aby uzyskać więcej informacji na temat sposobu uzyskania ewentualnym pracy aplikacji do urządzenia, zobacz [Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych](configure-and-deploy-lookout-for-work-apps.md).


## <a name="next-steps"></a>Następne kroki
[Włącz usługę Lookout MTP połączenie usługi Intune](enable-lookout-connection-in-intune.md)
