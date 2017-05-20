---
title: Definiowanie grup granic | Dokumentacja firmy Microsoft
description: "Zrozumienie grup granic, połączonych klientów z systemami lokacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 5684fd4fbfd0ffb8f3ffbcfa122eef3dafd77327
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Konfigurowanie grup granic dla programu System Center Configuration Manager


*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Używasz grup granic w programie System Center Configuration Manager do logicznie grupy związane z lokalizacji sieciowych ([granice](/sccm/core/servers/deploy/configure/boundaries)) w celu ułatwienia zarządzania infrastrukturą. Przed użyciem grup granic należy do nich przypisać granice.

Domyślnie program Configuration Manager tworzy grupę granic lokacji domyślne w każdej lokacji.

> [!IMPORTANT]  
>  **Informacje przedstawione w tej sekcji grup granic i jego sekcji podrzędnych dotyczy wersji 1610 lub nowszej.** Ta zawartość została zmieniona jest specyficzny dla zmian projektowych wprowadzonych w grupach granic z tą wersją aktualizacji.
>
> **Jeśli używasz wersji przed 1610**, zobacz [grup granic dla programu System Center Configuration Manager w wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) informacji o sposobie używania i konfigurowania grup granic z tych wersji produktu.

Konfigurowanie grup granic, należy skojarzyć granic (lokalizacje sieciowe) i role systemu lokacji, takich jak punkty dystrybucji do grupy granic. Dzięki temu można skojarzyć klientów na serwerach systemu lokacji, takich jak punkty dystrybucji, które znajdują się w pobliżu klientów w sieci.

Możesz przypisać tej samej granicy do wielu grup granic, a tej samej lokacji serwery systemu, takich jak punkty dystrybucji do wielu grup granic zwiększa dostępność systemów lokacji dla szerszej lokalizacje sieciowe.

Klienci używają grupę granic dla:  

