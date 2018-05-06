---
title: 'Konfigurowanie certyfikatów '
titleSuffix: Configuration Manager
description: Konfigurowanie certyfikatów dla zaufanej komunikacji na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 2a7d7170-1933-40e9-96d6-74a6eb7278e2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c538c3b7668cc93069f0805b98f29586c3d7c86c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-certificates-for-trusted-communications-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Konfigurowanie certyfikatów dla zaufanej komunikacji związanej z lokalnym zarządzaniem urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager na\-lokalne zarządzanie urządzeniami przenośnymi wymaga, punkt rejestracyjny, punkt proxy rejestracji, punktu dystrybucji i zarządzania urządzeniami punktu role systemu lokacji, aby ustawić dla zaufanej komunikacji z zarządzanymi urządzeniami. Każdy serwer systemu lokacji, który hostuje co najmniej jedną z tych ról, musi mieć unikatowy certyfikat PKI powiązany z serwerem sieci Web w tym systemie. Certyfikat z takim samym certyfikatem głównym, jak w przypadku certyfikatu na serwerach, należy również przechowywać na zarządzanych urządzeniach, aby umożliwić ustanowienie z nimi zaufanej komunikacji.  

 W przypadku urządzeń dołączonych do domeny usługi certyfikatów usługi Active Directory automatycznie instalują potrzebny certyfikat z zaufanym certyfikatem głównym na wszystkich urządzeniach. W przypadku urządzeń, które nie zostały dołączone do domeny, należy uzyskać prawidłowy certyfikat z zaufanym certyfikatem głównym przy użyciu innych metod. Jeśli urząd certyfikacji lokacji jest używany jako zaufany urząd główny (taki sam jak urząd główny używany przez usługę Active Directory w przypadku urządzeń dołączonych do domeny), serwery systemu lokacji dla punktu rejestracji i punktu serwera proxy rejestracji muszą mieć certyfikat wystawiony przez powiązany z nimi urząd certyfikacji.  

 Na każdym zarządzanym urządzeniu należy również zainstalować certyfikat z tym samym certyfikatem głównym, aby zapewnić obsługę zaufanej komunikacji z rolami systemu lokacji. W przypadku urządzeń rejestrowanych zbiorczo można uwzględnić certyfikat w pakiecie rejestracyjnym, który jest dodawany do urządzenia w celu zarejestrowania go, gdy zostanie uruchomione po raz pierwszy przez użytkownika. W przypadku urządzeń zarejestrowanych przez użytkownika należy dodać certyfikat, korzystając z poczty e-mail, pobierając go z sieci Web lub używając innej metody.  

 Alternatywnym rozwiązaniem w przypadku urządzeń, które nie zostały dołączone do domeny, jest użycie certyfikatu głównego znanego publicznego urzędu certyfikacji (na przykład Verisign lub GoDaddy) do wystawienia certyfikatu serwera. Takie rozwiązanie pozwala uniknąć konieczności ręcznego instalowania certyfikatu na urządzeniu, ponieważ w przypadku większości urządzeń obowiązuje natywne zaufanie do połączeń z serwerami korzystającymi z tego samego certyfikatu głównego publicznego urzędu certyfikacji. To alternatywne rozwiązanie jest przydatne w przypadku urządzeń zarejestrowanych przez użytkownika, gdy nie można zainstalować certyfikatów zaufanych za pośrednictwem urzędu certyfikacji lokacji na każdym urządzeniu.  

> [!IMPORTANT]  
>  Istnieje wiele sposobów konfigurowania certyfikatów dla zaufanej komunikacji między urządzeniami i serwery systemu lokacji dla na\-lokalnych zarządzanie urządzeniami przenośnymi. W tym artykule opisano przykład jednej z tych metod. W przypadku tej metody wymagane jest uruchomienie w lokacji serwera z rolą usług certyfikatów usługi Active Directory oraz zainstalowanymi usługami roli urzędu certyfikacji i rejestracji w sieci Web dla urzędu certyfikacji. Aby uzyskać więcej informacji i wskazówek dotyczących tej roli systemu Windows Server, zobacz [Usługi certyfikatów Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=115018).  

 Aby skonfigurować lokację programu Configuration Manager do komunikacji SSL wymagane przez\-lokalnego zarządzania urządzeniami przenośnymi, wykonaj następujące ogólne kroki:  

