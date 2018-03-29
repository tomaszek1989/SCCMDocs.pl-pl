---
title: Importowanie ustawień zgodności SCAP
titleSuffix: System Center Configuration Manager
description: Importowanie ustawień zgodności SCAP jako linie bazowe konfiguracji i eksportowanie wyników
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bdcb018-bac2-4540-b786-6242bac73ff4
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 5863f8b9a79e8e22e215e9feac7744b4a6ce279d
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="import-the-compliance-settings-compliant-cab-files-into-system-center-configuration-manager"></a>Zaimportuj pliki cab zgodne z funkcją ustawień zgodności do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

> [!Tip]  
> Ta funkcja została wprowadzona w wersji zapoznawczej Technical Preview 1803 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Ta wersja wstępna rozszerzeń SCAP można zainstalować w żadnej wersji obecnie obsługiwane w bieżącej gałęzi programu Configuration Manager i LTSB 1606. Plik instalacji znajduje się w cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi począwszy od wersji technical preview 1803. 

Następnym krokiem w procesie jest użycie konsoli programu Configuration Manager w celu zaimportowania zgodności zgodnych z funkcją ustawień plików cab do programu Configuration Manager. Po zaimportowaniu plików cab utworzonego wcześniej w tym procesie, elementy konfiguracji i linii bazowych konfiguracji są tworzone w bazie danych programu Configuration Manager. W dalszej części procesu można przypisać każdej linii bazowych konfiguracji do kolekcji komputerów w programie Configuration Manager.

## <a name="to-import-the-compliance-settings-compliant-cab-files-into-configuration-manager"></a>Aby zaimportować pliki cab zgodne z funkcją ustawień zgodności do programu Configuration Manager

1. Otwórz **konsoli programu Configuration Manager**.
2. W ** konsoli programu Configuration Manager, w okienku nawigacji przejdź do **zasoby i zgodność**> **ustawień zgodności** > **linii bazowych konfiguracji** .

3. W okienku Akcje kliknij polecenie **Importuj dane konfiguracji** można uruchomić Kreatora importu danych konfiguracyjnych.

1. Zakończenie **Kreatora importu danych konfiguracyjnych** korzystając z informacji w poniższej tabeli i akceptując wartości domyślne, chyba że określono inaczej.



Proces kreatora danych konfiguracji importu

| Nazwa strony kreatora | Akcja użytkownika |
| --- | --- |
| **Wybierz pliki** |1. Kliknij pozycję **Dodaj**. </br>Zostanie wyświetlone okno dialogowe Otwieranie.|
||2. W **Otwórz** okno dialogowe, przejdź do **&lt;wyjściowy plik cab zgodny\_folderu &gt;**. Kliknij przycisk  **&lt; zgodne\_pliku cab&gt;**plik .cab, gdzie cab _compliant **dane wyjściowe\_folderu** jest folder, w którym określono następujące Przełącznik dane wyjściowe po uruchomieniu narzędzia Sces.ScapToDcm.exe. **zgodne\_pliku** to nazwa pliku cab utworzonego wcześniej w procesie. Następnie kliknij przycisk **Otwórz**. </br> Konsola programu Configuration Manager — zostanie wyświetlone okno dialogowe Ostrzeżenie o zabezpieczeniach.|
||3. W **konsoli programu Configuration Manager — ostrzeżenie o zabezpieczeniach** okno dialogowe, kliknij przycisk **Uruchom**. Na stronie Wybieranie plików dane konfiguracji zostaną wyświetlone na liście linii bazowych do zaimportowania.|
||3. Kliknij przycisk **Dalej**.|
| **Podsumowanie** |5. Kliknij przycisk **Dalej**. |
| **Kończenie pracy Kreatora importu danych konfiguracyjnych** |6. Kliknij przycisk **Zamknij**. |

Nowa linia bazowa konfiguracji zostanie wyświetlony w okienku informacji konsoli programu Configuration Manager.

