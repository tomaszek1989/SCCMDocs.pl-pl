---
title: "Ochrona aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi | Dokumentacja firmy Microsoft"
description: "Modyfikowanie funkcji aplikacje wdrażane tak spełniają firmowych zgodności i zasady zabezpieczeń."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28115475-e563-4e16-bf30-f4c9fe704754
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 74f4dd44089d4a13526c981589e1f497f0e10290
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="protect-apps-using-mobile-application-management-policies-in-system-center-configuration-manager"></a>Ochrona aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zasady zarządzania programu System Center Configuration Manager aplikacji umożliwiają modyfikowanie funkcjonalności aplikacje wdrażane w celu dostosowania ich firmy zasad dotyczących zgodności i zabezpieczeń. Na przykład możesz ograniczyć wycinania, kopiowania i wklejanie w aplikacji lub skonfigurować aplikację tak, aby otworzyć wszystkie adresy URL w przeglądarce zarządzanej. Zasady zarządzania aplikacjami obsługują:  

-   Urządzenia z systemem Android 4 i nowszym  

-   Urządzenia z systemem iOS 7 i nowszym  

Zasady zarządzania aplikacjami mobilnymi umożliwia również chronić aplikacje na urządzeniach, które nie są zarządzane przez usługę Intune. Przy użyciu tej nowej możliwości, można stosować zasady zarządzania aplikacjami mobilnymi do aplikacji, które połączyć się z usługami Office 365. Nie jest to obsługiwane w przypadku aplikacji łączących się do lokalnego programu Exchange i SharePoint.  

