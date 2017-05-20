---
title: "Monitorowanie użycia aplikacji z zliczania oprogramowania | Dokumentacja firmy Microsoft"
description: 
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1fdaee2-2816-4447-94cd-609f6948f215
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a85a5cece803e5c16da71f897d5780049fbb82cd
ms.openlocfilehash: eddf20bebd80028336503957dfc4c3d1dbbb23f2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="software-metering-in-system-center-configuration-manager"></a>Pomiar użytkowania oprogramowania System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera odwołania do wszystkich operacji, które można wykonać przy użyciu zliczania oprogramowania System Center Configuration Manager.

> [!IMPORTANT]
>  Pomiar użytkowania oprogramowania służy do monitorowania aplikacji na komputerze z systemem Windows, których nazwa pliku kończy się rozszerzeniem **exe**. Pomiar użytkowania oprogramowania nie monitoruje nowoczesnych aplikacji systemu Windows (na przykład używanych przez system Windows 8).

##  <a name="prerequisites-for-software-metering"></a>Wymagania wstępne dotyczące pomiaru oprogramowania
Pomiar użytkowania oprogramowania nie ma zależności zewnętrznych — ma on tylko zależności w obrębie produktu.

|Zależność|Więcej informacji|
|----------------|----------------------|
|Ustawienia klienta dotyczące pomiaru użytkowania oprogramowania.|Aby można było korzystać z pomiaru użytkowania oprogramowania, na komputerach musi być włączone i wdrożone ustawienie klienta **Włącz zliczanie oprogramowania na klientach** . Możesz wdrożyć ustawienia pomiaru użytkowania oprogramowania na wszystkich komputerach w hierarchii lub wdrożyć ustawienia niestandardowe w grupach komputerów. Zobacz **skonfigurować zliczania oprogramowania** w tym temacie.|
|Punkt usług raportowania.|Aby móc wyświetlać raporty pomiaru użytkowania oprogramowania, musisz skonfigurować punkt usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).|

##  <a name="configure-software-metering"></a>Konfigurowanie zbierania danych oprogramowania
 Poniżej przedstawiono procedurę konfigurowania domyślnych ustawień klienta dotyczących pomiaru użytkowania oprogramowania, która dotyczy wszystkich komputerów w hierarchii. Jeśli te ustawienia mają być stosowane tylko do niektórych komputerów, utwórz niestandardowe ustawienie klienta urządzenia i wdróż je w kolekcji zawierającej komputery, na których chcesz używać pomiaru użytkowania oprogramowania. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień urządzenia, zobacz [Konfigurowanie ustawień klienta](../../core/clients/deploy/configure-client-settings.md).

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.

2.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.

3.  W oknie dialogowym **Ustawienia domyślne** kliknij pozycję **Zliczanie oprogramowania**.

4.  Na liście **Ustawienia urządzenia** skonfiguruj następujące ustawienia:

    -   **Włącz zliczanie oprogramowania na klientach**: Wybierz **True** umożliwiające zliczania oprogramowania.

    -   **Zbieranie danych**: Konfigurować, jak często dane pomiaru oprogramowania są zbierane z komputerów klienckich. Użyj wartości domyślnej, umożliwiającej zbieranie danych co **7 dni** , lub kliknij pozycję **Harmonogram** , aby określić harmonogram niestandardowy.

5.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia domyślne** .

 Komputery klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobierania zasad dla pojedynczego klienta, zobacz [zarządzania klientami](../../core/clients/manage/manage-clients.md).

##  <a name="create-software-metering-rules"></a>Tworzenie reguł zliczania oprogramowania
 Użyj kreatora Utwórz regułę zliczania oprogramowania, aby utworzyć nową regułę zliczania oprogramowania dla lokacji programu Configuration Manager.

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **zliczania oprogramowania**.

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz regułę zliczania oprogramowania**.

