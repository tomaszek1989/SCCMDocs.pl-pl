---
title: "Wdrażanie klientów systemu UNIX/Linux | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania klienta na serwerze UNIX lub Linux w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 15a4e323-9f42-4fea-bb14-f2b905d1f77c
caps.latest.revision: "9"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 1741506f390430c85dab9a5b8e8cc26dda7b57e3
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-deploy-clients-to-unix-and-linux-servers-in-system-center-configuration-manager"></a>Jak wdrażać klientów na serwerach z systemami UNIX i Linux w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby można było zarządzać serwerem systemu Linux lub UNIX z System Center Configuration Manager, należy zainstalować klienta programu Configuration Manager dla systemów Linux i UNIX na każdym serwerze z systemem Linux lub UNIX. Instalację klienta można przeprowadzić ręcznie na każdym komputerze albo użyć skryptu powłoki, za pomocą którego klient zostanie zainstalowany zdalnie. Menedżer konfiguracji nie obsługuje użycia instalacji wypychanej klienta dla serwerów z systemem Linux lub UNIX. Opcjonalnie można skonfigurować element Runbook dla programu System Center Orchestrator w celu automatyzacji instalacji klienta na serwerze z systemem Linux lub UNIX.  

 Niezależnie od używanej metody instalacji proces instalacji wymaga użycia skryptu o nazwie **install** (instaluj) do zarządzania procesem instalacji. Skrypt ten jest dołączany w momencie pobierania klienta dla systemów Linux i UNIX.  

 Skrypt instalacji klienta programu Configuration Manager dla systemów Linux i UNIX obsługuje właściwości wiersza polecenia. Niektóre właściwości wiersza polecenia są wymagane, a inne opcjonalne. Na przykład podczas instalowania klienta należy określić punkt zarządzania z lokacji, który jest używany przez serwer z systemem Linux lub UNIX do pierwszego kontaktu z lokacją. Pełna lista właściwości wiersza polecenia znajduje się w sekcji [Właściwości wiersza polecenia dotyczące instalowania klienta na serwerach z systemami Linux i UNIX](#BKMK_CmdLineInstallLnUClient).  

 Po zainstalowaniu klienta Określ ustawienia klienta w konsoli programu Configuration Manager w celu skonfigurowania agenta klienta w taki sam sposób jak w przypadku klientów z systemem Windows. Aby uzyskać więcej informacji, zobacz [Ustawienia klienta dla serwerów z systemami Linux i UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ClientSettingsforLnU).  

##  <a name="BKMK_AboutInstallPackages"></a> Pakiety instalacyjne klienta i agent uniwersalny — informacje  
 Aby zainstalować klienta dla systemów Linux i UNIX na danej platformie, należy użyć pakietu instalacyjnego klienta odpowiedniego dla komputera, na którym jest instalowany klient. Odpowiednie pakiety instalacyjne klienta są dołączane jako część każdego pobrania klienta z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184). Oprócz pakietów instalacyjnych klienta pobranie klienta obejmuje skrypt **install** (instaluj), który służy do zarządzania instalacją klienta na każdym komputerze.  

 Podczas instalowania klienta można użyć tego samego procesu i właściwości wiersza polecenia niezależnie od używanego pakietu instalacyjnego klienta.  

 Aby uzyskać informacje dotyczące systemów operacyjnych, platform i pakietów instalacyjnych klienta, które są obsługiwane w przypadku każdej wersji klienta programu Configuration Manager dla systemów Linux i UNIX, zobacz [serwerów Linux i UNIX](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#linux-and-unix-servers).  

##  <a name="BKMK_InstallLnUClient"></a> Instalowanie klienta na serwerach z systemem Linux i UNIX  
 Aby zainstalować klienta dla systemów Linux i UNIX, należy uruchomić skrypt na każdym komputerze z systemem Linux lub UNIX. Skrypt ma nazwę **install** i obsługuje właściwości wiersza polecenia, które modyfikują zachowanie instalacji i tworzą odwołanie do pakietu instalacyjnego klienta. Skrypt install i pakiet instalacyjny klienta muszą znajdować się na komputerze klienckim. Pakiet instalacyjny klienta zawiera pliki klienta programu Configuration Manager dla określonego systemu operacyjnego Linux lub UNIX i platformy.
Każdy pakiet instalacyjny klienta zawiera wszystkie pliki niezbędne do ukończenia instalacji klienta i w przeciwieństwie do komputerów z systemem Windows nie pobiera dodatkowych plików z punktu zarządzania ani innej lokalizacji źródłowej.  

 Po zainstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX nie ma potrzeby ponownego uruchamiania komputera. Klienta można użyć zaraz po zakończeniu instalacji oprogramowania. Jeśli ponowne uruchomienie komputera, automatycznie uruchamia ponownie klienta programu Configuration Manager.  

 Zainstalowany klient działa z poświadczeniami głównymi. Poświadczenia główne są wymagane do zbierania spisu sprzętu i wykonywania wdrożeń oprogramowania.  

 Format polecenia jest następujący:  

 **. / install -mp &lt;komputera\> - sitecode &lt;kod_lokacji\> &lt;właściwości #1 > &lt;właściwości #2 > &lt;pakietu instalacyjnego klienta\>**  

-   Element**install** to nazwa pliku skryptu służącego do instalowania klienta dla systemów Linux i UNIX. Ten plik jest dostarczany wraz oprogramowaniem klienckim.  

-   **-mp &lt;komputera** Określa początkowy punkt zarządzania używany przez klienta.  

     Przykład: smsmp.contoso.com  

-   **-sitecode &lt;kod lokacji\> ** Określa, czy klient jest przypisany do kod lokacji.  

     Przykład: S01  

-   &lt;Właściwość #1 > &lt;właściwości #2 > określa właściwości wiersza polecenia do użycia przy użyciu skryptu instalacji.  

    > [!NOTE]  
    >  Aby uzyskać więcej informacji, zobacz [Właściwości wiersza polecenia do instalowania klienta na serwerach z systemem Linux i UNIX](#BKMK_CmdLineInstallLnUClient)  

-   Element**pakiet instalacyjny klienta** to nazwa pakietu tar instalacji klienta dla danego systemu operacyjnego, wersji i architektury procesora CPU. Plik tar instalacji klienta musi być określony jako ostatni.  

     Przykład: ccm-Universal-x64. &lt;kompilacji\>tar  

###  <a name="BKMK_ToInstallLnUClinent"></a> Instalowanie klienta programu Configuration Manager na serwerach z systemami Linux i UNIX  

1.  Na komputerze z systemem Windows [pobierz odpowiedni plik klienta dla serwera z systemem Linux lub UNIX](http://go.microsoft.com/fwlink/?LinkID=525184) , którym chcesz zarządzać.  

2.  Uruchom samowyodrębniający się plik exe na komputerze z systemem Windows w celu wyodrębnienia skryptu instalacji oraz pliku tar instalacji klienta.  

3.  Skopiuj skrypt **install** i plik tar do folderu na serwerze, którym chcesz zarządzać.  

4.  Na serwerze z systemem UNIX lub Linux uruchom następujące polecenie, aby umożliwić uruchomienie skryptu jako programu: **chmod +x install**  

    > [!IMPORTANT]  
    >  Aby zainstalować klienta, należy użyć poświadczeń użytkownika root.  

5.  Następnie uruchom następujące polecenie, aby zainstalować klienta programu Configuration Manager: **. / install -mp &lt;hostname\> - sitecode &lt;kod\> ccm-Universal-x64.&lt; Tworzenie\>tar**  

     Po wprowadzeniu tego polecenia należy użyć dodatkowych wymaganych właściwości wiersza polecenia.  Aby uzyskać listę właściwości wiersza polecenia, zobacz [Właściwości wiersza polecenia dotyczące instalowania klienta na serwerach z systemami Linux i UNIX](#BKMK_CmdLineInstallLnUClient)  

6.  Po uruchomieniu skryptu zweryfikuj instalację, przeglądając plik **/var/opt/microsoft/scxcm.log** . Ponadto można potwierdzić, czy klient jest zainstalowany i komunikacji z lokacją, wyświetlając szczegółowe informacje dotyczące klienta w **urządzeń** węzła **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  

###  <a name="BKMK_CmdLineInstallLnUClient"></a> Właściwości wiersza polecenia dotyczące instalowania klienta na serwerach z systemami Linux i UNIX  
 Poniżej opisano dostępne właściwości służące do modyfikowania zachowania skryptu instalacji:  

> [!NOTE]  
>  Użyj właściwości **-h** do wyświetlania tej listy obsługiwanych właściwości.  

-   **-mp &lt;nazwa FQDN serwera\>**  

     Wymagany. Określony przez nazwę FQDN serwer punktu zarządzania, który będzie używany przez klienta jako pierwszy punkt kontaktu.  

    > [!IMPORTANT]  
    >  Ta właściwość nie określa punktu zarządzania, do którego klienci zostaną przypisani po zakończeniu instalacji.  

    > [!NOTE]  
    >  Jeśli właściwość **-mp** jest używana do określenia punktu zarządzania skonfigurowanego do akceptowania tylko połączeń klienckich HTTPS, należy również użyć właściwości **-UsePKICert** .  

-   **-sitecode &lt;kod_lokacji\>**  

     Wymagany. Określa lokację główną programu Configuration Manager można przypisać klienta programu Configuration Manager.  

     Przykład: -sitecode S01  

-   **-fsp &lt;nazwa_FQDN_serwera >**  

     Opcjonalny. Określony przez nazwę FQDN serwer rezerwowych punktów stanu używany przez klienta do przesyłania komunikatów o stanie.  

     Więcej informacji dotyczących rezerwowego punktu stanu znajduje się w temacie [Określanie, czy jest wymagany rezerwowy punkt stanu](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#determine-if-you-need-a-fallback-status-point).  


-   **-dir &lt;katalogu\>**  

     Opcjonalny. Określa alternatywną lokalizację instalacji plików klienta programu Configuration Manager.  

     Domyślnie klient jest instalowany w następującej lokalizacji: **/opt/microsoft**.  

-   **-nostart**  

     Opcjonalny. Uniemożliwia automatyczne uruchamianie usługi klienta Configuration Manager, **ccmexec.bin**po zakończeniu instalacji klienta.  

     Po zainstalowaniu klienta należy ręcznie uruchomić usługę klienta.  

     Domyślnie usługa klienta jest uruchamiana po zakończeniu instalacji klienta i po każdym ponownym uruchomieniu komputera.  

-   **-clean**  

     Opcjonalny. Oznacza usunięcie wszystkich plików i danych klienta z wcześniej zainstalowanego klienta dla systemów Linux i UNIX przed rozpoczęciem nowej instalacji. Spowoduje to usunięcie bazy danych klienta i magazynu certyfikatów.  

-   **-keepdb**  

     Opcjonalny. Określa, czy lokalna baza danych klienta jest zachowywana i ponownie używana po ponownej instalacji klienta. Domyślnie podczas ponownej instalacji klienta baza danych jest usuwana.  

-   **-UsePKICert &lt;parametru\>**  

     Opcjonalny. Określa pełną ścieżkę i nazwę pliku certyfikatu X.509 PKI w formacie certyfikatu klucza publicznego (PKCS #12). Ten certyfikat jest używany do uwierzytelnienia klienta. Jeśli certyfikat nie zostanie określony podczas instalacji i konieczne będzie dodanie lub zmiana certyfikatu, użyj narzędzia **certutil** . Zobacz [Jak zarządzać certyfikatami na kliencie dla systemów Linux i UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts), aby uzyskać informacje na temat narzędzia certutil.  

     W przypadku używania właściwości **-UsePKICert**należy również podać hasło skojarzone z plikiem PKCS#12 przy użyciu parametru **-certpw** wiersza polecenia.  

     Jeśli ta właściwość nie jest używana do określenia certyfikatu PKI, klient używa certyfikatu z podpisem własnym, a cała komunikacja z systemami lokacji odbywa się przy użyciu protokołu HTTP.  

     Jeśli określono nieprawidłowy certyfikat w wierszu polecenia instalacji klienta, nie są zwracane żadne błędy. Wynika to z tego, że weryfikacja certyfikatu ma miejsce po zainstalowaniu klienta. Podczas uruchamiania klienta, certyfikaty są weryfikowane z punktem zarządzania, a jeśli certyfikat weryfikacji nie powiedzie się w zostanie wyświetlony następujący komunikat **scxcm.log**, pliku dziennika systemu Unix i Linux Configuration Manager klienta: **Nie można zweryfikować certyfikatu punktu zarządzania**. Domyślna lokalizacja pliku dziennika to:  **/var/opt/microsoft/scxcm.log**.  

    > [!NOTE]  
    >  Należy określić tę właściwość, jeśli podczas instalacji klienta właściwość **-mp** jest używana do określenia punktu zarządzania skonfigurowanego do akceptowania tylko połączeń klienckich HTTPS.  

     Przykład: - UsePKICert &lt;Pełna ścieżka i nazwa pliku\> - certpw &lt;hasła\>  

-   **-certpw &lt;parametru\>**  

     Opcjonalny. Określa hasło skojarzone z plikiem PKCS #12 określonym przez użycie właściwości **-UsePKICert** .  

     Przykład: - UsePKICert &lt;Pełna ścieżka i nazwa pliku\> - certpw &lt;hasła\>  

-   **-NoCRLCheck**  

     Opcjonalny. Określa, że klient nie ma sprawdzać listy odwołania certyfikatów (CRL) podczas komunikacji za pomocą protokołu HTTPS przy użyciu certyfikatu PKI. Kiedy ta opcja nie jest określona, klient sprawdza listę CRL przed nawiązaniem połączenia HTTPS przy użyciu certyfikatów PKI. Więcej informacji o sprawdzaniu listy CRL przez klienta znajduje się w temacie Planowanie odwołania certyfikatu PKI.  

     Przykład: - UsePKICert &lt;Pełna ścieżka i nazwa pliku\> - certpw &lt;hasło\> - NoCRLCheck  

-   **-rootkeypath &lt;lokalizacja pliku\>**  

     Opcjonalny. Określa pełną ścieżkę i nazwę pliku do programu Configuration Manager zaufanego klucza głównego. Menedżer konfiguracji zaufanego klucza głównego zapewnia mechanizm klienci systemu Linux i UNIX użyj, aby sprawdzić, czy są one połączone z systemu lokacji, który należy do prawidłowej hierarchii.  

     Jeśli zaufany klucz główny nie zostanie określony w wierszu polecenia, klient będzie ufał pierwszemu punktowi zarządzania, z którym nawiąże komunikację, i automatycznie pobierze zaufany klucz główny z tego punktu zarządzania.  

     Aby uzyskać więcej informacji, zobacz [Planowanie zaufanego klucza głównego](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

     Przykład: - rootkeypath &lt;Pełna ścieżka i nazwa pliku\>  

-   **-httpport &lt;portu\>**  

     Opcjonalny. Określa port skonfigurowany w punktach zarządzania, których klient używa podczas komunikowania się z punktami zarządzania za pośrednictwem protokołu HTTP. Jeśli port nie jest określony, zostanie użyta domyślna wartość 80.  

     Przykład: -httpport 80  

-   **-httpsport &lt;portu\>**  

     Opcjonalny. Określa port skonfigurowany w punktach zarządzania, których klient używa podczas komunikowania się z punktami zarządzania za pośrednictwem protokołu HTTPS. Jeśli port nie jest określony, zostanie użyta domyślna wartość 443.  

     Przykład: - UsePKICert &lt;Pełna nazwa i ścieżka certyfikatu\> - httpsport 443  

-   **-ignoreSHA256validation**  

     Opcjonalny. Określa, że instalacja klienta pomija weryfikację za pomocą algorytmu SHA-256. Użyj tej opcji podczas instalowania klienta w systemach operacyjnych, które nie zostały wydane z wersją biblioteki OpenSSL obsługującą algorytm SHA-256. Aby uzyskać więcej informacji, zobacz [Informacje o systemach operacyjnych Linux i UNIX, które nie obsługują algorytmu SHA-256](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_NoSHA-256).  

-   **-signcertpath &lt;lokalizacja pliku\>**  

     Opcjonalny. Określa pełną ścieżkę i nazwę pliku **.cer** wyeksportowanego certyfikatu z podpisem własnym na serwerze lokacji. Jeśli certyfikaty PKI są niedostępne, serwer lokacji programu Configuration Manager automatycznie generuje certyfikaty z podpisem własnym.  

     Te certyfikaty są używane do weryfikacji, czy zasady klienta pobierane z punktu zarządzania zostały wysłane z planowanej lokacji. Jeśli certyfikat z podpisem własnym nie zostanie określony podczas instalacji lub konieczna będzie zmiana certyfikatu, należy użyć narzędzia **certutil** . Zobacz [Jak zarządzać certyfikatami na kliencie dla systemów Linux i UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts), aby uzyskać informacje na temat narzędzia certutil.  

     Ten certyfikat może zostać pobrany z magazynu certyfikatów programu **SMS** i ma przypisaną nazwę podmiotu **Serwer lokacji** oraz przyjazną nazwę **Certyfikat podpisywania serwera lokacji**.  

     Jeśli ta opcja nie zostanie określona podczas instalacji, klienci systemu Linux i UNIX będą ufać pierwszemu punktowi zarządzania, z którym nawiążą komunikację, i automatycznie pobiorą certyfikat podpisywania z tego punktu zarządzania.  

     Przykład: - signcertpath &lt;Pełna ścieżka i nazwa pliku\>  

-   **-rootcerts**  

     Opcjonalny. Określa dodatkowe certyfikaty PKI do zaimportowania, które nie są częścią hierarchii urzędu certyfikacji punktów zarządzania. W przypadku określania wielu certyfikatów w wierszu polecenia należy rozdzielić je przecinkami.  

     Użyj tej opcji w przypadku używania certyfikatów klienta PKI, które nie są powiązane z certyfikatem głównego urzędu certyfikacji zaufanym z perspektywy punktów zarządzania Twoich lokacji. Punkty zarządzania odrzucą klienta, jeśli certyfikat klienta nie będzie powiązany z zaufanym certyfikatem głównym listy wystawców certyfikatów dla lokacji.  

     Jeśli ta opcja nie zostanie użyta, klient systemów Linux i UNIX zweryfikuje hierarchię zaufania tylko przy użyciu certyfikatu znajdującego się w opcji **-UsePKICert** .  

     Przykład: - rootcerts &lt;Pełna ścieżka i nazwa pliku\>,&lt;Pełna ścieżka i nazwa pliku\>  

###  <a name="BKMK_UninstallLnUClient"></a> Odinstalowywanie klienta z serwerów z systemami Linux i UNIX  
 Aby odinstalować klienta programu Configuration Manager dla systemów Linux i UNIX za pomocą narzędzia odinstalowywania **Odinstaluj**. Domyślnie ten plik znajduje się w folderze **/opt/microsoft/configmgr/bin/** na komputerze klienckim. To polecenie odinstalowywania nie obsługuje żadnych parametrów wiersza polecenia i spowoduje usunięcie z serwera wszystkich plików związanych z oprogramowaniem klienta.  

 Aby odinstalować klienta, użyj następującego polecenia w wierszu polecenia: **/opt/microsoft/configmgr/bin/uninstall**  

 Nie trzeba ponownie uruchomić komputer po odinstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX.  

##  <a name="BKMK_ConfigLnUClientCommuincations"></a> Konfigurowanie portów żądań klienta dla systemów Linux i UNIX  
 Podobnie jak klienci z systemem Windows, klient programu Configuration Manager dla systemów Linux i UNIX korzysta z protokołów HTTP i HTTPS do komunikacji z systemami lokacji programu Configuration Manager. Porty używane przez klienta programu Configuration Manager do komunikacji są określane jako porty żądań.  

 Po zainstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX można zmienić domyślne porty żądań klientów, określając **- httpport** i **- httpsport** właściwości instalacji. Jeśli właściwość instalacji i wartość niestandardowa nie zostaną określone, klient użyje wartości domyślnych. Domyślne wartości to **80** dla ruchu HTTP i **443** dla ruchu HTTPS.  

 Po zainstalowaniu klienta nie można zmienić konfiguracji jego portów żądań. Zamiast tego w celu zmiany konfiguracji portów należy ponownie zainstalować klienta i określić nową konfigurację portu. Podczas ponownej instalacji klienta w celu zmiany numerów portów żądań uruchom polecenie **install** jak w przypadku nowej instalacji klienta, ale użyj dodatkowej właściwości wiersza polecenia **-keepdb**. Ten przełącznik powoduje, że w trakcie instalacji zachowana zostanie baza danych klienta i jego pliki, w tym identyfikatory GUID oraz magazyn certyfikatów klientów.  

 Więcej informacji o numerach portów dotyczących komunikacji z klientami znajduje się w temacie [Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md).  

##  <a name="BKMK_ConfigClientMP"></a> Konfigurowanie klienta dla systemów Linux i UNIX w celu zlokalizowania punktów zarządzania  
 Po zainstalowaniu klienta programu Configuration Manager dla systemów Linux i UNIX należy określić punkt zarządzania do użycia jako pierwszy punkt kontaktu.  

 Klient programu Configuration Manager dla systemów Linux i UNIX kontaktuje się z tego punktu zarządzania w momencie instalacji klienta. Jeśli klient nie może nawiązać połączenia z punktem zarządzania, oprogramowanie klienckie kontynuuje ponawianie prób aż do osiągnięcia sukcesu.  

 Aby uzyskać więcej informacji dotyczących sposobu lokalizowania punktów zarządzania przez klientów, zobacz [Lokalizowanie punktów zarządzania](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points).