-   Automatycznego przypisywania lokacji  
-   Aby znaleźć serwer systemu lokacji, dostarczające usługi, w tym:
    - Punkty dystrybucji dla lokalizacji zawartości
    -    Punkty aktualizacji oprogramowania (począwszy od wersji 1702)
    - Punkty migracji stanu
    - Preferowane punkty zarządzania (Jeśli użyje preferowane punkty, konieczne jest włączenie tej opcji dla hierarchii, a nie za pomocą konfigurację grupy granic. Zobacz [aby umożliwić użycie preferowane punkty](#to-enable-use-of-preferred-management-points) w tym temacie.)

##  <a name="boundary-groups-and-relationships"></a>Grupy granic i relacji
Dla każdej grupy granic w hierarchii można przypisać:

-  Jeden lub więcej granic. Kiedy klient znajduje się w lokalizacji sieciowej, która jest zdefiniowana jako granicę przypisane do określonej grupy, która jest wywoływana **bieżącej** grupy granic. Klient może mieć więcej niż jednej grupy granic bieżącej.
- Jedną lub więcej ról systemu lokacji.  Klienci mogą zawsze używać ról systemu lokacji skojarzonego z ich bieżącej grupy granic. W zależności od dodatkowe konfiguracje mogą one można używać w grupach granic dodatkowe role systemu lokacji.  

Dla każdej grupy granic, którą można utworzyć można skonfigurować jednokierunkowe łącze do innej grupy. Łącze jest nazywany **relacji**. Łącze do grupy granic są nazywane **sąsiada** grup granic. Grupa granic może mieć wiele relacji, każdy z grupą granic określonych sąsiada.

Konfiguracja każdej relacji określa, kiedy klient, który zakończy się niepowodzeniem, aby dowiedzieć się, że serwer systemu lokacji dostępne w jego bieżącą grupę granic można rozpocząć wyszukiwanie sąsiada grupie granic, aby znaleźć system lokacji dostępny. To wyszukiwanie dodatkowe grupy jest nazywany **rezerwowy**.

## <a name="fallback"></a>Opcja rezerwowa
Aby zapobiec problemom dla klientów, gdy nie można znaleźć system lokacji dostępny w swojej bieżącej grupie granic, należy zdefiniować relacje między grupami granic, które definiuje zachowanie rezerwowego. Powrotu pozwala rozszerzyć poszukiwania do grup granic dodatkowe znaleźć system lokacji klienta.

Relacje są skonfigurowane we właściwościach grupy granic **relacje** kartę. Po skonfigurowaniu relacji, należy zdefiniować łącze do grupy granic sąsiada. Dla każdego typu Rola systemu lokacji, która jest obsługiwana można skonfigurować niezależnie od ustawienia powrotu do tej grupy granic sąsiada. Na przykład podczas konfigurowania relacji do określonej grupy można ustawić rezerwowy na wystąpić po upływie 20 minut zamiast domyślnego 120 punktów dystrybucji. Zobacz [przykład za pomocą grup granic](#example-of-using-boundary-groups) na przykład bardziej rozległe.

Jeśli klient nie może znaleźć dostępna Rola systemu lokacji w jego bieżącą grupę granic, klient używa rezerwowej czas w minutach ustalenie po ile można rozpocząć wyszukiwanie systemu lokacji skojarzonego z tej grupy granic sąsiada.  

Gdy klient nie może znaleźć system lokacji dostępny i rozpocznie się wyszukiwanie lokalizacji z grupy granic sąsiada, zwiększa puli systemów lokacji, które mogą być używane w sposób, który jest zdefiniowany przez konfigurację grupy granic i ich relacji.

- Grupa granic może mieć więcej niż jedną relację. Dzięki temu można skonfigurować rezerwowych dla każdego typu systemu lokacji do różnych sąsiadów nastąpi po różnych okresach czasu.    
- Klienci będą tylko powrotu do grupy granic, która jest bezpośrednie sąsiada ich bieżącej grupy granic.
- Gdy klient jest członkiem wielu grup granic, bieżącą grupę granic jest zdefiniowany jako sumę tego klienta grup granic. Ten klient może następnie powrotu do sąsiadów któregokolwiek z tych grup granic oryginalnej.

### <a name="the-default-site-boundary-group"></a>Domyślna grupa granic lokacji
Oprócz tworzone grupy granic każda lokacja ma domyślna grupa granic lokacji jest tworzona przez program Configuration Manager. Ta grupa ma nazwę ***granicy grupy, domyślne lokacji w-&lt;kod_lokacji >***. Na przykład grupy dla lokacji ABC będą miały postać *granicy grupy, domyślne lokacji w-&lt;ABC >.*

Dla każdej grupy granic tworzonych programu Configuration Manager automatycznie tworzy dorozumianych łącza do każdej grupy granic lokacji domyślne w hierarchii.
-    Dorozumiany łącze jest domyślne opcji rezerwowej z bieżącej grupy granic do domyślnej grupy granic lokacji ma domyślny czas rezerwowy 120 minut.
-    Klientów, którzy nie znajdują się na granicy skojarzony z żadną inną grupą granic w hierarchii Użyj domyślnej grupy granic lokacji z przypisanej lokacji, aby ustalić role systemu lokacji prawidłową, którego mogą używać.

Aby zarządzać powrotu do domyślnej grupy granic lokacji:
- Można przejść do właściwości grupy granic domyślnej witryny i zmienić wartości na **domyślne zachowanie** kartę. Zmiany wprowadzone w tym miejscu dotyczą *wszystkie* niejawnego łącza do tej grupy granic. Te ustawienia mogą zostać zastąpione podczas konfigurowania jawne łącze do tej grupy granic lokacji domyślne z innej grupy granic.
- Przejdź do właściwości grupy granic utworzonej i zmień wartości jawne łącze prowadzące do domyślnej grupy granic lokacji. Po ustawieniu nowego czasu w minutach, powrotu lub powrotu bloku zmiana dotyczy tylko łącze, które są konfigurowane. Konfiguracje jawne łącza zastępują ustawienia na **domyślne zachowanie** domyślne grupy granic lokacji.


## <a name="site-assignment"></a>Przypisanie lokacji  
 Do każdej grupy granic można wprowadzić przypisaną lokację do klientów.  

-   Nowo zainstalowany klient używający automatyczne przypisanie lokacji będzie dołączać do przypisanej lokacji grupy granic, zawierający bieżącą lokalizację sieciową klienta.  
-   Po przypisaniu do lokacji klient nie zmienia przypisania lokacji, gdy zmienia lokalizację sieciową. Na przykład jeśli klient przejdzie do nowej lokalizacji sieciowej, która jest reprezentowana przez granicę w grupie granic z innym przypisaniem lokacji, przypisana lokacja klienta zostaną zmienione.  
-   Kiedy funkcja odnajdowania systemu usługi Active Directory odnajdzie nowy zasób, informacje o sieci odnalezionego zasobu zostaną ocenione względem granic w grupach granic. Ten proces powoduje skojarzenie nowego zasobu z przypisaną lokacją w celu użycia przez metodę instalacji klienta w trybie wypychania.  
-   Jeśli granica należy do wielu grup granic z różnymi przypisanymi lokacjami, klienci będą losowo wybierać jedną z lokacji.  
-   Zmiany lokacji przypisanej do grup granic dotyczą tylko nowych akcji przypisania lokacji. Klienci, którzy zostali już wcześniej przypisani do lokacji, nie ocenią ponownie przypisania lokacji na podstawie zmiany konfiguracji grupy granic (ani na podstawie zmiany własnej lokalizacji sieciowej).  

Aby uzyskać więcej informacji o przypisywaniu lokacji klienta, zobacz [za pomocą automatycznego przypisania lokacji dla komputerów](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Punkty dystrybucji

Gdy klient żąda położenie punktu dystrybucji, Configuration Manager wysyła klientowi listę, która obejmuje systemy lokacji odpowiedniego typu, które są skojarzone z każdą grupą granic zawierającą bieżącą lokalizację sieciową klientów:

-   **Podczas dystrybucji oprogramowania**, klient żąda lokacji wdrożenia zawartości, która jest dostępna z punktem dystrybucji lub innych prawidłowego źródła zawartości (takich jak klient skonfigurowany do Buforowanie równorzędne).

-   **Podczas wdrażania systemu operacyjnego**, klient żąda lokacji do wysłania lub odebrania informacji o migracji stanu.  

Podczas wdrażania zawartości Jeśli klient zażąda zawartości, który nie jest dostępny ze źródła w jego bieżącą grupę granic, klient w dalszym ciągu żądania tej zawartości do momentu osiągnięcia rezerwowy okres dla grupy granic sąsiada lub domyślna grupa granic lokacji w trakcie różnych źródeł zawartości w jego bieżącą grupę granic. Jeśli klient nie odnalazł jeszcze zawartości, następnie rozwija wyszukiwania źródła zawartości uwzględnić sąsiada grup granic.

Jednak jeśli zawartość będzie rozmieszczona na żądanie i nie są dostępne w punkcie dystrybucji, gdy żądana przez klienta, rozpoczyna proces transferu zawartości do tego punktu dystrybucji i jest możliwe, klient będzie przed powrotem do używania grupy granic sąsiada znaleźć tego serwera jako źródła zawartości.

## <a name="software-update-points"></a>Punkty aktualizacji oprogramowania
Począwszy od wersji 1702, klienci używają grup granic do znalezienia punktu aktualizacji oprogramowania. Punkty aktualizacji oprogramowania można dodać do grupy granic różnych do serwerów, które klient może znaleźć formantu.

Uaktualnienie z wersji przed 1702, wszystkie istniejące punkty aktualizacji oprogramowania są dodawane do domyślnej grupy granic lokacji w każdej lokacji. Zapewnia to dostępność zachowanie sprzed aktualizacji, której klienci wybierają punkt aktualizacji oprogramowania z puli punkty aktualizacji oprogramowania dostępne, które skonfigurowano dla hierarchii.  To zachowanie jest zachowywana, dopóki nie zostanie wybrana dodać punkty aktualizacji oprogramowania do grupy granic różnych wybór kontrolowanych i zachowanie rezerwowego.

W przypadku instalowania nowej lokacji z uruchomioną wersją 1702 lub później, należy przypisać punkty aktualizacji oprogramowania do grupy granic zanim klienci mogą znaleźć i używać ich.


Rezerwowych punktów aktualizacji oprogramowania jest skonfigurowany, podobnie jak inne role systemu lokacji, ale ma następujące ostrzeżenia:
- **Nowi klienci używają grup granic, aby wybrać punkty aktualizacji oprogramowania.** Po zainstalowaniu wersji 1702 nowych klientów, które można zainstalować, wybierz punkt aktualizacji oprogramowania z skojarzonych z grupy granic skonfigurowane.

  Spowoduje to zastąpienie poprzednie zachowanie, w którym klienci wybrać punkt aktualizacji oprogramowania losowo z listy tych, które współużytkują lasu klienta.

- **Wcześniej klientów zainstalowanych nadal używać ich bieżącego punktu aktualizacji oprogramowania do czasu powrotu znaleźć nową.** Klientów, które zostały wcześniej zainstalowane, a który jeszcze punkt aktualizacji oprogramowania będzie używać tego punktu aktualizacji oprogramowania, dopóki ten serwer jest nieosiągalny. Obejmuje to dalsze używanie punkt aktualizacji oprogramowania, który nie jest skojarzony z bieżącą grupę granic klienta.

  W przypadku awarii dostęp do klienta, który ma już punkt aktualizacji oprogramowania klient może następnie powrotu do znalezienia innego. Korzystając z rezerwowych, klient odbierze listę wszystkich punktów aktualizacji oprogramowania z jego bieżącej grupy granic. Jeśli nie znaleźć dostępnego serwera na 120 minut, zostanie następnie powrotu do jego grupę granic sąsiada i domyślna grupa granic lokacji. Powrót do obu grup granic spowodowany w tym samym czasie punkty czasu powrotu do grup sąsiada jest ustawiona na 120 minut i nie można zmienić aktualizacji oprogramowania. 120 minut jest również używana do powrotu do domyślnej grupy granic lokacji domyślny okres. Gdy klient powraca do obu sąsiada i domyślna grupa granic lokacji, klient próbuje połączyć się z punktami aktualizacji oprogramowania z grupy granic sąsiada przed podjęciem próby użycia jednej z domyślnej grupy granic lokacji.

  Dalsze używanie istniejącego punktu aktualizacji oprogramowania nawet wtedy, gdy ten serwer nie jest bieżącą grupę granic klienta jest zamierzone. Jest to spowodowane zmianą punktu aktualizacji oprogramowania może spowodować duże wykorzystanie przepustowości sieci jak klient synchronizuje dane z punktem aktualizacji oprogramowania. Opóźnienie w okresie przejściowym może pomóc uniknąć nasycanie sieci należy wszystkich klientów przełączyć się do nowego oprogramowania punkt aktualizacji w tym samym czasie.

- **Konfiguracje rezerwowy czasu:**  W przeciwieństwie do rezerwowego konfiguracje dla innych ról systemu lokacji punkty aktualizacji oprogramowania nie jest jeszcze obsługiwany konfigurowalne czas w minutach. Zamiast tego zachowanie rezerwowego jest ograniczone do następujących:  
  - **Rezerwowy czas (w minutach):**  Ta opcja jest wyszarzone punktów aktualizacji oprogramowania i nie można skonfigurować. Zostanie ona ustawiona na 120 minut.
  -     **Nigdy nie rezerwowego:** Możesz zablokować rezerwowych dla punktu aktualizacji oprogramowania do grupy granic sąsiada używania tej konfiguracji.

## <a name="preferred-management-points"></a>Preferowane punkty

 Preferowane punkty zarządzania umożliwiają klientom identyfikowanie punktów zarządzania skojarzonych z ich bieżącą lokalizacją sieciową (granicą).  

-   Klient próbuje użyć preferowanym punktem zarządzania z przypisanej mu lokacji przed rozpoczęciem korzystania z punktem zarządzania z przypisanej mu lokacji, który nie jest skonfigurowany jako preferowany.  
-   Aby użyć tej opcji, należy ją włączyć w hierarchii, a następnie skonfiguruj grupy granic w poszczególnych lokacjach głównych należy uwzględnić punkty zarządzania, które mogą być skojarzone z tej grupy granic granice skojarzone.  
-   Jeśli preferowane punkty zostały skonfigurowane, a klient organizuje listy punktów zarządzania, klient umieszcza preferowane punkty w górnej części listy punktów zarządzania przypisanej (co obejmuje wszystkie punkty zarządzania w przypisanej lokacji klienta).  

> [!NOTE]  
>  Gdy klient przemieszcza się (co oznacza, że zmienia lokalizację sieciową, np. laptop pojawia się w lokalizacji biura zdalnego), może w nowej lokalizacji używać punktu zarządzania (lub punktu zarządzania serwera proxy) z lokacji lokalnej przed podjęciem próby użycia punktu zarządzania z przypisanej lokacji (która obejmuje preferowane punkty zarządzania).  Zobacz [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) uzyskać więcej informacji.  

### <a name="overlapping-boundaries"></a>Nakładanie się granic  
 Program Configuration Manager obsługuje konfiguracje nakładających się granic dla lokalizacji zawartości:  

-   **Gdy klient zażąda zawartości**, a lokalizacja sieciowa klienta należy do różnych grup granic, program Configuration Manager wysyła klientowi listę wszystkich punktów dystrybucji z zawartością.  
-   **Gdy klient zażąda serwera, aby wysłać lub odebrać informacje o migracji stanu**, a lokalizacja sieciowa klienta należy do różnych grup granic, program Configuration Manager wysyła klientowi listę punktów migracji stanu skojarzonych z grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Pozwala to klientowi na wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  



## <a name="example-of-using-boundary-groups"></a>Przykład użycia grupy granic
W poniższym przykładzie użyto klienta wyszukiwanie zawartości z punktu dystrybucji. W tym przykładzie można zastosować do innych ról systemu lokacji, które używają grup granic. Jednak jak dotyczy punkty aktualizacji oprogramowania, należy pamiętać, że punkty aktualizacji oprogramowania nie obsługuje konfiguracji czas w minutach, powrotu do grupy sąsiada i zawsze używaj 120 minut.

Utwórz trzy grupy granic, które nie mają granice lub serwerów systemu lokacji:
-    Grupa BG_A z punktami dystrybucji DP_A1 i DP_A2 skojarzonego z grupą
-    Grupa BG_B z punktami dystrybucji DP_B1 i DP_B2 skojarzonego z grupą
-    Grupa BG_C z punktami dystrybucji DP_C1 i DP_C2 skojarzonego z grupą

Dodaj lokalizacje sieciowe klientów do tylko grupy granic BG_A i następnie skonfigurować relacje z tej grupy granic do innych grup granic dwóch:
-    Konfigurowanie punktów dystrybucji w pierwszym *sąsiada* grupy (BG_B) do użycia po 10 minutach. Ta grupa zawiera punkty dystrybucji DP_B1 i DP_B2. Oba są dobrze połączony z pierwszym lokalizacje granic grup.
-    Skonfiguruj drugi *sąsiada* grupy (BG_C) do użycia po upływie 20 minut. Ta grupa zawiera punkty dystrybucji DP_C1 i DP_C2. Oba są w sieci WAN z innych dwóch grup granic.
-    Również dodać punkt dystrybucji dodatkowe znajdujący się na serwerze lokacji do grupy granic lokacji domyślnej witryny. To jest najmniej polecana lokalizacji źródła zawartości, ale znajduje centralnie do grup granic.

    Przykład grupy granic i czasy rezerwowego:

     ![BG_Fallack](media/BG_Fallback.png)


W przypadku tej konfiguracji:
-    Klient rozpoczyna wyszukiwanie zawartości z punktów dystrybucji w jego *bieżącej* grupy granic (BG_A), wyszukiwanie dystrybucji każdego punktu dla dwóch minut przed przejściem do następnego punktu dystrybucji w grupie granic. Pula klientów z lokalizacji prawidłowego źródła zawartości zawiera DP_A1 i DP_A2.
-    Jeśli klient nie może odnaleźć zawartości z jego *bieżącej* grupy granic po przeszukaniu przez 10 minut, następnie dodaje punkty dystrybucji z grupy granic BG_B do wyszukiwania. Następnie nadal wyszukiwania zawartości z punktu dystrybucji w jego połączonych puli punktów dystrybucji, która zawiera te z BG_A i BG_B grup granic. Klient w dalszym ciągu skontaktować się z każdym punkcie dystrybucji dla dwóch minut przed przejściem do następnego punktu dystrybucji z puli. Pula klientów z lokalizacji prawidłowego źródła zawartości obejmuje DP_A1, DP_A2, DP_B1 i DP_B2.
-    Po 10 minutach dodatkowe (całkowita liczba 20 minut) Jeśli klient nadal ma nie można odnaleźć punktu dystrybucji z zawartością, rozszerza puli dostępnych punktów dystrybucji te od drugiego *sąsiada* grupie grupy granic BG_C. Klient jest teraz ma 6 punktów dystrybucji do wyszukiwania (DP_A1, DP_A2, DP_B2, DP_B2, DP_C1 i DP_C2) i kontynuuje wprowadzanie zmian do nowego punktu dystrybucji, co dwie minuty, aż do znalezienia zawartości.
-    Jeśli klient nie odnalazł zawartości po łącznie 120 minut, jego powraca do obejmują *domyślna grupa granic lokacji* w ramach jego ciągłego wyszukiwania. Teraz puli punktów dystrybucji zawiera wszystkie punkty dystrybucji z trzech skonfigurowanych grup granic i punktu końcowego dystrybucji znajdujących się na komputerze serwera lokacji.  Klient kontynuuje wyszukiwanie zawartości, zmiana punktów dystrybucji, co dwie minuty, aż do znalezienia zawartości.

Konfigurując grupy różnych sąsiada była dostępna w różnym czasie kontrolować po dodaniu konkretnych punktów dystrybucji jako lokalizacji źródła zawartości i gdy lub jeśli klient korzysta z powrotu do domyślnej grupy granic lokacji jako zabezpieczenie zawartości, które nie są dostępne z innej lokalizacji.






### <a name="update-existing-boundary-groups-to-the-new-model"></a>Aktualizowanie istniejących grup granic do nowego modelu
Podczas aktualizacji do wersji przed 1610, automatycznie stają się następujące konfiguracje. Są one przeznaczone do upewnij się, że Twoje bieżące zachowanie rezerwowego pozostaje dostępna, dopóki nie zostanie skonfigurowana nowej grupy granic i relacje.

-    Domyślne grupy granic lokacji jest tworzony dla każdej lokacji głównej, nazwa jest ***granicy grupy, domyślne lokacji w-&lt;kod lokacji >.***
  -    Punkty dystrybucji z *Zezwalaj na rezerwową lokalizację źródła zawartości* sprawdzany i punktów migracji stanu w lokacjach głównych są dodawane do *granicy grupy, domyślne lokacji w-&lt;kod lokacji >* grupy granic tej lokacji.
  -    Począwszy od wersji 1702, punkty aktualizacji oprogramowania są dodawane do każdej lokacji *granicy grupy, domyślne lokacji w-&lt;kod_lokacji >*.
-    Kopię składa się z każdej istniejącej grupy granic, która zawiera serwer lokacji, skonfigurowany z wolnego połączenia. Nazwa nowej grupy jest *** &lt;oryginalna nazwa grupy granic >-&lt;pierwotny identyfikator grupy granic >***:  
    -    Systemy lokacji z szybkim połączeniu są pozostawiane w oryginalnej grupie granic.
    -    Kopię systemy lokacji (punktami dystrybucji, punkty zarządzania) z wolnego połączenia są dodawane do kopiowania grupy granic. Oryginalny systemów lokacji, skonfigurowany jako wolne pozostają w ich oryginalnej grup granic dla zgodności z poprzednimi wersjami, ale nie są używane z tych grup granic.
    - Ta kopia grupy granic nie ma granicach skojarzonych z nim. Jednakże tworzone jest połączenie rezerwowy między oryginalna grupa i nową kopię grupy granic ma rezerwowy czasu, należy ustawić na zero.  


- **Specyficzne dla dodatkowej lokacji:**
  - Grupy granic jest tworzone, jeśli Lokacja pomocnicza ma co najmniej jeden punkt z dystrybucji *Zezwalaj na rezerwową lokalizację źródła zawartości* punkt migracji stanu lub zaznaczone. Nazwa grupy granic to ***pomocniczym-witryny-sąsiada--Tmp&lt;kod lokacji >.***
  - Punkty dystrybucji wszystkie z *Zezwalaj na rezerwową lokalizację źródła zawartości* sprawdzane i punktów migracji stanu zostaną dodane do tej grupy granic nowo utworzonej lokacji dodatkowej.
  - Tworzone jest połączenie rezerwowy między oryginalna grupa granic i grupy granic sąsiada nowo utworzony i czas rezerwowego jest równa zero.


 W poniższej tabeli przedstawiono nowe zachowanie rezerwowego można spodziewać się z kombinacji oryginalnego ustawienia wdrożenia i punktu dystrybucji konfiguracje:

"Nie uruchamiaj programu" w sieci o niskiej prędkości oryginalna konfiguracja wdrożenia  |Punkt dystrybucji oryginalna konfiguracja "Client Zezwalaj na użycie rezerwowej lokalizacji źródła zawartości"  |Nowe działanie rezerwowe  
---------|---------|---------
Wybrane     |  Wybrane    |  **Nie powrotu** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Wybrane     |  Nie wybrano|  **Nie powrotu** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Nie wybrano |  Nie wybrano|  **Powrót do sąsiada** — używać punktów dystrybucji w bieżącej grupie granic, a następnie dodaj punkty dystrybucji z grupy granic sąsiada. Chyba że jawne łącze do domyślnej grupy granic lokacji jest skonfigurowany, klienci nie będą powrotu do tej grupy.    
Nie wybrano | Wybrane        |   **Normalne powrotu** -używać punktów dystrybucji w bieżącej grupie granic, a następnie te z sąsiada i lokacji domyślne grupy granic

 Inne konfiguracje wdrożenia spowodować **normalnego powrotu**.  




## <a name="changes-from-prior-versions-for-ui-and-behavior-for-content-locations"></a>Zmiany z poprzednich wersji interfejsu użytkownika i zachowanie dla lokalizacji zawartości
Dostępne są następujące zmiany klucza do grupy granic i znajdowania zawartości klientom. Zmiany zostaną wprowadzone w wersji 1610. Wiele z tych zmian i pojęcia współpracują ze sobą.


-    **Konfiguracje dla Fast lub wolno zostaną usunięte:** Można już konfigurować poszczególne punkty dystrybucji do szybkiego lub powolnego.  Zamiast tego każdy system lokacji skojarzone z grupą granic jest traktowany takie same. Z powodu tej zmiany **odwołania** karta właściwości grupy granic nie obsługuje już konfiguracji Fast lub niska.
-     **Nową grupę granic domyślne w każdej lokacji:**  Każda lokacja główna ma nowej grupy granic domyślna o nazwie ***granicy grupy, domyślne lokacji w-&lt;kod_lokacji >***.  Gdy klient nie jest w lokalizacji sieciowej, która jest przypisana do grupy granic, ten klient użyje systemy lokacji skojarzone z grupą domyślne z przypisanej mu lokacji. Zaplanuj użycie tej grupy granic zastępujący koncepcję rezerwowej lokalizacji zawartości.      
 -    **"Zezwalaj na lokalizacje rezerwowego źródła zawartości"** zostanie usunięty: Nie jest już jawnie skonfigurować punkt dystrybucji ma być używany dla powrotu i opcje tę są usuwane z interfejsu użytkownika.

    Ponadto wynik ustawienie **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości** na wdrożenie zmienił się typ dla aplikacji. To ustawienie w typie wdrożenia teraz umożliwia klienta do używania domyślnej grupy granic lokacji jako lokalizację źródła zawartości.

 -    **Relacje grupy granic:** Każda grupa granic może zostać powiązany z co najmniej jedną grupę granic dodatkowe. Te łącza tworzą relacje, które są skonfigurowane na karcie właściwości nowej grupy granic o nazwie **relacje**:
     -    Każdą grupą granic, klient jest bezpośrednio z którym skojarzony jest nazywany **bieżącej** grupy granic.  
    -     Każda grupa granic klient może korzystać z powodu skojarzenia między ten klient *bieżącej* nosi nazwę grupy granic i innej grupy **sąsiada** grupy granic.
    -  Znajduje się ona na **relacje** kartę dodawanej grupy granic, które mogą być używane jako *sąsiada* grupy granic. Można również skonfigurować czas w minutach, które określa, kiedy klient, który nie może odnaleźć zawartości z punktu dystrybucji w *bieżącej* grupy rozpocznie się wyszukiwanie lokalizacji zawartości z tymi *sąsiada* grup granic.

        Podczas dodawania lub zmiany konfiguracji grupy granic, trzeba będzie opcja powrotu do tej grupy granic określone z bieżącej grupy, które są konfigurowane w bloku.

    Aby użyć nowej konfiguracji, definiowanie skojarzeń jawne (linki) z jednej grupy granic do innego i skonfiguruj wszystkie punkty dystrybucji w tej grupie skojarzone z tym samym czasie, w minutach. Podczas konfigurowania Określa, kiedy klient, który nie może odnaleźć Źródło zawartości z jego *bieżącej* grupy granic można rozpocząć wyszukiwanie źródła zawartości z tej grupy granic sąsiada.

    Oprócz grup granic, które jawnie skonfigurować każdą grupą granic ma dorozumianych łącze do domyślnej grupy granic lokacji. To łącze staje się aktywny po 120 minut po tym czasie domyślna grupa granic lokacji staje się grupie granic sąsiada, która umożliwia klientom korzystanie z punktów dystrybucji skojarzone z daną grupą granic jako lokalizacji źródła zawartości.

    To zachowanie zastępuje, co było wcześniej nazywane rezerwowych dla zawartości.  Można zastąpić to domyślne zachowanie 120 minut dokonując jawnie domyślna grupa granic lokacji do *bieżącej* grupy i ustawienie określony czas w minutach lub blokowanie powrotu całkowicie uniemożliwić korzystanie z niego.


-     **Klienci próbują uzyskać zawartości z poszczególnych punktów dystrybucji przez maksymalnie 2 minuty:** Gdy klient wyszukuje lokalizacji źródła zawartości, podejmie próbę dostępu do poszczególnych punktów dystrybucji dla dwóch minut przed podjęciem próby następnie innego punktu dystrybucji. Jest zmiany z poprzednich wersji, gdzie klienci próbował łączyć się z punktem dystrybucji przez maksymalnie 2 godziny.

    - Pierwszy punkt dystrybucji, klient próbuje użyć losowo z puli dostępnych punktów dystrybucji na komputerze klienckim *bieżącej* grupy granic (lub grup).

    - Po upływie dwóch minut Jeśli klient ma nie można odnaleźć zawartości, ją przełącza się do nowego punktu dystrybucji i próbuje pobrać zawartości z tego serwera. Ten proces jest powtarzany co dwie minuty, dopóki klient znajdzie zawartość lub osiągnie ostatniego serwera jej puli.

    - Jeśli klient nie może znaleźć lokalizację prawidłowego źródła zawartości z jego *bieżącej* puli przed okres powrotu do *sąsiada* osiągnięciu grupy granic, klient następnie dodaje punktów dystrybucji niż *sąsiada* grupy w celu jego bieżącą listę i następnie przeszuka rozwiniętej grupy lokalizacje źródłowe, która zawiera punkty dystrybucji z obu grup granic.

        > [!TIP]  
        > Po utworzeniu jawne łącze z bieżącej grupy granic do domyślnej grupy granic lokacji i zdefiniować rezerwowy godzinę, która jest mniejsza niż czas rezerwowy dla łącza do grupy granic sąsiada, klienci rozpocznie się wyszukiwanie lokalizacje źródłowe do domyślnej grupy granic lokacji przed tym grupy sąsiada.

    - Gdy klient nie może pobrać zawartości z ostatnich serwera w puli, rozpoczyna proces ponownie.


## <a name="procedures-for-boundary-groups"></a>Procedury dotyczące grup granic
Poniższe procedury dotyczą wersji 1610 lub nowszej. Jeśli używasz wersji przed 1610 zapoznać się z procedurami w [grup granic dla programu System Center Configuration Manager w wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).


### <a name="to-create-a-boundary-group"></a>Aby utworzyć grupę granic  
1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz grupę granicę**.  

3.  W oknie dialogowym **Utwórz grupę granicę** wybierz kartę **Ogólne** i określ **nazwę** tej grupy granic.  

4.  Kliknij przycisk **OK** , aby zapisać nową grupę granic.  


### <a name="to-configure-a-boundary-group"></a>Aby skonfigurować grupę granic  
 1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Ogólne** , aby zmodyfikować granice należące do tej grupy granic:  

     -   Aby dodać granice, kliknij przycisk **Dodaj**, zaznacz pole wyboru przynajmniej jednej granicy, a następnie kliknij przycisk **OK**.  

     -   Aby usunąć granicę, wybierz granicę i kliknij przycisk **Usuń**.  

 5.  Wybierz kartę **Odwołania** , aby zmodyfikować konfigurację przypisania lokacji i konfigurację skojarzonego serwera systemu lokacji:  

     -   Aby umożliwić użycie tej grupy granic przez klientów do przypisania lokacji, zaznacz pole wyboru **Użyj tej grupy granic do przypisania lokacji**, a następnie wypisz lokację z listy rozwijanej **Przypisana lokacja** .  

     -   Aby skonfigurować dostępne serwery systemu lokacji, które będą skojarzone z tą grupą granic:  

     1.  Kliknij przycisk **Dodaj**, a następnie zaznacz pole wyboru dla przynajmniej jednego serwera. Serwery zostaną dodane jako skojarzone serwery systemu lokacji dla tej grupy granic. Dostępne będą tylko serwery, na których zainstalowano obsługiwaną rolę systemu lokacji.  

         > [!NOTE]  
         >  Można wybrać dowolną kombinację dostępnych systemów lokacji z dowolnej lokacji w hierarchii. Wybrane systemy lokacji są wyświetlane na karcie **Systemy lokacji** we właściwościach wszystkich granic należących do tej grupy granic.  

     2.  Aby usunąć serwer z grupy granic, wybierz serwer i kliknij przycisk **Usuń**.  

         > [!NOTE]  
         >  Aby przestać używać tej grupy granic na potrzeby kojarzenia systemów lokacji, należy usunąć wszystkie serwery wyświetlane jako skojarzone serwery systemu lokacji.  

 6.  Wybierz **relacje** kartę, aby skonfigurować zachowanie rezerwowego:  

     - Kliknij przycisk **Dodaj**, a następnie wybierz grupę granic, którą chcesz skonfigurować.

     - Ustaw czas rezerwowy dla punktów dystrybucji. Po tym czasie klienci w grupie granic, którą konfigurujesz relacje, będzie można rozpocząć wyszukiwanie zawartości z punktów dystrybucji dodawanej grupy granic.

     - Aby zapobiec powrotu do określonej grupy, w tym *domyślna grupa granic lokacji* którego jest domyślnie konfigurowana, wybierz grupę granic, a następnie sprawdź pole **nigdy rezerwowy**.   

 7.  Kliknij przycisk **OK** , aby zamknąć właściwości grupy granic i zapisać konfigurację.  

#### <a name="to-associate-a-site-systme-server-with-a-boundary-group"></a>Aby powiązać serwer lokacji systme z grupą granic  
 1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Odwołania** .  

 5.  W sekcji **Wybierz serwery systemu lokacji**kliknij przycisk **Dodaj**, zaznacz pola wyboru dla serwerów systemu lokacji, które chcesz skojarzyć z tą grupą granic, a następnie kliknij przycisk **OK**.  

 6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację grupy granic.  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>Aby skonfigurować lokację rezerwową na użytek automatycznego przypisywania lokacji  

  1.  W konsoli programu Configuration Manager kliknij **Administracja** > **konfiguracja lokacji** >  **witryny**.  

  2.  Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.  

  3.  Na karcie **Ogólne** zaznacz pole wyboru **Użyj lokacji rezerwowej**, a następnie wybierz lokację z listy rozwijanej **Lokacja rezerwowa** .  

  4.  Kliknij przycisk **OK** , aby zapisać konfigurację.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Aby włączyć korzystanie z preferowanych punktów zarządzania  

 1.  W konsoli programu Configuration Manager kliknij **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie na **Home** wybierz opcję **ustawienia hierarchii**.  

 2.  Na karcie **Ogólne** w obszarze Ustawienia hierarchii wybierz pozycję **Klienci wolą używać punktów zarządzania określonych w grupach granic**.  

 3.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację.  

