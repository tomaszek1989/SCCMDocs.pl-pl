1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **aktualizacji oprogramowania**.  

2.  Wybierz aktualizację oprogramowania do pobrania przy użyciu jednej z następujących metod:  

    -   Wybierz co najmniej jedną grupę aktualizacji oprogramowania z listy **Grupy aktualizacji oprogramowania**, a następnie na karcie **Narzędzia główne** w grupie **Grupa aktualizacji** kliknij przycisk **Pobierz**.  

    -   Wybierz co najmniej jedną aktualizację oprogramowania z listy **Wszystkie aktualizacje oprogramowania**, a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pobierz**.  

        > [!NOTE]  
        >  Na **wszystkie aktualizacje oprogramowania** węzła, programu Configuration Manager wyświetla wyłącznie aktualizacje oprogramowania z **krytyczny** i **zabezpieczeń** klasyfikacji, które zostały wydane w ciągu ostatnich 30 dni.  

        > [!TIP]  
        >  Kliknij przycisk **Dodaj kryteria** , aby filtrować aktualizacje oprogramowania wyświetlane w węźle **Wszystkie aktualizacje oprogramowania** , zapisz często używane kryteria wyszukiwania, a następnie zarządzaj zapisanymi wyszukiwaniami na karcie **Wyszukiwanie** .  

         Otworzy się **Kreator pobierania aktualizacji oprogramowania** .  

3.  Na stronie **Pakiet wdrożeniowy** skonfiguruj następujące ustawienia:  

    1.  **Wybierz pakiet wdrożeniowy**: Wybierz to ustawienie umożliwia wybranie istniejącego pakietu wdrożeniowego aktualizacji oprogramowania, które są we wdrożeniu.  

        > [!NOTE]  
        >  Aktualizacje oprogramowania pobrane już do wybranego pakietu wdrożeniowego nie zostaną pobrane ponownie.  

    2.  **Utwórz nowy pakiet wdrożeniowy**: Wybierz to ustawienie, aby utworzyć nowy pakiet wdrażania dla aktualizacji oprogramowania we wdrożeniu. Skonfiguruj następujące ustawienia:  

        -   **Nazwa**: Określa nazwę pakietu wdrożeniowego. Pakiet musi mieć unikatową nazwę stanowiącą zwięzły opis jego zawartości.  Maksymalna długość to 50 znaków.  

        -   **Opis elementu**: Określa opis pakietu wdrożeniowego. Opis pakietu zawiera informacje na temat jego zawartości, zaś jego maksymalna długość to 127 znaków.  

        -   **Źródło pakietu**: Określa lokalizację plików źródłowych aktualizacji oprogramowania. Wpisz ścieżkę sieciową do lokalizacji źródłowej, na przykład **\\\serwer\nazwa_udziału\ścieżka**, lub kliknij przycisk **Przeglądaj** , aby znaleźć lokalizację sieciową. Przed kontynuowaniem do następnej strony należy utworzyć folder udostępniony dla plików źródłowych pakietu wdrożeniowego.  

            > [!NOTE]  
            >  Określona lokalizacja źródłowa pakietu wdrożeniowego nie może być używana przez inny pakiet wdrożeniowy oprogramowania.  

            > [!IMPORTANT]  
            >  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik, który uruchamia kreatora w celu pobrania aktualizacji oprogramowania, muszą mieć uprawnienia systemu plików NTFS **Zapis** w lokalizacji pobierania. Aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania przez osoby atakujące, należy odpowiednio ograniczyć dostęp do lokalizacji pobierania.  

            > [!IMPORTANT]  
            >  Można zmienić lokalizację źródłową pakietu w oknie właściwości pakietu wdrażania po programu Configuration Manager tworzy pakietu wdrożeniowego. Jednak w celu wykonania tej czynności należy najpierw skopiować zawartość z pierwotnego źródła pakietu do nowej lokalizacji źródłowej pakietu.  

     Kliknij przycisk **Dalej**.  

