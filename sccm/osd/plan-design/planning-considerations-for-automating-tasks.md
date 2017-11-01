---
title: "Uwagi dotyczące planowania automatyzacji zadań"
titleSuffix: Configuration Manager
description: "Planowanie przed automatyzacji zadań w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc497a8a-3c54-4529-8403-6f6171a21c64
caps.latest.revision: "13"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: cfd3e33006f05b4270266b3c8b316764d29cdb0d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="planning-considerations-for-automating-tasks-in-system-center-configuration-manager"></a>Zagadnienia związane z planowaniem automatyzacji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można tworzyć sekwencje zadań do automatyzacji zadań w środowisku programu System Center Configuration Manager. Są wśród nich zadania tak różnorodne, jak przechwytywanie systemu operacyjnego na komputerze odniesienia czy wdrażanie systemu operacyjnego na jednym lub wielu komputerach docelowych. Działania sekwencji zadań definiuje się w poszczególnych krokach sekwencji. Kiedy sekwencja zadań jest uruchamiana, działania każdego jej kroku są wykonywane na poziomie wiersza polecenia w kontekście systemu lokalnego i nie wymagają interwencji użytkownika. Poniższe sekcje umożliwiają ułatwiające planowanie automatyzacji zadań w programie Configuration Manager.

##  <a name="BKMK_TSStepsActions"></a>Kroki sekwencji zadań i akcji  
 Kroki to podstawowe składniki sekwencji zadań. Mogą one zawierać polecenia pozwalające konfigurować i przechwytywać system operacyjny komputera odniesienia lub mogą one zawierać polecenia instalujące system operacyjny, sterowniki, klienta programu Configuration Manager i oprogramowania na komputerze docelowym. Polecenia kroku sekwencji zadań definiuje się w działaniach tego kroku. Istnieją dwa rodzaje działań. Działanie definiowane za pomocą ciągu wiersza polecenia nazywa się akcją niestandardową. Działanie wstępnie zdefiniowane przez program Configuration Manager nazywa się akcją wbudowaną. Sekwencja zadań może wykonywać dowolne kombinacje akcji niestandardowych i wbudowanych.  

 Kroki sekwencji zadań mogą również obejmować warunki kontrolujące kroku zachowania, takie jak zatrzymanie sekwencji zadań lub kontynuować sekwencję zadań, jeśli wystąpi błąd. Warunki dodaje się do kroku przez włączenie do niego zmiennej sekwencji zadań. Za pomocą zmiennej **SMSTSLastActionRetCode** możesz na przykład testować warunek poprzedniego kroku. Zmienne można dodawać do pojedynczego kroku lub grupy kroków.  

 Kroki sekwencji zadań są przetwarzane sekwencyjnie, co obejmuje akcję samego kroku oraz wszelkie warunki, które są przypisane do tego kroku. Po uruchomieniu programu Configuration Manager przetwarzać krok sekwencji zadań, następnym krokiem nie jest uruchomiona, dopiero po ukończeniu poprzedniej akcji. Sekwencja zadań jest traktowany jako pełny, kiedy wszystkie jej kroki zostały ukończone lub kiedy programu Configuration Manager przerwał uruchamianie sekwencji zadań przed ukończeniem wszystkich jej kroków powoduje, że krok zakończony niepowodzeniem. Na przykład jeśli krok sekwencji zadań nie może zlokalizować obrazu w odwołaniu lub pakietu w punkcie dystrybucji, sekwencja zadań zawiera uszkodzone odwołanie i programu Configuration Manager zatrzymuje uruchamianie sekwencji zadań w tym momencie, chyba że kroku zakończonego niepowodzeniem był zdefiniowany warunek nakazujący kontynuowanie po wystąpieniu błędu.  