4.  Na **ogólne** strony kreatora Utwórz regułę zliczania oprogramowania, określ następujące informacje:

    -   **Nazwa** — nazwa reguły pomiaru użytkowania oprogramowania. Nazwa musi być unikatowa i opisowa.

        > [!NOTE]
        >  Reguły pomiaru użytkowania oprogramowania mogą mieć tę samą nazwę, jeśli nazwa pliku w regułach jest inna.

    -   **Nazwa pliku** — nazwa pliku programu, dla którego chcesz dokonać pomiaru. Możesz kliknąć przycisk **Przeglądaj** , aby wyświetlić okno dialogowe **Otwieranie** , w którym można wybrać plik programu do użycia.

        > [!NOTE]
        >  Jeśli wpiszesz nazwę pliku wykonywalnego w polu **Nazwa pliku** , nie zostaną przeprowadzone żadne testy mające na celu sprawdzenie, czy ten plik istnieje i czy zawiera wymagane informacje nagłówka. Jeśli to możliwe, kliknij przycisk **Przeglądaj** i wybierz plik wykonywalny, dla którego chcesz dokonać pomiaru.
        >
        >  Nazwa pliku nie może zawierać symboli wieloznacznych.
        >
        >  To pole jest opcjonalne, jeśli określono wartość ustawienia **Oryginalna nazwa pliku** .

    -   **Oryginalna nazwa pliku** — nazwa pliku wykonywalnego, dla którego chcesz dokonać pomiaru. Ta nazwa jest zgodna z informacjami w nagłówku pliku, a nie z samą nazwą pliku, dzięki czemu można jej użyć w sytuacji, gdy zmieniono nazwę pliku wykonywalnego i chcesz dokonać pomiaru według oryginalnej nazwy.

        > [!NOTE]
        >  Oryginalna nazwa pliku nie może zawierać symboli wieloznacznych.
        >
        >  To pole jest opcjonalne, jeśli określono wartość ustawienia **Nazwa pliku** .

    -   **Wersja** — wersja pliku wykonywalnego, dla którego chcesz dokonać pomiaru. Możesz użyć symbolu wieloznacznego (*) odpowiadającego dowolnemu ciągowi znaków lub symbolu wieloznacznego (?) odpowiadającego pojedynczemu znakowi. Do liczników dla wszystkich wersji pliku wykonywalnego, należy użyć wartości domyślnej (\*).

    -   **Język** — język pliku wykonywalnego, dla którego chcesz dokonać pomiaru. Wartością domyślną są bieżące ustawienia regionalne używanego systemu operacyjnego. W przypadku wybrania pliku wykonywalnego do pomiaru przez kliknięcie przycisku **Przeglądaj** to pole zostanie wypełnione automatycznie, jeśli nagłówek pliku zawiera informacje o języku. Aby dokonać pomiaru dla wszystkich wersji językowych pliku, wybierz z listy rozwijanej pozycję **Każdy** .

    -   **Opis** — opcjonalny opis reguły pomiaru użytkowania oprogramowania.

    -   **Zastosuj tę regułę zliczania oprogramowania do następujących klientów** — określ, czy chcesz zastosować regułę pomiaru użytkowania oprogramowania do wszystkich klientów w hierarchii czy do klientów przypisanych do lokacji podanej na liście **Lokacja** .

5.  Aby kontynuować, kliknij przycisk **Dalej**.

6.  Przejrzyj i potwierdź ustawienia, a następnie zakończ pracę kreatora, aby utworzyć regułę pomiaru użytkowania oprogramowania. Nowa reguła pomiaru użytkowania oprogramowania zostanie wyświetlona w węźle **Zliczanie oprogramowania** w obszarze roboczym **Zasoby i zgodność** .

##  <a name="configure-automatic-software-metering-rules"></a>Skonfiguruj automatyczne reguł zliczania oprogramowania
 Można skonfigurować w programie Configuration Manager do automatycznego generowania wyłączone reguł z ostatnich danych spisu użycia przechowywanych w bazie danych zliczania oprogramowania zliczania oprogramowania. Te dane spisu można skonfigurować tak, aby reguły pomiaru były tworzone tylko dla aplikacji używanych na określonej części komputerów. Możesz również określić maksymalną liczbę automatycznie generowanych reguł pomiaru użytkowania oprogramowania dozwolonych w lokacji.

> [!NOTE]
>  Automatycznie tworzone reguły pomiaru użytkowania oprogramowania są domyślnie wyłączone. Aby móc zacząć zbierać dane użycia przy użyciu tych reguł, musisz je włączyć.

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **zliczania oprogramowania**, a następnie w **Home** w karcie **ustawienia** , kliknij przycisk **właściwości zliczania oprogramowania**.