>[!IMPORTANT]
> Należy powtórzyć ten proces dla każdego pliku cab utworzonego wcześniej w procesie. Istnieje plik cab dla każdego selectedprofile w pliku XCCDF/DataStreamXML, który został pobrany z witryny internetowej NVD, który możesz przetworzyć, uruchamiając narzędzie Microsoft.Sces.ScapToDcm.exe.

Zaimportowana linia bazowa konfiguracji jest tylko do odczytu i ma stan &#39;włączone&#39; i początkowy stan wdrożenia &#39;nr&#39;.  &#39;Data modyfikacji&#39; właściwość wskazuje czas importu linii bazowej.  Nazwa linii bazowej konfiguracji jest pobierana z sekcji nazwy wyświetlanej pliku XML XCCDF/Datastream. Nazwa jest tworzony przy użyciu następującej konwencji:

ABC [XYZ], gdzie ABC jest identyfikator testu porównawczego XCCDF, a XYZ jest identyfikator profilu XCCDF (Jeśli wybrano profil).



## <a name="assign-configuration-baselines-to-the-computer-collections"></a>Przypisywanie linii bazowych konfiguracji do kolekcji komputerów

Po utworzeniu odpowiednich kolekcji komputerów dla komputerów, które chcesz ocenić zgodność SCAP, możesz przypisać linie bazowe konfiguracji, które zaimportowane do skojarzenia z kolekcji komputerów. Ta sekcja zawiera informacje umożliwiające przypisanie linii bazowej konfiguracji do kolekcji komputerów przy użyciu konsoli programu Configuration Manager.

Aby przypisać linię bazową konfiguracji do kolekcji komputerów:

1. Otwórz **programu Configuration Manager****konsoli**.  

2. W **konsoli programu Configuration Manager, w okienku nawigacji przejdź do **zasoby i zgodność** > **ustawień zgodności**  >**  Linie bazowe konfiguracji **.
3. W okienku nawigacji kliknij &lt; ** konfiguracji\_linii bazowej >, gdzie &lt; _konfiguracji\_linii bazowej&gt;_  jest nazwą linii bazowej konfiguracji które Czy chcesz przypisać do kolekcji komputerów.

    Na liście elementów konfiguracji dla linii bazowej konfiguracji zostaną wyświetlone w okienku informacji programu Configuration Manager.

4. W okienku Akcje kliknij polecenie **Wdróż**.

5. Zakończenie **Wdróż****linii bazowej konfiguracji****okna dialogowego** korzystając z informacji w poniższej tabeli i akceptując wartości domyślne, chyba że określono inaczej.    

### <a name="deploy-configuration-baseline-dialog-process"></a>Wdrażanie proces okna dialogowego linii bazowej konfiguracji

| Nazwa strony kreatora | Akcja użytkownika |
| --- | --- |
| **Wybierz kolekcję** | 1. Kliknij przycisk **Przeglądaj**.|
||2. W **Wybieranie kolekcji** okno dialogowe, wybierz **kolekcje urządzeń**. Następnie kliknij przycisk  **&lt;komputera\_kolekcji&gt;**, gdzie &lt; _komputera\_kolekcji&gt;_  jest nazwą kolekcji komputerów, który został utworzony wcześniej w procesie. Kliknij przycisk **OK**.|
| **Ustaw harmonogram** |3. Wybierz harmonogram, który jest odpowiedni dla Twojej organizacji.|
 
>[!IMPORTANT]
> Powtórz ten proces dla każdej kolekcji komputerów, które chcesz przypisać do każdej linii bazowej konfiguracji. Co najmniej każdej linii bazowej konfiguracji należy przypisać co najmniej jednej kolekcji komputerów.

## <a name="verify-that-the-compliance-data-has-been-collected"></a>Sprawdź, czy zebrano dane zgodności

