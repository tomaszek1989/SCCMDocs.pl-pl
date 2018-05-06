---
title: Tworzenie wstępnie przygotowanego nośnika
titleSuffix: Configuration Manager
description: Tworzenie wstępnie przygotowanego nośnika w System Center Configuration Manager można uprościć wdrażanie systemu Windows w kilku scenariuszach.
ms.date: 04/11/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: ff6e7267-302a-4563-815e-cdc0d1a4b60f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 61c54ad6c0224dfae03a26784f0b3f61271b172c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-prestaged-media-with-system-center-configuration-manager"></a>Tworzenie wstępnie przygotowanego nośnika w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wstępnie przygotowanego nośnika w programie System Center Configuration Manager to plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta tego komputera lub w Centrum przygotowywania przedsiębiorstwa niepołączonym do środowiska programu Configuration Manager.  
Nośnik wstępnie przygotowany zawiera obraz rozruchowy używany do uruchomienia komputera docelowego oraz obraz systemu operacyjnego stosowany względem tego komputera. Możesz także określić aplikacje, pakiety i pakiety sterowników, które mają zostać dołączone do wstępnie przygotowanego nośnika. Na nośniku nie znajduje się sekwencja zadań, która wdraża system operacyjny. Nośnik wstępnie przygotowany jest umieszczany na dysku twardym nowego komputera przed jego wysłaniem do użytkownika końcowego. Użyj wstępnie przygotowanego nośnika w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Tworzenie obrazu dla producenta OEM w fabryce lub lokalnym magazynie](../../osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Wdrażanie funkcji Windows to Go](deploy-windows-to-go.md)  

 Gdy taki komputer z wstępnie przygotowanym nośnikiem zostanie włączony po raz pierwszy, nastąpi rozruch środowiska Windows PE i nawiązanie połączenia z punktem zarządzania w celu zlokalizowania sekwencji zadań, która dokończy proces wdrożenia systemu operacyjnego. Możesz określić aplikacje, pakiety i pakiety sterowników do dołączenia do wstępnie przygotowanego nośnika. W czasie wdrażania sekwencji zadań wykorzystującej nośnik wstępnie przygotowany kreator sprawdza, czy w lokalnej pamięci podręcznej sekwencji zadań znajduje się prawidłowa zawartość. Jeśli zawartości nie można odnaleźć lub została zmieniona, kreator pobiera zawartość z punktu dystrybucji.  

##  <a name="BKMK_CreatePrestagedMedia"></a> Tworzenie wstępnie przygotowanych nośników  
 Przed utworzeniem wstępnie przygotowanego nośnika za pomocą Kreatora tworzenia nośnika sekwencji zadań sprawdź, czy są spełnione wszystkie następujące warunki:  

|Zadanie|Opis|  
|----------|-----------------|  
|Obraz rozruchowy|Należy wziąć pod uwagę następujące kwestie dotyczące obrazu rozruchowego, który będzie używany w sekwencji zadań do wdrażania systemu operacyjnego:<br /><br /> — Architektura obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.<br />-Sprawdź, czy obraz rozruchowy zawiera sterowniki sieciowe i masowej magazynu, które są wymagane do udostępnienia komputera docelowego.|  
|Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego|W ramach wstępnie przygotowanego nośnika musisz określić sekwencję zadań wdrożenia systemu operacyjnego.<br /><br /> — Aby uzyskać instrukcje dotyczące tworzenia nowej sekwencji zadań, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](../../osd/deploy-use/create-a-task-sequence-to-install-an-operating-system.md).<br />— Aby uzyskać więcej informacji o sekwencjach zadań, zobacz [Zarządzanie sekwencjami zadań do automatyzowania zadań](../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).|  
|Dystrybucja całej zawartości skojarzonej z sekwencją zadań|Całą zawartość wymaganą przez sekwencję zadań należy umieścić w co najmniej jednym punkcie dystrybucji. Zawartość ta obejmuje obraz rozruchowy, obraz systemu operacyjnego i inne skojarzone pliki. Kreator zbiera informacje z punktu dystrybucji, w którym tworzy nośnik samodzielny. Użytkownik musi mieć uprawnienia do **odczytu** biblioteki zawartości w tym punkcie dystrybucji.  Aby uzyskać więcej informacji, zobacz [informacje o bibliotece zawartości](../../core/plan-design/hierarchy/the-content-library.md).|  
|Dysk twardy na komputerze docelowym|Przed umieszczeniem wstępnie przygotowanego nośnika na dysku twardym komputera docelowego należy sformatować dysk twardy. Jeżeli dysk twardy nie będzie sformatowany w momencie stosowania nośnika, przy próbie uruchomienia komputera docelowego wystąpi błąd sekwencji zadań wdrażającej system operacyjny.|  