> [!IMPORTANT]  
>  Domyślnie sekwencja zadań kończy się niepowodzeniem po tym, kiedy jeden z jej kroków lub jedna z akcji kończy się niepowodzeniem. Jeśli chcesz, aby sekwencja zadań kontynuowała działanie, nawet gdy jeden etap zakończy się niepowodzeniem, przeprowadź edycję sekwencji zadań, kliknij kartę **Opcje** , a następnie wybierz opcję **Kontynuuj przy błędzie**.  

 Aby uzyskać więcej informacji na temat kroków, które można dodać do sekwencji zadań, zobacz [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

##  <a name="BKMK_TSGroups"></a> Grupy sekwencji zadań  
 **Grupy** obejmują wiele kroków w sekwencji zadań. Grupa sekwencji zadań składa się z nazwy, opcjonalnego opisu i wszelkich opcjonalnych warunków, które są oceniane jako jedna całość, zanim sekwencja zadań przejdzie do następnego kroku, aby kontynuować działanie. Grupy mogą być zagnieżdżane w innych grupach, przy czym każda może zawierać mieszaninę kroków i podgrup. Grupy są praktycznym sposobem łączenia wielu kroków, które mają jakiś wspólny warunek.  

> [!IMPORTANT]  
>  Domyślnie grupa sekwencji zadań kończy się niepowodzeniem po tym, kiedy dowolny z jej kroków lub dowolna z osadzonych w niej grup kończy się niepowodzeniem. Jeśli chcesz, aby sekwencja zadań kontynuowała działanie, gdy jeden krok lub osadzona grupa zakończy się niepowodzeniem, przeprowadź edycję sekwencji zadań, kliknij kartę **Opcje** , a następnie wybierz opcję **Kontynuuj przy błędzie**.  

 W poniższej tabeli przedstawiono sposób **Kontynuuj przy błędzie** działa opcja w przypadku grupowania kroków.  

 W tym przykładzie istnieją dwie grupy sekwencji zadań, które zawiera trzy kroki sekwencji zadań każdego.  

|Grupa lub krok sekwencji zadań|Ustawienie opcji Kontynuuj przy błędzie|  
|---------------------------------|-------------------------------|  
|**Sekwencja zadań — Grupa 1**|**Opcja Kontynuuj przy błędzie** wybrana.|  
|Sekwencja zadań — Krok 1|**Opcja Kontynuuj przy błędzie** wybrana.|  
|Sekwencja zadań — Krok 2|Nie ustawiono.|  
|Sekwencja zadań — Krok 3|Nie ustawiono.|  
|**Sekwencja zadań — Grupa 2**|Nie ustawiono.|  
|Sekwencja zadań — Krok 4|Nie ustawiono.|  
|Sekwencja zadań — Krok 5|Nie ustawiono.|  
|Sekwencja zadań — Krok 6|Nie ustawiono.|  

-   Jeśli krok 1 sekwencji zadań zakończy się niepowodzeniem, sekwencja zadań będzie kontynuowane przy użyciu sekwencji zadań — krok 2.  

-   Krok 2 sekwencji zadań zakończy się niepowodzeniem, sekwencja zadań, nie można uruchomić sekwencji zadań — krok 3, ale jest nadal uruchomione zadania sekwencji kroki 4 i 5, które znajdują się w innej grupie sekwencji zadań.  

-   Jeśli krok 4 sekwencji zadań zakończy się niepowodzeniem, żaden kolejny krok nie są uruchamiane i sekwencja zadań kończy się niepowodzeniem, ponieważ **Kontynuuj przy błędzie** ustawienie nie została skonfigurowana dla grupy 2 sekwencji zadań.  

 Należy przypisać nazwę do grupy sekwencji zadań, mimo że nazwa grupy nie musi być unikatowa. Grupę sekwencji zadań można również opatrzyć opcjonalnym opisem.  

##  <a name="BKMK_TSVariables"></a> Zmienne sekwencji zadań  
 Zmienne sekwencji zadań stanowią zbiór par nazw i wartości, zapewniających ustawienia wdrożenia systemu operacyjnego i konfiguracji dla komputera, systemu operacyjnego i użytkownika zadań konfiguracji stanu na komputerze klienckim programu Configuration Manager. Zmienne sekwencji zadań udostępniają mechanizm konfigurowania i dostosowywania kroków w sekwencjach zadań.  

 Podczas uruchamiania sekwencji zadań wiele jej ustawień jest przechowywanych jako zmienne środowiskowe. Można uzyskać dostęp, lub zmień wartości wbudowanych zmiennych sekwencji zadań i może utworzyć nowego zadania zmienne sekwencji do dostosowania sposobu uruchamiania sekwencji zadań na komputerze docelowym.  

 Zmienne sekwencji zadań w środowisku sekwencji zadań służy do wykonywania następujących czynności:  

-   Skonfiguruj ustawienia dla akcji sekwencji zadań  

-   Podać argumenty wiersza polecenia dla kroku sekwencji zadań  

-   Ocena warunku decydującego o tym, czy krok sekwencji zadań lub grupy jest uruchamiany  

-   Podanie wartości niestandardowym skryptom używanym w sekwencji zadań  

 Na przykład może być sekwencję zadań, która zawiera **Przyłącz do domeny lub grupy roboczej** krok sekwencji zadań. Sekwencja zadań może być wdrożona w różnych kolekcjach, w których przynależność do kolekcji jest określana na podstawie przynależności do domeny. W takim przypadku można określić zmienną sekwencji zadań dla kolekcji, dla każdej kolekcji, nazwę domeny, a następnie użyć tej zmiennej sekwencji zadań podać właściwej nazwy domeny w sekwencji zadań.  

###  <a name="BKMK_TSCreateVariables"></a> Tworzenie zmiennych sekwencji zadań  
 Możesz dodać nowe zmienne sekwencji zadań w celu dostosowania i kontrolowania kroków w sekwencji zadań. Można na przykład utworzyć zmienną sekwencji zadań zastępującą ustawienie kroku wbudowanej sekwencji zadań. Można też utworzyć niestandardową zmienną sekwencji zadań do wykorzystania w warunkach, wierszach polecenia lub niestandardowych krokach sekwencji zadań. Po utworzeniu zmiennej sekwencji zadań zarówno ta zmienna, jak i skojarzona z nią wartość są zachowywane w obrębie środowiska sekwencji zadań, nawet jeśli sekwencja powoduje ponowne uruchomienie komputera docelowego. Zmienna i jej wartość mogą być używane w obrębie sekwencji zadań w środowiskach różnych systemów operacyjnych. Na przykład można użyć w pełnym systemie operacyjnym Windows i w środowisku Windows PE.  

 W poniższej tabeli opisano metody tworzenia informacje o zmiennej i dodatkowe użycia sekwencji zadań.  

|Metoda tworzenia|Użycie|  
|-------------------|-----------|  
|Ustawianie pól w krokach sekwencji zadań za pomocą edytora sekwencji zadań|Określa wartości domyślne dla kroku sekwencji zadań. Zmienna i jej wartość są dostępne tylko podczas uruchamiania kroku w sekwencji zadań. Nie są one częścią ogólnego środowiska sekwencji, a nie są dostępne dla innych kroków sekwencji zadań w sekwencji zadań.<br /><br /> Aby uzyskać listę wbudowanych zmiennych i skojarzonych z nimi działań, zobacz [zmienne akcji sekwencji zadań](../understand/task-sequence-action-variables.md).|  
|Dodawanie kroku ustalonej zmiennej sekwencji zadań w sekwencji zadań|Określa zmienną sekwencji zadań i jej wartość w środowisku sekwencji zadań w momencie uruchamiania kroku sekwencji zadań w ramach sekwencji zadań. Wszystkie kolejne kroki sekwencji zadań mogą uzyskiwać dostęp do zmiennej środowiskowej i jej wartości.|  
|Definiowanie zmiennej dla kolekcji|Określa zmienne sekwencji zadań i ich wartości dla kolekcji komputerów. Wszystkie sekwencje zadań, dla których obiektem docelowym jest dana kolekcja, mogą uzyskiwać dostęp do zmiennych sekwencji zadań i ich wartości.|  
|Definiowanie zmiennej dla komputera|Określa zmienne sekwencji zadań i ich wartości dla konkretnego komputera. Wszystkie sekwencje zadań, dla których obiektem docelowym jest dany komputer, mogą uzyskiwać dostęp do zmiennych sekwencji zadań i ich wartości.|  
|Dodawanie zmiennej sekwencji zadań na stronie **Dostosowywanie** kreatora nośnika sekwencji zadań|Określa zmienne sekwencji zadań i ich wartości dla sekwencji zadań uruchamianej z nośnika, który może uzyskiwać dostęp do zmiennej sekwencji zadań i jej wartości.|  

 Aby zastąpić wartość domyślną wbudowanej zmiennej sekwencji zadań, należy zdefiniować zmienną sekwencji zadań pod taką samą nazwą, jak nazwa wbudowanej zmiennej sekwencji zadań. Aby uzyskać listę wbudowanych zmiennych sekwencji zadań z nimi działań i zastosowań, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md).  

 Zmienną sekwencji zadań można usunąć ze środowiska sekwencji zadań przy użyciu tych samych metod, jak podczas tworzenia zmiennej sekwencji zadań. W takim przypadku aby usunąć zmienną ze środowiska sekwencji zadań, należy ustawić wartość zmiennej sekwencji zadań na pusty ciąg.  

 Możesz łączyć metody Ustaw zmienną sekwencji zadań środowiska różne wartości w tej samej sekwencji. Realizując bardziej zaawansowany scenariusz, można ustawić wartości domyślne kroków sekwencji za pomocą kreatora sekwencji zadań, a następnie ustawić niestandardową wartość zmiennej, korzystając z różnych metod jej tworzenia. Poniższa lista zawiera opis zasady, które określają, która wartość jest używana podczas tworzenia zmiennej sekwencji zadań przy użyciu więcej niż jednej metody.  

