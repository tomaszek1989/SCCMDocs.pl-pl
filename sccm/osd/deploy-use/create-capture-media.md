---
title: Tworzenie nośnika przechwytywania
titleSuffix: Configuration Manager
description: Użyj Kreatora tworzenia nośnika sekwencji zadań do utworzenia nośnika przechwytywania w programie Configuration Manager do przechwycenia obrazu systemu operacyjnego z komputera odniesienia.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 10eb8958-3848-49d7-95c0-16119b624580
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 827247ba5d9c1badd1961ee56110b6dc1ea9351e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-capture-media-with-system-center-configuration-manager"></a>Tworzenie nośnika przechwytywania z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Nośnik przechwytywania w programie Configuration Manager umożliwia przechwytywanie obrazu systemu operacyjnego z komputera odniesienia. Nośnika przechwytywania należy użyć w następującym scenariuszu:  

-   [Tworzenie sekwencji zadań w celu przechwycenia systemu operacyjnego](create-a-task-sequence-to-capture-an-operating-system.md)  

##  <a name="BKMK_CreateCaptureMedia"></a> Tworzenie nośników przechwytywania  
 Nośnik przechwytywania umożliwia przechwycenie obrazu systemu operacyjnego z komputera odniesienia. Nośnik przechwytywania zawiera obraz rozruchowy, który uruchamia komputer odniesienia, oraz sekwencję zadań, która przechwytuje obraz systemu operacyjnego.

Nośnik przechwytywania można utworzyć za pomocą Kreatora tworzenia nośnika sekwencji zadań. Przed uruchomieniem kreatora upewnij się, że zostały spełnione wszystkie następujące warunki:  

|Zadanie|Opis|  
|----------|-----------------|  
|Obraz rozruchowy|Należy wziąć pod uwagę następujące kwestie dotyczące obrazu rozruchowego, który będzie używany w sekwencji zadań do przechwytywania systemu operacyjnego:<br /><br /> — Architektura obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.<br />-Sprawdź, czy obraz rozruchowy zawiera sterowniki sieciowe i masowej magazynu, które są wymagane do udostępnienia komputera docelowego.|  
|Dystrybucja całej zawartości skojarzonej z sekwencją zadań|Całą zawartość wymaganą przez sekwencję zadań należy umieścić w co najmniej jednym punkcie dystrybucji. Zawartość ta obejmuje obraz rozruchowy, obraz systemu operacyjnego i inne skojarzone pliki. Kreator zbiera informacje z punktu dystrybucji, w którym tworzy nośnik samodzielny. Użytkownik musi mieć uprawnienia do **odczytu** biblioteki zawartości w tym punkcie dystrybucji.  Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).|  
|Przygotowanie wymiennego dysku USB|Dla wymiennego dysku USB:<br /><br /> Jeśli ma być używany wymienny dysk USB, musi on być podłączony do komputera, na którym uruchomiono kreatora, i być wykrywalny przez system Windows jako urządzenie wymienne. Podczas tworzenia nośnika kreator zapisuje dane bezpośrednio na dysku USB.|  
|Tworzenie folderu wyjściowego|Dla zestawu dysków CD/DVD:<br /><br /> Przed uruchomieniem Kreatora tworzenia nośnika sekwencji zadań w celu utworzenia nośnika dla zestawu dysków CD lub DVD należy utworzyć folder na pliki wyjściowe kreatora. Nośnik utworzony dla zestawu dysków CD lub DVD jest zapisywany bezpośrednio w folderze w postaci plików ISO.|  

 Aby utworzyć nośnik przechwytywania, należy wykonać czynności opisane w poniższej procedurze.  

#### <a name="to-create-capture-media"></a>Tworzenie nośnika przechwytywania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybór typu nośnika** wybierz opcję **Nośnik przechwytywania**, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Typ nośnika** określ, czy nośnik jest dyskiem flash czy zestawem dysków CD/DVD, a następnie skonfiguruj następujące opcje:  

    -   Jeżeli wybrano opcję **Dysk flash USB**, określ dysk, na którym ma być przechowywana zawartość.  

    -   Jeśli wybrano opcję **Zestaw CD/DVD**, należy określić pojemność nośnika oraz nazwę i ścieżkę do plików wyjściowych. Kreator zapisuje pliki wyjściowe do tej lokalizacji. Na przykład:  **\\\servername\folder\outputfile.iso**  

         Jeżeli pojemność nośnika jest zbyt mała do zapisania całej zawartości, tworzonych jest kilka plików, które należy zapisać na wielu dyskach CD lub DVD. Jeżeli jest wymaganych wiele nośników, programu Configuration Manager dodaje kolejny numer do nazwy poszczególnych utworzonych plików wyjściowych. Ponadto jeśli wdrażania aplikacji z systemem operacyjnym, a nie mieści się na jednym nośniku, program Configuration Manager przechowuje aplikacji na kilku nośnikach. Po uruchomieniu nośnika samodzielnego program Configuration Manager monitu o kolejnego nośnika, na którym przechowywana jest aplikacja.  

        > [!IMPORTANT]  
        >  W przypadku wybrania istniejącego obrazu ISO Kreator tworzenia nośnika sekwencji zadań usuwa ten obraz z dysku lub udziału bezpośrednio po przejściu do następnej strony kreatora. Istniejący obraz zostanie usunięty nawet w przypadku anulowania pracy kreatora.  

     Kliknij przycisk **Dalej**.  

6.  Na stronie **Obraz rozruchowy** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Architektura wybranego obrazu rozruchowego musi być zgodna z architekturą komputera odniesienia. Przykładowo komputer odniesienia z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer odniesienia z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.  

    -   W polu **Obraz rozruchowy** wybierz obraz rozruchowy do uruchomienia komputera odniesienia.  

    -   W polu **Punkt dystrybucji** określ punkt dystrybucji, w którym znajduje się obraz rozruchowy. Kreator pobiera obraz rozruchowy z punktu dystrybucji i zapisuje go na nośniku.  

        > [!NOTE]  
        >  Użytkownik musi mieć uprawnienia do odczytu biblioteki zawartości w punkcie dystrybucji.  

7.  Ukończ pracę kreatora.  
