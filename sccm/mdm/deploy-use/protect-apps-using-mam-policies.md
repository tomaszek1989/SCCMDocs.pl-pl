---
title: "Ochrona aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi | Dokumentacja firmy Microsoft"
description: "Modyfikowanie funkcji wdrażanych aplikacji wdrażanych, spełniają firmowych zgodności i zasady zabezpieczeń."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28115475-e563-4e16-bf30-f4c9fe704754
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 50c137f159b0ef631f7173b8eec190182ce41cee
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="protect-apps-using-mobile-application-management-policies-in-system-center-configuration-manager"></a>Ochrona aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zasady zarządzania aplikacjami programu System Center Configuration Manager umożliwiają modyfikowanie funkcji wdrażanych aplikacji, co pomaga dostosować je zgodnie z firmy zasad dotyczących zgodności i zabezpieczeń. Na przykład można ograniczyć wycinania, kopiowania i operacji wklejania w ograniczonej aplikacji lub skonfigurować aplikację tak, aby otworzyć wszystkie adresy URL w programie managed browser. Zasady zarządzania aplikacjami obsługują:  

-   Urządzenia z systemem Android 4 i nowszym  

-   Urządzenia z systemem iOS 7 i nowszym  

Umożliwia także zasady zarządzania aplikacjami mobilnymi można chronić aplikacje na urządzeniach, które nie są zarządzane przez usługę Intune. Przy użyciu tej nowej możliwości, możesz zastosować zasady zarządzania aplikacjami mobilnymi do aplikacji łączących się z usługami Office 365. To nie jest obsługiwana w przypadku aplikacji łączących się do lokalnego programu Exchange lub SharePoint.  

