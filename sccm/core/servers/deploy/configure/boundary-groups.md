---
title: Konfigurowania grup granic
titleSuffix: Configuration Manager
description: Ułatwiają klientom znaleźć systemy lokacji za pomocą grup granic w celu logicznego uporządkowania lokalizacji sieciowych powiązanych o nazwie granic
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 297f4a5ecb7650a4ea643fff00dd67b6580256de
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Konfigurowanie grup granic dla programu System Center Configuration Manager


*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Używają grup granic w programie Configuration Manager w celu logicznego uporządkowania lokalizacji sieciowych powiązanych ([granice](/sccm/core/servers/deploy/configure/boundaries)) aby ułatwić zarządzanie infrastrukturą. Przypisz granice do grup granic, przed rozpoczęciem korzystania z grupy granic.

Domyślnie program Configuration Manager tworzy domyślną grupę granic lokacji w każdej lokacji.

Aby skonfigurować grupy granic, należy skojarzyć granic (lokalizacje sieciowe) i role systemu lokacji, takich jak punkty dystrybucji do grupy granic. Taka konfiguracja pozwala skojarzyć klientów na serwerach systemu lokacji, takich jak punkty dystrybucji, które znajdują się w pobliżu klientów w sieci.

Aby zwiększyć dostępność systemów lokacji serwerów, takich jak punkty dystrybucji dla szerszej grupy lokalizacji sieciowych, przypisać do wielu grup granic tej samej granicy, a tym samym serwerze.

Klienci używają grupę granic:  