Aby korzystać z tej nowej możliwości, należy korzystać z portalu Azure (wersja zapoznawcza). W poniższych tematach znajdują się informacje ułatwiające rozpoczęcie pracy:  
-   [Rozpoczynanie pracy z zasadami zarządzania aplikacjami mobilnymi w portalu Azure](https://technet.microsoft.com/library/mt627830.aspx)  
-   [Tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi przy użyciu usługi Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx)  

 Nie można wdrożyć zasady zarządzania aplikacjami bezpośrednio, tak jak pozycje konfiguracji i linii bazowych w programie Configuration Manager. Należy je skojarzyć z typem wdrożenia aplikacji, który ma zostać ograniczony. Po wdrożeniu i zainstalowaniu na urządzeniach typu wdrożenia aplikacji, należy określić ustawienia zostały wprowadzone.  

Aby zastosować ograniczenia dla aplikacji, aplikacja musi mieć Microsoft Intune App Software Development Kit (SDK). Istnieją dwie metody uzyskania tego typu aplikacji:  

-   **Użycie aplikacji zarządzanej przez zasady** (Android i iOS): Te aplikacje mają wbudowany zestaw SDK aplikacji. Aby dodać ten typ aplikacji, wystarczy podać link do wybranej aplikacji w sklepie z aplikacjami, takim jak iTunes lub Google Play. Żadne dalsze przetwarzanie nie jest wymagane w przypadku tego typu aplikacji. Listę aplikacji zarządzanych przez zasady, które są dostępne dla urządzeń z systemami iOS i Android, zamieszczono w artykule [Aplikacje zarządzane przy użyciu zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](https://technet.microsoft.com/en-us/library/dn708489.aspx).  

-   **Użycie aplikacji "zawinięty"** (Android i iOS): Te aplikacje są celu dodania do nich zestawu SDK aplikacji za pomocą **Microsoft Intune narzędzia opakowującego aplikacje**. To narzędzie jest zwykle używane do przetwarzania aplikacji firmowych utworzonych wewnętrznie. Nie można go używać do przetwarzania aplikacji, które zostały pobrane ze sklepu z aplikacjami. Zobacz następujące artykuły, aby uzyskać więcej informacji:
    - [Przygotowanie aplikacji systemu iOS do zarządzania aplikacjami mobilnymi za pomocą programu Microsoft Intune narzędzia opakowującego aplikacje](https://technet.microsoft.com/en-us/library/dn878028.aspx)

    - [Przygotowanie aplikacji systemu Android do zarządzania aplikacjami mobilnymi za pomocą programu Microsoft Intune narzędzia opakowującego aplikacje](https://technet.microsoft.com/en-us/library/mt147413.aspx)  

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Tworzenie i wdrażanie aplikacji podlegającej zasadom zarządzania aplikacjami mobilnymi  

##  <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>Krok 1: Uzyskaj link do aplikacji zarządzanej przez zasady lub Utwórz opakowaną aplikację  

-   **Aby uzyskać łącze do zasad aplikacji zarządzanej**: Ze sklepu z aplikacjami Znajdź i zanotuj adres URL aplikacji zarządzanej przez zasady, którą chcesz wdrożyć.  

     Na przykład adres URL aplikacji Microsoft Word dla urządzenia iPad to **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**  

-   **Aby utworzyć opakowaną aplikację**: Informacje zawarte w tematach [przygotowanie aplikacji systemu iOS do zarządzania aplikacjami mobilnymi za pomocą programu Microsoft Intune narzędzia opakowującego aplikacje](https://technet.microsoft.com/en-us/library/dn878028.aspx) i [przygotowanie aplikacji Android do zarządzania aplikacjami mobilnymi za pomocą programu Microsoft Intune narzędzia opakowującego aplikacje](https://technet.microsoft.com/en-us/library/mt147413.aspx) Aby utworzyć opakowaną aplikację.  

     Narzędzie tworzy przetworzoną aplikację i skojarzony plik manifestu. Pliki te są używane podczas tworzenia aplikacji programu Configuration Manager, który zawiera aplikację.  

##  <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>Krok 2: Tworzenie aplikacji programu Configuration Manager, który zawiera aplikację  
 Procedury tworzenia aplikacji programu Configuration Manager różni się w zależności od tego, czy używana aplikacja zarządzana przez zasady (łącze zewnętrzne) lub aplikacji, która została utworzona przy użyciu programu Microsoft Intune narzędzia opakowującego aplikacje dla systemu iOS (pakiet aplikacji dla systemu iOS). Do tworzenia aplikacji programu Configuration Manager, należy użyć jednej z poniższych procedur.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  W **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji** otworzyć **tworzenie aplikacji** kreatora.  

4.  Na stronie **Ogólne** wybierz opcję **Automatycznie wykryj informacje o tej aplikacji z plików instalacyjnych**.  

5.  Z listy rozwijanej **Typ** wybierz pozycję **Pakiet aplikacji dla systemu iOS (\*plik ipa)**.  

6.  Wybierz **Przeglądaj** aby wybrać pakiet aplikacji, które chcesz zaimportować, a następnie wybierz **dalej**.  

7.  Na stronie **Informacje ogólne** wprowadź opis oraz informacje o kategorii, które będą widoczne dla użytkowników w portalu firmy.  

8.  Ukończ pracę kreatora.  

 Nowa aplikacja jest wyświetlana w węźle **Aplikacje** w obszarze roboczym **Biblioteka oprogramowania** .  

### <a name="create-an-application-that-contains-a-link-to-a-policy-managed-app"></a>Tworzenie aplikacji zawierającej łącze do aplikacji zarządzanej przez zasady  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  W **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji** otworzyć **tworzenie aplikacji** kreatora.  

4.  Na stronie **Ogólne** wybierz opcję **Automatycznie wykryj informacje o tej aplikacji z plików instalacyjnych**.  

5.  Z listy rozwijanej **Typ** wybierz jedną z następujących pozycji:  

    -   Dla systemu iOS: **Pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**  

    -   Dla systemu Android: **Pakiet aplikacji dla systemu Android w witrynie Google Play**  

6.  Wprowadź adres URL aplikacji (z kroku 1), a następnie wybierz **dalej**.  

7.  Na stronie **Informacje ogólne** wprowadź opis oraz informacje o kategorii, które będą widoczne dla użytkowników w portalu firmy.  

8.  Ukończ pracę kreatora.  

 Nowa aplikacja jest wyświetlana w węźle **Aplikacje** w obszarze roboczym **Biblioteka oprogramowania** .  

##  <a name="step-3-create-an-application-management-policy"></a>Krok 3: Utwórz zasady zarządzania aplikacjami  
 Następnie utwórz zasady zarządzania aplikacjami, która jest skojarzona z aplikacją. Możesz utworzyć zasady ogólne lub zasady zarządzanej przeglądarki.  

1)  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **zasad zarządzania aplikacjami**.  

2)  W **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zasady zarządzania aplikacjami**.  

3)  Na **ogólne** strony, wprowadź nazwę i opis zasad, a następnie wybierz **dalej**.  

4)  Na **typ zasad** wybierz platformy i typ zasad dla tych zasad, a następnie wybierz **dalej**. Dostępne są następujące typy zasad:  

-   **Ogólne**: Typ zasady ogólne umożliwia modyfikowanie funkcjonalności aplikacje wdrażane w celu dostosowania ich firmowych zgodności i zasady zabezpieczeń. Można na przykład ograniczyć operacje wycinania, kopiowania i wklejania w ograniczonej aplikacji.  

-   **Managed Browser**: Zasady programu Managed Browser umożliwia określenie, czy zezwalania lub blokowania managed browser otwieranie listę adresów URL. Typ zasad Managed Browser umożliwia modyfikowanie funkcji aplikacji Intune Managed Browser. Ta aplikacja to przeglądarka sieci Web umożliwiająca zarządzanie akcjami, które użytkownicy mogą wykonywać, w tym witrynami, które mogą odwiedzać, i sposobem otwierania linków do zawartości w przeglądarce. Dowiedz się więcej na następujące tematy:  [Aplikacja programu Intune Managed Browser dla systemu iOS](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) i [Aplikacja programu Intune Managed Browser dla systemu Android](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en).

5)  Na **zasad systemu iOS** lub **zasad systemu Android** , skonfiguruj następujące wartości zgodnie z potrzebami, a następnie wybierz **dalej**. Opcje mogą się różnić w zależności od typu urządzenia, dla którego konfigurujesz zasady.  

