---
title: "Operacje i Obsługa raportowania | Dokumentacja firmy Microsoft"
description: "Dowiedz się, szczegółowe informacje o zarządzaniu raportami i subskrypcjami raportów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89bcfbf-f5b6-4fb1-bb5e-a5cc18ec0c78
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f5a58ba9ecd9b0998c2859b6d3f45e493d7ef3cb
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="operations-and-maintenance-for-reporting-in-system-center-configuration-manager"></a>Operacje i Obsługa raportowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zapewnieniu odpowiedniej infrastruktury umożliwiającej raportowanie w programie System Center Configuration Manager, istnieje wiele operacji, które należy wykonać w celu zarządzania raportami i subskrypcjami raportów.  

##  <a name="BKMK_ManageReports"></a>Zarządzanie raportami programu Configuration Manager  
 Program Configuration Manager udostępnia ponad 400 wstępnie zdefiniowanych raportów, które pomagają gromadzić, organizować i prezentować informacje o użytkownikach, sprzętu i spisu oprogramowania, aktualizacje oprogramowania, aplikacje, stanie lokacji i innych operacji programu Configuration Manager w organizacji. Można użyć wstępnie zdefiniowanych raportów, jak są one lub zmodyfikować raport, zgodnie z wymaganiami. Można również utworzyć niestandardowe modelu\-na podstawie SQL i\-na podstawie raportów zgodnie z wymaganiami. Poniższe sekcje należy użyć w celu zarządzania raportami programu Configuration Manager.  

###  <a name="BKMK_RunReport"></a>Uruchamianie raportu programu Configuration Manager  
 Raporty w programie Configuration Manager są przechowywane w usługach SQL Server Reporting Services, a dane renderowane w raporcie są pobierane z bazy danych lokacji programu Configuration Manager. Dostęp do raportów w konsoli programu Configuration Manager lub za pomocą Menedżera raportów, otwieranego w przeglądarce sieci web. Możesz otworzyć raporty na dowolnym komputerze mającym dostęp do komputera, na którym jest uruchomiony program SQL Server Reporting Services i musi mieć wystarczające uprawnienia do wyświetlania raportów. Po uruchomieniu raportu, tytuł, opis i kategoria są wyświetlane w języku lokalnego systemu operacyjnego.  

> [!NOTE]  
>  W niektórych innych niż\-English języków, znaki mogą nie być wyświetlane prawidłowo w raportach.  W takim przypadku raporty można wyświetlać przy użyciu sieci web\-na podstawie Menedżera raportów lub za pośrednictwem zdalnej konsoli administratora.  

> [!WARNING]  
>  Aby uruchamiać raporty, musi mieć **odczytu** prawami dostępu dla **witryny** uprawnienia i **Uruchom raport** skonfigurowane pod kątem konkretnych obiektów.  

> [!NOTE]  
>  Menedżer raportów usług sieci web jest\-na podstawie raportu dostępu i zarządzania narzędzie, które służy do administrowania pojedynczym wystąpieniem serwera raportów w zdalnej lokalizacji za pośrednictwem połączenia HTTP. Służy Menedżer raportów do zadań operacyjnych, na przykład do wyświetlania raportów, modyfikowania właściwości raportu i zarządzanie subskrypcjami raportów skojarzone. W tym temacie przedstawiono procedury wyświetlania raportu i modyfikowania właściwości raportu w Menedżerze raportów; więcej informacji o innych opcjach dostępnych Menedżera raportów znajduje się w temacie [Menedżera raportów](http://go.microsoft.com/fwlink/p/?LinkId=224916) w SQL Server 2008 — książki Online.  

 Użyj poniższej procedury do uruchamiania raportu programu Configuration Manager.  

##### <a name="to-run-a-report-in-the-configuration-manager-console"></a>Aby uruchomić raport w konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania**, a następnie kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów.  

    > [!IMPORTANT]  
    >  W tej wersji programu Configuration Manager **całą zawartość** wyświetlają tylko pakiety, nie aplikacje.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, należy sprawdzić, czy punkt usług raportowania jest zainstalowany i skonfigurowany. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md).  

3.  Wybierz raport, który chcesz uruchomić, a następnie na **Home** w karcie **grupy raportowania** , kliknij przycisk **Uruchom** aby otworzyć raport.  

4.  Jeśli są wymagane jakieś parametry, określ parametry, a następnie kliknij **Wyświetl raport**.  