3.  W oknie dialogowym **Właściwości zliczania oprogramowania** skonfiguruj następujące ustawienia:

    -   **Przechowywanie danych (w dniach)** — określa ilość czasu, przez który są przechowywane dane generowane przez reguły pomiaru użytkowania oprogramowania w bazie danych lokacji. Wartość domyślna to **90** dni.

    -   Włącz opcję **Automatycznie twórz wyłączone reguły zliczania na podstawie ostatnich danych spisu użycia**.

    -   **Określ procent komputerów w hierarchii, które muszą użyć programu przed automatycznym utworzeniem reguły zliczania oprogramowania** — wartość domyślna to **10** procent.

    -   **Określ liczbę reguł zliczania oprogramowania, która musi zostać przekroczona w hierarchii przed wyłączeniem automatycznego tworzenia reguł** — wartość domyślna to **100** reguł.

4.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości zliczania oprogramowania** .

##  <a name="manage-software-metering-rules"></a>Zarządzanie reguł zliczania oprogramowania
 W obszarze roboczym **Zasoby i zgodność** wybierz pozycję **Zliczanie oprogramowania**, wybierz regułę pomiaru użytkowania oprogramowania, którą chcesz zarządzać, a następnie wybierz zadanie zarządzania.

 Więcej informacji o zadaniach zarządzania, które mogą przed wybraniem wymagać dodatkowego opisu, znajduje się w poniższej tabeli.

|Zadanie zarządzania|Szczegóły|
|---------------------|-------------|
|**Włączenie**<br /><br /> **Wyłącz**|Włącza lub wyłącza regułę pomiaru użytkowania oprogramowania. To ustawienie jest pobierane na komputery klienckie zgodnie z ustawieniem **Interwał sondowania zasad klienta** w sekcji **Zasady klienta** w ustawieniach klienta (domyślnie sondowanie odbywa się co 60 minut).<br /><br /> Zobacz [Konfigurowanie ustawień klienta](../../core/clients/deploy/configure-client-settings.md) .|

##  <a name="monitor-software-metering"></a>Monitorowanie zliczania oprogramowania
 Pomiar użytkowania oprogramowania Configuration Manager zawiera wiele wbudowanych raportów umożliwiających monitorowanie informacji o operacjach zliczania oprogramowania. Te raporty należą do kategorii **Zliczanie oprogramowania**.

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).

 Ponadto można tworzyć kwerendy i kolekcje oparte na danych przechowywanych w bazie danych programu Configuration Manager przez zliczania oprogramowania.

 Aby uzyskać więcej informacji na temat kolekcje w programie Configuration Manager, zobacz [wprowadzenie do kolekcji](/sccm/core/clients/manage/collections/introduction-to-collections).

 Aby uzyskać więcej informacji dotyczących kwerend w programie Configuration Manager, zobacz [wprowadzenie do kwerend](/sccm/core/servers/manage/introduction-to-queries).

##  <a name="security-and-privacy-for-software-metering"></a>Bezpieczeństwo i prywatność pomiaru oprogramowania

### <a name="security-issues-for-software-metering"></a>Pomiar użytkowania oprogramowania — problemy z zabezpieczeniami
 Osoba atakująca może wysłać nieprawidłowe oprogramowania zliczania informacji do Menedżera konfiguracji, które będą akceptowane przez punkt zarządzania, nawet po wyłączeniu ustawienia klienta zliczania oprogramowania. Może to skutkować dużą liczbę reguł zliczania, które są replikowane w całej hierarchii, co powoduje odmowę usługi w sieci i serwerów lokacji programu Configuration Manager.

 Osoba atakująca może utworzyć nieprawidłowe dane pomiaru użytkowania oprogramowania, dlatego nie należy traktować informacji pomiaru użytkowania oprogramowania jako wiarygodnych.

 Pomiar użytkowania oprogramowania jest domyślnie włączony w ustawieniach klienta.

