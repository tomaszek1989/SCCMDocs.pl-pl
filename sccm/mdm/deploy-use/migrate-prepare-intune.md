---
title: "Przygotowanie usługi Intune dla użytkowników"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak przygotować usługę Intune na platformie Azure do migracji użytkownika z hybrydowego zarządzania urządzeniami przenośnymi."
keywords: 
author: dougeby
manager: dougeby
ms.date: 12/05/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: db97ae9e-34f4-4e10-a282-cd211f612bb4
ms.openlocfilehash: 226586f0ee42cdad98b1d74f25421685d85e0dcf
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="prepare-intune-for-user-migration"></a>Przygotowanie usługi Intune dla użytkowników 

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Przed przeprowadzeniem migracji użytkowników z hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager) do autonomicznej usługi Intune, należy wykonać czynności, aby przygotować usługę Intune. Poniższe kroki ułatwiają upewnij się, że zmigrowane użytkowników i ich urządzenia będą nadal zarządzane. Po wykonaniu wskazanych kroków i rozpocząć migrację do usługi Intune, należy go niewidoczny dla użytkowników.  

## <a name="fix-issues-found-during-data-collection-and-import"></a>Rozwiąż problemy znalezione podczas zbierania danych, a następnie zaimportuj
Jeśli poszło procesu [importowania danych programu Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md), narzędzie Intune odbierający dane dostarczone podsumowanie wszystkich obiektów, które nie mógł zaimportować. Niektóre typowe problemy, które prawdopodobnie uruchomiono, a także czynności, które należy wykonać, aby rozwiązać ten problem w usłudze Intune, przedstawiono w poniższej tabeli: 

|Problem  |Poprawka  |
|---------|---------|
|Kolekcje oparte na członkostwo bezpośrednie lub na złożony nie są być migrowane automatycznie.|Należy utworzyć grupy usługi Azure Active Directory (AAD) na platformie Azure, aby zastąpić kolekcji, które nie zostały zaimportowane. Następnie należy przypisać obiekt do grupy.|
|Zasady nie były importowane |Należy ponownie utworzyć zasady w usłudze Intune.|
|Wdrożenie dla obiekt nie został zaimportowany|Należy przypisać obiekt do grupy. Grupa powinna zawierać tej samej użytkownikom kolekcję dla wdrożenia.|

## <a name="create-intune-objects"></a>Tworzenie obiektów usługi Intune 
Jeśli poszło procesu [importowania danych programu Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md) i stały problemy podczas procesu importowania, należy sprawdzić importowanych obiektów są poprawnie skonfigurowane. Ponadto można tworzyć dodatkowe obiekty (zasady, profile, aplikacje itd.) w usłudze Intune, które są potrzebne w Twojej organizacji. 

## <a name="assign-intune-licenses-to-migrated-users"></a>Przypisywanie licencji usługi Intune do migrowanych użytkowników
W programie Configuration Manager w przypadku dodania kolekcji do subskrypcji usługi Intune i elementów członkowskich kolekcji mają możliwość rejestrowania swoich urządzeń. Gdy licencji usługi Intune jest zarezerwowana dla zarejestrowanych urządzeń, licencje nie są specjalnie skojarzone z użytkowników lub urządzeń. Na przykład nie znaleźć licencji usługi Intune w usłudze AAD dla użytkownika, który ma zarejestrowanego urządzenia. Jednak w przypadku autonomicznej usługi Intune należy skonfigurować licencji usługi Intune dla każdego użytkownika. Należy to zrobić przed przeprowadzeniem migracji użytkownik autonomicznej usługi Intune, aby upewnić się, że użytkownik i ich urządzenia są zarządzane przez usługę Intune po zmianie urzędu zarządzania urządzeniami Przenośnymi. Aby uzyskać więcej informacji, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/licenses-assign). 