#### <a name="to-run-a-report-in-a-web-browser"></a>Aby uruchomić raport w przeglądarce sieci web  

1.  W przeglądarce sieci web wprowadź adres URL Menedżera raportów, na przykład **http:\/\/serwer1\/raporty**. Adres URL Menedżera raportów możesz ustalić na **adres URL Menedżera raportów** strony w Reporting Services Configuration Manager.  

2.  W Menedżerze raportów kliknij folder raportów dla programu Configuration Manager, na przykład **ConfigMgr\_urzędom certyfikacji**.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, należy sprawdzić, czy punkt usług raportowania jest zainstalowany i skonfigurowany. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md).  

3.  Kliknij kategorię raportu, który chcesz uruchomić, a następnie kliknij łącze raportu. Raport zostanie otwarty w Menedżerze raportów.  

4.  Jeśli są wymagane jakieś parametry, określ parametry, a następnie kliknij **Wyświetl raport**.  

###  <a name="BKMK_ModifyReportProperties"></a>Modyfikowanie właściwości raportu programu Configuration Manager  
 W konsoli programu Configuration Manager można wyświetlać właściwości raportu, takie jak nazwa i opis, ale aby zmienić właściwości, za pomocą Menedżera raportów. Poniższa procedura umożliwia modyfikowanie właściwości raportu programu Configuration Manager.  

#### <a name="to-modify-report-properties-in-report-manager"></a>Aby zmodyfikować właściwości raportu w Menedżerze raportów  

1.  W przeglądarce sieci web wprowadź adres URL Menedżera raportów, na przykład **http:\/\/serwer1\/raporty**. Adres URL Menedżera raportów możesz ustalić na **adres URL Menedżera raportów** strony w Reporting Services Configuration Manager.  

2.  W Menedżerze raportów kliknij folder raportów dla programu Configuration Manager, na przykład **ConfigMgr\_urzędom certyfikacji**.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, należy sprawdzić, czy punkt usług Reporting Services jest zainstalowany i skonfigurowany. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md)  

3.  Kliknij kategorię raportu, dla którego chcesz zmodyfikować właściwości, a następnie kliknij łącze raportu. Raport zostanie otwarty w Menedżerze raportów.  

4.  Kliknij przycisk **właściwości** kartę. Można zmodyfikować nazwę i opis raportu.  

5.  Gdy skończysz, kliknij przycisk **Zastosuj**. Właściwości raportu zostają zapisane na serwerze raportów i konsoli programu Configuration Manager pobiera zaktualizowane właściwości raportu.  

###  <a name="BKMK_EditReport"></a>Edytowanie raportu programu Configuration Manager  
 Jeśli istniejący raport programu Configuration Manager nie pobiera informacje, które muszą mieć albo nie oferuje układu lub projekt, można edytować raportu w programie Report Builder.  

> [!NOTE]  
>  Istnieje również możliwość Sklonowanie istniejącego raportu, otwierając go w celu edycji, a następnie klikając polecenie **Zapisz jako** ją zapisać jako nowy raport.  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnienia i **modyfikowanie raportu** uprawnienia do konkretnych obiektów skojarzonych z raportem, który chcesz zmodyfikować.  

> [!IMPORTANT]  
>  Gdy program Configuration Manager zostanie uaktualniony do nowszej wersji, nowe raporty zastępują raporty wstępnie zdefiniowane. W przypadku zmodyfikowania wstępnie zdefiniowanych raportów, należy wykonać kopię raportu przed zainstalowaniem nowej wersji, a potem przywrócić raport w usługach Reporting Services. Jeśli w raporcie wstępnie zdefiniowanym są istotne zmiany, należy wziąć pod uwagę zamiast tego utworzyć nowy raport. Nowe raporty utworzone przed uaktualnieniem lokacji nie zostaną zastąpione.  

 Poniższa procedura służy do edytowania właściwości raportu programu Configuration Manager.  

#### <a name="to-edit-report-properties"></a>Aby edytować właściwości raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania**, a następnie kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów.  

3.  Wybierz raport, który chcesz zmodyfikować, a następnie na **Home** w karcie **grupy raportowania** , kliknij przycisk **edytować**. Wprowadź konto użytkownika i hasło, jeśli zostanie wyświetlony monit, a następnie kliknij **OK**. Na komputerze nie zainstalowano programu Report Builder, monit o zainstalowanie go. Kliknij przycisk **Uruchom** do zainstalowania programu Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

