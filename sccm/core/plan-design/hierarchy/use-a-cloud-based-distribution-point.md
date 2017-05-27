---
title: Punkt dystrybucji w chmurze | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat konfiguracji i ograniczenia dotyczące korzystania z punktu dystrybucji w chmurze z System Center Configuration Manager."
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
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: 489f38d3f88391e42b5271c03151203d22b26d9e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-cloud-based-distribution-point-with-system-center-configuration-manager"></a>Używanie chmurowego punktu dystrybucji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Punkt dystrybucji w chmurze jest punktem dystrybucji programu System Center Configuration Manager, który jest hostowany w programie Microsoft Azure. Poniższe informacje mają pomóc dowiedzieć się więcej na temat konfiguracji i ograniczeń dotyczących korzystania z chmurowego punktu dystrybucji.

Po zainstalowaniu lokacji głównej i są gotowe do zainstalowania punktu dystrybucji w chmurze, zobacz [zainstalować punkty dystrybucji w chmurze w usłudze Azure](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md).


## <a name="plan-to-use-a-cloud-based-distribution-point"></a>Planowanie używania chmurowego punktu dystrybucji
W przypadku korzystania z chmurowych punktów dystrybucji należy wykonać następujące czynności:  

-   **Konfigurowanie ustawień klienta** aby zapewnić użytkownikom i urządzeniom dostęp do zawartości.  

-   **Określ lokację główną do zarządzania transferem zawartości** do punktu dystrybucji.  

-   **Określ progi** ilości zawartości, które mają być przechowywane na punkcie dystrybucji oraz ilości zawartości, który chcesz włączyć klienci mogą przenosić z punktu dystrybucji.  


Na podstawie progów skonfigurowanych, Configuration Manager może zgłosić alerty, które ostrzegają użytkownika, gdy łączna ilość zawartości przechowywanej w punkcie dystrybucji zbliża się wielkość magazynu określony lub gdy ilość danych transferowanych przez klientów zbliża się zdefiniowanych progów.  

Punkty dystrybucji w chmurze obsługuje kilka funkcji umożliwiający są również lokalne punkty dystrybucji:  

-   Zarządzanie punktami dystrybucji w chmurze indywidualnie lub jako członkowie dystrybucji grupy punktów.  

-   Punkt dystrybucji w chmurze można użyć jako rezerwowej lokalizacji zawartości.  

-   Punkty te zapewniają obsługę klientów intranetowych i internetowych.  


Punkty dystrybucji w chmurze zapewniają następujące korzyści:  

-   Zawartość, która jest wysyłana do punktu dystrybucji w chmurze jest szyfrowana przez program Configuration Manager, przed Menedżera konfiguracji wysyła ją do Azure.  

-   W systemie Azure można ręcznie skalować usługę chmury, aby spełnić potrzeby w zakresie żądań zawartości przez klientów bez konieczności instalowania i udostępniania dodatkowych punktów dystrybucji zgłaszanych.  

-   Chmurowy punkt dystrybucji obsługuje pobieranie zawartości przez klientów skonfigurowanych w usłudze Windows BranchCache.  


Chmurowe punkty dystrybucji charakteryzują się następującymi ograniczeniami:  

-  Przed użyciem wersji 1610 z KB4010155 poprawki, nie można używać punktu dystrybucji w chmurze do hostowania pakietów aktualizacji oprogramowania. Ten problem zostanie usunięty, począwszy od wersji 1702, a później.  

-   Nie można używać punktu dystrybucji w chmurze PXE lub z obsługą multiemisji wdrożeń.  

-   Klienci nie mogą używać chmurowego punktu dystrybucji jako lokalizacji zawartości dla sekwencji zadań wdrożonej przy użyciu opcji **W razie potrzeby pobierz zawartość lokalnie przez uruchomienie sekwencji zadań**. Natomiast sekwencje zadań wdrożone przy użyciu opcji **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań** mogą używać chmurowego punktu dystrybucji jako prawidłowych lokalizacji zawartości.  

-   Chmurowy punkt dystrybucji nie obsługuje pakietów uruchomionych z poziomu punktu dystrybucji. Cała zawartość musi być pobrane przez klienta, a następnie uruchom lokalnie.  

-   Chmurowy punkt dystrybucji nie obsługuje przesyłania strumieniowego aplikacji przy użyciu programu Application Virtualization lub podobnych.  

