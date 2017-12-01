---
title: Planowanie dostawcy programu SMS
titleSuffix: Configuration Manager
description: "Więcej informacji na temat sposobu dostawcy programu SMS pomaga w zarządzaniu System Center Configuration Manager."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: "8"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2ae9f17fd6d0695c78560b303b42011827a13b6d
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="plan-for-the-sms-provider-for-system-center-configuration-manager"></a>Planowanie dostawcy programu SMS dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby zarządzać System Center Configuration Manager, należy użyć konsoli programu Configuration Manager, która łączy się z wystąpieniem programu **dostawcy programu SMS**. Domyślnie dostawca programu SMS instaluje na serwerze lokacji podczas instalowania centralnej lokacji administracyjnej lub lokacji głównej. 


##  <a name="BKMK_PlanSMSProv"></a> Dostawca programu SMS — informacje  
 Dostawca programu SMS jest dostawcą Instrumentacji zarządzania Windows (WMI) przypisującym **odczytu** i **zapisu** dostępu do bazy danych programu Configuration Manager w lokacji:  

-   W każdej centralnej lokacji administracyjnej i lokacji głównej jest wymagany co najmniej jeden dostawca programu SMS. W razie potrzeby można zainstalować dodatkowych dostawców.  
-   **Administratorzy programu SMS** grupy zabezpieczeń zapewnia dostęp do dostawcy programu SMS. Menedżer konfiguracji automatycznie utworzy tę grupę na serwerze lokacji i na każdym komputerze, na którym jest instalowane wystąpienie dostawcy programu SMS.  

-   Lokacje dodatkowe nie obsługują dostawcy programu SMS.  


Użytkownicy administracyjni programu Configuration Manager używa dostawcy programu SMS dostęp do informacji przechowywanych w bazie danych. Aby to zrobić, Administratorzy można użyć konsoli programu Configuration Manager, Eksploratora zasobów, narzędzia i skrypty niestandardowe. Dostawca programu SMS nie nawiązuje interakcji z klientami programu Configuration Manager. Gdy konsola programu Configuration Manager łączy się z lokacją, konsola programu Configuration Manager kwerendę usługi WMI na serwerze lokacji w celu zlokalizowania wystąpienia dostawcy programu SMS do użycia.  

 Dostawca programu SMS pomaga Wymuszanie zabezpieczeń programu Configuration Manager. Zwraca czy tylko te informacje, które użytkownik administracyjny, który korzysta z konsoli programu Configuration Manager jest autoryzowany do wyświetlenia.  

> [!IMPORTANT]  
>  Każdy komputer z dostawcą programu SMS dla lokacji jest w trybie offline, konsole programu Configuration Manager nie może nawiązać bazy danych lokacji.  

 Informacje o zarządzaniu dostawcą programu SMS znajdują się w sekcji [Zarządzanie konfiguracją dostawcy programu SMS](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) w temacie [Modyfikowanie infrastruktury programu System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md).  

## <a name="prerequisites-to-install-the-sms-provider"></a>Wymagania wstępne dotyczące instalacji dostawcy programu SMS  

 Aby obsługiwać dostawcę programu SMS:  

-   Komputer musi należeć do domeny mającej dwukierunkową relację zaufania z serwerem lokacji a systemami lokacji bazy danych lokacji.  

-   Komputer nie może mieć roli systemu lokacji z innej lokacji.  

-   Komputer nie może mieć dostawcy programu SMS z żadnej lokacji.  

-   Na komputerze musi być zainstalowany system operacyjny obsługiwany przez serwer lokacji.  