1.  **Ustaw zmienną sekwencji zadań** krok zastępuje wszystkie inne metody tworzenia.  

2.  Zmienne dla komputera mają pierwszeństwo przed zmiennymi dla kolekcji. Jeśli określisz tej samej nazwy zmiennej sekwencji zadań dla zmiennej dla komputera i zmiennej dla kolekcji, wartość zmiennej dla komputera jest używany, gdy komputer docelowy uruchomi wdrożona sekwencja zadań.  

3.  Sekwencje zadań można uruchamiać z nośnika. Zamiast zmiennych dla kolekcji lub dla komputera należy użyć zmiennych dla nośnika. Kiedy sekwencję zadań uruchamia się z nośnika, zmienne dla komputera i dla kolekcji nie są uwzględniane ani używane. Zamiast tego zmienne sekwencji zadań zdefiniowane na **dostosowywania** kreatora nośnika sekwencji zadań służą do ustawienia wartości właściwych dla sekwencji zadań uruchamianej z nośnika  

4.  Jeśli wartość zmiennej sekwencji zadań nie jest ustawiona w ogólnym środowisku sekwencji, akcje wbudowane Użyj wartości domyślnej dla kroku, zgodnie z ustawieniami w edytorze sekwencji zadań.  

 Oprócz zastępowania wartości dla ustawienia kroku sekwencji zadań wbudowanych, można też utworzyć nową zmienną środowiskową do użycia w kroku sekwencji zadań, skryptów, wiersza polecenia lub warunku. Podczas określania nazwy nowej zmiennej sekwencji zadań, skorzystaj z następujących wskazówek:  

-   Nazwa zmiennej sekwencji zadań, który określisz może zawierać litery, cyfry, znaku podkreślenia (_) i myślnik (-).  

-   Nazwy zmiennych sekwencji zadań mają długość co najmniej 1 znaku i długość maksymalną 256 znaków.  

-   Zmienne zdefiniowane przez użytkownika musi zaczynać się od litery (A-Z lub a-z).  

-   Nazwy zmiennych zdefiniowanych przez użytkownika nie może rozpoczynać się od znaku podkreślenia. Tylko zmienne sekwencji zadań tylko do odczytu są poprzedzone znakiem podkreślenia  

    > [!NOTE]  
    >  Zmienne sekwencji zadań tylko do odczytu mogą być odczytywane przez kroki sekwencji zadań w sekwencji zadań, ale nie można ustawić. Na przykład można użyć zmiennej sekwencji zadań tylko do odczytu jako część wiersza polecenia dla **Uruchom wiersz polecenia** zmiennej akcji sekwencji zadań, ale nie można ustawić zmiennej tylko do odczytu za pomocą **Ustaw zmienną sekwencji zadań** zmiennej akcji.  

-   Nazwy zmiennych sekwencji zadań nie jest uwzględniana wielkość liter. Na przykład nazwy OSDVAR i osdvar oznaczają tę samą zmienną sekwencji zadań.  

-   Nazwy zmiennych sekwencji zadań nie może rozpocząć lub kończyć spacją ani zawierać spacji osadzonych. Spacje pozostawione na początku lub na końcu nazwy zmiennej sekwencji zadań są ignorowane.  

 W poniższej tabeli przedstawiono przykłady zmiennych sekwencji zadań prawidłowe i nie jest ważna określone przez użytkownika.  

