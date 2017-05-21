---
title: "Tworzenie nośnika rozruchowego - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Nośnik rozruchowy w programie Configuration Manager ułatwiają zainstalować nową wersję systemu Windows lub Zastąp ustawienia komputera i transferu."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ead79e64-1b63-4d0d-8bd5-addff8919820
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 9032698fa12bf453041ea06bf330d3b4687c2a97
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-bootable-media-with-system-center-configuration-manager"></a>Tworzenie nośnika rozruchowego z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Nośnik rozruchowy w programie Configuration Manager zawiera obraz rozruchowy, opcjonalne polecenia przeduruchomieniowe i skojarzonych z nimi plików i pliki programu Configuration Manager. Użyj wstępnie przygotowanego nośnika w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Zastąp istniejący komputer i przenieść ustawień](replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_CreateBootableMedia"></a> Tworzenie nośnika rozruchowego  
 Podczas uruchamiania za pomocą nośnika rozruchowego uruchomiany jest komputer docelowy, który następnie łączy się z siecią i pobiera z niej sekwencję zadań, obraz systemu operacyjnego oraz inną wymaganą zawartość. Ponieważ sekwencja zadań nie znajduje się na nośniku, sekwencję zadań oraz zawartość można zmienić bez konieczności ponownego tworzenia nośnika. Pakiety na nośniku rozruchowym nie są szyfrowane. Należy podjąć odpowiednie środki bezpieczeństwa, takie jak dodanie hasła do nośnika, oraz upewnić się, że zawartość pakietu jest chroniona przed nieautoryzowanymi użytkownikami.  

 Przed utworzeniem nośnika rozruchowego za pomocą Kreatora tworzenia nośnika sekwencji zadań należy upewnić się, że zostały spełnione wszystkie z następujących warunków:  

|Zadanie|Opis|  
|----------|-----------------|  
|Obraz rozruchowy|Należy wziąć pod uwagę następujące kwestie dotyczące obrazu rozruchowego, który będzie używany w sekwencji zadań do wdrażania systemu operacyjnego:<br /><br /> -Architektura obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.<br />-Upewnij się, czy obraz rozruchowy zawiera sterowniki pamięci masowej i sieci, są wymagane do udostępnienia komputera docelowego.|  
|Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego|W ramach nośnika rozruchowego należy określić sekwencję zadań służącą do wdrażania systemu operacyjnego. Czynności w celu utworzenia nowej sekwencji zadań, można znaleźć w temacie [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).|  
|Dystrybucja całej zawartości skojarzonej z sekwencją zadań|Całą zawartość wymaganą przez sekwencję zadań należy umieścić w co najmniej jednym punkcie dystrybucji. Zawartość ta obejmuje obraz rozruchowy i inne skojarzone pliki przeduruchomieniowe. Kreator zbiera informacje z punktu dystrybucji, w którym tworzy nośnik rozruchowy. Użytkownik musi mieć uprawnienia do **odczytu** biblioteki zawartości w tym punkcie dystrybucji.  Aby uzyskać szczegółowe informacje, zobacz [informacje o bibliotece zawartości](../../core/plan-design/hierarchy/the-content-library.md).|  
|Przygotowanie wymiennego dysku USB|Dla wymiennego dysku USB:<br /><br /> Jeśli ma być używany wymienny dysk USB, musi on być podłączony do komputera, na którym uruchomiono kreatora, i być wykrywalny przez system Windows jako urządzenie wymienne. Podczas tworzenia nośnika kreator zapisuje dane bezpośrednio na dysku USB. Nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnika samodzielnego na dysku flash USB zawierającym plik o rozmiarze ponad 4 GB.|  
|Tworzenie folderu wyjściowego|Dla zestawu dysków CD/DVD:<br /><br /> Przed uruchomieniem Kreatora tworzenia nośnika sekwencji zadań w celu utworzenia nośnika dla zestawu dysków CD lub DVD należy utworzyć folder na pliki wyjściowe kreatora. Nośnik utworzony dla zestawu dysków CD lub DVD jest zapisywany bezpośrednio w folderze w postaci plików ISO.|  

 Aby utworzyć nośnik rozruchowy, należy wykonać czynności opisane w poniższej procedurze.  

