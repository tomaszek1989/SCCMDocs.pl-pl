---
title: Funkcje w wersji zapoznawczej Technical Preview 1604
titleSuffix: Configuration Manager
description: Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersji 1604.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
author: aczechowski
robots: noindex,nofollow
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 113e22c33e9e8545c382373f3ba093dba3969939
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1604 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersji 1604. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_WindowsVPP"></a> Zarządzanie aplikacjami zakupionymi zbiorczo w Sklepie Windows dla firm  
 [Sklep Windows dla firm](https://www.microsoft.com/en-us/business-store) jest, gdzie można znaleźć i zakupić aplikacje dla Twojej organizacji, pojedynczo lub zbiorczo. Łącząc Sklep do programu Configuration Manager, można zarządzać aplikacjami zakupionymi zbiorczo z poziomu konsoli programu Configuration Manager, na przykład:  

-   Możesz zsynchronizować listę zakupionych aplikacji z programu Configuration Manager  

-   Aplikacje, które są synchronizowane są wyświetlane w konsoli programu Configuration Manager i można wdrażać je tak jak wszystkie inne aplikacje  

-   Można śledzić liczbę licencji są dostępne i liczby są używane w konsoli programu Configuration Manager  

### <a name="try-it-out"></a>Wypróbuj  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>Scenariusz 1. Konfigurowanie Sklepu Windows dla firm synchronizacji  

1.  W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web". Otrzymasz identyfikator klienta, który będzie potrzebny później.  

    1.  W **usługi Active Directory** węzła [ https://manage.windowsazure.com ](https://manage.windowsazure.com), wybierz w usłudze Azure Active Directory, a następnie kliknij przycisk **aplikacji** > **Dodaj**.  

    2.  Kliknij przycisk **Dodaj aplikację moją organizację**.  

    3.  Wprowadź nazwę aplikacji, wybierz pozycję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij strzałkę dalej.  

    4.  Wprowadź ten sam adres URL dla obu **adres URL logowania** i **identyfikator URI aplikacji**.  Adres URL może być dowolny i nie musi prowadzić do faktycznego adresu. Na przykład można wprowadzić **https://&lt;twojadomena\>/sccm**.  

    5.  Ukończ pracę kreatora.  

2.  W usłudze Azure Active Directory Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania.  

    1.  Wyróżnij utworzoną aplikację i kliknij przycisk **Konfiguruj**.  

    2.  W obszarze **klucze**, wybierz czas trwania z listy i kliknij przycisk **zapisać**.  Spowoduje to utworzenie nowego klucza klienta.  Nie opuścić tę stronę, dopóki nie zakończysz dołączania Sklepu Windows dla firm do programu Configuration Manager.  

3.  W Sklepie Windows dla firm należy skonfigurować programu Configuration Manager jako narzędzie do zarządzania magazynami.  

    1.  Otwórz [ https://businessstore.microsoft.com/en-us/managementtools ](https://businessstore.microsoft.com/en-us/managementtools) i zaloguj się w przypadku wyświetlenia monitu.  

    2.  Zaakceptuj warunki użytkowania, jeśli jest to wymagane.  

    3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzie do zarządzania**.  

    4.  W **Wyszukaj narzędzie według nazwy**, wpisz nazwę aplikacji wcześniej utworzony w usłudze AAD, a następnie kliknij przycisk **Dodaj**.  

    5.  Kliknij przycisk **Aktywuj** obok zaimportowanej aplikacji.  

    6.  W **Pokaż aplikacje** kreatora, kliknij przycisk **tak** Jeśli chcesz zezwolić na można kupić aplikacji licencjonowanych w trybie offline.  

4.  Zakup co najmniej jedną aplikację ze Sklepu Windows dla firm.  

5.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, następnie kliknij przycisk **Sklep Windows dla firm**.  

6.  Na **Home** karcie **Utwórz** kliknij przycisk **Dodaj Sklepu Windows dla firm**.  

7.  Dodaj identyfikator dzierżawy, identyfikator klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.  

8.  Gdy wszystko będzie gotowe, zobaczysz skonfigurowane konto **Sklepu Windows dla firm kont** listy w konsoli programu Configuration Manager.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>Scenariusz 2. Tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla firm w trybie offline licencjonowanych aplikacji  

1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Zarządzanie aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji ze sklepu**.  

2.  **Zakupione w Sklepie Windows dla aplikacji biznesowych** lista zawiera listę aplikacji, które zostały zsynchronizowane ze sklepu. Wybierz aplikację, którą chcesz wdrożyć, a następnie na **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji**.  

3.  Tworzenia aplikacji programu Configuration Manager zawierający Sklepu Windows dla aplikacji biznesowych. Można następnie wdrożyć i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.  

##  <a name="BKMK_PFW"></a> Ulepszenia w usłudze Microsoft Passport dla zarządzania pracą  
 Teraz można wdrożyć usługi Passport dla zasad pracy na urządzeniach z systemem Windows 10 przyłączonych do domeny zarządzanych przez klienta programu Configuration Manager.  

##  <a name="bkmk_switchsup"></a> Opcja dla klientów przełączyć się do nowego punktu aktualizacji oprogramowania  
 W wersji 1604 Technical Preview można włączyć opcję dla klientów programu Configuration Manager przełączyć się do nowego punktu aktualizacji oprogramowania, gdy występują problemy z punktem aktualizacji oprogramowania aktywnego. Dla tej opcji musi mieć wiele punktów aktualizacji oprogramowania dostępne w lokacji głównej. Włącz tę opcję w kolekcji urządzeń, a po włączeniu, klienci w kolekcji będzie szukać innego punktu aktualizacji oprogramowania podczas kolejnego skanowania, gdy klient nie może połączyć się z aktywnym punktem aktualizacji oprogramowania. W zależności od ustawienia konfiguracji programu WSUS (klasyfikacje aktualizacji, produktów, itp.) przełączenie na nowy punkt aktualizacji oprogramowania wygeneruje dodatkowy ruch sieciowy. Dlatego opcji tej należy używać wyłącznie wtedy, gdy jest to konieczne.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>Aby włączyć opcję przełączania punktów aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij pozycję **Zasoby i zgodność > Przegląd > Kolekcje urządzeń**.  

2.  Na karcie **Narzędzia główne** w grupie **Kolekcja** kliknij opcję **Powiadomienie klienta**, a następnie kliknij opcję **Przełącz na następny punkt aktualizacji oprogramowania**.  

> [!NOTE]  
>  Ta opcja jest dostępna tylko w lokacjach, które mają wiele punktów aktualizacji oprogramowania.  

##  <a name="bkmk_peercache"></a> Ustawienia klienta do zarządzania ustawieniami pamięci podręcznej klienta i buforowania równorzędnego klienta  
 Wersja Technical preview 1604 wprowadza dwa nowe ustawienia urządzenia klienta, które mają wpływ na korzystanie z pamięci podręcznej klienta. Jednocześnie można użyć pojedynczo, ale są skonfigurowane na tej samej karcie właściwości ustawień klienta i połączyć pomocne w zarządzaniu wdrażaniem zawartości dla klientów w lokalizacjach zdalnych.  

-   Najpierw jest **buforowania równorzędnego klienta**, wbudowane rozwiązanie klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej programu Configuration Manager. Dla klientów równorzędnej pamięci podręcznej na współużytkowanie zawartości muszą należeć do tej samej grupy granic. Buforowanie równorzędne nie zastępuje użycia innych rozwiązań, takich jak BracnchCache, ale działa side-by-side daje więcej opcji rozszerzenia tradycyjnych rozwiązań wdrażania zawartości takie jak punkty dystrybucji.  

     Po wdrożeniu ustawień klienta umożliwiających Buforowanie równorzędne kolekcji elementy członkowskie tej kolekcji może działać jako źródło zawartości elementu równorzędnego dla innych klientów w jego grupę granic.  Ma w pamięci podręcznej klienta, który działa jako element równorzędny zawartości źródłowej zostanie przesyłania listy dostępnej zawartości do swojego punktu zarządzania. Następnie gdy następny klient w tej grupie granic zażąda zawartości, źródła równorzędnej pamięci podręcznej jest oferowany jako potencjalne źródła zawartości oraz wszystkich punktów dystrybucji, które są skonfigurowane szybkie. Klient wybiera losowe źródła zawartości z tej puli połączonych źródeł zawartości. Klienci będą tylko wyszukiwanie zawartości z punktu dystrybucji skonfigurowanego jako wolne w przypadku żadnych punktów dystrybucji szybkiego lub równorzędnej pamięci podręcznej źródeł znajdują się w grupie granic.  

-   Drugie nowe ustawienie umożliwia **Zarządzanie rozmiarem pamięci podręcznej** na klientach. Można ustawić pamięci podręcznej, aby mieć maksymalny rozmiar w megabajtach i maksymalny rozmiar jako procent miejsca na dysku klientów.  Klient wymusza ustawienie, które zostanie osiągnięty jako pierwszy.  

Aby ułatwić zrozumienie użycie buforowania równorzędnego klientów, można wyświetlić **źródła danych klienta** pulpitu nawigacyjnego. W konsoli przejdź do **monitorowanie > Stan klienta > źródła danych klienta**. W tym miejscu można wybrać okres czasu, aby zastosować do pulpitu nawigacyjnego. Następnie na ekranie można wybrać grupę granic lub pakiet, dla którego chcesz wyświetlić informacje. Podczas wyświetlania informacji może wskaźnika myszy powierzchnię, aby zobaczyć więcej szczegółów na temat różnych zawartości lub zasad źródła.  

 Można również użyć nowego raportu **źródła danych klienta — Podsumowanie**, aby wyświetlić podsumowanie dotyczące źródeł danych klienta dla każdej grupy granic.   
**Wymagania dotyczące używania równorzędnej pamięci podręcznej:**  

-   Należy skonfigurować swoją witrynę przy użyciu **konta dostępu do sieci** mający **Pełna kontrola** do folderu pamięci podręcznej na każdym komputerze klienckim. Domyślnie jest to **%windir%\ccmcache**  

-   Klienci mogą przesyłać tylko zawartości przy użyciu równorzędnej pamięci podręcznej, gdy są oni członkami tej samej grupy granic.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>Aby skonfigurować ustawienia klienta buforowania równorzędnego klienta  

1.  Oba ustawienia konfiguruje się na tej samej stronie ustawień klienta. W konsoli programu Configuration Manager, przejdź do **Administracja > Ustawienia klienta**, a następnie ustawienia klienta urządzenia Otwórz obiekt, którego chcesz użyć. Można również zmodyfikować obiekt domyślne ustawienia klienta.  

2.  Wybierz z listy dostępnych ustawień, **ustawienia pamięci podręcznej klienta**.  

3.  Aby zarządzać rozmiarem pamięci podręcznej, należy ustawić **skonfiguruj rozmiar pamięci podręcznej klienta** równa **tak**. Następnie można skonfigurować maksymalny rozmiar buforu dla obu megabajtów i jako procent miejsca na dysku klientów.  

4.  Aby umożliwić klientom udział w buforowania równorzędnego klientów, należy ustawić **klienta Włącz program Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość** równa **tak**. Następnie można skonfigurować porty używane przez klientów, w tym, jeśli będą one HTTP lub HTTPS.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać następujące zadania, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

1.  Zmodyfikuj ustawienia klienta, aby określić nowy rozmiar pamięci podręcznej klienta, a następnie upewnij się, to ustawienie na komputerze klienckim.  

2.  Ustawienia klienta umożliwiają konfigurowanie wielu klientów równorzędnej pamięci podręcznej  

3.  Wdróż zawartość dla klientów, dzięki czemu niektóre większości klientów uzyskiwanie tę zawartość z innego klienta przy użyciu równorzędnej pamięci podręcznej.  Można potwierdzić źródła zawartości, który jest używany, wyświetlając pulpit nawigacyjny.  

    > [!NOTE]  
    >  Aby wykonać to zadanie z wersji zapoznawczej technical preview i pojedynczego punktu dystrybucji, skonfiguruj punkt dystrybucji, który będzie wolny dla lokalizacji sieciowej wszystkich klientów. Następnie dystrybuować zawartość do jednego klienta.  Po klient pobiera zawartość, możesz dystrybuować zawartość do dodatkowych klientów, którzy powinni wyszukać lokalnych równorzędnych do użycia jako źródło zawartości przed skorzystaniem z punktu dystrybucji, który jest uznawane za powolne z lokalizacji klienta.  

##  <a name="bkmk_passport"></a> Obsługa usługi Passport for Work jako dostawcy magazynu KLUCZY  
 System Center Configuration Manager umożliwia integrację z usługą Microsoft Passport for Work, czyli alternatywną metodą logowania korzystającą z usługi Active Directory lub konta usługi Azure Active Directory w celu zastąpienia hasła, karty inteligentnej lub wirtualnej karty inteligentnej.  
Usługa Passport pozwala używać do logowania gestu użytkownika zamiast hasła. Gestem użytkownika może być prosty numer PIN, uwierzytelnianie biometryczne, takie jak Windows Hello lub urządzenie zewnętrzne, np. czytnik linii papilarnych.  

-   Można użyć programu Configuration Manager, aby kontrolować gesty użytkownicy mogą i nie można używać do logowania oraz skonfigurować wymagania dotyczące złożoności kodu PIN.  

-   Certyfikaty uwierzytelniania można przechowywać w usługi Passport for Work dostawca magazynu kluczy (KSP).  

Gdy użytkownik utworzy numer PIN usługi Passport, system Windows wysyła powiadomienia, na którym nasłuchuje program Configuration Manager.  Dzięki temu programu Configuration Manager może szybko dowiedzieć się, użytkowników, którzy mają utworzyć numeru PIN usługi Passport. Następnie program Configuration Manager może również wydać nowe certyfikaty tym użytkownikom, jeśli usługa Passport jest używana jako dostawca magazynu kluczy w profilu certyfikatu.  

##  <a name="bkmk_onpremdha"></a> Zaświadczanie o kondycji urządzenia lokalnego  
 Zaświadczanie o kondycji dla urządzeń z systemem Windows 10 można teraz skonfigurować do komunikacji za pomocą infrastruktury lokalnej.  Administratorzy mogą określić, czy raportowania odbywa się za pośrednictwem chmury lub zasobów lokalnych.  Jeśli **lokalnymi** został wybrany do raportowania o kondycji, a następnie można określić identyfikatora URI dla usługi. Dzięki temu komputery klienckie bez dostępu do Internetu można włączać urządzenia i zarządzać nimi za pomocą zaświadczania o kondycji.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>Włączanie zaświadczania o kondycji urządzeń lokalnych  

1.  W konsoli programu Configuration Manager przejdź do pozycji **Administracja** > **Przegląd** > **Ustawienia klienta**, a następnie ustaw opcję **Użyj lokalnej usługi zaświadczania o kondycji** na **Tak**.  

2.  Określ adres w polu **Adres URL lokalnej usługi zaświadczania o kondycji**, a następnie kliknij przycisk **OK**.  

Aby wypróbować tę funkcję, należy skonfigurować usługę zaświadczania o kondycji lokalnej za pomocą ustawień agenta klienta.  

##  <a name="BKMK_Smart"></a> Ustawienie SmartLock dla urządzeń z systemem Android  
 Nowe ustawienie **Zezwalaj na funkcję SmartLock i innych agentów zaufania** został dodany do **Android i Samsung KNOX** elementu konfiguracji, które umożliwia kontrolowanie funkcji SmartLock na zgodnych urządzeniach z systemem Android. Ta funkcja telefonu, czasami znana jako funkcja agentów zaufania, umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji, np. gdy zostało podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. To ustawienie umożliwia uniemożliwić użytkownikom końcowym Konfigurowanie funkcji SmartLock.  
