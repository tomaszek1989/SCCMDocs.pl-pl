---
title: Technical Preview 1801 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1801 programu System Center Configuration Manager."
ms.custom: na
ms.date: 01/19/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a352ae0-355f-4fcf-b863-fb0654f51c52
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f4be3ffe817392bf8fefdcf4e481c739778025ff
ms.sourcegitcommit: db9978135d7a6455d83dbe4a5175af2bdeaeafd8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="capabilities-in-technical-preview-1801-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1801 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1801. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. 

Przegląd [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview) przed zainstalowaniem tej wersji technical preview. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


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
<!--sms 489412-->


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the tasks. Then send **Feedback** from the **Home** tab of the ribbon letting us know how it worked.
 -  Task 1
 -  Task 2              
-->



## <a name="create-phased-deployments"></a>Tworzenie wdrożenia etapowego
<!-- 1357405 -->
Wdrożenia etapowego zautomatyzować skoordynowane, Sekwencyjna wdrażanie oprogramowania bez tworzenia wielu wdrożeń. W tej wersji Technical Preview można wykonać kreatora etapowego wdrażania dla sekwencji zadań w konsoli administracyjnej. Wdrożenia nie są tworzone. 

### <a name="try-it-out"></a>Wypróbuj  
  Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.
 
**Utwórz etapowego wdrażania dla sekwencji zadań** </br>
1. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Kliknij prawym przyciskiem myszy na istniejącej sekwencji zadań i wybierz **tworzenia wdrożenia stopniowo**. 
3. Na **ogólne** karcie, określ etapowego wdrażania nazwę, opis (opcjonalnie) i wybierz **automatycznie utworzyć domyślne pilotażowy i produkcyjny fazy**. 
4. Wypełnij **pilotażowe kolekcji** i **kolekcji dla środowiska produkcyjnego** pola. Wybierz **dalej**.
5. Na **ustawienia** , wybierz jedną z opcji dla każdego ustawienia planowania i wybierz **dalej** po zakończeniu. 
6. Na **fazy** karcie, Edytuj poszczególnych faz, jeśli to konieczne, a następnie kliknij przycisk **dalej**.
7. Potwierdź wybrane opcje na **Podsumowanie** karcie, a następnie kliknij przycisk **dalej** aby kontynuować.

## <a name="co-management-reporting"></a>Raportowanie zarządzania wspólnej
<!-- 1356648 -->
Jeśli używasz [zarządzania wspólnej](/sccm/core/clients/manage/co-management-overview) możliwości, można wyświetlać pulpit nawigacyjny z informacjami o wspólnej zarządzania w środowisku. W konsoli programu Configuration Manager, przejdź do **monitorowanie** obszaru roboczego, rozwiń węzeł **gotowości do uaktualnienia**i wybierz **zarządzania wspólnej** pulpitu nawigacyjnego. Pulpit nawigacyjny zawiera następujące Kafelki:
- **Urządzenia zarządzane wspólnie**: odsetek urządzeń w środowisku, w którym są włączone do wspólnego zarządzania
- **System operacyjny dystrybucji**: podział systemów operacyjnych (OS) w wersji. Ten wykres korzysta z następujących grup:
   - Windows 7 & 8.x
   - Niższe niż 1709 systemu Windows 10
   - Windows 10 1709 i powyżej.
  > [!NOTE] 
  > Windows 10, wersja 1709 i nowsze, jest wymagane w przypadku zarządzania wspólnej
- **Stan zarządzania wspólnej**: podział urządzenia powodzenie lub Niepowodzenie w ramach następujących kategorii:
   - Sukces, hybrydowego Joined usługi Azure AD
   - Sukces, usługi Azure AD dołączony
   - Wystąpił błąd: Automatyczna rejestracja nie powiodła się
- **Przejście obciążenia**: wykres słupkowy przedstawiający liczbę urządzeń, których należy dokonać usłudze Microsoft Intune dla trzech obciążeń dostępne: 
   - Zasady zgodności
   - Dostęp do zasobów
   - Windows Update dla firm

### <a name="prerequisites"></a>Wymagania wstępne
- Komputer, na którym uruchomiona jest konsola programu Configuration Manager wymaga programu Internet Explorer 9 lub nowszy.



