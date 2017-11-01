---
title: Konfiguracja subskrypcji z Lookout
titleSuffix: Configuration Manager
description: "Tematy to szczegółowe informacje na temat konfigurowania ochrony Lookout urządzenia przed zagrożeniami."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 142926bc41a79adc8d8300e413022fb0e3566c5a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Konfigurowanie subskrypcji dla ochrony Lookout urządzenia przed zagrożeniami

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do przygotowania subskrypcji Lookout zagrożenia ochrony usługi urządzeń, obsługę Lookout (enterprisesupport@lookout.com) wymaga następujących informacji o subskrypcji usługi Azure Active Directory (Azure AD). Dzierżawy Lookout mobilności punktu końcowego zabezpieczeń zostanie skojarzona z subskrypcją usługi Azure AD do integracji Lookout przy użyciu usługi Intune. 

* **Identyfikator dzierżawy usługi Azure AD**
* **Identyfikator obiektu grupy usługi Active Directory Azure** dla **pełne** Lookout dostępu do konsoli
* **Identyfikator obiektu grupy usługi Active Directory Azure** dla **ograniczeniami** Lookout dostępu do konsoli (opcjonalnie)

> [!IMPORTANT]
> Nie można użyć istniejącej dzierżawy Lookout Mobile punktu końcowego zabezpieczeń, który nie jest już skojarzony z dzierżawą usługi Azure AD dla integracji z usługą Azure AD i usługi Intune. Skontaktuj się z pomocą techniczną Lookout, aby utworzyć nową dzierżawę Lookout Mobile punktu końcowego zabezpieczeń. Użyj nowej dzierżawy, aby dołączyć użytkowników usługi Azure AD.

Następująca sekcja służy do zbierania informacji, które należy do zespołu pomocy technicznej Lookout.  

