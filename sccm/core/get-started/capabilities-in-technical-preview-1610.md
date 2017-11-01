---
title: Funkcje w wersji zapoznawczej Technical Preview 1610
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1610."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b58595bd02a78dea4f8925765dae344c3234a047
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1610 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*



W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1610. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filtruj według rozmiaru zawartości w regułach wdrażania automatycznego
Teraz można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Na przykład można ustawić **zawartości rozmiar (KB)** filtrowane w celu **< 2048** tylko pobrać aktualizacje oprogramowania, które są mniejsze niż 2 MB. Przy użyciu tego filtru uniemożliwia aktualizacje oprogramowania dużych automatyczne pobieranie lepsze uproszczone Obsługa systemu Windows niższego poziomu obsługi, gdy przepustowość sieci jest ograniczona. Aby uzyskać więcej informacji, zobacz [programu Configuration Manager i uproszczone Obsługa systemu Windows na dół systemami operacyjnymi](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

#### <a name="to-configure-the-content-size-field"></a>Aby skonfigurować rozmiar zawartości pola
Aby skonfigurować **zawartości rozmiar (KB)** pola, przejdź do **aktualizacji oprogramowania** automatycznego wdrażania Kreatora tworzenia reguł podczas tworzenia reguły ADR lub przejdź do strony **aktualizacji oprogramowania** we właściwości istniejącej reguły ADR.

![Rozmiar zawartości pola](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>Udoskonalone funkcje w oknach dialogowych wymaganego oprogramowania
Kiedy użytkownik odbiera wymaganego oprogramowania, z **Odłóż i Przypomnij:** ustawienie, można wybrać z listy rozwijanej następujące wartości:
- Później: Określa, czy powiadomienia zostały zaplanowane na podstawie ustawień powiadomień skonfigurowanego w ustawieniach agenta klienta.
- Stały czas: Określa, że powiadomienie zostanie zaplanowane do wyświetlenia ponownie po wybrana wartość czasu. Na przykład jeśli użytkownik wybierze 30 minut, powiadomienia wyświetli się ponownie w ciągu 30 minut.

![Konfiguracja agenta w ustawieniach agenta klienta](media/computeragentsettings.png)

Czas włączenia trybu czuwania maksymalną zawsze opiera się na wartości powiadomień skonfigurowanego w ustawieniach agenta klienta w czasie, co na osi czasu wdrażania. Na przykład jeśli **wdrożenia termin ostateczny dłuższego niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie na komputerze agenta strona jest skonfigurowana do 10 godzin i po uruchomieniu okna dialogowego jest dłuższy niż 24 godziny przed upływem ostatecznego terminu, użytkownik obejmowałoby z zestawu opcji włączenia trybu czuwania do lecz nigdy nie więcej niż 10 godzin. Jak zbliża się termin okna dialogowego zostaną wyświetlone mniej opcji zgodne z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wysokiego ryzyka, takiego jak wdrożenie sekwencji zadań, która wdraża system operacyjny środowisko użytkownika końcowego powiadomień jest teraz bardziej natrętnych. Zamiast przejściowej zadań powiadomienie o każdym razem, gdy użytkownik jest powiadamiany, że konserwacji krytyczne oprogramowanie jest wymagane okno dialogowe takie jak następujące wyświetla na komputerze użytkownika:

![Wymagane oprogramowanie okna dialogowego](media/requiredsoftwaredialog.png)


Aby uzyskać więcej informacji:
- [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Jak skonfigurować ustawienia klienta](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>Odrzucanie żądań zatwierdzone wcześniej aplikacji

Jako administrator możesz teraz odrzucanie żądań wcześniej zatwierdzonych aplikacji. Odmowa raz, aby zainstalować tę aplikację nowsze użytkownicy muszą ponownie prześlij żądanie. Odmowa nie powoduje odinstalowania aplikacji; zamiast wymusi reapproval dla dowolnego nowego żądania dla tej aplikacji z tego użytkownika. Wcześniej odmowy żądania aplikacji była dostępna tylko dla żądań aplikacji, które nie zostały zatwierdzone.

#### <a name="try-it-out"></a>Podczas próby
Odrzucanie aplikacji zatwierdził żądanie:

1.  W konsoli programu Configuration Manager [tworzenie i wdrażanie aplikacji](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications) który wymaga zatwierdzenia.
2.  Na komputerze klienckim otwórz Centrum oprogramowania i prześlij żądanie do aplikacji.
3.  W konsoli programu Configuration Manager zatwierdzić żądań aplikacji.
4.  Odrzucanie żądań zatwierdzonych aplikacji: W konsoli programu Configuration Manager Przejdź **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **żądań zatwierdzenia** i wybierz żądanie aplikacji chcesz odmówić.  Na wstążce kliknij **Odmów**.

## <a name="exclude-clients-from-automatic-upgrade"></a>Wyklucz z automatycznego uaktualnienia klientów
Technical Preview 1610 wprowadza nowe ustawienie służące do wykluczenia kolekcję klientów z automatycznego instalowania wersji zaktualizowanego klienta.  Dotyczy to automatycznego uaktualniania, a także innych metod, takich jak uaktualnianie oparta na aktualizacji oprogramowania, skryptów logowania i zasad grupy. Może być używany dla kolekcji komputerów, które wymagają większej szczególną uwagę podczas uaktualniania klienta. Klient, który znajduje się w wykluczonej kolekcji ignoruje żądania instalacji oprogramowania zaktualizowanego klienta.

### <a name="configure-exclusion-from-automatic-upgrade"></a>Konfiguruj wykluczenia z automatycznej aktualizacji
Aby skonfigurować automatyczne uaktualnienia wykluczenia:
1.  W konsoli programu Configuration Manager Otwórz **ustawienia hierarchii** w obszarze **Administracja > Konfiguracja lokacji > witryn**, a następnie wybierz **uaktualnienie klienta** kartę.
2.  Zaznacz pole wyboru **Wyklucz określone klientów z uaktualnienia**, a następnie **wykluczania kolekcji**, wybierz kolekcję, które chcesz wykluczyć. Można wybrać tylko jednej kolekcji do wykluczenia.
3.  Kliknij przycisk **OK** zamknąć i zapisać konfigurację. Następnie po klientów aktualizacji zasad, klienci w kolekcji wykluczonych przestaną być automatycznie zainstaluje aktualizacje oprogramowania klienckiego.

  ![Ustawienia automatycznego uaktualniania wykluczeń](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> Chociaż interfejs użytkownika stwierdza, że klienci nie zostaną uaktualnione przy użyciu dowolnej metody, istnieją dwie metody, którą można przesłonić te ustawienia. Wypychana instalacja klienta i ręczna instalacja klienta może służyć do zastępowania tej konfiguracji. Aby uzyskać więcej informacji zobacz sekcję poniżej.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Jak uaktualnić klienta, który znajduje się w wykluczonej kolekcji
Tak długo, jak kolekcja jest skonfigurowana do wykluczenia, elementy członkowskie tej kolekcji może mieć tylko oprogramowanie klienckie, ich uaktualnić przy użyciu jednej z dwóch metod, które zastąpią wykluczenia:
 - **Wypychana instalacja klienta** — wypychana instalacja klienta służy do uaktualniania klienta, który znajduje się w wykluczonej kolekcji. To jest dozwolona, ponieważ jest on uznawany za można zamiar administratora i pozwala na uaktualnienie klientów bez usuwania całą kolekcję z wykluczeń.       
 - **Ręczna instalacja klienta** — należy ręcznie uaktualnić klientów, którzy są w wykluczonej kolekcji, gdy użytkownik korzysta z programu ccmsetup następujący przełącznik wiersza polecenia: ***/ignoreskipupgrade***

  Jeśli próba ręcznie uaktualnić klienta, który jest członkiem kolekcji wykluczonych i nie należy używać tego przełącznika, klient nie zainstaluje nowe oprogramowanie klienckie. Aby uzyskać więcej informacji, zobacz [jak zainstalować ręcznie Configuration Manager klientów](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually).

Aby uzyskać więcej informacji na temat metod instalacji klienta, zobacz [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

## <a name="windows-defender-configuration-settings"></a>Ustawienia konfiguracji usługi Windows Defender

Można teraz skonfigurować ustawienia klienta usługi Windows Defender na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 za pomocą elementów konfiguracji w konsoli programu Configuration Manager.

W szczególności można skonfigurować następujące ustawienia usługi Windows Defender:
- Zezwalaj na monitorowanie w czasie rzeczywistym
- Zezwalaj na monitorowanie zachowania
- Włącz system inspekcji sieci
- Skanuj wszystkie pobrane pliki
- Zezwalaj na skanowanie skryptów
- Monitoruj działanie plików i programów
  - Pliki monitorowane
- Liczba dni śledzenia wykrytego złośliwego oprogramowania
- Zezwalaj na dostęp do interfejsu użytkownika klienta
- Zaplanuj skanowanie systemu
  - Zaplanowany dzień
  - Zaplanowana godzina
- Zaplanuj codzienne szybkie skanowanie
  - Zaplanowana godzina
- % Użycia limitu procesora CPU podczas skanowania Skanuj pliki archiwum
- Skanuj wiadomości e-mail
- Skanuj dyski wymienne
- Skanuj zamapowane dyski
- Skanuj pliki otwierane z udziałów net
- Interwał aktualizacji sygnatur
- Zezwalaj na ochronę w chmurze
- Pytaj użytkowników o próbek
- Potencjalnie niechcianych aplikacji wykrywania
- Wykluczone pliki/foldery.
- Rozszerzenia plików wykluczonych
- Wykluczonych procesów

> [!NOTE]
> Te ustawienia można skonfigurować tylko na komputerach klienckich z systemem Windows 10 listopada aktualizacji (1511) lub nowszym.

### <a name="try-it-out"></a>Wypróbuj

1.  W konsoli programu Configuration Manager przejdź do pozycji **zasoby i zgodność** > **omówienie** > **ustawień zgodności** > **elementy konfiguracji**i utworzyć nową **elementu konfiguracji**.
2.  Wprowadź nazwę, a następnie wybierz **Windows 8.1 i Windows 10** w obszarze **ustawienia dla urządzeń zarządzanych bez klienta programu Configuration Manager** i kliknij przycisk **dalej**.
3.  Upewnij się, **wszystkie systemu Windows 10 (wersja 64-bitowa)** i **wszystkie systemu Windows 10 (wersja 32-bitowa)** zostały wybrane na **obsługiwane platformy** strony, a następnie kliknij przycisk **dalej**.
4.  Wybierz **usługa Windows Defender** ustawienie grupy, następnie kliknij przycisk **dalej**.
5.  Skonfiguruj odpowiednie ustawienia na tej stronie, a następnie kliknij przycisk **dalej**.
6.  Ukończ pracę kreatora.
7.  Dodać ten element konfiguracji do linii bazowej konfiguracji, a następnie wdrożyć na komputerach z systemem Windows 10 listopada aktualizacji tej linii bazowej (1511) lub nowszy.

> [!NOTE]
> Pamiętaj, aby sprawdzić **Koryguj niezgodne ustawienia** wyboru podczas wdrażania linii bazowej konfiguracji.

## <a name="request-policy-sync-from-administrator-console"></a>Żądania zasady synchronizacji z konsoli administratora

Może teraz wysłać żądanie synchronizacji zasad dla urządzeń przenośnych z konsoli programu Configuration Manager, bez konieczności żądania synchronizacji z urządzenia. Informacje o stanie żądanie synchronizacji jest dostępna jako nową kolumnę w widokach urządzenia o nazwie **stan synchronizacji zdalnej**. Stan jest także wyświetlany w **danych odnajdywania** sekcji **właściwości** okna dialogowego na każdym urządzeniu przenośnym.

### <a name="try-it-out"></a>Wypróbuj

1.  W konsoli programu Configuration Manager przejdź do pozycji **zasoby i zgodność** > **omówienie** > urządzenia.
2.  W **akcje urządzeń zdalnych** menu, wybierz opcję **Wyślij żądanie synchronizacji**.

Synchronizacja może potrwać od pięciu do dziesięciu minut. Wszelkie zmiany w zasadach są synchronizowane z urządzeniem. Można śledzić stan żądania synchronizacji **stan synchronizacji zdalnej** kolumny w **urządzeń** widoku lub na urządzeniu **właściwości** okna dialogowego.

## <a name="additional-security-role-support"></a>Obsługa roli zabezpieczeń

Oprócz administrator o pełnych uprawnieniach, następujące wbudowanych ról zabezpieczeń teraz mają pełny dostęp do elementów w **wszystkich firmowych urządzeń** węzła, w tym **wcześniej zadeklarowanej urządzeń**, **profile rejestracji systemu iOS**, i **profilami rejestracji systemu Windows**: • **Menedżera zasobów** • **Menedżer dostępu do zasobów firmy**

Tylko do odczytu do tych obszarów konsoli programu Configuration Manager nadal dostęp do **analityk z uprawnieniami tylko do odczytu** roli.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Dostęp warunkowy dla profilów sieci VPN systemu Windows 10

Można teraz wymagają systemu Windows 10 urządzenia zarejestrowane w usłudze Azure Active Directory, aby było zgodne, aby mieć dostęp do sieci VPN za pomocą profilów VPN w systemie Windows 10 utworzone w konsoli programu Configuration Manager. Można to zrobić za pomocą nowej **włączania dostępu warunkowego dla tego połączenia VPN** wyboru na **metodę uwierzytelniania** strony Kreatora profilu sieci VPN i właściwości profilu sieci VPN, profilów sieci VPN systemu Windows 10. Można również określić oddzielny certyfikat dla pojedynczego uwierzytelniania logowania, po włączeniu dostępu warunkowego dla profilu.

## <a name="see-also"></a>Zobacz też
[Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md)