Przed wyeksportowaniem danych zgodności do formatu SCAP, musisz potwierdzić, że dane zostały zebrane. Po przypisaniu linii bazowej konfiguracji do kolekcji komputerów, klient programu Configuration Manager na każdym komputerze w kolekcji automatycznie zbiera informacje o zgodności. Następnie informacje o zgodności są przechowywane w bazie danych programu Configuration Manager.

Możesz wyświetlić stan wdrożenia linii bazowej konfiguracji w programie Configuration Manager w celu zapewnienia, że odpowiednie dane zostały zebrane przez klientów programu Configuration Manager. Jest ważne, aby sprawdzić, czy zgodności odpowiednie dane zostały zebrane w programie Configuration Manager, ponieważ może pomóc podczas weryfikowania plików z wynikami XCCDF/DataStream tworzonych w dalszej części procesu.



### <a name="verify-that-the-compliance-data-has-been-collected"></a>Sprawdź, czy zebrano dane zgodności

1. Otwórz konsolę programu Configuration Manager.
2. W konsoli programu Configuration Manager, w okienku nawigacji przejdź do **monitorowanie** > **wdrożeń**.
3. Kliknij przycisk **typu funkcji** sortować typu wdrożenia i Znajdź elementy mające typ **linii bazowej** na liście.
4. Kliknij prawym przyciskiem myszy &lt;konfiguracji\_linii bazowej&gt; na liście, którą właśnie wdrożono do kolekcji, a następnie kliknij przycisk **Wyświetl stan**.
5. Następnie można przejść do &lt;konfiguracji\_linii bazowej&gt; węzeł, aby wyświetlić stan zgodności, jeśli jest to kolekcja danych zgodności maszyny w nieznanym stanie nadal nie działa dla tego komputera.

### <a name="validate-the-xccdfdatastream-results"></a>Zweryfikuj wyniki XCCDF/Datastream

1. Otwórz konsolę programu Configuration Manager.
2. W konsoli programu Configuration Manager, w okienku nawigacji przejdź do **ustawień zgodności** > **pulpitu nawigacyjnego SCAP**.
3. Wybierz linię bazową konfiguracji, przypisania, plik SCAP Datastream, testu porównawczego i profilu (jeśli dotyczy).
4. Kliknij przycisk **Pokaż raport**
 ![raport SCAP](./media/scap-report.png)



## <a name="export-compliance-results-to-scap-format"></a>Eksportowanie wyników sprawdzania zgodności do formatu SCAP

Następne zadanie w procesie jest eksportować dane zgodności ustawień zgodności do formatu SCAP, czyli pliku ARFreport w formacie XML/zrozumiałą dla użytkownika. Kreator eksportu rozszerzeń SCAP i narzędzie Microsoft.Sces.DcmToScap.exe wyeksportować oddzielny plik wyników XCCDF/DataStreamARF dla każdej linii bazowej konfiguracji ustawień zgodności. Te pliki odpowiadają każdego pliku wejściowego XCCDF/DataStream, który używa narzędzia Microsoft.Sces.ScapToDcm.exe do tworzenia każdej linii bazowej konfiguracji ustawień zgodności.

### <a name="export-the-compliance-settings-compliance-data-using-the-export-scap-report-wizard"></a>Eksportuj dane zgodności ustawień zgodności za pomocą Kreatora eksportu raport SCAP

1. Uruchom Kreatora eksportowania raportów SCAP z menu kliknij prawym przyciskiem myszy na pulpicie nawigacyjnym SCAP.
![Importuj z pulpitu nawigacyjnego SCAP](./media/import-from-scap-dashboard.png)

2. Wybierz linię bazową konfiguracji i przypisanie ![wybierz linię bazową](./media/select-ci-baseline.png)

3. Wybierz lokalizację pliku datastream SCAP, plik XCCDF/CPE lub Oval pliki zawartości i zmiennej.
![Wybierz datastream](./media/export-scap-report-datastream.png)

4. Określ nazwę organizacji i wybierz lokalizację folderu, aby wyeksportować raport SCAP.
 ![Wybierz datastream](./media/specify-org-export.png)

