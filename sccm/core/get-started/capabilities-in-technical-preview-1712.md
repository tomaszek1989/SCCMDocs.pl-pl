---
title: Technical Preview 1712 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1712 programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ce372d6-bd93-4d4d-b612-5303f89c36f0
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 85f0b22b3dc067f6f07816ad36d23a090885f355
ms.sourcegitcommit: ed8b2438ef85c9160741ef61f9171be41dd1ae0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2017
---
# <a name="capabilities-in-technical-preview-1712-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1712 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1712. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. 

Przegląd [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview) przed zainstalowaniem tej wersji technical preview. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
**Known Issues in this Technical Preview:**
-->
**Znane problemy w tej wersji Technical Preview:**
-   **Aktualizacja do nowej wersji zapoznawczej nie powiedzie się, jeśli masz serwer lokacji w trybie pasywnym**. Jeśli masz [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), a następnie przed uaktualnieniem do nowej wersji zapoznawczej musi odinstalować serwer lokacji w trybie pasywnym. Zakończone aktualizacji lokacji można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji**  >  **Serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.
<!--sms489412-->


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="do-not-automatically-upgrade-superseded-applications"></a>Nie uaktualniaj automatycznie zastąpionej aplikacji
<!-- 1351266 -->
Na podstawie Twojej [opinie użytkowników głosu](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/11532669-fix-supercedence-behavior), w tej wersji należy skonfigurować wdrożenie aplikacji, aby automatycznie Uaktualnij wszystkie zastąpione wersje. Teraz podczas tworzenia wdrożenia, na **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**, w obu **dostępne** lub **wymagane**zainstalować cel, można włączyć lub wyłączyć opcję **automatyczne uaktualnianie dowolnej wersji tej aplikacji zastąpione**.


## <a name="install-multiple-applications-in-software-center"></a>Zainstaluj wiele aplikacji w programie Software Center
<!-- 1357126 -->
Jeśli użytkownik końcowy lub pulpitu technika musi zainstalować wiele aplikacji na urządzeniu, Centrum oprogramowania obsługuje teraz instalowanie wielu wybranych aplikacji. Dzięki temu użytkownik będzie bardziej wydajne, nie oczekując na zakończenie przed rozpoczęciem następnego jednej instalacji.

W trybie wielokrotnego wyboru w **aplikacji** kartę, aplikacje, które Centrum oprogramowania pozwala na wybór wielokrotny określić następujące kryteria:
 - Aplikacja jest widoczny dla użytkownika
 - Aplikacja nie jest już zainstalowana.
 - Zatwierdzenie przez administratora nie jest wymagana lub jest już przydzielone
 - Stan aplikacji jest dostępny (na przykład nie jest jeszcze pobierania zawartości)

### <a name="try-it-out"></a>Wypróbuj
**W konsoli programu Configuration Manager:** Wdrożyć wielu aplikacji na potrzeby instalacji, jako dostępne lub wymagane (z terminem w przyszłości) użytkownika lub urządzenia. Nie wymagają zatwierdzenia przez administratora. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).

**W programie Software Center:**
 1. **Aplikacji** kartę powinno spowodować otwarcie domyślnie. 
 2. Aby przejść do trybu wielokrotnego wyboru w widoku listy, kliknij ikonę Nowy ![Ikonę wyboru wielokrotnego, Centrum oprogramowania](media/software-center-multi-select-apps.png) w prawym górnym rogu.
 3. Wybierz co najmniej dwa zainstalowania aplikacji przez kliknięcie pola wyboru po lewej aplikacje na liście.
 4. Kliknij przycisk **zainstalować wybrany** przycisku.

Aplikacje zainstalować normalne, tylko w przedziale czasu.


## <a name="client-based-pxe-responder-service"></a>Usługa klienta środowiska PXE
<!-- 1357148 -->
Żądanie wspólnych dla klientów zapewnia usługi środowiska PXE w zdalnego/biurach oddziałów z infrastrukturą serwera niewielkiego lub żadnego. Rozkład punktu roli obsługuje klienckich systemów operacyjnych, ale nie może być obsługą środowiska PXE ze względu na zależność od usługi wdrażania systemu Windows.