4.  W programie Report Builder zmodyfikuj odpowiednie ustawienia raportu, a następnie kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów.  

###  <a name="BKMK_CreateModelBasedReport"></a>Utwórz model\-na podstawie raportu  
 Model\-na podstawie raportu pozwala interaktywnie wybierać elementy, które chcesz uwzględnić w raporcie. Aby uzyskać więcej informacji o tworzeniu niestandardowych modeli raportów, zobacz [Tworzenie niestandardowych modeli raportów programu System Center Configuration Manager w usługach SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnień do utworzenia nowego raportu. Użytkownik może utworzyć raport tylko w folderach, do których użytkownik ma **modyfikowanie raportu** uprawnienia.  

 Poniższa procedura umożliwia utworzenie modelu\-na podstawie raportu programu Configuration Manager.  

#### <a name="to-create-a-model-based-report"></a>Aby utworzyć model\-na podstawie raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty**.  

3.  Na **Home** w karcie **Utwórz** , kliknij przycisk **Utwórz raport** otworzyć **Kreatora tworzenia raportów**.  

4.  Na **informacji** skonfiguruj następujące ustawienia:  

    -   **Typ**: Wybierz **modelu\-na podstawie raportu** utworzyć raport w programie Report Builder za pomocą modelu usług Reporting Services.  

    -   **Nazwa**: Określ nazwę raportu.  

    -   **Opis**: Określ opis raportu.  

    -   **Serwer**: Wyświetla nazwę serwera raportów, na którym jest tworzony dany raport.  

    -   **Ścieżka**: Kliknij przycisk **Przeglądaj** , aby określić folder, w którym mają być przechowywane w raporcie.  

     Kliknij przycisk **Dalej**.  

5.  Na **wybór modelu** stronie, wybierz dostępny model z listy używanej do tworzenia tego raportu. Kiedy wybierzesz model raportu **podglądu** wyświetlą się widoki programu SQL Server i jednostkami, które są udostępniane przez wybrany model raportu.  

6.  Na stronie **Podsumowanie** przejrzyj ustawienia. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia raportu w programie Configuration Manager.  

7.  Na **potwierdzenia** kliknij **Zamknij** aby zakończyć pracę kreatora, a następnie otwórz program Report Builder, aby skonfigurować ustawienia raportu. Wprowadź konto użytkownika i hasło, jeśli zostanie wyświetlony monit, a następnie kliknij **OK**. Na komputerze nie zainstalowano programu Report Builder, monit o zainstalowanie go. Kliknij przycisk **Uruchom** do zainstalowania programu Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

8.  W programie Microsoft Report Builder Utwórz układ raportu, wybierz dane w dostępnych widokach programu SQL Server, Dodaj do raportu parametry i tak dalej. Aby uzyskać więcej informacji o tworzeniu nowego raportu za pomocą programu Report Builder można znaleźć w temacie Pomocy programu Report Builder.  

9. Kliknij przycisk **Uruchom** do uruchomienia raportu. Sprawdź, czy raport zawiera informacje, które oczekujesz. Kliknij przycisk **projekt** aby powrócić do widoku projektu i zmodyfikować raport, w razie potrzeby.  

10. Kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów. Można uruchamiać i modyfikować nowy raport **raporty** w węźle **monitorowanie** obszaru roboczego.  

###  <a name="BKMK_CreateSQLBasedReport"></a>Utwórz SQL\-na podstawie raportu  
 SQL\-na podstawie raportu pozwala pobierać dane oparte na instrukcji języka SQL dla raportu.  

> [!IMPORTANT]  
>  Tworząc instrukcję języka SQL dla raportu niestandardowego, nie należy bezpośrednio odwoływać tabel programu SQL Server. Zamiast tego należy odwoływać widoków raportowania programu SQL Server \(wyświetlanie nazw rozpoczynających się v\_ \) z bazy danych lokacji. Można także odwoływać się do publicznych procedur składowanych \(przechowywane procedury o nazwach zaczynających sp\_ \) z bazy danych lokacji.  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnień do utworzenia nowego raportu. Użytkownik może utworzyć raport tylko w folderach, do których użytkownik ma **modyfikowanie raportu** uprawnienia.  

 Poniższa procedura umożliwia utworzenie SQL\-na podstawie raportu programu Configuration Manager.  

#### <a name="to-create-a-sql-based-report"></a>Aby utworzyć SQL\-na podstawie raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** rozwiń węzeł **Raportowanie**, a następnie kliknij przycisk **Raporty**.  

3.  Na **Home** w karcie **Utwórz** , kliknij przycisk **Utwórz raport** otworzyć **Kreatora tworzenia raportów**.  

4.  Na **informacji** skonfiguruj następujące ustawienia:  

    -   **Typ**: Wybierz **SQL\-na podstawie raportu** utworzyć raport w programie Report Builder za pomocą instrukcji języka SQL.  

    -   **Nazwa**: Określ nazwę raportu.  

    -   **Opis**: Określ opis raportu.  

    -   **Serwer**: Wyświetla nazwę serwera raportów, na którym jest tworzony dany raport.  

    -   **Ścieżka**: Kliknij przycisk **Przeglądaj** , aby określić folder, w którym mają być przechowywane w raporcie.  

     Kliknij przycisk **Dalej**.  

5.  Na stronie **Podsumowanie** przejrzyj ustawienia. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia raportu w programie Configuration Manager.  

6.  Na **potwierdzenia** kliknij **Zamknij** aby zakończyć działanie kreatora i Otwórz program Report Builder, aby skonfigurować ustawienia raportu. Wprowadź konto użytkownika i hasło, jeśli zostanie wyświetlony monit, a następnie kliknij **OK**. Na komputerze nie zainstalowano programu Report Builder, monit o zainstalowanie go. Kliknij przycisk **Uruchom** do zainstalowania programu Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

7.  W programie Microsoft Report Builder Podaj instrukcję języka SQL dla raportu lub Skonstruuj instrukcję SQL przy użyciu kolumn w dostępnych widokach programu SQL Server, Dodaj do raportu parametry i tak dalej.  

8.  Kliknij przycisk **Uruchom** do uruchomienia raportu. Sprawdź, czy raport zawiera informacje, które oczekujesz. Kliknij przycisk **projekt** aby powrócić do widoku projektu i zmodyfikować raport, w razie potrzeby.  

9. Kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów. Nowy raport możesz uruchamiać **raporty** w węźle **monitorowanie** obszaru roboczego.  

##  <a name="BKMK_ManageReportSubscriptions"></a>Zarządzanie subskrypcjami raportów  
 Subskrypcje raportów w programie SQL Server Reporting Services pozwalają konfigurować automatyczne dostarczanie określonych raportów pocztą e-mail lub do udziału plików w zaplanowanych odstępach czasu. Użyj **Kreatora tworzenia subskrypcji** w System Center 2012 Configuration Manager do konfigurowania subskrypcji raportów.  

###  <a name="BKMK_ReportSubscriptionFileShare"></a>Tworzenie subskrypcji raportu w celu dostarczania raportu do udziału plików  
 Podczas tworzenia subskrypcji raportów w celu dostarczania raportu do udziału plików raport jest kopiowany we wskazanym formacie do określonego udziału plików. Można subskrybować i żądanie dostarczania dla tylko jednego raportu naraz.  

 W przeciwieństwie do raportów, które są obsługiwane i zarządzane przez serwer raportów raporty dostarczane do folderu udostępnionego są plikami statycznymi. Zdefiniowane dla raportu funkcje interaktywne nie działają w przypadku raportów, które są przechowywane jako pliki w systemie plików. Funkcje interakcji są reprezentowane jako elementy statyczne. Jeśli raport zawiera wykresy, domyślny sposób ich prezentacji. Jeśli raport zawiera łącza do innego raportu, łącze jest renderowane jako tekst statyczny. Aby w dostarczanym raporcie zachować funkcje interaktywne, należy zastosować dostarczanie poczty e-mail. Aby uzyskać więcej informacji o dostarczaniu pocztą e-mail, zobacz [utworzyć subskrypcję raportu w celu dostarczenia raportu pocztą e-mail](#BKMK_ReportSubscriptionEmail) później w tym temacie.  

 Podczas tworzenia subskrypcji dostarczanej plików udziału musi określić istniejący folder jako folder docelowy. Serwer raportów nie tworzy folderów w systemie plików. Folder, w którym można określić muszą być dostępne za pośrednictwem połączenia sieciowego. Podczas określania folderu docelowego w subskrypcji należy użyć ścieżki UNC i bez końcowych ukośników odwrotnych w ścieżce folderu. Na przykład jest prawidłowa ścieżka UNC do folderu docelowego: \\ \\ &lt;servername\>\\reportfiles\\operacji\\2011.  

 Raporty mogą być renderowane w różnych formatach, takich jak MHTML czy programu Excel. Aby zapisać raport w określonym formacie pliku, należy wybrać ten format renderowania podczas tworzenia subskrypcji. Na przykład wybranie opcji Excel zapisuje raport w formacie programu Microsoft Excel. Chociaż możesz użyć dowolnego z obsługiwanych formatów renderowania, niektóre formaty działają lepiej od innych podczas renderowania do pliku.  

 Poniższa procedura umożliwia utworzenie subskrypcji raportu w celu dostarczania raportu do udziału plików.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-to-a-file-share"></a>Aby utworzyć subskrypcję raportu w celu dostarczania raportu do udziału plików  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów. Możesz wybrać folder raportów, aby wyświetlić tylko raporty, które są skojarzone z folderem.  

3.  Wybierz raport, który chcesz dodać do subskrypcji, a następnie na **Home** w karcie **grupy raportowania** , kliknij przycisk **Utwórz subskrypcję** otworzyć **Kreatora tworzenia subskrypcji**.  

4.  Na **dostarczanie subskrypcji** skonfiguruj następujące ustawienia:  

    -   Raport dostarczony przez: Wybierz **udostępnianie plików systemu Windows** aby dostarczyć raport do udziału plików.  

    -   **Nazwa pliku**: Określ nazwę pliku raportu. Domyślnie plik raportu nie ma rozszerzenie nazwy pliku. Wybierz **Dodaj rozszerzenie pliku po utworzeniu** automatycznie dodać rozszerzenie nazwy pliku do tego raportu na podstawie formatu renderowania.  

    -   **Ścieżka**: Określ ścieżkę UNC do istniejącego folderu, w którym mają zostać dostarczone w tym raporcie \(na przykład \\ \\ &lt;nazwa serwera\>\\&lt;udziału serwera\>\\&lt;folder raportów\>\).  

        > [!NOTE]  
        >  Nazwa użytkownika określona dalej na tej stronie musi mieć dostęp do tego udziału serwera oraz uprawnienie zapisu do folderu docelowego.  

    -   **Format renderowania**: Wybierz jeden z następujących formatów dla pliku raportu:  

        -   **Plik XML z danymi raportu**: Raport jest zapisywany w formacie Extensible Markup Language.  

        -   **CSV \(rozdzielany przecinkami\)**: Raport jest zapisywany w przecinkami\-rozdzielone\-format wartości.  

        -   **Plik TIFF**: Raport jest zapisywany w formacie Tagged Image File Format.  

        -   **Acrobat \(PDF\) pliku**: Raport jest zapisywany w formacie Acrobat Portable Document Format.  

        -   **HTML 4.0**: Raport jest zapisywany jako strona sieci Web można wyświetlać tylko w przeglądarkach obsługujących język HTML 4.0. Internet Explorer 5 i nowsze wersje obsługuje język HTML 4.0.  

            > [!NOTE]  
            >  Jeśli w raporcie znajdują się obrazy, format HTML 4.0 nie dołącza ich w pliku.  

        -   **MHTML \(archiwum sieci web\)**: Raport jest zapisywany w formacie MIME HTML \(mhtml\), który jest możliwy do wyświetlenia w wielu przeglądarkach sieci web.  

        -   **Moduł renderowania RPL**: Raport jest zapisywany w układ strony raportu \(RPL\) format.  

        -   **Excel**: Raport jest zapisywany jako arkusz kalkulacyjny programu Microsoft Excel.  

        -   **Word**: Raport jest zapisywany jako dokument programu Microsoft Word.  

    -   **Nazwa użytkownika**: Określ konto użytkownika systemu Windows z uprawnieniami dostępu do folderu i udziału na serwerze docelowym. Konto użytkownika musi mieć dostęp do tego udziału serwera oraz uprawnienie zapisu do folderu docelowego.  

    -   **Hasło**: Określ hasło do konta użytkownika systemu Windows. W **Potwierdź hasło**, re\-wprowadź hasło.  

    -   Wybierz jedną z poniższych opcji, aby skonfigurować działanie podejmowane, gdy w folderze docelowym istnieje plik o tej samej nazwie:  

        -   **Zastąp istniejący plik nowszą wersją**: Określa, że jeśli plik raportu już istnieje, zostanie zastąpiony nową wersją go.  

        -   **Nie zastępuj istniejącego pliku**: Określa, jeśli plik raportu już istnieje, nie zostanie żadnej akcji.  

        -   **Zwiększaj przyrostowo nazwy plików w miarę dodawania nowszych wersji**: Określa, jeśli plik raportu już istnieje, jest dodawany numer nowego raportu do nazwy pliku odróżniający go od innych wersji.  

    -   **Opis**: Określa opis subskrypcji raportów.  

     Kliknij przycisk **Dalej**.  

5.  Na **harmonogram subskrypcji** wybierz jedną z następujących opcji harmonogramu dostaw dla subskrypcji raportów:  

    -   **Użyj harmonogramu udostępnionego**: Udostępniony harmonogram to uprzednio zdefiniowany harmonogram, które mogą być używane przez inne Subskrypcje raportów. Zaznacz to pole wyboru, a następnie wybierz harmonogram udostępniony na liście, jeśli dowolny zostały określone.  

    -   **Utwórz nowy harmonogram**: Skonfiguruj harmonogram, na którym uruchamiania tego raportu, w tym interwał, czas i datę rozpoczęcia oraz datę zakończenia subskrypcji.  

6.  Na **parametry subskrypcji** Określ parametry tego raportu, które są używane podczas nienadzorowanego uruchamiania. Jeśli nie ma żadnych parametrów raportu, ta strona nie jest wyświetlana.  

7.  Na **Podsumowanie** Przejrzyj ustawienia subskrypcji raportów. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia subskrypcji raportu.  

8.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** . Sprawdź, czy subskrypcja raportów została pomyślnie utworzona. Można wyświetlać i modyfikować subskrypcji raportów w **subskrypcje** węzeł w węźle **raportowania** w **monitorowanie** obszaru roboczego.  

###  <a name="BKMK_ReportSubscriptionEmail"></a>Tworzenie subskrypcji raportu w celu dostarczenia raportu pocztą e-mail  
 Podczas tworzenia subskrypcji raportów w celu dostarczenia raportu pocztą e-mail wiadomość e-mail jest wysyłana do skonfigurowanych adresatów, a raport jest dołączony jako załącznik. Serwer raportów nie weryfikuje adresów e-mail lub uzyskać adresy e-mail z serwera e-mail. Wcześniej należy wiedzieć, których chcesz użyć adresów e-mail. Domyślnie można wysyłać pocztą e-mail raportów na dowolne prawidłowe konta e-mail w obrębie lub poza organizacją. Można wybrać jedną lub obie następujące opcje dostawy poczty e-mail:  

-   Wysłanie powiadomienia i hiperłącza do generowanego raportu.  

-   Wysłanie osadzonego lub dołączonego raportu. Format renderowania i docelowej przeglądarki określają jest osadzenie lub dołączenie raportu. Jeśli używana przeglądarka obsługuje język HTML 4.0 i MHTML i wybierz MHTML \(archiwum sieci web\) renderowania formatu, raport zostanie osadzony w wiadomości. Wszystkich pozostałych formatów renderowania \(CSV, PDF, Word, i tak dalej\) dostarczania raportów jako załączniki. Usługi raportowania nie sprawdzają rozmiaru załącznika ani wiadomości przed wysłaniem raportu. Jeśli załącznik lub wiadomość osiągnie maksymalny limit dozwolony przez serwer poczty, raport nie zostanie dostarczony.  

> [!IMPORTANT]  
>  Należy skonfigurować ustawienia poczty e-mail w usługach Reporting Services dla **E-mail** opcja dostarczania, które mają być dostępne. Aby uzyskać więcej informacji o konfigurowaniu ustawień poczty e-mail w usługach Reporting Services, zobacz [Konfigurowanie serwera raportów na potrzeby dostarczania poczty E-mail](http://go.microsoft.com/fwlink/p/?LinkId=226668) w SQL Server — książki Online.  

 Poniższa procedura umożliwia utworzenie subskrypcji raportu w celu dostarczenia raportu za pomocą poczty e-mail.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-by-email"></a>Aby utworzyć subskrypcję raportu w celu dostarczenia raportu pocztą e-mail  

-   W konsoli programu Configuration Manager kliknij **monitorowanie**.  

-   W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów. Możesz wybrać folder raportów wyświetlający tylko raporty, które są skojarzone z folderem.  

-   Wybierz raport, który chcesz dodać do subskrypcji, a następnie na **Home** w karcie **grupy raportowania** , kliknij przycisk **Utwórz subskrypcję** otworzyć **Kreatora tworzenia subskrypcji**.  

-   Na **dostarczanie subskrypcji** skonfiguruj następujące ustawienia:  

    -   **Raport dostarczony przez**: Wybierz **E\-poczty** aby dostarczyć raport jako załącznik wiadomości e-mail.  

    -   **To**: Określ prawidłowy adres e-mail do wysyłania tego raportu.  

        > [!NOTE]  
        >  Musisz wprowadzić wielu adresatów wiadomości e-mail, oddzielając każdy adres e-mail średnikiem.  

    -   **Cc**: Opcjonalnie określ adres e-mail kopia tego raportu.  

    -   **Bcc**: Opcjonalnie określ adres e-mail do wysyłania ukryta kopia tego raportu.  

    -   **Udzielenie odpowiedzi na**: Określ adres zwrotny do użycia w przypadku odbiorcy odpowiedzi na wiadomość e-mail.  

    -   **Temat**: Określ wiersz tematu wiadomości e-mail subskrypcji.  

    -   **Priorytet**: Wybierz flagę priorytetu dla tej wiadomości e-mail. Select **Low**, **Normal**, or **High**. Ustawienie priorytetu jest używane przez program Microsoft Exchange do ustawienia flagi informującej o ważności wiadomości e-mail.  

    -   **Komentarz**: Określ tekst, który ma zostać dodany do treści wiadomości e-mail subskrypcji.  

    -   **Opis**: Określ opis dla tej subskrypcji raportu.  

    -   **Dołącz łącze**: Zawiera adres URL subskrybowanego raportu w treści wiadomości e-mail.  

    -   **Dołącz raport**: Określ, czy raport jest dołączony do e\-wiadomości e-mail. Format, w którym raport jest dołączany jest określona w **Format renderowania** listy.  

    -   **Format renderowania**: Wybierz jeden z następujących formatów dla dołączanego raportu:  

        -   **Plik XML z danymi raportu**: Raport jest zapisywany w formacie Extensible Markup Language.  

        -   **CSV \(rozdzielany przecinkami\)**: Raport jest zapisywany w przecinkami\-rozdzielone\-format wartości.  

        -   **Plik TIFF**: Raport jest zapisywany w formacie Tagged Image File Format.  

        -   **Acrobat \(PDF\) pliku**: Raport jest zapisywany w formacie Acrobat Portable Document Format.  

        -   **MHTML \(archiwum sieci web\)**: Raport jest zapisywany w formacie MIME HTML \(mhtml\), który jest możliwy do wyświetlenia w wielu przeglądarkach sieci web.  

        -   **Excel**: Raport jest zapisywany jako arkusz kalkulacyjny programu Microsoft Excel.  

        -   **Word**: Raport jest zapisywany jako dokument programu Microsoft Word.  

-   Na **harmonogram subskrypcji** wybierz jedną z następujących opcji harmonogramu dostaw dla subskrypcji raportów:  

    -   **Użyj harmonogramu udostępnionego**: Udostępniony harmonogram to uprzednio zdefiniowany harmonogram, które mogą być używane przez inne Subskrypcje raportów. Zaznacz to pole wyboru, a następnie wybierz harmonogram udostępniony na liście, jeśli dowolny zostały określone.  

    -   **Utwórz nowy harmonogram**: Skonfiguruj harmonogram uruchamiania tego raportu, w tym interwał, godzinę rozpoczęcia i Data oraz datę zakończenia subskrypcji.  

-   Na **parametry subskrypcji** Określ parametry tego raportu, które są używane podczas nienadzorowanego uruchamiania. Jeśli nie ma żadnych parametrów raportu, ta strona nie jest wyświetlana.  

-   Na **Podsumowanie** Przejrzyj ustawienia subskrypcji raportów. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia subskrypcji raportu.  

-   Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** . Sprawdź, czy subskrypcja raportów została pomyślnie utworzona. Można wyświetlać i modyfikować subskrypcji raportów w **subskrypcje** węzeł w węźle **raportowania** w **monitorowanie** obszaru roboczego.  