> [!NOTE]  
>  Kreatora tworzenia nośnika sekwencji zadań ustawia następujący warunek zmiennej sekwencji zadań na nośniku: **_SMSTSMediaType = OEMMedia**. Możesz użyć tego warunku w sekwencji zadań.  

 Aby utworzyć wstępnie przygotowany nośnik, należy wykonać czynności opisane w poniższej procedurze.  

#### <a name="to-create-prestaged-media"></a>Aby utworzyć wstępnie przygotowany nośnik  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybór typu nośnika** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz pozycję **Wstępnie przygotowany nośnik**.  

    -   Opcjonalnie, aby zezwolić na wdrożenie systemu operacyjnego bez wprowadzania danych przez użytkownika, wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego**. Po wybraniu tej opcji nie będzie wyświetlany monit o wprowadzenie przez użytkownika informacji o konfiguracji sieci lub opcjonalnych sekwencji zadań. Jednak w przypadku skonfigurowania ochrony hasłem nośnika użytkownik nadal otrzymuje monit o hasło.  

5.  Na stronie **Zarządzanie nośnikiem** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz opcję **Nośnik dynamiczny** , jeżeli chcesz zezwolić punktowi zarządzania na przekierowywanie nośnika do innego punktu zarządzania w oparciu o lokalizację klienta w granicach lokacji.  

    -   Wybierz opcję **Nośnik oparty na lokacji** , aby nośnik kontaktował się tylko z określonym punktem zarządzania.  

6.  Na stronie **Właściwości nośnika**  określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Utworzone przez**: Określ twórcę nośnika.  

    -   **Wersja**: Określ numer wersji nośnika.  

    -   **Komentarz**: Określ unikatowy opis dotyczący przeznaczenia nośnika.  

    -   **Plik nośnika**: Określ nazwę i ścieżkę plików wyjściowych. Kreator zapisuje pliki wyjściowe do tej lokalizacji. Na przykład:  **\\\servername\folder\outputfile.wim**  

