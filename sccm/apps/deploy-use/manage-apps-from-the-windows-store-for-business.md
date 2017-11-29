---
title: "Zarządzanie aplikacjami ze sklepu firmy Microsoft dla firm"
titleSuffix: Configuration Manager
description: "Zarządzanie i wdrażanie aplikacji Microsoft Store dla firm za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: "11"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 0400262c6d00a83a3da10cb0a60072552dd14360
ms.sourcegitcommit: 1dd051d8548a19b724bb8f9e6a2278a4901ed916
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="manage-apps-from-the-microsoft-store-for-business-with-system-center-configuration-manager"></a>Zarządzanie aplikacjami ze sklepu firmy Microsoft dla firm z programu System Center Configuration Manager
[Microsoft Store dla firm](https://www.microsoft.com/business-store) jest, gdzie można znaleźć i zakupić aplikacje systemu Windows w Twojej organizacji, pojedynczo lub zbiorczo. Łącząc Sklep do programu Configuration Manager, można zsynchronizować listę aplikacji, które zostały zakupione w programie Configuration Manager. Następnie można wyświetlić tych aplikacji w konsoli programu Configuration Manager i wdrażać je tak, jaki wdraża się innych aplikacji.


## <a name="online-and-offline-apps"></a>Aplikacje online i offline

Microsoft Store dla firm obsługuje dwa typy aplikacji:

- **Online** — ten typ licencji wymaga użytkowników i urządzeń, aby połączyć się z magazynem można pobrać aplikacji i jej licencji. Urządzenia Windows 10 muszą być przyłączone do domeny usługi Azure Active Directory.
- **W trybie offline** — umożliwia aplikacji w pamięci podręcznej i licencji na wdrożenie bezpośrednio w sieci lokalnej, bez konieczności nawiązywania połączenia z magazynem, lub mając połączenie z Internetem.

[Dowiedz się więcej](https://docs.microsoft.com/microsoft-store/microsoft-store-for-business-overview) o Microsoft Store dla firm.

Program Configuration Manager obsługuje zarządzanie Microsoft Store dla aplikacji biznesowych na zarówno urządzeń z systemem Windows 10 uruchomiony klient programu Configuration Manager, a także urządzeń z systemem Windows 10, które są zarejestrowane w usłudze Microsoft Intune (nazywane Konfiguracja hybrydowa). Configuration Manager oferuje następujące funkcje dla aplikacji online i offline.

> [!IMPORTANT]
> Aby użyć tej funkcji, urządzeń z systemem Windows 10 musi działać wersja listopada 2015 (1511) lub nowszym.


|Możliwość|Aplikacje w trybie offline|Aplikacje online|
|------------|------------|------------|
|Synchronizowanie danych aplikacji w programie Configuration Manager<br>(synchronizacja jest przeprowadzana co 24 godziny)|Tak|Tak|
|Tworzenie aplikacji programu Configuration Manager z aplikacji do sklepu|Tak|Tak|
|Obsługuje bezpłatne aplikacje ze sklepu|Tak|Tak|
|Obsługa płatnych aplikacji ze sklepu|Nie|Tak|
|Obsługuje wymaganych wdrożeń do kolekcji użytkowników lub urządzeń|Tak|Tak|
|Obsługa wdrożeń dostępnych do kolekcji użytkowników lub urządzeń|Tak|Tak|
|Obsługa aplikacji biznesowych — w sklepie|Tak|Tak|

Aby wdrożyć licencjonowane aplikacje komputerów z systemem Windows 10 przy użyciu klienta programu Configuration Manager, musi być uruchomiona usługa Windows Update twórców do 10 lub nowszego.

## <a name="deploying-online-apps-using-the-microsoft-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Wdrażanie aplikacji online przy użyciu Microsoft Store dla firm z komputerami z klientem programu Configuration Manager
Przed wdrożeniem Microsoft Store dla aplikacji biznesowych na komputerach z systemem pełnego klienta programu Configuration Manager, należy wziąć pod uwagę następujące kwestie:

- Zapewnienia pełnej funkcjonalności komputerów musi być uruchomiona aktualizacji twórców systemu Windows 10 lub nowszego.
- Komputery musi być Azure Active Directory w miejscu pracy przyłączone i należeć do tej samej dzierżawie usługi AAD rejestracji Microsoft Store dla firm jako narzędzia do zarządzania.
- Gdy komputery są rejestrowane przy użyciu wbudowanego konta administratora, nie można ich dostęp do Microsoft Store dla aplikacji biznesowych.
- Komputery muszą mieć aktywne połączenie internetowe do Microsoft Store dla firm.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Informacje o komputerach z wcześniejszymi wersjami systemu Windows 10
Na komputerach z systemem Windows 10 w wersji starszej niż aktualizacji twórców (za pomocą klienta programu Configuration Manager) stosowane są następujące funkcje:


- Podczas instalacji jest wymuszana przez użytkownika instalacji aplikacji, przez aplikację osiągnięcia termin instalacji albo przez post instalacji ponowną ocenę dla wdrożeń wymagane:
    - Aplikacja jest "wymuszone" uruchamiając Microsoft Store dla aplikacji biznesowych. 
    - Użytkownik końcowy musi następnie ukończyć instalację w sklepie, przed zainstalowaniem aplikacji
    - Stan aplikacji w raportach konsoli programu Configuration Manager nie powiodło się z powodu błędu "aplikacji Microsoft Store został otwarty na komputerze klienckim i oczekuje na użytkownika, aby zakończyć instalację."
- W następnym cyklu oceny aplikacji:
    - Jeśli aplikacja została zainstalowana przez użytkownika końcowego w sklepie, aplikacja zgłasza stan **Powodzenie**. 
    - Jeśli użytkownik końcowy nie próbował zainstalować aplikację ze Sklepu:
        - Wymagane wdrożenia próba uruchomienia sklepu i wymuszać ponownie instalację aplikacji.
        - Dostępne wdrożenia nie są wymuszane ponownie.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Dodatkowe uwagi dla komputerów z wcześniejszymi wersjami systemu Windows 10:

- Nie można wdrożyć aplikacji biznesowych z Microsoft Store dla firm
- Podczas wdrażania płatnych aplikacji ze sklepu, użytkownicy końcowi musi zalogować się w magazynie i się zakupu aplikacji.
- Jeśli wdrożono dostępu wyłączanie zasad grupy do wersji klienta programu Microsoft Store, wdrożeń z Microsoft Store dla firm nie działają, nawet jeśli włączono Microsoft Store dla firm.


## <a name="set-up-microsoft-store-for-business-synchronization"></a>Konfigurowanie Microsoft Store dla firm synchronizacji

### <a name="for-configuration-manager-versions-prior-to-1706"></a>Wersje programu Configuration Manager przed 1706

**W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web". Ta akcja umożliwia Identyfikatora klienta, które są potrzebne później.**
1. W węźle usługi Active Directory [https://manage.windowsazure.com](https://manage.windowsazure.com), wybierz w usłudze Azure Active Directory, a następnie kliknij przycisk **aplikacji** > **Dodaj**.
2.  Kliknij przycisk **Dodaj aplikację moją organizację**.
3.  Wprowadź nazwę aplikacji, wybierz pozycję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij przycisk **dalej** strzałki.
4.  Wprowadź ten sam adres URL dla obu **adres URL logowania** i **identyfikator URI aplikacji**. Adres URL może być dowolny i nie musi prowadzić do faktycznego adresu. Na przykład można wprowadzić *https://yourdomain/sccm*.
5.  Ukończ pracę kreatora.

**W usłudze Azure Active Directory Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania**
1.  Wyróżnij utworzoną aplikację i kliknij przycisk **Konfiguruj**.
2.  W obszarze **klucze**, wybierz czas trwania z listy, a następnie kliknij przycisk **zapisać**. Ta akcja powoduje utworzenie nowego klucza klienta. Nie opuścić tę stronę, dopóki nie został załadowany Microsoft Store dla firm do programu Configuration Manager.

**W Store firmy Microsoft dla firm Konfigurowanie programu Configuration Manager jako narzędzie do zarządzania magazynami**
1.  Otwórz [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) i zaloguj się w przypadku wyświetlenia monitu.
2.  Zaakceptuj warunki użytkowania, jeśli jest to wymagane.
3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzie do zarządzania**.
4.  W **Wyszukaj narzędzie według nazwy**, wpisz nazwę aplikacji wcześniej utworzony w usłudze AAD, a następnie kliknij przycisk **Dodaj**.
5.  Kliknij przycisk **Aktywuj** obok aplikacji zaimportowana.
6.  W **Zarządzaj > informacje o koncie** wybierz pozycję **Pokaż aplikacje** Jeśli chcesz zezwolić aplikacji licencjonowanych w trybie offline do zakupu.

**Dodawanie konta magazynu do programu Configuration Manager**

1. Upewnij się, że zakupiono co najmniej jedną aplikację z Microsoft Store dla firm. W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, następnie kliknij przycisk **Microsoft Store dla firm**.
2.  Na **Home** karcie **Microsoft Store dla firm** kliknij przycisk **dodać magazyn Microsoft dla firm**. 
3.  Dodaj identyfikator dzierżawy, identyfikator klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.
4. Gdy wszystko będzie gotowe, zobaczysz skonfigurowane konto **Microsoft Store dla firm** listy w konsoli programu Configuration Manager.

### <a name="for-configuration-manager-version-1706-and-later"></a>Dla 1706 wersji programu Configuration Manager i nowszych

1. W konsoli przejdź do **administracji** > **omówienie** > **zarządzania usługami w chmurze** > **Azure** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure** uruchomić **Kreator usług Azure**.
2. Na **usług Azure** wybierz usługi, które chcesz skonfigurować, a następnie kliknij przycisk **dalej**.
3. Na **ogólne** Podaj przyjazną nazwę dla nazwy usługi Azure i opcjonalny opis, a następnie kliknij pozycję **dalej**.
4. Na **aplikacji** , określ środowisku platformy Azure, a następnie kliknij przycisk **Przeglądaj** otworzyć **aplikacji Server** okna.
5. W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**. Aplikacje serwera są aplikacjami sieci web platformy Azure, które zawierają konfiguracje dla konta platformy Azure, w tym Identyfikatora dzierżawy, identyfikator klienta i klucz tajny dla klientów. Jeśli nie ma dostępnego serwera aplikacji, użyj jednej z następujących czynności:
    - **Utwórz:** Aby utworzyć nową aplikację serwera, kliknij przycisk **Utwórz**. Podaj przyjazną nazwę dla aplikacji i dzierżawcy. Następnie po możesz zalogować się do platformy Azure, programu Configuration Manager utworzy aplikacji sieci web na platformie Azure, w tym identyfikator klienta i klucz tajny do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.
    - **Import:** Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po **Sprawdź** informacji, kliknij przycisk **OK** aby kontynuować. 
6. Przegląd **informacji** strony i wykonać wszelkie dodatkowe kroki i konfiguracje, zgodnie z instrukcją. Te konfiguracje są niezbędne do korzystania z usługi z programem Configuration Manager. Na przykład, aby skonfigurować Microsoft Store dla firm:
    - Na platformie Azure musisz zarejestrować programu Configuration Manager jako interfejs API sieci Web lub aplikacji sieci web i zarejestrować identyfikator klienta. Możesz również określić klucz klienta do użycia przez narzędzie do zarządzania (czyli programu Configuration Manager).
    - Microsoft Store dla firm konsoli musi skonfigurować programu Configuration Manager jako narzędzie do zarządzania magazynami, umożliwia obsługę aplikacji licencjonowanych w trybie offline i następnie zakupu co najmniej jedną aplikację. 
7. Kliknij przycisk **dalej** po osiągnięciu gotowości kontynuować.
8. Na **konfiguracji aplikacji** ukończenia konfiguracji katalogu i język aplikacji dla tej usługi, a następnie kliknij przycisk **dalej**.
9. Po zakończeniu działania kreatora, konsoli programu Configuration Manager pokazuje, że skonfigurowano **Microsoft Store dla firm** jako **typu usługi w chmurze**.




## <a name="create-and-deploy-a-configuration-manager-application-from-a-microsoft-store-for-business-app"></a>Tworzenie i wdrażanie aplikacji programu Configuration Manager z Microsoft Store dla aplikacji biznesowych.
1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Zarządzanie aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji ze sklepu**.
2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie na **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji**.
Tworzenia aplikacji programu Configuration Manager zawierający Microsoft Store dla aplikacji biznesowych. Można następnie wdrożyć i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.

> [!IMPORTANT]
> W przypadku urządzeń zarejestrowanych w usłudze Intune wdrożone aplikacje są dostępne tylko dla użytkownika, który pierwotnie zarejestrował urządzenie. Inni użytkownicy nie mogą uzyskać dostępu do aplikacji.

## <a name="next-steps"></a>Następne kroki

W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji ze sklepu**.

Dla każdego zarządzanych aplikacji ze sklepu, można wyświetlić informacje o aplikacji, w tym jego nazwa, platformy, a następnie liczbą licencji dla aplikacji, którego jesteś właścicielem oraz liczbę licencji od posiadanego.

Po wdrożeniu aplikacji online, należy pamiętać, że wszelkie aktualizacje, aplikacja będzie pochodzić bezpośrednio z Microsoft Store.

W przypadku wdrażania aplikacji w trybie offline na urządzeniach z systemem Windows 10 przy użyciu klienta programu Configuration Manager (szczególnie w środowiskach wielu użytkowników, takich jak klasy), wyłącz Microsoft Store i/lub aktualizacji aplikacji za pomocą Microsoft Store (na przykład za pomocą [zasady grupy](https://docs.microsoft.com/en-us/windows/configuration/stop-employees-from-using-microsoft-store#a-href-idblock-store-group-policyablock-microsoft-store-using-group-policy)) tak, aby użytkownicy nie można zaktualizować aplikacji zewnętrznych do wdrożenia programu Configuration Manager. Ponadto po zakupi Microsoft Store dla administratora biznesowych aplikacji (w związku z tym udostępnieniem jej w stan offline w celu synchronizacji z programem Configuration Manager) nie publikowanie aplikacji dla użytkowników tak, aby ich instalacji lub aktualizacji w trybie online. Daje to pewność, że wszyscy użytkownicy uzyskują tylko aktualizacji aplikacji za pomocą programu Configuration Manager. 