Aby użyć tej nowej możliwości, należy korzystać z portalu Azure w wersji zapoznawczej. W poniższych tematach znajdują się informacje ułatwiające rozpoczęcie pracy:  
-   [Rozpoczynanie pracy z zasadami zarządzania aplikacjami mobilnymi w portalu Azure](https://technet.microsoft.com/library/mt627830.aspx)  
-   [Tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi przy użyciu usługi Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx)  

 Nie można wdrożyć zasady zarządzania aplikacjami bezpośrednio, czy z elementami konfiguracji i linii bazowych w programie Configuration Manager. Należy je skojarzyć z typem wdrożenia aplikacji, który ma zostać ograniczony. Po wdrożeniu i zainstalowaniu na urządzeniach typ wdrożenia aplikacji, ustawień, które określisz zaczynają obowiązywać.  

Aby zastosować ograniczenia dla aplikacji, aplikacja musi mieć Microsoft Intune App Software Development Kit (SDK). Istnieją dwie metody uzyskania tego typu aplikacji:  

-   **Użycie aplikacji zarządzanej przez zasady** (Android i iOS): Te aplikacje mają wbudowany zestaw SDK aplikacji. Aby dodać ten typ aplikacji, wystarczy podać link do wybranej aplikacji w sklepie z aplikacjami, takim jak iTunes lub Google Play. Żadne dalsze przetwarzanie nie jest wymagane w przypadku tego typu aplikacji. Listę aplikacji zarządzanych przez zasady, które są dostępne dla urządzeń z systemami iOS i Android, zamieszczono w artykule [Aplikacje zarządzane przy użyciu zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx).  

-   **Użycie aplikacji "zawinięty"** (Android i iOS): Te aplikacje pakietach do nich zestawu SDK aplikacji przy użyciu **Microsoft Intune App Wrapping Tool**. To narzędzie jest zwykle używane do przetwarzania aplikacji firmowych utworzonych wewnętrznie. Nie można go używać do przetwarzania aplikacji, które zostały pobrane ze sklepu z aplikacjami. Zobacz następujące artykuły, aby uzyskać więcej informacji:
    - [Przygotowanie aplikacji systemu iOS do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/dn878028.aspx)

    - [Przygotowanie aplikacji systemu Android do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/mt147413.aspx)  

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Tworzenie i wdrażanie aplikacji podlegającej zasadom zarządzania aplikacjami mobilnymi  

##  <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>Krok 1. Uzyskiwanie linku do aplikacji zarządzanej przez zasady lub tworzenie opakowanej aplikacji  

-   **Aby uzyskać link do zasad aplikacji zarządzanej**: Ze sklepu z aplikacjami Znajdź i zanotuj adres URL aplikacji zarządzanej przez zasady, którą chcesz wdrożyć.  

     Na przykład adres URL aplikacji Microsoft Word dla urządzenia iPad to **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**  

-   **Aby utworzyć opakowaną aplikację**: Użyj informacji podanych w tematach [przygotowanie aplikacji systemu iOS do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/dn878028.aspx) i [przygotowanie aplikacji systemu Android do zarządzania aplikacjami mobilnymi za pomocą narzędzia zawijania aplikacji usługi Intune Microsoft](https://technet.microsoft.com/library/mt147413.aspx) Aby utworzyć opakowaną aplikację.  

     Narzędzie tworzy przetworzoną aplikację i skojarzony plik manifestu. Pliki te są używane podczas tworzenia aplikacji programu Configuration Manager, który zawiera aplikację.  

##  <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>Krok 2. Tworzenie aplikacji programu Configuration Manager, która zawiera aplikację  
 Procedura tworzenia aplikacji programu Configuration Manager zależy od tego, czy używana aplikacja zarządzana przez zasady (link zewnętrzny) lub aplikacji, która została utworzona przy użyciu programu Microsoft Intune App Wrapping Tool dla systemu iOS (pakietu aplikacji systemu iOS). Użyj jednej z poniższych procedur do tworzenia aplikacji programu Configuration Manager.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  W **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji** otworzyć **tworzenie aplikacji** kreatora.  

4.  Na stronie **Ogólne** wybierz opcję **Automatycznie wykryj informacje o tej aplikacji z plików instalacyjnych**.  

5.  Z listy rozwijanej **Typ** wybierz pozycję **Pakiet aplikacji dla systemu iOS (\*plik ipa)**.  

6.  Wybierz **Przeglądaj** aby wybrać pakiet aplikacji, które chcesz zaimportować, a następnie wybierz pozycję **dalej**.  

7.  Na stronie **Informacje ogólne** wprowadź opis oraz informacje o kategorii, które będą widoczne dla użytkowników w portalu firmy.  

8.  Ukończ pracę kreatora.  

 Nowa aplikacja jest wyświetlana w węźle **Aplikacje** w obszarze roboczym **Biblioteka oprogramowania** .  

### <a name="create-an-application-that-contains-a-link-to-a-policy-managed-app"></a>Tworzenie aplikacji zawierającej link do aplikacji zarządzanej przez zasady  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  W **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji** otworzyć **tworzenie aplikacji** kreatora.  

4.  Na stronie **Ogólne** wybierz opcję **Automatycznie wykryj informacje o tej aplikacji z plików instalacyjnych**.  

5.  Z listy rozwijanej **Typ** wybierz jedną z następujących pozycji:  

    -   Dla systemu iOS: **Pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**  

    -   Dla systemu Android: **Pakiet aplikacji dla systemu Android w witrynie Google Play**  

6.  Wprowadź adres URL aplikacji (z kroku 1), a następnie wybierz pozycję **dalej**.  

7.  Na stronie **Informacje ogólne** wprowadź opis oraz informacje o kategorii, które będą widoczne dla użytkowników w portalu firmy.  

8.  Ukończ pracę kreatora.  

 Nowa aplikacja jest wyświetlana w węźle **Aplikacje** w obszarze roboczym **Biblioteka oprogramowania** .  

##  <a name="step-3-create-an-application-management-policy"></a>Krok 3. Tworzenie zasad zarządzania aplikacjami  
 Następnie utwórz zasady zarządzania aplikacjami, które skojarzysz z aplikacją. Możesz utworzyć zasady ogólne lub zasady zarządzanej przeglądarki.  

1)  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **zasad zarządzania aplikacjami**.  

2)  W **Home** karcie **Utwórz** grupy, wybierz **Utwórz zasady zarządzania aplikacjami**.  

3)  Na **ogólne** strony, wprowadź nazwę i opis zasad, a następnie wybierz **dalej**.  