4.  Na **punktów dystrybucji** określ punkty dystrybucji lub grupy punktów dystrybucji, które będą obsługiwać pliki aktualizacji oprogramowania, a następnie kliknij pozycję **dalej**. Więcej informacji dotyczących punktów dystrybucji znajduje się w sekcji [Konfiguracje punktów dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

    > [!NOTE]  
    >  Strona Punkty Dystrybucji jest dostępna wyłącznie w przypadku utworzenia nowego pakietu wdrożeniowego aktualizacji oprogramowania.  

6.  Na **ustawienia dystrybucji** określ następujące ustawienia:  

    -   **Priorytet dystrybucji**: To ustawienie umożliwia określenie priorytetu dystrybucji pakietu wdrożeniowego. Priorytet dystrybucji ma zastosowanie, gdy pakiet wdrożeniowy zostanie wysłany do punktów dystrybucji w lokacjach podrzędnych Pakiety wdrożeniowe są wysyłane w kolejności priorytetu: **Wysoka**, **średni**, lub **małej**. Pakiety o identycznych priorytetach są wysyłane w kolejności ich utworzenia. Jeżeli nie występuje zaległość, przetwarzanie pakietu rozpocznie się natychmiast niezależnie od jego priorytetu. Domyślnie pakiety są wysyłane przy użyciu priorytetu **Średni** .  

    -   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**: To ustawienie umożliwia włączenie dystrybucji zawartości na żądanie do preferowanych punktów dystrybucji. Po włączeniu tego ustawienia punkt zarządzania utworzy wyzwalacz nakazujący menedżerowi dystrybucji rozesłanie zawartości do wszystkich preferowanych punktów dystrybucji, gdy klient zażąda zawartości pakietu niedostępnej w żadnym z preferowanych punktów dystrybucji. Aby uzyskać więcej informacji na temat preferowanych punktów dystrybucji i zawartości na żądanie, zapoznaj się z tematem [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

    -   **Wstępnie przygotowane ustawienia punktu dystrybucji**: Użyj tego ustawienia, aby określić sposób dystrybucji zawartości do wstępnie przygotowanych punktów dystrybucji. Wybierz jedną z następujących opcji:  

        -   **Automatycznie Pobierz zawartość po przypisaniu pakietów do punktów dystrybucji**: To ustawienie umożliwia zignorowanie przygotowanych ustawień i dystrybucję zawartości do punktu dystrybucji.  

        -   **Pobierz tylko zmiany zawartości w punkcie dystrybucji**: To ustawienie umożliwia wstępne przygotowanie oryginalnej zawartości do punktu dystrybucji, a następnie dystrybucję zmian zawartości do punktu dystrybucji.  

        -   **Ręcznie skopiuj zawartość tego pakietu do punktu dystrybucji**: To ustawienie umożliwia wstępne przygotowanie zawartości w punkcie dystrybucji. To jest ustawienie domyślne.  

         Aby uzyskać więcej informacji o wstępnym przygotowywaniu zawartości dla punktów dystrybucji, zobacz [Używanie wstępnie przygotowanej zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Kliknij przycisk **Dalej**.  

6.  Na **Lokalizacja pobierania** Określ lokalizację, używanego do pobrania plików źródłowych aktualizacji oprogramowania programu Configuration Manager. W miarę potrzeby użyj następujących opcji:  

    -   **Pobierz aktualizacje oprogramowania z Internetu**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z lokalizacji w Internecie. To jest ustawienie domyślne.  

    -   **Pobierz aktualizacje oprogramowania z lokalizacji w sieci lokalnej**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z folderu lokalnego lub udostępnionego folderu sieciowego. Użyj tego ustawienia, jeśli komputer, na którym uruchamiasz kreatora, nie ma dostępu do Internetu.  

        > [!NOTE]  
        >  Używając tego oprogramowania, możesz pobrać aktualizacje oprogramowania z dowolnego komputera z dostępem do Internetu, a następnie załadować aktualizacje oprogramowania do lokalizacji w sieci lokalnej dostępnej dla komputera, na których uruchamiasz kreatora.  

     Kliknij przycisk **Dalej**.  

7.  Na **wybór języka** Określ języki, dla których wybrane aktualizacje oprogramowania mają być pobierane, a następnie kliknij pozycję **dalej**. Configuration Manager pobiera aktualizacje oprogramowania tylko wtedy, gdy są one dostępne w wybranych językach. Aktualizacje oprogramowania bez określonego języka będą pobierane zawsze.  

8. Na **Podsumowanie** , sprawdź ustawienia wybrane w kreatorze, a następnie kliknij przycisk **dalej** oprogramowanie do pobrania aktualizacji.  

9. Na **zakończenia** upewnij się, że aktualizacje oprogramowania zostały pobrane pomyślnie, a następnie kliknij **Zamknij**.  
