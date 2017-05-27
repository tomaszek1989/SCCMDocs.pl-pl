---
title: "Zarządzanie aplikacjami ze Sklepu Windows dla firm | Dokumentacja firmy Microsoft"
description: "Zarządzanie i wdrażanie aplikacji ze Sklepu Windows w przedsiębiorstwie za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 3/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: f2d9da1c584f78e27e84b7f55e7ffe4dd052a27c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-apps-from-the-windows-store-for-business-with-system-center-configuration-manager"></a>Zarządzanie aplikacjami zakupionymi w Sklepie Windows dla firm przy użyciu programu System Center Configuration Manager
[Sklepu Windows dla firm](https://www.microsoft.com/business-store) pozwala znaleźć i zakupić aplikacji systemu Windows dla danej organizacji, pojedynczo lub w woluminie. Łącząc sklepu do programu Configuration Manager, możesz zsynchronizować listę aplikacji zakupiony z programu Configuration Manager, wyświetlać je w konsoli programu Configuration Manager i wdrażać je, jak w przypadku innych aplikacji.


## <a name="online-and-offline-apps"></a>Aplikacje online i offline

Sklep Windows dla firm obsługuje dwa typy aplikacji:

- **Online** -wymaga tego typu licencji użytkowników i urządzeń, aby połączyć się ze sklepem pobrać aplikację i jego licencją. Windows 10 urządzenia muszą być przyłączone do domeny usługi Azure Active Directory.
- **W trybie offline** — organizacje Buforowanie aplikacji i licencje, aby wdrożyć bezpośrednio w lokalnej sieci bez łączenia się z magazynem lub konieczność połączenia z Internetem.

[Dowiedz się więcej](https://technet.microsoft.com/itpro/windows/whats-new/windows-store-for-business-overview?f=255&MSPPError=-2147217396) o Sklepu Windows dla firm.

Program Configuration Manager obsługuje zarządzanie Sklepu Windows dla aplikacji biznesowych na zarówno urządzeń systemu Windows 10 uruchomiony klient programu Configuration Manager, a także urządzeń systemu Windows 10, które zostały zarejestrowane w usłudze Microsoft Intune (nazywanych konfiguracji hybrydowe). Program Configuration Manager oferuje następujące funkcje dla aplikacji w trybie online i offline.

> [!IMPORTANT]
> Aby użyć tej funkcji, urządzeń z systemem Windows 10 musi działać w wersji 2015 listopada (1511) lub nowszy.


|Możliwość|Aplikacje offline|Aplikacje online|
|------------|------------|------------|
|Synchronizowanie danych aplikacji do programu Configuration Manager<br>(synchronizację co 24 godziny)|Tak|Tak|
|Tworzenie aplikacji programu Configuration Manager z aplikacji do sklepu|Tak|Tak|
|Bezpłatnie obsługuje aplikacje ze sklepu|Tak|Tak|
|Obsługa płatną aplikacji w sklepie|Nie|Tak|
|Obsługuje wdrożenia wymagane do kolekcji użytkowników lub urządzeń|Tak|Tak|
|Obsługa wdrożeń dostępnych do kolekcji użytkowników lub urządzeń|Tak|Tak|
|Obsługa aplikacji biznesowych — w sklepie|Tak|Tak|

Aby wdrożyć online licencjonowane aplikacje na komputery z systemem Windows 10 za pomocą klienta programu Configuration Manager, musi być uruchomiona usługa Windows Update twórcy do 10 lub nowszego.

## <a name="deploying-online-apps-using-the-windows-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Wdrażanie aplikacji online przy użyciu Sklepu Windows dla firm z komputerami z systemem klienta programu Configuration Manager
Przed wdrożeniem Sklepu Windows dla aplikacji biznesowych do komputerów z systemem pełnego klienta programu Configuration Manager, należy rozważyć następujące kwestie:

- Do zapewnienia pełnej funkcjonalności, komputerami musi być uruchomiony Windows Update twórcy do 10 lub nowszego.
- Komputery muszą zostać Azure Active Directory w miejscu pracy przyłączone i znajdować się w tej samej dzierżawy AAD gdzie Sklepu Windows dla firm jest zarejestrowany jako narzędzia do zarządzania.
- Gdy komputery są rejestrowane za pomocą wbudowanego konta administratora, nie uzyskują dostęp do Sklepu Windows dla aplikacji biznesowych.
- Komputery musi mieć aktywne połączenie internetowe do Sklepu Windows dla firm.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Uwagi dla komputerów z wcześniejszymi wersjami systemu Windows 10
W przypadku komputerów z systemem Windows 10 w wersji starszej niż aktualizacji twórcy (przy użyciu klienta programu Configuration Manager) mają zastosowanie następujące funkcje:


- Podczas instalacji jest wymuszana przez użytkownika instalacji aplikacji lub aplikacji osiągnięcia jej ostateczny termin instalacji albo po instalacji ponowną ocenę dla wdrożeń wymagane:
    - Aplikacja zostanie "wymuszone" poprzez uruchomienie Sklepu Windows dla aplikacji biznesowych. 
    - Użytkownik końcowy musi następnie ukończenie instalacji z magazynu jest w rzeczywistości instalowane
    - Stan aplikacji w konsoli programu Configuration Manager będą raportowane jako zakończone niepowodzeniem z powodu błędu "aplikacji do Sklepu Windows został otwarty na komputerze klienta i oczekuje na użytkownika zakończyć instalację."
- W następnym cyklu oceny aplikacji:
    - Jeśli aplikacja została zainstalowana przez użytkownika końcowego w sklepie, aplikacja będzie zgłosić stan **Powodzenie**. 
    - Jeśli użytkownik końcowy nie próbować zainstalować aplikację ze Sklepu:
        - Wdrożenia wymagane będzie podejmować próby uruchomienia sklepu i wymusić ponownie instalację aplikacji.
        - Nie będzie ponownie wymuszone dostępne wdrożenia.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Dodatkowe uwagi dla komputerów z wcześniejszymi wersjami systemu Windows 10:

- Nie można wdrożyć aplikacje biznesowe w Sklepie Windows dla firm
- Podczas wdrażania płatne aplikacje ze sklepu, użytkownicy końcowi będzie wymagane do logowania do magazynu i samych zakupu aplikacji.
- Jeśli wdrożono wyłączenie dostępu do zasad grupy do wersji klienta Sklepu Windows, wdrożeń w Sklepie Windows dla firm nie będzie działać, nawet jeśli jest włączone Sklepu Windows dla firm.


## <a name="set-up-windows-store-for-business-synchronization"></a>Konfigurowanie magazynu systemu Windows dla synchronizacji biznesowe

**W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web". Zapewni to identyfikator klienta, który trzeba będzie później.**
1. W węźle usługi Active Directory [https://manage.windowsazure.com](https://manage.windowsazure.com), wybierz Azure Active Directory, a następnie kliknij przycisk **aplikacje** > **Dodaj**.
2.  Kliknij przycisk **Dodawanie mojej organizacji jest opracowywanie aplikacji**.
3.  Wprowadź nazwę aplikacji, wybierz opcję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij przycisk **dalej** strzałki.
4.  Wprowadź ten sam adres URL dla obu **adres URL logowania jednokrotnego** i **URI Identyfikatora aplikacji**. Adres URL może być dowolny i nie musi rozpoznać adres rzeczywisty. Na przykład, można wprowadzić *https://yourdomain/sccm*.
5.  Ukończ pracę kreatora.

**W usłudze Azure Active Directory Utwórz klucz klienta dla narzędzia do zarządzania zarejestrowanych**
1.  Wyróżnij aplikacji został utworzony, a następnie kliknij przycisk **Konfiguruj**.
2.  W obszarze **klucze**, wybierz czas trwania na liście, a następnie kliknij przycisk **zapisać**. Spowoduje to utworzenie nowego klucza klienta. Nie opuścić tę stronę, aż do uzyskania pomyślnie dołączono maszynę wirtualną w Sklepie Windows biznesowych programu Configuration Manager.

**W Sklepie Windows dla firm Konfigurowanie programu Configuration Manager jako narzędzie do zarządzania magazynami**
1.  Otwórz [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) i zaloguj się po wyświetleniu monitu.
2.  Zaakceptuj warunki użytkowania na żądanie.
3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzia do zarządzania**.
4.  W **Wyszukaj według nazwy narzędzie**, wpisz nazwę aplikacji utworzonych w AAD wcześniej, a następnie kliknij przycisk **Dodaj**.
5.  Kliknij przycisk **uaktywnienia** obok aplikacji zostały zaimportowane.
6.  W **Zarządzaj > informacje o koncie** wybierz opcję **Show Offline-Licensed aplikacje** Jeśli chcesz zezwolić offline licencjonowane aplikacje do zakupu.

**Dodaj konto magazynu do programu Configuration Manager**

1. Upewnij się, że użytkownik zakupił co najmniej jednej aplikacji ze Sklepu Windows dla firm. W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usług w chmurze**, następnie kliknij przycisk **Sklepu Windows dla firm**.
2.  Na **Home** w karcie **Sklepu Windows dla firm** , kliknij przycisk **Dodaj Sklep Windows dla konta firmowego**. 
3.  Dodaj identyfikator dzierżawcy, identyfikatora klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.
4. Gdy wszystko będzie gotowe, zobaczysz konta skonfigurowanego w **Sklepu Windows dla firm** listy w konsoli programu Configuration Manager.


## <a name="create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-app"></a>Tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla aplikacji biznesowych.
1.  W **Biblioteka oprogramowania** rozwiń obszar roboczy w konsoli programu Configuration Manager **zarządzania aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji do sklepu**.
2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie w **Home** w karcie **Utwórz** , kliknij przycisk **tworzenie aplikacji**.
Tworzenia aplikacji programu Configuration Manager zawierający Sklepu Windows dla aplikacji biznesowych. Można następnie wdrażać i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.
> [!IMPORTANT]
> W przypadku urządzeń zarejestrowanych w usłudze Intune wdrożonych aplikacji są dostępne tylko dla użytkownika, który pierwotnie zarejestrowane urządzenia. Użytkownicy nie mogą uzyskać dostępu do aplikacji.

## <a name="monitor-windows-store-for-business-apps"></a>Monitor Sklep Windows dla aplikacji biznesowych

W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **zarządzania aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji do sklepu**.

Dla każdej aplikacji magazynu można zarządzać, można wyświetlić informacje o aplikacji, w tym jej nazwę, platformy, a następnie liczbę licencji własnej aplikacji oraz liczbę licencji masz dostępne.