4)  Na **typ zasad** strony, wybierz platformę i typ zasad dla tej zasady, a następnie wybierz **dalej**. Dostępne są następujące typy zasad:  

-   **Ogólne**: Typ zasad ogólny umożliwia modyfikowanie funkcji wdrażanych aplikacji, co pomaga dostosować je zgodnie z firmowych zasad dotyczących zgodności i zabezpieczeń. Można na przykład ograniczyć operacje wycinania, kopiowania i wklejania w ograniczonej aplikacji.  

-   **Managed Browser**: Zasady programu Managed Browser umożliwia podjęcie decyzji o Zezwalaj lub Blokuj w zarządzanej przeglądarce Otwieranie listy adresów URL. Typ zasad Managed Browser umożliwia modyfikowanie funkcji aplikacji Intune Managed Browser. Ta aplikacja to przeglądarka sieci Web umożliwiająca zarządzanie akcjami, które użytkownicy mogą wykonywać, w tym witrynami, które mogą odwiedzać, i sposobem otwierania linków do zawartości w przeglądarce. Dowiedz się więcej na następujące tematy:  [Aplikacja programu Intune Managed Browser dla systemu iOS](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) i [Aplikacja programu Intune Managed Browser dla systemu Android](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en).

5)  Na **zasady systemu iOS** lub **zasad systemu Android** strony, skonfiguruj następujące wartości zgodnie z wymaganiami, a następnie wybierz **dalej**. Opcje mogą się różnić w zależności od typu urządzenia, dla którego konfigurujesz zasady.  