-   Komputer musi mieć co najmniej 650 MB wolnego miejsca na dysku do obsługi składników zestawu zautomatyzowanej wdrażania (systemu Windows Windows ADK), które są instalowane z dostawcy programu SMS. Aby uzyskać więcej informacji o zestawie Windows ADK i dostawcy programu SMS, zobacz sekcję [Wymagania dotyczące wdrażania systemu operacyjnego dla dostawcy programu SMS](#BKMK_WAIKforSMSProv) w tym temacie.  

##  <a name="bkmk_location"></a> Lokalizacje dostawcy programu SMS  
 Po zainstalowaniu lokacji można automatycznie zainstalować pierwszego dostawcę programu SMS dla lokacji. Można określić dowolną z następujących obsługiwanych lokalizacji dostawcy programu SMS:  

-   komputerze serwera lokacji;  

-   komputer bazy danych lokacji,  

-   Komputer klasy serwera, który nie ma dostawcy programu SMS lub roli systemu lokacji z innej lokacji  


Aby wyświetlić lokalizacje poszczególnych dostawców programu SMS jest zainstalowany w lokacji, wybierz **ogólne** kartę witryny **właściwości** okno dialogowe.  

 Każdy dostawca programu SMS obsługuje jednocześnie połączenia z wielu żądań. Jedynymi ograniczeniami obsługi owych połączeń są: liczba połączeń z serwerem dostępnych na komputerze dostawcy programu SMS oraz dostępne zasoby na komputerze dostawcy programu SMS obsługujące żądania połączeń.  

 Po zainstalowaniu lokacji można ponownie uruchomić Instalatora na serwerze lokacji w celu zmiany lokalizacji istniejącego dostawcy programu SMS lub zainstalowania dodatkowych dostawców programu SMS w tej lokacji. Na komputerze można zainstalować tylko jednego dostawcę programu SMS. Nie można również zainstalować dostawcy programu SMS z więcej niż jednej lokacji.  

 Aby zidentyfikować zalety i wady zainstalowania dostawcy programu SMS w poszczególnych obsługiwanych lokalizacjach, należy użyć następujących elementów:  

 **Serwer lokacji programu Configuration Manager**  

-   **Zalety:**  

    -   Dostawca programu SMS nie używa zasobów systemu komputera bazy danych lokacji.  

    -   Ta lokalizacja może zapewnić lepszą wydajność dostawcy programu SMS w porównaniu z lokalizacją na komputerze innym niż serwer lokacji lub komputer bazy danych lokacji.  

-   **Wady:**  

    -   Dostawca programu SMS używa zasobów systemu i sieciowych, które mogłyby być przeznaczone do obsługi operacji serwera lokacji.  


**Serwer SQL, na którym znajduje się baza danych lokacji**  

-   **Zalety:**  

    -   Dostawca programu SMS nie używa zasobów systemu lokacji na serwerze lokacji.  

    -   Ta lokalizacja może zapewnić największą wydajność spośród wszystkich trzech lokalizacji, pod warunkiem dostępności odpowiednich zasobów serwera.  

-   **Wady:**  

    -   Dostawca programu SMS używa zasobów systemu i sieciowych, które mogłyby być przeznaczone do obsługi operacji bazy danych lokacji.  

    -   Baza danych lokacji znajduje się w klastrowanym wystąpieniu programu SQL Server, nie można użyć w tej lokalizacji.  


**Komputer inny niż serwer lokacji lub komputer bazy danych lokacji**  

-   **Zalety:**  

    -   Dostawca programu SMS nie używa zasobów serwera lokacji ani komputera bazy danych lokacji.  

    -   Ten typ lokalizacji umożliwia wdrożenie dodatkowych dostawców programu SMS w celu zapewnienia wysokiego poziomu dostępności do obsługi połączeń.  

-   **Wady:**  

    -   Wydajność dostawcy programu SMS może ulec zmniejszeniu z uwagi dodatkowe sieci działania, która jest wymagana do zapewnienia koordynacji z serwerem lokacji a komputerem bazy danych lokacji.  

    -   Ten serwer musi być zawsze dostępny na komputerze bazy danych lokacji i na wszystkich komputerach z konsoli programu Configuration Manager zainstalowane.  

    -   Ta lokalizacja może używać zasobów systemu, które byłyby w innym przypadku przeznaczone do obsługi innych usług.  

##  <a name="BKMK_SMSProvLanguages"></a>Języki dostawcy programu SMS — informacje  
 Dostawca programu SMS działa niezależnie od języka wyświetlania wybranego na komputerze, na którym jest zainstalowany.  

 Gdy użytkownik administracyjny lub dane żądań proces programu Configuration Manager przy użyciu dostawcy programu SMS, dostawca programu SMS próbuje zwrócić te dane w formacie który jest zgodny z językiem systemu operacyjnego komputera wysyłającego żądanie.

Sposób próbuje język jest nieco pośrednich. Dostawca programu SMS nie tłumaczy informacji z jednego języka na drugi. Zamiast tego gdy dane są zwracane do wyświetlenia w konsoli programu Configuration Manager, język wyświetlania danych zależy od źródła obiektu i typu magazynu.  

 Gdy dane obiektu są przechowywane w bazie danych, dostępne języki są uzależnione od następujących czynników:  

-   Obiekty utworzone przez Menedżera konfiguracji są przechowywane w bazie danych przy użyciu funkcji obsługi wielu języków. Obiekt jest przechowywany z zastosowaniem języków skonfigurowanych w lokacji utworzenia obiektu po uruchomieniu Instalatora. Te obiekty są wyświetlane w konsoli programu Configuration Manager w języku wyświetlania komputera wysyłającego żądanie, jeśli ten język jest dostępny dla obiektu. Jeśli obiektu nie można wyświetlić w języku wyświetlania komputera wysyłającego żądanie, zostanie wyświetlony w języku domyślnym, tj. angielskim.  

-   Obiekty tworzone przez użytkownika administracyjnego są przechowywane w bazie danych z zastosowaniem języka użytego do utworzenia obiektu. Te obiekty będą wyświetlane w konsoli programu Configuration Manager w tym samym języku. Nie można przetłumaczyć przez dostawcę programu SMS i nie ma opcji obsługi wielu języków.  

##  <a name="BKMK_MultiSMSProv"></a> Korzystanie z wielu dostawców programu SMS  
 Po ukończeniu instalacji lokacji można zainstalować w niej dodatkowych dostawców programu SMS. Aby zainstalować dodatkowych dostawców programu SMS, należy uruchomić Instalatora programu Configuration Manager na serwerze lokacji. Warto zastanowić się nad zainstalowaniem dodatkowych dostawców programu SMS w przypadku spełnienia któregoś z następujących warunków:  

-   Będziesz mieć wielu użytkowników administracyjnych, którzy Uruchom konsolę programu Configuration Manager i połączenie z lokacją, w tym samym czasie.  

-   Korzystasz z zestawu SDK programu Configuration Manager lub innych produktów mogących powodować częste wywołania dostawcy programu SMS.  

-   konieczność zapewnienia wysokiego poziomu dostępności dostawcy programu SMS.  


Wielu dostawców programu SMS zainstalowanych w lokacji i zostanie wysłane żądanie połączenia, lokacji losowo przypisuje do każdego nowego żądania połączenia, aby użyć zainstalowanego dostawcę programu SMS. Nie można określić lokalizacji dostawcy programu SMS używanej w określonej sesji połączenia.  

> [!NOTE]  
>  Należy rozważyć zalety i wady każdej lokalizacji dostawcy programu SMS. Równoważenie powyższe zagadnienia, z informacjami o braku możliwości kontrolowania, który dostawca programu SMS jest używany do każdego nowego połączenia.  

Na przykład gdy połączysz najpierw konsolę programu Configuration Manager do lokacji, połączenie kwerendę usługi WMI na serwerze lokacji, aby zidentyfikować wystąpienie dostawcy programu SMS używanego przez konsolę. To wystąpienie dostawcy programu SMS będzie używane przez konsolę programu Configuration Manager do momentu zakończenia sesji konsoli programu Configuration Manager. Jeśli sesja zakończy się, ponieważ komputer dostawcy programu SMS przestanie być dostępny w sieci, po ponownym uruchomieniu konsoli programu Configuration Manager, lokacji po prostu powtarza identyfikowania wystąpienie dostawcy programu SMS, aby nawiązać połączenie. Istnieje możliwość przypisania tego samego niedostępnego komputera dostawcy programu SMS. W takim przypadku możesz spróbować ponownie połączyć konsolę programu Configuration Manager do momentu przypisania dostępnego komputera dostawcy programu SMS.  

##  <a name="BKMK_AboutSMSAdmins"></a> Grupa Administratorzy SMS — informacje  
 Grupa Administratorzy SMS służy do udzielania dostępu administracyjnego do dostawcy programu SMS. Taka grupa zostanie utworzona automatycznie na serwerze lokacji podczas jej instalacji oraz na każdym komputerze z zainstalowanym dostawcą programu SMS. Poniżej przedstawiono dodatkowe informacje na temat grupy Administratorzy SMS:  

-   Na komputerze będącym serwerem członkowskim grupa Administratorzy SMS zostanie utworzona jako grupa lokalna.  

-   Na komputerze będącym kontrolerem domeny grupa Administratorzy SMS zostanie utworzona jako grupa lokalna domeny.  

-   Gdy dostawca programu SMS zostanie odinstalowany z komputera, grupa Administratorzy SMS nie zostanie usunięta z tego komputera.  


Aby użytkownik mógł pomyślnie nawiązać połączenie z dostawcą programu SMS, jego konto musi być członkiem grupy Administratorzy SMS. Każdy użytkownik administracyjny skonfigurowany w konsoli programu Configuration Manager jest automatycznie dodawane do grupy Administratorzy SMS na każdym serwerze lokacji i na każdym komputerze dostawcy programu SMS w hierarchii. Usunięcie użytkownika administracyjnego z konsoli programu Configuration Manager, ten użytkownik zostaje usunięty z grupy administratorów programu SMS na każdym serwerze lokacji i na każdym komputerze dostawcy programu SMS w hierarchii.  

Po nawiązaniu połączenia do dostawcy programu SMS, administracji opartej na rolach Określa, jakie programu Configuration Manager zasobów tego użytkownika do dostęp lub zarządzać.  

Można wyświetlać i konfigurować uprawnienia grupy administratorów programu SMS za pomocą przystawki MMC sterowania usługą WMI. Domyślnie użytkownicy z kategorii **Wszyscy** mają uprawnienia **Wykonywanie metod**, **Zapis dostawcy**oraz **Włączanie konta** . Gdy użytkownik połączy się dostawcy programu SMS, użytkownik uzyska dostęp do danych w bazie danych lokacji, na podstawie praw zabezpieczeń administracji opartej na rolach, zdefiniowanych w konsoli programu Configuration Manager. Grupa Administratorzy SMS ma jawnie przyznane uprawnienia **włączanie konta** i **Włączanie zdalne** uprawnienia **Root\SMS** przestrzeni nazw.  

> [!NOTE]  
>  Każdy użytkownik administracyjny używający zdalnej konsoli programu Configuration Manager wymaga uprawnień modelu DCOM zdalnej aktywacji na komputerze serwera lokacji i komputerze dostawcy programu SMS. Mimo że można przyznać tych praw dowolnemu użytkownikowi lub grupie, jest dobrym rozwiązaniem jest ich udzielić grupie Administratorzy SMS w celu ułatwienia administracji. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie uprawnień modelu DCOM dotyczących zdalnych konsol programu Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) w temacie [Modyfikowanie infrastruktury programu System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md).  


