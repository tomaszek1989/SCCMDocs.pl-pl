---
title: "Automatyzacja zadań zagadnienia związane z planowaniem | Dokumentacja firmy Microsoft"
description: "Planowanie przed automatyzacji zadań w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc497a8a-3c54-4529-8403-6f6171a21c64
caps.latest.revision: 13
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 830f715b688cc9929a179da94eba9c81de8db11a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-considerations-for-automating-tasks-in-system-center-configuration-manager"></a>Zagadnienia związane z planowaniem automatyzacji zadań w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można utworzyć sekwencje zadań do automatyzacji zadań w środowisku programu System Center Configuration Manager. Są wśród nich zadania tak różnorodne, jak przechwytywanie systemu operacyjnego na komputerze odniesienia czy wdrażanie systemu operacyjnego na jednym lub wielu komputerach docelowych. Działania sekwencji zadań definiuje się w poszczególnych krokach sekwencji. Kiedy sekwencja zadań jest uruchamiana, działania każdego jej kroku są wykonywane na poziomie wiersza polecenia w kontekście systemu lokalnego i nie wymagają interwencji użytkownika. Poniższe sekcje służą do ułatwić zaplanowanie do automatyzacji zadań w programie Configuration Manager.

##  <a name="BKMK_TSStepsActions"></a>Kroki sekwencji zadań i akcji  
 Kroki to podstawowe składniki sekwencji zadań. Mogą one zawierać polecenia pozwalające konfigurować i przechwytywać system operacyjny komputera odniesienia lub mogą one zawierać polecenia instalujące system operacyjny, sterowniki, klienta programu Configuration Manager i oprogramowania na komputerze docelowym. Polecenia kroku sekwencji zadań definiuje się w działaniach tego kroku. Istnieją dwa rodzaje działań. Działanie definiowane za pomocą ciągu wiersza polecenia nazywa się akcją niestandardową. Działanie wstępnie zdefiniowane przez program Configuration Manager nazywa się akcją wbudowaną. Sekwencja zadań może wykonywać dowolne kombinacje akcji niestandardowych i wbudowanych.  

 Kroki sekwencji zadań mogą ponadto obejmować warunki kontrolujące zachowanie danego kroku, takie jak zatrzymanie sekwencji zadań lub kontynuować sekwencję zadań, jeśli wystąpi błąd. Warunki dodaje się do kroku przez włączenie do niego zmiennej sekwencji zadań. Za pomocą zmiennej **SMSTSLastActionRetCode** możesz na przykład testować warunek poprzedniego kroku. Zmienne można dodawać do pojedynczego kroku lub grupy kroków.  

 Kroki sekwencji zadań są przetwarzane sekwencyjnie, co obejmuje akcję samego kroku oraz wszelkie warunki, które są przypisane do kroku. Po uruchomieniu programu Configuration Manager do przetworzenia sekwencji zadań, następnego kroku nie jest uruchomiona, dopóki nie zakończy się akcja poprzedniego. Sekwencję zadań uważa się za ukończoną, gdy wszystkie jej kroki zostały wykonane lub programu Configuration Manager przerwał uruchamianie sekwencji zadań przed ukończeniem wszystkich jej kroków powoduje kroku nie powiodło się. Na przykład jeśli w kroku sekwencji zadań nie może zlokalizować obrazu w odwołaniu lub pakietu w punkcie dystrybucji, sekwencja zadań zawiera uszkodzone odwołanie i programu Configuration Manager zatrzymuje uruchamianie sekwencji zadań w tym momencie, chyba że kroku zakończonego niepowodzeniem był zdefiniowany warunek nakazujący kontynuowanie po wystąpieniu błędu.  