Nowe ustawienia klienta są teraz dostępne w celu umożliwienia obsługi obiektu odpowiadającego w trybie środowiska PXE na klientach programu Configuration Manager. Obraz rozruchowy z włączoną funkcją PXE muszą znajdować się w pamięci podręcznej klienta odpowiadający środowiska PXE.

### <a name="try-it-out"></a>Wypróbuj
Upewnij się, że nie ma żadnych istniejących punktów dystrybucji z włączoną obsługą środowiska PXE lub do innych serwerów PXE w środowisku testowym, które mogą powodować konflikt z obiektu odpowiadającego tej klienta środowiska PXE.

W konsoli programu Configuration Manager:
 1. W **Biblioteka oprogramowania** obszarze roboczym **systemów operacyjnych**, **sekwencje zadań**: Tworzenie sekwencji zadań przy użyciu szablonu niestandardowego.
    1. Kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**, a następnie **Ustaw zmienną sekwencji zadań** kroku. Wprowadź **SMSTSPersistContent** jako zmienną sekwencji zadań, a następnie wprowadź wartość **TRUE**.
    1. Kliknij przycisk **Dodaj**, wybierz pozycję **oprogramowania**, a następnie **Pobierz zawartość pakietu** kroku. Kliknij przycisk gwiazdki złota, a następnie wybierz obraz rozruchowy z włączoną funkcją PXE. Obejmują x x86 i x64 obrazy rozruchowe. Skonfiguruj krok, aby umieścić go w **pamięci podręcznej klienta programu Configuration Manager**.
    1. Kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**, a następnie **Ustaw zmienną sekwencji zadań** kroku. Wprowadź **SMSTSPreserveContent** jako zmienną sekwencji zadań, a następnie wprowadź wartość **TRUE**.
 2. W **administracji** obszarze roboczym **ustawień klienta**: utworzyć zasady niestandardowe ustawienia urządzenia.
    1. Wybierz **ustawienia pamięci podręcznej klienta** grupy.
  1. Ustaw **klienta Włącz program Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość** ustawienie **tak**.
    1. Ustaw **Włączanie obsługi środowiska PXE obiektu odpowiadającego w trybie** ustawienie **tak**.
  1. Dla **Tworzenie certyfikatu z podpisem własnym lub zaimportuj certyfikat klienta PKI** ustawienie, kliknij przycisk **Określ certyfikat**. Wybierz **Importowanie certyfikatu** Jeśli środowisko testowe ma infrastruktury kluczy publicznych, w przeciwnym razie kliknij przycisk **OK** do utworzenia certyfikatu z podpisem własnym. 
    1. Skonfiguruj pozostałe ustawienia zgodnie z potrzebami dla danego środowiska testowego. (Ustawienia domyślne powinny działać, o ile nie ma określonej sieci lub wymagania dotyczące zabezpieczeń.)
 3. Wdrażanie sekwencji zadań i niestandardowe ustawienia klienta w kolekcji docelowej klientów jako obiekty odpowiadające środowiska PXE. Poczekaj, aż zasady do zastosowania i sekwencji zadań do wykonania.
 4. Uruchom innego klienta w tej samej podsieci do rozruchu środowiska PXE i sieci, jak zwykle.

### <a name="known-issues"></a>Znane problemy
 - Edytor sekwencji zadań jest wyświetlana ikona czerwonym błędu dla **Pobierz zawartość pakietu** kroku możesz dodać obraz rozruchowy, kiedy sekwencja zadań pomyślnie zapisuje. Ponownie otworzyć tę sekwencję zadań w edytorze również pokazano, że nie można odnaleźć nieszkodliwe ostrzeżenia, która odwołuje się do obiektów. <!-- sms427542 -->
 - Obraz rozruchowy z kroku pobierania zawartości pakietu nie są wyświetlane w niestandardowej sekwencji zadań na liście odwołań. Również **Dystrybuuj zawartość** akcja jest niedostępna. <!-- sms504017 -->