## <a name="verify-intune-user-groups"></a>Sprawdź grupy użytkowników usługi Intune
Użytkownikami i grupami są prawdopodobnie już w usłudze AAD, ponieważ ma skonfigurowany synchronizacji katalogów. Aby upewnić się, że użytkownicy są częścią grupy użytkownika, firma Microsoft zaleca przejrzenie grupy użytkowników usługi Intune. Zasady, profile, aplikacje itd. do tych grup są przeznaczone. Upewnij się, że użytkowników, których można dokonać migracji do autonomicznej usługi Intune są częścią grupy poprawne. 

## <a name="configure-role-based-administration-control-rbac"></a>Skonfiguruj kontrolę administracji opartej na rolach (RBAC)
W ramach migracji skonfiguruj wszystkie wymagane role RBAC w usłudze Intune i przypisać użytkowników do tych ról. Należy pamiętać, że istnieją różnice między RBAC w programie Configuration Manager i usługi Intune, takie jak zakres zasobów. Aby uzyskać więcej informacji, zobacz [kontroli administracji opartej na rolach (RBAC) przy użyciu usługi Intune](https://docs.microsoft.com/en-us/intune/role-based-access-control).

## <a name="assign-apps-and-policies-to-aad-groups"></a>Przypisywanie aplikacji i zasad do grup usługi AAD
Jeśli poszło za pośrednictwem [danych Import Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md) fazy procesu migracji przeprowadzić migrację innego programu Configuration Manager obiekty do usługi Intune, wiele obiektów mogą być już przypisane do grup usługi AAD. Jednak należy sprawdzić, czy wszystkie obiekty (aplikacje, zasady, profile, itp.) są przypisane do poprawne grup usługi AAD. Jeśli poprawnie przypisanie obiektów urządzeń użytkownika są konfigurowane automatycznie po migracji należy niewidoczny dla użytkowników i migracji użytkownika. Aby uzyskać więcej informacji o przypisywaniu obiekty do grupy usługi AAD, zobacz następujące tematy: 
- [Przypisać zasady](https://docs.microsoft.com/intune/get-started-policies) 
- [Przypisz profile](https://docs.microsoft.com/intune/device-profile-assign) 
- [Przypisywanie aplikacji](https://docs.microsoft.com/intune/get-started-apps) 

## <a name="terms-and-conditions-policy"></a>Zasady dotyczące warunków i postanowień
Podobnie jak inne zasady na poziomie dzierżawy zasady warunków i postanowień są automatycznie migrowane do usługi Intune po urzędu mieszany jest włączona dla Twojej dzierżawy.  Jednak należy przypisać warunki i postanowienia do grupy, która zawiera migrowane użytkownikom dokładnie raport dotyczący akceptacji dla migrowanych użytkowników i upewnij się, że warunki i postanowienia prawidłowo są przeznaczone dla przyszłych warunków i postanowień aktualizacji lub urządzenia rejestracji. Nie masz użytkownicy mają ponownie akceptować warunków i postanowień, chyba że zmiany zasad w konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [przypisać warunków i postanowień](https://docs.microsoft.com/intune/terms-and-conditions-create#assign-terms-and-conditions).

## <a name="configure-the-exchange-connector"></a>Konfigurowanie programu Exchange Connector
Jeśli korzystasz z programu Exchange i mieć łącznik lokalnego programu Exchange w programie Configuration Manager, musisz [skonfigurować łącznik lokalnego programu Exchange w usłudze Intune](https://docs.microsoft.com/intune/exchange-connector-install). Należy również rozważyć informacje w poniższych sekcjach ułatwiają migrację do programu Intune Exchange Connector i zapewnienie dostępu warunkowego pracy prawidłowo po migracji.

### <a name="powershell-scripts-to-help-you-migrate-to-the-intune-exchange-connector"></a>Skrypty programu PowerShell, aby przeprowadzić migrację do programu Intune Exchange Connector 
Skrypty programu PowerShell dostępnych może ułatwić przygotowania do przejścia urządzenia programu Exchange z programu Configuration Manager Exchange Connector do programu Intune Exchange Connector. Podczas pracy te skrypty są opcjonalne, zaleca się uruchomić je, aby usunąć nieaktywne urządzenia z programu Exchange, co zapobiega odnajdywania niepotrzebnych urządzeń usługi Intune. Uruchamianie skryptów upewnij się, że urządzenia odnalezione za pomocą programu Exchange mogą łączyć się z urządzeniami zarejestrowanymi w usłudze Intune możliwie bez zakłóceń. Uruchom te skrypty przed skonfigurowaniem programu Intune Exchange Connector. Skrypty programu PowerShell są część instalacji odbierający dane usługi Intune, który umożliwia [importowania danych programu Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md) w artykule. Aby uzyskać szczegółowe informacje i Pobierz skrypty, przejdź do [odbierający dane usługi Microsoft Intune](https://github.com/ConfigMgrTools/Intune-Data-Importer) stronie GitHub.

### <a name="steps-to-ensure-conditional-access-works-properly-after-user-migration"></a>Kroki w celu zapewnienia działania dostępu warunkowego prawidłowo po migracji użytkowników
Dla dostępu warunkowego do poprawnego działania po przeprowadzeniu migracji użytkowników i upewnij się, że użytkownicy nadal mają dostęp do swojego serwera poczty e-mail upewnij się, że są spełnione następujące warunki:
- Jeśli programu Exchange ActiveSync dostępu poziomu ustawieniem domyślnym (DefaultAccessLevel) jest ustawiona na blokowanie lub kwarantannę, urządzenia mogą utracić dostęp do poczty e-mail. 
- Jeśli łącznik programu Exchange jest zainstalowany w programie Configuration Manager i **poziom dostępu, gdy urządzenie przenośne nie jest zarządzane przez regułę** ustawienie ma wartość **zezwolić na dostęp**, musisz zainstalować [ Łącznik programu Exchange lokalnego](https://docs.microsoft.com/en-us/intune/conditional-access-exchange-create#configure-exchange-on-premises-access) w usłudze Intune, przed przeprowadzeniem migracji użytkowników. Skonfiguruj domyślne ustawienia poziomu dostępu w usłudze Intune na **do lokalnego programu Exchange** bloku w **ustawień dostępu do programu Exchange ActiveSync zaawansowane**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie lokalnego programu Exchange dostępu](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access).
- Użyj tej samej konfiguracji dla łączników. Ostatni łącznik, który należy skonfigurować zastępuje ustawienia organizacji ActiveSync wcześniej zapisane przez łącznik programu. Jeśli konfigurujesz łączniki inaczej, może to spowodować zmiany nieoczekiwany dostępu warunkowego.
- Usunąć użytkowników z dostępu warunkowego obiektów docelowych w programie Configuration Manager po ich zmigrowaniu do autonomicznej usługi Intune.

## <a name="configure-the-microsoft-intune-certificate-connector"></a>Konfigurowanie łącznika certyfikatów usługi Microsoft Intune
Jeśli używasz usługi NDES do wystawiania certyfikatów przy użyciu protokołu SCEP, należy skonfigurować łącznik certyfikatów usługi Microsoft Intune. Komputer, który będzie hostem łącznika usługi NDES w usłudze Intune nie może być tym samym komputerze, który będzie hostem łącznika usługi NDES w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [Konfigurowanie certyfikatów SCEP z usługą Intune i zarządzania nimi](https://docs.microsoft.com/en-us/intune/certificates-scep-configure). 

> [!Important]    
> Po skonfigurowaniu łącznika, należy zmodyfikować importowanych profilów protokołu SCEP, aby odwołać nowy adres URL serwera.

## <a name="next-step"></a>Następny krok
Po Intune przygotowania do migracji, można przystąpić do migracji zbiór użytkowników testowych do autonomicznej usługi Intune. Aby uzyskać więcej informacji, zobacz [zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu)](migrate-mixed-authority.md).