### <a name="to-create-bootable-media"></a>Tworzenie nośnika rozruchowego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybór typu nośnika** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz opcję **Nośnik rozruchowy**.  

    -   Opcjonalnie, aby zezwolić tylko na wdrożenie systemu operacyjnego bez wprowadzania danych przez użytkownika, wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego**.  

        > [!IMPORTANT]  
        >  Po wybraniu tej opcji nie będzie wyświetlany monit o wprowadzenie przez użytkownika informacji o konfiguracji sieci lub opcjonalnych sekwencji zadań. Jednak w przypadku skonfigurowania ochrony hasłem nośnika użytkownik nadal otrzymuje monit o hasło.  

5.  Na stronie **Zarządzanie nośnikiem** wybierz jedną z poniższych opcji, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz opcję **Nośnik dynamiczny** , jeżeli chcesz zezwolić punktowi zarządzania na przekierowywanie nośnika do innego punktu zarządzania w oparciu o lokalizację klienta w granicach lokacji.  

    -   Wybierz opcję **Nośnik oparty na lokacji** , aby nośnik kontaktował się tylko z określonym punktem zarządzania.  

6.  Na stronie **Typ nośnika** określ, czy nośnik jest dyskiem flash czy zestawem dysków CD/DVD, a następnie skonfiguruj następujące opcje:  

    > [!IMPORTANT]  
    >  Nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnika samodzielnego na dysku flash USB zawierającym plik o rozmiarze ponad 4 GB.  

    -   Jeżeli wybrano opcję **Dysk flash USB**, określ dysk, na którym ma być przechowywana zawartość.  

    -   Jeśli wybrano opcję **Zestaw CD/DVD**, należy określić pojemność nośnika oraz nazwę i ścieżkę do plików wyjściowych. Kreator zapisuje pliki wyjściowe do tej lokalizacji. Na przykład:  **\\\servername\folder\outputfile.iso**  

         Jeżeli pojemność nośnika jest zbyt mała do zapisania całej zawartości, tworzonych jest kilka plików, które należy zapisać na wielu dyskach CD lub DVD. Jeżeli jest wymaganych wiele nośników, program Configuration Manager dodaje kolejny numer do nazw poszczególnych plików wyjściowych, który tworzy. Ponadto można wdrożyć aplikację z systemem operacyjnym, a nie mieści się na jednym nośniku, Configuration Manager są przechowywane aplikacji na kilku nośnikach. Po uruchomieniu nośnika samodzielnego program Configuration Manager monituje użytkownika o kolejnego nośnika, na którym przechowywana jest aplikacja.  

        > [!IMPORTANT]  
        >  W przypadku wybrania istniejącego obrazu ISO Kreator tworzenia nośnika sekwencji zadań usuwa ten obraz z dysku lub udziału bezpośrednio po przejściu do następnej strony kreatora. Istniejący obraz zostanie usunięty nawet w przypadku anulowania pracy kreatora.  

     Kliknij przycisk **Dalej**.  