-   Chmurowy punkt dystrybucji nie obsługuje wstępnie przygotowanej zawartości. Menedżer dystrybucji w lokacji głównej, która zarządza dystrybucji punktu transferuje całą zawartość do punktu dystrybucji.  

-   Punktu dystrybucji w chmurze nie można skonfigurować jako punktu dystrybucji ściągania.  

##  <a name="BKMK_PrereqsCloudDP"></a> Wymagania wstępne dotyczące chmurowych punktów dystrybucji  
 W celu używania chmurowych punktów dystrybucji należy spełnić następującego wymagania wstępne:  

-   Subskrypcja Azure (zobacz [o subskrypcjach i certyfikatach](#BKMK_CloudDPCerts) w tym temacie).

-   Certyfikat zarządzania podpisem własnym lub publicznych (PKI) infrastruktury kluczy do komunikacji z serwera lokacji podstawowej programu Configuration Manager do usługi w chmurze platformy Azure (zobacz [o subskrypcjach i certyfikatach](#BKMK_CloudDPCerts) w tym temacie).

-   Certyfikat usługi (PKI) używanego przez klientów programu Configuration Manager do łączenia się z punktami dystrybucji w chmurze i pobierania z nich zawartości przy użyciu protokołu HTTPS.  

-  Urządzenie lub użytkownik musi mieć **wskazuje Zezwalaj na dostęp do dystrybucji chmury** ustawić **tak** w kliencie ustawienie **usług w chmurze** zanim urządzenie lub użytkownik może uzyskać dostęp do zawartości z punktu dystrybucji w chmurze. Domyślnie to ustawienie ma wartość **Nie**.  

-   Klient musi być w stanie rozpoznać nazwę usługi w chmurze, co wymaga alias systemu nazw domen (DNS) i rekord CNAME w danym obszarze nazw DNS.  

-   Aby używać chmurowego punktu dystrybucji, klient musi mieć dostęp do Internetu.  

##  <a name="BKMK_CloudDPCost"></a> Koszty korzystania z chmurowych punktów dystrybucji  
 Używania punktu dystrybucji w chmurze należy planować koszt przechowywania danych i transferów pobierania, wykonujących przez klientów programu Configuration Manager.  

 Menedżer konfiguracji zawiera opcje, aby ułatwić kontrolę kosztów i monitorowania dostępu do danych:  

-   Można kontrolować i monitorować ilość zawartości, która jest przechowywana w usłudze chmury.  

-   Można skonfigurować programu Configuration Manager do alert, gdy **progi** dla klienta pobierze osiągnięciu lub przekroczenia limitów miesięcznych.  

-   Ponadto można użyć (Windows BranchCache) Buforowanie równorzędne w celu zmniejszenia liczby transferów danych z punktów dystrybucji w chmurze przez klientów. Klienci programu Configuration Manager, które są skonfigurowane dla usługi BranchCache mogą przesyłać zawartość przy użyciu punktów dystrybucji w chmurze.  


**Opcje:**  

-   **Ustawienia klienta dla chmury**: Kontrola dostępu do wszystkich punktów dystrybucji w chmurze w hierarchii za pomocą **ustawień klienta**.  

     W oknie **Ustawienia klienta**kategoria **Ustawienia chmury** obsługuje ustawienie **Zezwalaj na dostęp do chmurowych punktów dystrybucji**. Domyślnie to ustawienie ma wartość **Nie**. Można włączyć to ustawienie dla użytkowników i urządzeń.  

-   **Progi transferów danych**: Można skonfigurować progi ilości danych, które mają być przechowywane w punkcie dystrybucji i ilości danych pobierane przez klientów z punktu dystrybucji.  

     Progi dla chmurowych punktów dystrybucji są następujące:  

    -   **Próg alertu miejsca do magazynowania**: Próg alertu miejsca do magazynowania umożliwia ustawienie górnego limitu ilości danych lub zawartości przechowywanej w punkcie dystrybucji w chmurze. Program Configuration Manager może generować ostrzeżenie, gdy pozostałe wolne miejsce osiągnie określony poziom, który określisz.  

    -   **Próg alertu transferu**: Próg alertu transferu ułatwia monitorowanie ilości zawartości przesyłanej z punktu dystrybucji do klientów w ciągu 30 dni. Próg alertu transferu monitoruje transfer danych z poprzednich 30 dni oraz wywołania alertu ostrzegawczego i krytycznego, gdy transfer osiągnie zdefiniowane wartości.  

        > [!IMPORTANT]  
        >  Program Configuration Manager monitoruje transfer danych, ale nie zatrzymuje go po osiągnięciu określonego progu alertu transferu.  

 Progi dla każdego chmurowego punktu dystrybucji można określić podczas instalacji punktu dystrybucji lub edytować właściwości każdego chmurowego punktu dystrybucji po jego zainstalowaniu.  

-   **Alerty**: Można skonfigurować programu Configuration Manager, aby zgłaszał alerty dotyczące transferów danych do i z każdego punktu dystrybucji w chmurze, na podstawie progów transferu danych przez użytkownika. Te alerty ułatwiają monitorowanie transferów danych co ułatwia określenie, kiedy Aby zatrzymać usługę chmury, dostosować zawartość przechowywane na punkcie dystrybucji lub zmodyfikuj których klienci mogą używać chmurowych punktów dystrybucji punkty.  

     Co godzinę lokacja główna monitorująca punkt dystrybucji w chmurze pobiera dane transakcji z platformy Azure i zapisuje go w pliku CloudDP -&lt;ServiceName\>.log na serwerze lokacji. Program Configuration Manager ocenia następnie te informacje pod kątem przydziałów magazynu i transferu dla każdego punktu dystrybucji w chmurze. Gdy transfer danych osiągnie lub przekroczy określoną ilość dla ostrzeżenia lub alertów krytycznych, program Configuration Manager wygeneruje odpowiedni alert.  

    > [!WARNING]  
    >  Ponieważ informacje o transferach danych są pobierane z Azure co godzinę, wykorzystanie danych może przekroczyć próg ostrzegawczy lub krytyczny zanim program Configuration Manager można uzyskać dostęp do danych i zgłosi alert.  

    > [!NOTE]  
    >  Alerty dla punktu dystrybucji w chmurze zależą od statystyk użycia z Azure, który może potrwać do 24 godzin staną się dostępne. Informacje o Analytics magazynu dla platformy Azure, jak często Azure aktualizacji statystyk użycia przez, w tym temacie [Analytics magazynu](http://go.microsoft.com/fwlink/p/?LinkID=275111) w bibliotece MSDN.  


-   **Zatrzymanie lub uruchomienie usługi w chmurze na żądanie**: Aby zatrzymać usługę chmury w dowolnym momencie, aby uniemożliwić klientom ciągłe korzystanie z usługi, można użyć opcji. Zatrzymanie usługi chmurowej natychmiast uniemożliwia klientom pobranie z niej dodatkowej zawartości. Ponadto można ponownie uruchomić usługę chmurową, aby przywrócić klientom dostęp. Usługę chmurową można na przykład zatrzymać po osiągnięciu progów ilości danych.  

     Po zatrzymaniu usługa w chmurze nie usuwa zawartości z punktu dystrybucji i nie zapobiega przesyłaniu przez serwer lokacji dodatkowej zawartości do chmurowego punktu dystrybucji.  

     Aby zatrzymać usługę chmury, w konsoli programu Configuration Manager wybierz punkt dystrybucji w **punkty dystrybucji w chmurze** węzeł w węźle **usług w chmurze**w **administracji** obszaru roboczego. Następnie kliknij **zatrzymać usługę** zatrzymać usługę w chmurze działającą w usłudze Azure.  

##  <a name="BKMK_CloudDPCerts"></a> Informacje o subskrypcjach i certyfikatach dla chmurowych punktów dystrybucji  
 Punkty dystrybucji w chmurze certyfikaty wymagane do włączenia programu Configuration Manager do zarządzania usługą w chmurze, który obsługuje punkt dystrybucji, a klientom dostęp do zawartości z rozkładem punktów. Poniższe informacje zawiera omówienie dotyczące tych certyfikatów. Aby uzyskać bardziej szczegółowe informacje, zobacz [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

 **Certyfikaty**  

-   **Certyfikat zarządzania do serwera lokacji do komunikacji między punktem dystrybucji**: Certyfikat zarządzania ustanawia relację zaufania między interfejsem API zarządzania Azure i programu Configuration Manager. Takie uwierzytelnianie umożliwia programu Configuration Manager do wywołania interfejsu API Azure podczas wykonywania zadań, takich jak wdrażanie zawartości lub uruchamianie i zatrzymywanie usługi w chmurze. Za pomocą Azure, można tworzyć własne certyfikaty zarządzania, które mogą być certyfikaty z podpisem własnym lub certyfikatów wystawionych przez urząd certyfikacji (CA):  

    -   Określ plik .cer certyfikatu zarządzania Azure, podczas konfigurowania Azure dla programu Configuration Manager. Plik .cer zawiera klucz publiczny certyfikatu zarządzania. Ten certyfikat należy przesłać Azure przed zainstalowaniem punktu dystrybucji w chmurze. Tego certyfikatu program Configuration Manager, aby uzyskać dostęp do interfejsu API Azure.  

    -   Określ plik .pfx certyfikatu zarządzania do programu Configuration Manager po zainstalowaniu punktu dystrybucji w chmurze. Plik .pfx zawiera klucz prywatny certyfikatu zarządzania. Program Configuration Manager przechowuje ten certyfikat w bazie danych lokacji. Ponieważ plik .pfx zawiera klucz prywatny, należy podać hasło do zaimportowania tego pliku do bazy danych programu Configuration Manager.  

    W przypadku utworzenia certyfikatu z podpisem własnym, należy najpierw wyeksportować certyfikat jako plik cer i następnie wyeksportować go ponownie w formie pliku .pfx.  

    Opcjonalnie można określić jedną wersję **.publishsettings** pliku z Azure SDK 1.7. Informacje o plikach .publishsettings można znaleźć w dokumentacji usługi Azure.  

    Aby uzyskać więcej informacji, zobacz [Tworzenie certyfikatu zarządzania](http://go.microsoft.com/fwlink/p/?LinkId=220281) i [jak dodać certyfikat zarządzania do subskrypcji platformy Azure](http://go.microsoft.com/fwlink/p/?LinkId=241722) w sekcji platformy Azure w bibliotece MSDN.  

-   **Certyfikat usługi do komunikacji z klientem w punkcie dystrybucji**: Certyfikat usługi punktu dystrybucji w chmurze programu Configuration Manager ustanawia relację zaufania między klientami programu Configuration Manager i punkt dystrybucji w chmurze i zabezpiecza dane pobierane przez klientów przy użyciu protokołu Secure Socket Layer (SSL) za pośrednictwem protokołu HTTPS.  

    > [!IMPORTANT]  
    >  W polu podmiotu certyfikatu usługi należy określić unikatową nazwę pospolitą w domenie, która nie jest zgodna z żadnym urządzeniem dołączonym do domeny.  

   Przykład wdrożenia tego certyfikatu, zobacz sekcję **wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze** w temacie [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="bkmk_Tasks"></a> Typowe zadania związane z zarządzaniem chmurowymi punktami dystrybucji  

-   **Serwer lokacji do komunikacji między punktem dystrybucji w chmurze**: Podczas instalowania punktu dystrybucji w chmurze, należy przypisać jedną lokację główną do zarządzania transferem zawartości do usługi w chmurze. Tę akcję można wykonać zamiast instalowania roli systemu lokacji punktu dystrybucji w określonej lokacji.  

-   **Klient do komunikacji między punktem dystrybucji w chmurze**: Gdy urządzenie lub użytkownik urządzenia skonfigurowano ustawienie klienta, które umożliwia korzystanie z punktu dystrybucji w chmurze, urządzenie może traktować punktu dystrybucji w chmurze jako prawidłową lokalizację zawartości:  

    -   Punkt dystrybucji w chmurze jest traktowany jako zdalny punkt dystrybucji, gdy klient ocenia dostępne lokalizacje zawartości.  

    -   Klienci w intranecie używać tylko punkty dystrybucji w chmurze jako opcji rezerwowej, gdy lokalne punkty dystrybucji nie są dostępne.  

    Pomimo zainstalowania punktów dystrybucji w chmurze w określonych regionach systemu Azure, klientów, którzy używają punktów dystrybucji w chmurze nie rozpoznają regionów systemu Azure i wybierają punkt chmury dystrybucji.

Oznacza to, że jeśli zainstalowaniu punktów dystrybucji w chmurze w wielu regionach, a klient otrzymuje wiele punktów dystrybucji w chmurze jako lokalizacje zawartości, klient nie może on używać punktu dystrybucji w chmurze z tego samego regionu systemu Azure, co klient.  

Klienci, którzy używają punktów dystrybucji w chmurze należy użyć następującej żądań lokalizacji zawartości:  

1.  Klient skonfigurowany do używania chmurowych punktów dystrybucji zawsze najpierw próbuje uzyskać zawartość z preferowanego puntu dystrybucji.  

2.  Gdy preferowany punkt dystrybucji nie jest dostępna, klient używa zdalnego punktu dystrybucji, jeśli wdrożenie obsługuje tę opcję i zdalny punkt dystrybucji jest dostępna.  

3.  Gdy zarówno preferowany, jak i zdalny punkt dystrybucji jest niedostępny, klient może uzyskać zawartość z chmurowego punktu dystrybucji.  



  Gdy klient korzysta z punktu dystrybucji w chmurze jako lokalizacji zawartości, klient uwierzytelnia się przy użyciu tokenu dostępu programu Configuration Manager do punktu dystrybucji w chmurze. Jeśli klient ufa certyfikat punktu dystrybucji w chmurze programu Configuration Manager, klient może pobrać żądanej zawartości.  

-   **Monitorowanie punktów dystrybucji w chmurze**: Można monitorować zawartość wdrażaną w każdym punkcie dystrybucji w chmurze i można monitorować usługi w chmurze, który obsługuje punkt dystrybucji.  

    -   **Zawartość**: Można monitorować zawartość wdrażaną do punktu dystrybucji w chmurze taki sam sposób, jak podczas wdrażania zawartości do punktów dystrybucji lokalnie.  

    -   **Usługa w chmurze**: Program Configuration Manager okresowo sprawdza usługę Azure i zgłasza alert, jeżeli usługa jest nieaktywna lub jeśli występują problemy z subskrypcją lub certyfikatem. Można również wyświetlić szczegółowe informacje dotyczące punktu dystrybucji w **punkty dystrybucji w chmurze** węzeł w węźle **usług w chmurze** w **administracji** obszaru roboczego w konsoli programu Configuration Manager. Z tej lokalizacji można zobaczyć informacje wysokiego poziomu o punkcie dystrybucji. Można również wybrać punkt dystrybucji, a następnie edytować jej właściwości.  

    Podczas edytowania właściwości chmurowego punktu dystrybucji można wykonać następujące czynności:  

    -   Dostosować progi danych dla magazynowania i alertów.  

    -   Zarządzanie zawartością w przypadku czy lokalnego punktu dystrybucji.  

    Dla każdego chmurowego punktu dystrybucji można wyświetlić, ale nie edytować, identyfikator subskrypcji, nazwę usługi i inne powiązane szczegóły określone podczas instalowania chmurowego punktu dystrybucji.  

-   **Kopii zapasowych i odzyskiwania dla punktów dystrybucji w chmurze**: Korzystając z punktu dystrybucji w chmurze w hierarchii, należy użyć poniższe informacje ułatwią Planowanie tworzenia kopii zapasowej i przywracania danych punktu dystrybucji:  

    -   Używając wstępnie zdefiniowanego **kopii zapasowej serwera lokacji** zadanie konserwacji programu Configuration Manager automatycznie uwzględnia konfiguracje punktu dystrybucji w chmurze.  

    -   Jest najlepszym rozwiązaniem jest utworzenie kopii zapasowej i zapisanie kopii certyfikatu zarządzania i certyfikat usługi, które są używane z punktem dystrybucji w chmurze. W przypadku przywracania lokacji programu Configuration Manager głównej zarządzającej punktem dystrybucji w chmurze na inny komputer, należy ponownie zaimportować certyfikaty, zanim będzie można kontynuować z nich korzystać.  

-   **Odinstalować punkt dystrybucji w chmurze** : Aby odinstalować punkt dystrybucji w chmurze, wybierz punkt dystrybucji w konsoli programu Configuration Manager, a następnie wybierz **usunąć**.  

    Po usunięciu punktu dystrybucji w chmurze z hierarchii programu Configuration Manager usuwa zawartość z usługi w chmurze w systemie Azure.  

