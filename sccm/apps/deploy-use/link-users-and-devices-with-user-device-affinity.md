---
title: Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika
titleSuffix: Configuration Manager
description: Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika i automatycznie wdrażać aplikacje na wszystkich urządzeniach powiązanych z użytkownikiem.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 5b30b0d5-722d-4d4b-9ed7-5a43de315461
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 40bab1725b074bc549eeb9e9764ab8a1dd8b83e7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="link-users-and-devices-with-user-device-affinity-in-system-center-configuration-manager"></a>Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Koligację urządzenia użytkownika w programie System Center Configuration Manager (program Configuration Manager) umożliwia skojarzenie użytkownika z jednego lub większej liczby urządzeń. Ten sposób można wyeliminować konieczność znajomości nazw urządzeń użytkownika do wdrożenia aplikacji dla użytkownika. Zamiast wdrażać aplikację na każdym z urządzeń użytkownika, wystarczy ją wdrożyć dla użytkownika. Następnie koligacja urządzenia użytkownika zapewni zainstalowanie aplikacji na wszystkich urządzeniach powiązanych z użytkownikiem.  

 Można zdefiniować urządzenia podstawowe, które zwykle są urządzeń używanych codziennie przez użytkowników do wykonywania ich pracy. Tworząc koligację między użytkownikiem i urządzeniem, możesz zyskać dodatkowe opcje wdrażania aplikacji. Na przykład jeśli użytkownik wymaga programu Microsoft Visio, można zainstalować go na urządzeniu podstawowym użytkownika przy użyciu wdrożenia Instalatora Windows. Jednak na urządzeniu niebędącym urządzeniem podstawowym, można wdrożyć program Visio jako aplikację wirtualną. Możesz również użyć koligacji urządzenia użytkownika do wstępnego wdrażania oprogramowania na urządzeniu użytkownika, gdy użytkownik nie jest zalogowany, tak aby po zalogowaniu się użytkownika aplikacja jest już zainstalowany i gotowy do uruchomienia.  

 Zarządzanie informacjami o koligacji urządzeń użytkowników dla komputerów jest wymagane. Menedżer konfiguracji automatycznie zarządza koligacji urządzeń użytkownika dla urządzeń przenośnych, które rejestruje.  

## <a name="manually-set-up-user-device-affinity"></a>Ręczne konfigurowanie koligacji urządzenia użytkownika  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń**.  

3.  Na liście Wybierz urządzenia. Następnie na **Home** karcie **urządzenia** grupy, wybierz **Edytuj użytkowników podstawowych**.  

4.  W **Edytuj użytkowników podstawowych** okno dialogowe, wyszukaj i wybierz użytkowników, aby dodać jako użytkowników podstawowych dla wybranego urządzenia. Wybierz **dodać**.  

    > [!NOTE]  
    > **Użytkowników podstawowych** listy wyświetlani użytkownicy, którzy już są użytkownikami podstawowymi danego urządzenia, a metoda, przez które każdy użytkownik urządzenie relacja została przypisana.  

## <a name="set-up-primary-devices-for-a-user"></a>Konfigurowanie urządzenia podstawowe dla użytkownika  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **użytkowników**.  

3.  Na liście Wybierz użytkownika. Następnie na **urządzenia** , wybierz pozycję **Edytuj urządzenia podstawowe**.  

4.  W **Edytuj urządzenia podstawowe** okno dialogowe, wyszukaj i wybierz urządzenia, które chcesz dodać jako urządzenia podstawowe dla wybranego użytkownika. Wybierz **dodać**.  

    > [!NOTE]  
    > **Urządzenia podstawowe** listy wyświetlane urządzenia, które są już ustawione jako urządzenia podstawowe dla tego użytkownika, a metoda, przez które każdy użytkownik urządzenie relacja została przypisana.  

## <a name="automatically-create-user-device-affinities-windows-pcs-only"></a>Automatyczne tworzenie koligacji urządzenia użytkownika (tylko komputery z systemem Windows)  
 Menedżer konfiguracji odczytuje dane dotyczące logowania użytkowników z dziennika zdarzeń systemu Windows. Automatyczne tworzenie koligacji urządzenia użytkownika, należy włączyć te dwie opcje w lokalnych zasadach zabezpieczeń na komputerach klienckich do zapisywania zdarzeń logowania w dzienniku zdarzeń systemu Windows:  