|Wartość|Więcej informacji|  
|-----------|----------------------|  
|**Ogranicz zawartość sieci Web wyświetlaną w zarządzanej przeglądarce firmowej**|Włącza wszystkie linki w aplikacji do otwierania w programie Managed Browser. Aplikacja musi być wdrożona na urządzeniach, aby ta opcja działała.|  
|**Nie zezwalaj na kopie zapasowe systemu Android** lub **Nie zezwalaj na kopie zapasowe programu iTunes i usługi iCloud**|Wyłącza wykonywanie kopii zapasowych informacji aplikacji.|  
|**Zezwalaj aplikacji na przesyłanie danych do innych aplikacji**|Określa aplikacje, do których ta aplikacja może przesyłać dane. Użytkownik może nie zezwalać na przesyłanie danych do żadnych aplikacji, aby zezwolić tylko na przesyłanie danych do innych ograniczonych aplikacji lub zezwalać na przesyłanie danych do dowolnych aplikacji.<br /><br /> Aby uniemożliwić przesyłanie dokumentów między aplikacjami zarządzanymi i niezarządzanymi na urządzeniach z systemem iOS, musisz również skonfigurować i wdrożyć zasady zabezpieczeń urządzeń przenośnych, które wyłączają ustawienie **Zezwalaj na niezarządzane dokumenty w innych zarządzanych aplikacjach**.<br /><br /> W przypadku wybrania tylko zezwalać na przesyłanie danych do innych ograniczonych aplikacji przeglądarki Intune PDF i obrazów (jeśli je wdrożono) są używane do otwierania zawartości odpowiednich typów.|  
|**Zezwalaj aplikacji na odbieranie danych z innych aplikacji**|Określa aplikacje, z których ta aplikacja może odbierać dane. Użytkownik może nie zezwalać na przesyłanie danych z żadnych aplikacji, tylko zezwalać na przesyłanie danych z innych ograniczonych aplikacji lub zezwalać na przesyłanie z dowolnych aplikacji.|  
|**Nie zezwalaj na używanie polecenia „Zapisz jako”**|Wyłącza używanie **Zapisz jako** opcji w dowolnej aplikacji, która używa tych zasad.|  
|**Ogranicz wycinanie, kopiowanie i wklejanie w innych aplikacjach**|Określa możliwości korzystania z operacji wycinania, kopiowania i wklejania w ramach aplikacji. Wybierz spośród opcji:<br /><br /> **Zablokowane** — nie zezwalaj na wycinania, kopiowania i wklejanie między tą aplikacją i innymi aplikacjami.<br /><br /> **Aplikacje zarządzane przez zasady** — zezwala wycinania, kopiowania i wklejania w między tylko z tą aplikacją i innymi ograniczonymi aplikacjami.<br /><br /> **Aplikacje zarządzane przez zasady z funkcją wklejania** — umożliwia danych wyciętych lub skopiowanych z tej aplikacji tylko na wklejanie w innych ograniczonych aplikacjach. Umożliwia danych wyciętych lub skopiowanych z dowolnych aplikacji na wklejanie w tej aplikacji.<br /><br /> **Dowolna aplikacja** — Brak ograniczeń wycinania, kopiowania i wklejania do lub z tej aplikacji.|  
|**Wymagaj prostego numeru PIN w celu udzielenia dostępu**|Wymaga od użytkownika wprowadzania numeru PIN określonej w celu korzystania z aplikacji. Użytkownik zostanie poproszony o skonfigurowanie numeru podczas pierwszego uruchomienia aplikacji.|  
|**Liczba prób przed zresetowaniem numeru PIN**|Określa liczbę prób wprowadzenia numeru PIN, które mogą być wykonane, zanim użytkownik musi zresetować numer PIN.|  
|**Wymagaj poświadczeń firmowych w celu udzielenia dostępu**|Wymaga użytkownik wprowadził swoje firmowe informacje logowania zanim uzyska dostęp aplikacji.|  
|**Wymagaj zgodności urządzenia z zasadami firmowymi w celu udzielenia dostępu**|Umożliwia aplikacji można używać tylko wtedy, gdy urządzenie nie jest złamane zabezpieczenia lub odblokowany dostęp.|  
|**Ponownie sprawdź wymagania dostępu po (w minutach)**|Określa okres czasu, po uruchomieniu aplikacji częstotliwość sprawdzania wymagań dostępu aplikacji (w **limit czasu** pól).<br /><br /> W **okres karencji w trybie Offline** pola, jeśli urządzenie jest w trybie offline, określa okres czasu przed częstotliwość sprawdzania wymagań dostępu aplikacji.|  
|**Szyfruj dane aplikacji**|Określa, że wszystkie dane, które są skojarzone z tą aplikacją jest szyfrowane, w tym dane przechowywane zewnętrznie, takich jak dane przechowywane na kartach SD.<br /><br /> **Szyfrowanie dla systemu iOS**<br /><br /> Dla aplikacji, które są skojarzone z zasadami zarządzania aplikacjami mobilnymi programu Configuration Manager dane są szyfrowane nieużywanymi za pomocą szyfrowania na poziomie urządzenia, które są dostarczane przez system operacyjny. Ta funkcja jest włączana za pomocą urządzenia zasad numeru PIN, które muszą być ustawione przez administratora IT. Jeśli numer PIN jest wymagany, dane są szyfrowane zgodnie z ustawieniami zasad zarządzania aplikacjami mobilnymi. Zgodnie z dokumentacją firmy Apple [moduły używane przez system iOS 7 mają certyfikaty FIPS 140-2](http://support.apple.com/en-us/HT202739).<br /><br /> **Szyfrowanie dla systemu Android**<br /><br /> Dla aplikacji, które są skojarzone z zasadami zarządzania aplikacjami mobilnymi programu Configuration Manager szyfrowanie jest obsługiwane przez firmę Microsoft. Dane są szyfrowane synchronicznie podczas operacji we/wy na plikach zgodnie z ustawieniem w zasadach zarządzania aplikacjami mobilnymi. Aplikacje zarządzane w systemie Android używają szyfrowania AES-128 w trybie CBC przy użyciu bibliotek kryptografii platformy. Metoda szyfrowania nie ma certyfikatu FIPS 140-2. Zawartość w magazynie urządzenia są zawsze szyfrowane.|  
    |**Zablokuj przechwytywanie ekranu** (tylko urządzenia z systemem Android)|Określa, że możliwości przechwytywania ekranu urządzenia są blokowane podczas korzystania z tej aplikacji.|  

6)  Na **Managed Browser** wybierz zezwolić na managed browser na otwieranie tylko adresów URL na liście lub managed browser otwieranie adresów URL na liście, a następnie wybierz **dalej**.  
Aby uzyskać więcej informacji, zobacz [Internet zarządzać dostępu przy użyciu zarządzanego zasady przeglądarki](manage-internet-access-using-managed-browser-policies.md).  

