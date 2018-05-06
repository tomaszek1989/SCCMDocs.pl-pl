---
title: Rozwiązywanie problemów z klientem usługi Windows Defender lub program Endpoint Protection
titleSuffix: Configuration Manager
description: Dowiedz się, jak rozwiązywanie problemów z usługi Windows Defender oraz programu Endpoint Protection.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: d837253e-fcc2-422a-9e2c-c78b938dfd8c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2a8f0e51e5808a691251e4d9acf38d70f2874508
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshooting-windows-defender-or-endpoint-protection-client"></a>Rozwiązywanie problemów z klientem usługi Windows Defender lub program Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


W razie wystąpienia problemów z usługą Windows Defender lub programem Endpoint Protection skontaktuj się z administratorem zabezpieczeń, aby uzyskać pomoc. Można też spróbować rozwiązać następujące problemy:  

-   [Aktualizacja usługi Windows Defender lub program Endpoint Protection](#update-windows-defender-or-endpoint-protection)  
-   [Uruchamianie usługi Windows Defender lub program Endpoint Protection](#starting-windows-defender-or-endpoint-protection-service)  
-   [Problemy z połączeniem internetowym](#internet-connection-issues)  
-   [Nie można skorygować wykrytych zagrożeń](#detected-threat-cant-be-remediated)  
-   [Zainstaluj klienta programu Endpoint Protection](#install-the-endpoint-protection-client)  

##  <a name="update-windows-defender-or-endpoint-protection"></a>Aktualizacja usługi Windows Defender lub program Endpoint Protection  
 Usługa Windows Defender lub program Endpoint Protection automatycznie współpracuje z usługą Microsoft Update, aby upewnić się, że Twoje definicje wirusów i programów szpiegujących są zawsze aktualne.  

 **Objawy**  

 W tym artykule opisano często występujące problemy z aktualizacjami automatycznymi, np. następujące sytuacje:  

-   Zostają wyświetlone komunikaty o błędach wskazujące, że aktualizacje się nie powiodły.  

-   Podczas sprawdzania dostępności aktualizacji zostaje wyświetlony komunikat o błędzie z informacją, że nie można sprawdzić, pobrać lub zainstalować aktualizacji definicji wirusów i programów szpiegujących.  

-   Pomimo działającego połączenia z Internetem aktualizacje nie zostają zakończone pomyślnie.  

-   Aktualizacje nie są automatycznie instalowane zgodnie z harmonogramem.  

 **Przyczyna**  

 Najczęstszymi przyczynami problemów z aktualizacjami są problemy z połączeniem internetowym. Jednak jeśli wiesz, że masz połączenie z Internetem, ponieważ możesz przechodzić do innych witryn, problem może być spowodowany konfliktami z ustawieniami w programie Windows Internet Explorer.  

> [!IMPORTANT]  
>  Aby wykonać te kroki musisz zamknąć program Internet Explorer. W związku z tym wydrukuj te instrukcje albo zapisz lub skopiuj do innego pliku, a następnie oznacz ten temat zakładką, aby mieć do niego łatwy dostęp w przyszłości.  

### <a name="step-1-reset-your-internet-explorer-settings"></a>Krok 1. Zresetuj ustawienia programu Internet Explorer  

1.  Zamknij wszystkie otwarte programy, w tym program Internet Explorer.  

    > [!NOTE]  
    >  Zresetowanie tych ustawień w programie Internet Explorer powoduje usunięcie plików tymczasowych, plików cookie, historii przeglądania i haseł online. Jednak Ulubione nie zostają usunięte.  

2.  Kliknij przycisk **Start** i wyszukaj program **inetcpl.cpl**, a następnie naciśnij klawisz **Enter**.  

3.  W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .  

4.  W obszarze **Resetowanie ustawień programu Internet Explorer**kliknij przycisk **Resetuj**, a następnie ponownie kliknij przycisk **Resetuj** .  

5.  Zaczekaj, aż program Internet Explorer zakończy resetowanie ustawień, a następnie kliknij przycisk **OK**.  

6.  Otwórz program Internet Explorer.  

7.  Otwórz program Microsoft Security Essentials, kliknij kartę **Aktualizacja** , a następnie opcję **Aktualizuj**.  

8.  Jeśli problem nie został rozwiązany, przejdź do następnego kroku.  

### <a name="step-2-set-internet-explorer-as-the-default-browser"></a>Krok 2. Ustaw program Internet Explorer jako domyślnej przeglądarki  

1.  Zamknij wszystkie otwarte programy, w tym program Internet Explorer.  

2.  Kliknij przycisk **Start** i wyszukaj program **inetcpl.cpl**, a następnie naciśnij klawisz **Enter**.  

3.  W oknie dialogowym **Opcje internetowe** kliknij kartę **Programy** .  

4.  W obszarze **Domyślna przeglądarka sieci Web**kliknij przycisk **Ustaw jako domyślny**.  

5.  Kliknij przycisk **OK**.  

6.  Otwórz usługę Windows Defender lub program Endpoint Protection. Kliknij kartę **Aktualizacja** , a następnie kliknij pozycję **Aktualizuj**.  

7.  Jeśli problem nie został rozwiązany, przejdź do następnego kroku.  

### <a name="step-3-ensure-that-the-date-and-time-are-set-correctly-on-your-computer"></a>Krok 3. Upewnij się, że data i godzina są poprawnie ustawione na komputerze  

1.  Otwórz usługę Windows Defender lub program Endpoint Protection.  

2.  Jeśli wyświetlony komunikat o błędzie zawiera kod 0x80072f8f, problem najprawdopodobniej wynika z nieprawidłowego ustawienia daty lub godziny na komputerze.  

3.  Aby zresetować komputera ustawienia daty lub godziny, postępuj zgodnie z instrukcjami [napraw przerwanych skrótów pulpitu i wspólny system zadania konserwacji](http://go.microsoft.com/fwlink/?LinkId=155579) (http://go.microsoft.com/fwlink/?LinkId=155579).  

### <a name="step-4-rename-the-software-distribution-folder-on-your-computer"></a>Krok 4. Zmień nazwę folderu dystrybucji oprogramowania na komputerze  

1. Wyłącz usługę aktualizacji automatycznych  

    1.  Kliknij przycisk **Start** i wyszukaj program **services.msc**, a następnie kliknij przycisk **OK**.  

    2.  Kliknij prawym przyciskiem myszy pozycję **Usługa aktualizacji automatycznych**, a następnie kliknij przycisk **Zatrzymaj**.  

    3.  Zminimalizuj przystawkę Usługi.  

2.  Zmień nazwę katalogu **SoftwareDistribution** w następujący sposób:  

    1.  Kliknij przycisk **Start** i wyszukaj program  **cmd**, a następnie kliknij przycisk **OK**.  

    2.  Wpisz polecenie **cd %windir%**, a następnie naciśnij klawisz **Enter**.  

    3.  Wpisz polecenie **ren SoftwareDistribution SDTemp**, a następnie naciśnij klawisz **Enter**.  

    4.  Wpisz polecenie **exit**, a następnie naciśnij klawisz **Enter**.  

3.  Włącz usługę aktualizacji automatycznych w następujący sposób:  

    1.  Zmaksymalizuj przystawkę Usługi.  

    2.  Kliknij prawym przyciskiem myszy pozycję **Usługa aktualizacji automatycznych**, a następnie kliknij przycisk **Uruchom**.  

    3.  Zamknij okno przystawki Usługi.  

### <a name="step-5-reset-the-microsoft-antivirus-update-engine-on-your-computer"></a>Krok 5. Zresetuj aparat aktualizacji oprogramowania antywirusowego firmy Microsoft na komputerze  

1.  Kliknij przycisk **Start** , wyszukaj program  **cmd**, kliknij przycisk **OK**, kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia**, a następnie wybierz pozycję **Uruchom jako administrator**.  

2.  W oknie **Wiersz polecenia** wpisz następujące polecenia i naciśnij klawisz **Enter** po każdym z nich:  

     **dysku CD\\**  

     **Usługa defender files\windows program dysku CD**  

     **Mpcmdrun - RemoveDefinitions-wszystkie**  

     **Zakończ**  

3.  Uruchom ponownie komputer.  

4.  Otwórz program Windows Defender lub  
          Program Endpoint Protection, kliknij przycisk **aktualizacji** , a następnie kliknij pozycję **aktualizacji**.  

5.  Jeśli problem nie został rozwiązany, przejdź do następnego kroku.  

### <a name="step-6-manually-install-the-virus-and-spyware-definition-updates"></a>Krok 6. Ręczne instalowanie aktualizacji definicji wirusów i programów szpiegujących  

-   Jeśli używasz 32-bitowym systemie operacyjnym Windows, Pobierz ręcznie najnowsze aktualizacje przy [ http://go.microsoft.com/fwlink/?LinkID=87342 ](http://go.microsoft.com/fwlink/?LinkID=87342) (http://go.microsoft.com/fwlink/?LinkID=87342).  

-   Jeśli używasz 64-bitowym systemie operacyjnym Windows, Pobierz ręcznie najnowsze aktualizacje przy [ http://go.microsoft.com/fwlink/?LinkID=87341 ](http://go.microsoft.com/fwlink/?LinkID=87341) (http://go.microsoft.com/fwlink/?LinkID=87341).  

-   Kliknij przycisk **Uruchom**. Najnowsze aktualizacje zostaną ręcznie zainstalowane na komputerze.  


### <a name="step-7-contact-support"></a>Krok 7. Skontaktuj się z pomocą techniczną  

-   Jeśli powyższe czynności nie rozwiążą problemu, skontaktuj się z pomocą techniczną. Aby uzyskać więcej informacji, zobacz [techniczną](http://go.microsoft.com/fwlink/?LinkID=196174) (http://go.microsoft.com/fwlink/?LinkID=196174).  

##  <a name="starting-windows-defender-or-endpoint-protection-service"></a>Uruchamianie usługi Windows Defender lub program Endpoint Protection  
 **Objaw**  

 Zostanie wyświetlony komunikat z informacją, że **usługa Windows Defender lub program Endpoint Protection nie monitoruje komputera, ponieważ usługa programu została zatrzymana. Należy ponownie uruchomić go teraz.** 

 **Rozwiązanie**  

### <a name="step-1-restart-your-computer"></a>Krok 1. Uruchom ponownie komputer.  

-   Zamknij wszystkie aplikacje i uruchom ponownie komputer.  

### <a name="step-2-make-sure-the-windows-defender-or-endpoint-protection-service-is-set-to-automatic-and-is-started"></a>Krok 2. Upewnij się, że "Usługa Windows Defender" lub "Usługa programu Endpoint Protection" jest ustawiony na automatyczny i została uruchomiona  

1.  Kliknij przycisk **Start** i wyszukaj program **services.msc**, a następnie naciśnij klawisz **Enter**.  

2.  Wyszukaj pozycję **Usługa firmy Microsoft chroniąca przed złośliwym kodem**. Kliknij ją prawym przyciskiem myszy i wybierz opcję **Właściwości** lub kliknij ją dwukrotnie, aby otworzyć usługę.  

3.  Upewnij się, że opcja „**Typ uruchomienia**” ma ustawioną wartość „**Automatyczny**”.  

4.  Kliknij przycisk **Uruchom** przycisk, aby uruchomić usługę. Jeśli przycisk **Uruchom** nie jest dostępny, kliknij przycisk **Zatrzymaj** , a następnie kliknij przycisk **Uruchom** , aby ponownie uruchomić usługę.  

5.  Zwróć uwagę na wszystkie błędy, które mogą pojawić się w trakcie tego procesu, prześlij przypadek w trybie online i dołącz informacje o błędzie.  

### <a name="step-3-remove-any-existing-internet-security-programs"></a>Krok 3. Usuń wszystkie istniejące programy zabezpieczeń internetowych  

1.  Kliknij przycisk **Start** i wyszukaj program **appwiz.cpl**, a następnie naciśnij klawisz **Enter**.  

2.  Na liście zainstalowanych programów odinstaluj wszystkie programy zabezpieczeń internetowych innych firm.*  

3.  Uruchom ponownie komputer, a następnie spróbuj zainstalować usługę Windows Defender lub  
          Ponownie program Endpoint Protection.  

> [!NOTE]  
>  Niektóre aplikacje zabezpieczeń internetowych nie zostają całkowicie odinstalowane. Może okazać się konieczne pobranie i uruchomienie narzędzia do oczyszczania przeznaczonego do poprzedniej aplikacji zabezpieczającej w celu jej całkowitego usunięcia.  

> [!CAUTION]  
>  Po usunięciu programów zabezpieczeń internetowych komputer nie jest chroniony. Jeśli masz problemy z instalacją   
>       Program Endpoint Protection po usunięciu istniejących programów zabezpieczeń internetowych, skontaktuj się z usługi Windows Defender lub  
>       Obsługa ochrony punktu końcowego poprzez przesłanie przypadku w trybie online (Aby uzyskać więcej informacji, zobacz [temat dotyczący przesyłania przypadku w trybie Online](http://www.microsoft.com/en-ph/security_essentials/Support/8c9074b6-1558-4d14-bc39-d294ced11096.aspx)).  

### <a name="step-4-uninstallreinstall-endpoint-protection"></a>Krok 4. Odinstalowywanie i ponowna instalacja programu Endpoint Protection  

1.  Kliknij przycisk **Start** i wyszukaj program **appwiz.cpl**, a następnie naciśnij klawisz **Enter**.  

2.  Na liście zainstalowanych programów kliknij pozycję **Endpoint Protection**, a następnie odinstaluj program.  

3.  Jeśli zostanie wyświetlony monit, uruchom ponownie komputer, a następnie spróbuj zainstalować ponownie program Endpoint Protection.  

##  <a name="internet-connection-issues"></a>Problemy z połączeniem internetowym  
 Aby mieć pewność, że komputer otrzyma najnowsze aktualizacje z usługi Windows Update, musisz mieć połączenie z Internetem.  

### <a name="step-1-verify-that-your-computer-is-connected-to-the-internet"></a>Krok 1. Sprawdź, czy komputer jest połączony z Internetem  

1.  Kliknij przycisk **Start**i wyszukaj program **ncpa.cpl**, a następnie naciśnij klawisz **Enter**.  

2.  Kliknij prawym przyciskiem myszy nazwę połączenia, a następnie kliknij pozycję **Stan**.  

3.  Jeśli komputer jest połączony, w systemie Windows XP stan połączenia zostanie wyświetlony jako **Połączono**, **Włączono**lub **Uwierzytelnianie zakończyło się pomyślnie** . W systemach Windows Vista i Windows 7 stan **IPv4** będzie wyświetlany jako **Internet**.  

4.  Jeśli wygląda na to, że komputer nie jest połączony, kliknij prawym przyciskiem myszy nazwę połączenia, a następnie kliknij pozycję **Połącz**, **Włącz**, **Uwierzytelnij**lub **Napraw**.  

### <a name="step-3-restart-your-computer"></a>Krok 3. Uruchom ponownie komputer  

-   Zamknij wszystkie otwarte programy i uruchom ponownie komputer.  

### <a name="step-4-if-you-still-cant-connect-to-the-internet-check-your-connections"></a>Krok 4. Jeśli nadal nie można połączyć się z Internetem, sprawdź połączenia  

1.  Jeśli używasz połączenia telefonicznego, upewnij się, że kabel połączenia telefonicznego w gnieździe ściennym i w modemie jest dobrze podłączony.  

2.  Jeśli używasz modemu kablowego, upewnij się, że połączenie kablowe z modemem oraz połączenie między modemem a komputerem są prawidłowe.  

3.  Jeśli używasz modemu kablowego lub routera DSL, upewnij się, że połączenia z routerem i z komputerem są prawidłowe. Spróbuj odłączyć i wyłączyć router i modem. Odczekaj kilka minut, podłącz najpierw modem, odczekaj minutę, następnie podłącz router i uruchom ponownie komputer.  

##  <a name="detected-threat-cant-be-remediated"></a>Nie można skorygować wykrytych zagrożeń  
 Gdy usługa Windows Defender lub program Endpoint Protection wykryje potencjalne zagrożenie, które znajduje się wewnątrz skompresowanego pliku z rozszerzeniem zip lub w udziale sieciowym, zostanie próba akcji związanej z zagrożeniem przez poddawanie kwarantannie lub jego usunięcie.  

### <a name="remove-or-scan-the-file"></a>Usuwanie lub skanowanie pliku  

-   Jeśli wykryte zagrożenie znajduje się w pliku zip, przejdź do tego pliku, a następnie usuń go lub przeprowadź jego skanowanie, klikając plik prawym przyciskiem myszy i wybierając pozycję **Skanuj za pomocą usługi Windows Defender** lub **Skanuj za pomocą programu Endpoint Protection**. Jeśli usługa Windows Defender lub program Endpoint Protection wykryje dodatkowe zagrożenia w pliku, wyświetlane jest powiadomienie o tych zagrożeniach i możliwe jest wybranie odpowiedniej akcji.  

-   Jeśli wykryte zagrożenie znajduje się w udziale sieciowym, przejdź do tego udziału, a następnie przeprowadź jego skanowanie, wybierając pozycję **Skanuj za pomocą usługi Windows Defender** lub **Skanuj za pomocą programu Endpoint Protection**. Jeśli usługa Windows Defender lub program Endpoint Protection wykryje dodatkowe zagrożenia w udziale sieciowym, wyświetlane jest powiadomienie o tych zagrożeniach i możliwe jest wybranie odpowiedniej akcji.  

-   Jeśli nie masz pewności co do pochodzenia pliku, to jednym z najlepszych rozwiązań jest uruchomienie pełnego skanowania na komputerze. Pełne skanowanie może zająć trochę czasu, ale umożliwia ono znalezienie źródła infekcji i usunięcie go przez usługę Windows Defender lub program Endpoint Protection.  

##  <a name="install-the-endpoint-protection-client"></a>Zainstaluj klienta programu Endpoint Protection  

> [!NOTE]  
>  Na komputerze z systemem Windows 10 usługa Windows Defender jest instalowana wraz z systemem operacyjnym.  

 **Objawy**  

 Błąd instalacji z nieznanej przyczyny lub zostaje wyświetlony komunikat o błędzie z kodem błędu, np. 0x80070643, 0X8007064A, 0x8004FF2E, 0x8004FF01, 0x8004FF07, 0x80070002, 0x8007064C, 0x8004FF00, 0x80070001, 0x80070656, 0x8004FF40, 0xC0000156, 0x8004FF41 0x8004FF0B, 0x8004FF11, 0x80240022, 0x8004FF04, 0x80070660, 0x800106B5, 0x80070715, 0x80070005, 0x8004EE00, 0x8007003, 0x800B0100, 0x8007064E lub 0x8007007E.  

 Jeśli na komputerze jest uruchomiony system Windows XP Service Pack 2 (SP2), może zostać wyświetlony co najmniej jeden z następujących komunikatów o błędzie:  

-   W Kreatorze instalacji brakuje pakietu zbiorczego Menedżera filtrów potrzebnego do zakończenia instalacji.  

-   Błąd instalacji KB914882, Instalator nie może zaktualizować plików systemu Windows XP, ponieważ język zainstalowany w tym systemie różni się od języka aktualizacji.  

 **Przyczyna**  

 Program Endpoint Protection nie może zostać zainstalowany na komputerze, na którym są uruchomione inne programy zabezpieczające. Czasami nawet w przypadku usunięcia innych programów zabezpieczających nie zostają one całkowicie odinstalowane. Aby instalacja programu Endpoint Protection była możliwa, musi być używana oryginalna wersja systemu operacyjnego Windows.  

 **Rozwiązanie**  

> [!IMPORTANT]  
>  Podczas rozwiązywania tego problemu konieczne będzie ponowne uruchomienie komputera. Oznacz tę stronę zakładką (oznacz ją jako ulubioną), aby ułatwić ponowne wyszukanie tego tematu, lub wydrukuj ją, aby mieć do niej łatwy dostęp.  

### <a name="step-1-remove-any-existing-security-programs"></a>Krok 1. Usuń wszystkie istniejące programy zabezpieczeń  
**Program Endpoint Protection**

1.  Całkowicie odinstaluj wszystkie istniejące programy zabezpieczeń internetowych.  

2.  Uruchom ponownie komputer.  

3.  Zainstaluj program Endpoint Protection ponownie. Jeśli to nie rozwiąże problemu, przejdź do następnego kroku.  

### <a name="step-2-ensure-that-the-windows-installer-service-is-running"></a>Krok 2. Upewnij się, że usługa Instalator Windows jest uruchomiona  

1.  Kliknij przycisk **Start** i wyszukaj program **services.msc**, a następnie naciśnij klawisz **Enter**.  

2.  Kliknij prawym przyciskiem myszy aplet **Instalator Windows**, a następnie kliknij przycisk **Uruchom**. Jeśli przycisk **Uruchom** jest niedostępny, a są dostępne opcje **Zatrzymaj** i **Uruchom ponownie** , oznacza to, że usługa została już włączona.  

3.  Na stronie **Usługi** w menu **Plik** kliknij przycisk **Zakończ**.  

4.  Kliknij przycisk **Start** i wyszukaj **wiersza polecenia**. Kliknij prawym przyciskiem myszy pozycję **Wiersz polecenia**, a następnie kliknij polecenie **Uruchom jako administrator**.  

5.  Wpisz **MSIEXEC /REGSERVER**, a następnie naciśnij klawisz **Enter**.  

    > [!NOTE]  
    >  Nie ma żadnego wskazania, że to polecenie zakończyło się pomyślnie lub nie powiodło się.  

6.  Zainstaluj program Endpoint Protection ponownie. Jeśli to nie rozwiąże problemu, przejdź do następnego kroku.  

### <a name="step-3-start-windows-in-selective-startup-mode"></a>Krok 3. Uruchomienie systemu Windows w trybie uruchamiania selektywnego  

1.  Kliknij przycisk **Start** i wyszukaj program **msconfig**, a następnie naciśnij klawisz **Enter**.  

2.  Na karcie **Ogólne** kliknij opcję **Uruchamianie selektywne**, a następnie usuń zaznaczenie pola wyboru **Załaduj elementy startowe** .  

3.  Na karcie **Usługi** zaznacz pole wyboru **Ukryj wszystkie usługi Microsoft** , a następnie usuń zaznaczenie wszystkich pól wyboru dla usług, które pozostają na liście.  

4.  Kliknij przycisk **OK**, a następnie kliknij przycisk **Uruchom ponownie** w celu ponownego uruchomienia komputera.  

5.  Spróbuj zainstalować program Endpoint Protection ponownie.  



### <a name="see-also"></a>Zobacz także  
 [Klient programu Endpoint Protection — często zadawane pytania](../../protect/deploy-use/endpoint-protection-client-faq.md)   

 [Pomoc klienta programu Endpoint Protection](../../protect/deploy-use/endpoint-protection-client-help.md)