## <a name="change-in-the-configuration-manager-client-install"></a>Zainstaluj zmiany w kliencie programu Configuration Manager  
W wyniku swoją opinię głos użytkownika [Silverlight nie jest już zainstalowane na klientach automatycznie.](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/10886427-please-do-not-install-silverlight-by-default-in-v) <!--1356195-->
  

## <a name="change-to-the-surface-device-dashboard"></a>Zmień na pulpicie nawigacyjnym powierzchni urządzenia
Powierzchni pulpitu nawigacyjnego przedstawia teraz wersji oprogramowania układowego dla powierzchni urządzeń, a nie wersja systemu operacyjnego. W konsoli przejdź do **monitorowanie** > **urządzeń Surface**. Można wyświetlić następujące elementy:
- procent powierzchni.
- procent powierzchni modeli
- Wersje oprogramowania układowego 5
 <!--1355788-->


## <a name="improvements-to-office-365-client-management-dashboard"></a>Ulepszenia zarządzania usługi Office 365 klienta pulpitu nawigacyjnego 
Pulpit nawigacyjny zarządzania usługi Office 365 klienta zostanie wyświetlona lista odpowiednich urządzeń, po wybraniu sekcje wykresu. W konsoli przejdź do **Biblioteka oprogramowania** >**omówienie** >**zarządzania klienta usługi Office 365**. Pulpit nawigacyjny jest wyświetlana po prawej stronie. Wybranie kryteriów z wykresu zawiera listę urządzeń.  
<!--1357281-->


## <a name="improvements-to-the-configuration-manager-console"></a>Ulepszenia konsoli programu Configuration Manager 
Wprowadzono następujące ulepszenia w konsoli programu Configuration Manager, będące wynikiem swoją opinię głosu użytkownika.

- [Podstawowy użytkownik wyświetla listę urządzeń](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8782225-enable-a-column-for-primary-user): Listy urządzeń w obszarze zasoby i zgodność, urządzeń, jest teraz wyświetlany głównego użytkownika domyślnie. Można również dodać ostatniego zalogowanego użytkownika jako opcjonalne kolumny. <!-- 1357280 -->
- [Zmieniono nazwę kolekcji wyświetlania w istniejących reguł członkostwa w kolekcji](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20125567-fix-the-renaming-of-collections): Jeśli kolekcja jest członkiem innej kolekcji, a jego nazwa zostanie zmieniona, Nowa nazwa jest aktualizowana w ramach reguł członkostwa.<!--1357282--> 


## <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadziliśmy następujące ulepszenia do wdrażania systemów operacyjnych, niektóre z nich wynikały z Twoją opinię głosu użytkownika.
 - [Domyślna przeglądarka dzienników w obrazie rozruchowym](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/19269823-stop-cmtrace-from-asking-us-if-we-want-to-use-it-a): W systemie Windows PE, podczas uruchamiania cmtrace.exe już monit o wybranie, czy to program domyślnej przeglądarki dla plików dziennika. <!-- SMS 500897 -->
 - Pobierz zawartość pakietu krok: Obrazy rozruchowe można teraz dodać do tego kroku sekwencji zadań.


## <a name="windows-10-feedback-hub-app-integration"></a>Integracja aplikacji Centrum opinii 10 systemu Windows

Można przyłączyć opinii w związku z czym duża, że możemy Cię teraz włączenie informacje zwrotne przez [aplikacji Centrum opinii](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) wbudowana w systemie Windows 10. Gdy możesz **dodać nowe opinii**, pamiętaj o wybraniu **zarządzania przedsiębiorstwem** kategorii, a następnie wybierz jedną z następujących podkategorii:
 - Klient programu Configuration Manager
 - Konsola programu Configuration Manager
 - Wdrażanie systemu operacyjnego programu Configuration Manager
 - Serwera programu Configuration Manager

Nadal używać naszych [strony głos użytkownika](http://configurationmanager.uservoice.com/) zagłosować na pomysły dotyczące funkcji nowe w programie Configuration Manager.


<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