## <a name="improvements-to-automatic-deployment-rule-evaluation-schedule"></a>Ulepszenia dotyczące harmonogramu oceny reguły wdrażania automatycznego
<!-- 1357133 -->
Na podstawie Twojej [opinie użytkowników głosu](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8819518-software-update-patch-tuesday-scheduling), Szacowanie reguły (ADR) automatycznego wdrażania do przesunięcia od dnia podstawowa można teraz harmonogramu. Na przykład przesunięcie dwa dni po drugi wtorek miesiąca ocenia reguły w czwartek. 

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło. <br/>

**Utwórz harmonogram niestandardowy, który oblicza i ADR przesunięcie od dnia podstawowa** </br>
1.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **aktualizacji oprogramowania**i wybierz **reguły wdrażania automatycznego**.
2. Kliknij prawym przyciskiem myszy **reguły wdrażania automatycznego** i wybierz polecenie **Utwórz regułę wdrażania automatycznego**. 
3. Postępuj zgodnie z monitami, aby ukończyć **ogólne**, **ustawienia wdrażania**, i **aktualizacji oprogramowania** karty. 
4. Na **harmonogram oceny** wybierz opcję **uruchomić regułę, zgodnie z harmonogramem** i **Dostosuj**.
5. Harmonogram niestandardowy, wybierz **miesięczne** i umieszcza w ciągu dnia podstawowa, takich jak drugi wtorek. 
6. Sprawdź **przesunięcie (w dniach)** i liczbę dni, następnie przesunięcia **OK** po zakończeniu.  
7. Wykonaj pozostałe **wdrożenia Kreatora tworzenia reguły automatycznego**. 



## <a name="reassign-distribution-point"></a>Ponowne przypisanie punktu dystrybucji
<!-- 1306937 -->
Wielu klientów mają duże infrastruktury programu Configuration Manager i ograniczają lokacjach głównych lub dodatkowych, aby uprościć ich środowiska. Nadal należy zachować punktów dystrybucji w oddziałach, aby obsługiwać zawartość dla klientów zarządzanych. Te punkty dystrybucji zawierają często wielu terabajtów lub więcej zawartości. Ta zawartość jest kosztowna pod względem przepustowości czasu i sieci do dystrybucji na tych serwerach zdalnych. 

Ta funkcja umożliwia ponowne przypisanie punktu dystrybucji do innej lokacji głównej bez dystrybucję zawartości. Aktualizuje przypisania systemu lokacji podczas utrwalanie całej zawartości na serwerze. Jeśli do ponownego przypisania wielu punktów dystrybucji, należy najpierw wykonać tej akcji na pojedynczego punktu dystrybucji, a następnie kontynuować dodatkowych serwerów w czasie.

> [!IMPORTANT]
> Serwer systemu lokacji może zawierać tylko rolę punktu dystrybucji. Jeśli serwer systemu lokacji obsługuje innej roli serwera programu Configuration Manager, takie jak punkt migracji stanu nie może ponownie przypisać punktu dystrybucji. Nie można ponownie przypisać punkt dystrybucji w chmurze. 

Ta opcja nie działa w tej wersji z powodu limitu Technical Preview z jednej lokacji głównej. Rozważmy scenariusz, a następnie wyślij **opinii** z **Home** karty wstążki, dotyczące możliwości tej akcji.
1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, a następnie wybierz **punktów dystrybucji** węzła.
2. Kliknij prawym przyciskiem myszy docelowy punkt dystrybucji, a następnie wybierz **ponowne przypisanie punktu dystrybucji**. 
  ![Ponowne przypisanie punktu dystrybucji](media/1306937-reassign-dp.png)
3. Wybierz serwer lokacji i kod lokacji, do których chcesz ponownie przypisać ten punkt dystrybucji. 
  ![Wybierz serwer lokacji](media/1306937-select-site.png)



## <a name="improvements-to-hardware-inventory"></a>Ulepszenia dotyczące spisu sprzętu
<!-- 1357389 -->
Dla nowo dodanego klas można określić więcej niż 255 znaków długości ciągu dla właściwości spisu sprzętu, które nie są kluczami.

### <a name="try-it-out"></a>Wypróbuj  
Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.<br/>