5. Potwierdź ustawienia.
 ![Wybierz datastream](./media/confirm-export.png)

6. Wybierz ** obok eksportu raportu.  Pojawi się pasek postępu, a następnie stronę ukończenia.
 ![Zakończyć eksportowania](./media/complete-report-export.png)



### <a name="alternate-method-export-the-compliance-settings-compliance-data-using-the-microsoftscesdcmtoscapexe-tool"></a>(Metoda alternatywna) Eksportuj dane zgodności ustawień zgodności za pomocą narzędzia Microsoft.Sces.DcmToScap.exe

1. W wierszu polecenia przejdź do typu folderu AdminConsole\Bin parametry wiersza polecenia wymienione w poniższej tabeli, a następnie naciśnij klawisz ** ENTER:

    >[!NOTE] 
    >Twoje konto musi mieć uprawnienia do odczytu dla dostawcy programu Configuration Manager, a także uprawnienia do zapisu do folderu wyjściowego określono w out parametru wiersza polecenia.

**Zawartość SCAP 1.0/1.1 (np. zawartość USGCB i DISA):**

Microsoft.Sces.DcmToScap.exe — linii bazowej BaselineCIID — przypisanie AssignmentID — xccdf &lt;xccdf.xml&gt; - cpe &lt;cpe.xml&gt; — wybierz &lt;xccdfBenchmark profil&gt; -out &lt;outputResultFolder&gt; [-dziennika plik_dziennika]

  >[!NOTE] 
    >Należy używać wybierz parametr, aby określić profil, który został oceniony na klientach, jeśli istnieje wiele profilu testu porównawczego w zawartości.

**Zawartość scap 1.2 (np. najnowsza zawartość USGCB):**

Microsoft.Sces.DcmToScap.exe-linii bazowej BaselineCIID — przypisanie AssignmentID — wybierz &lt;datastream xccdfBenchmark/profil&gt; — limit &lt;outputResultFolder&gt; [-dziennika plik_dziennika]

   >[!NOTE] 
   >Należy używać — wybierz parametr do określenia datastream profil, który został oceniony na klientach, jeśli istnieje wiele datastream/profilu testu porównawczego w zawartości.

**Pojedynczy plik OVAL ze zmiennymi zewnętrznymi:**

Microsoft.Sces.DcmToScap.exe-linii bazowej BaselineCIID — przypisanie AssignmentID — oval &lt;singleOvalFile.xml&gt; [-zmiennej &lt;externalVariableFile.xml&gt;]-out &lt;outputResultFolder &gt; [-dziennika plik_dziennika]

   >[!NOTE] 
    >Microsoft.Sces.DcmToScap.exe _will generować tylko raport wyników definicji OVAL dla każdego komputera docelowego, raport ARF nie zostanie wygenerowany.

#### <a name="how-to-get-baseline-ci-id-and-assignment-id"></a>Jak uzyskać identyfikator elementu konfiguracji linii bazowej i identyfikator przypisania

W konsoli administracyjnej, przejdź do **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**. Identyfikator elementu konfiguracji jest identyfikator elementu konfiguracji linii bazowej konfiguracji.

![Pobierz identyfikator i identyfikator przypisania CI](./media/get-to-baselines.png)

Wybierz odpowiednią linię bazową konfiguracji, kliknij kartę wdrożenia, jeśli identyfikator przypisania nie jest wyświetlana, kliknij prawym przyciskiem myszy nagłówek kolumny, kliknij Identyfikatora przypisania, aby je włączyć.
![Pobierz identyfikator i identyfikator przypisania CI](./media/get-to-baselines.png)


#### <a name="microsoftscesdcmtoscapexe-command-line-parameters"></a>Parametry wiersza polecenia Microsoft.Sces.DcmToScap.exe