7)  Ukończ pracę kreatora.  

 Nowe zasady są wyświetlane w węźle **Zasady zarządzania aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** .  

##  <a name="step-4-associate-the-application-management-policy-with-a-deployment-type"></a>Krok 4: Skojarzyć zasady zarządzania aplikacjami z typu wdrożenia  

 Po utworzeniu typu wdrożenia dla aplikacji, która wymaga zasady zarządzania aplikacjami programu Configuration Manager to rozpoznaje i wyświetla monit o skojarzyć zasad zarządzania aplikacjami. Dla programu Managed Browser należy skojarzyć zasady zarówno ogólne, jak i Managed Browser. Aby uzyskać więcej informacji, zobacz [tworzenia aplikacji](create-applications.md).  

> [!IMPORTANT]  
>  Jeśli aplikacja jest już wdrożona, wdrożenia dla nowego typu wdrożenia nie działa do momentu udostępnienia tego skojarzenia. Skojarzenie można utworzyć za pomocą pozycji **Właściwości** aplikacji na karcie **Zarządzanie aplikacjami** .  

> [!IMPORTANT]  
>  W przypadku urządzeń z systemem operacyjnym wcześniejszym niż iOS 7.1 skojarzone zasady nie są usuwane po odinstalowaniu aplikacji.  
>   
>  Jeśli urządzenie zostanie wyrejestrowane z programu Configuration Manager, zasady nie zostaną usunięte z aplikacji. Aplikacje, które były stosowane zachować ustawienia zasad, nawet po odinstalowaniu i ponownym zainstalowaniu aplikacji.  