-   [Skonfigurowanie urzędu certyfikacji (CA) do publikowania listy CRL](#bkmk_configCa)  

-   [Tworzenie szablonu certyfikatu serwera sieci web w urzędzie certyfikacji](#bkmk_certTempl)  

-   [Żądanie certyfikatu serwera sieci web dla każdej roli systemu lokacji](#bkmk_requestCert)  

-   [Powiązać certyfikat z serwera sieci web](#bkmk_bindCert)  

-   [Eksportowanie certyfikatu z tym samym katalogu głównym jako certyfikatu serwera sieci web](#bkmk_exportCert)  

##  <a name="bkmk_configCa"></a> Skonfigurowanie urzędu certyfikacji (CA) do publikowania listy CRL  
 Domyślnie urząd certyfikacji korzysta z list odwołania certyfikatów (CRL), opartych na protokole LDAP, co umożliwia ustanawianie połączeń dla urządzeń dołączonych do domeny. Należy dodać do urzędu certyfikacji listy CRL oparte na protokole HTTP, aby umożliwić ustanawianie relacji zaufania dla urządzeń, które nie zostały dołączone do domeny, przy użyciu certyfikatów wystawianych przez urząd certyfikacji. Te certyfikaty są wymagane do komunikacji SSL między serwerami hostującymi role systemu lokacji programu Configuration Manager i urządzeń zarejestrowanych dla na\-lokalnych zarządzanie urządzeniami przenośnymi.  

 Wykonaj poniższe kroki, aby skonfigurować urząd certyfikacji do automatycznego publikowania list CRL w celu wystawiania certyfikatów umożliwiających ustanawianie zaufanych połączeń dla urządzeń dołączonych do domeny i urządzeń, które nie zostały dołączone do domeny:  

1.  Na serwerze, na którym uruchomiono urząd certyfikacji dla lokacji, kliknij pozycje **Start** > **Narzędzia administracyjne** > **Urząd certyfikacji**.  

2.  W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy pozycję **Urząd certyfikacji**, a następnie kliknij pozycję **Właściwości**.  

3.  We właściwościach urzędu certyfikacji kliknij kartę **Rozszerzenia** i upewnij się, że opcja **Wybierz rozszerzenie** jest skonfigurowana z ustawieniem **Punkt dystrybucji listy CRL (CDP)**.  

4.  Wybierz pozycję **http://<nazwa_DNS_serwera\>/CertEnroll/<nazwa_urzędu_CA\><sufiks_nazwy_listy_CRL\><dozwolona_różnicowa_lista_CRL\>.crl**. Oraz trzy poniższe opcje:  

    -   **Dołącz do list CRL. Klienci używają tego do znajdowania lokalizacji różnicowych list CRL.**  

    -   **Dołącz rozszerzenia CDP wystawionych certyfikatów.**  

    -   **Dołącz do rozszerzenia IDP wystawionych list CRL**  

5.  Kliknij przycisk **moduł zakończenia** , kliknij pozycję **właściwości...** , a następnie wybierz pozycję **Zezwalaj na publikowanie w systemie plików certyfikatów**.  

6.  Kliknij przycisk **OK** po wyświetleniu powiadomienia o konieczności ponownego uruchomienia usług certyfikatów Active Directory.  

7.  Kliknij prawym przyciskiem myszy pozycję **Odwołane certyfikaty**, kliknij pozycję **Wszystkie zadania**, a następnie kliknij pozycję **Publikuj**.  

8.  W oknie dialogowym Publikowanie listy CRL wybierz pozycję **Tylko różnicowa lista CRL**, a następnie kliknij przycisk **OK**.  

##  <a name="bkmk_certTempl"></a> Tworzenie szablonu certyfikatu serwera sieci web w urzędzie certyfikacji  
 Następnym krokiem po opublikowaniu nowej listy CRL w urzędzie certyfikacji jest utworzenie szablonu certyfikatu serwera sieci Web. Ten szablon jest wymagany do wystawiania certyfikatów dla serwerów hostujących role systemu lokacji punktu rejestracji, punktu serwera proxy rejestracji, punktu dystrybucji i punktu zrządzania urządzeniami. Te serwery będą punktami końcowymi protokołu SSL dla zaufanej komunikacji między rolami systemu lokacji i zarejestrowanymi urządzeniami.    Aby utworzyć szablon certyfikatu, wykonaj następujące czynności:  

1.  Utwórz grupę zabezpieczeń o nazwie **Serwery funkcji MDM programu ConfigMgr** zawierającą serwery, na których zostały uruchomione systemy lokacji wymagające zaufanej komunikacji z zarejestrowanymi urządzeniami.  

2.  W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy pozycję **Szablony certyfikatów**, a następnie kliknij polecenie **Zarządzaj**, aby załadować konsolę Szablony certyfikatów.  

3.  W okienku wyników w kolumnie **Nazwa wyświetlana szablonu** kliknij prawym przyciskiem myszy wpis opisany jako **Serwer sieci Web**i kliknij polecenie **Duplikuj szablon**.  

4.  W oknie dialogowym **Duplikowanie szablonu** sprawdź, czy jest wybrany system **Windows 2003 Server, Enterprise Edition** , a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**. Menedżer konfiguracji nie obsługuje szablonów certyfikatów w systemie Windows Server 2008 dla zaufanej komunikacji przy użyciu protokołu HTTPS.  

    > [!NOTE]  
    >  Jeśli używany urząd certyfikacji znajduje się w systemie Windows Server 2012, monit o podanie wersji szablonu certyfikatu nie jest wyświetlany po kliknięciu pozycji **Duplikuj szablon**. Zamiast tego na karcie **Zgodność** właściwości szablonu należy podać następujące dane:  
    >   
    >  **Urząd certyfikacji**: **Windows Server 2003**  
    >   
    >  **Odbiorca certyfikatu**: **Windows XP / Server 2003**  

5.  W oknie dialogowym **Właściwości nowego szablonu** na karcie **Ogólne** wprowadź nazwę szablonu w celu wygenerowania certyfikatów sieci Web, które będą używane w systemach lokacji programu Configuration Manager, taką jak **Serwer sieci Web funkcji MDM programu ConfigMgr**.  

6.  Kliknij kartę **Nazwa podmiotu**, wybierz pozycję **Konstruuj z informacji usługi Active Directory**, a następnie określ ustawienie **Nazwa DNS** dla formatu nazwy podmiotu. Wyczyść pole wyboru alternatywnej nazwy podmiotu, jeśli opcja **Nazwa główna użytkownika (UPN)** została zaznaczona.  

7.  Kliknij kartę **Zabezpieczenia** i usuń uprawnienie **Rejestracja** z grup zabezpieczeń **Administratorzy domeny** i **Administratorzy przedsiębiorstwa**.  

8.  Kliknij przycisk **Dodaj**, w polu tekstowym wprowadź tekst **Serwery IIS programu ConfigMgr**, a następnie kliknij przycisk **OK**.  

9. Wybierz dla tej grupy uprawnienie **Rejestracja** i nie usuwaj zaznaczenia uprawnienia **Odczyt** .  

10. Kliknij przycisk **OK** i zamknij konsolę Szablony certyfikatów.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy pozycję **Szablony certyfikatów**, kliknij polecenie **Nowy**, a następnie kliknij pozycję **Szablon certyfikatu do wystawienia**.  

12. W oknie dialogowym **Włączanie szablonu certyfikatu** wybierz właśnie utworzony nowy szablon **Serwer sieci Web funkcji MDM programu ConfigMgr**, a następnie kliknij przycisk **OK**.  

##  <a name="bkmk_requestCert"></a> Żądanie certyfikatu serwera sieci web dla każdej roli systemu lokacji  
 Urządzenia zarejestrowane dla na\-lokalne zarządzanie urządzeniami przenośnymi muszą ufać punktom końcowym SSL hosting punkt rejestracyjny, punkt proxy rejestracji, punktu dystrybucji i punktu zarządzania urządzeniami.  Aby zażądać certyfikatu serwera sieci Web dla programu IIS, należy wykonać poniższe czynności. Należy wykonać tę czynność dla każdego serwera (punktu końcowego protokołu SSL) hostującego jedną z ról systemu lokacji wymagane dla na\-lokalnych zarządzanie urządzeniami przenośnymi.  

1.  Na serwerze lokacji głównej otwórz wiersz polecenia, korzystając z uprawnienia administratora, wpisz **MMC** i naciśnij klawisz **Enter**.  

2.  W programie MMC kliknij pozycje **Plik** > **Dodaj/Usuń przystawkę**.  

3.  W przystawce Certyfikaty wybierz pozycję **Certyfikaty**, kliknij pozycję **Dodaj**, wybierz opcję **Konto komputera**, kliknij przycisk **Dalej**, kliknij przycisk **Zakończ**, a następnie kliknij przycisk **OK**, aby zamknąć okno Dodawanie lub usuwanie przystawek.  

4.  Kliknij prawym przyciskiem myszy pozycję **Certyfikaty**, a następnie kliknij pozycje **Wszystkie zadania** > **Żądaj nowego certyfikatu**.  

5.  W kreatorze Rejestracja certyfikatu kliknij przycisk **Dalej**, wybierz pozycję **Zasady rejestracji usługi Active Directory**, a następnie kliknij przycisk **Dalej**.  

6.  Zaznacz pole wyboru obok certyfikatu serwera sieci Web (**Serwer sieci Web funkcji MDM programu ConfigMgr**), a następnie kliknij przycisk **Zarejestruj**.  

7.  Po zarejestrowaniu certyfikatu kliknij przycisk **Zakończ**.  

 Ponieważ każdy serwer będzie potrzebować certyfikatu serwera sieci web unikatowy, należy powtórzyć ten proces dla każdego serwera hostującego jedną z ról systemu lokacji wymagane dla na\-lokalnych zarządzanie urządzeniami przenośnymi.  Jeśli jeden serwer hostuje wszystkie role sytemu lokacji, wystarczy zażądać jednego certyfikatu serwera sieci Web.  

##  <a name="bkmk_bindCert"></a> Powiązać certyfikat z serwera sieci web  
 Nowy certyfikat należy powiązać z serwerem sieci web każdego serwera systemu lokacji hostujących role systemu lokacji wymagane dla na\-lokalnych zarządzanie urządzeniami przenośnymi. Poniższe czynności należy wykonać dla każdego serwera hostującego role systemu lokacji punktu rejestracji i punktu serwera proxy rejestracji. Jeśli jeden serwer hostuje wszystkie role sytemu lokacji, wystarczy wykonać te czynności tylko jeden raz. Wykonywanie tego zadania dla ról systemu lokacji punktu dystrybucji i punktu zarządzania urządzeniami nie jest konieczne, ponieważ automatycznie otrzymują one certyfikat podczas rejestrowania.  

1.  Na serwerze hostującym punkt rejestracji, punkt proxy rejestracji, punkt dystrybucji lub punkt zarządzania urządzeniami kliknij pozycje **Start** > **Narzędzia administracyjne** > **Menedżer usług IIS**.  

2.  W obszarze połączenia przejdź do, a następnie kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie kliknij przycisk **Edytuj powiązania...**  

3.  W oknie dialogowym powiązania witryny kliknij **https**, a następnie kliknij przycisk **edycji...**  

4.  W oknie dialogowym Edytowanie powiązań witryny wybierz w obszarze **Certyfikat SSL** certyfikat, który właśnie został zarejestrowany, kliknij przycisk **OK**, a następnie kliknij przycisk **Zamknij**.  

5.  W konsoli Menedżer usług IIS w obszarze Połączenia wybierz serwer sieci Web, a następnie w prawym okienku akcji kliknij pozycję **Uruchom ponownie**.  

##  <a name="bkmk_exportCert"></a> Eksportowanie certyfikatu z tym samym katalogu głównym jako certyfikatu serwera sieci web  
 Usługi certyfikatów w usługi Active Directory zazwyczaj instalują wymagany certyfikat z urzędu certyfikacji na wszystkich urządzeniach dołączonych do domeny. Urządzenia, które nie zostały dołączone do domeny, nie będą jednak mogły komunikować się z rolami systemu lokacji bez certyfikatu z głównego urzędu certyfikacji. Aby uzyskać certyfikat umożliwiający urządzeniom komunikowanie się z rolami systemu lokacji, można eksportować go z certyfikatu powiązanego z serwerem sieci Web.  

 Aby eksportować certyfikat główny certyfikatu serwera sieci Web, wykonaj poniższe czynności.  

1.  W Menedżerze usług IIS kliknij **domyślna witryna sieci Web**, a następnie w prawym okienku akcji kliknij **powiązań...**  

2.  W oknie dialogowym powiązania witryny kliknij **https**, a następnie kliknij przycisk **edycji...**  

3.  Upewnij się, że certyfikat serwera sieci web jest zaznaczone, a następnie kliknij przycisk **widoku...**  

4.  We właściwościach certyfikatu serwera sieci Web kliknij pozycję **Ścieżka certyfikacji**, kliknij certyfikat główny na początku ścieżki certyfikacji, a następnie kliknij pozycję **Wyświetl certyfikat**.  

5.  We właściwościach certyfikatu głównego, kliknij przycisk **szczegóły**, a następnie kliknij przycisk **Kopiuj do pliku...**  

6.  W Kreatorze eksportu certyfikatu kliknij przycisk **Dalej**.  

7.  Upewnij się, że wybrano opcję formatu **Certyfikat X.509 szyfrowany binarnie algorytmem DER (CER)**, a następnie kliknij przycisk **Dalej**.  

8.  Dla nazwy pliku, kliknij przycisk **Przeglądaj...** , wybierz lokalizację do zapisania pliku certyfikatu, określ nazwę pliku i kliknij przycisk **zapisać**.  

     Urządzenia do zarejestrowania muszą uzyskać dostęp do tego pliku w celu zaimportowania certyfikatu głównego, dlatego należy wybrać wspólną lokalizację dostępną dla większości komputerów i urządzeń lub zapisać go w dogodnej lokalizacji teraz (na przykład dysk C) i przenieść go wspólnej lokalizacji później.  

     Kliknij przycisk **Dalej**.  

9. Przejrzyj ustawienia, a następnie kliknij przycisk **Zakończ**.  
