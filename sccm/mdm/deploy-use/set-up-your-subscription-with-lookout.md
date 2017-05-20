---
title: Konfiguracja subskrypcji z ewentualnym | System Center Configuration Manager
description: "Ten temat zawiera szczegółowe informacje dotyczące sposobu konfigurowania urządzenia szczególną ochroną."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: b777140c753e709f4048a30e63d8ae730d3e8723
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Skonfiguruj subskrypcję dla urządzenia szczególną ochroną

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Uzyskanie subskrypcji gotowy ewentualnym zagrożenia ochrony usługi urządzeń, obsługa ewentualnym (enterprisesupport@lookout.com) wymaga następujących informacji o subskrypcji usługi Azure Active Directory (Azure AD). Dzierżawcy ewentualnym mobilności punktu końcowego zabezpieczeń zostaną skojarzone z subskrypcją usługi Azure AD do integracji z usługą Intune szczególną. 

* **Identyfikator dzierżawcy usługi Azure AD**
* **Identyfikator obiektu grupy usługi Active Directory Azure** dla **pełne** ewentualnym dostępu do konsoli
* **Identyfikator obiektu grupy usługi Active Directory Azure** dla **ograniczone** ewentualnym dostępu do konsoli (opcjonalnie)

> [!IMPORTANT]
> Nie można użyć istniejącej dzierżawy ewentualnym Mobile punktu końcowego zabezpieczeń, który nie jest już skojarzony z dzierżawą usługi Azure AD dla integracji z usługą Azure AD i usługi Intune. Skontaktuj się z ewentualnym Obsługa tworzenia nowego dzierżawcy ewentualnym Mobile punktu końcowego zabezpieczeń. Użyj nowego dzierżawcy w celu dołączenia użytkowników usługi Azure AD.

Aby zebrać informacje potrzebne do zespołu pomocy technicznej szczególną za pomocą następujących sekcji.  

