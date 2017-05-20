---
title: "Przypisać klientów do lokacji | Dokumentacja firmy Microsoft"
description: "Przypisać klientów do lokacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ba9b623f-6e86-4006-93f2-83d563de0cd0
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: a0ccd453fbe346c239eb6e37bc3ed557487b1e27
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-assign-clients-to-a-site-in-system-center-configuration-manager"></a>Jak przypisywać klientów do lokacji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zainstalowaniu klienta programu System Center Configuration Manager, należy przyłączyć lokacji głównej programu Configuration Manager, aby można było zarządzać. Nosi nazwę lokacji, który klient łączy się jego *przypisanej lokacji*. Klienci nie mogą być przypisani do centralnej lokacji administracyjnej ani lokacji dodatkowej.  

Proces przypisywania dzieje się po pomyślnym zainstalowaniu klienta i określa, która lokacja będzie zarządzać komputerem klienckim. Można bezpośrednio przypisać klienta do lokacji lub którego klient automatycznie znajdzie odpowiednią lokację na podstawie bieżącej lokalizacji sieciowej lub lokacji rezerwowej skonfigurowanej dla hierarchii można użyć automatycznego przypisania lokacji.

Po zainstalowaniu klienta urządzenia przenośnego podczas rejestracji menedżera konfiguracji, urządzenie jest zawsze automatycznie przypisany do lokacji. Po zainstalowaniu klienta na komputerze, można wybrać, czy należy przypisać klienta do lokacji. Jeśli jednak klient został zainstalowany, lecz nie został przypisany, klient nie będzie zarządzany do chwili pomyślnego przypisania lokacji.  
 

> [!NOTE]  
>  Zawsze należy przypisać klientów do lokacji zainstalowaną tę samą wersję programu Configuration Manager. Należy unikać przypisywania klienta programu Configuration Manager z nowszą wersją do lokacji w starszej wersji.   W razie potrzeby zaktualizować lokacji podstawowej do tej samej wersji programu Configuration Manager, używanego dla klientów.  

Po przypisaniu klienta do lokacji klient pozostanie do niej przypisany, nawet jeśli zmieni adres IP i przejdzie do innej lokacji. Tylko administrator może ręcznie przypisać klienta do innej lokacji lub usunąć przypisanie klienta.  

> [!WARNING]  
>  Klient nie pozostanie przypisany do danej lokacji jedynie wtedy, jeśli zostanie przypisany na urządzeniu Windows Embedded po włączeniu filtrów zapisu. Jeśli filtry zapisu nie zostaną wyłączone przed przypisaniem klienta, po ponownym uruchomieniu urządzenia zostanie przywrócony oryginalny stan przypisania lokacji klienta.  
>   
>  Na przykład, jeśli dla klienta zostało skonfigurowane automatyczne przypisanie lokacji, po uruchomieniu klient może zostać przypisany do innej lokacji. Jeśli klient nie jest skonfigurowany do automatycznego przypisania lokacji, ale wymaga ręcznego przypisania lokacji, należy należy ręcznie przypisać ponownie klienta po uruchomieniu zanim Zarządzanie klientem ponownie przy użyciu programu Configuration Manager.  
>   
>  Aby uniknąć tego zachowania, przed przypisaniem klienta na urządzeniach osadzonych należy wyłączyć filtry zapisu, sprawdzić, czy lokacja została przypisana pomyślnie i włączyć filtry zapisu.  

Przypisanie klienta nie powiedzie się, oprogramowanie klienckie będzie nadal zainstalowane, ale pozostanie niezarządzany. Klient nie jest zarządzany, jeśli jest zainstalowany, ale nie został przypisany do lokacji, lub jest przypisany do lokacji, lecz nie może komunikować się z punktem zarządzania.  

##  <a name="using-manual-site-assignment-for-computers"></a>Korzystanie z ręcznego przypisania lokacji komputerów  
 Komputery klienckie można ręcznie przypisać do lokacji za pomocą następujących dwóch metod:  

-   Zastosowanie właściwości instalacji klienta określającej kod lokacji.  

-   Określenie kodu lokacji w Panelu sterowania programu **Configuration Manager**.  

> [!NOTE]  
>  Ręcznie przypisać komputer kliencki do kodu lokacji programu Configuration Manager, który nie istnieje, przypisanie lokacji nie powiedzie się.   

##  <a name="BKMK_AutomaticAssignment"></a> Korzystanie z automatycznego przypisania lokacji komputerów  
 Automatyczne przypisanie lokacji może nastąpić podczas wdrażania klienta lub po kliknięciu przycisku **Odkryj** na karcie **Zaawansowane** we **właściwościach programu Configuration Manager** w Panelu sterowania. Klient programu Configuration Manager porównuje własną lokalizację sieciową z granicami skonfigurowanymi w hierarchii programu Configuration Manager. Jeśli lokalizacja sieciowa klienta znajduje się w grupie granic włączonej w celu przypisania lokacji lub hierarchia została skonfigurowana dla lokacji rezerwowej, klient zostanie automatycznie przypisany do tej lokacji bez konieczności określania kodu lokacji.  

 Granice można skonfigurować w jeden z następujących sposobów:  