|Przykłady prawidłowych nazw zmiennych określonych przez użytkownika|Przykłady nieprawidłowych nazw zmiennych określonych przez użytkownika|  
|-------------------------------------------------------|----------------------------------------------------------|  
|MojaZmienna|1Variable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie może rozpoczynać się cyfrą.|  
|Moja_Zmienna|MyV@riable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie może zawierać znaku @.|  
|Moja_Zmienna_2|_MyVariable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie może rozpoczynać się od znaku podkreślenia.|  

 Ogólne ograniczenia dotyczące zmiennych sekwencji zadań:  

-   Wartości zmiennych sekwencji zadań nie może przekraczać 4000 znaków.  

-   Nie można tworzyć ani zastępować zmiennej sekwencji zadań tylko do odczytu. Zmienne tylko do odczytu są oznaczane nazwami, które zaczynają się od znaku podkreślenia (_). Można uzyskać dostęp do wartości zmiennych sekwencji zadań tylko do odczytu w danej sekwencji zadań, nie można jednak zmienić skojarzonych z nimi wartości.  

-   W wartościach zmiennych sekwencji zadań może być uwzględniana wielkość liter, zależnie od sposobu użycia wartości. W większości wypadków w wartościach zmiennych sekwencji zadań wielkość liter nie jest uwzględniana. Jednak niektóre wartości mogą być uwzględniana wielkość liter jak w przypadku zmiennej zawierającej hasło.  

-   Nie ma żadnego limitu liczby zmiennych sekwencji zadań można utworzyć. Ogólnie jednak liczbę zmiennych ogranicza rozmiar środowiska sekwencji zadań. Całkowity limit rozmiaru środowiska sekwencji zadań wynosi 32 MB.  

###  <a name="BKMK_TSEnvironmentVariables"></a> Dostęp do zmiennych środowiskowych  
 Po określeniu zmiennej sekwencji zadań i jej wartość przy użyciu jednej z metod opisanych w poprzedniej części można użyć wartości zmiennej środowiskowej w sekwencjach zadań. Można uzyskać dostępu do wartości domyślnych wbudowanych zmiennych sekwencji zadań, określić nową wartość dla zmiennej wbudowanej lub użyć niestandardowej zmiennej sekwencji zadań w wierszu polecenia lub skryptu.  

 W poniższej tabeli przedstawiono operacje sekwencji zadań, które może zostać wykonana przez uzyskiwanie dostępu do zmiennych środowiskowych sekwencji zadań.  

|Operacja sekwencji zadań|Użycie|  
|-----------------------------|-----------|  
|Konfigurowanie ustawień akcji|Można określić, że ustawienia kroku sekwencji zadań znajduje się wartość zmiennej, po uruchomieniu sekwencji.<br /><br /> Aby przekazać krok sekwencji zadań ustawienie przy użyciu zmiennej środowiskowej sekwencji zadań, użyj edytora sekwencji zadań do edycji danego kroku i określ nazwę zmiennej jako wartości pola. Nazwę zmiennej należy ująć w znaki procentu (%) w celu wskazania, że chodzi o zmienną środowiskową.|  
|Przekazanie argumentów do wiersza polecenia|Można określić część lub całość niestandardowego wiersza polecenia przy użyciu wartości zmiennej środowiskowej.<br /><br /> Aby przekazać do ustawienia wiersza za pomocą zmiennej środowiskowej, użyj nazwy zmiennej jako części **wiersza polecenia** pole **Uruchom wiersz polecenia** krok sekwencji zadań. Nazwa zmiennej musi być ujęta w znaki procentu (%).<br /><br /> Na przykład następujące polecenie w wierszu korzysta z wbudowanej zmiennej środowiskowej C:\File.txt zapisać nazwę komputera.<br /><br /> <br /><br /> **Cmd /C % _SMSTSMachineName % > C:\File.txt**|  
|Ocena warunku kroku|Wbudowanych lub niestandardowych zmiennych środowiskowych można użyć w ramach warunku kroku lub grupy sekwencji zadań. Wartość zmiennej środowiskowej zostanie oceniona przed kroku sekwencji zadań lub uruchamia grupy.<br /><br /> Aby dodać warunek oceniający wartość zmiennej, wykonaj następujące czynności:<br /><br /> 1.  Wybierz odpowiedni krok lub grupę, którą chcesz dodać warunek.<br />2.  Na **opcje** krok lub grupę, wybierz kartę **zmienną sekwencji zadań** z **Dodaj warunek** listy rozwijanej.<br />3.  W **zmienną sekwencji zadań** okna dialogowego wprowadź nazwę zmiennej, testowany warunek i wartość zmiennej.|  
|Przekazanie informacji do niestandardowego skryptu|Zmienne sekwencji zadań można Odczyt i zapis za pośrednictwem obiektu Microsoft.SMS.TSEnvironment COM sekwencja zadań jest uruchomiona.<br /><br /> Poniższy przykład przedstawia plik skryptu języka Visual Basic, który odpytuje **_SMSTSLogPath** zmienną sekwencji zadań, aby uzyskać bieżącą lokalizację dziennika. Skrypt ustawia ponadto zmienną niestandardową.<br /><br /> <br /><br /> **dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")**<br /><br /> <br /><br /> **dim logPath**<br /><br /> <br /><br /> **’ Można wysyłać zapytania do środowiska, aby uzyskać istniejącą zmienną.**<br /><br /> **logPath = env("_SMSTSLogPath")**<br /><br /> <br /><br /> **’ Można również ustawić zmienną w środowisku OSD.**<br /><br /> **env("MyCustomVariable") = "varname"**<br /><br /> <br /><br /> Więcej informacji o sposobach używania zmiennych sekwencji zadań w skryptach znajduje się w dokumentacji zestawu SDK.|  