###  <a name="privacy-information-for-software-metering"></a>Informacje o ochronie prywatności pomiaru oprogramowania
 Pomiar użytkowania oprogramowania monitoruje użycie aplikacji na komputerach klienckich. Pomiar użytkowania oprogramowania jest domyślnie włączony. Musisz skonfigurować aplikacje, dla których chcesz dokonać pomiaru. Pomiaru informacje są przechowywane w bazie danych programu Configuration Manager. Informacje są szyfrowane podczas transferu do punktu zarządzania, ale nie są przechowywane w zaszyfrowanym formacie w bazie danych programu Configuration Manager.

 Te informacje są przechowywane w bazie danych do czasu ich usunięcia w ramach zadań konserwacji lokacji **Usuń przestarzałe dane pomiaru oprogramowania** (co pięć dni) i **Usuń przestarzałe dane podsumowania pomiaru oprogramowania** (co 270 dni). Możesz skonfigurować interwał usuwania. Informacje dotyczące pomiarów nie są wysyłane do firmy Microsoft.

 Przed skonfigurowaniem pomiaru użytkowania oprogramowania należy wziąć pod uwagę wymagania związane z ochroną prywatności.

## <a name="example-scenario-for-using-software-metering"></a>Przykładowy scenariusz zastosowania pomiaru użytkowania oprogramowania
 W tej sekcji utworzysz przykładową regułę pomiaru użytkowania oprogramowania, która może pomóc w określeniu następujących wymagań biznesowych:

-   Określenie liczby kopii danej aplikacji w firmie

-   Odkrycie wszystkich nieużywanych kopii aplikacji

-   Określenie użytkowników, którzy regularnie korzystają z danej aplikacji

 W banku Woodgrove wdrożono pakiet Microsoft Office 2010 jako standardowy pakiet biurowy ułatwiający zarządzanie produktywnością. Jednak do obsługi starszych aplikacji na niektórych komputerach należy nadal używać programu Microsoft Office Word 2003. Dział IT chce ograniczyć koszty licencjonowania i pomocy technicznej przez usunięcie tych kopii programu Word 2003, jeśli aplikacja w starszej wersji nie jest już używana. Dział pomocy technicznej chce również zidentyfikować użytkowników korzystających ze starszej aplikacji.

 Jacek jest Menedżer systemów IT banku Woodgrove, używający zliczania oprogramowania w programie Configuration Manager do osiągnięcia tych celów biznesowych. Wykonuje następujące czynności:

- Jan sprawdza wymagania wstępne dotyczące pomiaru użytkowania oprogramowania i potwierdza, że punkt usług raportowania został zainstalowany i działa.
- Jan konfiguruje domyślne ustawienia na potrzeby pomiaru użytkowania oprogramowania:<br>Włącza pomiar użytkowania oprogramowania i stosuje domyślne harmonogramy zbierania danych co siedem dni.<br>Konfiguruje spis oprogramowania w celu uwzględnienia plików z rozszerzeniem EXE, konfigurując ustawienie klienta spisu oprogramowania **Następujące typy plików do spisu**.<br>Dodaje nową regułę pomiaru użytkowania oprogramowania o nazwie **woodgrove.exe**, aby monitorować starszą aplikację.
- Jan czeka siedem dni, po upływie których komputery klienckie zaczynają raportować dane użycia pliku wykonywalnego **woodgrove.exe** .
- Jan używa raportu programu Configuration Manager **base instalacji dla wszystkich zliczanych programów** komputery, które mają aplikacji **woodgrove.exe** załadowane.
- Po upływie sześciu miesięcy Jan uruchamia raport **Komputery z zainstalowanym mierzonym programem, na których ten program nie został uruchomiony od określonej daty**, określając regułę pomiaru użytkowania oprogramowania i datę przypadającą sześć miesięcy wcześniej. Ten raport umożliwia zidentyfikowanie 120 komputerów, na których w ciągu ostatnich sześciu miesięcy nie uruchomiono programu.
- Jan wykonuje dalsze procesy kontroli, aby potwierdzić, że starsza aplikacja nie jest wymagana na określonych komputerach. Następnie odinstalowuje starszą wersję aplikacji i kopię programu Word 2003 z tych komputerów.<br>Jan uruchamia raport **Użytkownicy, którzy uruchamiali określony mierzony program** , aby przedstawić działowi pomocy technicznej listę użytkowników, którzy nadal używają starszej aplikacji.
- Jan kontynuuje sprawdzanie raportów pomiaru użytkowania oprogramowania co tydzień i w razie potrzeby podejmuje działania naprawcze.

 W wyniku takiego sposobu działania pomocy koszty pomocy technicznej w zakresie IT oraz koszty licencjonowania zostały zredukowane przez usunięcie aplikacji, które nie są już wymagane. Ponadto dział pomocy technicznej ma teraz żądaną listę użytkowników, którzy korzystają ze starszej aplikacji.