> [!IMPORTANT]  
>  Domyślnie sekwencja zadań kończy się niepowodzeniem po tym, kiedy jeden z jej kroków lub jedna z akcji kończy się niepowodzeniem. Jeśli chcesz, aby sekwencja zadań kontynuowała działanie, nawet gdy jeden etap zakończy się niepowodzeniem, przeprowadź edycję sekwencji zadań, kliknij kartę **Opcje** , a następnie wybierz opcję **Kontynuuj przy błędzie**.  

 Aby uzyskać więcej informacji na temat kroków, które można dodać do sekwencji zadań, zobacz [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

##  <a name="BKMK_TSGroups"></a> Grupy sekwencji zadań  
 **Grupy** obejmują wiele kroków w sekwencji zadań. Grupa sekwencji zadań składa się z nazwy, opcjonalnego opisu i wszelkich opcjonalnych warunków, które są oceniane jako jedna całość, zanim sekwencja zadań przejdzie do następnego kroku, aby kontynuować działanie. Grupy mogą być zagnieżdżane w innych grupach, przy czym każda może zawierać mieszaninę kroków i podgrup. Grupy są praktycznym sposobem łączenia wielu kroków, które mają jakiś wspólny warunek.  

> [!IMPORTANT]  
>  Domyślnie grupa sekwencji zadań kończy się niepowodzeniem po tym, kiedy dowolny z jej kroków lub dowolna z osadzonych w niej grup kończy się niepowodzeniem. Jeśli chcesz, aby sekwencja zadań kontynuowała działanie, gdy jeden krok lub osadzona grupa zakończy się niepowodzeniem, przeprowadź edycję sekwencji zadań, kliknij kartę **Opcje** , a następnie wybierz opcję **Kontynuuj przy błędzie**.  

 W poniższej tabeli przedstawiono sposób, w jaki **Kontynuuj przy błędzie** działa opcja w przypadku grupowania kroków.  

 W tym przykładzie przedstawiono dwie grupy sekwencji zadań, które obejmuje trzy kroki sekwencji zadań każdego.  

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

-   Jeśli krok 1 sekwencji zadań zakończy się niepowodzeniem, sekwencja zadań jest kontynuowany krok 2 sekwencji zadań.  

-   Jeśli krok 2 sekwencji zadań zakończy się niepowodzeniem, sekwencja zadań nie można uruchomić krok 3, ale kontynuuje działanie kroków 4 i 5, które znajdują się w innej grupie sekwencji zadań sekwencji zadań.  

-   Jeśli krok 4 sekwencji zadań zakończy się niepowodzeniem, żaden kolejny krok nie są uruchamiane i sekwencji zadań zakończy się niepowodzeniem, ponieważ **Kontynuuj przy błędzie** ustawienie nie została skonfigurowana dla grupy 2 sekwencji zadań.  

 Do grup sekwencji zadań, należy przypisywać nazwy, choć nazwa grupy nie musi być unikatowy. Grupę sekwencji zadań można również opatrzyć opcjonalnym opisem.  

##  <a name="BKMK_TSVariables"></a> Zmienne sekwencji zadań  
 Zmienne sekwencji zadań stanowią zbiór par nazw i wartości, zapewniających ustawienia wdrażania systemu operacyjnego i konfiguracji dla komputera, systemu operacyjnego i użytkownika zadań konfiguracyjnych stanu na komputerze klienckim programu Configuration Manager. Zmienne sekwencji zadań udostępniają mechanizm konfigurowania i dostosowywania kroków w sekwencjach zadań.  

 Podczas uruchamiania sekwencji zadań wiele jej ustawień jest przechowywanych jako zmienne środowiskowe. Można uzyskać dostęp lub zmienić wartości wbudowanych zmiennych sekwencji zadań i można utworzyć nowe zadanie zmienne sekwencji w celu dostosowania sposobu uruchamiania sekwencji zadań na komputerze docelowym.  

 Zmienne sekwencji zadań w środowisku sekwencji zadań umożliwia wykonywanie następujących czynności:  

-   Skonfiguruj ustawienia dla akcji sekwencji zadań  

-   Podanie argumentów wiersza polecenia dla kroku sekwencji zadań  

-   Ocena warunku określająca, czy krok sekwencji zadań lub grupa jest uruchomione  

-   Podanie wartości niestandardowym skryptom używanym w sekwencji zadań  

 Na przykład może być sekwencji zadań, która obejmuje **Przyłącz do domeny lub grupy roboczej** sekwencji zadań. Sekwencja zadań może być wdrożona w różnych kolekcjach, w których przynależność do kolekcji jest określana na podstawie przynależności do domeny. W takim przypadku można określić zmienną sekwencji zadań dla kolekcji dla każdej kolekcji nazwy domeny i następnie użyć tej zmiennej sekwencji zadań do podania właściwej nazwy domeny w sekwencji zadań.  

###  <a name="BKMK_TSCreateVariables"></a> Tworzenie zmiennych sekwencji zadań  
 Można dodać nowe zmienne sekwencji zadań w celu dostosowania i kontrolowania kroków w sekwencji zadań. Można na przykład utworzyć zmienną sekwencji zadań zastępującą ustawienie kroku wbudowanej sekwencji zadań. Można też utworzyć niestandardową zmienną sekwencji zadań do wykorzystania w warunkach, wierszach polecenia lub niestandardowych krokach sekwencji zadań. Po utworzeniu zmiennej sekwencji zadań zarówno ta zmienna, jak i skojarzona z nią wartość są zachowywane w obrębie środowiska sekwencji zadań, nawet jeśli sekwencja powoduje ponowne uruchomienie komputera docelowego. Zmienna i jej wartość mogą być używane w obrębie sekwencji zadań w środowiskach różnych systemów operacyjnych. Na przykład można użyć w pełnym systemie operacyjnym Windows i w środowisku Windows PE.  

 W poniższej tabeli opisano metody tworzenia informacje o zmiennej i dodatkowe użycia sekwencji zadań.  

|Metoda tworzenia|Użycie|  
|-------------------|-----------|  
|Ustawianie pól w krokach sekwencji zadań za pomocą edytora sekwencji zadań|Określa wartości domyślne dla kroku sekwencji zadań. Zmienna i jej wartość są dostępne tylko podczas uruchamiania kroku w sekwencji zadań. Nie są one częścią ogólnego środowiska sekwencji, a nie są dostępne dla innych kroków w sekwencji zadań.<br /><br /> Lista wbudowanych zmiennych i skojarzonych z nimi działań, zobacz [zmienne akcji sekwencji zadań](../understand/task-sequence-action-variables.md).|  
|Dodawanie kroku ustalonej zmiennej sekwencji zadań w sekwencji zadań|Określa zmienną sekwencji zadań i jej wartość w środowisku sekwencji zadań w momencie uruchamiania kroku sekwencji zadań w ramach sekwencji zadań. Wszystkie kolejne kroki sekwencji zadań mogą uzyskiwać dostęp do zmiennej środowiskowej i jej wartości.|  
|Definiowanie zmiennej dla kolekcji|Określa zmienne sekwencji zadań i ich wartości dla kolekcji komputerów. Wszystkie sekwencje zadań, dla których obiektem docelowym jest dana kolekcja, mogą uzyskiwać dostęp do zmiennych sekwencji zadań i ich wartości.|  
|Definiowanie zmiennej dla komputera|Określa zmienne sekwencji zadań i ich wartości dla konkretnego komputera. Wszystkie sekwencje zadań, dla których obiektem docelowym jest dany komputer, mogą uzyskiwać dostęp do zmiennych sekwencji zadań i ich wartości.|  
|Dodawanie zmiennej sekwencji zadań na stronie **Dostosowywanie** kreatora nośnika sekwencji zadań|Określa zmienne sekwencji zadań i ich wartości dla sekwencji zadań uruchamianej z nośnika, który może uzyskiwać dostęp do zmiennej sekwencji zadań i jej wartości.|  

 Aby zastąpić wartość domyślną wbudowanej zmiennej sekwencji zadań, należy zdefiniować zmienną sekwencji zadań pod taką samą nazwą, jak nazwa wbudowanej zmiennej sekwencji zadań. Lista wbudowanych zmiennych sekwencji zadań z nimi działań i zastosowań, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md).  

 Zmienną sekwencji zadań można usunąć ze środowiska sekwencji zadań za pomocą tej samej metody, jak podczas tworzenia zmiennej sekwencji zadań. W tym przypadku aby usunąć zmienną ze środowiska sekwencji zadań, należy ustawić wartość zmiennej sekwencji zadań jako ciąg pusty.  

 Można połączyć metody ustawiać różne wartości dla tej samej sekwencji środowiskowej zmiennej sekwencji zadań. Realizując bardziej zaawansowany scenariusz, można ustawić wartości domyślne kroków sekwencji za pomocą kreatora sekwencji zadań, a następnie ustawić niestandardową wartość zmiennej, korzystając z różnych metod jej tworzenia. Poniższa lista opisuje zasady określające wartość, która jest używana podczas tworzenia zmiennej sekwencji zadań przy użyciu więcej niż jednej metody.  