-   **Przeprowadź inspekcję zdarzeń logowania na kontach**  
-   **Przeprowadź inspekcję zdarzeń logowania**  

 Aby skonfigurować te ustawienia, należy użyć zasad grupy systemu Windows.  

> [!IMPORTANT]  
> Jeśli błąd powoduje, że dziennik zdarzeń systemu Windows wygenerować dużą liczbę wpisów, może utworzyć nowego dziennika zdarzeń. W takim przypadku istniejące zdarzenia logowania mogą nie być już dostępne w programie Configuration Manager.  
>   
> Należy zachować ostrożność podczas włączania **Przeprowadź inspekcję zdarzeń logowania na koncie** i **Przeprowadź inspekcję zdarzeń logowania** ustawienia w systemie Windows XP. Domyślnie w zasadach przechowywania wynosi 7 dni i jest bardzo prawdopodobne, że te zdarzenia zapełnienie dziennika zdarzeń zabezpieczeń. Użytkownicy standardowi nie można się zalogować, jeśli dziennik zdarzeń jest pełny. Aby temu zapobiec, w dzienniku zdarzeń zabezpieczeń, należy ustawić zasady **metoda przechowywania** do wartości **Zastąp zdarzenia w razie potrzeby**. Wystarczających danych dla koligacji urządzenia użytkownika należy również ustawić rozmiar dziennika zdarzeń zabezpieczeń maksymalną zasad rozsądną wartość, na przykład 5-20 MB.  

### <a name="set-up-the-site-to-automatically-create-user-device-affinities"></a>Konfigurowanie lokacji w celu automatycznego utworzenia koligacji urządzeń użytkowników  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta**.  

2.  Aby zmodyfikować domyślne ustawienia klienta, wybierz opcję **domyślnych ustawień klienta**, a następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**. Aby utworzyć ustawienia niestandardowe klienta agenta, wybierz **ustawień klienta** węzła, a następnie na **Home** karcie **Utwórz** grupy, wybierz **Tworzenie niestandardowych ustawień urządzenia klienckiego**.  

    > [!NOTE]  
    > Po zmodyfikowaniu domyślnych ustawień klienta zostaną one wdrożone na wszystkich komputerach w hierarchii. Aby uzyskać więcej informacji o konfigurowaniu ustawień klienta, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

3.  Aby uzyskać **koligacja użytkowników i urządzeń**, określić następujące ustawienia:  

    -   **Próg koligacji użytkownika i urządzenia (minuty)**. Ustaw liczbę minut użycia urządzenia przed utworzeniem koligacji urządzenia użytkownika.  

    -   **Próg koligacji użytkownika i urządzenia (dni)**. Ustaw liczbę dni, przez jaką jest mierzony próg koligacji na podstawie użycia.  

    -   **Automatycznie Konfiguruj koligację urządzenia użytkownika na podstawie danych użycia**. Aby umożliwić lokacji automatycznego tworzenia koligacji urządzeń użytkowników, z listy rozwijanej, wybierz **True**. W przypadku wybrania **False**, musisz zatwierdzić wszystkie przypisania koligacji urządzenia użytkownika.  

    > [!TIP]  
    > **Przykład:** Jeśli ustawisz **próg koligacji użytkownika i urządzenia (minuty)** do **60** minut i należy ustawić **próg koligacji użytkownika i urządzenia (dni)** do**5** dni, użytkownik musi używać urządzenia przez co najmniej 60 minut w okresie 5 dni w celu automatycznego utworzenia koligacji urządzenia użytkownika.  

Po utworzeniu koligacji urządzenia użytkownika automatyczne programu Configuration Manager kontynuuje monitorowanie progów koligacji urządzeń użytkowników. Jeśli aktywność użytkownika na urządzeniu spadnie poniżej progów, który został skonfigurowany, koligacji urządzenia użytkownika zostanie usunięte. Ustaw **próg koligacji użytkownika i urządzenia (dni)** wartość co najmniej **7** dni, aby uniknąć sytuacji, w których automatycznie skonfigurowana koligacja urządzenia użytkownika może zostać utracona, gdy użytkownik nie jest zalogowany, na przykład przez weekend.  

