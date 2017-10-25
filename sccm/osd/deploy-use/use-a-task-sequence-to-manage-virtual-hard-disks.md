---
title: "Zarządzanie wirtualnymi dyskami twardymi za pomocą sekwencji zadań | Dokumentacja firmy Microsoft"
description: "Tworzenie i modyfikowanie dysku VHD, dodawać aplikacje i aktualizacje oprogramowania oraz publikować dyski VHD do System Center Virtual Machine Manager (VMM) z programu Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0212b023-804a-4f84-b880-7a59cdb49c67
caps.latest.revision: "5"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: f77af4b8fcb193ed44511c0e5eea7290f55dbbf8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="use-a-task-sequence-to-manage-virtual-hard-disks-in-system-center-configuration-manager"></a>Zarządzanie wirtualnymi dyskami twardymi w programie System Center Configuration Manager za pomocą sekwencji zadań

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie System Center Configuration Manager, można zarządzać wirtualnymi dyskami twardymi (VHD) oraz integrować wirtualne dyski twarde, tworzonych w centrum danych z konsoli programu Configuration Manager. W szczególności można utworzyć i modyfikować dyski VHD, dodawać aplikacje i aktualizacje oprogramowania do dysku VHD i publikować dyski VHD do System Center Virtual Machine Manager (VMM) z konsoli programu Configuration Manager.  

 Następujące sekcje służą do zarządzania dyskami VHD w programie Configuration Manager.

## <a name="prerequisites"></a>Wymagania wstępne  
 Przed rozpoczęciem sprawdź następujące wymagania wstępne:  

-   Na komputerze używanym do zarządzania dyskami VHD musi być uruchomiony jeden z następujących systemów operacyjnych:  

    -   Windows 8.1 x64  

    -   Windows 8 x64  

    -   Windows Server 2008 R2  

    -   Windows Server 2012  

    -   Windows Server 2012 R2  