-   Podsieć IP  

-   Lokacja usługi Active Directory  

-   Prefiks adresu IPv6  

-   Zakres adresów IP  

> [!NOTE]  
>  Jeśli klient programu Configuration Manager ma wiele kart sieciowych i w związku z tym ma wiele adresów IP, adres IP służący do oceny przypisania lokacji klienta są przypisywane losowo.  

 Informacje dotyczące sposobu konfigurowania grup granic w celu przypisania lokacji oraz konfigurowania lokacji rezerwowej w celu automatycznego przypisania lokacji znajdują się w temacie [Definiowanie granic lokacji i grup granic w programie System Center Configuration Manager](../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

 Klientów programu Configuration Manager, którzy używają automatycznego przypisania lokacji próbuje odnaleźć witryny grup granic, które są publikowane w usługach domenowych w usłudze Active Directory. W przypadku niepowodzenia (na przykład w usłudze Active Directory, schemat nie zostanie rozszerzony dla programu Configuration Manager lub klienci są komputerami grupy roboczej), klientów można uzyskać informacje o grupach granic w punkcie zarządzania.  

 Użytkownik może określić punkt zarządzania, z którego będą korzystały komputery klienckie po ich zainstalowaniu, lub klienci mogą znaleźć punkt zarządzania przy użyciu publikowania DNS lub usługi WINS.  

 Jeśli klient nie może znaleźć lokacji z przypisaną grupą granic zawierającej jej lokalizację sieciową, a hierarchia nie ma lokacji rezerwowej, klient będzie ponawiać próbę przypisania do lokacji co 10 minut.  

 Nie można automatycznie przypisać komputerów klienckich programu Configuration Manager do lokacji, jeśli dowolny z następujących warunków, a następnie trzeba je ręcznie przypisać:  

-   Komputery klienckie są obecnie przypisane do lokacji.  

-   Komputery klienckie są połączone z Internetem lub zostały skonfigurowane wyłącznie jako klienci internetowi.  

-   Lokalizacja sieciowa komputerów klienckich nie znajduje się w jednej ze skonfigurowanych grup granic w hierarchii programu Configuration Manager, a dla hierarchii nie istnieje lokacja rezerwowa.  

##  <a name="completing-site-assignment-by-checking-site-compatibility"></a>Kończenie przypisania lokacji przez sprawdzenie zgodności lokacji  
 Po znalezieniu przypisanej lokacji, wersja i system operacyjny klienta jest sprawdzany w celu zapewnienia, że lokacji programu Configuration Manager można nim zarządzać. Na przykład programu Configuration Manager nie może zarządzać klientów programu Configuration Manager 2007, System Center 2012 Configuration Manager lub klientami z systemem operacyjnym Windows 2000.  

 Przypisanie lokacji nie powiedzie się, po przypisaniu klienta z systemem Windows 2000 do lokacji programu Configuration Manager. Po przypisaniu klienta programu Configuration Manager 2007 lub klienta programu System Center 2012 Configuration Manager do lokacji programu Configuration Manager (bieżącej gałęzi) przypisanie lokacji powiedzie się, aby obsługiwać automatyczne uaktualnienie klienta. Jednakże do momentu uaktualnienia starszych klientów Generowanie klienta programu Configuration Manager (bieżącej gałęzi), programu Configuration Manager nie może zarządzać tego klienta przy użyciu ustawień klienta, aplikacji lub aktualizacji oprogramowania.  

> [!NOTE]  
>  Aby umożliwić przypisywanie lokacji programu Configuration Manager 2007 lub System Center 2012 Configuration Manager klienta do lokacji programu Configuration Manager (bieżącej gałęzi), należy skonfigurować automatyczne uaktualnienie klienta w hierarchii. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

Program Configuration Manager sprawdza również, czy użytkownik przypisał klienta programu Configuration Manager (bieżącej gałęzi) do lokacji, która je obsługuje. Następujące scenariusze mogą wystąpić podczas migracji z poprzednich wersji programu Configuration Manager.  

-   Scenariusz: Użyto automatycznego przypisania lokacji i swoje granice pokrywają się z tymi określonymi w poprzedniej wersji programu Configuration Manager.  

     W takim przypadku klient automatycznie podejmie próbę odnalezienia lokacji programu Configuration Manager (bieżącej gałęzi).  

     Klient sprawdzi najpierw usługi domenowe Active Directory i w razie napotkania lokacji programu Configuration Manager (bieżącej gałęzi) opublikowane przypisanie lokacji powiedzie się. W przypadku niepowodzenia (na przykład programu Configuration Manager lokacja nie jest opublikowana lub komputer jest klientem grupy roboczej), klient sprawdzi informacje o lokacji w przypisanym punkcie zarządzania.  

    > [!NOTE]  
    >  Przypisaniem punktu zarządzania do klienta podczas instalacji klienta za pomocą właściwości Client.msi **SMSMP =&lt;nazwa_serwera >**.  

     W przypadku gdy obie metody zawiodą, przypisanie lokacji nie powiedzie się, a użytkownik będzie musiał ręcznie przypisać klienta.  

-   Scenariusz: Masz przypisane przy użyciu określonego kodu lokacji zamiast automatycznego przypisania lokacji klienta programu Configuration Manager (bieżącej gałęzi), a określony przez pomyłkę kod lokacji dla wersji programu Configuration Manager wcześniejszych niż System Center 2012 R2 Configuration Manager.  

     W takim przypadku przypisanie lokacji nie powiedzie się i należy ręcznie przypisać ponownie klienta do lokacji programu Configuration Manager (bieżącej gałęzi).  

 Sprawdzanie zgodności lokacji wymaga spełnienia jednego z następujących warunków:  

-   Klient ma dostęp do informacji o lokacji programu publikowanych w usługach domenowych w usłudze Active Directory.  

-   Klient może komunikować się z punktem zarządzania w lokacji.  

 Jeśli sprawdzanie zgodności lokacji nie zakończyło się pomyślnie, przypisanie lokacji nie powiedzie się, a klient nadal będzie niezarządzane sprawdzanie zgodności lokacji zostanie ponownie uruchomione zakończy się pomyślnie.  

 Sprawdzanie zgodności lokacji nie zostanie wykonane, jeśli klient został skonfigurowany dla internetowego punktu zarządzania. W takim przypadku stają się sprawdzanie zgodności. W przypadku przypisania klientów do lokacji zawierającej internetowe systemy lokacji i określenia internetowego punktu zarządzania należy sprawdzić, czy klient został przypisany do poprawnej lokacji. Jeśli przez pomyłkę przypisać klienta do lokacji programu Configuration Manager 2007, witryny System Center 2012 Configuration Manager, lub do lokacji programu Configuration Manager nie ma ról systemu lokacji internetowych, klient będzie mógł być niezarządzane.  

##  <a name="locating-management-points"></a>Lokalizowanie punktów zarządzania  
 Po pomyślnym przypisaniu klienta do lokacji klient zlokalizuje punkt zarządzania w lokacji.  

 Lista punktów zarządzania, które mogą łączą się z witryny pobierania przez komputery klienckie. Dzieje się tak po każdym uruchomieniu klienta, lub co 25 godzin lub po wykryciu przez klienta zmiany sieci, takie jak komputer rozłącza i ponownie nawiąże połączenie w sieci lub otrzymaniu nowego adresu IP. Lista zawiera punkty zarządzania w sieci intranet oraz określa, czy punkty te akceptują połączenia klienckie przy użyciu protokołu HTTP lub HTTPS. Jeśli komputer kliencki jest połączony z Internetem, a klient nie ma jeszcze listy punktów zarządzania, klient nawiąże połączenie z określonym internetowym punktem zarządzania w celu uzyskania listy punktów zarządzania. Jeśli klient ma listę punktów zarządzania przypisanej lokacji, wybierze punkt, z którym nawiąże połączenie:  

-   Jeśli klient jest połączony z siecią intranet i ma prawidłowy certyfikat PKI, którego może użyć, klient będzie preferował punkty zarządzania HTTPS zamiast punktów zarządzania HTTP. Następnie klient zlokalizuje najbliższy punkt zarządzania na podstawie członkostwa w lesie.  

-   Jeśli klient jest połączony z Internetem, losowo wybiera jeden z punktów zarządzania internetowego.  

Urządzenie przenośne zarejestrowane przez program Configuration Manager łączyć się tylko z jednym zarządzania punkt w przypisanej lokacji i nigdy nie nawiązują połączenia z punktami zarządzania w lokacjach dodatkowych. Ci klienci zawsze nawiązują połączenie przy użyciu protokołu HTTPS, a punkt zarządzania musi być skonfigurowany tak, aby akceptował połączenia klienckie przez Internet. Jeśli punkt zarządzania więcej niż jeden dla klientów urządzeń przenośnych w lokacji głównej, Configuration Manager losowo wybiera się, że jeden z tych punktów zarządzania w trakcie przypisywania, a klient urządzenia przenośnego będzie nadal używał tego samego punktu zarządzania.  

Po pobraniu przez klienta zasady klienta z punktu zarządzania w lokacji klient stanie się klientem zarządzanym.  

##  <a name="downloading-site-settings"></a>Pobieranie ustawień lokacji  
 Po pomyślnym przypisaniu lokacji i odnalezieniu przez klienta punktu zarządzania komputer kliencki korzystający z usług domenowych w usłudze Active Directory w celu sprawdzenia zgodności lokacji pobierze klienckie ustawienia lokacji przypisanej lokacji. Ustawienia te zawierają kryteria wyboru certyfikatu klienta i numery portów żądań klienta oraz określają, czy ma być używana lista odwołania certyfikatów. Klient będzie okresowo sprawdzał te ustawienia.  

 Gdy komputery klienckie nie mogą uzyskać ustawień lokacji z usług domenowych w usłudze Active Directory, pobierają je z punktu zarządzania. Komputery klienckie można również uzyskać ustawienia lokacji, gdy są one zainstalowane za pomocą wypychania klienta lub określić je ręcznie przy użyciu CCMSetup.exe i właściwości instalacji klienta. Aby uzyskać więcej informacji o właściwościach instalacji klienta, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

##  <a name="downloading-client-settings"></a>Pobieranie ustawień klienta  
 Wszyscy klienci pobierają domyślne zasady ustawień klienta wraz z wszelkimi mającymi zastosowanie niestandardowymi zasadami ustawień klienta. Program Software Center wymaga tych zasad konfiguracji klienta na komputerach z systemem Windows i powiadomi użytkownika, że nie będzie działał prawidłowo przed pobraniem tych informacji o konfiguracji. W zależności od skonfigurowanych ustawień klienta początkowe pobieranie ustawień klienta może trochę potrwać, a niektóre zadania zarządzania klientem mogą nie zostać uruchomione przed zakończeniem tego procesu.  

##  <a name="verifying-site-assignment"></a>Weryfikowanie przypisania lokacji  
 Można sprawdzić Powodzenie przypisania lokacji przez jedną z następujących metod:  

-   W przypadku klientów na komputerach z systemem Windows za pomocą Menedżera konfiguracji w Panelu sterowania i sprawdź, czy kod lokacji jest prawidłowo wyświetlany na **witryny** kartę.  

-   W przypadku komputerów klienckich w **zasoby i zgodność** obszaru roboczego > **urządzeń** węzła, sprawdź, czy komputer jest wyświetlany **tak** dla **klienta** kolumny i lokacji głównej, poprawna kod **kod lokacji** kolumny.  

-   W przypadku klienckich urządzeń przenośnych użyj kolekcji **Wszystkie urządzenia przenośne** w obszarze roboczym **Zasoby i zgodność** , aby sprawdzić, czy w kolumnie **Klient** urządzenia przenośnego jest wyświetlana wartość **Tak** oraz czy w kolumnie **Kod lokacji** jest wyświetlany prawidłowy kod lokacji głównej.  

-   Użyj raportów dotyczących przypisania klienta i rejestracji urządzenia przenośnego.  

-   W przypadku komputerów klienckich użyj na kliencie pliku LocationServices.log.  

##  <a name="roaming-to-other-sites"></a>Przejście do innych lokacji  
 Gdy komputery klienckie w intranecie są przypisane do lokacji głównej, ale zmieniają swoją lokalizację sieciową w taki sposób, że przechodzą do grupy granic skonfigurowanej dla innej lokacji, traktuje się je jako przeniesione do innej lokacji. Gdy ta lokacja jest lokacją dodatkową dla przypisanej lokacji, klienci mogą używać punktu zarządzania w lokacji dodatkowej, aby pobierać zasady klienta i przekazywać dane klienta w celu uniknięcia przesyłania tych danych przez potencjalnie wolną sieć. Jeśli jednak Ci klienci przejdą do granic innej lokacji głównej lub dodatkowej, która nie jest lokacją podrzędną przypisanej do nich lokacji, mogą oni zawsze używać punktu zarządzania w swojej przypisanej lokacji, aby pobierać zasady klienta oraz przekazywać dane do swojej lokacji.  

 Te komputery klienckie, które przechodzą do innych lokacji (wszystkie lokacje główne i wszystkie lokacje dodatkowe), mogą zawsze używać punktów zarządzania w innych lokacjach w ramach żądań lokalizacji zawartości. Punkty zarządzania w bieżącej lokacji mogą udostępniać klientom listy punktów dystrybucji zawierających zawartość żądaną przez klientów.  

 Dla komputerów klienckich, które są skonfigurowane do zarządzania klientami wyłącznie przez Internet i urządzeń przenośnych i komputerów Mac, które są zarejestrowane przez program Configuration Manager mogą się komunikować tylko z punktami zarządzania w przypisanej lokacji. Tacy klienci nigdy nie komunikują się z punktami zarządzania w lokacjach dodatkowych ani z punktami zarządzania w innych lokacjach głównych.  