1.  **Ustaw zmienną sekwencji zadań** krok zastępuje wszystkie inne metody tworzenia.  

2.  Zmienne dla komputera mają pierwszeństwo przed zmiennymi dla kolekcji. W przypadku określenia tej samej nazwy zmiennej sekwencji w zadań dla zmiennej dla komputera i zmiennej dla kolekcji, zostanie użyta wartość zmiennej dla komputera, gdy komputer docelowy uruchomi wdrożoną sekwencję zadań.  

3.  Sekwencje zadań można uruchamiać z nośnika. Zamiast zmiennych dla kolekcji lub dla komputera należy użyć zmiennych dla nośnika. Kiedy sekwencję zadań uruchamia się z nośnika, zmienne dla komputera i dla kolekcji nie są uwzględniane ani używane. Zamiast tego zadania zdefiniowane w zmiennych sekwencji **dostosowywania** kreatora nośnika sekwencji zadań są używane do ustawienia wartości właściwych dla sekwencji zadań uruchamianej z nośnika  

4.  Jeśli wartość zmiennej sekwencji zadań nie jest ustawiona w ogólnym środowisku sekwencji, akcje wbudowane posługują się wartością domyślną dla danego kroku, ustawioną w edytorze sekwencji zadań.  

 Oprócz zastępowania wartości ustawień kroku sekwencji zadań wbudowanych, można również tworzyć nowe zmienne środowiskowe do wykorzystania w kroku sekwencji zadań, skryptów, wiersza polecenia lub warunku. Podczas określania nazwy nowej zmiennej sekwencji zadań, należy przestrzegać następujących wytycznych:  

-   Nazwa zmiennej sekwencji zadań przez użytkownika może zawierać litery, cyfry, znak podkreślenia (_) i łącznik (-).  

-   Nazwy zmiennych sekwencji zadań mają długość minimalną 1 znaku i długość maksymalną 256 znaków.  

-   Zmienne zdefiniowane przez użytkownika muszą zaczynać się od litery (A-Z lub a-z).  

-   Nazwy zmiennych zdefiniowanych przez użytkownika nie mogą zaczynać się od znaku podkreślenia. Tylko zmienne sekwencji zadań tylko do odczytu są poprzedzone znakiem podkreślenia  

    > [!NOTE]  
    >  Zmienne sekwencji zadań tylko do odczytu mogą być odczytane przez kroki sekwencji zadań w sekwencji zadań, ale nie można ustawić. Na przykład można użyć zmiennej sekwencji zadań tylko do odczytu jako część wiersza polecenia dla **Uruchom wiersz polecenia** zmiennej akcji sekwencji zadań, ale nie można ustawić zmiennej tylko do odczytu przy użyciu **Ustaw zmienną sekwencji zadań** zmiennej akcji.  

-   Nazwy zmiennych sekwencji zadań nie jest uwzględniana wielkość liter. Na przykład nazwy OSDVAR i osdvar oznaczają tę samą zmienną sekwencji zadań.  

-   Nazwy zmiennych sekwencji zadań nie może rozpocząć lub kończyć spacją ani zawierać spacji osadzonych. Spacje pozostawione na początku lub na końcu nazwy zmiennej sekwencji zadań są ignorowane.  

 W poniższej tabeli przedstawiono przykłady zmienne sekwencji zadań prawidłowych i nieprawidłowych określone przez użytkownika.  

|Przykłady prawidłowych nazw zmiennych określonych przez użytkownika|Przykłady nieprawidłowych nazw zmiennych określonych przez użytkownika|  
|-------------------------------------------------------|----------------------------------------------------------|  
|MojaZmienna|1Variable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie może rozpoczynać się cyfrą.|  
|Moja_Zmienna|MyV@riable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie może zawierać znaku @.|  
|Moja_Zmienna_2|_MyVariable<br /><br /> Zmienne sekwencji zadań określone przez użytkownika nie mogą zaczynać się od znaku podkreślenia.|  

 Ogólne ograniczenia dotyczące zmiennych sekwencji zadań:  