-   Wirtualizacja musi być włączona w systemie BIOS i funkcji Hyper-V musi być zainstalowany na komputerze z poziomu konsoli programu Configuration Manager do zarządzania dyskami VHD. Ponadto zaleca się zainstalowanie narzędzi do zarządzania funkcją Hyper-V umożliwiających testowanie i rozwiązywanie problemów z wirtualnymi dyskami twardymi. Narzędzia do zarządzania funkcją Hyper-V należy zainstalować na przykład w celu monitorowania postępu sekwencji zadań w funkcji Hyper-V przy użyciu pliku smsts.log. Więcej informacji na temat wymagań dotyczących funkcji Hyper-V znajduje się w temacie [Wymagania wstępne instalacji funkcji Hyper-V](http://technet.microsoft.com/library/cc731898.aspx).  

    > [!IMPORTANT]  
    >  Proces tworzenia dysku VHD wiąże się ze zużyciem pamięci i czasu procesora. W związku z tym zaleca się Zarządzanie dyskami VHD z poziomu konsoli programu Configuration Manager, który nie jest zainstalowany na serwerze lokacji.  

-   W przypadku zarządzania dyskami VHD za pomocą komputera sterowanego zdalnie z serwera lokacji, serwer ten musi mieć uprawnienie dostępu **Zapis** w folderze zawierającym plik VHD.  

-   Sprawdź, czy na komputerze używanym do zarządzania dyskami VHD jest wystarczająca ilość wolnego miejsca na dysku. Wymagania dotyczące miejsca na dysku twardym w ramach dysku VHD różnią się w zależności od zainstalowanych aplikacji i systemu operacyjnego.  

-   Sprawdź, czy na komputerze używanym do zarządzania dyskami VHD jest wystarczająca ilość pamięci. Podczas procesu tworzenia dysku VHD maszyna wirtualna zużywa 2 GB pamięci.  

-   Zainstaluj konsolę programu System Center Virtual Machine Manager (VMM) na komputerze, z którego dysk VHD zostanie przekazany do programu VMM. Konsolę programu VMM można zainstalować na osobnym komputerze używanym do zarządzania dyskami VHD, dzięki czemu do zaimportowania dysku VHD do programu VMM nie trzeba instalować funkcji Hyper-V.  

    > [!NOTE]  
    >  Po otwarciu konsoli programu Configuration Manager należy zainstalować konsolę programu VMM, należy ponownie uruchomić konsolę programu Configuration Manager po ukończeniu instalacji konsoli programu VMM. W przeciwnym razie programu Configuration Manager zostanie nie mógł nawiązać serwerze zarządzania programu VMM w celu przekazania dysku VHD.  

##  <a name="BKMK_CreateVHDSteps"></a> Procedura tworzenia dysku VHD  
 Aby utworzyć dysk VHD, należy utworzyć sekwencję zadań obejmującą wymagane do tego celu czynności, a następnie użyć jej w Kreatorze tworzenia wirtualnych dysków twardych. W poniższych sekcjach opisano procedurę tworzenia dysku VHD.  

###  <a name="BKMK_CreateTS"></a> Tworzenie sekwencji zadań w ramach dysku VHD  
 Należy utworzyć sekwencję zadań obejmującą czynności w celu utworzenia dysku VHD. W Kreatorze tworzenia sekwencji zadań jest dostępna opcja **Zainstaluj istniejący pakiet obrazów na wirtualnym dysku twardym** , dzięki której można utworzyć czynności w celu utworzenia dysku VHD. Kreator dodaje na przykład wykonać następujące czynności: Uruchom ponownie w środowisku Windows PE, Formatuj dysk i podziel go na partycje, Zastosuj system operacyjne i Wyłącz komputer. Dysku VHD nie można utworzyć w pełnej wersji systemu operacyjnego. Ponadto programu Configuration Manager musi poczekać na maszyna wirtualna jest zamknięta, przed ukończeniem pakietu. Domyślnie kreator oczekuje 5 minut, a następnie wyłącza maszynę wirtualną. Po utworzeniu sekwencji zadań można w razie potrzeby dodać więcej czynności.  

> [!IMPORTANT]  
>  Poniższa procedura dotyczy tworzenia sekwencji zadań przy użyciu opcji **Zainstaluj istniejący pakiet obrazów na wirtualnym dysku twardym** , która automatycznie dodaje czynności wymagane do pomyślnego utworzenia dysku VHD. W przypadku użycia istniejącej sekwencji zadań lub ręcznego tworzenia sekwencji zadań należy pamiętać, aby na końcu sekwencji zadań dodać czynność Wyłącz komputer. W przeciwnym razie tymczasowa maszyna wirtualna nie zostanie usunięta i nie będzie można ukończyć procesu tworzenia dysku VHD. Kreator ukończy jednak działanie i zgłosi powodzenie operacji.  

 Aby utworzyć sekwencję zadań tworzenia dysku VHD, wykonaj czynności opisane w następującej procedurze:  

#### <a name="to-create-the-task-sequence-to-create-the-vhd"></a>Aby utworzyć sekwencję zadań tworzenia dysku VHD  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** kliknij opcję **Zainstaluj istniejący pakiet obrazów na wirtualnym dysk twardym**, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis elementu**: Określ opis sekwencji zadań.  

    -   **Obraz rozruchowy**: Określ obraz rozruchowy, który instaluje system operacyjny na komputerze docelowym. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

6.  Na stronie **Instalowanie systemu Windows** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Pakiet obrazów**: Określ pakiet, który zawiera obraz systemu operacyjnego do zainstalowania.  

    -   **Obraz**: Jeśli pakiet obrazu systemu operacyjnego zawiera wiele obrazów, określ indeks obrazu systemu operacyjnego do zainstalowania.  

    -   **Klucz produktu**: Określ klucz produktu systemu operacyjnego do zainstalowania. Możesz określić zakodowane klucze licencji zbiorczych oraz standardowe klucze produktów. W przypadku użycia niezakodowanego klucza produktu poszczególne grupy 5 znaków muszą być oddzielone kreskami (-). Na przykład: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Tryb licencjonowania serwera**: Określ, czy serwer licencji jest **na stanowisko**, **na serwer**, lub które nie licencji. W przypadku wybrania licencji serwera **Na serwer**określ również maksymalną liczbę połączeń serwera.  

    -   Określ, w jaki sposób ma być obsługiwane konto administratora używane podczas wdrażania obrazu systemu operacyjnego.  

        -   **Losowo Generuj hasło administratora lokalnego i Wyłącz konto na wszystkich obsługiwanych platformach (zalecane)**: Użyj tego ustawienia, aby Kreator losowo utworzył hasło do konta administratora lokalnego i wyłączył to konto po wdrożeniu obrazu systemu operacyjnego.  

        -   **Włącz konto i określ hasło administratora lokalnego**: Użyj tego ustawienia, aby użyć konkretnego hasła dla konta administratora lokalnego na wszystkich komputerach z wdrożonym obrazem systemu operacyjnego.  

7.  Na stronie **Konfigurowanie sieci** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Przyłącz do grupy roboczej**: Określ, czy dodać komputer docelowy do grupy roboczej.  

    -   **Przyłącz do domeny**: Określ, czy dodać komputer docelowy do domeny. W polu **Domena**określ nazwę domeny.  

        > [!IMPORTANT]  
        >  W lesie lokalnym możesz przeglądać w poszukiwaniu domen, lecz w przypadku lasu zdalnego musisz określić nazwę domeny.  

         Możesz również określić jednostkę organizacyjną (OU). To jest ustawienie opcjonalne określające nazwę wyróżniającą LDAP X.500 jednostki OU, w której ma zostać utworzone konto komputera, jeżeli jeszcze nie istnieje.  

    -   **Konto**: Określ nazwę użytkownika i hasło dla konta, które ma uprawnienia do dołączenia do określonej domeny. Przykład: *domena\użytkownik* lub *%zmienna%*.  

8.  Na **Instalowanie programu Configuration Manager** Określ pakiet klienta programu Configuration Manager można zainstalować na komputerze docelowym, a następnie kliknij przycisk **dalej**.  

9. Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

10. Ukończ pracę kreatora.  

###  <a name="BKMK_CreateVHD"></a> Tworzenie dysku VHD  
 Po utworzeniu sekwencji zadań dla dysku VHD utwórz dysk VHD za pomocą Kreatora tworzenia wirtualnych dysków twardych.  

> [!IMPORTANT]  
>  Przed rozpoczęciem tej procedury sprawdź, czy spełniono wymania wstępne wymienione na początku tego tematu.  

 Aby utworzyć dysk VHD, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-a-vhd"></a>Aby utworzyć dysk VHD  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Wirtualne dyski twarde**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz wirtualny dysk twardy** , aby uruchomić Kreatora tworzenia wirtualnych dysków twardych.  

    > [!NOTE]  
    >  Funkcji Hyper-V musi być zainstalowany na komputer z uruchomioną konsolą programu Configuration Manager, z którego zarządzania dyskami VHD lub **Utwórz wirtualny dysk twardy** opcja nie jest włączona. Więcej informacji na temat wymagań dotyczących funkcji Hyper-V znajduje się w temacie [Wymagania wstępne instalacji funkcji Hyper-V](http://technet.microsoft.com/library/cc731898.aspx).  

    > [!TIP]  
    >  Aby organizować dyski VHD, utwórz nowy folder lub wybierz istniejący folder w węźle **Wirtualne dyski twarde** , a następnie z poziomu danego folderu kliknij przycisk **Utwórz wirtualny dysk twardy** .  

4.  Na stronie **Ogólne** określ następujące informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa**: Określ unikatową nazwę dysku VHD.  

    -   **Wersja**: Określ numer wersji dysku VHD. To jest ustawienie opcjonalne.  

    -   **Komentarz**: Określ opis dysku VHD.  

    -   **Ścieżka**: Określ ścieżkę i nazwę pliku, dla których kreator utworzy plik VHD.  

         Należy wprowadzić prawidłową ścieżkę sieciową w formacie UNC. Na przykład:  **\\\servername\\< nazwa_udziału\>\\< nazwa pliku\>VHD**.  

        > [!WARNING]  
        >  Menedżer konfiguracji musi mieć **zapisu** dostęp do uprawnień do określonej ścieżki do utworzenia dysku VHD. W przypadku programu Configuration Manager nie może uzyskać dostępu do ścieżki, rejestruje skojarzony błąd w pliku distmgr.log na serwerze lokacji.  

5.  Na stronie **Sekwencja zadań** określ sekwencję zadań wybraną w poprzedniej sekcji, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Punkty dystrybucji** wybierz co najmniej jeden punkt dystrybucji z zawartością wymaganą przez sekwencję zadań, a następnie kliknij przycisk **Dalej**.  

7.  Na stronie **Dostosowywanie** kliknij przycisk **Dalej**. Proces tworzenia dysku VHD zignoruje wszystkie ustawienia określone na tej stronie.  

8.  Sprawdź ustawienia i kliknij przycisk **Dalej**. Kreator utworzy dysk VHD.  

    > [!TIP]  
    >  Czas wymagany do ukończenia procesu tworzenia dysku VHD może się różnić. Postęp procesu wykonywanego przez kreatora można monitorować przy użyciu poniższych plików dzienników. Domyślnie dzienniki znajdują się na komputerze z konsolą programu Configuration Manager w lokalizacji %*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: Kreator zapisuje informacje w tym dzienniku podczas tworzenia nośnika sekwencji zadań. Ten plik dziennika umożliwia monitorowanie postępu tworzenia nośnika autonomicznego przez kreatora.  
    > -   **DeployToVHD.log**: Kreator zapisuje informacje w tym dzienniku podczas procesu tworzenia dysku VHD. Ten plik dziennika umożliwia monitorowanie postępu wszystkich czynności kreatora po utworzeniu nośnika autonomicznego.  
    >   
    >  Ponadto aby zobaczyć uruchomioną sekwencję zadań, po rozpoczęciu instalacji systemu operacyjnego można otworzyć Menedżera funkcji Hyper-V (jeżeli na komputerze zainstalowano narzędzia do zarządzania funkcją Hyper-V) i nawiązać połączenie z tymczasową maszyną wirtualną utworzoną przez kreatora. Postęp sekwencji zadań można monitorować z poziomu maszyny wirtualnej za pomocą pliku smsts.log. Ten plik dziennika umożliwia rozwiązywanie problemów związanych z ukończeniem poszczególnych czynności sekwencji zadań. Plik smsts.log znajduje się w x: \windows\temp\smstslog\smsts.log przed sformatowaniem dysku twardego i c:\\_SMSTaskSequence\Logs\Smstslog\ po jego sformatowaniu. Po ukończeniu sekwencji zadań maszyna wirtualna zostanie wyłączona po upływie 5 minut (domyślnie) i usunięta.  

 Gdy programu Configuration Manager utworzy wirtualny dysk twardy, znajduje się w **wirtualne dyski twarde** węzeł w konsoli programu Configuration Manager w obszarze **wdrożenia systemu operacyjnego** w węźle **Biblioteka oprogramowania** obszaru roboczego.  

> [!NOTE]  
>  Configuration Manager pobiera rozmiar dysku VHD, nawiązując połączenie z lokalizacją źródłową wirtualnego dysku twardego. Jeśli programu Configuration Manager nie może uzyskać dostępu do pliku VHD, **0** jest wyświetlany w **rozmiar (KB)** kolumny dysku VHD.  

##  <a name="BKMK_ModifyVHDSteps"></a> Procedura modyfikowania istniejącego dysku VHD  
 Aby zmodyfikować dysk VHD, należy utworzyć sekwencję zadań obejmującą wymagane do tego celu czynności. Tę sekwencję zadań należy następnie wybrać w Kreatorze modyfikowania wirtualnych dysków twardych. Kreator dołącza dysk VHD do maszyny wirtualnej, uruchamia na tym dysku sekwencję zadań, a następnie aktualizuje plik VHD. W poniższych sekcjach opisano procedurę modyfikowania dysku VHD.  

###  <a name="BKMK_ModifyTS"></a> Tworzenie sekwencji zadań w celu zmodyfikowania dysku VHD  
 Aby zmodyfikować istniejący dysk VHD, w pierwszej kolejności należy utworzyć sekwencję zadań. Wybierz tylko czynności wymagane do zmodyfikowania sekwencji zadań. Na przykład aby dodać aplikację do dysku VHD, utwórz niestandardową sekwencję zadań, a następnie dodaj tylko czynność Zainstaluj aplikację.  

 Aby utworzyć sekwencję zadań modyfikowania dysku VHD, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-a-custom-task-sequence-to-modify-the-vhd"></a>Aby utworzyć niestandardową sekwencję zadań w celu zmodyfikowania dysku VHD  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** wybierz opcję **Utwórz nową niestandardową sekwencję zadań**, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis elementu**: Określ opis sekwencji zadań.  

    -   **Obraz rozruchowy**: Określ obraz rozruchowy, który instaluje system operacyjny na komputerze docelowym. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

6.  Ukończ pracę kreatora.  

 Aby dodać czynności do niestandardowej sekwencji zadań, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-add-task-sequence-steps-to-the-custom-task-sequence"></a>Aby dodać czynności do niestandardowej sekwencji zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, kliknij przycisk **Sekwencje zadań**, a następnie wybierz niestandardową sekwencję zadań utworzoną w poprzedniej procedurze.  

3.  Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Edytuj** , aby uruchomić edytora sekwencji zadań.  

4.  Dodaj czynności sekwencji zadań wymagane do zmodyfikowania dysku VHD.  

5.  Aby zakończyć działanie edytora sekwencji zadań, kliknij przycisk **OK** .  

###  <a name="BKMK_ModifyVHD"></a> Modyfikowanie dysku VHD  
 Po utworzeniu sekwencji zadań dla dysku VHD zmodyfikuj dysk VHD za pomocą Kreatora modyfikowania wirtualnych dysków twardych.  

 Aby zmodyfikować dysk VHD, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-modify-a-vhd"></a>Aby zmodyfikować dysk VHD  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, kliknij przycisk **Wirtualne dysku twarde**, a następnie wybierz dysk VHD do zmodyfikowania.  

3.  Na karcie **Narzędzia główne** w grupie **Wirtualny dysk twardy** kliknij przycisk **Modyfikuj wirtualny dysk twardy** , aby uruchomić Kreatora modyfikowania wirtualnych dysków twardych.  

    > [!NOTE]  
    >  Funkcji Hyper-V musi być zainstalowany na komputer z uruchomioną konsolą programu Configuration Manager, z którego zarządzania dyskami VHD lub **Modyfikuj wirtualny dysk twardy** opcja nie jest włączona. Więcej informacji na temat wymagań dotyczących funkcji Hyper-V znajduje się w temacie [Wymagania wstępne instalacji funkcji Hyper-V](http://technet.microsoft.com/library/cc731898.aspx).  

4.  Na stronie **Ogólne** potwierdź następujące ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa**: Określa unikatową nazwę dysku VHD.  

    -   **Wersja**: Określa numer wersji dysku VHD. To jest ustawienie opcjonalne.  

    -   **Komentarz**: Określa opis dysku VHD.  

    -   **Ścieżka**: Określa nazwę i ścieżka pliku, w którym znajduje się plik VHD. Nie można modyfikować tego ustawienia.  

        > [!WARNING]  
        >  Menedżer konfiguracji musi mieć **zapisu** dostęp do uprawnień do określonej ścieżki do utworzenia dysku VHD. W przypadku programu Configuration Manager nie może uzyskać dostępu do ścieżki, rejestruje skojarzony błąd w pliku distmgr.log na serwerze lokacji.  

5.  Na stronie **Sekwencja zadań** określ niestandardową sekwencję zadań utworzoną w poprzedniej sekcji, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Punkty dystrybucji** wybierz co najmniej jeden punkt dystrybucji z zawartością wymaganą przez sekwencję zadań, a następnie kliknij przycisk **Dalej**.  

7.  Na stronie **Dostosowywanie** kliknij przycisk **Dalej**. Proces modyfikowania dysku VHD zignoruje wszystkie ustawienia określone na tej stronie.  

8.  Sprawdź ustawienia i kliknij przycisk **Dalej**. Kreator utworzy zmodyfikowany dysk VHD.  

    > [!TIP]  
    >  Czas wymagany do ukończenia procesu modyfikowania dysku VHD może się różnić. Postęp procesu wykonywanego przez kreatora można monitorować przy użyciu poniższych plików dzienników. Domyślnie dzienniki znajdują się na komputerze z konsolą programu Configuration Manager w lokalizacji %*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: Kreator zapisuje informacje w tym dzienniku podczas tworzenia nośnika sekwencji zadań. Ten plik dziennika umożliwia monitorowanie postępu tworzenia nośnika autonomicznego przez kreatora.  
    > -   **DeployToVHD.log**: Kreator zapisuje informacje w tym dzienniku podczas procesu modyfikowania dysku VHD. Ten plik dziennika umożliwia monitorowanie postępu wszystkich czynności kreatora po utworzeniu nośnika autonomicznego.  
    >   
    >  Ponadto, aby zobaczyć uruchomioną sekwencję zadań, można otworzyć Menedżera funkcji Hyper-V (jeżeli na komputerze zainstalowano narzędzia do zarządzania funkcją Hyper-V) i nawiązać połączenie z tymczasową maszyną wirtualną utworzoną przez kreatora. Postęp sekwencji zadań można monitorować z poziomu maszyny wirtualnej za pomocą pliku smsts.log. Ten plik dziennika umożliwia rozwiązywanie problemów związanych z ukończeniem poszczególnych czynności sekwencji zadań. Plik smsts.log znajduje się w x: \windows\temp\smstslog\smsts.log przed sformatowaniem dysku twardego i c:\\_SMSTaskSequence\Logs\Smstslog\ po jego sformatowaniu. Po ukończeniu sekwencji zadań maszyna wirtualna zostanie wyłączona po upływie 5 minut (domyślnie) i usunięta.  

##  <a name="BKMK_ApplyUpdates"></a> Stosowanie aktualizacji oprogramowania do dysku VHD  
 Okresowo są wydawane nowe aktualizacje oprogramowania, które mają zastosowanie do systemu operacyjnego znajdującego się na używanym dysku VHD. Odpowiednie aktualizacje oprogramowania można stosować do dysku VHD zgodnie z zaplanowanym harmonogramem. Zgodnie z harmonogramem określonym przez użytkownika programu Configuration Manager stosuje wybrane aktualizacje oprogramowania do dysku VHD.  

 Informacje o dysku VHD, w tym informacje o aktualizacjach oprogramowania zastosowanych podczas utworzenia dysku VHD, są przechowywane w bazie danych lokacji. W bazie danych lokacji są także przechowywane informacje o aktualizacjach oprogramowania zastosowanych do dysku VHD od chwili jego pierwszego utworzenia. Po uruchomieniu kreatora w celu zastosowania aktualizacji oprogramowania do dysku VHD kreator pobiera listę dostępnych do wyboru aktualizacji, które nie zostały jeszcze zastosowane do dysku VHD.  

 Możesz wybrać **Kontynuuj przy błędzie** wybrane ustawienie dla programu Configuration Manager, aby kontynuować stosowanie oprogramowania aktualizuje nawet wtedy, gdy występuje błąd stosowanie jednej lub więcej oprogramowania aktualizacjami.  

> [!NOTE]  
>  Poszczególne aktualizacje oprogramowania są kopiowane z biblioteki zawartości znajdującej się na serwerze lokacji.  

 Aby zastosować aktualizację oprogramowania do dysku VHD, należy wykonać poniższą procedurę.  

#### <a name="to-apply-software-updates-to-a-vhd"></a>Aby zastosować aktualizację oprogramowania do dysku VHD  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Wirtualne dyski twarde**.  

3.  Wybierz dysk VHD, do którego chcesz zastosować aktualizacje oprogramowania.  

4.  Na karcie **Narzędzia główne** w grupie **Wirtualny dysk twardy** kliknij polecenie **Zaplanuj aktualizacje** , aby uruchomić kreatora.  

5.  Na stronie **Wybierz aktualizacje** wybierz aktualizacje oprogramowania, które mają zostać zastosowane do dysku VHD, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Ustawianie harmonogramu** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Harmonogram**: Określ harmonogram stosowania aktualizacji oprogramowania do dysku VHD.  

    2.  **Kontynuuj przy błędzie**: Wybierz tę opcję, aby kontynuować stosowanie aktualizacji oprogramowania do obrazu nawet wtedy, gdy występuje błąd.  

7.  Na stronie **Podsumowanie** sprawdź informacje, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Ukończenie** sprawdź, czy aktualizacje oprogramowania zostały pomyślnie zastosowane do obrazu systemu operacyjnego.  

##  <a name="BKMK_ImportToVMM"></a> Importowanie dysku VHD do Menedżera maszyny wirtualnej dla programu System Center  
 Program System Center VMM to rozwiązanie zarządzania dla zwirtualizowanego centrum danych, które pozwala konfigurować hosty, funkcje sieciowe i magazyny wirtualizacji w ramach tworzenia i wdrażania usługi i maszyn wirtualnych w utworzonych uprzednio prywatnych chmurach. Po utworzeniu dysku VHD w programie Configuration Manager, można importować i zarządzanie dysk VHD za pomocą programu VMM.  

> [!TIP]  
>  Przed przekazaniem dysku VHD do programu VMM sprawdź, czy konsola programu VMM pomyślnie nawiązuje połączenie z serwerem zarządzania VMM.  

 Aby zaimportować dysk VHD do programu VMM, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-import-a-vhd-to-vmm"></a>Aby zaimportować dysk VHD do programu VMM  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Wirtualne dyski twarde**.  

3.  Na karcie **Narzędzia główne** w grupie **Wirtualny dysk twardy** kliknij polecenie **Przekaż do menadżera maszyny wirtualnej** , aby uruchomić Kreatora menedżera maszyny wirtualnej.  

4.  Na stronie **Ogólne** skonfiguruj następujące ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa serwera VMM**: Określ nazwę FQDN komputera, na którym jest zainstalowany serwer zarządzania programu VMM. Kreator połączy się z serwerem zarządzania VMM, aby pobrać z serwera udziały biblioteki.  

    -   **Udział biblioteki VMM**: Określ udział biblioteki VMM z listy rozwijanej.  

    -   **Użyj nieszyfrowanego transferu**: Wybierz to ustawienie, aby przesłać plik VHD na serwer zarządzania VMM bez szyfrowania.  

5.  Na stronie Podsumowanie sprawdź ustawienia, a następnie zakończ pracę kreatora. Czas potrzebny na przekazanie dysku VHD zależy od rozmiaru pliku VHD oraz od przepustowości sieci do serwera zarządzania VMM.  
