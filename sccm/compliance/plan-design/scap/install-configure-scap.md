---
title: Instalowanie i Konfigurowanie rozszerzeń Security Content Automation Protocol (SCAP)
titleSuffix: System Center Configuration Manager
description: Instalowanie i Konfigurowanie rozszerzeń Security Content Automation Protocol (SCAP)
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f53b484b-5123-48f0-be2f-4e30318f3d39
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 03fc9fa9f82aeae8ab22d6b4c3fa7858e93401cc
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="install-and-configure-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>Instalowanie i Konfigurowanie rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

> [!Tip]  
> Ta funkcja została wprowadzona w wersji zapoznawczej Technical Preview 1803 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Ta wersja wstępna rozszerzeń SCAP można zainstalować w żadnej wersji obecnie obsługiwane w bieżącej gałęzi programu Configuration Manager i LTSB 1606. Plik instalacji znajduje się w cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi począwszy od wersji technical preview 1803.   

Po przygotowaniu wstępnie wymaganej infrastruktury, możesz przystąpić do instalowania i konfigurowania rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager na komputerze, z którego chcesz uruchomić ten proces.

## <a name="install-scap-extensions-configuration-manager"></a>Instalowanie rozszerzeń SCAP programu Configuration Manager

1. Uruchom program ConfigMgr\_rozszerzenia\_dla\_SCAP.msi, aby zainstalować narzędzie.
2. W Eksploratorze Windows przejdź do folderu, do którego pobrano **ConfigMgr\_rozszerzenia\_dla\_SCAP.msi** pliku, a następnie kliknij dwukrotnie **ConfigMgr\_ Rozszerzenia\_dla\_SCAP.msi** pliku. Spowoduje to uruchomienie rozszerzeń SCAP dla Kreatora instalacji programu Microsoft System Center Configuration Manager.

Zakończenie **rozszerzeń SCAP dla Kreatora instalacji programu Microsoft System Center Configuration Manager** korzystając z informacji w poniższej tabeli, Kreator akceptowanie&#39;s domyślne wartości, chyba że konieczne jest ich określenie.

**Tabela 1.0** rozszerzeń SCAP dla programu Microsoft System Center procesu Kreatora instalacji programu Configuration Manager

| Nazwa strony kreatora | Akcja użytkownika |
| --- | --- |
| Zapraszamy i umowę licencyjną użytkownika oprogramowania |1. Przejrzyj umowę licencyjną|
| Zapraszamy i umowę licencyjną użytkownika oprogramowania|2. Kliknij przycisk **akceptuję warunki umowy licencyjnej**.|
| Zapraszamy i umowę licencyjną użytkownika oprogramowania|3. Kliknij pozycję **Zainstaluj**.|
| Ukończono rozszerzeń SCAP dla Kreatora instalacji programu Microsoft System Center Configuration Manager |4. Kliknij przycisk **Zakończ**.|
 



Rozszerzenia SCAP dla Kreatora instalacji programu Microsoft System Center Configuration Manager instaluje rozszerzenia domyślny folder instalacji konsoli programu Configuration Manager.



## <a name="download-and-install-the-scap-data-stream-files"></a>Pobierz i zainstaluj pliki strumieni danych SCAP