-   Automatycznego przypisywania lokacji  
-   Aby znaleźć serwer systemu lokacji, która może zapewnić usługę, w tym:
    - Punkty dystrybucji dla lokalizacji zawartości
    -   Punkty aktualizacji oprogramowania
    - Punkty migracji stanu
    - Preferowanych punktów zarządzania (Jeśli używasz preferowane punkty zarządzania, należy włączyć tę opcję dla hierarchii, a nie za pomocą konfiguracji grupy granic. Zobacz [umożliwia korzystanie z preferowanych punktów zarządzania](#to-enable-use-of-preferred-management-points) w tym temacie.)

##  <a name="boundary-groups-and-relationships"></a>Grupy granic i relacje
Dla każdej grupy granic w hierarchii można przypisać:

-  Co najmniej jedną granicę. Klient **bieżącego** grupa granic jest lokalizacji sieciowej, która jest zdefiniowana jako granicę przypisane do określonej grupy. Klient może mieć więcej niż jednej grupy granic bieżącej.
- Jeden lub więcej ról systemu lokacji. Klienci mogą zawsze używać ról systemu lokacji skojarzone z ich bieżącą grupę granic. W zależności od dodatkowe konfiguracje mogą one można używać w grupach granic dodatkowe role systemu lokacji.  

Dla każdej grupy granic, które możesz utworzyć można skonfigurować jednokierunkowe łącze do innej grupy granic. Łącze jest nazywany **relacji**. Łącze do grupy granic są nazywane **sąsiada** grup granic. Grupa granic może mieć wiele relacji, każdy z grupą granic określonych sąsiedniego.

Gdy klient nie może znaleźć serwera systemu lokacji dostępne w jego bieżącej grupy granic, konfigurację każdej relacji określa, kiedy rozpoczyna wyszukiwania sąsiada grupy granic. To wyszukiwanie dodatkowych grup jest nazywany **rezerwowy**.

## <a name="fallback"></a>Opcja rezerwowa
Aby zapobiec problemom, gdy klienci nie może znaleźć system lokacji dostępny w ich bieżącej grupy granic, definiowania relacji między grup granic w celu zachowania alternatywnego. Rezerwa umożliwia klienta rozwiń wyszukiwanie do grup granic dodatkowe można znaleźć systemu lokacji.

Relacje są skonfigurowane na właściwości grupy granic **relacje** kartę. Po skonfigurowaniu relacji z grupą granic sąsiada należy zdefiniować łącza. Dla każdego typu obsługiwaną rolę systemu lokacji należy skonfigurować niezależnie od ustawienia powrotu do grupy granic sąsiedniego. Na przykład po skonfigurowaniu relacji z grupą granic określonych ustawić rezerwowy dla punktów dystrybucji zostać przeprowadzone po upływie 20 minut, zamiast domyślnej 120. Na przykład szerszej, zobacz [przykład za pomocą grup granic](#example-of-using-boundary-groups).

Jeśli klient nie może znaleźć dostępna Rola systemu lokacji w jego bieżącej grupy granic, klient używa rezerwowej czas w minutach. Teraz rezerwowy określa rozpoczęcia klienta do wyszukiwania systemu lokacji skojarzone z grupą granic sąsiedniego.  

Gdy klient nie może znaleźć system lokacji dostępny i rozpocznie się wyszukiwanie w lokalizacjach od sąsiada grup granic, zwiększa puli dostępnych systemów lokacji. Konfiguracja grupy granic oraz ich relacji definiuje użycia przez klienta w tej puli dostępnych systemów lokacji.

- Grupa granic może mieć więcej niż jedną relację. Wiele relacji można skonfigurować używane dla każdego typu systemu lokacji z różnych sąsiadów występuje po różnych okresach czasu.    
- Klienci tylko powrotu do grupy granic, która jest bezpośrednio sąsiada ich bieżącej grupy granic.
- Gdy klient jest członkiem wielu grup granic, bieżącą grupę granic jest zdefiniowany jako Unii grup granic wszystkich klientów. Klient powraca do sąsiadów któregokolwiek z tych oryginalnego grup granic.

### <a name="the-default-site-boundary-group"></a>Domyślna grupa granic lokacji
Oprócz grup granic, które możesz utworzyć każda lokacja ma domyślne grupy granic lokacji jest tworzony przez program Configuration Manager. Ta grupa ma nazwę ***domyślna--grupy granic lokacji&lt;kod lokacji >***. Na przykład, czy nazwę grupy w lokacji ABC *domyślna--grupy granic lokacji —&lt;ABC >.*

Dla każdej grupy granic tworzonych programu Configuration Manager automatycznie tworzy domniemanych łącze do każdej grupy granic lokacji domyślnej w hierarchii.
-   Dorozumiany łącze jest domyślne opcji rezerwowej z bieżącej grupy granic do domyślnej grupy granic lokacji rezerwowego czasu domyślne 120 minut.
-   W przypadku klientów nie znajduje się w granicy skojarzony z żadną inną grupą granic: Aby zidentyfikować role systemu lokacji prawidłowe, należy użyć domyślnej grupy granic lokacji w przypisanej lokacji.

Aby zarządzać powrotu do domyślnej grupy granic lokacji:
- Otwórz właściwości domyślnej grupie granic lokacji i zmień wartości w **domyślne zachowanie** kartę. Zmiany wprowadzone w tym miejscu dotyczą *wszystkie* niejawnego łącza do tej grupy granic. Te ustawienia mogą zostać zastąpione podczas konfigurowania jawne łącze do tej grupy granic lokacji domyślnej z innej grupy granic.
- Otwórz właściwości grupy granic niestandardowych. Zmień wartości jawne łącza do domyślnej grupy granic lokacji. Po ustawieniu nowego czas w minutach, powrotu lub bloku powrotu tej wpływa tylko łącze, które są konfigurowane. Konfiguracja jawne łącza zastępuje ustawienia na **domyślne zachowanie** kartę domyślne grupy granic lokacji.


## <a name="site-assignment"></a>Przypisanie lokacji  
 Do każdej grupy granic można wprowadzić przypisaną lokację do klientów.  

-   Nowo zainstalowanego klienta, który używa automatycznego przypisania lokacji łączy przypisanej lokacji grupę granic zawierającą bieżącą lokalizację sieciową klienta.  
-   Po przypisaniu do lokacji klient nie zmienia przypisania lokacji, gdy zmienia lokalizację sieciową. Na przykład, jeśli klient uzyskuje mobilny dostęp do lokalizacji sieciowej reprezentowana przez granicę w grupie granic z innym przypisaniem lokacji, klienta przypisanej lokacji pozostaną bez zmian.  
-   Kiedy funkcja odnajdowania systemu usługi Active Directory odnajdzie nowy zasób, informacje o sieci odnalezionego zasobu zostaną ocenione względem granic w grupach granic. Ten proces powoduje skojarzenie nowego zasobu z przypisaną lokacją w celu użycia przez metodę instalacji klienta w trybie wypychania.  
-   Gdy granicy do wielu grup granic, które mają przypisane różne lokacje, klientów losowo wybierać jedną z lokacji.  
-   Zmiany lokacji przypisanej do grup granic dotyczą tylko nowych akcji przypisania lokacji. Klienci, którzy wcześniej przypisani do lokacji nie obliczyć ponownie przypisania lokacji na podstawie zmian w konfiguracji grupy granic (lub do lokalizacji sieciowej).  

Aby uzyskać więcej informacji o przypisywaniu lokacji klienta, zobacz [przy użyciu automatycznego przypisania lokacji komputerów](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Punkty dystrybucji

Gdy klient żąda lokalizacji punktu dystrybucji, programu Configuration Manager wysyła klientowi listę systemów lokacji. Te systemy lokacji są odpowiedniego typu skojarzone z każdą grupą granic, co obejmuje także bieżącą lokalizację sieciową klientów:

-   **Podczas dystrybucji oprogramowania**, klient żąda lokacji wdrożenia zawartości, która jest dostępna z punktem dystrybucji lub innych poprawne źródło zawartości (na przykład klient skonfigurowany na potrzeby równorzędnej pamięci podręcznej).

-   **Podczas wdrażania systemu operacyjnego**, klienci żądają lokalizacji do wysłania lub odebrania informacji o migracji stanu.  

Podczas wdrażania zawartości gdy klient zażąda zawartości, który nie jest dostępny ze źródła w jego bieżącej grupy granic, klient w dalszym ciągu zażądać tej zawartości. Klient próbuje różnych źródeł zawartości w jego bieżącej grupy granic, dopóki nie osiągnie rezerwowy okresu dla grupy granic sąsiada lub domyślna grupa granic lokacji. Jeśli klient nie odnalazł jeszcze zawartość, następnie rozwija wyszukiwanie źródeł zawartości uwzględnić sąsiada grupy granic.

Jeśli zawartość będzie rozmieszczona na żądanie i nie jest dostępna w punkcie dystrybucji, gdy żądany przez klienta, rozpoczyna proces transferu zawartości do tego punktu dystrybucji. Istnieje możliwość, klient znajduje ten serwer jako źródła zawartości przed powrotem do używania grupy granic sąsiedniego.

## <a name="software-update-points"></a>Punkty aktualizacji oprogramowania
Klienci używają grup granic do znajdowania punktu aktualizacji oprogramowania. Aby kontrolować serwerów, które można znaleźć klienta, należy dodać punkty aktualizacji oprogramowania do różnych grup granic.

Po aktualizacji z wersji przed 1702 każdej lokacji dodaje wszystkie istniejące punkty aktualizacji oprogramowania do domyślnej grupy granic lokacji. To zachowanie aktualizacji lokacji obsługuje zachowanie wcześniejsze klienta, aby wybrać punkt aktualizacji oprogramowania z puli serwerów dostępnych. To zachowanie jest zachowywana do momentu dodania do różnych grup granic zaznaczenia kontrolowane i działanie rezerwowe punkty aktualizacji oprogramowania.

Po zainstalowaniu nowej lokacji, punkty aktualizacji oprogramowania nie są dodawane do domyślnej grupy granic lokacji. Przypisać punkty aktualizacji oprogramowania do grupy granic, tak aby klienci mogą znaleźć i używać ich.

### <a name="fallback-for-software-update-points"></a>Używane dla punktów aktualizacji oprogramowania
Używane dla punktów aktualizacji oprogramowania jest skonfigurowane tak jak inne role systemu lokacji, ale ma następujące ostrzeżenia:
- **Nowi klienci używają grup granic, aby wybrać punkty aktualizacji oprogramowania.** Nowych klientów, które można zainstalować, wybierz punkt aktualizacji oprogramowania z tych serwerów skojarzone z grupami granic, które można skonfigurować. To zachowanie zastępuje poprzednie gdzie klienci wybierają punkt aktualizacji oprogramowania losowo z listy serwerów, które będą współużytkować lesie klienta.

- **Klienci w dalszym ciągu korzystać punktu aktualizacji oprogramowania dobrej Ostatnia znana do nich rezerwowy można znaleźć nową.** Klienci, którzy już mają punkt aktualizacji oprogramowania w dalszym ciągu używać go, dopóki nie można nawiązać połączenia. To zachowanie zawiera dalsze używanie punkt aktualizacji oprogramowania, który nie jest skojarzony z bieżącą grupę granic klienta.

  Dalsze używanie istniejącego punktu aktualizacji oprogramowania nawet wtedy, gdy ten serwer nie jest w bieżącej grupie granic klienta jest zamierzone. Podczas zmiany punkt aktualizacji oprogramowania, klient synchronizuje dane z nowym serwerem, co powoduje, że użycie znaczących sieci. Jeśli wszyscy klienci przełączyć się do nowego serwera w tym samym czasie, opóźnienie w przejścia pomaga uniknąć nasycenia sieci.

- **Klient zawsze próbuje nawiązać połączenie jego ostatnim punktem aktualizacji oprogramowania znanego dobrego na 120 minut przed uruchomieniem rezerwowego.** Po 120 minut Jeśli klient nie ma nawiązać kontaktu, następnie rozpoczyna powrotu. Po uruchomieniu rezerwowe, klient odbierze listę wszystkich punktów aktualizacji oprogramowania z jego bieżącej grupy granic. Dodatkowe punkty aktualizacji oprogramowania od sąsiada i lokacji granic domyślne grupy są dostępne w konfiguracji rezerwowego.

### <a name="fallback-configurations-for-software-update-points"></a>Konfiguracje rezerwowy dla punktów aktualizacji oprogramowania
#### <a name="beginning-with-version-1706"></a>Począwszy od wersji 1706   
Można skonfigurować **powrotu czas (w minutach)** na aktualizacji oprogramowania punktów za mniej niż 120 minut. Jednak klient nadal próbuje osiągnąć jego oryginalnej punktu aktualizacji oprogramowania na 120 minut. Następnie rozszerza on wyszukiwanie do dodatkowych serwerów. Czasy rezerwowy grupy granic rozpocząć, gdy klient najpierw nie może nawiązać oryginalnego serwera. Gdy klient rozszerza wyszukiwanie, witryna zawiera wszystkie grupy granic skonfigurowane dla mniej niż 120 minut.

Aby zablokować używane dla punktu aktualizacji oprogramowania do grupy granic sąsiada, należy skonfigurować ustawienie, aby **nigdy rezerwowy**.

Po awarii do oryginalnego serwera przez 2 godziny, klient używa następnie wywołania skrócenie cyklu nawiązanie połączenia punktu aktualizacji oprogramowania. To zachowanie umożliwia klientowi szybko przeszukiwać rosnącą listę potencjalnych punktów aktualizacji oprogramowania.

 -  **Przykład powrotu:**  
    Bieżącą grupę granic klienta jest używane dla punktów aktualizacji oprogramowania, które są skonfigurowane jako *10* minut dla grupy granic *A*, i *130* minut dla grupy granic *B*. Gdy klient nie może nawiązać jego ostatnim punktem aktualizacji oprogramowania znanego dobrego:
    -   Klient próbuje osiągnąć jego oryginalny serwer dalej 120 minut. Po 10 minutach punktów z grupą granic, są dodawane do puli serwerów dostępnych aktualizacji oprogramowania. Klient nie może jednak próbę skontaktowania się z ich lub na innym serwerze przed upływem okresu wstępnego 120 minut połączyć się ponownie z oryginalnego serwera.
    -   Po próbuje zlokalizować tego oryginalnego punktu aktualizacji oprogramowania na 120 minut, klient może rozszerzyć poszukiwania. W tym czasie klient dodaje serwery do dostępnej puli punktów aktualizacji oprogramowania, które są w nim na bieżący i grup granic sąsiada skonfigurowane na 120 minut lub mniej. Ta pula zawiera serwery w granicy grupy A, które zostały wcześniej dodane do puli dostępnych serwerów.
    -       Po 10 minutach (130 minut całkowity czas po klient najpierw nie może połączyć się jego ostatnim punktem aktualizacji oprogramowania znanego dobrego) klient rozszerza wyszukiwania w celu uwzględnienia punktów aktualizacji oprogramowania z grupy granic B.  

#### <a name="prior-to-version-1706"></a>Przed wersją 1706
Poprzedzające wersję 1706 rezerwowej konfiguracji punktów aktualizacji oprogramowania nie obsługują można skonfigurować czas w minutach. Zamiast tego zachowania alternatywnego jest ograniczona do:

  - **Rezerwowy czas (w minutach):** Ta opcja jest niedostępny dla punktów aktualizacji oprogramowania i nie można skonfigurować. Jest ustawiona na 120 minut.
  -     **Nigdy nie rezerwowej:** Możesz zablokować używane dla punktu aktualizacji oprogramowania do grupy granic sąsiada używania tej konfiguracji.

Gdy klient, który ma już punkt aktualizacji oprogramowania nie można uzyskać do niej dostęp, klient następnie powraca można znaleźć innego. Korzystając z metody rezerwowej, klient odbiera listę wszystkich punktów aktualizacji oprogramowania z jego bieżącej grupy granic. W przypadku niepowodzenia można znaleźć dostępnego serwera na 120 minut ją następnie przechodzi do jego grupę granic sąsiada a domyślna grupa granic lokacji. Powrót do obu grup granic odbywa się w tym samym czasie. Czas rezerwowy punkt aktualizacji oprogramowania do grup sąsiada jest ustawiony na 120 minut. Nie można zmienić czas rezerwowego. 120 minut jest również domyślny okres używane powrotu do domyślnej grupy granic lokacji. Gdy klient powraca do obu sąsiada i domyślnej grupy granic lokacji, klient próbuje skontaktować się z punktów aktualizacji oprogramowania z grupy granic sąsiada przed podjęciem próby użycia jednej z domyślnej grupy granic lokacji.

### <a name="manually-switch-to-a-new-software-update-point"></a>Ręcznie przełączać się do nowego punktu aktualizacji oprogramowania
Oprócz używania rezerwowego, można użyć *powiadomienie klienta* ręcznie wymusić urządzenia, aby przełączyć się do nowego punktu aktualizacji oprogramowania.

Przełączenie do nowego serwera urządzenia używają rezerwowego do znajdowania ten nowy serwer. Przegląd konfiguracji grupy granic. Upewnij się, że punkty aktualizacji oprogramowania znajdują się w grupach granic poprawne przed rozpoczęciem tej zmiany.

Aby uzyskać więcej informacji, zobacz [ręcznie przełączać klientów do nowego punktu aktualizacji oprogramowania](/sccm/sum/plan-design/plan-for-software-updates#manually-switch-clients-to-a-new-software-update-point).



## <a name="management-points"></a>Punkty zarządzania
<!-- 1324594 -->
Począwszy od wersji 1802 skonfigurować relacje rezerwowy dla punktów zarządzania, między grupami granic. To zachowanie zapewnia większą kontrolę dla punktów zarządzania używanych przez klientów. Na **relacje** karcie właściwości grupy granic, to kolumna dla punktu zarządzania. Podczas dodawania nowej grupy granic rezerwowego rezerwowy punkt zarządzania jest obecnie zawsze zero (0). To zachowanie jest takie samo dla **domyślne zachowanie** w domyślnej grupie granic lokacji.

Wcześniej, to powszechny problem występuje, gdy chroniony punkt zarządzania w bezpiecznej sieci. Zasady obejmujące tego punktu zarządzania chronionym, jest wyświetlany w klientom w sieci firmowej głównym, nawet jeśli nie mogli komunikować się z nim przez zaporę. Aby rozwiązać ten problem, należy użyć **nigdy rezerwowy** opcję, aby zapewnić, że tylko powrotu do zarządzania klientami wskazuje, z którym mogą komunikować.

Podczas uaktualniania lokacji do wersji 1802, programu Configuration Manager doda wszystkie punkty zarządzania z systemem innym niż — internetowy w domyślnej grupie granic lokacji. To zachowanie zapewnia, że starsze wersje klienta do komunikowania się z punktami zarządzania. Aby w pełni korzystać z tej funkcji, należy przenieść punkty zarządzania do grup granic żądany.

Rezerwa grupy granic punktu zarządzania nie zmienia zachowanie podczas instalacji klienta (ccmsetup.exe). Jeśli w wierszu polecenia nie określa początkowy punkt zarządzania za pomocą parametru /MP, nowy klient otrzymuje pełną listę dostępnych punktów zarządzania. Dla początkowego procesu ładowania początkowego klient używa pierwszego punktu zarządzania, który można uzyskać dostęp. Gdy klient rejestruje z lokacją, otrzymuje listę punktów zarządzania poprawnie sortowane z to nowe zachowanie. 

Aby klienci mogli używać tej funkcji należy włączyć następujące ustawienie: **Klienci wolą używać punktów zarządzania określonych w grupach granic** w **ustawienia hierarchii**. 

> [!Note]
> Procesy wdrażania systemu operacyjnego nie są znane grup granic.

### <a name="troubleshooting"></a>Rozwiązywanie problemów
Nowe wpisy zostaną wyświetlone w **LocationServices.log**. **Miejscowości** atrybut identyfikuje jeden z następujących stanów:
- 0: Nieznane
- 1: Z określonym punktem zarządzania jest tylko w grupie granic lokacji domyślnej jako metody rezerwowej
- 2: Z określonym punktem zarządzania znajduje się w grupie granic sąsiada lub zdalnym. Gdy punkt zarządzania jest zarówno sąsiada i domyślnych grup granic lokacji, lokalizacja jest 2.
- 3: Z określonym punktem zarządzania znajduje się w grupie granic lokalnego lub bieżący. Gdy punkt zarządzania znajduje się w bieżącej grupie granic, a także sąsiada lub domyślnej grupie granic lokacji, lokalizacja jest 3. Lokalizacja, jeśli preferowane punkty zarządzania w hierarchii ustawień nie zostanie włączone, jest zawsze 3 niezależnie od tego, które granic grupa punkt zarządzania znajduje się w.

Klienci używają punktów zarządzania lokalnego pierwszej (miejscowości 3), drugi zdalnego (miejscowości 2), a następnie powrotu (miejscowości 1). 

Gdy klient otrzyma pięć błędy w ciągu 10 minut, a nie do komunikowania się z punktem zarządzania w jego bieżącej grupy granic, próbuje skontaktować się z punktem zarządzania w sąsiada lub w domyślnej grupie granic lokacji. Jeśli punkt zarządzania w bieżącej grupie granic później wraca do trybu online, klient powróci do punktu zarządzania lokalnego w następnym cyklu odświeżania. Cykl odświeżania jest 24 godzin lub po uruchomieniu usługi agenta programu Configuration Manager.




## <a name="preferred-management-points"></a>Preferowane punkty zarządzania

 > [!Note]
 > Zachowanie tego ustawienia, hierarchii, **klienci wolą używać punktów zarządzania określonych w grupach granic**, począwszy od wersji 1802 zmiany. Po włączeniu tego ustawienia programu Configuration Manager korzysta z funkcji grupy granic dla przypisanego punktu zarządzania. Aby uzyskać więcej informacji, zobacz [punktów zarządzania](#management-points). 

 Preferowane punkty zarządzania umożliwiają klientom identyfikowanie punktów zarządzania skojarzonych z ich bieżącą lokalizacją sieciową (granicą).  

-   Klienci podejmują próbę użycia preferowanego punktu zarządzania z przypisanej do niego lokacji, zanim przy użyciu jednego nie są skonfigurowane jako preferowane, z przypisanej lokacji.  
-   Aby użyć tej opcji, należy włączyć **klienci wolą używać punktów zarządzania określonych w grupach granic** w **ustawienia hierarchii**. Następnie skonfiguruj grupy granic w poszczególnych lokacjach głównych. Uwzględnienia punktów zarządzania, które powinny być skojarzone ze skojarzonymi granicami tej grupy granic.
-   Gdy skonfigurować preferowane punkty zarządzania, a klient organizuje swoją listę punktów zarządzania, klient umieszcza preferowane punkty zarządzania na początku listy. Ta lista zawiera wszystkie punkty zarządzania z przypisanej lokacji klienta.  

> [!NOTE]  
>  Klient roamingu oznacza, że zmienia lokalizację sieciową. Na przykład laptop pojawia się w lokalizacji biura zdalnego. Klient zmieniający, może użyć punktu zarządzania lub punktu zarządzania serwera proxy z lokalnej lokacji w nowej lokalizacji, przed rozpoczęciem korzystania z serwera z przypisanej lokacji. Ta lista serwerów z przypisanej lokacji zawiera preferowane punkty zarządzania. Aby uzyskać więcej informacji, zobacz [zrozumieć, jak klienci znajdują zasoby i usługi lokacji](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="overlapping-boundaries"></a>Nakładanie się granic  
 Program Configuration Manager obsługuje nakładających się granic konfiguracje lokalizacji zawartości. Jeśli lokalizacja sieciowa klienta należy do wielu grup granic:

-   Gdy klient zażąda zawartości, programu Configuration Manager wysyła klientowi listę wszystkich punktów dystrybucji zawierających daną zawartość.  
-   Gdy klient zażąda serwera, aby wysłać lub odebrać informacje o migracji stanu, programu Configuration Manager wysyła klientowi listę punktów migracji stanu skojarzonych z grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Pozwala to klientowi na wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  



## <a name="example-of-using-boundary-groups"></a>Przykład użycia grup granic
W poniższym przykładzie użyto wyszukiwanie zawartości z punktu dystrybucji klienta. W tym przykładzie można zastosować do innych ról systemu lokacji, które używają grup granic. Należy pamiętać, że punktów aktualizacji oprogramowania nie obsługuje konfiguracji powrotu do grupy sąsiada i zawsze używaj 120 minut.

Możesz tworzyć trzech grup granic, które nie udostępniają granic lub serwerów systemu lokacji:
-   Grupy BG_A z punktami dystrybucji DP_A1 i DP_A2 skojarzonego z grupy
-   Grupy BG_B z punktami dystrybucji DP_B1 i DP_B2 skojarzonego z grupy
-   Grupy BG_C z punktami dystrybucji DP_C1 i DP_C2 skojarzonego z grupy

Dodawanie lokalizacje sieciowe klientów jako granic do grupy granic BG_A. Następnie skonfiguruj relacje z tej grupy granic do innych grup granic dwóch:
-   Konfigurowanie punktów dystrybucji w pierwszym *sąsiada* grupy (BG_B) do użycia po 10 minutach. Ta grupa zawiera punkty dystrybucji DP_B1 i DP_B2. Oba są dobrze połączonych do pierwszej grupy lokalizacje granic.
-   Skonfiguruj drugi *sąsiada* grupy (BG_C) do użycia po upływie 20 minut. Ta grupa zawiera punkty dystrybucji DP_C1 i DP_C2. Są w sieci WAN z innych grup granic dwa.
-   Również dodać do grupy granic lokacji domyślnej witryny innego punktu dystrybucji, który znajduje się na serwerze lokacji roboczej. Ten serwer jest najmniej preferowanych lokalizacji źródła zawartości, ale jest on umieszczony centralnie do grup granic.

    Przykład grupy granic i rezerwowy razy:

     ![Przykład grupy granic i czasy rezerwowej](media/BG_Fallback.png)


W tej konfiguracji:
-   Klient rozpocznie się wyszukiwanie zawartości z punktów dystrybucji w jego *bieżącego* grupy granic (BG_A). Wyszukuje poszczególnych punktów dystrybucji dla dwóch minut, a następnie przełącza do następnego punktu dystrybucji w grupie granic. Pula klientów lokalizacji poprawne źródło zawartości zawiera DP_A1 i DP_A2.
-   Jeśli klient nie można odnaleźć zawartości z jego *bieżącego* grupy granic po przeszukaniu przez 10 minut, następnie dodaje punkty dystrybucji z grupy granic BG_B do jego wyszukiwania. Następnie kontynuuje do wyszukiwania zawartości z punktu dystrybucji w jego pulę połączonych serwerów. Ta pula zawiera teraz serwery z BG_A i BG_B grup granic. Klient nadal, skontaktuj się z poszczególnych punktów dystrybucji dla dwóch minut, a następnie przełącza do następnego serwera w jego puli. Pula klientów lokalizacji poprawne źródło zawartości zawiera DP_A1, DP_A2 DP_B1 i DP_B2.
-   Po dodatkowe 10 minut (łącznie 20 minut), jeśli klient nadal nie odnalazł do punktu dystrybucji z zawartością, rozszerza jego pulę, aby obejmować dostępnych serwerów od drugiego *sąsiada* grupy, grupa granic BG_C. Klient ma teraz sześciu punktów dystrybucji w celu wyszukiwania (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 i DP_C2). Nadal zmiana na nowy punkt dystrybucji co dwie minuty, aż do znalezienia zawartości.
-   Jeśli klient nie odnalazł zawartości po łącznie 120 minut, jego powraca do uwzględnienia *domyślnej grupy granic lokacji* jako część jej ciągłego wyszukiwania. Teraz puli obejmuje wszystkie punkty dystrybucji z trzech skonfigurowanych grup granic i punktu końcowego dystrybucji znajduje się na serwerze lokacji. Klient kontynuuje wyszukiwanie zawartości, zmiana co dwie minuty, aż do znalezienia zawartości w punktach dystrybucji.

Skonfigurowanie grup różnych sąsiada mają być dostępne w różnych momentach, możesz kontrolować termin jego konkretnych punktów dystrybucji są dodawane jako lokalizacji źródła zawartości. Klient używa powrotu do domyślnej grupy granic lokacji zabezpieczenie na zawartość, która nie jest dostępna w innej lokalizacji.





<!--
### Update existing boundary groups to the new model
When you update to version prior to 1610, the following configurations are automatically made. This behavior ensures your current fallback behavior remains available until you configure new boundary groups and relationships.

-   Each primary site creates a default site boundary group named ***Default-Site-Boundary-Group&lt;sitecode>***.
  - The primary site adds to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group any state migration points and distribution points configured to **Allow fallback source location for content**.
  - The site adds software update points to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group.
-   The site makes a copy of each existing boundary group that includes a site server configured with a slow connection. The name of the new group is ***&lt;original boundary group name>-&lt;original boundary group ID>***:  
    -   Site systems that have a fast connection are left in the original boundary group.
    -   A copy of site systems (distribution points, management points) that have a slow connection are added to the copy of the boundary group. The original site systems configured as slow remain in their original boundary groups for backward compatibility, but are not used from those boundary groups.
    - This boundary group copy does not have boundaries associated with it. However, A fallback link is created between the original group and the new boundary group copy that has the fallback time set to zero.  


- **Specific to secondary sites:**
  - If a secondary site has at least one state migration point or distribution point enabled to **Allow fallback source location for content**, Configuration Manager creates a boundary group named ***Secondary-Site-Neighbor--Tmp&lt;Sitecode>***. 
  - All distribution points enabled to **Allow fallback source location for content** and state migration points are added to this secondary site boundary group.
  - A fallback link is created between the original boundary group and the newly created neighbor boundary group. The fallback time is set to zero.


 The following table identifies the new fallback behavior you can expect from the combination the original deployment settings and distribution point configurations:

Original deployment configuration for “Do not run program” in slow network  |Original distribution point configuration for “Allow client to use a fallback source location for content”  |New fallback behavior  
---------|---------|---------
Selected     |  Selected    |  **No fallback** - Only use the distribution points in current boundary group       
Selected     |  Not selected|  **No fallback** - Only use the distribution points in current boundary group       
Not selected |  Not selected|  **Fallback to neighbor** - Use the distribution points in current boundary group, and then add the distribution points from the neighbor boundary group. Unless an explicit link to the default site boundary group is configured, clients do not fallback to that group.    
Not selected | Selected     |   **Normal fallback** - Use distribution points in current boundary group, then servers from the neighbor and site default boundary groups

 All other deployment configurations result in **Normal fallback**.  
-->



## <a name="changes-from-prior-versions"></a>Zmiany w poprzednich wersjach
Poniżej przedstawiono zmiany klucza do grupy granic i jak klienci znajdują zawartości w programie Configuration Manager bieżącej gałęzi. Wiele z tych zmian i pojęcia współdziałają ze sobą.


-   Konfiguracje dla Fast lub wolno zostaną usunięte: Można już konfigurować poszczególne punkty dystrybucji można dużą lub małą. Zamiast tego jest traktowany każdego systemu lokacji skojarzone z grupą granic takie same. Z powodu tej zmiany **odwołania** na karcie właściwości grupy granic już nie obsługuje konfiguracji Fast lub niska.
- Nową grupę granic domyślne w każdej lokacji: Każda lokacja główna ma nowej grupy granic domyślny o nazwie ***domyślna--grupy granic lokacji&lt;kod lokacji >***. Gdy klient nie jest w lokalizacji sieciowej przypisanej do grupy granic, używa systemy lokacji skojarzone z domyślnej grupy z przypisanej lokacji. Zaplanuj użycie tej grupy granic w zastępstwie koncepcję rezerwowej lokalizacji zawartości.   
 -  **Zezwalaj na lokalizacji rezerwowej dla zawartości** zostaną usunięte: Nie jest już jawnie skonfigurować punkt dystrybucji do użycia jako metody rezerwowej. Opcje do skonfigurowania tego ustawienia zostaną usunięte z konsoli.

    Ponadto wynik ustawienie **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości** w ramach wdrożenia zmienił się typ dla aplikacji. To ustawienie w typie wdrożenia teraz umożliwia klienta do używania domyślnej grupy granic lokacji jako lokalizacji źródła zawartości.

 -  Relacje grupy granic: Każda grupa granic może odnosić się do co najmniej jednej grupy granic dodatkowe. Łącza te tworzą relacje, które są skonfigurowane na karcie właściwości nowej grupy granic o nazwie **relacje**:
    -   Każdą grupą granic, klient jest bezpośrednio z którym skojarzony jest nazywany **bieżącego** grupy granic.  
    -   Żadną inną grupą granic klient może korzystać z powodu skojarzenia między tego klienta *bieżącego* nosi nazwę grupy granic i innej grupy **sąsiada** grupy granic.
    -  Na **relacje** kartę, Dodaj grupy granic do użycia jako *sąsiada* grupy granic. Również skonfigurować czas w minutach, jako metody rezerwowej. Jeśli klient nie powiodło się uzyskanie zawartości z punktu dystrybucji w *bieżącego* grupę, jest teraz, po rozpoczęciu klienta do wyszukiwania lokalizacji zawartości z *sąsiada* grup granic.

        Podczas dodawania lub zmienić konfigurację grupy granic, istnieje możliwość powrotu do tej grupy granic określone z bieżącej grupy, który jest konfigurowany blok.

    Aby korzystać z nowej konfiguracji, zdefiniować skojarzenia jawnego (linki) z jednej grupy granic do innego. Skonfiguruj wszystkie punkty dystrybucji w tej grupie skojarzony z tym samym czasie w ciągu minut. Gdy klient nie może znaleźć źródła zawartości z jego *bieżącego* określa podczas konfigurowania grupy granic, gdy rozpoczyna się wyszukiwanie źródła zawartości z grupy granic sąsiedniego.

    Oprócz grup granic, które jawnie skonfigurować każdą grupą granic ma domniemanych łącze do domyślnej grupy granic lokacji. To łącze staje się aktywny po 120 minut. Domyślna grupa granic lokacji staje się grupie granic sąsiedniego. Takie zachowanie umożliwia klientów do używania jako lokalizacji źródła zawartości punkty dystrybucji skojarzone z tej grupy granic.

    To zachowanie zastępuje, co zostało wcześniej określone jako metody rezerwowej dla zawartości. Zastąp to domyślne zachowanie 120 minut kojarząc jawnie domyślnej grupy granic lokacji do *bieżącego* grupy. Ustaw określony czas w minutach lub blokowanie rezerwowa całkowicie uniemożliwić korzystanie z niego.


-   Klienci próbują uzyskać zawartości z każdego punktu dystrybucji do dwóch minut: Gdy klient wyszukuje lokalizacji źródła zawartości, próbuje uzyskiwać dostęp do poszczególnych punktów dystrybucji dla dwóch minut przed podjęciem próby następnie innego punktu dystrybucji. To zachowanie jest zmiana z poprzednich wersji, gdzie klienci nastąpiła próba połączenia do punktu dystrybucji przez maksymalnie 2 godziny.

    - Klienci wybierają losowo pierwszego punktu dystrybucji z puli serwerów dostępnych na komputerze klienckim *bieżącego* grupy granic (lub grupy).

    - Po dwóch minut Jeśli klient nie odnalazł zawartości, go przełącza się do nowego punktu dystrybucji i próbuje pobrać zawartość z tego serwera. Ten proces jest powtarzany co dwie minuty, aż do klienta znajduje się zawartość lub osiągnie ostatni serwer w jego puli.

    - Jeśli klient nie może znaleźć lokalizację poprawne źródło zawartości z jego *bieżącego* puli przed jego okresu powrotu do *sąsiada* grupy granic, klient następnie dodaje punkty dystrybucji z który *sąsiada* grupy w celu jego bieżącej listy. Wyszukuje rozwiniętej grupy lokalizacje źródłowe zawiera punkty dystrybucji z obu tych grup granic.

        > [!TIP]  
        > Podczas tworzenia wyraźnego związku z bieżącej grupy granic do domyślnej grupy granic lokacji i rezerwowy czasu, która jest mniejsza niż rezerwowy czasu dla łącza do grupy granic sąsiada, klienci rozpocząć wyszukiwanie lokalizacje źródłowe z domyślnej witryny grupy granic przed dołączeniem grupy sąsiedniego.

    - Gdy klient nie można pobrać zawartości z ostatniego serwera w puli, rozpoczyna proces ponownie.


## <a name="procedures-for-boundary-groups"></a>Procedury dotyczące grup granic

### <a name="to-create-a-boundary-group"></a>Aby utworzyć grupę granic  
1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz grupę granicę**.  

3.  W **Utwórz grupę granicę** okno dialogowe, wybierz opcję **ogólne** , a następnie określ **nazwa** dla tej grupy granic.  

4.  Kliknij przycisk **OK** , aby zapisać nową grupę granic.  


### <a name="to-configure-a-boundary-group"></a>Aby skonfigurować grupę granic  
 1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Ogólne** , aby zmodyfikować granice należące do tej grupy granic:  

     -   Aby dodać granice, kliknij przycisk **Dodaj**, zaznacz pole wyboru przynajmniej jednej granicy, a następnie kliknij przycisk **OK**.  

     -   Aby usunąć granicę, wybierz granicę i kliknij przycisk **Usuń**.  

 5.  Wybierz kartę **Odwołania** , aby zmodyfikować konfigurację przypisania lokacji i konfigurację skojarzonego serwera systemu lokacji:  

     -   Aby umożliwić tej grupy granic do użycia przez klientów do przypisania lokacji, wybierz **Użyj tej grupy granic do przypisania lokacji**. Następnie wybierz lokację z **przypisana lokacja** listy rozwijanej.  

     -   Aby skonfigurować dostępne serwery systemu lokacji, które będą skojarzone z tą grupą granic:  

     1.  Kliknij przycisk **Dodaj**, a następnie zaznacz pole wyboru dla przynajmniej jednego serwera. Serwery zostaną dodane jako skojarzone serwery systemu lokacji dla tej grupy granic. Dostępne będą tylko serwery, na których zainstalowano obsługiwaną rolę systemu lokacji.  

         > [!NOTE]  
         >  Można wybrać dowolną kombinację dostępnych systemów lokacji z dowolnej lokacji w hierarchii. Wybrane systemy lokacji są wyświetlane na karcie **Systemy lokacji** we właściwościach wszystkich granic należących do tej grupy granic.  

     2.  Aby usunąć serwer z grupy granic, wybierz serwer i kliknij przycisk **Usuń**.  

         > [!NOTE]  
         >  Aby przerwać użycie tej grupy granic do kojarzenia systemów lokacji, należy usunąć wszystkie serwery wyświetlane jako skojarzone serwery systemu lokacji.  

 6.  Aby skonfigurować działanie rezerwowe, wybierz **relacje** karty:  

     - Kliknij przycisk **Dodaj**, a następnie wybierz grupę granic, w której chcesz skonfigurować.

     - Ustaw czas rezerwowy dla punktów dystrybucji. Po tym okresie klienci w grupie granic, konfigurowanej relacji, będzie można rozpocząć wyszukiwanie zawartości z punktów dystrybucji do grupy granic, który dodajesz.

     - Aby zapobiec powrotu do określonej grupy, łącznie z *domyślnej grupy granic lokacji* skonfigurowanym domyślnie wybierz grupę granic, a następnie zaznacz pole wyboru, aby uzyskać **nigdy rezerwowy**.   

 7.  Kliknij przycisk **OK** , aby zamknąć właściwości grupy granic i zapisać konfigurację.  

#### <a name="to-associate-a-site-system-server-with-a-boundary-group"></a>Aby skojarzyć serwer systemu lokacji z grupą granic  
 1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Odwołania** .  

 5.  W obszarze **wybierz serwery systemu lokacji**, kliknij przycisk **Dodaj**. Wybierz serwery systemu lokacji skojarzone z tą grupą granic, a następnie kliknij przycisk **OK**.  

 6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację grupy granic.  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>Aby skonfigurować lokację rezerwową na użytek automatycznego przypisywania lokacji  

  1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** >  **witryny**.  

  2.  Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.  

  3.  Na karcie **Ogólne** zaznacz pole wyboru **Użyj lokacji rezerwowej**, a następnie wybierz lokację z listy rozwijanej **Lokacja rezerwowa** .  

  4.  Kliknij przycisk **OK** , aby zapisać konfigurację.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Aby włączyć korzystanie z preferowanych punktów zarządzania  

 1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** > **witryny**, a następnie na **Home** wybierz pozycję **ustawienia hierarchii**.  

 2.  Na karcie **Ogólne** w obszarze Ustawienia hierarchii wybierz pozycję **Klienci wolą używać punktów zarządzania określonych w grupach granic**.  

 3.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację.  