## <a name="import-user-device-affinities-from-a-file"></a>Importowanie koligacji urządzenia użytkownika z pliku  
 W tym samym czasie, aby utworzyć relacje wiele można zaimportować pliku, który zawiera szczegóły dotyczące wielu koligacje urządzenia użytkownika. Do wykonania tej procedury, urządzenia muszą zostać wykryte i istnieć jako zasoby w bazie danych programu Configuration Manager lub procedura zakończy się niepowodzeniem.  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **użytkowników** lub **urządzeń**.  

2.  Na **Home** karcie **Utwórz** grupy, wybierz **Importuj koligację urządzenia użytkownika**.  

3.  W Kreatorze koligacji urządzenia użytkownika importu na **wybierz mapowanie** ustaw te informacje:  

    -   **Nazwa pliku**. Określ plik wartości rozdzielanych przecinkami (CSV), który zawiera listę użytkowników i urządzeń, między którymi chcesz utworzyć koligacje. W tym pliku każda para użytkownika i urządzenie musi być w oddzielnym wierszu wartości rozdzielonych przecinkami. Użyj tego formatu: <*domeny*>&#92;<*nazwy użytkownika*>, <*nazwa NetBIOS urządzenia*>.  

    -   **Ten plik zawiera nagłówki kolumn do celów referencyjnych**. Jeśli plik CSV zawiera nagłówek w górnym wierszu, wybierz tę opcję, wiersz nagłówka jest ignorowane podczas importu.  

4.  Jeśli importowany plik zawiera więcej niż dwa elementy w każdym wierszu, możesz użyć **kolumny** i **przypisać** do określenia, które kolumny reprezentują użytkowników i urządzeń, a które kolumny mają zostać zignorowane podczas importowania.  

5.  Wybierz **dalej**, a następnie Zakończ Kreatora importowania koligacji urządzeń użytkownika.  

## <a name="let-users-create-their-own-device-affinities"></a>Zezwala użytkownikom na tworzenie własnych koligacji urządzenia  
 Z następnej procedury można skonfigurować użytkownika do tworzenia własnych koligacji urządzenia użytkownika w aplikacji Centrum oprogramowania.  

### <a name="set-up-the-site-to-allow-user-created-user-device-affinity-requests"></a>Konfigurowanie lokacji umożliwia żądaniami koligacji urządzeń użytkownika utworzone przez użytkownika  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta**.  

2.  Aby zmodyfikować domyślne ustawienia klienta, wybierz opcję **domyślnych ustawień klienta**, a następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**. Aby utworzyć ustawienia niestandardowe klienta agenta, wybierz **ustawień klienta** węzła, a następnie na **Home** karcie **Utwórz** grupy, wybierz **Utwórz niestandardowe ustawienia użytkownika klienta**.  

    > [!NOTE]  
    > Po zmodyfikowaniu domyślnych ustawień klienta zostaną one wdrożone na wszystkich komputerach w hierarchii. Aby uzyskać więcej informacji o konfigurowaniu ustawień klienta, zobacz [Konfigurowanie ustawień klienta](../../core/clients/deploy/configure-client-settings.md).  

3.  Wybierz ustawienie klienta **Koligacja użytkowników i urządzeń** , a następnie z listy rozwijanej **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych** wybierz wartość **Prawda**.  

### <a name="set-up-a-user-device-affinity"></a>Konfigurowanie koligacji urządzenia użytkownika  

1.  W katalogu aplikacji, wybierz **Moje systemy**.  

2.  Wybierz opcję **regularnie używam tego komputera do pracy**.  

## <a name="manage-user-device-affinity-requests-from-users"></a>Zarządzanie żądaniami koligacji urządzenia użytkownika od użytkowników  
 Jeśli ustawienie klienta **Automatycznie konfiguruj koligację użytkownika i urządzenia na podstawie danych użycia** ma wartość **Fałsz**, musisz zatwierdzić wszystkie przypisania koligacji urządzenia użytkownika.  

### <a name="approve-or-reject-a-user-device-affinity-request"></a>Zatwierdzanie lub odrzucanie żądania koligacji urządzenia użytkownika  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** wybierz kolekcję użytkowników lub urządzeń, dla której chcesz zarządzać żądaniami koligacji.  

3.  Na **Home** karcie **kolekcji** grupy, wybierz **Zarządzaj żądaniami koligacji**.  

4.  W **Zarządzanie żądaniami koligacji urządzeń użytkownika** okno dialogowe, wybierz żądanie koligacji, a następnie wybierz **Zatwierdź** lub **Odrzuć**.  