-   Wartości zmiennych sekwencji zadań nie może przekraczać 4000 znaków.  

-   Nie można utworzyć ani zastąpić zmienną sekwencji zadań tylko do odczytu. Zmienne tylko do odczytu są oznaczane nazwami, które zaczynają się od znaku podkreślenia (_). Można uzyskać dostęp do wartości zmiennych sekwencji zadań tylko do odczytu w danej sekwencji zadań, nie można jednak zmienić skojarzonych z nimi wartości.  

-   W wartościach zmiennych sekwencji zadań może być uwzględniana wielkość liter, zależnie od sposobu użycia wartości. W większości wypadków w wartościach zmiennych sekwencji zadań wielkość liter nie jest uwzględniana. Jednak niektóre wartości mogą być uwzględniana wielkość liter, jak w przypadku zmiennej zawierającej hasło.  

-   Nie ma żadnego limitu liczby zmiennych sekwencji zadań można utworzyć. Ogólnie jednak liczbę zmiennych ogranicza rozmiar środowiska sekwencji zadań. Całkowity limit rozmiaru środowiska sekwencji zadań wynosi 32 MB.  

###  <a name="BKMK_TSEnvironmentVariables"></a> Dostęp do zmiennych środowiskowych  
 Po określeniu zmiennej sekwencji zadań i jej wartość za pomocą jednej z metod opisanych w poprzedniej części można użyć wartości zmiennej środowiskowej w swoich sekwencjach zadań. Można uzyskać dostęp do wartości domyślnych wbudowanych zmiennych sekwencji zadań, określić nową wartość dla zmiennej wbudowanej lub użyć niestandardowej zmiennej sekwencji zadań w wierszu polecenia lub skryptu.  

 W poniższej tabeli omówiono operacje sekwencji zadań, które mogą być wykonywane przez uzyskanie dostępu do zmiennych środowiskowych sekwencji zadań.  

|Operacja sekwencji zadań|Użycie|  
|-----------------------------|-----------|  
|Konfigurowanie ustawień akcji|Można określić, że ustawienie kroku sekwencji zadań będzie przyjmować wartość zmiennej po uruchomieniu sekwencji.<br /><br /> Aby przekazać sekwencji zadań ustawienie przy użyciu zmiennej środowiskowej sekwencji zadań, użyj edytora sekwencji zadań do edycji danego kroku i jako wartość pola określ nazwę zmiennej. Nazwę zmiennej należy ująć w znaki procentu (%) w celu wskazania, że chodzi o zmienną środowiskową.|  
|Przekazanie argumentów do wiersza polecenia|Można określić część lub całość niestandardowego wiersza polecenia, używając wartości zmiennej środowiskowej.<br /><br /> Do ustawienia wiersza polecenia przekazać wartość zmiennej środowiskowej, użyj nazwy zmiennej jako części **wiersza polecenia** pola **Uruchom wiersz polecenia** sekwencji zadań. Nazwa zmiennej musi być ujęta w znaki procentu (%).<br /><br /> Na przykład następujący wiersz polecenia korzysta z wbudowanej zmiennej środowiskowej, aby zapisać nazwę komputera do C:\File.txt.<br /><br /> <br /><br /> **Cmd /C % _SMSTSMachineName % > C:\File.txt**|  
|Ocena warunku kroku|Wbudowanych lub niestandardowych zmiennych środowiskowych można użyć w ramach warunku kroku lub grupy sekwencji zadań. Wartość zmiennej środowiskowej zostanie oceniona przed kroku sekwencji zadań lub uruchamia grupy.<br /><br /> Aby dodać warunek oceniający wartość zmiennej, wykonaj następujące czynności:<br /><br /> 1.  Zaznacz krok lub grupę, którą chcesz dodać warunek.<br />2.  Na **opcje** kartę krok lub grupę, wybierz opcję **zmienną sekwencji zadań** z **Dodaj warunek** listy rozwijanej.<br />3.  W **zmienną sekwencji zadań** okna dialogowego należy określić nazwę zmiennej, testowany warunek i wartość zmiennej.|  
|Przekazanie informacji do niestandardowego skryptu|Zmienne sekwencji zadań można odczytywać i zapisywane przy użyciu obiektu Microsoft.SMS.TSEnvironment COM sekwencji zadań jest uruchomiona.<br /><br /> Poniższy przykład przedstawia plik skryptu języka Visual Basic, który odpytuje **_SMSTSLogPath** zmienną sekwencji zadań, aby uzyskać bieżącą lokalizację dziennika. Skrypt ustawia ponadto zmienną niestandardową.<br /><br /> <br /><br /> **dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")**<br /><br /> <br /><br /> **dim logPath**<br /><br /> <br /><br /> **’ Można wysyłać zapytania do środowiska, aby uzyskać istniejącą zmienną.**<br /><br /> **logPath = env("_SMSTSLogPath")**<br /><br /> <br /><br /> **’ Można również ustawić zmienną w środowisku OSD.**<br /><br /> **env("MyCustomVariable") = "varname"**<br /><br /> <br /><br /> Więcej informacji o sposobach używania zmiennych sekwencji zadań w skryptach znajduje się w dokumentacji zestawu SDK.|  