| **Parametr** | **Użycie** | **Wymagane** |
| --- | --- | --- |
| -baseline [Baseline CI ID] | Określenie linii bazowej konfiguracji | Tak |
| -przypisania [identyfikator przypisania] | Określ wdrożenia linii bazowej konfiguracji | Tak |
| -organization [nazwa organizacji] | Określ nazwę organizacji, która będzie wyświetlana w raporcie. Mogą być oddzielone znakami &#39;; &#39; Aby określić nazwę organizacji w wielu wierszach. | Nie |
| — Typ [elastycznej/pełnej/fullnosc] | Określ typ wyniku OVAL: wynik uproszczony, wynik, lub wynik pełny lub wynik pełny bez charakterystyki systemu. | Nie (Jeśli nie jest określony, wartością domyślną jest pełna) |
| -scap [plik strumienia danych scap] | Określ plik strumienia danych SCAP | Tak (dla strumienia danych SCAP 1.2, wzajemnie wyklucza się z parametrami-xccdf oraz -oval i - variable) |
| -xccdf [plik xccdf] | Określ plik XCCDF | Tak (dla protokołu SCAP 1.0/1.1 XCCDF, wzajemnie wyklucza się z — scap oraz -oval i - variable) |
| -cpe [plik cpe] | Określ plik CPE | Tak (dla protokołu SCAP 1.0/1.1 XCCDF, wzajemnie wyklucza się z — scap oraz -oval i - variable) |
| -oval [plik oval] | Określ plik OVAL | Tak (w przypadku autonomicznego pliku OVAL, wzajemnie wyklucza się z parametrami-xccdf i - scap) |
| -zmienna [plik zmiennych zewnętrznych oval] | Określ plik zmiennych zewnętrznych OVAL | Nie (opcjonalny w przypadku autonomicznego pliku OVAL po zewnętrzny plik zmiennych OVAL, wzajemnie wyklucza się z parametrami-xccdf i - scap) |
| -Wybierz [profilu testu porównawczego xccdf] | Wybierz testu porównawczego XCCDF, profil ze strumienia danych SCAP lub pliku XCCDF | Tak (wybór jest konieczny do wygenerowania raportu, dzięki czemu można dopasować odpowiednią linię bazową DCM w bazie danych programu Configuration Manager |
| -out [katalog wyjściowy] | Określ, gdzie ma zostać zapisany plik cab funkcji ustawień zgodności | Nie (Jeśli nie zostanie określony, następnie narzędzie jedynie wyświetli zawartość bez użycia konwersji) |
| -log [plik dziennika] | Określ plik dziennika | Nie (Jeśli nie jest określony, a następnie dziennik jest zapisywany do pliku Microsoft.Sces.DcmToScap.log) |
| -Pomoc i -? | Wyświetl składnię narzędzia | Nie |



 >[!TIP] 
 >Można określić? – h, lub – help Aby wyświetlić składnię narzędzia Microsoft.Sces.DcmToScap.exe oraz listę parametrów.

Domyślnie narzędzie Microsoft.Sces.DcmToScap.exe uzyskuje dostęp do bazy danych programu Configuration Manager przy użyciu poświadczeń. Narzędzie Microsoft.Sces.DcmToScap.exe wymaga co najmniej dostęp do odczytu do bazy danych programu Configuration Manager.

Po zweryfikowaniu, że odpowiednie **ARF** raportu: _ARF\_xxxx.xml_ i/lub **czytelny dla człowieka** raportu: xxx.txt, **Cyberscope** raportu: LASR\_xxx.xml, **ConsumedOval** raportu: xx-oval -&lt;machineName&gt;.xml, **wynik testu porównawczego XCCDF** raportu: xccdf\_xxx.xml pliki istnieją , w wierszu polecenia wpisz polecenie exit, a następnie naciśnij klawisz **ENTER** aby zamknąć wiersz polecenia.

## <a name="next-step"></a>Następny krok
> [!div class="nextstepaction"]
> [Rozwiązywanie problemów](/sccm/compliance/plan-design/scap/troubleshooting-scap)