|Wartość|Więcej informacji|  
|-----------|----------------------|  
|**Ogranicz zawartość sieci Web wyświetlaną w zarządzanej przeglądarce firmowej**|Włącza wszystkie linki w aplikacji, aby otworzyć w programie Managed Browser. Aplikacja musi być wdrożona na urządzeniach, aby ta opcja działała.|  
|**Nie zezwalaj na kopie zapasowe systemu Android** lub **Nie zezwalaj na kopie zapasowe programu iTunes i usługi iCloud**|Wyłącza wykonywanie kopii zapasowych informacji aplikacji.|  
|**Zezwalaj aplikacji na przesyłanie danych do innych aplikacji**|Określa aplikacje, do których ta aplikacja może przesyłać dane. Możesz nie zezwalać na przesyłanie danych do żadnych aplikacji, aby zezwolić tylko na transfer do innych ograniczonych aplikacji lub zezwalać na transfer do żadnej aplikacji.<br /><br /> Aby uniemożliwić przesyłanie dokumentów między aplikacjami zarządzanymi i niezarządzanymi na urządzeniach z systemem iOS, musisz również skonfigurować i wdrożyć zasady zabezpieczeń urządzeń przenośnych, które wyłączają ustawienie **Zezwalaj na niezarządzane dokumenty w innych zarządzanych aplikacjach**.<br /><br /> Jeśli wybierzesz opcję Zezwalaj tylko na transfer do innych ograniczonych aplikacji, przeglądarki Intune PDF i obrazów (jeśli je wdrożono) są używane do otwierania zawartości odpowiednich typów.|  
|**Zezwalaj aplikacji na odbieranie danych z innych aplikacji**|Określa aplikacje, z których ta aplikacja może odbierać dane. Możesz nie zezwalać na przesyłanie danych z żadnych aplikacji, aby zezwolić tylko na transfer z innych ograniczonych aplikacji lub zezwalać na przesyłanie z dowolnych aplikacji.|  
|**Nie zezwalaj na używanie polecenia „Zapisz jako”**|Wyłącza używanie **Zapisz jako** we wszystkich aplikacjach korzystających z tych zasad.|  
|**Ogranicz wycinanie, kopiowanie i wklejanie w innych aplikacjach**|Określa możliwości korzystania z operacji wycinania, kopiowania i wklejania w ramach aplikacji. Wybierz spośród opcji:<br /><br /> **Zablokowane** — nie zezwalaj na wycinanie, kopiowanie i wklejanie między tą aplikacją i innymi aplikacjami.<br /><br /> **Aplikacje zarządzane przez zasady** — umożliwia wycinanie, kopiowanie i wklejanie działań między tylko tą aplikacją i innymi ograniczonymi aplikacjami.<br /><br /> **Aplikacje zarządzane przez zasady z funkcją wklejania** — umożliwia danych wyciętych lub skopiowanych z tej aplikacji tylko w innych ograniczonych aplikacjach. Umożliwia danych wyciętych lub skopiowanych z dowolnych aplikacji w tej aplikacji.<br /><br /> **Dowolna aplikacja** — Brak ograniczeń wycinania, kopiowania i wklejania w do lub z tej aplikacji.|  
|**Wymagaj prostego numeru PIN w celu udzielenia dostępu**|Wymaga od użytkownika podania numeru PIN, które określają, aby użyć tej aplikacji. Użytkownik jest proszony o skonfigurowanie tego numeru przy pierwszym uruchomieniu uruchomią oni aplikację.|  
|**Liczba prób przed zresetowaniem numeru PIN**|Określa liczbę prób wprowadzenia numeru PIN, które można wykonać, zanim użytkownik musi zresetować numer PIN.|  
|**Wymagaj poświadczeń firmowych w celu udzielenia dostępu**|Wymaga się, że użytkownik musi wprowadzić swoje firmowe informacje logowania przed uzyskaniem dostępu do aplikacji.|  
|**Wymagaj zgodności urządzenia z zasadami firmowymi w celu udzielenia dostępu**|Umożliwia aplikacji można używać tylko wtedy, gdy urządzenie ma zdjęte zabezpieczenia lub odblokowany dostęp.|  
|**Ponownie sprawdź wymagania dostępu po (w minutach)**|Określa okres czasu przed sprawdzeniem wymagań dostępu aplikacji po uruchomieniu aplikacji (w **limitu czasu** pól).<br /><br /> W **okres karencji w trybie Offline** pole, jeśli urządzenie jest w trybie offline, określa okres czasu przed sprawdzeniem wymagań dostępu aplikacji.|  
|**Szyfruj dane aplikacji**|Określa, że wszystkie dane, które jest skojarzone z tą aplikacją jest szyfrowane, w tym dane przechowywane zewnętrznie, takich jak dane przechowywane na kartach SD.<br /><br /> **Szyfrowanie dla systemu iOS**<br /><br /> W przypadku aplikacji, które są skojarzone z zasadami zarządzania aplikacjami mobilnymi programu Configuration Manager dane są szyfrowane w stanie spoczynku za pomocą szyfrowania na poziomie urządzenia, które są dostarczane przez system operacyjny. Ta opcja jest włączona za pomocą zasad numeru PIN urządzenia musi być ustawiony przez administratora IT. Jeśli numer PIN jest wymagany, dane są szyfrowane zgodnie z ustawieniami w zasadach zarządzania aplikacjami mobilnymi. Zgodnie z dokumentacją firmy Apple, [modułów, które są używane przez system iOS 7 są FIPS 140-2 certyfikowanych](http://support.apple.com/en-us/HT202739).<br /><br /> **Szyfrowanie dla systemu Android**<br /><br /> W przypadku aplikacji, które są skojarzone z zasadami zarządzania aplikacjami mobilnymi programu Configuration Manager szyfrowanie jest obsługiwane przez firmę Microsoft. Dane są szyfrowane synchronicznie podczas operacji we/wy na plikach zgodnie z ustawieniem w zasadach zarządzania aplikacjami mobilnymi. Aplikacje zarządzane w systemie Android używają szyfrowania AES-128 w trybie CBC przy użyciu bibliotek kryptografii platformy. Metoda szyfrowania nie ma certyfikatu FIPS 140-2. Zawartość w magazynie urządzenia są zawsze szyfrowane.|  
    |**Zablokuj przechwytywanie ekranu** (tylko urządzenia z systemem Android)|Określa, że możliwości przechwytywania ekranu urządzenia są blokowane podczas korzystania z tej aplikacji.|  

6)  Na **Managed Browser** wybierz zezwolić managed browser na otwieranie tylko adresów URL na liście lub Blokuj w zarządzanej przeglądarce otwieranie adresów URL na liście, a następnie wybierz pozycję **dalej**.  
Aby uzyskać więcej informacji, zobacz [Zarządzanie Internetu dostępu za pomocą zasad programu managed browser](manage-internet-access-using-managed-browser-policies.md).  

