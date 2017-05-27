---
title: "Zarządzanie dostępem do Internetu za pomocą zasad programu managed browser | Dokumentacja firmy Microsoft"
description: "Wdróż Intune Managed Browser zarządzanie i ograniczać dostęp do Internetu."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e25e00c-c9a8-473f-bcb7-ea989f6ca3c5
caps.latest.revision: 6
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: d2dd2c25a2714851ba1e71414cabcef38d3ce014
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-internet-access-using-managed-browser-policies-with-system-center-configuration-manager"></a>Zarządzanie dostępem do Internetu za pomocą zasad programu Managed Browser przy użyciu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W System Center Configuration Manager, można wdrożyć Intune Managed Browser (przeglądanie witryn sieci web aplikacji) i skojarzenia aplikacji z zasady. Zasady programu managed browser skonfigurowanie listy dozwolonych lub zablokowanych ograniczającej zakres witryn sieci Web, które użytkownicy programu managed browser mogą przejść do.  

 Ponieważ jest to aplikacja zarządzana, można również stosować zasady zarządzania aplikacjami mobilnymi, takie jak kontrolowanie użycia wycinania, kopiowania i wkleić. To uniemożliwia Przechwytywanie ekranu i gwarantuje również, że łącza do zawartości otworzyć tylko w innych aplikacjach zarządzanych. Aby uzyskać szczegółowe informacje, zobacz [chronić aplikacje przy użyciu zasad zarządzania aplikacjami mobilnymi](protect-apps-using-mam-policies.md).  

> [!IMPORTANT]  
>  Jeśli użytkownicy sami zainstalują program Managed Browser, nie będzie on zarządzany zgodnie z żadną z wybranych przez Ciebie zasad. W celu zapewnienia, że przeglądarka jest zarządzana przez program Configuration Manager, użytkownicy muszą odinstalować aplikację przed wdrożeniem do nich jako zarządzaną aplikację.  

 Zasady programu Managed Browser można tworzyć dla następujących typów urządzeń:  

-   Urządzenia z systemem Android 4 i nowszym  

-   Urządzenia z systemem iOS 7 i nowszym  

> [!NOTE]  
>  Aby uzyskać więcej informacji oraz aby pobrać aplikację Intune Managed Browser, zobacz [iTunes](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) dla systemu iOS i [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en) dla systemu Android.  

## <a name="create-a-managed-browser-policy"></a>Tworzenie zasad programu Managed Browser  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **zasad zarządzania aplikacjami**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zasady zarządzania aplikacjami**.  

4.  Na **ogólne** strony, wprowadź nazwę i opis zasad, a następnie wybierz **dalej**.  

5.  Na **typ zasad** wybierz platformę, wybierz **Managed Browser** zasad typu, a następnie wybierz **dalej**.  

     Na stronie **Managed Browser** wybierz jedną z następujących opcji:  

    -   **Zezwalaj na managed browser na otwieranie tylko adresów URL wymienionych poniżej**— Określ listę adresów URL, które można otworzyć w przeglądarce zarządzanej.  

    -   **Blokuj managed browser otwieranie adresów URL wymienionych poniżej**— Określ listę adresów URL, których otwieranie zostanie zablokowane managed browser.  

    > [!NOTE]  
    >  W jednej zasadzie programu Managed Browser nie można uwzględnić jednocześnie dozwolonych i zablokowanych adresów URL.  

     Aby uzyskać więcej informacji dotyczących formatów adresów URL można określić, zobacz format adresu URL dla dozwolonych i zablokowanych adresów URL w tym artykule.  

    > [!NOTE]  
    >  Typ zasady ogólne pozwala zmienić funkcjonalność aplikacji, które są wdrażane na naruszały wiersza z firmowych zgodności i zasady zabezpieczeń. Można na przykład ograniczyć operacje wycinania, kopiowania i wklejania w ograniczonej aplikacji. Aby uzyskać więcej informacji o typie ogólnych zasad, zobacz [chronić aplikacje przy użyciu zasad zarządzania aplikacjami mobilnymi](protect-apps-using-mam-policies.md).  

6.  Zakończ pracę kreatora.  

Nowe zasady są wyświetlane w węźle **Zasady zarządzania aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** .  

## <a name="create-a-software-deployment-for-the-managed-browser-app"></a>Tworzenie wdrożenia oprogramowania dla aplikacji programu Managed Browser  
 Po utworzeniu zasad programu Managed Browser możesz utworzyć typ wdrożenia oprogramowania dla aplikacji Managed Browser. Należy skojarzyć obie zasady ogólne i zarządzanych przeglądarki dla aplikacji managed browser.  

 Aby uzyskać więcej informacji, zobacz [tworzenia aplikacji](create-applications.md).  

## <a name="security-and-privacy-for-the-managed-browser"></a>Zabezpieczenia i prywatność programu Managed Browser  

-   Na urządzeniach z systemem iOS nie można otworzyć witryny sieci Web, które wygasły lub niezaufane certyfikaty.  

-   Ustawienia przeglądarki wbudowanej na urządzeniach użytkowników nie są używane w programie Managed Browser. Managed browser nie ma dostępu do tych ustawień.  

