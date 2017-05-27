---
title: "Możliwości w Technical Preview 1610 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1610."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 59633ce68e2bb2d722900215751f345d6d098721
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1610 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*



Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1610. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filtrowanie według rozmiaru zawartości w zasadach wdrażania automatycznego
Teraz można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Na przykład można ustawić **zawartości rozmiar (KB)** odfiltrować **< 2048** tylko pobrać aktualizacje oprogramowania, które są mniejsze niż 2 MB. Za pomocą tego filtra zapobiega dużych aktualizacje automatyczne pobieranie lepszą obsługę uproszczony Windows niskiego poziomu obsługi, gdy przepustowość sieci jest ograniczona. Aby uzyskać szczegółowe informacje, zobacz [programu Configuration Manager i uproszczony obsługi systemu Windows na dół systemami operacyjnymi](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

#### <a name="to-configure-the-content-size-field"></a>Aby skonfigurować rozmiar zawartości pola
Do konfigurowania **zawartości rozmiar (KB)** pola, przejdź do **aktualizacji oprogramowania** automatycznego wdrażania Kreatora tworzenia reguł podczas tworzenia ADR lub przejdź do strony **aktualizacji oprogramowania** we właściwości istniejącego ADR.

![Rozmiar zawartości pola](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>Udoskonalone funkcje w oknach dialogowych wymaganego oprogramowania
Kiedy użytkownik otrzyma wymaganego oprogramowania, od **Odłóż i Przypomnij mi:** ustawienia, można wybrać z listy rozwijanej następujące wartości:
- Później: Określa zaplanowane powiadomienia na podstawie ustawień powiadomień skonfigurowanym w ustawieniach agenta klienta.
- Stały czas: Określa, czy powiadomienia są planowane do wyświetlenia ponownie po zaznaczony czas. Na przykład jeśli użytkownik wybierze opcję 30 minut, powiadomienia wyświetli się ponownie w ciągu 30 minut.

![Komputer agenta strony w ustawieniach agenta klienta](media/computeragentsettings.png)

Czas maksymalny odłożenia zawsze opiera się na wartości powiadomienia skonfigurowanym w ustawieniach agenta klienta w każdej chwili wzdłuż osi czasu wdrożenia. Na przykład jeśli **wdrożenia termin ostateczny dłużej niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie agenta do komputera jest konfigurowane przez 10 godzin i jest więcej niż 24 godziny przed upływem ostatecznego terminu przy uruchomieniu okna dialogowego, użytkownik będzie udostępniana zestaw opcji czuwania do ale nigdy nie większa niż 10 godzin. Jak zbliża się termin, okno dialogowe wyświetli mniej opcji zgodne z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wdrożenia o wysokim ryzyku, takie jak sekwencji zadań, która wdraża system operacyjny powiadomienia użytkownika końcowego jest teraz bardziej niepożądanego. Zamiast powiadomień paska zadań przejściowy, zawsze, gdy użytkownik zostanie powiadomiony, że konserwacji krytyczne oprogramowanie jest wymagane okno dialogowe takich jak następujące wyświetla na komputerze użytkownika:

![Wymagane oprogramowanie okna dialogowego](media/requiredsoftwaredialog.png)


Aby uzyskać więcej informacji:
- [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Jak skonfigurować ustawienia klienta](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>Odrzucanie żądań uprzednio zatwierdzonych aplikacji

Jako administrator możesz teraz odrzucanie żądań zatwierdzone wcześniej aplikacji. Odmowa raz, aby zainstalować tę aplikację później użytkownicy muszą ponownie prześlij żądanie. Odmowa nie powoduje odinstalowania aplikacji; raczej wymusi reapproval dla dowolnego nowego żądania dla tej aplikacji z tego użytkownika. Wcześniej odmowa żądania aplikacji był dostępny wyłącznie dla żądania aplikacji, które nie zostały zatwierdzone.

#### <a name="try-it-out"></a>Wypróbuj to
Odrzucanie aplikacji zatwierdził żądanie:

1.    W konsoli programu Configuration Manager [tworzenie i wdrażanie aplikacji](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications) wymagające zatwierdzenia.
2.    Na komputerze klienckim otwórz Centrum oprogramowania i przesłać żądania dla aplikacji.
3.    W konsoli programu Configuration Manager zatwierdzić żądanie aplikacji.
4.    Odmowa żądania zatwierdzonych aplikacji: W konsoli programu Configuration Manager Przejdź **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **żądań zatwierdzenia** i wybierz chcesz odrzucić żądanie aplikacji.  Na wstążce kliknij **Odmów**.

## <a name="exclude-clients-from-automatic-upgrade"></a>Wyklucz klientów z automatycznej aktualizacji
Technical Preview 1610 wprowadza nowe ustawienie służące do wykluczenia kolekcję klientów z automatycznie instalowanie klienta zaktualizowanej wersji.  Dotyczy to automatyczne uaktualnianie, jak również innych metod, takich jak uaktualnienie oparta na aktualizacji oprogramowania, skryptów logowania i zasad grupy. Może być używany dla kolekcji komputerów, które muszą opieka większe w przypadku uaktualniania klienta. Klient, który znajduje się w kolekcji wykluczonych ignoruje żądania do zainstalowania zaktualizowanego oprogramowania klienckiego.

### <a name="configure-exclusion-from-automatic-upgrade"></a>Skonfiguruj wykluczenia z automatycznej aktualizacji
Aby skonfigurować automatyczne uaktualnienia wykluczenia:
1.    W konsoli programu Configuration Manager Otwórz **ustawienia hierarchii** pod **Administracja > Konfiguracja lokacji > witryny**, a następnie wybierz **uaktualnienie klienta** kartę.
2.    Zaznacz pole wyboru dla **Wyklucz określone klientów z uaktualnienia**, a następnie dla **kolekcji wykluczeń**, wybierz kolekcję, aby wykluczyć. Możesz wybrać tylko jedną kolekcję do wykluczenia.
3.    Kliknij przycisk **OK** zamknąć i zapisać konfigurację. Następnie po klientów aktualizacji zasad, klienci w kolekcji wykluczonych nie będzie automatycznie zainstaluje aktualizacje oprogramowania klienckiego.

  ![Ustawienia automatycznego uaktualniania wykluczeń](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> Chociaż interfejs użytkownika stwierdza, że klienci nie zostaną uaktualnione przy użyciu dowolnej metody, istnieją dwie metody używanej do zastąpienia tych ustawień. Instalację wypychaną klienta i ręcznej instalacji klienta może służyć do zastąpienia tej konfiguracji. Aby uzyskać więcej informacji zobacz sekcję następujące.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Jak uaktualnić klienta, który jest wykluczony kolekcji
Tak długo, jak długo kolekcja jest skonfigurowana do wykluczenia, Członkowie tej kolekcji może mieć tylko uaktualnić przy użyciu jednej z dwóch metod, które zastąpią wykluczeń oprogramowania klienta:
 - **Instalację wypychaną klienta** — instalacji wypychanej klienta służy do uaktualniania klienta, który jest wykluczony kolekcji. To jest dozwolone, gdyż uważa się zamiar administratora i pozwala na uaktualnienie klientów bez usuwania całą kolekcję z wykluczeń.       
 - **Ręczna instalacja klienta** — można ręcznie uaktualnić klientów, którzy są w wykluczonych kolekcji, korzystając z następującego przełącznika wiersza polecenia przy użyciu programu ccmsetup: ***/ignoreskipupgrade***

  Jeśli próba ręcznie uaktualnić klienta, który jest członkiem kolekcji wykluczone i nie należy używać tego przełącznika, klient nie zainstaluje nowe oprogramowanie klienckie. Aby uzyskać więcej informacji, zobacz [jak instalować klientów programu Configuration Manager ręcznie](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually).

Aby uzyskać więcej informacji na temat metod instalacji klienta można znaleźć w temacie [wdrażanie klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

## <a name="windows-defender-configuration-settings"></a>Ustawienia konfiguracji usługi Windows Defender

Na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 za pomocą elementów konfiguracji w konsoli programu Configuration Manager można teraz skonfigurować ustawienia klienta usługi Windows Defender.

W szczególności można skonfigurować następujące ustawienia usługi Windows Defender:
- Zezwalaj na monitorowanie w czasie rzeczywistym
- Zezwalaj na monitorowanie zachowania
- Włącz system inspekcji sieci
- Skanuj wszystkie pobrane pliki
- Zezwalaj na skanowanie skryptów
- Monitorowanie działania plików i programów
  - Pliki monitorowane
- Liczba dni śledzenia wykrytego złośliwego oprogramowania
- Zezwalaj na dostęp do interfejsu użytkownika klienta
- Harmonogram skanowania systemu
  - Dzień zaplanowane
  - Zaplanowana godzina
- Zaplanuj codzienne szybkie skanowanie
  - Zaplanowana godzina
- % Użycia limitu Procesora podczas skanowania Skanuj pliki archiwum
- Skanuj wiadomości e-mail
- Skanuj dyski wymienne
- Skanuj zamapowane dyski
- Skanuj pliki otwierane z udostępnionych net
- Interwał aktualizacji sygnatur
- Zezwalaj na ochrony chmury
- Pytaj użytkowników o przykłady
- Potencjalnie niechciane aplikacji wykrywania
- Wykluczonych plików/folderów
- Rozszerzenia plików wykluczonych
- Wykluczonych procesów

> [!NOTE]
> Te ustawienia można skonfigurować tylko na komputerach klienckich z systemem Windows 10 listopada Update (1511) lub nowszej.

### <a name="try-it-out"></a>Wypróbuj to!

1.    W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > **ustawień zgodności** > **elementy konfiguracji**i Utwórz nową **elementu konfiguracji**.
2.    Wprowadź nazwę, a następnie wybierz **Windows 8.1 i Windows 10** pod **zarządzane ustawienia urządzeń bez klienta programu Configuration Manager** i kliknij przycisk **dalej**.
3.    Upewnij się, **wszystkie systemu Windows 10 (wersja 64-bitowa)** i **wszystkie systemu Windows 10 (wersja 32-bitowa)** wybranych na **obsługiwane platformy** strony, a następnie kliknij przycisk **dalej**.
4.    Wybierz **programu Windows Defender** ustawienie grupy, następnie kliknij przycisk **dalej**.
5.    Skonfiguruj odpowiednie ustawienia na tej stronie, a następnie kliknij przycisk **dalej**.
6.    Ukończ pracę kreatora.
7.    Dodaj ten element konfiguracji do linii bazowej konfiguracji i wdrażania tej linii bazowej na komputerach z systemem Windows 10 listopada aktualizacji (1511) lub nowszej.

> [!NOTE]
> Należy pamiętać sprawdzić **korygowanie niezgodnych ustawień** wyboru podczas wdrażania linii bazowej konfiguracji.

## <a name="request-policy-sync-from-administrator-console"></a>Żądanie zasad synchronizacji z konsoli administratora

Teraz można zażądać synchronizacji zasad dla urządzeń przenośnych z konsoli programu Configuration Manager, bez konieczności wprowadzania żądania synchronizacji z urządzenia. Informacje o stanie żądania synchronizacji jest dostępna jako nową kolumnę w widokach urządzenia, o nazwie **zdalnego stan synchronizacji**. Stan pojawia się również w **danych wykrywania** części **właściwości** okno dialogowe dla każdego urządzenia przenośnego.

### <a name="try-it-out"></a>Wypróbuj to!

1.    W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > urządzenia.
2.    W **zdalnego akcji urządzenia** menu, wybierz opcję **Wyślij żądanie synchronizacji**.

Synchronizacja może zająć pięciu do dziesięciu minut. Wszelkie zmiany w zasadach są synchronizowane z urządzeniem. Możesz śledzić stan żądania synchronizacji w **stan synchronizacji zdalnego** kolumny w **urządzeń** widoku lub na urządzeniu **właściwości** okna dialogowego.

## <a name="additional-security-role-support"></a>Obsługa roli zabezpieczeń

Oprócz pełny Administrator następujące wbudowanych ról zabezpieczeń teraz mają pełny dostęp do elementów w **wszystkie urządzenia należące** węzła, w tym **Predeclared urządzeń**, **iOS profile rejestracji**, i **profilami rejestracji systemu Windows**: • **Menedżera zasobów** • **Menedżer dostępu do zasobów firmy**

Tylko do odczytu do tych obszarów konsoli programu Configuration Manager nadal dostęp do **analityk z uprawnieniami tylko do odczytu** roli.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Funkcja dostępu warunkowego dla profilów sieci VPN systemu Windows 10

Możesz teraz wymagać systemu Windows 10 urządzeń zarejestrowanych w usłudze Azure Active Directory zgodności w celu dostępu do sieci VPN za pomocą profili sieci VPN systemu Windows 10 utworzone w konsoli programu Configuration Manager. Można to zrobić za pomocą nowej **Włącz dostęp warunkowy dla tego połączenia VPN** pole wyboru na **metodę uwierzytelniania** strony Kreatora profilu sieci VPN i właściwości profilu sieci VPN dla profilów sieci VPN systemu Windows 10. Można również określić osobny certyfikatu dla uwierzytelniania rejestracji jednokrotnej po włączeniu dostępu warunkowego dla profilu.

## <a name="see-also"></a>Zobacz też
[Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md)