###  <a name="BKMK_ComputerCollectionVariables"></a> Zmienne komputerów i kolekcji  
 Można skonfigurować sekwencje zadań, aby działać jednocześnie na wielu komputerach lub kolekcji. Można określić unikatowe informacje dla poszczególnych komputerów lub kolekcji, takich jak określ klucz produktu systemu operacyjnego lub Dołącz wszystkich członków kolekcji do określonej domeny.  

 Zmienne sekwencji zadań można przypisać do jednego komputera lub kolekcji. Kiedy sekwencja zadań zaczyna być uruchamiana na komputerze docelowym lub w kolekcji, wartości są stosowane do komputera docelowego lub kolekcji.  

 Można określić zmienne sekwencji zadań dla pojedynczego komputera lub kolekcji. Kiedy sekwencja zadań zaczyna być uruchamiana na komputerze docelowym lub w kolekcji, określone zmienne są dodawane do środowiska i wartości są dostępne dla wszystkich kroków sekwencji zadań w sekwencji zadań.  

> [!WARNING]  
>  Jeśli używasz tej samej nazwy zmiennej dla zmiennej zarówno dla kolekcji, jak i na komputerze, wartość zmiennej komputera mają pierwszeństwo przed zmiennej dla kolekcji. Zmienne sekwencji zadań, które są przypisywane do kolekcji mają pierwszeństwo przed wbudowanych zmiennych sekwencji zadań.  

 Aby uzyskać więcej informacji dotyczących sposobu tworzenia zmiennych sekwencji dla komputerów i kolekcji zadań, zobacz [utworzyć zmienne sekwencji zadań dla komputerów i kolekcji](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTSVariables).  

###  <a name="BKMK_TSMediaVariables"></a> Zmienne nośnika sekwencji zadań  
 Można określić zmienne sekwencji zadań dla sekwencji zadań, które są uruchamiane z nośnika. W przypadku używania nośnika do wdrażania systemu operacyjnego należy dodać zmienne sekwencji zadań i określić ich wartości podczas tworzenia nośnika; zmienne i ich wartości są przechowywane na nośniku.  

> [!NOTE]  
>  Sekwencje zadań są magazynowane na nośnikach autonomicznych. Jednak wszystkie inne typy nośników, takich jak nośniki wstępnie przygotowane, pobierają sekwencję zadań z punktu zarządzania.  

 Zmienne sekwencji zadań można określić na **dostosowywania** strony kreatora nośnika sekwencji zadań. Aby uzyskać informacje o tworzeniu nośników, zobacz [Tworzenie nośnika sekwencji zadań](../deploy-use/create-task-sequence-media.md).  

> [!TIP]  
>  Sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

##  <a name="BKMK_TSCreate"></a> Tworzenie sekwencji zadań  
 Sekwencje zadań można tworzyć przy użyciu Kreatora tworzenia sekwencji zadań. Kreator służy do tworzenia wbudowanych sekwencji zadań, wykonujących określone zadania, lub niestandardowych sekwencji zadań, które mogą wykonywać wiele rozmaitych zadań.  

 Można na przykład utworzyć sekwencje zadań, które kompilują i przechwytują obraz systemu operacyjnego komputera odniesienia, instalują obraz istniejącego systemu operacyjnego na komputerze docelowym lub tworzą niestandardową sekwencję zadań, która wykonuje dostosowane zadanie. Można użyć niestandardowych sekwencji zadań można wykonywać specjalne wdrożenia systemów operacyjnych.  

 Aby uzyskać więcej informacji o sposobie tworzenia sekwencji zadań, zobacz [tworzenia sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTaskSequence).  

##  <a name="BKMK_TSEdit"></a> Edycja sekwencji zadań  
 Sekwencja zadań można edytować za pomocą **edytora sekwencji zadań**. Edytor pozwala wprowadzać następujące zmiany do sekwencji zadań:  

-   Można dodawać i usuwać kroki z sekwencji zadań.  

-   Można zmienić kolejność kroków sekwencji zadań.  

-   Można dodawać i usuwać grupy kroków.  

-   Można określić, czy sekwencja zadań będzie kontynuować działanie po wystąpieniu błędu.  

-   Dodawanie warunków do kroków i grup sekwencji zadań.  