Przed uruchomieniem rozszerzenia SCAP w celu konwersji plików strumieni danych SCAP, a następnie zaimportować je do funkcji ustawień zgodności, należy pobrać plików strumieni danych SCAP z National Vulnerability Database (NVD) [stronępobierania](http://nvd.nist.gov/fdcc/download_fdcc.cfm)Witryny sieci Web. Następnie skopiuj je do folderu, w którym zainstalowano rozszerzenia SCAP

W zależności od środowiska mogą nie być potrzebne wszystkie pliki strumieni danych SCAP wymienione na stronie pobierania.

Aby zainstalować strumienie danych SCAP

1. Odwiedź stronę [witryny internetowej NVD](http://nvd.nist.gov/) do identyfikowania strumienie danych SCAP, które są wymagane przez Twoją organizację.
Strumienie danych SCAP publikowane przez Instytut NIST są podzielone na kilka pakietów, które są również nazywane _listy kontrolne_.

2. Pobierz strumienie danych SCAP z [witryny internetowej NVD](http://nvd.nist.gov/home.cfm), które są przechowywane w skompresowanych plikach z rozszerzeniem zip lub oznaczone jako plik DataStream XML.

    >[!IMPORTANT] 
    >Istnieje wiele plików strumieni danych SCAP z rozszerzeniem .xml, który można pobrać z witryny NVD. Jednak tylko pliki XML, które obejmują XCCDF (scap 1.0 i 1.1) / zawartość DataStream (scap 1.2) są odpowiednie do użytku z rozszerzeń SCAP.

3. Wyodrębnij SCAP danych strumieni plików/DataStream XML plik zip pobranego w tym samym folderze, w którym zainstalowano rozszerzenia SCAP.

## <a name="convert-and-import-the-scap-data-stream-files-using-the-import-scap-content-wizard"></a>Konwertowanie oraz importowanie plików strumieni danych SCAP przy użyciu Kreatora importu SCAP zawartości

Po otrzymaniu strumienie danych SCAP, możesz przystąpić do importowania i przekonwertować strumienie danych do linii bazowych konfiguracji. Strumienie danych SCAP publikowane przez Instytut NIST są podzielone na kilka pakietów. Wykonaj NIST&#39;s instrukcjami, aby określić, których pakietów do użycia w danym środowisku. Na przykład jest dostępny oddzielny pakiet dla każdej wersji systemu Windows, inny pakiet określonej wersji w konfiguracji zapory i pakiet dla programu Internet Explorer 8.0. Użyj poniższych procedur, by wykonać to zadanie.

### <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>Aby zaimportować strumienie danych SCAP do programu Configuration Manager

1. Na Wstążce linii bazowej konfiguracji, należy uruchomić Kreatora zawartości SCAP importu.

     ![Uruchom Kreatora zawartości SCAP importu z elementu konfiguracji linii bazowej wstążki](./media/import-scap-content.png)

2. Wybierz typ zawartości.

      ![Wybierz typ zawartości](./media/import-new-scap-content.png)

3. Wybierz plik datastream SCAP, XCCDF i CPE słownika lub Oval zawartości pliku.

     ![Wybierz plik datastream SCAP](./media/select-datastream-file.png)

4. Jeśli SCAP 1.2 Wybierz datastream. Następnie wybierz profil i testu porównawczego SCAP 1.x.  Wybierz **dalej** do konwersji zawartości. Będzie wyświetlany pasek postępu.

      ![Wybierz profil i testów porównawczych dla SCAP 1.2](./media/select-benchmark-and-profile.png)

5. Potwierdź dane konfiguracyjne do zaimportowania.

      ![Potwierdź zrzut ekranu konfiguracji](./media/confirm-configuration.png)

6. Kliknij przycisk**dalej** importowanie danych konfiguracji.

      ![Ukończenie importu](./media/complete-import.png)

## <a name="alternate-method-convert-and-import-the-scap-data-stream-files-using-the-cmd-line-tool"></a>(Metoda alternatywna) Konwertowanie oraz importowanie plików strumieni danych SCAP przy użyciu narzędzia wiersza polecenia

Po otrzymaniu strumienie danych SCAP, może użyć narzędzia Microsoft.Sces.ScapToDcm.exe, aby przekonwertować strumienie danych SCAP na pliki cab zgodne z funkcją ustawień zgodności. Następnie zaimportować pliki cab do programu Configuration Manager. Narzędzie Microsoft.Sces.ScapToDcm.exe konwertuje strumienie danych SCAP na elementy konfiguracji i linie bazowe konfiguracji, które uzyskują dostęp przy użyciu funkcji ustawień zgodności w programie Configuration Manager. Narzędzie Microsoft.Sces.ScapToDcm.exe konwertuje strumienie danych SCAP na Manifesty XML. Następnie pakiety Manifesty XML w pliku cab, który można zaimportować do programu Configuration Manager.

Strumienie danych SCAP publikowane przez Instytut NIST są podzielone na kilka pakietów. Wykonaj NIST&#39;s instrukcjami, aby określić, których pakietów do użycia w danym środowisku. Na przykład jest dostępny oddzielny pakiet dla każdej wersji systemu Windows, inny pakiet określonej wersji w konfiguracji zapory i pakiet dla programu Internet Explorer 8.0. Użyj poniższych procedur, by wykonać to zadanie.





## <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>Aby zaimportować strumienie danych SCAP do programu Configuration Manager

1. Konwertuj strumienie danych SCAP na plik cab zgodne z funkcją ustawień zgodności.
2. Zaimportuj plik cab do programu Configuration Manager.

### <a name="convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files"></a>Przekonwertować strumienie danych SCAP na pliki cab zgodne z funkcją ustawień zgodności

Aby można było analizować i oceniać zgodność systemów, należy przekonwertować strumienie danych SCAP w formacie XML na Manifesty XML, które są zgodne z ustawieniami zgodności elementów konfiguracji i linie bazowe konfiguracji. Narzędzie Microsoft.Sces.ScapToDcm.exe konwertuje strumienie danych SCAP na Manifesty XML. Następnie pakiety Manifesty XML w pliku cab, który można później zaimportować do programu Configuration Manager.

#### <a name="to-convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files-using-the-microsoftscesscaptodcmexe-tool"></a>**Aby przekonwertować strumienie danych SCAP na pliki cab zgodne z funkcją ustawień zgodności za pomocą narzędzia Microsoft.Sces.ScapToDcm.exe**

W wierszu polecenia przejdź do folderu AdminConsole\Bin, uruchom Microsoft.Sces.ScapToDcm.exe Aby wygenerować plik cab zgodny z ustawieniami zgodności i zaimportować go do lokacji programu Configuration Manager.

   >[!NOTE] 
   > Twoje konto musi mieć uprawnienia odczytu i zapisu do folderu wyjściowego

**Zawartość SCAP 1.0/1.1 (plik XCCDF XML, np. zawartość USGCB i DISA):**

 Microsoft.Sces.ScapToDcm.exe — xccdf &lt;xccdf.xml&gt; - cpe &lt;cpe.xml&gt; — limit &lt;outputFolder&gt; [-wybierz profilu testu porównawczego] [-dziennika plik_dziennika]

   >[!NOTE] 
   >Jeśli nie zrobisz&#39;t Określ profilu testu porównawczego za pomocą wybierz parametr, a następnie narzędzie wygeneruje plik cab DCM dla każdego testu porównawczego w pliku zawartości.

**Scap 1.2 zawartości-(plik DataStream XML, np. najnowsza zawartość usgcb):**

Microsoft.Sces.ScapToDcm.exe — scap &lt;scapdatastreamfile.xml&gt; -out &lt;outputFolder&gt; [— wybierz profil datastream] [-dziennika plik_dziennika]

   >[!NOTE] 
   > Jeśli nie zrobisz&#39;t Określ datastream/profilu testu porównawczego za pomocą parametru – select, a następnie, narzędzie wygeneruje plik cab DCM dla każdego testu porównawczego w pliku zawartości.

**Pojedynczy plik OVAL ze zmiennymi zewnętrznymi:**

Microsoft.Sces.ScapToDcm.exe — oval &lt;singleOvalFile.xml&gt; [-zmienna &lt;externalVariableFile.xml&gt;]-limit &lt;outputFolder&gt; [-dziennika plik_dziennika]

   >[!NOTE] 
   > Jeśli istnieje wiele wartości dla jednej zmiennej w pliku zmiennych zewnętrznych, narzędzie Microsoft.Sces.ScapToDcm.exe będzie traktować te wartości jako tablicę dla tej zmiennej.



#### <a name="microsoftscesscaptodcmexe-command-line-parameters"></a>Microsoft.Sces.ScapToDcm.exe. Parametry wiersza polecenia

| **Parametr** | **Użycie** | **Wymagane** |
| --- | --- | --- |
| -scap [plik strumienia danych scap] | Określ plik strumienia danych SCAP | Tak (dla strumienia danych SCAP 1.2, wzajemnie wyklucza się z parametrami-xccdf oraz -oval i - variable) |
| -xccdf [plik xccdf] | Określ plik XCCDF | Tak (dla protokołu SCAP 1.0/1.1 XCCDF, wzajemnie wyklucza się z — scap oraz -oval i - variable) |
| -cpe [plik cpe] | Określ plik CPE | Tak (dla protokołu SCAP 1.0/1.1 XCCDF, wzajemnie wyklucza się z — scap oraz -oval i - variable) |
| -oval [plik oval] | Określ plik OVAL | Tak (w przypadku autonomicznego pliku OVAL, wzajemnie wyklucza się z parametrami-xccdf i - scap) |
| -zmienna [plik zmiennych zewnętrznych oval] | Określ plik zmiennych zewnętrznych OVAL | Nie (opcjonalny w przypadku autonomicznego pliku OVAL po zewnętrzny plik zmiennych OVAL, wzajemnie wyklucza się z parametrami-xccdf i - scap) |
| -Wybierz [profilu testu porównawczego xccdf] | Wybierz testu porównawczego XCCDF, profil ze strumienia danych SCAP lub pliku XCCDF | Nie (zalecamy określenie tego przełącznika. Jeśli nie zostanie określony, narzędzie zostanie wygenerowany plik cab dla wszystkich profilów w wszystkich osadzonych testach porównawczych strumienia) |
| -out [katalog wyjściowy] | Określ, gdzie ma zostać zapisany plik cab DCM | Nie (Jeśli nie jest określony, narzędzie jedynie wyświetli listę zawartości bez użycia konwersji, a następnie) |
| -log [plik dziennika] | Określ plik dziennika | Nie (Jeśli nie jest określony, a następnie dziennik jest zapisywany do pliku Microsoft.Sces.ScapToDcm.log) |
| -Pomoc i -? | Wyświetl składnię narzędzia | Nie |





#### <a name="the-following-command-lines-are-samples-for-the-microsoftscesscaptodcmexe-tool"></a>Poniższe wiersze poleceń są przykłady dla narzędzia Microsoft.Sces.ScapToDcm.exe:

**Zawartość scap 1.2:**

  Scap — scap Microsoft.Sces.ScapToDcm.exe\_gov.nist\_USTCB ie8.xml — limit. \mytestfolder — wybierz mySCAPDataStreamID/myBenchMarkID/myProfileID

**Zawartość SCAP1.0/1.1:**

   Microsoft.Sces.ScapToDcm.exe–xccdf scap\_gov.nist\_Test-WinXP\_xccdf.xml –cpe scap\_gov.nist\_Test-WinXP\_cpe.xml –out .\mytestfolder –select XCCDFBenchmarkID/MyProfileID

**Zawartość OVAL SCAP:**

  Microsoft.Sces.ScapToDcm.exe –oval myOvalFile.xml –variable myOvalExternalVariableFile.xml –out .\mytestfolder

**Następujące dane wyjściowe są przykładowe narzędzie Microsoft.Sces.ScapToDcm.exe:**

  Utworzony plik plik cab zgodny ustawień zgodności:

  Sprawdzanie poprawności schematu plik strumienia danych SCAP C:\24SCAP\BVT\_testu\_danych\_Stream.xml

  Pomyślnie sprawdzanie poprawności schematu plik strumienia danych SCAP C:\24SCAP\BVT\_testu\_danych\_Stream.xml

  Proces testu porównawczego XCCDF xccdf\_tst.bvt\_testu porównawczego\_Windows-F

  Proces profilu XCCDF: xccdf\_tst.bvt\_profilu\_wersji\_1.0.0.0-BVT profil #1

  Proces OVAL: scap\_tst.bvt\_kompozycji\_Windows-F-oval.xml

  Pomyślnie zakończono proces OVAL: scap\_tst.bvt\_kompozycji\_Windows-F-oval.xml

  Proces OVAL: scap\_tst.bvt\_kompozycji\_Windows-F-cpe-oval.xml

  Pomyślnie zakończono proces OVAL: scap\_tst.bvt\_kompozycji\_strumienia danych SCAP procesu systemu Windows-F-cpe-oval.xml: scap\_tst.bvt\_datastream\_danych SCAP F.zip systemu Windows Strumień: [scap\_tst.bvt\_datastream\_F.zip systemu Windows]

  Wersja: [1.2]

  Sygnatura czasowa: [2/24/2012]

  Przypadek użycia: [Konfiguracja]

  Słownik CPE: [scap\_tst.bvt\_kompozycji\_Windows-F-cpe-dictionary.xml]

  OVAL: Nazwa produktu [Windows-F-cpe-oval.xml]: [National Institute of Standards and Technology]

  Wersja produktu:]

  Wersja schematu: [5.3]

  Sygnatura czasowa: [2/24/2012]

  XCCDF Benchmark: [xccdf\_tst.bvt\_benchmark\_Windows-F]

  Wersji: Aktualizacja [v1.0.0.0]: [http://usgcb.nist.gov]

  Sygnatura czasowa: [2/24/2012]

  Stan: [zaakceptowane]

  Data stanu: [2/24/2012]

  Nazwa: [Niestety nowe BVT SCAP 1.2]

 Opis: [Opisu]

  Profil XCCDF: [xccdf\_tst.bvt\_profilu\_wersji\_1.0.0.0]
 
  OVAL:              [Windows-F-oval.xml]

   Nazwa produktu: [scaptool]

   Wersja produktu:]

   Wersja schematu: [5.4]

   Sygnatura czasowa: [2/24/2012]

  Rozpocznij SCAP do konwersji DCM...

  Przetwarzanie strumienia danych SCAP: scap\_tst.bvt\_datastream\_F.zip systemu Windows

  Przetwarzanie słownika CPE: scap\_tst.bvt\_kompozycji\_Windows-F-cpe-dictionary.xml

  …

  Generowanie pliku cab elementu konfiguracji linii bazowej: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  Pomyślnie wygenerowano plik cab elementu konfiguracji linii bazowej: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  Pomyślnie przekonwertowany profilu XCCDF: xccdf\_tst.bvt\_profilu\_wersji\_1.0.0.0 do xccdf linii bazowej DCM\_tst.bvt\_testu porównawczego\_Windows-F [xccdf \_tst.bvt\_profilu\_wersji\_1.0.0.0].cab

## <a name="next-step"></a>Następny krok
> [!div class="nextstepaction"]
> [Importowanie ustawień zgodności SCAP i eksportowanie wyników sprawdzania zgodności](/sccm/compliance/plan-design/scap/import-scap-compliance-settings)