## <a name="get-your-azure-ad-information"></a>Uzyskaj informacje w usłudze Azure AD
### <a name="azure-ad-tenant-id"></a>Identyfikator dzierżawy usługi Azure AD
Zaloguj się do [portalu zarządzania usługi Azure AD](https://manage.windowsazure.com) i wyboru subskrypcji. 

![Zrzut ekranu przedstawiający stronę usługi Azure AD, przedstawiający nazwy dzierżawcę](media/aad_tenant_name.png) po wybraniu nazwę subskrypcji wynikowy adres URL zawiera identyfikator subskrypcji.  Jeśli masz problemy znajdowanie identyfikator subskrypcji, zobacz ten [artykuł pomocy technicznej firmy Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) dotyczące znajdowania Twojego identyfikatora subskrypcji.   
### <a name="azure-ad-group-id"></a>Identyfikator grupy usługi Active Directory Azure
Konsola Lookout obsługuje 2 poziomy dostępu:  
* **Pełny dostęp:** Administrator usługi Azure AD można utworzyć grupę dla użytkowników, które będą mieli pełny dostęp i opcjonalnie utworzyć grupę dla użytkowników, które będą miały ograniczony dostęp.  Tylko użytkownicy w tych grupach będą mogli logować się do **konsoli Lookout**.
* **Ograniczony dostęp:** Użytkownicy w tej grupie zostaną nie mają dostępu do kilku konfiguracji i rejestracji powiązane moduły konsoli Lookout i mają dostęp tylko do odczytu do **zasady zabezpieczeń** modułu Lookout konsoli.  

Aby uzyskać więcej informacji dotyczących uprawnień, przeczytaj [w tym artykule](https://personal.support.lookout.com/hc/en-us/articles/114094105653) w witrynie sieci Web Lookout.

**Identyfikator obiektu grupy** znajduje się na **właściwości** strony grupy w **konsoli zarządzania usługą Azure AD**.

![Zrzut ekranu przedstawiający stronę właściwości z polem GroupID wyróżnione](media/aad_group_object_id.png)

Po po zebraniu tych informacji, skontaktuj się z obsługą Lookout (poczty e-mail: enterprisesupport@lookout.com).

Obsługa lookout będzie współpracować kontakt podstawowy, aby dodać subskrypcję i Utwórz konto Lookout przedsiębiorstwa, korzystając z informacji zebranych.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Skonfiguruj subskrypcję z ochrony Lookout urządzenia przed zagrożeniami
### <a name="step-1-set-up-your-device-threat-protection"></a>Krok 1. Konfigurowanie sieci ochrony urządzenia przed zagrożeniami
Gdy Lookout pomocy technicznej utworzy konto Lookout przedsiębiorstwa, można logowania się do konsoli Lookout.   Wiadomość e-mail z ewentualnym są wysyłane do głównej osoby kontaktowej w firmie łącze do adresu url logowania: https://aad.lookout.com/les?action=consent

Podczas pierwszego logowania konsoli Lookout, ponieważ Lookout wymaga te informacje do zarejestrowania dzierżawy usługi Azure AD, należy użyć konta użytkownika z roli Administrator globalny usługi Azure AD.   Kolejne logowania nie wymaga od użytkownika posiadania ten poziom uprawnień usługi Azure AD.  W tym pierwszego logowania zostanie wyświetlona strona zgody. Wybierz **Akceptuj** do ukończenia rejestracji.

![Zrzut ekranu przedstawiający pierwsza strona logowania konsoli Lookout czasu](media/lookout-initial-login.png)

Po zaakceptowane i zgodę, nastąpi przekierowanie do konsoli Lookout. Kolejnych logowań po wstępnej można zrobić za pomocą adresu URL: https://aad.lookout.com

Zobacz [Rozwiązywanie problemów z artykułu]() Jeśli wystąpiły problemy dotyczące logowania.

Następne kroki przedstawiają zadań, które należy wykonać, aby ukończyć Lookout w [konsoli Lookout](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>Krok 2. Konfigurowanie łącznika Intune

1.  W konsoli Lookout z **systemu** modułu, wybierz **łączniki** , a następnie wybierz **Intune**.

  ![Zrzut ekranu konsoli Lookout, otwórz kartę łączników i wyróżnioną opcją usługi Intune](media/lookout-setup-intune-connector.png)

2.  W opcji ustawienia połączenia należy skonfigurować częstotliwość pulsu w minutach.  Z łącznika usługi Intune jest teraz gotowy.  

  ![Zrzut ekranu przedstawiający kartę Ustawienia połączenia z przedstawiający częstotliwości pulsu skonfigurowanych](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>Krok 3. Konfigurowanie grup rejestracji
Na **zarządzania rejestracji** , należy zdefiniować zbioru użytkowników, których urządzenia powinny zostać zarejestrowane w usłudze Lookout. Najlepszym rozwiązaniem jest zaczynać się małą grupę użytkowników do testowania i poznać sposób działania integracji.  Po przejściu wyniki testów można rozszerzyć rejestracji dodatkowych grup użytkowników.

Aby rozpocząć pracę z grupami rejestracji, należy najpierw zdefiniować grupy zabezpieczeń usługi Azure AD, która byłaby dobrej pierwszy zestaw użytkowników, aby zarejestrować się w ochronie przed zagrożeniami Lookout urządzenia. Po utworzeniu grupy utworzone w usłudze Azure AD, w konsoli Lookout, przejdź do **zarządzania rejestracji** , aby dodać grupę zabezpieczeń usługi Azure AD **nazwy wyświetlane** do rejestracji.

Jeśli użytkownik jest w grupie rejestracji, żadnego ze swoich urządzeń, które są zidentyfikowane i obsługiwane w usłudze Azure AD są zarejestrowane i kwalifikuje się do aktywacji w ochronie przed zagrożeniami Lookout urządzenia.  Przy pierwszym otwarciu szukać aplikacji pracy na obsługiwanym urządzeniu urządzenia jest aktywowana w Lookout.

![Zrzut ekranu przedstawiający stronę rejestracji łącznika usługi Intune](media/lookout-enrollment.png)

Najlepszym rozwiązaniem jest używanie domyślnych (5 minut) dla przyrost czasu na sprawdzenie dla nowych urządzeń.

>[!IMPORTANT]
> Nazwa wyświetlana jest uwzględniana wielkość liter.  Użyj **Nazwa wyświetlana** jak pokazano w **właściwości** strony grupy zabezpieczeń w portalu Azure. Uwaga na rysunku poniżej **właściwości** strona grupy zabezpieczeń, nazwa wyświetlana jest camelcase.  Tytuł jednak jest wyświetlana w małe litery i nie należy używać do wprowadzania do konsoli Lookout.
>![Zrzut ekranu portalu Azure, usługa Azure Active Directory, strony właściwości](media/aad-group-display-name.png)

Bieżąca wersja ma następujące ograniczenia:  
* Nie ma żadnych sprawdzania poprawności nazwy wyświetlania grup.  Upewnij się, że należy użyć wartości w **nazwa WYŚWIETLANA** pole widoczne w portalu Azure do grupy zabezpieczeń usługi Azure AD.
* Tworzenie grup w ramach grup nie jest obecnie obsługiwane.  Określone grupy zabezpieczeń usługi Azure AD może zawierać tylko użytkowników i grup zagnieżdżonych nie.


### <a name="step-4-configure-state-sync"></a>Krok 4. Skonfiguruj stan synchronizacji
W **stan synchronizacji** , należy określić typ danych, które mają być wysyłane do usługi Intune.  Obecnie należy włączyć zarówno stanu urządzeń i stanu zagrożeń w kolejności integracji usługi Intune Lookout działała prawidłowo.  Te są domyślnie włączone.
### <a name="step-5-configure-error-report-email-recipient-information"></a>Krok 5. Skonfiguruj informacje o błędzie raport e-mail adresatów
W **błąd zarządzania** opcji, wprowadź adres e-mail, który powinien zostać wyświetlony raportów o błędach.

![Zrzut ekranu przedstawiający stronę Zarządzanie błąd łącznika usługi Intune](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>Krok 6. Skonfiguruj ustawienia rejestracji
W **systemu** modułu na **łączniki** Określ liczbę dni, zanim urządzenie jest uznawane za jako odłączona.  Odłączone urządzenia są traktowane jako niezgodne i będą miały zablokowany dostęp do aplikacji firmowych na podstawie zasad dostępu warunkowego programu SCCM. Można określić wartości od 1 do 90 dni.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>Krok 7. Skonfiguruj powiadomienia e-mail
Jeśli chcesz otrzymywać alerty e-mail dotyczące zagrożeń, zaloguj się do [konsoli Lookout](https://aad.lookout.com) przy użyciu konta użytkownika, na który powinny być przesyłane powiadomienia. Na **preferencje** karcie **systemu** moduł, wybrać żądaną powiadomienia i ustawić ich **ON**. Zapisz zmiany.

![Zrzut ekranu przedstawiający stronę preferencji przy użyciu konta użytkownika wyświetlane](media/lookout-email-notifications.png) Jeśli nie chcesz otrzymywać powiadomienia pocztą e-mail, ustawić powiadomień **OFF** i Zapisz zmiany.
### <a name="step-8-configure-threat-classification"></a>Krok 8. Skonfiguruj Klasyfikacja zagrożeń
Ochrony lookout urządzenia przed zagrożeniami klasyfikuje przenośnych zagrożenia różnych typów. [Lookout zagrożeń klasyfikacje](http://personal.support.lookout.com/hc/en-us/articles/114094130693) ma domyślne poziomy ryzyko związane z nimi. Te można zmienić w dowolnym momencie do zestawu z wymaganiami firmy.

![Zrzut ekranu przedstawiający stronę zasad przedstawiający zagrożeń i klasyfikacji](media/lookout-threat-classification.png)

>[!IMPORTANT]
> Poziomów ryzyka określony w tym miejscu są istotnym elementem ochrony urządzenia przed zagrożeniami, ponieważ integracja usługi Intune oblicza zgodności urządzeń zgodnie z tych poziomów ryzyka w czasie wykonywania. Innymi słowy, administrator usługi Intune Ustawia regułę zasad, aby zidentyfikować urządzenia jako niezgodne, jeśli urządzenie ma aktywne zagrożeń i co najmniej poziom: wysoki, średni lub niski. Zasady klasyfikacji zagrożeń w ochronie przed zagrożeniami Lookout urządzenia bezpośrednio dysków obliczania zgodności urządzenia w usłudze Intune.

## <a name="watching-enrollment"></a>Obserwowanie rejestracji
Po zakończeniu instalacji ochrony Lookout urządzenia przed zagrożeniami uruchamia sondowanie usługi Azure AD dla urządzeń, które odpowiadają grupy określonej rejestracji.  Można znaleźć informacje o urządzeniach zarejestrowanych w module urządzeń.  Stan początkowy dla urządzeń jest wyświetlany jako oczekujące.  Zmiany stanu urządzenia, po zainstalowaniu aplikację Lookout for Work aplikacji otwarty i aktywowana na urządzeniu.  Aby uzyskać szczegółowe informacje dotyczące sposobu uzyskania ewentualnym pracy aplikacji do urządzenia, zobacz [Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych](configure-and-deploy-lookout-for-work-apps.md) tematu.
## <a name="next-steps"></a>Następne kroki
[Włącz usługę Lookout MTP połączenie usługi Intune](enable-lookout-connection-in-intune.md)