7.  Na stronie **Zabezpieczenia** wybierz poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz **Włącz obsługę nieznanych komputerów** pole wyboru, aby zezwolić nośnikowi na wdrażanie systemu operacyjnego na komputerze, który nie jest zarządzany przez program Configuration Manager. Nie ma rekordów tych komputerów w bazie danych programu Configuration Manager.  

         Nie rozpoznano następujących komputerów:  

        -   Komputer, na którym nie zainstalowano klienta programu Configuration Manager  

        -   Komputer, który nie jest importowany do programu Configuration Manager  

        -   Komputer, który nie został odnaleziony przez program Configuration Manager  

    -   Zaznacz pole wyboru **Chroń nośnik hasłem** i wprowadź silne hasło w celu ochrony nośnika przed nieautoryzowanym dostępem. Po określeniu hasła użytkownik musi podać to hasło, aby używać nośnika rozruchowego.  

        > [!IMPORTANT]  
        >  Zgodnie z najlepszymi rozwiązaniami w zakresie bezpieczeństwa, w celu ochrony nośnika rozruchowego zawsze należy przypisać mu hasło.  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTP wybierz opcję **Utwórz certyfikat nośnika z podpisem własnym**, a następnie określ daty rozpoczęcia i wygaśnięcia certyfikatu.  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTPS wybierz opcję **Importuj certyfikat PKI**, a następnie określ certyfikat do zaimportowania i jego hasło.  

         Aby uzyskać więcej informacji dotyczących tego certyfikatu klienta używanego dla obrazów rozruchowych, zobacz [wymagania dotyczące certyfikatu PKI](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Koligacja urządzenia użytkownika**: Do obsługi zarządzania skoncentrowanego na użytkowniku w programie Configuration Manager, określ sposób nośnik ma skojarzyć użytkowników z komputerem docelowym. Aby uzyskać więcej informacji o sposobie wdrażania systemów operacyjnych obsługi koligacji urządzenia użytkownika, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym. Ta funkcja opiera się na akcjach w ramach sekwencji zadań, która wdraża system operacyjny. W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym podczas wdrażania systemu operacyjnego do komputera docelowego.  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika w oczekiwaniu na zatwierdzenie przez administratora** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym po udzieleniu zatwierdzenia. Ta funkcja opiera się na zakresie sekwencji zadań, która wdraża system operacyjny.  W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym, lecz przed wdrożeniem systemu operacyjnego oczekuje na zatwierdzenie przez użytkownika administracyjnego.  

        -   Wybierz opcję **Nie zezwalaj na koligację urządzenia użytkownika** , jeżeli nie chcesz, aby nośnik skojarzał użytkowników z komputerem docelowym. W tym scenariuszu sekwencja zadań nie skojarza użytkowników z komputerem docelowym podczas wdrażania systemu operacyjnego.  

8.  Na stronie **Obraz rozruchowy** wybierz poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Architektura dystrybuowanego obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.  

    -   W polu **Obraz rozruchowy** wybierz obraz rozruchowy do uruchomienia komputera docelowego.  

    -   W polu **Punkt dystrybucji** określ punkt dystrybucji, w którym znajduje się obraz rozruchowy. Kreator pobiera obraz rozruchowy z punktu dystrybucji i zapisuje go na nośniku.  

        > [!NOTE]  
        >  Użytkownik musi mieć uprawnienia do **odczytu** biblioteki zawartości w punkcie dystrybucji.  

    -   W przypadku tworzenia nośnika rozruchowego opartego na lokacji na stronie **Zarządzanie nośnikiem** kreatora należy wybrać punkt zarządzania w lokacji głównej w polu **Punkt zarządzania** .  

    -   W przypadku tworzenia dynamicznego nośnika rozruchowego na stronie **Zarządzanie nośnikiem** kreatora należy określić używane punkty zarządzania lokacji głównej i  kolejność wstępnej komunikacji wg priorytetów w polu **Skojarzone punkty zarządzania**.  

9. Na stronie **Dostosowywanie** wybierz poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   Określ zmienne używane przez sekwencję zadań do wdrożenia systemu operacyjnego.  

    -   Określ dowolne polecenia przeduruchomieniowe, które chcesz uruchomić przed rozpoczęciem sekwencji zadań. Polecenia przeduruchomieniowe są skryptami lub plikami wykonywalnymi, które mogą prowadzić interakcję z użytkownikiem w środowisku Windows PE przed uruchomieniem sekwencji zadań w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [polecenia dla nośnika sekwencji zadań Przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Podczas tworzenia nośnika sekwencji zadań sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

         Opcjonalnie zaznacz pole wyboru **Dołącz pliki dla polecenia przeduruchomieniowego** , aby dodać wymagane pliki dla polecenia przeduruchomieniowego.  

10. Ukończ pracę kreatora.  

## <a name="create-bootable-media-on-a-usb-drive-from-a-network-share"></a>Tworzenie nośnika rozruchowego na dysku USB z udziału sieciowego
Informacje w tej sekcji opisano tworzenia nośnika rozruchowego na dysk flash USB w przypadku dysku flash nie jest podłączony do komputera z konsolą programu Configuration Manager. Do tworzenia nośnika rozruchowego na dysk USB, można utworzyć nośnik rozruchowy sekwencji zadań, zainstaluj obraz ISO i transferu plików z ISO na dysk USB.

1. [Tworzenie nośnika rozruchowego sekwencji zadań](#to-create-task-boobable-media). Na **typu nośnika** wybierz opcję **zestaw CD/DVD**. Kreator zapisuje pliki wyjściowe w lokalizacji określonej przez użytkownika. Na przykład:  **\\\servername\folder\outputfile.iso**.  
2. Przygotuj wymienny dysk USB. Dysku musi być sformatowany, puste i rozruchowego.
3. Zainstaluj obraz ISO z lokalizacji udziału i transferu plików z ISO na dysk USB.

## <a name="next-steps"></a>Następne kroki  
[Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego](use-bootable-media-to-deploy-windows-over-the-network.md)  