7.  Na stronie **Zabezpieczenia** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz **Włącz obsługę nieznanych komputerów** pole wyboru, aby zezwolić nośnikowi na wdrażanie systemu operacyjnego na komputerze, który nie jest zarządzany przez program Configuration Manager. Nie ma rekordów tych komputerów w bazie danych programu Configuration Manager.  Aby uzyskać więcej informacji, zobacz [przygotowania do wdrożeń na nieznanych komputerach](../get-started/prepare-for-unknown-computer-deployments.md).  

    -   Zaznacz pole wyboru **Chroń nośnik hasłem** i wprowadź silne hasło w celu ochrony nośnika przed nieautoryzowanym dostępem. Po określeniu hasła użytkownik musi podać to hasło, aby używać wstępnie przygotowanego nośnika.  

        > [!IMPORTANT]  
        >  Zgodnie z najlepszymi rozwiązaniami w zakresie bezpieczeństwa, w celu ochrony wstępnie przygotowanego nośnika zawsze należy przypisać mu hasło.  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTP wybierz opcję **Utwórz certyfikat nośnika z podpisem własnym**, a następnie określ daty rozpoczęcia i wygaśnięcia certyfikatu.  

    -   W przypadku komunikacji za pośrednictwem protokołu HTTPS wybierz opcję **Importuj certyfikat PKI**, a następnie określ certyfikat do zaimportowania i jego hasło.  

         Aby uzyskać więcej informacji dotyczących tego certyfikatu klienta używanego dla obrazów rozruchowych, zobacz [wymagania dotyczące certyfikatu PKI](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Koligacja urządzenia użytkownika**: Aby obsługiwać w programie Configuration Manager Zarządzanie skoncentrowane na użytkowniku, określ sposób nośnik ma skojarzyć użytkowników z komputerem docelowym. Aby uzyskać więcej informacji o sposobie obsługi koligacji urządzenia użytkownika przez wdrożenie systemu operacyjnego, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym. Ta funkcja opiera się na akcjach w ramach sekwencji zadań, która wdraża system operacyjny. W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym podczas wdrażania systemu operacyjnego do komputera docelowego.  

        -   Wybierz opcję **Zezwalaj na koligację urządzenia użytkownika w oczekiwaniu na zatwierdzenie przez administratora** , aby nośnik automatycznie skojarzał użytkowników z komputerem docelowym po udzieleniu zatwierdzenia. Ta funkcja opiera się na zakresie sekwencji zadań, która wdraża system operacyjny. W tym scenariuszu sekwencja zadań tworzy relację między określonymi użytkownikami a komputerem docelowym, lecz przed wdrożeniem systemu operacyjnego oczekuje na zatwierdzenie przez użytkownika administracyjnego.  

        -   Wybierz opcję **Nie zezwalaj na koligację urządzenia użytkownika** , jeżeli nie chcesz, aby nośnik skojarzał użytkowników z komputerem docelowym. W tym scenariuszu sekwencja zadań nie skojarza użytkowników z komputerem docelowym podczas wdrażania systemu operacyjnego.  

8.  Na stronie **Sekwencja zadań** określ sekwencję zadań, która zostanie uruchomiona na komputerze docelowym. Zawartość, do której odwołuje się sekwencja zadań, jest wyświetlona w obszarze **Ta sekwencja zadań odwołuje się do następującej zawartości**. Sprawdź zawartość i kliknij przycisk **Dalej**.  

9. Na stronie **Obraz rozruchowy** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Architektura dystrybuowanego obrazu rozruchowego musi być zgodna z architekturą komputera docelowego. Na przykład komputer docelowy z procesorem x64 obsługuje rozruch i uruchamianie obrazów rozruchowych x86 lub x64. Jednak komputer docelowy z procesorem x86 obsługuje tylko rozruch i uruchamianie obrazów rozruchowych x86.  

    -   W polu **Obraz rozruchowy** wybierz obraz rozruchowy do uruchomienia komputera docelowego. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

    -   W polu **Punkt dystrybucji** określ punkt dystrybucji, w którym znajduje się obraz rozruchowy. Kreator pobiera obraz rozruchowy z punktu dystrybucji i zapisuje go na nośniku.  

        > [!NOTE]  
        >  Użytkownik musi mieć uprawnienia typu **Odczyt** do biblioteki zawartości w punkcie dystrybucji. Aby uzyskać więcej informacji, zobacz [informacje o bibliotece zawartości](../../core/plan-design/hierarchy/the-content-library.md).  

    -   W przypadku wybrania na stronie **Zarządzanie nośnikiem** kreatora opcji **Nośnik oparty na lokacji** , w polu **Punkt zarządzania** określ punkt zarządzania z lokacji głównej.  

    -   W przypadku wybrania na stronie **Zarządzanie nośnikiem** kreatora opcji **Nośnik dynamiczny** , w polu **Skojarzone punkty zarządzania** określ używane punkty zarządzania lokacji głównej oraz kolejność wstępnej komunikacji według priorytetów.  

10. Na stronie **Obrazy** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Pakiet obrazów** określ obraz systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

    -   Jeżeli pakiet zawiera kilka obrazów systemu operacyjnego, w polu **Indeks obrazu** określ obraz do wdrożenia.  

    -   W polu **Punkt dystrybucji** określ punkt dystrybucji, w którym znajduje się pakiet obrazu systemu operacyjnego. Kreator pobiera obraz systemu operacyjnego z punktu dystrybucji i zapisuje go na nośniku.  

11. Na stronie **Dostosowywanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Określ zmienne używane przez sekwencję zadań do wdrożenia systemu operacyjnego.  

    -   Określ dowolne polecenia przeduruchomieniowe, które chcesz uruchomić przed rozpoczęciem sekwencji zadań. Polecenia przeduruchomieniowe są skryptami lub plikami wykonywalnymi, które mogą prowadzić interakcję z użytkownikiem w środowisku Windows PE przed uruchomieniem sekwencji zadań w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji dotyczących poleceń przeduruchomieniowych nośnika, zobacz [polecenia dla nośnika sekwencji zadań Przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Podczas tworzenia nośnika sekwencji zadań sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

12. Ukończ pracę kreatora.  

## <a name="next-steps"></a>Następne kroki
[Scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw](scenarios-to-deploy-enterprise-operating-systems.md)