## <a name="get-your-azure-ad-information"></a>Uzyskaj informacje w usłudze Azure AD
### <a name="azure-ad-tenant-id"></a>Identyfikator dzierżawcy usługi Azure AD
Zaloguj się do [portalu zarządzania Azure AD](https://manage.windowsazure.com) i wybierz subskrypcję. 

![Zrzut ekranu przedstawiający nazwę dzierżawy strony Azure AD](media/aad_tenant_name.png) po wybraniu Nazwa subskrypcji wynikowy adres URL zawiera identyfikator subskrypcji.  Jeśli masz problemy znajdowanie identyfikator subskrypcji, zobacz ten [artykuł pomocy technicznej firmy Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) porady dotyczące znajdowania identyfikatora subskrypcji   
### <a name="azure-ad-group-id"></a>Identyfikator grupy usługi Active Directory Azure
Konsola ewentualnym obsługuje 2 poziomy dostępu:  
* **Pełny dostęp:** Administrator usługi Azure AD można utworzyć grupę użytkowników, którzy będą mieć pełny dostęp i opcjonalnie utworzyć grupę użytkowników, którzy mają ograniczony dostęp.  Tylko użytkownicy w tych grupach będą mogli logować się do **konsoli ewentualnym**.
* **Dostęp ograniczony:** Użytkownicy w tej grupie będą nie mają dostępu do kilku konfiguracji i rejestracji związane z modułów konsoli ewentualnym oraz mają dostęp tylko do odczytu do **zasady zabezpieczeń** modułu ewentualnym konsoli.  

Więcej informacji dotyczących uprawnień odczytu [w tym artykule](https://personal.support.lookout.com/hc/en-us/articles/114094105653) w witrynie sieci Web szczególną.

**Identyfikator obiektu grupy** na **właściwości** strony grupy w **konsoli zarządzania usługi Azure AD**.

![Zrzut ekranu strony właściwości z polem GroupID wyróżnione](media/aad_group_object_id.png)

Po zgromadzeniu tych informacji, skontaktuj się z obsługą ewentualnym (adres e-mail: enterprisesupport@lookout.com).

Obsługa ewentualnym będzie pracować z głównej kontakt, aby dołączyć subskrypcji i Utwórz konto ewentualnym przedsiębiorstwa, korzystając z informacji zebranych.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Konfigurowanie subskrypcji z ochroną ewentualnym urządzenia
### <a name="step-1-set-up-your-device-threat-protection"></a>Krok 1: Konfigurowanie urządzeń zagrożenia bezpieczeństwa
Po ewentualnym Obsługa tworzy Enterprise ewentualnym konta, należy zarejestrować się w programie ewentualnym konsoli.   Jest wysyłana wiadomość e-mail z ewentualnym do głównej osoby kontaktowej w firmie za pomocą łącza do adresu url logowania: https://aad.lookout.com/les?action=consent

Podczas pierwszego logowania konsoli szczególną, ponieważ ewentualnym wymaga tych informacji, aby zarejestrować swoje dzierżawy usługi Azure AD, należy użyć konta użytkownika z roli administratora globalnego usługi Azure AD.   Kolejne logowania nie zażąda od użytkownika posiadania ten poziom uprawnień Azure AD.  W tym pierwszego logowania zostanie wyświetlona strona zgody użytkownika. Wybierz **Akceptuj** do ukończenia rejestracji.

![Zrzut ekranu pierwszej strony logowania czasu ewentualnym konsoli](media/lookout-initial-login.png)

Po zaakceptowane i zgodę, nastąpi przekierowanie do konsoli szczególną. Kolejne logowania po wstępnej jest możliwe przy użyciu adresu URL: https://aad.lookout.com

Zobacz [Rozwiązywanie problemów z artykułu]() Jeśli wystąpią problemy dotyczące logowania.

Następne kroki wchodzą w skład zadania, które należy wykonać, aby ukończyć szczególną w [konsoli ewentualnym](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>Krok 2: Skonfiguruj łącznik usługi Intune

1.  W konsoli ewentualnym z **systemu** modułu, wybierz **łączniki** , a następnie wybierz **Intune**.

  ![Zrzut ekranu konsoli szczególną, otwórz kartę łączników i zaznaczoną opcją Intune](media/lookout-setup-intune-connector.png)

2.  W opcji ustawienia połączenia skonfiguruj częstotliwość pulsu w minutach.  Łącznik programu Intune jest teraz gotowy.  

  ![Zrzut ekranu karty Ustawienia połączenia z przedstawiający częstotliwość pulsu skonfigurowane](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>Krok 3: Konfigurowanie grup rejestracji
Na **zarządzania rejestracji** , a następnie zdefiniuj zestawu użytkowników, których urządzenia powinny być zarejestrowane w usłudze szczególną. Najlepszym rozwiązaniem jest rozpoczynać małe grupy użytkowników do testowania i zapoznanie się z działaniem integracji.  Po otwarciu wyników testu można rozszerzyć rejestracji dla dodatkowych grup użytkowników.

Aby rozpocząć rejestracje grup, należy najpierw zdefiniować grupy zabezpieczeń usługi Azure AD, która byłaby dobrej pierwszy zestaw użytkowników do rejestrowania w szczególną ochroną urządzenia. Po utworzeniu grupy utworzone w usłudze Azure AD, w konsoli szczególną, przejdź do **zarządzania rejestracji** opcję i dodać do grupy zabezpieczeń usługi Azure AD **nazwy wyświetlane** do rejestracji.

Gdy użytkownik znajduje się w grupie rejestracji, żadnego ze swoich urządzeń, które są zidentyfikowane i obsługiwane w usłudze Azure AD są zarejestrowane i kwalifikuje się do aktywacji w szczególną ochroną urządzenia.  Przy pierwszym otwarciu szukać pracy aplikacji na urządzeniu obsługiwane urządzenia jest aktywowana w ewentualnym.

![Zrzut ekranu strony rejestracji łącznik usługi Intune](media/lookout-enrollment.png)

Najlepszym rozwiązaniem jest użycie domyślnego (5 minut) dla przyrost czasu na sprawdzenie dla nowych urządzeń.

>[!IMPORTANT]
> Nazwa wyświetlana jest uwzględniana wielkość liter.  Użyj **Nazwa wyświetlana** jak pokazano w **właściwości** strony grupy zabezpieczeń w portalu Azure. Uwaga na ilustracji poniżej **właściwości** strony grupy zabezpieczeń, nazwa wyświetlana jest camelcase.  Jednak tytuł jest wyświetlana w wszystkie małe litery i nie powinna być używana do wprowadzania do konsoli szczególną.
>![Zrzut ekranu przedstawiający portalu Azure, usługi Azure Active Directory, strony właściwości](media/aad-group-display-name.png)

Bieżąca wersja ma następujące ograniczenia:  
* Nie ma żadnych sprawdzania poprawności nazwy wyświetlane grupy.  Upewnij się, że użycie wartości w **nazwa WYŚWIETLANA** pole widoczne w portalu Azure dla grupy zabezpieczeń usługi Azure AD.
* Tworzenie grupy w grupach nie jest obecnie obsługiwane.  Określony Azure grup zabezpieczeń usługi Active Directory może zawierać tylko użytkownicy i grupy zagnieżdżone nie.


### <a name="step-4-configure-state-sync"></a>Krok 4: Skonfiguruj stan synchronizacji
W **stan synchronizacji** , określ typ danych, które powinny być przesyłane do usługi Intune.  Obecnie należy włączyć zarówno stanu urządzeń i stan zagrożenia w kolejności dla integracji Intune ewentualnym działała prawidłowo.  Te są domyślnie włączone.
### <a name="step-5-configure-error-report-email-recipient-information"></a>Krok 5. Skonfiguruj informacje o błędzie raport e-mail adresatów
W **zarządzania błąd** , a następnie wprowadź adres e-mail, który powinien zostać wyświetlony raportów o błędach.

![Zrzut ekranu strony zarządzania błędu łącznik usługi Intune](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>Krok 6. Konfigurowanie ustawień rejestracji
W **systemu** modułu na **łączniki** Określ liczbę dni, zanim urządzenie to uznane za jako odłączona.  Odłączone urządzenia są uznawane za niezgodne i będą miały dostęp do aplikacji firmowych na podstawie zasad dostępu warunkowego SCCM. Można określić wartości od 1 do 90 dni.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>Krok 7: Skonfiguruj powiadomienia e-mail
Jeśli chcesz otrzymywać alerty e-mail dotyczące zagrożenia, zaloguj się do [konsoli ewentualnym](https://aad.lookout.com) przy użyciu konta użytkownika, który powinien otrzymywać powiadomienia. Na **preferencje** na karcie **systemu** modułu, wybierz żądaną powiadomień i ustaw je **ON**. Zapisz zmiany.

![Zrzut ekranu strony preferencji przy użyciu konta użytkownika wyświetlane](media/lookout-email-notifications.png) , jeśli nie chcesz już otrzymywać powiadomienia pocztą e-mail, należy ustawić powiadomienia **OFF** i Zapisz zmiany.
### <a name="step-8-configure-threat-classification"></a>Krok 8. Konfigurowanie klasyfikacji zagrożeń
Urządzenie szczególną ochroną klasyfikuje przenośnych zagrożenia różnych typów. [Klasyfikacje zagrożenia ewentualnym](http://personal.support.lookout.com/hc/en-us/articles/114094130693) ma domyślne poziomy ryzyko związane z nimi. Te można zmienić w dowolnym momencie do zestawu z wymaganiami firmy.

![Zrzut ekranu przedstawiający zagrożenia i klasyfikacji strony zasad](media/lookout-threat-classification.png)

>[!IMPORTANT]
> Poziom ryzyka określony tutaj są istotnym elementem urządzenia zagrożenia bezpieczeństwa, ponieważ integracji Intune oblicza zgodności urządzenia zgodnie z tymi poziomami ryzyko w czasie wykonywania. Innymi słowy, administrator usługi Intune Ustawia regułę zasad do identyfikowania urządzenia jako niezgodne, jeśli urządzenie ma aktywne zagrożenia i co najmniej poziom: wysoki, średni lub niski. Zasady klasyfikacji zagrożenie w szczególną ochroną urządzenia bezpośrednio dysków obliczanie zgodności urządzeń w usłudze Intune.

## <a name="watching-enrollment"></a>Obejrzyj rejestracji
Po zakończeniu instalacji urządzenia szczególną ochroną uruchamia sondowanie Azure AD dla urządzeń, które odpowiadają określonej rejestracji grup.  Można znaleźć informacje o urządzeniach zarejestrowanych w module urządzeń.  Początkowy stan urządzenia jest wyświetlany jako oczekujące.  Zmiany stanu urządzenia po zainstalowaniu szukać aplikacji pracy otwarte i aktywacji na urządzeniu.  Szczegółowe informacje dotyczące sposobu uzyskania ewentualnym pracy aplikacji do urządzenia, zobacz [Konfigurowanie i wdrażanie aplikacji pracy ewentualnym](configure-and-deploy-lookout-for-work-apps.md) tematu.
## <a name="next-steps"></a>Następne kroki
[Włącz połączenie MTP ewentualnym Intune](enable-lookout-connection-in-intune.md)