###  <a name="BKMK_ComputerCollectionVariables"></a> Zmienne komputerów i kolekcji  
 Można skonfigurować sekwencje zadań w celu jednoczesnego uruchamiania na wielu komputerach lub w kolekcji. Można określić unikatowe informacje dla każdego komputera lub kolekcji, takie jak określić klucz produktu systemu operacyjnego lub Dołącz wszystkich członków kolekcji do określonej domeny.  

 Zmienne sekwencji zadań można przypisać do jednego komputera lub kolekcji. Kiedy sekwencja zadań zaczyna być uruchamiana na komputerze docelowym lub w kolekcji, określone wartości są stosowane do komputera docelowego lub kolekcji.  

 Można określić zmienne sekwencji zadań dla jednego komputera lub kolekcji. Kiedy sekwencja zadań zaczyna być uruchamiana na komputerze docelowym lub w kolekcji, określone zmienne są dodawane do środowiska i wartości są dostępne dla wszystkich kroków sekwencji zadań w sekwencji zadań.  

> [!WARNING]  
>  Jeśli używasz tej samej nazwy zmiennej zarówno dla kolekcji, jak i na komputerze zmiennej, wartość zmiennej komputera ma pierwszeństwo przed zmiennej kolekcji. Zmienne sekwencji zadań, które można przypisać do kolekcji mają pierwszeństwo przed wbudowanymi zmiennymi sekwencji zadań.  

 Aby uzyskać więcej informacji o sposobie tworzenia zmiennych sekwencji dla komputerów i kolekcji zadań, zobacz [utworzyć zmienne sekwencji zadań dla komputerów i kolekcji](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTSVariables).  

###  <a name="BKMK_TSMediaVariables"></a> Zmienne nośnika sekwencji zadań  
 Można określić zmienne sekwencji zadań dla sekwencji zadań, które są uruchamiane z nośnika. W przypadku używania nośnika do wdrażania systemu operacyjnego należy dodać zmienne sekwencji zadań i określić ich wartości podczas tworzenia nośnika; zmienne i ich wartości są przechowywane na nośniku.  

> [!NOTE]  
>  Sekwencje zadań są magazynowane na nośnikach autonomicznych. Jednak inne typy nośników, takie jak nośniki wstępnie przygotowane, pobierają sekwencję zadań z punktu zarządzania.  

 Zmienne sekwencji zadań można określić na **dostosowanie** strony kreatora nośnika sekwencji zadań. Aby uzyskać informacje o tworzeniu nośników, zobacz [Tworzenie nośnika sekwencji zadań](../deploy-use/create-task-sequence-media.md).  

> [!TIP]  
>  Sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

##  <a name="BKMK_TSCreate"></a> Tworzenie sekwencji zadań  
 Sekwencje zadań można tworzyć za pomocą Kreatora tworzenia sekwencji zadań. Kreator służy do tworzenia wbudowanych sekwencji zadań, wykonujących określone zadania, lub niestandardowych sekwencji zadań, które mogą wykonywać wiele rozmaitych zadań.  

 Można na przykład utworzyć sekwencje zadań, które kompilują i przechwytują obraz systemu operacyjnego komputera odniesienia, instalują obraz istniejącego systemu operacyjnego na komputerze docelowym lub tworzą niestandardową sekwencję zadań, która wykonuje dostosowane zadanie. Niestandardowych sekwencji zadań można użyć do wykonania specjalne wdrożenia systemów operacyjnych.  

 Aby uzyskać więcej informacji dotyczących sposobu tworzenia sekwencji zadań, zobacz [tworzenia sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTaskSequence).  

##  <a name="BKMK_TSEdit"></a> Edycja sekwencji zadań  
 W przypadku edytowania sekwencji zadań za pomocą **edytora sekwencji zadań**. Edytor pozwala wprowadzać następujące zmiany w sekwencjach zadań:  

-   Można dodać lub usuwanie kroków sekwencji zadań.  

-   Można zmienić kolejność kroków sekwencji zadań.  

-   Można dodać lub usunąć grupy kroków.  

-   Można określić, czy sekwencja zadań będzie kontynuować działanie po wystąpieniu błędu.  

-   Dodawanie warunków do kroków i grup sekwencji zadań.  

