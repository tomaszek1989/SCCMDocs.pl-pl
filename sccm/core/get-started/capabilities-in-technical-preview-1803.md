---
title: Technical Preview 1803
titleSuffix: Configuration Manager
description: Więcej informacji na temat nowych funkcji dostępnych w wersji Configuration Manager Technical Preview 1803.
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56dc4b07-5aa4-43e2-9be8-d26ae5ff5613
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f3c200fe699f85c195e41fc2b395a3d710b1788a
ms.sourcegitcommit: d3863a9b34f9925515cabe9a290a6c733e10108b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2018
---
# <a name="capabilities-in-technical-preview-1803-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1803 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu Configuration Manager, wersja 1803. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do swojej witryny wersji zapoznawczej technical preview. 

Przegląd [Technical Preview](/sccm/core/get-started/technical-preview) artykuł przed zainstalowaniem tej aktualizacji. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->


</br>

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  



 
## <a name="pull-distribution-points-support-cloud-distribution-points-as-source"></a>Dystrybucji ściągania punktów obsługi punktów dystrybucji w chmurze jako źródło  
<!--1321554-->
Wielu klientów używa [ściągające punkty dystrybucji](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point) w zdalnej lub oddziałów, które pobierają zawartość z punktu dystrybucji w sieci WAN. Jeśli biura zdalnego ma lepszą połączenia z Internetem lub aby zmniejszyć obciążenie łącza sieci WAN, można teraz używać [punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) platformie Microsoft Azure jako źródła. Po dodaniu źródła na **ściągający punkt dystrybucji** kartę Właściwości punktu dystrybucji, wszystkie punkty dystrybucji w chmurze w witrynie teraz znajduje się w dostępnych punktach dystrybucji. Zachowanie obu ról systemu lokacji zmienia się, w przeciwnym razie wartość. 

### <a name="prerequisites"></a>Wymagania wstępne
- Punkt dystrybucji ściągania wymaga dostępu do Internetu do komunikowania się z Microsoft Azure.
- Zawartość musi zostać dystrybuowany do punktu dystrybucji chmury.