##  <a name="BKMK_SMSProvNamespace"></a>Przestrzeń nazw dostawcy programu SMS — informacje  
Struktura dostawcy programu SMS jest definiowana przez schemat usługi WMI. Przestrzenie nazw schematu opisują lokalizację danych programu Configuration Manager w ramach schematu dostawcy programu SMS. Poniższa tabela zawiera niektóre z popularnych przestrzeni nazw używanych przez dostawcę programu SMS.  

|Przestrzeń nazw|Opis|  
|---------------|-----------------|  
|Root\SMS\site_*&lt;kod lokacji\>*|Dostawca programu SMS, używany często przez konsolę Configuration Manager, Eksploratora zasobów, narzędzia programu Configuration Manager i skryptów.|  
|Root\SMS\SMS_ProviderLocation|Lokalizację komputerów dostawcy programu SMS dla lokacji.|  
|Root\CIMv2|Lokalizacja zinwentaryzowana na potrzeby informacji dotyczących przestrzeni nazw usługi WMI podczas inwentaryzacji sprzętu i oprogramowania.|  
|Nazwy Root\CCM|Zasady konfiguracji klienta programu Configuration Manager i dane klienta.|  
|root\CIMv2\SMS|Lokalizacja klas, które są zbierane przez agenta klienta spisu raportowania spisu. Te ustawienia są kompilowane przez klientów podczas oceny zasad komputera i opierają się na konfiguracji ustawień klienta dla komputera.|  

##  <a name="BKMK_WAIKforSMSProv"></a>Wymagania dotyczące wdrażania systemu operacyjnego dla dostawcy programu SMS  
Komputer, na którym jest instalowane wystąpienie dostawcy programu SMS musi mieć wymaganą wersję zestawu Windows ADK, który wymaga wersji programu Configuration Manager używasz.  

 -   Na przykład w wersji 1511 programu Configuration Manager wymaga wersji systemu Windows 10 RTM (10.0.10240) zestawu Windows adk.  

 -   Aby uzyskać więcej informacji na temat tego wymagania, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

Podczas zarządzania wdrożeniami systemu operacyjnego, zestaw Windows ADK umożliwia dostawcy programu SMS wykonywanie różnych zadań, takich jak:  

-   Wyświetlanie szczegółów pliku WIM.  

-   Dodać pliki sterowników do istniejących obrazów rozruchowych.  

-   Utwórz rozruchu. Pliki ISO.  


Instalacja zestawu Windows ADK wymaga do 650 MB wolnego miejsca na dysku każdego komputera, na którym ma być zainstalowany dostawca programu SMS. To wymaganie miejsca na dysku jest konieczne dla programu Configuration Manager mógł zainstalować obrazy rozruchowe Windows PE.  
