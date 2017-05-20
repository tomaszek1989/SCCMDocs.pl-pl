---
title: "Ikony używane dla aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Konsola programu Configuration Manager zawiera ikony wskazujące stanu zsynchronizowanych grupy aktualizacji oprogramowania lub aktualizacji."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 63c5ef72-5715-4d86-85a2-71beba469fab
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 04c5ccc53263b2672096b564695a636bfb28d952
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="icons-used-for-software-updates-in-system-center-configuration-manager"></a>Ikony używane dla aktualizacji oprogramowania System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zsynchronizowane aktualizacje oprogramowania są wyświetlane w konsoli programu Configuration Manager, a pierwsza kolumna dla każdej aktualizacji oprogramowania zawiera ikonę, która wskazuje określonego stanu. Grupy aktualizacji oprogramowania również są przedstawiane za pomocą ikony, która zawiera informacje o stanie aktualizacji oprogramowania należących do grupy. Ta sekcja zawiera informacje o ikonach aktualizacji oprogramowania oraz znaczeniu poszczególnych ikon.  

## <a name="icons-for-software-updates"></a>Ikony aktualizacji oprogramowania  
 Synchronizowane aktualizacje oprogramowania są reprezentowane przez jedną z następujących ikon.  

### <a name="normal-icon"></a>Ikona elementów normalnych  
 ![ikona](../media/Normal.jpg "normalna ikona") ikonę z zieloną strzałkę reprezentuje aktualizacji oprogramowania normalnego.  

 **Opis:**  

 Normalne aktualizacje oprogramowania zostały zsynchronizowane i są dostępne na potrzeby wdrożenia oprogramowania.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.  

### <a name="expired-icon"></a>Ikona elementów wygasłych  
 ![ikona](../media/Expired.jpg "ikona wygasłe") ikonę z czarny symbol X reprezentuje wygasłą aktualizację oprogramowania. Wygasłe aktualizacje oprogramowania można też wskazać, wyświetlając **wygasłe** kolumny dla aktualizacji oprogramowania, gdy są wyświetlane w konsoli programu Configuration Manager.  

 **Opis:**  

 Wygasłe aktualizacje oprogramowania były wcześniej dostępne do wdrożenia na komputerach klienckich, ale po wygaśnięciu aktualizacji oprogramowania nie można tworzyć nowych wdrożeń aktualizacji oprogramowania. Wygasłe oprogramowania aktualizacje zostaną usunięte z aktywnego wdrożenia i nie będą dostępne dla klientów.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.

### <a name="superseded-icon"></a>Ikona elementów zastąpionych  
 ![ikona](../media/Superseded.jpg "ikona zastąpione") ikonę z żółtą gwiazdkę reprezentuje zastąpionej aktualizacji oprogramowania. Można również zidentyfikować zastąpione aktualizacje oprogramowania, wyświetlając **zastąpione** kolumny dla aktualizacji oprogramowania, gdy są wyświetlane w konsoli programu Configuration Manager.  

 **Opis:**  

 Zastąpione aktualizacje oprogramowania zostały zamienione na nowsze wersje aktualizacji oprogramowania. Najczęściej aktualizacja oprogramowania zastępująca inną aktualizację oprogramowania wykonuje jedno lub więcej z następujących działań:  

-   Wzbogaca, usprawnia lub rozszerza poprawkę udostępnioną przez jedną lub więcej wcześniej wydanych aktualizacji oprogramowania.  

-   Zwiększa wydajność pakietu plików aktualizacji oprogramowania instalowanego przez klientów w przypadku zatwierdzenia aktualizacji oprogramowania do instalacji. Na przykład zastąpiona aktualizacja oprogramowania może zawierać pliki, które nie mają już zastosowania do poprawki lub systemów operacyjnych obsługiwanych przez nową aktualizację. Dlatego pliki te zostały usunięte z pakietu zastępującej aktualizacji oprogramowania.  