> [!Note]  
> Ta funkcja spowodować naliczenie opłat do subskrypcji platformy Azure dla magazynu i sieci wyjście danych. Aby uzyskać więcej informacji, zobacz [kosztów chmurowych punktów dystrybucji](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#BKMK_CloudDPCost).



## <a name="partial-download-support-in-client-peer-cache-to-reduce-wan-utilization"></a>Obsługa częściowej pobierania w klienta równorzędnej pamięci podręcznej, aby zmniejszyć wykorzystanie sieci WAN
<!--1357346-->
Klient równorzędnej pamięci podręcznej źródeł teraz podzielić na części zawartości. Części te zminimalizować transferu sieciowego, aby zmniejszyć wykorzystanie sieci WAN. Punkt zarządzania zapewnia bardziej szczegółowe śledzenie części zawartości. Próbuje usunąć więcej niż jeden pobieranie tej samej zawartości dla każdej grupy granic. 

### <a name="example-scenario"></a>Przykładowy scenariusz
Firma Contoso ma jedną lokację główną z dwóch grup granic: Główna i oddział firmy centrali (kg). Brak relacji rezerwowy 30-minutowych między grupami granic. Punkt zarządzania i punkt dystrybucji dla lokacji są tylko w granicy HQ. Oddziału firmy ma żaden lokalny punkt dystrybucji. Dwa z czterech klientów w biurze oddziału są skonfigurowane jako równorzędnej pamięci podręcznej źródeł. 

![Diagram konfiguracji sieci, zgodnie z opisem przykładowy scenariusz](media/1357346-peer-cache-source-parts.png)

1. W przypadku skierowania wdrożenia o zawartości do wszystkich klientów cztery w biurze oddziału. Tylko dystrybucji zawartości do punktu dystrybucji.
2. Client3 i Client4 nie masz lokalne źródło wdrożenia. Punkt zarządzania nakazuje klientom Odczekaj 30 minut przed powrotem do grupy granic zdalnego.
3. Client1 (PCS1) jest pierwszym źródła równorzędnej w pamięci podręcznej, aby odświeżyć zasady w punkcie zarządzania. Ten klient jest włączony jako źródło równorzędnej pamięci podręcznej, punkt zarządzania nakazuje, aby natychmiast rozpocząć pobieranie części A z punktu dystrybucji.  
4. Gdy KLIENT2 (PCS2) kontaktuje się z punktem zarządzania, A część jest już w toku, ale jeszcze niekompletny, punkt zarządzania nakazuje, aby natychmiast rozpocząć pobieranie części B z punktu dystrybucji.
5. PCS1 zakończeniu pobrać części A i natychmiast powiadomi punkt zarządzania. W ramach B jest już w toku, ale jeszcze niekompletny, punkt zarządzania nakazuje, aby rozpocząć pobieranie części C z punktu dystrybucji.
6. PCS2 zakończeniu pobrać części B i natychmiast powiadomi punkt zarządzania. Punkt zarządzania nakazuje, aby rozpocząć pobieranie części D z punktu dystrybucji. 
7. PCS1 zakończeniu pobrać części C i natychmiast powiadomi punkt zarządzania. Punkt zarządzania informuje o jego czy nie dostępnych żadnych części więcej ze zdalnego punktu dystrybucji. Punkt zarządzania nakazuje go pobrać części B z jego lokalnego elementu równorzędnego PCS2.
8. Ten proces jest kontynuowany do momentu zarówno klient równorzędnej pamięci podręcznej źródeł ma wszystkie części od siebie. Punkt zarządzania priorytetem części ze zdalnego punktu dystrybucji przed poinstruowanie źródła pamięci podręcznej elementów równorzędnych, aby pobrać części z lokalnych elementów równorzędnych. 
9. Client3 jest pierwszą, aby odświeżyć zasady, po wygaśnięciu okresu rezerwowy 30 minut. Teraz sprawdza ponownie z punktem zarządzania, który informuje klienta nowych lokalnych źródeł. Zamiast pobierania zawartości w pełni z punktu dystrybucji w sieci WAN, pobierania zawartości w pełni z jednego ze źródeł klienta równorzędnej pamięci podręcznej. Klienci priorytetów źródła lokalnego elementu równorzędnego. 

> [!Note]  
> Jeśli liczba klientów równorzędnej pamięci podręcznej źródeł jest większa niż liczba części zawartości, punkt zarządzania nakazuje źródeł pamięci podręcznej dodatkowego elementu równorzędnego czekać na rezerwowy, takich jak normalne klienta. 


### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. Konfigurowanie [grup granic](/sccm/core/servers/deploy/configure/boundary-groups) i [elementu równorzędnego pamięci podręcznej źródeł](/sccm/core/plan-design/hierarchy/client-peer-cache) na normalny.
2. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i wybierz **witryny**. Kliknij przycisk **ustawienia hierarchii** na Wstążce. 
3. Na **ogólne** karcie, należy włączyć opcję **Konfigurowanie klienta równorzędnej pamięci podręcznej źródeł do dzielenia zawartości na części**. 
4. Utworzyć wymagane wdrożenie z zawartością.  

   > [!Note]  
   > Ta funkcja działa tylko w przypadku, gdy klient pobiera zawartość w tle, takie jak wymagane wdrożenie. Pobieranie na żądanie, takie jak kiedy użytkownik instaluje wdrożenie dostępne w programie Software Center zachowuje się jak zwykle.  

1. Aby wyświetlić ich obsługa pobieranie zawartości w części, sprawdź **ContentTransferManager.log** na źródła klienta równorzędnej pamięci podręcznej i **MP_Location.log** w punkcie zarządzania.  
 



## <a name="maintenance-windows-in-software-center"></a>Okna obsługi w programie Software Center
<!--1358131-->
Program Software Center są obecnie wyświetlane w następnym zaplanowanym oknie obsługi. Widok wszystkich na nadchodzące przełączać na karcie Stan instalacji. Wyświetla przedział czasu i listę wdrożeń, które są planowane. Lista jest pusta, jeśli nie ma żadnych okien obsługi przyszłych. 

![Wyświetlanie listy kolejnych wdrożeń na karcie Stan instalacji w programie Software Center](media/1358131-software-center-maintenance-windows.png)


## <a name="custom-tab-for-webpage-in-software-center"></a>Karta niestandardowe dla strony sieci Web w programie Software Center
<!--1358132-->
Można teraz utworzyć dostosowane kartę, aby otworzyć stronę sieci Web w programie Software Center. Ta funkcja umożliwia wyświetlanie zawartości użytkownikom końcowym w sposób spójny, niezawodne. Poniższa lista zawiera kilka przykładów:
- Kontakt z działem IT: informacje o sposobie skontaktuj się z działem informatycznym
- Centrum pomocy technicznej IT: IT samoobsługi akcje, takie jak przeszukiwanie bazy wiedzy lub otwarcie biletu pomocy technicznej.
- Dokumentacja użytkownika: artykułów dla użytkowników w organizacji na różne tematy IT, takich jak aplikacje lub uaktualnić do systemu Windows 10.


### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **administracji** roboczym **ustawień klienta** otworzyć węzła **domyślne ustawienia klienta** zasad.
2. Wybierz **Centrum oprogramowania** grupy.
3. Aby uzyskać **ustawienia Centrum oprogramowania**, kliknij przycisk **Dostosuj**.
4. Przełącz się do **karty** kartę.
5. Włącz opcję, aby **Określ kart niestandardowych w programie Software Center**.
    1. Wprowadź nazwę w **nazwy karty** pola tekstowego. Ta nazwa jest, co jest wyświetlany w programie Software Center.
    2. Wprowadź prawidłowy adres URL w **adres URL zawartości** pola tekstowego. Ten adres URL jest zawartość, która wyświetla Centrum oprogramowania, gdy użytkownik kliknie na tej karcie.

> [!Tip]  
> Centrum oprogramowania używa składników programu Internet Explorer do renderowania strony sieci web.

## <a name="enable-third-party-software-update-support-on-clients"></a>Włącz obsługę aktualizacji oprogramowania innych firm na klientach

Można teraz włączyć konfiguracji klientów programu Configuration Manager dla aktualizacji oprogramowania innych firm. Gdy użytkownik **Włącz aktualizacje oprogramowania innych firm** dla właściwości składnika punktu aktualizacji oprogramowania, pobierze SUP certyfikatu podpisywania, używany przez usługi WSUS aktualizacji innych firm. <!--1357605-->

Wybieranie **Włącz aktualizacje oprogramowania innych firm** w ustawieniach klienta wykonuje następujące czynności: 
- Na komputerze klienckim ustawia zasady dla "Zezwalaj na podpisane aktualizacje z intranetowej lokalizacji usługi aktualizacji firmy Microsoft" 
- Instaluje certyfikat podpisywania w magazynie zaufanego wydawcy na kliencie. 

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W lokacji najwyższego poziomu w hierarchii programu Configuration Manager, przejdź do **administracji** węzła, rozwiń węzeł **konfiguracja lokacji**, następnie **witryny**.
2. Kliknij prawym przyciskiem myszy na serwerze lokacji najwyższego poziomu, a następnie wybierz **Konfiguruj składniki lokacji** następnie **punkt aktualizacji oprogramowania**.
3. Polecenie **aktualizacji innych firm** i sprawdź **Włącz aktualizacje oprogramowania innych firm**.
4. Otwórz **ustawień klienta** i przejdź do ustawień **aktualizacji oprogramowania**.
5. Upewnij się, **Włącz aktualizacje oprogramowania innych firm** ustawiono **tak**.

## <a name="enable-copypaste-of-asset-details-from-monitoring-views"></a>Włącz kopiowanie/wklejanie szczegóły zasobu z widokami monitorowania
W Twojej [opinie użytkowników głosu](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20234866-allow-us-to-copy-information-out-of-the-asset-det) można teraz włączyć funkcji kopiowania i wklejania w okienku szczegółów zasobów w stan wdrażania i dystrybucji widoki monitorowania.  <!--1357552-->

## <a name="scap-extensions"></a>Rozszerzenia SCAP
W folderze Cd.latest SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi dostępna jest wersja wstępna rozszerzeń SCAP. Ta wersja wstępna rozszerzeń SCAP można zainstalować w żadnej wersji obecnie obsługiwane w bieżącej gałęzi programu Configuration Manager i LTSB 1606. Aby uzyskać więcej informacji, zobacz [rozszerzenia dotyczące automatyzacji protokołu SCAP (Security Content)](/sccm/compliance/plan-design/scap/about-scap).



## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