##  <a name="step-5-monitor-the-app-deployment"></a>Krok 5. Monitorowanie wdrożenia aplikacji  
 Po utworzeniu i wdrożeniu aplikacji skojarzonej z zasadami zarządzania aplikacjami mobilnymi, można monitorować aplikacji i rozwiązywania konfliktów zasad.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Przegląd** > **wdrożeń**.  

3.  Wybierz wdrożenie, który został utworzony. Następnie na **Home** , wybierz **właściwości**.  

4.  W okienku szczegółów wdrożenia w obszarze **powiązanych obiektów**, wybierz **zasad zarządzania aplikacjami**.  

 Aby uzyskać więcej informacji na temat monitorowania aplikacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

##  <a name="learn-how-policy-conflicts-are-resolved"></a>Dowiedz się, jak są rozwiązywane konflikty zasad  
 Jeśli występuje konflikt zasad zarządzania aplikacjami mobilnymi przy pierwszym wdrożeniu dla użytkownika lub urządzenia, wartość ustawienia powodująca konflikt zostanie usunięty z zasad, które zostały wdrożone dla aplikacji. Następnie aplikacja korzysta z wartości wbudowanej.  

 Jeśli występuje konflikt zasad zarządzania aplikacji mobilnej przy kolejnym wdrożeniu dla aplikacji lub użytkownika, wartość ustawienia powodująca konflikt nie zostanie zaktualizowana w zasadach zarządzania aplikacjami mobilnymi wdrożonej aplikacji, a aplikacja korzysta z istniejącej wartości tego ustawienia.  

 W przypadkach, gdy urządzenie lub użytkownik otrzyma dwie zasady powodujące konflikt, stosuje się następujące działania:  

-   Jeśli na urządzeniu wdrożono jeszcze zasady, istniejące ustawienia zasad nie zostaną zastąpione.  

-   Jeśli do urządzenia już wdrożono nie zasad i zostaną wdrożone dwa ustawienia powodujące konflikt, używane jest domyślne ustawienie, które jest wbudowane w urządzeniu.  

##  <a name="see-a-list-of-available-policy-managed-apps"></a>Lista dostępnych aplikacji zarządzanych przez zasady  
 Lista zasad zarządzanych aplikacji, które są dostępne dla systemu iOS i android, zobacz [partnerów usługi Microsoft Intune aplikacji](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).  