1. W **administracji** obszaru roboczego kliknij **ustawień klienta** zaznacz Edytuj, kliknij prawym przyciskiem myszy, a następnie wybierz ustawienie urządzenia klienckiego **właściwości**. 
2. Wybierz **spisu sprzętu**, następnie **Ustaw klasy**, i **dodać**.
3. Kliknij przycisk **Connect** przycisku.
4. Wypełnij **nazwy komputera**, **obszar nazw usługi WMI**, wybierz pozycję **cykliczne** w razie potrzeby. Podaj poświadczenia, jeśli jest to niezbędne do połączenia. Kliknij przycisk **Connect** Aby wyświetlić klasy obszaru nazw.
5. Wybierz nową klasę, a następnie kliknij przycisk **Edytuj**.
6. Zmień **długość** z co najmniej jedną właściwość, która jest ciągiem znaków innych niż key, powinien być większy niż 255. Kliknij przycisk **OK**. 
7. Upewnij się, że właściwość edytowanych został wybrany do **Dodaj klasę spisu sprzętu** i kliknij przycisk **OK**. 
8. Zbieranie spisu sprzętu przy użyciu klasy nowo dodanego zawierający właściwości więcej niż 255 znaków długości. 



## <a name="improvements-to-client-settings-for-software-center"></a>Udoskonalenia ustawień klienta w programie Software Center
<!-- 1351224 & 1355146 -->
W tej wersji Technical Preview wprowadzono ulepszenia dostosowywania Centrum oprogramowania w ustawieniach klienta. 

1. Ustawienia klienta w programie Software Center już **Dostosuj** przycisku.
2. Podgląd dodano pokazanie, jak wygląda na banerze Centrum oprogramowania.<!--1351224-->
    - Jeśli nie wybrano logo, Podgląd tekstu nazwy firmy i kolor.
    - Jeśli wybrano logo, Podgląd logo i firmy tekstu nazwy.  
3.  **Ukryj niezatwierdzonych aplikacji w programie Software Center** jest nowe ustawienie w programie Software Center. Gdy ta opcja jest włączona, użytkownik dostępnych aplikacji, które wymagają zatwierdzenia są ukryte w programie Software Center.<!--1355146-->

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W **administracji** obszaru roboczego kliknij **ustawień klienta**. Wybierz ustawienie urządzenia klienckiego, aby edytować. Kliknij prawym przyciskiem myszy na nim, a następnie wybierz **właściwości** następnie **Centrum oprogramowania**.
2.  Polecenie **Dostosuj** przycisku. Wypróbuj ustawienia różne dostosowania, w tym w wersji zapoznawczej.
3. Włącz ustawienie **Ukryj niezatwierdzonych aplikacji w programie Software Center**. Obserwować zmiany w programie Software Center. 



## <a name="new-settings-for-windows-defender-application-guard"></a>Nowe ustawienia dla systemu Windows Defender aplikacji Guard
<!-- 1356256 -->
Dla wersji systemu Windows 10 1709 i urządzenia z nowszymi wersjami, istnieją dwa nowe ustawienia hosta interakcji dla [Windows Defender aplikacji Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy). 
1. Witryny sieci Web mogą mieć dostęp do procesora graficznego wirtualnego hosta. 
2. Pliki pobierane wewnątrz kontenera może trwale znajdować się na hoście. </br>



## <a name="improvements-to-run-scripts"></a>Ulepszenia na uruchamianie skryptów
<!-- 1236459 -->
[ **Uruchamianie skryptów** funkcji](/sccm/apps/deploy-use/create-deploy-scripts) umożliwia teraz importowanie i uruchamiania podpisanych skryptów środowiska PowerShell. 
- Aby zachować spójność skryptu, musi być importowany zamiast za pomocą kopiowania i wklejania podpisanych skryptów. 
- Nie można edytować importowane podpisanych skryptów po zaimportowaniu.
    
>[!IMPORTANT]
>W tej wersji Technical Preview istnieją dwie czasowe ograniczenia.
>- Skrypty można importować tylko w funkcji uruchamianie skryptów i nie można edytować bezpośrednio z konsoli.
>- Skrypty zaimportowane wraz z kodowaniem Unicode nie może być wyświetlany niepoprawnie w konsoli. Skrypt zostanie wykonany nadal jako pierwotnie napisane.





## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
