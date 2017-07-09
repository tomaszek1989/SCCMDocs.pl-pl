---
title: "Punktu dystrybucji bazującego na chmurze | Dokumentacja firmy Microsoft"
description: "Informacje o konfiguracji i ograniczenia dotyczące używania punktu dystrybucji w chmurze w programie System Center Configuration Manager."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cd9c725-6b42-427d-9191-86e67f84e48c
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6ee0ed635ab81b5e454e3cd85637ff3e20dbb34
ms.openlocfilehash: 8caf3319d93b98680ed4a719a8db714c7e4e96ce
ms.contentlocale: pl-pl
ms.lasthandoff: 06/08/2017


---
# <a name="use-a-cloud-based-distribution-point-with-system-center-configuration-manager"></a>Używanie chmurowego punktu dystrybucji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Punkt dystrybucji w chmurze jest punkt dystrybucji programu System Center Configuration Manager, który jest hostowana na platformie Microsoft Azure. Poniższe informacje mają pomóc dowiedzieć się więcej na temat konfiguracji i ograniczeń dotyczących korzystania z chmurowego punktu dystrybucji.

Po zainstalowaniu lokacji głównej i są gotowe do zainstalowania punktu dystrybucji w chmurze, zobacz [zainstalować punkty dystrybucji w chmurze na platformie Azure](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md).


## <a name="plan-to-use-a-cloud-based-distribution-point"></a>Planowanie używania chmurowego punktu dystrybucji
W przypadku korzystania z chmurowych punktów dystrybucji należy wykonać następujące czynności:  

-   **Konfigurowanie ustawień klienta** umożliwia użytkownikom i urządzeniom dostęp do zawartości.  

-   **Określ lokację główną do zarządzania przesyłaniem zawartości** do punktu dystrybucji.  

-   **Określ progi** ilości zawartości, która ma być przechowywany w punkcie dystrybucji oraz ilości zawartości, który chcesz umożliwić klientom transfer z punktu dystrybucji.  


Na podstawie progów skonfigurowanych, programu Configuration Manager może zgłaszać alerty w celu ostrzeżenia użytkownika, gdy łączna ilość zawartości przechowywanej w punkcie dystrybucji zbliża się wielkość określona magazynu lub gdy ilość danych transferowanych przez klientów zbliża się zdefiniowanych progów.  

Punkty dystrybucji w chmurze obsługują kilka funkcji, które także są oferowane przez lokalne punkty dystrybucji:  

-   Zarządzać punktami dystrybucji w chmurze indywidualnie lub jako elementy członkowskie dystrybucji grupy punktów.  

-   Punkt dystrybucji w chmurze można użyć jako rezerwowej lokalizacji zawartości.  

-   Punkty te zapewniają obsługę klientów intranetowych i internetowych.  


Punkty dystrybucji oparte na chmurze zapewniają następujące dodatkowe korzyści:  

-   Zawartość wysyłana do punktu dystrybucji w chmurze jest szyfrowana przez program Configuration Manager, przed Menedżera konfiguracji wysyła go do platformy Azure.  

-   Na platformie Azure można ręcznie skalować usługę w chmurze do zmieniających się wymagań dotyczących żądań zawartości przez klientów bez konieczności instalowania i udostępniania dodatkowych punktów dystrybucji.  

-   Chmurowy punkt dystrybucji obsługuje pobieranie zawartości przez klientów skonfigurowanych w usłudze Windows BranchCache.  


Chmurowe punkty dystrybucji charakteryzują się następującymi ograniczeniami:  

-  Przed użyciem wersji 1610 z KB4010155 poprawkę, nie można używać z punktem dystrybucji w chmurze w celu hostowania pakietów aktualizacji oprogramowania. Ten problem jest rozwiązany, począwszy od wersji 1702 lub nowszy.  

-   Nie można używać punktu dystrybucji w chmurze dla środowiska PXE lub wdrożeniach z obsługą multiemisji.  

-   Klienci nie mogą używać chmurowego punktu dystrybucji jako lokalizacji zawartości dla sekwencji zadań wdrożonej przy użyciu opcji **W razie potrzeby pobierz zawartość lokalnie przez uruchomienie sekwencji zadań**. Natomiast sekwencje zadań wdrożone przy użyciu opcji **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań** mogą używać chmurowego punktu dystrybucji jako prawidłowych lokalizacji zawartości.  

