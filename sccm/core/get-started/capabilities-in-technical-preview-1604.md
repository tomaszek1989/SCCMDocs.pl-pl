---
title: "Możliwości w Technical Preview 1604 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1604."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 26b0d8ea7b3e841c48945df55f8860394a98a29f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1604 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1604. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_WindowsVPP"></a>Zarządzanie aplikacjami zakupione woluminu w Sklepie Windows dla firm  
 [Sklepu Windows dla firm](https://www.microsoft.com/en-us/business-store) pozwala znaleźć i zakupić aplikacji dla danej organizacji, pojedynczo lub w woluminie. Łącząc sklepu do programu Configuration Manager, można zarządzać zakupione woluminu aplikacji z konsoli programu Configuration Manager, na przykład:  

-   Listy zakupionych aplikacji można synchronizować z programu Configuration Manager  

-   Aplikacje, które są synchronizowane są wyświetlane w konsoli programu Configuration Manager i można wdrożyć takich jak inne aplikacje  

-   Można śledzić liczbę licencji są dostępne i jak wiele są używane w konsoli programu Configuration Manager  

### <a name="try-it-out"></a>Wypróbuj to!  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>Scenariusz 1: Konfigurowanie magazynu systemu Windows dla synchronizacji biznesowe  

1.  W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web". Zapewni to identyfikator klienta, który trzeba będzie później.  

    1.  W **usługi Active Directory** węzła [https://manage.windowsazure.com](https://manage.windowsazure.com), wybierz Azure Active Directory, a następnie kliknij przycisk **aplikacje** > **Dodaj**.  

    2.  Kliknij przycisk **Dodawanie mojej organizacji jest opracowywanie aplikacji**.  

    3.  Wprowadź nazwę aplikacji, wybierz opcję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij strzałkę dalej.  

    4.  Wprowadź ten sam adres URL dla obu **adres URL logowania jednokrotnego** i **URI Identyfikatora aplikacji**.  Adres URL może być dowolny i nie musi rozpoznać adres rzeczywisty. Na przykład, można wprowadzić **https://&lt;domena\>/sccm**.  

    5.  Ukończ pracę kreatora.  

2.  W usłudze Azure Active Directory Utwórz klucz klienta dla narzędzia do zarządzania zarejestrowane.  

    1.  Wyróżnij aplikacji został utworzony, a następnie kliknij przycisk **Konfiguruj**.  

    2.  W obszarze **klucze**, wybierz czas trwania z listy i kliknij przycisk **zapisać**.  Spowoduje to utworzenie nowego klucza klienta.  Nie opuścić tę stronę, dopóki nie został pomyślnie dołączono maszynę wirtualną Sklepu Windows dla firm do programu Configuration Manager.  

3.  W Sklepie Windows dla firmy należy skonfigurować jako narzędzie do zarządzania magazynami programu Configuration Manager.  

    1.  Otwórz [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) i zaloguj się po wyświetleniu monitu.  

    2.  Zaakceptuj warunki użytkowania, jeśli jest to wymagane.  

    3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzia do zarządzania**.  

    4.  W **Wyszukaj według nazwy narzędzie**, wpisz nazwę aplikacji utworzonych w AAD wcześniej, a następnie kliknij przycisk **Dodaj**.  

    5.  Kliknij przycisk **uaktywnienia** obok aplikacji zostały zaimportowane.  

    6.  W **aplikacje Show Offline-Licensed** kreatora, kliknij przycisk **tak** Jeśli chcesz zezwolić offline licencjonowane aplikacje do zakupu.  

4.  Zachęcamy do zakupu co najmniej jednej aplikacji ze Sklepu Windows dla firm.  

5.  W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usług w chmurze**, następnie kliknij przycisk **Sklepu Windows dla firm**.  

6.  Na **Home** w karcie **Utwórz** , kliknij przycisk **Dodaj Sklep Windows dla konta firmowego**.  

7.  Dodaj identyfikator dzierżawcy, identyfikatora klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.  

8.  Gdy wszystko będzie gotowe, zobaczysz konta skonfigurowanego w **Sklep Windows dla konta firmowe** listy w konsoli programu Configuration Manager.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>Scenariusz 2: Tworzenie i wdrażanie aplikacji ze Sklepu Windows dla aplikacji biznesowej w trybie offline licencjonowanego dla programu Configuration Manager  

1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **zarządzania aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji do sklepu**.  

2.  **Zakupione Sklep Windows dla aplikacji biznesowych** lista zawiera listę aplikacji, które zostały zsynchronizowane ze sklepu. Wybierz aplikację, którą chcesz wdrożyć, a następnie w **Home** w karcie **Utwórz** , kliknij przycisk **tworzenie aplikacji**.  

3.  Tworzenia aplikacji programu Configuration Manager zawierający Sklepu Windows dla aplikacji biznesowych. Można następnie wdrażać i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.  

##  <a name="BKMK_PFW"></a>Ulepszenia dla pracy zarządzania Microsoft Passport  
 Teraz można wdrożyć usługi Passport na pracy zasad przyłączonych do domeny systemu Windows 10 urządzeń zarządzanych przez klienta programu Configuration Manager.  

##  <a name="bkmk_switchsup"></a>Opcja dla klientów przełączyć się do nowego punktu aktualizacji oprogramowania  
 1604 Technical Preview można włączyć opcję dla klientów programu Configuration Manager przełączyć się do nowego punktu aktualizacji oprogramowania, gdy występują problemy związane z aktywnym punktem aktualizacji oprogramowania. Ta opcja musi mieć wiele punktów aktualizacji oprogramowania dostępnych w lokacji podstawowej. Włącz tę opcję na kolekcję urządzeń, a po włączeniu, klientów w kolekcji będzie szukał innego punktu aktualizacji oprogramowania w następnym skanowanie, gdy klient nie będzie mógł nawiązywać połączeń z aktywnym punktem aktualizacji oprogramowania. W zależności od ustawienia konfiguracji programu WSUS (klasyfikacje aktualizacji, produktów, itp.) Przełącz do nowego punktu aktualizacji oprogramowania generuje dodatkowe obciążenie sieci. Dlatego opcji tej należy używać wyłącznie wtedy, gdy jest to konieczne.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>Aby włączyć opcję przełączania punktów aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij pozycję **Zasoby i zgodność > Przegląd > Kolekcje urządzeń**.  

2.  Na karcie **Narzędzia główne** w grupie **Kolekcja** kliknij opcję **Powiadomienie klienta**, a następnie kliknij opcję **Przełącz na następny punkt aktualizacji oprogramowania**.  

> [!NOTE]  
>  Ta opcja jest dostępna tylko w witrynach, które mają wiele punktów aktualizacji oprogramowania.  

##  <a name="bkmk_peercache"></a>Ustawienia klienta do zarządzania ustawieniami pamięci podręcznej klienta i klienta Buforowanie równorzędne  
 Wersji Technical preview 1604 wprowadzono dwa nowe ustawienia klienta urządzenia wpływające na korzystanie z pamięci podręcznej klienta. Oba mogą być używane indywidualnie, ale są skonfigurowane na tym samym arkuszu właściwości dla ustawień klienta i połączyć, aby ułatwić Zarządzanie wdrażaniem zawartości do klientów w lokalizacjach zdalnych.  

-   Najpierw jest **klienta Buforowanie równorzędne**, wbudowane rozwiązanie klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej programu Configuration Manager. Buforowanie równorzędne klientom na współużytkowanie zawartości muszą należeć do tej samej grupy granic. Buforowanie równorzędne zastępuje użycie innych rozwiązań, takich jak BracnchCache, lecz zamiast tego działa side-by-side więcej opcji rozszerzania rozwiązań tradycyjny rozmieszczania zawartości, takich jak punkty dystrybucji.  

     Po wdrożeniu ustawień klienta, które umożliwiają Buforowanie równorzędne w kolekcji członków tej kolekcji może działać jako źródła zawartości elementu równorzędnego dla innych klientów w jego grupę granic.  Ma w pamięci podręcznej klienta, który działa jako element równorzędny zawartości źródłowej przedstawi listę dostępnej zawartości do swojego punktu zarządzania. Następnie gdy następny klient w tej grupie granic żąda tej zawartości, peer źródła pamięci podręcznej jest oferowane jako potencjalne źródła zawartości wraz ze wszystkich punktów dystrybucji, które są skonfigurowane jako szybkie. Klient wybiera losowe źródła zawartości z tej puli połączonych źródeł zawartości. Klienci będą tylko przeszukiwania zawartości z punktu dystrybucji skonfigurowanego wolno, gdy nie ma żadnych punktów dystrybucji szybkie lub źródeł pamięci podręcznej elementów równorzędnych znajdują się w grupie granic.  

-   Drugi nowe ustawienie umożliwia **Zarządzanie rozmiar pamięci podręcznej** na komputerach klienckich. Można ustawić w pamięci podręcznej, aby mieć maksymalny rozmiar w megabajtach i maksymalny rozmiar jako procent klientów miejsca na dysku.  Klient wymusza ustawienie, które zostanie osiągnięty.  

Aby ułatwić zrozumienie stosowania elementów równorzędnych w pamięci podręcznej klienta, można wyświetlić **źródeł danych klientów** pulpitu nawigacyjnego. W konsoli, przejdź do **monitorowanie > Stan klienta > źródeł danych klientów**. W tym miejscu można wybrać okres czasu, który ma być zastosowany do pulpitu nawigacyjnego. Następnie na ekranie, można wybrać grupę granic lub pakiet, dla którego chcesz wyświetlić informacje. Podczas wyświetlania informacji, możesz umieść kursor nad powierzchni, aby zobaczyć więcej szczegółów na temat różnych zawartości lub zasad źródeł.  

 Można również użyć nowego raportu **źródeł danych klientów - podsumowania**, aby wyświetlić podsumowanie źródeł danych klienta dla każdej grupy granic.   
**Wymagania dotyczące korzystania z pamięci podręcznej elementu równorzędnego:**  

-   Należy skonfigurować witryny za pomocą **konta dostępu do sieci** z **Pełna kontrola** do folderu pamięci podręcznej na każdym komputerze klienckim. Domyślnie jest to **%windir%\ccmcache**  

-   Klienci tylko mogą przesyłać zawartość przy użyciu Buforowanie równorzędne, gdy są członkami tej samej grupy granic.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>Aby skonfigurować ustawienia klienta pamięci podręcznej klienta równorzędnego  

1.  Oba ustawienia są skonfigurowane na tej samej stronie ustawień klienta. W konsoli programu Configuration Manager, przejdź do **Administracja > Ustawienia klienta**, a następnie ustawienia klienta urządzenia Otwórz obiektu, którego chcesz użyć. Można również zmodyfikować obiekt domyślne ustawienia klienta.  

2.  Wybierz z listy dostępnych ustawień **ustawienia pamięci podręcznej klienta**.  

3.  Aby zarządzać rozmiar pamięci podręcznej, ustaw **skonfigurować rozmiar pamięci podręcznej klienta** równa **tak**. Następnie można skonfigurować maksymalny rozmiar pamięci podręcznej dla obu megabajtów i jako procent klientów miejsca na dysku.  

4.  Aby umożliwić klientom na uczestniczenie w kliencie Buforowanie równorzędne, ustaw **klienta programu Configuration Manager Włącz w pełnej wersji systemu operacyjnego na współużytkowanie zawartości** równa **tak**. Następnie można skonfigurować porty używane przez klientów, włącznie, jeśli będą one protokołu HTTP lub HTTPS.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

1.  Modyfikowanie ustawień klienta, aby określić nowy rozmiar pamięci podręcznej klienta, a następnie potwierdź to ustawienie na komputerze klienckim.  

2.  Umożliwia skonfigurowanie wielu klientów do używania Buforowanie równorzędne ustawienia klienta  

3.  Wdrażania zawartości do klientów, aby niektóre lub większości klientów uzyskać tej zawartości z innego klienta za pomocą Buforowanie równorzędne.  Można potwierdzić źródła zawartości, które jest używane przez wyświetlanie nowego pulpitu nawigacyjnego.  

    > [!NOTE]  
    >  Aby zakończyć to zadanie z technical preview i pojedynczego punktu dystrybucji, konfigurowania punktu dystrybucji wolno dla lokalizacji sieciowej wszystkich klientów. Następnie dystrybuować zawartość do jednego klienta.  Po tym klient pobiera zawartość, można dokonać dystrybucji zawartości do dodatkowych klientów, które należy znaleźć lokalnego równorzędne do użycia jako źródło zawartości przed rozpoczęciem korzystania z punktu dystrybucji, który jest uznawane za powolne z lokalizacji klienta.  

##  <a name="bkmk_passport"></a>Obsługa usługi Passport pracy jako dostawcy magazynu KLUCZY  
 System Center Configuration Manager umożliwia integrację z Microsoft Passport for Work, czyli alternatywna metoda logowania korzystającej z usługi Active Directory lub konto usługi Azure Active Directory zastępuje hasło, kartę inteligentną lub wirtualnej karty inteligentnej.  
Paszport umożliwia używanie gest użytkownika do logowania, zamiast hasła. Gest użytkownika może być prostego numeru PIN, uwierzytelniania biometrycznego, takich jak Windows Hello lub urządzenie zewnętrzne, takie jak czytnik linii papilarnych.  

-   Aby kontrolować, którzy użytkownicy gestów mogą i nie można używać do logowania, a także skonfigurować wymagań dotyczących złożoności, można użyć programu Configuration Manager.  

-   Można przechowywać certyfikatów uwierzytelniania w usłudze Passport for pracy dostawca magazynu kluczy (KSP).  

Gdy użytkownik tworzy numeru PIN usługi Passport, system Windows wysyła powiadomienie, które wykrywa programu Configuration Manager.  Umożliwia Configuration Manager, aby szybko zostaną powiadomieni o użytkownikach, którzy utworzono numeru PIN usługi Passport. Następnie program Configuration Manager może również wydać nowe certyfikaty tym użytkownikom, jeśli usługa Passport jest używana jako dostawca magazynu kluczy w profilu certyfikatu.  

##  <a name="bkmk_onpremdha"></a>Poświadczenie zdrowia urządzeń lokalnych  
 Zaświadczanie kondycji dla urządzeń z systemem Windows 10 można teraz skonfigurowane do komunikacji przy użyciu infrastruktury lokalnej.  Administratorzy mogą określić, czy raportowania odbywa się za pośrednictwem chmury lub lokalnych zasobów.  Jeśli **lokalnego** został wybrany do raportowania zaświadczania kondycji, a następnie można określić identyfikatora URI usługi. Dzięki temu klient komputerów bez dostępu do Internetu enable a zarządzanie urządzeniami za pomocą zaświadczania kondycji.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>Włącz zaświadczania kondycji dla urządzeń lokalnych  

1.  W konsoli programu Configuration Manager przejdź do pozycji **Administracja** > **Przegląd** > **Ustawienia klienta**, a następnie ustaw opcję **Użyj lokalnej usługi zaświadczania o kondycji** na **Tak**.  

2.  Określ adres w polu **Adres URL lokalnej usługi zaświadczania o kondycji**, a następnie kliknij przycisk **OK**.  

Spróbuj go, należy skonfigurować usługi zaświadczania kondycji lokalnie przy użyciu ustawień agenta klienta.  

##  <a name="BKMK_Smart"></a>Ustawienie SmartLock dla urządzeń z systemem Android  
 Nowe ustawienie **SmartLock Zezwalaj i inne zaufane agentów** został dodany do **Android i Samsung KNOX** element konfiguracji, który umożliwia sterowanie funkcji SmartLock na urządzeniach zgodnych. Ta funkcja telefonu, czasami znana jako funkcja agentów zaufania, umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji, np. gdy zostało podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. To ustawienie umożliwia uniemożliwić użytkownikom końcowym Konfigurowanie SmartLock.  