-   Aktualizuje nowsze wersje produktu albo, innymi słowy, nie ma już zastosowania do starszych wersji lub konfiguracji produktu. Aktualizacje oprogramowania mogą także zastępować inne aktualizacje oprogramowania, jeśli wprowadzono modyfikacje rozszerzające obsługę języków. Na przykład nowsza wersja aktualizacji pakietu Microsoft Office może już nie obsługiwać starszych systemów operacyjnych, lecz wprowadzać obsługę nowych języków, których nie było w pierwotnej wersji aktualizacji oprogramowania.  

 Na karcie Reguły zastępowania we właściwościach składnika punktu aktualizacji oprogramowania można określić sposób zarządzania zastąpionymi aktualizacjami oprogramowania. Aby uzyskać więcej informacji, zobacz [Reguły zastępowania](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

 **Problemy operacyjne:**  

 Jeśli to możliwe, należy wdrożyć zastępującą aktualizację oprogramowania na komputerach klienckich zamiast zastąpionej aktualizacji oprogramowania. Listę aktualizacji oprogramowania, które zastępują daną aktualizację oprogramowania, można wyświetlić na karcie **Informacje o zastępowaniu** we właściwościach aktualizacji oprogramowania.  

### <a name="invalid-icon"></a>Ikona elementów nieprawidłowych  
 ![ikona](../media/Invalid.jpg "ikona nieprawidłowy") ikoną z czerwonym znakiem X reprezentuje Nieprawidłowa aktualizacja oprogramowania.  

 **Opis:**  

 Nieprawidłowe aktualizacje oprogramowania znajdują się w aktywnym wdrożeniu, ale z jakiegoś powodu zawartość (pliki aktualizacji oprogramowania) nie jest dostępna. Poniżej przedstawiono scenariusze, w których może wystąpić ten stan:  

-   Aktualizacja oprogramowania została wdrożona pomyślnie, ale plik aktualizacji oprogramowania został usunięty z pakietu wdrożenia i nie jest już dostępny.  

-   Utworzono wdrożenie aktualizacji oprogramowania w lokacji i obiekt wdrożenia został pomyślnie zreplikowany do lokacji podrzędnej, ale pakiet wdrożenia nie został pomyślnie zreplikowany do lokacji podrzędnej.  

 **Problemy operacyjne:**  

 W przypadku braku zawartości aktualizacji oprogramowania klienci nie są w stanie zainstalować aktualizacji do momentu udostępnienia zawartości w punkcie dystrybucji. Ponowną dystrybucję zawartości do punktów dystrybucji można przeprowadzić przy użyciu akcji **Ponowna dystrybucja** . Jeśli brakuje zawartości dla aktualizacji oprogramowania we wdrożeniu utworzonym w lokacji nadrzędnej, konieczna jest replikacja lub ponowna dystrybucja aktualizacji oprogramowania do lokacji podrzędnej. Aby uzyskać więcej informacji dotyczących ponownej dystrybucji zawartości, zobacz [zarządzanie zawartością, których dystrybucja](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

### <a name="metadata-only-icon"></a>Ikona elementów zawierających tylko metadane
 ![ikona](../media/MetadataOnly.png "ikona tylko metadane") ikona ze strzałką niebieski reprezentuje aktualizacji oprogramowania tylko metadane.

 **Opis:**  

 Aktualizacje oprogramowania tylko metadane są dostępne w konsoli programu Configuration Manager do raportowania. Aktualizacji oprogramowania zawierających tylko metadane nie można wdrożyć ani pobrać, ponieważ żaden plik aktualizacji oprogramowania nie jest skojarzony z metadanymi aktualizacji oprogramowania.  

 **Problemy operacyjne:**  

 Aktualizacje oprogramowania zawierające tylko metadane są dostępne dla celów raportowania i nie są przeznaczone do wdrażania.  

## <a name="icons-for-software-update-groups"></a>Ikony grup aktualizacji oprogramowania  
 Grupy aktualizacji oprogramowania są reprezentowane przez jedną z następujących ikon.  

### <a name="normal-icon"></a>Ikona elementów normalnych  
 ![ikona](../media/Normal.jpg "normalna ikona") ikonę z zieloną strzałkę reprezentuje grupę aktualizacji oprogramowania zawierającej aktualizacje oprogramowania tylko normalne.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.  

### <a name="expired-icon"></a>Ikona elementów wygasłych  
 ![ikona](../media/Expired.jpg "ikona wygasłe") ikonę z czarny symbol X reprezentuje grupy aktualizacji oprogramowania, który zawiera co najmniej jeden Wygasłe aktualizacje oprogramowania.  

 **Problemy operacyjne:**  

 Jeśli to możliwe, należy usunąć lub zamienić wygasłe aktualizacje oprogramowania w grupie aktualizacji oprogramowania.  

### <a name="superseded-icon"></a>Ikona elementów zastąpionych  
 ![ikona](../media/Superseded.jpg "ikona zastąpione") ikonę z żółtą gwiazdkę reprezentuje grupę aktualizacji, która zawiera jeden lub więcej zastąpione aktualizacje oprogramowania.  

 **Problemy operacyjne:**  

 Jeśli to możliwe, zastąpioną aktualizację oprogramowania w grupie aktualizacji oprogramowania należy zamienić na zastępującą aktualizację oprogramowania.  

### <a name="invalid-icon"></a>Ikona elementów nieprawidłowych  
 ![ikona](../media/Invalid.jpg "ikona nieprawidłowy") ikoną z czerwonym znakiem X reprezentuje grupę aktualizacji oprogramowania zawierającą co najmniej jeden nieprawidłowy aktualizacje.  

 **Problemy operacyjne:**  

 W przypadku braku zawartości aktualizacji oprogramowania klienci nie są w stanie zainstalować aktualizacji do momentu udostępnienia zawartości w punkcie dystrybucji. Ponowną dystrybucję zawartości do punktów dystrybucji można przeprowadzić przy użyciu akcji **Ponowna dystrybucja** . Jeśli brakuje zawartości dla aktualizacji oprogramowania we wdrożeniu utworzonym w lokacji nadrzędnej, konieczna jest replikacja lub ponowna dystrybucja aktualizacji oprogramowania do lokacji podrzędnej. Aby uzyskać więcej informacji dotyczących ponownej dystrybucji zawartości, zobacz [zarządzanie zawartością, których dystrybucja](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