-   Po skonfigurowaniu opcji **Wymagaj prostego numeru PIN w celu udzielenia dostępu** lub **Wymagaj poświadczeń firmowych w celu udzielenia dostępu** zasad zarządzania aplikacjami mobilnymi skojarzonych z managed browser, użytkownik może kliknij przycisk Pomoc na stronie uwierzytelniania, a następnie przejdź do witryny — nawet dodane do listy zablokowanych w zasadach programu managed browser.  

-   Program Managed Browser może zablokować dostęp do witryn tylko w przypadku uzyskiwania do nich bezpośredniego dostępu. Dostępu do witryny nie można zablokować, jeśli jest on uzyskiwany za pomocą usług pośrednich (na przykład usługi tłumaczenia).  

## <a name="reference-information"></a>Informacje referencyjne  

###  <a name="url-format-for-allowed-and-blocked-urls"></a>Format adresu URL dla dozwolonych i zablokowanych adresów URL  

Poniższe informacje dotyczą dopuszczalnych formatów i symboli wieloznacznych, których można używać podczas określania adresów URL na listach witryn dozwolonych i zablokowanych.  

-   Symbol wieloznaczny „**\***” może być używany zgodnie z regułami z poniższej listy dozwolonych wzorców.  

-   Upewnij się, że wszystkie adresy URL dodawane do listy będą mieć prefiks **http** lub **https**.  

-   W adresie można określić numery portów. Jeśli nie określisz numeru portu, będą używane następujące wartości:  

    -   Port 80 dla protokołu http  

    -   Port 443 dla protokołu https  

     Symboli wieloznacznych nie można używać w numerze portu, na przykład **http://www.contoso.com:\*** i **http://www.contoso.com: /\***  

-   W poniższej tabeli przedstawiono dozwolone wzorce do użycia podczas określania adresów URL:  

    |Adres URL|Jest zgodny z|Nie jest zgodny z|  
    |---------|-------------|--------------------|  
    |http://www.contoso.com<br /><br /> Zgodny z pojedynczą stroną|www.contoso.com|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> contoso.com/|  
    |http://contoso.com<br /><br /> Zgodny z pojedynczą stroną|contoso.com/|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com|  
    |http://www.contoso.com/*<br /><br /> Zgodny ze wszystkimi adresami URL rozpoczynającymi się od www.contoso.com|www.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com/videos/tvshows|host.contoso.com<br /><br /> host.contoso.com/images|  
    |http://*.contoso.com/\*<br /><br /> Zgodny ze wszystkimi domenami podrzędnymi w domenie contoso.com|developer.contoso.com/resources<br /><br /> news.contoso.com/images<br /><br /> news.contoso.com/videos|contoso.host.com|  
    |http://www.contoso.com/images<br /><br /> Zgodny z pojedynczym folderem|www.contoso.com/images|www.contoso.com/images/dogs|  
    |http://www.contoso.com:80<br /><br /> Zgodny z pojedynczą stroną z użyciem numeru portu|http://www.contoso.com:80||  
    |https://www.contoso.com<br /><br /> Zgodny z pojedynczą, bezpieczną stroną|https://www.contoso.com|http://www.contoso.com|  
    |http://www.contoso.com/images/*<br /><br /> Zgodny z pojedynczym folderem ze wszystkimi podfolderami|www.contoso.com/images/dogs<br /><br /> www.contoso.com/images/cats|www.contoso.com/videos|  

-   Poniżej przedstawiono niektóre niedozwolone wzorce:  

    -   *.com  

    -   *.contoso /\*  

    -   www.contoso.com/*images  

    -   www.contoso.com/*images\*pigs  

    -   www.contoso.com/page*  

    -   Adresy IP  

    -   https://*  

    -   http://*  

    -   http://www.contoso.com:*  

    -   http://www.contoso.com: /*  

> [!NOTE]  
>  *. microsoft.com zawsze jest dozwolone.  

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Jak rozwiązywane są konflikty pozycji list witryn dozwolonych i zablokowanych  
 Jeśli zasady programu Managed Browser są wdrażane na urządzeniu i wystąpi konflikt ustawień, analizowane są listy trybu (zezwalania lub blokowania) oraz adresów URL. W przypadku konfliktu stosowane są następujące rozwiązania:  

-   Jeśli tryby w każdej z zasad są takie same, ale adresy URL są różne, adresy URL nie będzie wymuszane na urządzeniu.  

-   Jeśli tryby w każdej z zasad są różne, ale adresy URL są takie same, adresy URL nie będzie wymuszane na urządzeniu.  

-   Jeśli urządzenie otrzymuje zasady programu Managed Browser po raz pierwszy i wystąpi konflikt dwóch zasad, adresy URL nie są wymuszane na urządzeniu. Aby przejrzeć informacje o konfliktach, użyj węzła **Konflikty zasad** w obszarze roboczym **Zasady**.  

-   Jeśli urządzenie już otrzymało zasady programu Managed Browser, a drugie zasady są wdrażane z ustawieniami powodującymi konflikt, na urządzeniu będą używane ustawienia oryginalne. Aby przejrzeć informacje o konfliktach, użyj węzła **Konflikty zasad** w obszarze roboczym **Zasady**.  