> [!IMPORTANT]  
>  Jeśli sekwencja zadań powstaną jakiekolwiek nieskojarzone odwołania do pakietu lub programu wyniku edycji, należy skorygować odwołania, usunąć pozbawiony odwołania program z sekwencji zadań lub czasowo wyłączyć błędny krok sekwencji zadań, dopóki uszkodzone odwołanie nie zostanie naprawione lub usunięte.  

 Aby uzyskać więcej informacji dotyczących sposobu edytowania sekwencji zadań, zobacz [edytować sekwencję zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

##  <a name="BKMK_TSDeploy"></a> Wdrażanie sekwencji zadań  
 Sekwencję zadań można wdrożyć na komputerach docelowych, które znajdują się w dowolnej kolekcji programu Configuration Manager. Dotyczy to także kolekcji **Wszystkie nieznane komputery** , która służy do wdrażania systemów operacyjnych na nieznanych komputerach. Sekwencji zadań nie można jednak wdrażać w kolekcjach użytkowników.  

> [!IMPORTANT]  
>  Nie należy wdrażać sekwencji zadań instalujących systemy operacyjne w nieodpowiednich kolekcjach, na przykład w kolekcji **Wszystkie systemy** . Należy upewnić się, że kolekcja, do której nastąpi wdrażanie sekwencji zadań, zawiera tylko te komputery, na których ma zostać zainstalowany system operacyjny. Aby zapobiec niepożądanemu wdrożeniu systemu operacyjnego, można zarządzać ustawieniami wdrażania. Aby uzyskać więcej informacji, zobacz [ustawienia do zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

 Każdy komputer docelowy, który otrzyma sekwencję zadań uruchamia sekwencję zadań zgodnie z ustawieniami określonymi we wdrożeniu. Sama sekwencja zadań nie zawiera skojarzonych z nią plików ani programów. Wszelkie pliki, do których odwołuje się sekwencja zadań, muszą już być obecne na komputerze docelowym lub rezydować w punkcie dystrybucji dostępnym dla klientów. Sekwencja zadań instaluje Ponadto pakiety, które odwołują się programy, nawet jeśli program lub pakiet jest już zainstalowany na komputerze docelowym.  

> [!NOTE]  
>  W odróżnieniu pakietów i programów, jeśli sekwencja zadań instaluje jakąś aplikację, aplikacja jest instalowana tylko wtedy, gdy są spełnione dotyczące jej reguły wymagań aplikacji i aplikacja nie jest już zainstalowana, na podstawie metody wykrywania określonej dla aplikacji.  

 Klient programu Configuration Manager uruchamia wdrożenie sekwencji zadań po pobraniu zasad klienta. Informacje o tym, jak zainicjować to działanie, nie czekając na następny cykl sondowania, znajdują się w temacie [Inicjowanie pobierania zasad dla klienta programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 Wdrażając sekwencje zadań na urządzeniach z systemem Windows Embedded z włączoną obsługą filtru zapisu, można określić, czy podczas wdrażania należy wyłączyć filtr zapisu na urządzeniu, a następnie po zakończonym wdrażaniu ponownie uruchomić urządzenie. Jeśli filtr zapisu nie zostanie wyłączony, sekwencja zadań jest wdrożona na tymczasowej nakładce i nie będzie dostępna po ponownym uruchomieniu urządzenia.  

> [!NOTE]  
>  Podczas wdrażania sekwencji zadań na urządzeniu Windows Embedded, upewnij się, że urządzenie jest członkiem kolekcji, który ma skonfigurowanego okna obsługi. Pozwala to zarządzać czasem włączania i wyłączania filtru zapisu oraz po ponownym uruchomieniu urządzenia.  
>   
>  Jeśli klienci pobierają sekwencje zadań poza oknem obsługi, sekwencja zadań zostaje pobrana dwukrotnie. W tym scenariuszu klienci będą pobiorą sekwencję zadań, wyłączyć filtry zapisu, ponowne uruchomienie komputera i następnie sekwencji zadań ponownie pobrać ponieważ sekwencja zadań została pobrana na tymczasową nakładkę, która zostanie wyczyszczona po ponownym uruchomieniu urządzenia.  

 Aby uzyskać więcej informacji o sposobie wdrażania sekwencji zadań, zobacz [wdrażania sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_TSExportImport"></a> Eksportowanie i importowanie sekwencji zadań  
 Menedżer konfiguracji umożliwia eksportowanie i Importowanie sekwencji zadań. Podczas eksportowania sekwencji zadań można dołączyć do niej obiekty, do których sekwencja zadań się odwołuje. Należą do nich obrazu systemu operacyjnego, obraz rozruchowy, pakiet agenta klienta, pakiet sterownika i aplikacje z zależnościami.  

> [!NOTE]  
>  Proces eksportu i importu sekwencji zadań jest bardzo podobny do procesu eksportu i importu aplikacji w programie Configuration Manager.  

 Aby uzyskać więcej informacji dotyczących sposobu eksportowania i importowania sekwencji zadań, zobacz [eksportu i importu sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ExportImport).  

##  <a name="BKMK_TSRun"></a> Uruchamianie sekwencji zadań  
 Domyślnie sekwencje zadań są zawsze uruchamiane przy użyciu konta systemu lokalnego. Krok wiersza polecenia sekwencji zadań daje możliwość uruchamiania sekwencji zadań pod kontrolą innego konta. Po uruchomieniu sekwencji zadań, klient programu Configuration Manager najpierw sprawdza pod kątem ewentualnych pakietów występujące w odwołaniu przed wykonaniem kroków sekwencji zadań. Jeśli pakiet, do którego odwołuje się sekwencja zadań, nie przeszedł sprawdzania poprawności lub nie jest dostępny w punkcie dystrybucji, sekwencja zadań zwraca błąd dla kroku sekwencji skojarzonego z tym pakietem.  

 Jeśli rozpowszechniana sekwencja zadań jest skonfigurowana do pobierania i uruchamiania, wszystkie pakiety i aplikacje zależne zostaną pobrane do pamięci podręcznej klienta programu Configuration Manager. Wymagane pakiety i aplikacje są pobierane z punktów dystrybucji, a jeśli jest za mały rozmiar pamięci podręcznej klienta programu Configuration Manager lub nie można odnaleźć pakietu lub aplikacji, sekwencja zadań kończy się niepowodzeniem i generowany jest komunikat o stanie. Można też określić, że klient ma pobierać zawartość tylko wtedy, kiedy jest to wymagane — w tym celu należy wybrać opcję **W razie potrzeby pobierz zawartość lokalnie przez uruchomienie sekwencji zadań**— albo wskazać, używając opcji **Uruchom program z punktu dystrybucji** , że klient ma zainstalować pliki bezpośrednio z punktu dystrybucji, bez uprzedniego pobierania ich do pamięci podręcznej. **Uruchom program z punktu dystrybucji** opcja jest dostępna tylko wtedy, gdy pakiety, do którego istnieje odwołanie mają ustawienie **skopiuj zawartość tego pakietu do udziału pakietu w punktach dystrybucji** włączone **dostęp do danych** na karcie **pakietu** właściwości.  

 Jeśli nie można zlokalizować zależnego pakietu lub aplikacji przez uruchomienie sekwencji zadań klienta, klient wysyła natychmiast wystąpił błąd, gdy wdrożenie jest skonfigurowane jako **dostępne**. Jednak jeśli wdrożenie jest skonfigurowane jako **wymagane**, czeka klienta programu Configuration Manager i ponownych prób pobrania zawartości aż do terminu ostatecznego, w przypadku, gdy zawartość nie jest jeszcze zreplikowane do dystrybucji punkt ten klient uzyskuje dostęp.  

 Sekwencja zadań zakończy się pomyślnie lub nie powiedzie się, Configuration Manager rejestruje to historia klienta programu Configuration Manager. Nie można anulować ani zatrzymać sekwencji zadań po zainicjowaniu na komputerze.  

> [!IMPORTANT]  
>  Jeśli krok sekwencji zadań wymaga ponownego uruchomienia komputera klienckiego, klient musi być w stanie do rozruchu ze sformatowanej partycji dysku. W przeciwnym razie sekwencja zadań nie powiedzie się niezależnie od metody obsługi błędów skonfigurowanej w sekwencji.  

 Gdy obiekt zależny sekwencji zadań, na przykład pakiet dystrybucji oprogramowania, zostanie zaktualizowany do nowszej wersji, wszystkie sekwencje zadań zawierające odniesieniu do tego pakietu zostaną automatycznie zaktualizowane zgodnie z nowszą wersją, bez względu na liczbę wdrożonych aktualizacji.  

> [!NOTE]  
>  Zanim klient programu Configuration Manager uruchomi sekwencję zadań, klient sprawdza wszystkie sekwencje zadań dla możliwych zależności oraz dostępność tych zależności w punkcie dystrybucji. W przypadku zidentyfikowania usuniętego obiektu, od którego zależy sekwencja zadań, klient generuje błąd i nie wykonuje sekwencji.  

###  <a name="BKMK_RunProgram"></a> Uruchamianie programu przed uruchomieniem sekwencji zadań  
 Można wybrać program uruchamiany przed uruchomieniem sekwencji zadań. Aby określić, jaki program ma być uruchomiony, otwórz **właściwości** okno dialogowe dla sekwencji zadań i wybierz **zaawansowane** kartę, aby ustawić następujące opcje:  

> [!IMPORTANT]  
>  Aby uruchomić program przed uruchomieniem sekwencji zadań, cała zawartość zadania sekwencji i programu musi być dostępna jako udział dla pakietu. Udział pakietu można skonfigurować na karcie **Dostęp do danych** w oknie właściwości pakietu.  

-   **Uruchom najpierw inny program**: Określ, czy inny program do uruchomienia przed uruchomieniem sekwencji zadań.  

    > [!IMPORTANT]  
    >  To ustawienie ma zastosowanie tylko do sekwencji zadań, które są uruchamiane w pełnej wersji systemu operacyjnego. Menedżer konfiguracji ignoruje to ustawienie, jeśli sekwencja zadań została uruchomiona przy użyciu środowiska PXE lub nośnika rozruchowego.  

-   **Pakiet**: Określ pakiet, który zawiera program.  

-   **Program**: Określ program, który ma być uruchomiony.  

-   **Zawsze uruchamiaj ten program w pierwszej kolejności**: Określ, czy program Configuration Manager, aby uruchomić ten program każdorazowo przed uruchomieniem sekwencji zadań na tym samym kliencie. Po pomyślnym uruchomieniu programu domyślnie ten program nie jest ponownie uruchamiany, gdy na tym samym kliencie następuje ponowne uruchomienie sekwencji zadań.  

 Jeśli uruchomienie wybranego programu na kliencie nie powiedzie się, sekwencja zadań nie jest uruchamiana.  

##  <a name="BKMK_TSMaintenanceWindow"></a> Zastosowanie okna obsługi do określenia czasu uruchomienia sekwencji zadań  
 Można określić czas uruchomienia sekwencji zadań, definiując okno obsługi kolekcji zawierającej komputery docelowe. W przypadku okna obsługi konfiguruje się datę rozpoczęcia, godzinę rozpoczęcia i zakończenia oraz wzorzec cyklu. Ponadto podczas ustalania harmonogramu dla okna obsługi można zdecydować, że to okno ma zastosowanie tylko do sekwencji zadań. Aby uzyskać więcej informacji, zobacz [sposobu używania okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

> [!IMPORTANT]  
>  W przypadku skonfigurowania uruchamiania sekwencji zadań przy użyciu okna obsługi uruchomiona sekwencja jest wykonywana nawet po zakończeniu okna obsługi. Sekwencja zadań może się zakończyć powodzeniem lub błędem.  

##  <a name="BKMK_TSNetworkAccessAccount"></a> Sekwencje zadań i konto dostępu do sieci  
 Mimo że sekwencje zadań są uruchamiane tylko w kontekście konta System lokalny, może być konieczne skonfigurowanie konta dostępu do sieci w następujących okolicznościach:  

-   Należy prawidłowo skonfigurować konto dostępu do sieci lub sekwencji zadań zakończy się niepowodzeniem, jeśli próbuje uzyskać dostęp do pakietów programu Configuration Manager w punktach dystrybucji zakończy się. Aby uzyskać więcej informacji dotyczących kont dostępu do sieci, zobacz [konta dostępu do sieci](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#a-namebkmknaaa-network-access-account).  

    > [!NOTE]  
    >  Konto dostępu do sieci nigdy nie jest używana jako kontekst zabezpieczeń dla uruchamiania programów, instalowania aplikacji, instalowania aktualizacji ani uruchamiania sekwencji zadań. Jednak konto dostępu do sieci służy do uzyskania dostępu do skojarzonych zasobów w sieci.  

-   Korzystając z obrazu rozruchowego do inicjowania wdrożenia systemu operacyjnego, programu Configuration Manager używa środowiska Windows PE, który nie jest pełną wersją systemu operacyjnego. Środowisko systemu Windows PE używa generowanej automatycznie nazwy niestandardowej, która nie jest członkiem żadnej domeny. Jeśli konto dostępu do sieci nie będzie prawidłowo skonfigurowane, komputer może nie mieć wystarczających uprawnień dostępu do wymaganych pakietów programu Configuration Manager do dokończenia sekwencji zadań.  

##  <a name="BKMK_TSCreateMedia"></a> Tworzenie nośnika sekwencji zadań  
 Kilka rodzajów nośników może zapisywać sekwencji zadań i ich powiązanych plików i zależności. Dotyczy to takich nośników wymiennych, jak zestawy dysków DVD lub CD, dyski flash USB na potrzeby nośników przechwytywania, samodzielnych i rozruchowych. Można też zapisywać w plikach formatu Windows Imaging Format (WIM) na nośnikach wstępnych.  

 Można tworzyć nośniki następujących typów:  

-   **Nośnik przechwytywania**. Przechwyć nośnika przechwytywania obrazu systemu operacyjnego, który jest skonfigurowany i utworzony poza infrastrukturą programu Configuration Manager. Nośnik przechwytywania może zawierać niestandardowe programy uruchamiane przed sekwencją zadań. Program niestandardowy może współdziałać z pulpitem, monitować użytkownika o wprowadzenie wartości lub tworzyć zmienne do użytku przez sekwencję zadań.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika przechwytywania](../deploy-use/create-capture-media.md).  

-   **Nośnik samodzielny**. Nośniki samodzielne zawierają sekwencję zadań i wszystkie skojarzone obiekty, które są niezbędne do uruchomienia sekwencji. Zadanie nośnika samodzielnego sekwencji można uruchomić ograniczony programu Configuration Manager lub brak łączności z siecią. Nośniki samodzielne można uruchamiać w następujący sposób:  

    -   Jeśli komputer docelowy nie jest uruchomiony, obraz systemu Windows PE, który jest skojarzony z sekwencją zadań jest używany z nośnika autonomicznego i rozpocznie się sekwencja zadań.  

    -   Nośnik samodzielny można uruchomić ręcznie, jeśli użytkownik jest zalogowany do sieci i inicjuje instalację.  

    > [!IMPORTANT]  
    >  Kroki sekwencji zadań nośnika samodzielnego musi mieć możliwość uruchomienia bez żadnych danych pobieranie z sieci. w przeciwnym razie krok sekwencji zadań, który próbuje pobrać danych kończy się niepowodzeniem. Na przykład krok sekwencji zadań, który wymaga pobrania pakietu z punktu dystrybucji kończy się niepowodzeniem; Jeśli jednak potrzebny pakiet znajduje się na nośnikach autonomicznych, krok sekwencji zadań powiedzie się.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](../deploy-use/create-stand-alone-media.md).  

-   **Nośnik rozruchowy**. Nośnik rozruchowy zawiera pliki wymagane do uruchomienia komputera docelowego, tak aby możliwość połączenia z infrastrukturą programu Configuration Manager, aby określić, które sekwencje zadań w celu uruchomione na podstawie przynależności do kolekcji. Sekwencja zadań i obiekty zależne nie znajdują się na nośniku; są pobierane przez sieć z klienta programu Configuration Manager. Ta metoda jest przydatna dla nowych komputerów lub wdrożeń systemu operacyjnego lub gdy żaden klient programu Configuration Manager lub systemu operacyjnego znajduje się na komputerze docelowym.  

     Aby uzyskać więcej informacji, zobacz [tworzenia nośnika rozruchowego](../deploy-use/create-bootable-media.md).  

-   **Wstępnie przygotowanego nośnika**. Nośniki wstępne pozwalają wdrażać obrazy systemu operacyjnego na komputerach docelowych, które nie mają zainicjowanej obsługi administracyjnej. Wstępnie przygotowanego nośnika jest przechowywany jako plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta lub w Centrum przygotowywania przedsiębiorstwa, który nie jest podłączony do środowiska programu Configuration Manager.  

     Aby uzyskać więcej informacji, zobacz [Tworzenie wstępnie przygotowanego nośnika](../deploy-use/create-prestaged-media.md).  

 Podczas tworzenia nośnika należy określić hasło umożliwiające kontrolę dostępu do plików znajdujących się na nośniku. W przypadku określenia hasła, użytkownik musi być obecna, aby wprowadzić hasło na komputerze docelowym po uruchomieniu sekwencji zadań.  

 Po uruchomieniu sekwencji zadań za pomocą nośnika architektura mikroukładu komputera określona na nośniku nie zostanie rozpoznana i sekwencji zadań próbuje uruchomić, nawet jeśli określona architektura nie jest zgodny, co faktycznie jest zainstalowany na komputerze docelowym. Jeśli architektura mikroukładu znajdująca się na nośniku nie jest zgodna z architekturą zainstalowaną na komputerze docelowym, instalacja nie powiedzie się.  

 Aby uzyskać więcej informacji o sposobie wdrażania systemów operacyjnych za pomocą nośników, zobacz [Utwórz nośnik sekwencji zadań](../deploy-use/create-task-sequence-media.md).  