7)  Ukończ pracę kreatora.  

 Nowe zasady są wyświetlane w węźle **Zasady zarządzania aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** .  

##  <a name="step-4-associate-the-application-management-policy-with-a-deployment-type"></a>Krok 4. Kojarzenie zasad zarządzania aplikacjami z typem wdrożenia  

 Po utworzeniu typu wdrożenia dla aplikacji wymagającej zasad zarządzania aplikacjami programu Configuration Manager rozpoznaje to i wyświetli monit o skojarzenie zasad zarządzania aplikacjami. Dla programu Managed Browser konieczne skojarzenie zasad ogólnych oraz Managed Browser. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](create-applications.md).  

> [!IMPORTANT]  
>  Jeśli aplikacja została już wdrożona, wdrożenie dla nowego typu wdrożenia nie działa do momentu tego skojarzenia. Skojarzenie można utworzyć za pomocą pozycji **Właściwości** aplikacji na karcie **Zarządzanie aplikacjami** .  

> [!IMPORTANT]  
>  W przypadku urządzeń z systemem operacyjnym wcześniejszym niż iOS 7.1 skojarzone zasady nie zostaną usunięte po odinstalowaniu aplikacji.  
>   
>  Jeśli urządzenie zostanie wyrejestrowane z programu Configuration Manager, zasady nie zostaną usunięte z aplikacji. Aplikacje, do których zastosowano zasady zachowują ustawienia zasad, nawet po odinstalowaniu i ponownym zainstalowaniu aplikacji.  

##  <a name="step-5-monitor-the-app-deployment"></a>Krok 5. Monitorowanie wdrożenia aplikacji  
 Po utworzeniu i wdrożeniu aplikacji skojarzonej z zasadami zarządzania aplikacjami mobilnymi można monitorować aplikację i rozwiązywać konflikty zasad.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **omówienie** > **wdrożeń**.  

3.  Wybierz wdrożenie, który został utworzony. Następnie na **Home** , wybierz pozycję **właściwości**.  

4.  W okienku szczegółów wdrożenia w obszarze **powiązanych obiektów**, wybierz **zasad zarządzania aplikacjami**.  

 Aby uzyskać więcej informacji na temat monitorowania aplikacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

##  <a name="learn-how-policy-conflicts-are-resolved"></a>Dowiedz się, jak są rozwiązywane konflikty zasad  
 Jeśli wystąpi konflikt zasad zarządzania aplikacjami mobilnymi przy pierwszym wdrożeniu dla użytkownika lub urządzenia, wartość ustawienia powodująca konflikt jest usuwany z zasad, które zostało wdrożone w aplikacji. Następnie aplikacja korzysta z wartości wbudowanej.  

 Jeśli wystąpi konflikt zasad zarządzania aplikacjami mobilnymi przy kolejnym wdrożeniu dla aplikacji lub użytkownika, wartość ustawienia powodująca konflikt nie zostanie zaktualizowana na zasady zarządzania aplikacjami mobilnymi, które zostało wdrożone w aplikacji, a aplikacja korzysta z istniejącej wartości tego ustawienia.  

 W przypadkach, gdy urządzenie lub użytkownik otrzyma dwie zasady powodujące konflikt, stosuje się następujące działania:  

-   Jeśli na urządzeniu wdrożono jeszcze zasady, istniejące ustawienia zasad nie zostaną zastąpione.  

-   Jeśli żadne zasady nie zostało już wdrożone na urządzeniu, a następnie są wdrażane dwa ustawienia powodujące konflikt, używane jest domyślne ustawienie, które są wbudowane w urządzeniu.  

##  <a name="see-a-list-of-available-policy-managed-apps"></a>Lista dostępnych aplikacji zarządzanych zasady  
 Lista zasad zarządzane aplikacje, które są dostępne dla urządzeń iOS i Android, zobacz [partnerów aplikacji Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-partners).  
