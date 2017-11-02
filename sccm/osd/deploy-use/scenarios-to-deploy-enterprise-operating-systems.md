---
title: "Scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw"
titleSuffix: Configuration Manager
description: "Dowiedz się o kilka scenariuszy wdrażania systemów operacyjnych dla przedsiębiorstw o programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f74fdb86-c7c2-447f-91f6-b42df6370d7f
caps.latest.revision: "11"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d7934c3d757ec0ede6553d9c17b3d36117da3892
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="scenarios-to-deploy-enterprise-operating-systems-with-system-center-configuration-manager"></a>Scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Następujące systemu operacyjnego scenariusze wdrażania są dostępne w programie System Center Configuration Manager:  

-   [Uaktualnianie systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md): Ten scenariusz uaktualnia system operacyjny na komputerach z systemem operacyjnym Windows 7, Windows 8, Windows 8.1 lub Windows 10. W procesie uaktualnienia zostają zachowane aplikacje, ustawienia i dane użytkowników komputera. Nie występują żadne zależności zewnętrzne (np. zależność zestawu Windows ADK) i ten proces jest szybszy oraz bardziej odporny niż tradycyjne wdrażanie systemu operacyjnego.  

-   [Odświeżenie istniejącego komputera przy użyciu nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md): Ten scenariusz partycje i formatuje (czyści) istniejący komputer oraz instaluje nowy system operacyjny na komputerze. Po zainstalowaniu systemu operacyjnego można przenieść do niego ustawienia i dane użytkowników.  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md): Ten scenariusz instaluje system operacyjny na nowym komputerze. To nowa instalacja systemu operacyjnego, więc nie wymaga migrowania ustawień ani danych użytkowników.  

-   [Zastąpienie istniejącego komputera i przetransferowanie ustawień](replace-an-existing-computer-and-transfer-settings.md): Ten scenariusz instaluje system operacyjny na nowym komputerze. Opcjonalnie można przenieść ustawienia i dane użytkowników ze starego komputera na nowy.  

## <a name="things-to-consider-before-you-deploy-operating-system-images"></a>Zagadnienia do wzięcia pod uwagę przed przystąpieniem do wdrażania obrazów systemu operacyjnego  
 Przed wdrożeniem systemu operacyjnego należy rozważyć pewne zagadnienia.  

### <a name="operating-system-image-size"></a>Rozmiar obrazu systemu operacyjnego  
 Rozmiar obrazu systemu operacyjnego może być dość duży. Przykładowo rozmiar obrazu systemu Windows 7 to 3 gigabajty (GB) lub więcej. Rozmiar obrazu i liczba komputerów, na których jednocześnie wdrażany jest system operacyjny, wypływają na wydajność sieci i dostępną przepustowość. Należy przetestować wydajność sieci, aby lepiej określić potencjalny wpływ wdrożenia obrazu i całkowity czas wdrażania. Działania programu Configuration Manager, które mają wpływ na wydajność sieci obejmują przesyłanie obrazu do punktu dystrybucji, przesyłanie obrazu z jednej lokacji do innej i pobieranie obrazu do klienta programu Configuration Manager.  

 Należy także przeznaczyć wystarczającą ilość miejsca na dyskach punktów dystrybucji zawierających obrazy systemu operacyjnego.  

### <a name="client-cache-size"></a>Rozmiar pamięci podręcznej klienta  
 Podczas pobierania zawartości klienci programu Configuration Manager, automatycznie korzystają z usługi inteligentnego transferu w tle (BITS) Jeśli jest dostępna. Podczas wdrażania sekwencji zadań, która instaluje system operacyjny, można ustawić opcję wdrożenia, aby klienci programu Configuration Manager pobranie pełnego obrazu do lokalnej pamięci podręcznej przed uruchomieniem sekwencji zadań.  

 Ogólnie rzecz biorąc gdy klient programu Configuration Manager musi pobrać obraz systemu operacyjnego (lub inny pakiet), ale nie ma wystarczającej ilości miejsca w pamięci podręcznej, klient sprawdza inne pakiety w pamięci podręcznej, aby określić, czy usunięcie dowolnego lub wszystkich najstarszych pakietów zwolni wystarczającą ilość miejsca na dysku do pomieszczenia obrazu. Jeżeli usunięcie pakietów nie spowoduje zwolnienia wystarczającej ilości miejsca na dysku, klient nie pobiera obrazu i wdrożenie kończy się niepowodzeniem. Taka sytuacja może wystąpić, jeżeli pamięć podręczna zawiera duży pakiet skonfigurowany tak, aby trwale w niej pozostawał. Jeżeli usunięcie pakietów spowoduje zwolnienie wystarczającej ilości miejsca w pamięci podręcznej, klient usunie je, a następnie pobierze obraz do pamięci podręcznej.  

 Domyślny rozmiar pamięci podręcznej na klientach programu Configuration Manager nie może być wystarczająco duży dla wdrożenia obrazów większości systemów operacyjnych. Jeżeli planowane jest pobranie pełnego obrazu do pamięci podręcznej klienta, należy dostosować rozmiar pamięci podręcznej klienta programu Configuration Manager na komputerach docelowych tak, aby zmieścił się obrazu, który jest wdrażany.  

 Aby uzyskać więcej informacji, zobacz [Konfiguracja pamięci podręcznej klienta w klientach programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_ClientCache).  

## <a name="task-sequence-deployments"></a>Wdrożenia sekwencji zadań  
 Utworzona sekwencja zadań można wdrożyć obraz systemu operacyjnego na komputerze klienckim programu Configuration Manager w jednym z następujących sposobów:  

-   Pobranie obrazu i jego zawartości najpierw do pamięci podręcznej klienta programu Configuration Manager z punktu dystrybucji, a następnie zainstaluj go.  

-   Zainstalowanie obrazu i jego zawartości bezpośrednio z punktu dystrybucji  

-   Zainstalowanie obrazu i jego zawartości z punktu dystrybucji zgodnie z wymaganiami  

 Domyślnie podczas tworzenia wdrożenia dla sekwencji zadań obraz jest najpierw pobierany do pamięci podręcznej klienta programu Configuration Manager i następnie instalowany. Jeżeli wybrano pobranie obrazu do pamięci podręcznej klienta programu Configuration Manager przed uruchomieniem obrazu, a sekwencja zadań zawiera krok ponownego podziału dysku twardego krok partycje, jego kończy się niepowodzeniem, ponieważ podział dysku twardego na partycje powoduje usunięcie zawartości pamięci podręcznej klienta programu Configuration Manager. Jeśli sekwencja zadań wymaga ponownego podziału dysku twardego na partycje, przy wdrażaniu sekwencji zadań należy uruchomić instalację obrazu z punktu dystrybucji, używając opcji **Uruchom program z punktu dystrybucji**  .  

 Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  