> [!IMPORTANT]  
>  Jeśli sekwencja zadań powstaną jakiekolwiek nieskojarzone odwołania do jakiegoś pakietu lub programu wyniku edycji, należy skorygować odwołania, usunąć pozbawiony odwołania program z sekwencji zadań lub tymczasowo wyłączyć krok sekwencji zadań zakończonych niepowodzeniem, dopóki uszkodzone odwołanie zostanie naprawione lub usunięte.  

 Aby uzyskać więcej informacji o sposobie edytowania sekwencji zadań, zobacz [edytowania sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

##  <a name="BKMK_TSDeploy"></a> Wdrażanie sekwencji zadań  
 Sekwencję zadań można wdrożyć na komputerach docelowych, które znajdują się w dowolnej kolekcji programu Configuration Manager. Dotyczy to także kolekcji **Wszystkie nieznane komputery** , która służy do wdrażania systemów operacyjnych na nieznanych komputerach. Sekwencji zadań nie można jednak wdrażać w kolekcjach użytkowników.  

> [!IMPORTANT]  
>  Nie należy wdrażać sekwencji zadań instalujących systemy operacyjne w nieodpowiednich kolekcjach, na przykład w kolekcji **Wszystkie systemy** . Należy upewnić się, że kolekcja, do której nastąpi wdrażanie sekwencji zadań, zawiera tylko te komputery, na których ma zostać zainstalowany system operacyjny. Aby zapobiec niepożądanemu wdrożeniu systemu operacyjnego, można zarządzać ustawieniami wdrażania. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

 Każdy komputer docelowy, który odbiera sekwencję zadań uruchamia sekwencję zadań zgodnie z ustawieniami określonymi we wdrożeniu. Sama sekwencja zadań nie zawiera skojarzonych z nią plików ani programów. Wszelkie pliki, do których odwołuje się sekwencja zadań, muszą już być obecne na komputerze docelowym lub rezydować w punkcie dystrybucji dostępnym dla klientów. Sekwencja zadań instaluje Ponadto pakiety, które odwołują się programy, nawet jeśli program lub pakiet jest już zainstalowana na komputerze docelowym.  

> [!NOTE]  
>  W odróżnieniu od pakietów i programów Jeśli sekwencja zadań instaluje jakąś aplikację, instalowania aplikacji tylko wtedy, gdy są spełnione dotyczące jej reguły wymagań aplikacji i aplikacja nie jest już zainstalowana, na podstawie metody wykrywania określonej aplikacji.  

 Klient programu Configuration Manager uruchamia wdrożenie sekwencji zadań po pobraniu zasad klienta. Informacje o tym, jak zainicjować to działanie, nie czekając na następny cykl sondowania, znajdują się w temacie [Inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 Wdrażając sekwencje zadań na urządzeniach z systemem Windows Embedded z włączoną obsługą filtru zapisu, można określić, czy podczas wdrażania należy wyłączyć filtr zapisu na urządzeniu, a następnie po zakończonym wdrażaniu ponownie uruchomić urządzenie. Jeśli filtr zapisu nie zostanie wyłączony, sekwencja zadań zostaje wdrożona na tymczasowej nakładce i nie będzie dostępna po ponownym uruchomieniu urządzenia.  

> [!NOTE]  
>  Podczas wdrażania sekwencji zadań na urządzeniu z systemem Windows Embedded, upewnij się, że urządzenie jest członkiem do kolekcji ze skonfigurowanym oknem obsługi. Pozwala na zarządzanie, gdy jest włączona i wyłączania filtru zapisu, a po ponownym uruchomieniu urządzenia.  
>   
>  Jeśli klienci pobierają sekwencje zadań poza oknem obsługi, sekwencja zadań zostaje pobrana dwukrotnie. W tym scenariuszu klienci będą pobiorą sekwencję zadań, wyłączyć filtry zapisu ponownego uruchomienia komputera i następnie sekwencji zadań ponownie pobrać ponieważ sekwencja zadań została pobrana na tymczasową nakładkę, która zostanie wyczyszczona po ponownym uruchomieniu urządzenia.  

 Aby uzyskać więcej informacji na temat sposobu wdrażania sekwencji zadań, zobacz [wdrożyć sekwencję zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_TSExportImport"></a> Eksportowanie i importowanie sekwencji zadań  
 Menedżer konfiguracji umożliwia eksportowanie i Importowanie sekwencji zadań. Podczas eksportowania sekwencji zadań można dołączyć do niej obiekty, do których sekwencja zadań się odwołuje. Obejmują one obrazu systemu operacyjnego, obraz rozruchowy, pakiet agenta klienta, pakiet sterownika i aplikacje z zależnościami.  

> [!NOTE]  
>  Proces eksportu i importu sekwencji zadań jest bardzo podobny do procesu eksportu i importu aplikacji w programie Configuration Manager.  

 Aby uzyskać więcej informacji dotyczących sposobu eksportowania i importowania sekwencji zadań, zobacz [eksportu i importu sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ExportImport).  

##  <a name="BKMK_TSRun"></a> Uruchamianie sekwencji zadań  
 Domyślnie sekwencje zadań są zawsze uruchamiane przy użyciu lokalnego konta systemowego. Krok wiersza polecenia sekwencji zadań daje możliwość uruchamiania sekwencji zadań pod kontrolą innego konta. Po uruchomieniu sekwencji zadań, klient programu Configuration Manager najpierw sprawdza ewentualnych pakietów, do którego istnieje odwołanie przed uruchomieniem jej kroków sekwencji zadań. Jeśli pakiet, do którego odwołuje się sekwencja zadań, nie przeszedł sprawdzania poprawności lub nie jest dostępny w punkcie dystrybucji, sekwencja zadań zwraca błąd dla kroku sekwencji skojarzonego z tym pakietem.  

 Jeśli rozpowszechniana sekwencja zadań jest skonfigurowany do pobierania i uruchamiania, wszystkie pakiety i aplikacje zależne zostaną pobrane do pamięci podręcznej klienta programu Configuration Manager. Wymagane pakiety i aplikacje są pobierane z punktów dystrybucji, a jeśli rozmiar pamięci podręcznej klienta programu Configuration Manager jest zbyt mała lub nie można znaleźć pakietu lub aplikacji, sekwencja zadań kończy się niepowodzeniem i jest generowany komunikat o stanie. Można też określić, że klient ma pobierać zawartość tylko wtedy, kiedy jest to wymagane — w tym celu należy wybrać opcję **W razie potrzeby pobierz zawartość lokalnie przez uruchomienie sekwencji zadań**— albo wskazać, używając opcji **Uruchom program z punktu dystrybucji** , że klient ma zainstalować pliki bezpośrednio z punktu dystrybucji, bez uprzedniego pobierania ich do pamięci podręcznej. **Uruchom program z punktu dystrybucji** opcja jest dostępna tylko wtedy, gdy pakiety, do którego istnieje odwołanie ustawienie **skopiuj zawartość tego pakietu do udziału pakietu w punktach dystrybucji** włączone **dostęp do danych** karcie **pakietu** właściwości.  

 Jeśli klient wykonujący sekwencję zadań, nie można zlokalizować zależnego pakietu lub aplikacji, klienta natychmiast wysyła informację o błędzie, gdy wdrożenie jest skonfigurowane jako **dostępne**. Jednak jeśli jest skonfigurowane jako wdrożenie **wymagane**, oczekiwania przez klienta programu Configuration Manager i ponownych prób próbę pobrania zawartości aż do terminu ostatecznego, w przypadku, gdy zawartość nie została jeszcze zreplikowana do dystrybucji punkt ten klient uzyskuje dostęp.  

 Jeśli sekwencja zadań zakończy się pomyślnie lub nie powiedzie się, programu Configuration Manager jest rejestrowana w historii klienta programu Configuration Manager. Nie można anulować ani zatrzymać sekwencji zadań po zainicjowaniu na komputerze.  

> [!IMPORTANT]  
>  Jeśli krok sekwencji zadań wymaga ponownego uruchomienia komputera klienckiego, klient musi mieć możliwość rozruchu ze sformatowanej partycji dysku. W przeciwnym razie sekwencja zadań nie powiedzie się niezależnie od metody obsługi błędów skonfigurowanej w sekwencji.  

 Gdy obiekt zależny sekwencji zadań, na przykład pakiet dystrybucji oprogramowania, zostanie zaktualizowany do nowszej wersji, wszystkie sekwencje zadań zawierające odniesieniu do tego pakietu zostaną automatycznie zaktualizowane zgodnie z nowszą wersją, bez względu na liczbę wdrożonych aktualizacji.  

> [!NOTE]  
>  Zanim klient programu Configuration Manager uruchamia sekwencję zadań, klient sprawdza wszystkie sekwencje zadań na potrzeby możliwych zależności oraz dostępność tych zależności w punkcie dystrybucji. W przypadku zidentyfikowania usuniętego obiektu, od którego zależy sekwencja zadań, klient generuje błąd i nie wykonuje sekwencji.  

###  <a name="BKMK_RunProgram"></a> Uruchamianie programu przed uruchomieniem sekwencji zadań  
 Można wybrać program uruchamiany przed uruchomieniem sekwencji zadań. Aby określić, jaki program ma być uruchomiony, otwórz **właściwości** okno dialogowe dla sekwencji zadań i wybierz **zaawansowane** kartę, aby ustawić następujące opcje:  

> [!IMPORTANT]  
>  Aby uruchomić program przed uruchomieniem sekwencji zadań, cała zawartość zadania sekwencji i programu musi być dostępny w udziale pakietu dla pakietu. Udział pakietu można skonfigurować na karcie **Dostęp do danych** w oknie właściwości pakietu.  

-   **Uruchom najpierw inny program**: Określ, czy inny program do uruchomienia przed uruchomieniem sekwencji zadań.  

    > [!IMPORTANT]  
    >  To ustawienie ma zastosowanie tylko do sekwencji zadań, które są uruchamiane w pełnej wersji systemu operacyjnego. Menedżera konfiguracji ignoruje to ustawienie, jeśli sekwencja zadań została uruchomiona przy użyciu środowiska PXE lub nośnika rozruchowego.  

-   **Pakiet**: Określ pakiet, który zawiera program.  

-   **Program**: Określ program do uruchomienia.  

-   **Zawsze uruchamiaj ten program w pierwszej kolejności**: Określ, czy program Configuration Manager, aby uruchomić ten program każdorazowo przed uruchomieniem sekwencji zadań na tym samym kliencie. Po pomyślnym uruchomieniu programu domyślnie ten program nie jest ponownie uruchamiany, gdy na tym samym kliencie następuje ponowne uruchomienie sekwencji zadań.  

 Jeśli uruchomienie wybranego programu na kliencie nie powiedzie się, sekwencja zadań nie jest uruchamiana.  

##  <a name="BKMK_TSMaintenanceWindow"></a> Zastosowanie okna obsługi do określenia czasu uruchomienia sekwencji zadań  
 Można określić podczas uruchomienia sekwencji zadań, definiując okno obsługi kolekcji zawierającej komputery docelowe. W przypadku okna obsługi konfiguruje się datę rozpoczęcia, godzinę rozpoczęcia i zakończenia oraz wzorzec cyklu. Ponadto podczas ustalania harmonogramu dla okna obsługi można zdecydować, że to okno ma zastosowanie tylko do sekwencji zadań. Aby uzyskać więcej informacji, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

> [!IMPORTANT]  
>  W przypadku skonfigurowania uruchamiania sekwencji zadań przy użyciu okna obsługi uruchomiona sekwencja jest wykonywana nawet po zakończeniu okna obsługi. Sekwencja zadań może się zakończyć powodzeniem lub błędem.  

##  <a name="BKMK_TSNetworkAccessAccount"></a> Sekwencje zadań i konto dostępu do sieci  
 Mimo że sekwencje zadań są uruchamiane tylko w kontekście konta systemu lokalnego, może być konieczne konfigurowanie konta dostępu do sieci w następujących okolicznościach:  

-   Należy poprawnie skonfigurować konto dostępu do sieci lub sekwencja zadań zakończy się niepowodzeniem, jeśli próby uzyskiwania dostępu do pakietów programu Configuration Manager w punktach dystrybucji zakończy się. Aby uzyskać więcej informacji o koncie dostępu do sieci, zobacz [konta dostępu do sieci](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

    > [!NOTE]  
    >  Konto dostępu do sieci nigdy nie jest używana jako kontekst zabezpieczeń dla uruchamiania programów, instalowania aplikacji, instalowania aktualizacji ani uruchamiania sekwencji zadań; jednak konta dostępu do sieci umożliwia dostęp do skojarzonych zasobów w sieci.  

-   Korzystając z obrazu rozruchowego do inicjowania wdrożenia systemu operacyjnego, programu Configuration Manager używa środowiska Windows PE, która nie jest pełną wersją systemu operacyjnego. Środowisko systemu Windows PE używa generowanej automatycznie nazwy niestandardowej, która nie jest członkiem żadnej domeny. Jeśli nie poprawnie skonfigurować konto dostępu do sieci, komputer może nie mieć wystarczających uprawnień dostępu do wykonania sekwencji zadań wymaganych pakietów programu Configuration Manager do.  

##  <a name="BKMK_TSCreateMedia"></a> Tworzenie nośnika sekwencji zadań  
 Sekwencji zadań oraz ich powiązane pliki i zależności może zapisywać na różnorodnych nośnikach. Dotyczy to takich nośników wymiennych, jak zestawy dysków DVD lub CD, dyski flash USB na potrzeby nośników przechwytywania, samodzielnych i rozruchowych. Można też zapisywać w plikach formatu Windows Imaging Format (WIM) na nośnikach wstępnych.  

 Można utworzyć następujące typy nośnika:  

-   **Nośnik przechwytywania**. Przechwyć nośnika przechwytywania obrazu systemu operacyjnego, który jest skonfigurowany i utworzony poza infrastrukturą programu Configuration Manager. Nośnik przechwytywania może zawierać niestandardowe programy uruchamiane przed sekwencją zadań. Program niestandardowy może interakcje z pulpitem, monitować użytkownika o wprowadzenie wartości lub tworzenia zmienne, które mają być używane przez sekwencję zadań.  

     Aby uzyskać więcej informacji, zobacz [Tworzenie nośnika przechwytywania](../deploy-use/create-capture-media.md).  

-   **Nośnik samodzielny**. Nośniki samodzielne zawierają sekwencję zadań i wszystkie skojarzone obiekty, które są niezbędne do uruchomienia sekwencji. Zadanie nośnika autonomicznego, które można uruchomić sekwencji, gdy programu Configuration Manager jest ograniczona lub nie łączności z siecią. Nośnik samodzielny można uruchomić w następujący sposób:  

    -   Jeśli komputer docelowy nie jest uruchomiony, obraz środowiska Windows PE, który jest skojarzony z sekwencją zadań jest używany z nośnika autonomicznego i następuje uruchomienie sekwencji zadań.  

    -   Nośnik samodzielny można uruchomić ręcznie, jeśli użytkownik jest zalogowany w sieci i inicjuje instalację.  

    > [!IMPORTANT]  
    >  Kroki sekwencji zadań nośnika autonomicznego musi być w stanie uruchomić bez żadnych pobierania danych z sieci, a w przeciwnym razie krok sekwencji zadań, który próbuje pobrać danych kończy się niepowodzeniem. Na przykład krok sekwencji zadań, która wymaga pobrania pakietu w punkcie dystrybucji nie powiodło się; Jednak jeśli potrzebny pakiet znajduje się na nośniku samodzielnym, krok sekwencji zadań zakończy się pomyślnie.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](../deploy-use/create-stand-alone-media.md).  

-   **Nośnik rozruchowy**. Nośnik rozruchowy zawiera pliki wymagane do uruchomienia komputera docelowego, tak aby możliwość połączenia z infrastrukturą programu Configuration Manager, aby określić, które sekwencji zadań do uruchomienia w oparciu o przynależności do kolekcji. Sekwencja zadań i obiekty zależne nie znajdują się na nośniku; są pobierane przez sieć z klienta programu Configuration Manager. Ta metoda jest przydatna na nowych komputerach lub wdrożenia bez systemu operacyjnego, lub gdy żaden klient programu Configuration Manager lub system operacyjny znajduje się na komputerze docelowym.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika rozruchowego](../deploy-use/create-bootable-media.md).  

-   **Wstępnie przygotowanego nośnika**. Nośniki wstępne pozwalają wdrażać obrazy systemu operacyjnego na komputerach docelowych, które nie mają zainicjowanej obsługi administracyjnej. Wstępnie przygotowanego nośnika jest przechowywana jako plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta tego komputera lub w Centrum przygotowywania przedsiębiorstwa niepołączonym do środowiska programu Configuration Manager.  

     Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie przygotowanego nośnika](../deploy-use/create-prestaged-media.md).  

 Podczas tworzenia nośnika należy określić hasło umożliwiające kontrolę dostępu do plików, które znajdują się na nośniku. Jeśli w przypadku określenia hasła użytkownik musi występować o wprowadzenie hasła na komputerze docelowym po uruchomieniu sekwencji zadań.  

 Po uruchomieniu sekwencji zadań za pomocą nośnika architektura mikroukładu komputera określona zawarte na nośniku nie zostaną rozpoznane i sekwencja zadań podejmie próbę uruchomienia nawet, jeśli określona architektura nie odpowiada rzeczywiście zainstalowanych na komputerze docelowym. Jeśli architektura mikroukładu znajdująca się na nośniku nie jest zgodna z architekturą zainstalowaną na komputerze docelowym, instalacja nie powiedzie się.  

 Aby uzyskać więcej informacji o sposobie wdrażania systemów operacyjnych za pomocą nośników, zobacz [Utwórz nośnik sekwencji zadań](../deploy-use/create-task-sequence-media.md).  