-   Chmurowy punkt dystrybucji nie obsługuje pakietów uruchomionych z poziomu punktu dystrybucji. Całą zawartość musi być pobrana przez klienta, a następnie uruchom lokalnie.  

-   Chmurowy punkt dystrybucji nie obsługuje przesyłania strumieniowego aplikacji przy użyciu programu Application Virtualization lub podobnych.  

-   Chmurowy punkt dystrybucji nie obsługuje wstępnie przygotowanej zawartości. Menedżer dystrybucji lokacji głównej, która zarządza punkt dystrybucji przesyła całą zawartość do punktu dystrybucji.  

-   Punktu dystrybucji w chmurze nie można skonfigurować jako punktu dystrybucji ściągania.  

##  <a name="BKMK_PrereqsCloudDP"></a> Wymagania wstępne dotyczące chmurowych punktów dystrybucji  
 W celu używania chmurowych punktów dystrybucji należy spełnić następującego wymagania wstępne:  

-   Subskrypcja platformy Azure (zobacz [o subskrypcjach i certyfikatach](#BKMK_CloudDPCerts) w tym temacie).

-   Certyfikat zarządzania podpisem lub publicznego klucza infrastruktury (PKI) do komunikacji z serwera lokacji podstawowej programu Configuration Manager do usługi w chmurze na platformie Azure (zobacz [o subskrypcjach i certyfikatach](#BKMK_CloudDPCerts) w tym temacie).

-   Certyfikat usługi (PKI) używanego przez klientów programu Configuration Manager do łączenia się z punktami dystrybucji w chmurze i pobierania z nich zawartości przy użyciu protokołu HTTPS.  

-  Urządzenia lub użytkownika musi mieć **punktów Zezwalaj na dostęp do dystrybucji chmury** ustawioną **tak** w kliencie ustawienie **usługi w chmurze** zanim urządzeniu lub użytkownikowi dostęp do zawartości z punktu dystrybucji w chmurze. Domyślnie to ustawienie ma wartość **Nie**.  

-   Klient musi mieć możliwość rozpoznania nazwy usługi w chmurze, która wymaga alias systemu nazw domen (DNS, Domain Name System) i rekord CNAME w obszarze nazw DNS.  

-   Aby używać chmurowego punktu dystrybucji, klient musi mieć dostęp do Internetu.  

##  <a name="BKMK_CloudDPCost"></a> Koszty korzystania z chmurowych punktów dystrybucji  
 Korzystając z punktu dystrybucji w chmurze, należy zaplanować koszty przechowywania danych i transferów pobierania, wykonujących klientów programu Configuration Manager.  

 Configuration Manager zawiera opcje, aby ułatwić kontrolę kosztów i monitorowanie dostępu do danych:  

-   Można kontrolować i monitorować ilość zawartości, która jest przechowywana w usłudze chmury.  

-   Można skonfigurować programu Configuration Manager w celu wysyłania alertów, gdy **progi** dla klienta pobierze osiągną lub przekroczą limit miesięczny.  

-   Ponadto można użyć buforowania równorzędnego (BranchCache systemu Windows) w celu zmniejszenia liczby transferów danych z punktów dystrybucji w chmurze przez klientów. Klienci programu Configuration Manager, które są skonfigurowane dla usługi BranchCache mogą przesyłać zawartość przy użyciu punktów dystrybucji w chmurze.  


**Opcje:**  

-   **Ustawienia klienta dla chmury**: Kontrolowanie dostępu do wszystkich punktów dystrybucji w chmurze w hierarchii przy użyciu **ustawień klienta**.  

     W oknie **Ustawienia klienta**kategoria **Ustawienia chmury** obsługuje ustawienie **Zezwalaj na dostęp do chmurowych punktów dystrybucji**. Domyślnie to ustawienie ma wartość **Nie**. Można włączyć to ustawienie dla użytkowników i urządzeń.  

-   **Progi transferów danych**: Możesz skonfigurować progi ilości danych, które mają być przechowywane w punkcie dystrybucji i ilości danych pobieranych przez klientów z punktu dystrybucji.  

     Progi dla chmurowych punktów dystrybucji są następujące:  

    -   **Próg alertu miejsca do magazynowania**: Próg alertu miejsca do magazynowania umożliwia ustawienie górnego limitu ilości danych lub zawartości przechowywanej w punkcie dystrybucji w chmurze. Programu Configuration Manager może wygenerować alert ostrzeżenia, jeśli pozostałe wolne miejsce osiągnie określony poziom, który określisz.  

    -   **Próg alertu transferu**: Próg alertu dotyczącego transferu ułatwia monitorowanie ilości zawartości przesyłanej z punktu dystrybucji do klientów w 30-dniowego okresu. Próg alertu transferu monitoruje transfer danych w ciągu 30 dni poprzedniego i może zgłaszać alertu ostrzegawczego i krytycznego, gdy transfer osiągnie zdefiniowane wartości.  

        > [!IMPORTANT]  
        >  Configuration Manager monitoruje transfer danych, ale nie zatrzymuje go po osiągnięciu określonego progu alertu transferu.  

 Progi dla każdego chmurowego punktu dystrybucji można określić podczas instalacji punktu dystrybucji lub edytować właściwości każdego chmurowego punktu dystrybucji po jego zainstalowaniu.  

-   **Alerty**: Można skonfigurować programu Configuration Manager, aby zgłaszał alerty dotyczące transferów danych do i z każdego punktu dystrybucji w chmurze, na podstawie progów transferu danych przez użytkownika. Te alerty umożliwiają monitorowanie transferów danych i mogą pomóc decyzję o Aby zatrzymać usługę chmury, dostosować zawartość przechowywanych w punkcie dystrybucji lub zmodyfikuj których klienci mogą używać chmurowych punktów dystrybucji punkty.  

     W co godzinę lokacja główna monitorująca punkt dystrybucji w chmurze pobiera dane transakcji z platformy Azure i zapisuje je w pliku CloudDP -&lt;ServiceName\>.log na serwerze lokacji. Program Configuration Manager ocenia następnie te informacje pod kątem przydziałów magazynu i transferu dla każdego punktu dystrybucji w chmurze. Gdy transfer danych osiągnie lub przekroczy określoną ilość ostrzeżenia lub alertów krytycznych, program Configuration Manager generuje odpowiedni alert.  

    > [!WARNING]  
    >  Ponieważ informacje o transferach danych są pobierane z usługi Azure co godzinę, wykorzystanie danych może przekroczyć próg ostrzegawczy lub krytyczny zanim programu Configuration Manager można uzyskać dostęp do danych i zgłosi alert.  

    > [!NOTE]  
    >  Alerty dla punktu dystrybucji w chmurze zależą od statystyk użycia z platformy Azure, który może potrwać do 24 godzin dostępności. Informacje o analityka magazynu platformy Azure, jak często Azure aktualizacji statystyk użycia w tym temacie [analityka magazynu](http://go.microsoft.com/fwlink/p/?LinkID=275111) w bibliotece MSDN.  


-   **Zatrzymanie lub uruchomienie usługi chmurowej na żądanie**: Opcja służy do zatrzymania usługi chmurowej w dowolnym momencie, aby uniemożliwić klientom ciągłe korzystanie z usługi. Zatrzymanie usługi chmurowej natychmiast uniemożliwia klientom pobranie z niej dodatkowej zawartości. Ponadto można ponownie uruchomić usługę chmurową, aby przywrócić klientom dostęp. Usługę chmurową można na przykład zatrzymać po osiągnięciu progów ilości danych.  

     Po zatrzymaniu usługa w chmurze nie usuwa zawartości z punktu dystrybucji i nie zapobiega przesyłaniu przez serwer lokacji dodatkowej zawartości do chmurowego punktu dystrybucji.  

     Aby zatrzymać usługę chmurową w konsoli programu Configuration Manager, wybierz punkt dystrybucji w **punkty dystrybucji w chmurze** węźle **usługi w chmurze**w **administracji** obszaru roboczego. Następnie wybierz **Zatrzymaj usługę** zatrzymać usługę chmurową, która działa na platformie Azure.  

##  <a name="BKMK_CloudDPCerts"></a> Informacje o subskrypcjach i certyfikatach dla chmurowych punktów dystrybucji  
 Punkty dystrybucji w chmurze wymagają certyfikatów, aby włączyć zarządzanie usługą w chmurze, który jest hostem punktu dystrybucji program Configuration Manager i zapewnić klientom dostęp do zawartości z rozkładem punkcie. Poniższe informacje zawiera przegląd informacji o tych certyfikatów. Aby uzyskać bardziej szczegółowe informacje, zobacz [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

 **Certyfikaty**  

-   **Certyfikat zarządzania do serwera lokacji do komunikacji między punktem dystrybucji**: Certyfikat zarządzania ustanawia relację zaufania między interfejsem API zarządzania platformy Azure i programu Configuration Manager. Tego uwierzytelniania program Configuration Manager, aby wywołać interfejs API Azure podczas wykonywania zadań, takich jak wdrażanie zawartości lub uruchamianie i zatrzymywanie usługi w chmurze. Przy użyciu usługi Azure, możesz utworzyć własne certyfikaty zarządzania, które mogą być certyfikaty z podpisem własnym lub certyfikatów wystawionych przez urząd certyfikacji (CA):  

    -   Określ plik .cer certyfikatu zarządzania na platformie Azure, podczas konfigurowania platformy Azure dla programu Configuration Manager. Plik .cer zawiera klucz publiczny certyfikatu zarządzania. Ten certyfikat należy przesłać na platformę Azure, przed zainstalowaniem punktu dystrybucji w chmurze. Ten certyfikat umożliwia dostęp do interfejsu API Azure program Configuration Manager.  

    -   Określ plik .pfx certyfikatu zarządzania do programu Configuration Manager po zainstalowaniu punktu dystrybucji w chmurze. Plik .pfx zawiera klucz prywatny certyfikatu zarządzania. Program Configuration Manager przechowuje ten certyfikat w bazie danych lokacji. Ponieważ plik .pfx zawiera klucz prywatny, należy podać hasło, aby zaimportować ten plik certyfikatu do bazy danych programu Configuration Manager.  

    W przypadku utworzenia certyfikatu z podpisem własnym, musi najpierw wyeksportować certyfikat jako plik cer, a następnie wyeksportować go ponownie jako plik pfx.  

    Opcjonalnie można określić jedną wersję **.publishsettings** pliku z zestawu Azure SDK 1.7. Informacje o plikach .publishsettings zapoznaj się z dokumentacją systemu Azure.  

    Aby uzyskać więcej informacji, zobacz [jak utworzyć certyfikat zarządzania](http://go.microsoft.com/fwlink/p/?LinkId=220281) i [jak dodać certyfikat zarządzania do subskrypcji platformy Azure](http://go.microsoft.com/fwlink/p/?LinkId=241722) w sekcji platformy Azure w bibliotece MSDN.  

-   **Certyfikat usługi komunikacji klienta z punktu dystrybucji**: Certyfikat usługi punktu dystrybucji w chmurze programu Configuration Manager ustanawia relację zaufania między klientami programu Configuration Manager i punktem dystrybucji w chmurze i zabezpiecza dane klientów pobierane przy użyciu protokołu Secure Socket Layer (SSL) za pośrednictwem protokołu HTTPS.  

    > [!IMPORTANT]  
    >  W polu podmiotu certyfikatu usługi należy określić unikatową nazwę pospolitą w domenie, która nie jest zgodna z żadnym urządzeniem dołączonym do domeny.  

   Przykład wdrożenia tego certyfikatu, zobacz sekcję **wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze** w temacie [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="bkmk_Tasks"></a> Typowe zadania związane z zarządzaniem chmurowymi punktami dystrybucji  

-   **Serwer lokacji do komunikacji między punktem dystrybucji w chmurze**: Po zainstalowaniu punktu dystrybucji w chmurze, należy przypisać jedną lokację główną do zarządzania transferem zawartości do usługi w chmurze. Tę akcję można wykonać zamiast instalowania roli systemu lokacji punktu dystrybucji w określonej lokacji.  

-   **Klient do komunikacji między punktem dystrybucji w chmurze**: Gdy urządzenia lub użytkownika tego urządzenia jest skonfigurowany przy użyciu ustawienia klienta umożliwiającego używanie punktu dystrybucji w chmurze, urządzenie może traktować punktu dystrybucji w chmurze jako prawidłową lokalizację zawartości:  

    -   Punkt dystrybucji w chmurze jest traktowany jako zdalny punkt dystrybucji, gdy klient ocenia dostępne lokalizacje zawartości.  

    -   Klienci w intranecie używać tylko punkty dystrybucji w chmurze jako opcji rezerwowej, gdy lokalne punkty dystrybucji nie są dostępne.  

    Pomimo zainstalowania chmurowych punktów dystrybucji punktów w określonych regionach platformy Azure, klientów korzystających z punktów dystrybucji w chmurze nie rozpoznają regionów platformy Azure i wybierają punkt chmury dystrybucji.

Oznacza to, że jeśli zainstalowaniu punktów dystrybucji w chmurze w wielu regionach, a klient otrzymuje wiele punktów dystrybucji w chmurze jako lokalizacje zawartości, klient nie może on używać punktu dystrybucji w chmurze z tego samego regionu Azure co klient.  

Klienci, którzy używają punktów dystrybucji w chmurze stosują następującą sekwencję dla żądań lokalizacji zawartości:  

1.  Klient skonfigurowany do używania chmurowych punktów dystrybucji zawsze najpierw próbuje uzyskać zawartość z preferowanego puntu dystrybucji.  

2.  Gdy punkt dystrybucji jest niedostępny, klient używa zdalnego punktu dystrybucji, jeśli wdrożenie obsługuje tę opcję i zdalny punkt dystrybucji jest dostępna.  

3.  Gdy zarówno preferowany, jak i zdalny punkt dystrybucji jest niedostępny, klient może uzyskać zawartość z chmurowego punktu dystrybucji.  



  Gdy klient używa punktu dystrybucji w chmurze jako lokalizacji zawartości, klient samodzielnie przeprowadza uwierzytelnianie z punktem dystrybucji w chmurze przy użyciu tokenu dostępu programu Configuration Manager. Gdy ma zaufany certyfikat punktu dystrybucji w chmurze programu Configuration Manager, klient następnie może pobrać żądaną zawartość.  

-   **Monitorowanie chmurowych punktów dystrybucji punktów**: Można monitorować zawartość wdrażaną w każdym punkcie dystrybucji w chmurze, a można monitorować usługi w chmurze, który hostuje punkt dystrybucji.  

    -   **Zawartości**: Można monitorować zawartość wdrażaną do punktu dystrybucji w chmurze taki sam sposób jak podczas wdrażania zawartości do punktów dystrybucji lokalnymi.  

    -   **Usługi w chmurze**: Configuration Manager okresowo sprawdza usługę Azure i zgłasza alert, jeżeli usługa jest nieaktywna lub jeśli występują problemy z subskrypcją lub certyfikatem. Możesz również wyświetlić szczegółowe informacje dotyczące punktu dystrybucji w **punkty dystrybucji w chmurze** węźle **usługi w chmurze** w **administracji** obszaru roboczego w konsoli programu Configuration Manager. Z tej lokalizacji możesz zobaczyć informacje wysokiego poziomu o punkcie dystrybucji. Można również wybrać punkt dystrybucji, a następnie edytować jej właściwości.  

    Podczas edytowania właściwości chmurowego punktu dystrybucji można wykonać następujące czynności:  

    -   Dostosować progi danych dla magazynu i alerty.  

    -   Zarządzać zawartością tak jak dystrybucji lokalnego punktu.  

    Dla każdego chmurowego punktu dystrybucji można wyświetlić, ale nie edytować, identyfikator subskrypcji, nazwę usługi i inne powiązane szczegóły określone podczas instalowania chmurowego punktu dystrybucji.  

-   **Kopii zapasowych i odzyskiwania dla punktów dystrybucji w chmurze**: Korzystając z punktu dystrybucji w chmurze w hierarchii, należy użyć poniższe informacje ułatwią Planowanie tworzenia kopii zapasowej i przywracania danych punktu dystrybucji:  

    -   Jeśli używasz wstępnie zdefiniowane **Utwórz kopię zapasową serwera lokacji** zadania konserwacji, programu Configuration Manager automatycznie uwzględnia konfiguracje punktu dystrybucji w chmurze.  

    -   Jest najlepszym rozwiązaniem jest tworzenie kopii zapasowej i zapisanie kopii certyfikatu zarządzania i certyfikat usługi, które są używane z punktem dystrybucji w chmurze. W przypadku przywracania lokacji głównej programu Configuration Manager, zarządzającej punktem dystrybucji w chmurze na inny komputer, należy ponownie zaimportować certyfikaty, zanim będzie można kontynuować z nich korzystać.  

-   **Odinstalować punkt dystrybucji w chmurze** : Aby odinstalować punkt dystrybucji w chmurze, wybierz punkt dystrybucji w konsoli programu Configuration Manager, a następnie wybierz **usunąć**.  

    Usunięcie punktu dystrybucji w chmurze z hierarchii programu Configuration Manager usuwa zawartość z usługi w chmurze na platformie Azure.  

