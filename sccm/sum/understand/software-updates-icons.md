---
title: Ikony stosowane przy aktualizacjach oprogramowania
titleSuffix: Configuration Manager
description: Konsola programu Configuration Manager zawiera ikony, które wskazują stan synchronizowane grupy aktualizacji update lub oprogramowania.
author: aczechowski
manager: dougeby
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 63c5ef72-5715-4d86-85a2-71beba469fab
ms.author: aaroncz
ms.openlocfilehash: d772b4ede4c8bfe13c68597ec8fe9a1f3dccbf38
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="icons-used-for-software-updates-in-system-center-configuration-manager"></a>Ikony stosowane przy aktualizacjach oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Synchronizowane aktualizacje oprogramowania są wyświetlane w konsoli programu Configuration Manager, a pierwsza kolumna każdej aktualizacji oprogramowania zawiera ikonę, która wskazuje określony stan. Grupy aktualizacji oprogramowania również są przedstawiane za pomocą ikony, która zawiera informacje o stanie aktualizacji oprogramowania należących do grupy. Ta sekcja zawiera informacje o ikonach aktualizacji oprogramowania oraz znaczeniu poszczególnych ikon.  

## <a name="icons-for-software-updates"></a>Ikony aktualizacji oprogramowania  
 Synchronizowane aktualizacje oprogramowania są reprezentowane przez jedną z następujących ikon.  

### <a name="normal-icon"></a>Ikona elementów normalnych  
 ![ikona](../media/Normal.jpg "ikona elementów normalnych") ikona z zieloną strzałką reprezentuje normalną aktualizację oprogramowania.  

 **Opis:**  

 Normalne aktualizacje oprogramowania zostały zsynchronizowane i są dostępne na potrzeby wdrożenia oprogramowania.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.  

### <a name="expired-icon"></a>Ikona elementów wygasłych  
 ![ikona](../media/Expired.jpg "ikona wygasłe") ikona z czarnym symbolem X reprezentuje wygasłą aktualizację oprogramowania. Wygasłe aktualizacje oprogramowania można zidentyfikować także przy **wygasłe** kolumnę do aktualizacji oprogramowania wyświetlanych w konsoli programu Configuration Manager.  

 **Opis:**  

 Wygasłe aktualizacje oprogramowania były wcześniej dostępne do wdrożenia na komputerach klienckich, ale po wygaśnięciu aktualizacji oprogramowania nie można tworzyć nowych wdrożeń aktualizacji oprogramowania. Wygasłe aktualizacje oprogramowania są usuwane z aktywnych wdrożeń i nie będą dostępne dla klientów.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.

### <a name="superseded-icon"></a>Ikona elementów zastąpionych  
 ![ikona](../media/Superseded.jpg "ikona zastąpione") ikona z żółtą gwiazdką reprezentuje zastąpioną aktualizację oprogramowania. Zastąpione aktualizacje oprogramowania można zidentyfikować także przy **zastąpione** kolumnę do aktualizacji oprogramowania wyświetlanych w konsoli programu Configuration Manager.  

 **Opis:**  

 Zastąpione aktualizacje oprogramowania zostały zamienione na nowsze wersje aktualizacji oprogramowania. Najczęściej aktualizacja oprogramowania zastępująca inną aktualizację oprogramowania wykonuje jedno lub więcej z następujących działań:  

-   Wzbogaca, usprawnia lub rozszerza poprawkę udostępnioną przez jedną lub więcej wcześniej wydanych aktualizacji oprogramowania.  

-   Zwiększa wydajność pakietu plików aktualizacji oprogramowania instalowanego przez klientów w przypadku zatwierdzenia aktualizacji oprogramowania do instalacji. Na przykład zastąpiona aktualizacja oprogramowania może zawierać pliki, które nie mają już zastosowania do poprawki lub systemów operacyjnych obsługiwanych przez nową aktualizację. Dlatego pliki te zostały usunięte z pakietu zastępującej aktualizacji oprogramowania.  

-   Aktualizuje nowsze wersje produktu albo, innymi słowy, nie ma już zastosowania do starszych wersji lub konfiguracji produktu. Aktualizacje oprogramowania mogą także zastępować inne aktualizacje oprogramowania, jeśli wprowadzono modyfikacje rozszerzające obsługę języków. Na przykład nowsza wersja aktualizacji pakietu Microsoft Office może już nie obsługiwać starszych systemów operacyjnych, lecz wprowadzać obsługę nowych języków, których nie było w pierwotnej wersji aktualizacji oprogramowania.  

 Na karcie Reguły zastępowania we właściwościach składnika punktu aktualizacji oprogramowania można określić sposób zarządzania zastąpionymi aktualizacjami oprogramowania. Aby uzyskać więcej informacji, zobacz [Reguły zastępowania](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

 **Problemy operacyjne:**  

 Jeśli to możliwe, należy wdrożyć zastępującą aktualizację oprogramowania na komputerach klienckich zamiast zastąpionej aktualizacji oprogramowania. Listę aktualizacji oprogramowania, które zastępują daną aktualizację oprogramowania, można wyświetlić na karcie **Informacje o zastępowaniu** we właściwościach aktualizacji oprogramowania.  

### <a name="invalid-icon"></a>Ikona elementów nieprawidłowych  
 ![ikona](../media/Invalid.jpg "ikona elementów nieprawidłowych") ikona z czerwonym symbolem X reprezentuje nieprawidłową aktualizację oprogramowania.  

 **Opis:**  

 Nieprawidłowe aktualizacje oprogramowania znajdują się w aktywnym wdrożeniu, ale z jakiegoś powodu zawartość (pliki aktualizacji oprogramowania) nie jest dostępna. Poniżej przedstawiono scenariusze, w których może wystąpić ten stan:  

-   Aktualizacja oprogramowania została wdrożona pomyślnie, ale plik aktualizacji oprogramowania został usunięty z pakietu wdrożenia i nie jest już dostępny.  

-   Utworzono wdrożenie aktualizacji oprogramowania w lokacji i obiekt wdrożenia został pomyślnie zreplikowany do lokacji podrzędnej, ale pakiet wdrożenia nie został pomyślnie zreplikowany do lokacji podrzędnej.  

 **Problemy operacyjne:**  

 W przypadku braku zawartości aktualizacji oprogramowania klienci nie są w stanie zainstalować aktualizacji do momentu udostępnienia zawartości w punkcie dystrybucji. Ponowną dystrybucję zawartości do punktów dystrybucji można przeprowadzić przy użyciu akcji **Ponowna dystrybucja** . Jeśli brakuje zawartości dla aktualizacji oprogramowania we wdrożeniu utworzonym w lokacji nadrzędnej, konieczna jest replikacja lub ponowna dystrybucja aktualizacji oprogramowania do lokacji podrzędnej. Aby uzyskać więcej informacji o ponownej dystrybucji zawartości, zobacz [zarządzania zawartością zostały rozproszonych](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

### <a name="metadata-only-icon"></a>Ikona elementów zawierających tylko metadane
 ![ikona](../media/MetadataOnly.png "ikona elementów zawierających tylko metadane") ikona z niebieską strzałką reprezentuje aktualizację oprogramowania zawierające tylko metadane.

 **Opis:**  

 Aktualizacje oprogramowania zawierające tylko metadane są dostępne w konsoli programu Configuration Manager do raportowania. Aktualizacji oprogramowania zawierających tylko metadane nie można wdrożyć ani pobrać, ponieważ żaden plik aktualizacji oprogramowania nie jest skojarzony z metadanymi aktualizacji oprogramowania.  

 **Problemy operacyjne:**  

 Aktualizacje oprogramowania zawierające tylko metadane są dostępne dla celów raportowania i nie są przeznaczone do wdrażania.  

## <a name="icons-for-software-update-groups"></a>Ikony grup aktualizacji oprogramowania  
 Grupy aktualizacji oprogramowania są reprezentowane przez jedną z następujących ikon.  

### <a name="normal-icon"></a>Ikona elementów normalnych  
 ![ikona](../media/Normal.jpg "ikona elementów normalnych") ikona z zieloną strzałką reprezentuje grupę aktualizacji oprogramowania zawierającą tylko normalne aktualizacje oprogramowania.  

 **Problemy operacyjne:**  

 Brak problemów operacyjnych.  

### <a name="expired-icon"></a>Ikona elementów wygasłych  
 ![ikona](../media/Expired.jpg "ikona wygasłe") ikona z czarnym symbolem X reprezentuje grupę aktualizacji oprogramowania, który zawiera co najmniej jeden Wygasłe aktualizacje oprogramowania.  

 **Problemy operacyjne:**  

 Jeśli to możliwe, należy usunąć lub zamienić wygasłe aktualizacje oprogramowania w grupie aktualizacji oprogramowania.  

### <a name="superseded-icon"></a>Ikona elementów zastąpionych  
 ![ikona](../media/Superseded.jpg "ikona zastąpione") ikona z żółtą gwiazdką reprezentuje grupę aktualizacji oprogramowania, która zawiera jeden lub więcej zastąpione aktualizacje oprogramowania.  

 **Problemy operacyjne:**  

 Jeśli to możliwe, zastąpioną aktualizację oprogramowania w grupie aktualizacji oprogramowania należy zamienić na zastępującą aktualizację oprogramowania.  

### <a name="invalid-icon"></a>Ikona elementów nieprawidłowych  
 ![ikona](../media/Invalid.jpg "ikona elementów nieprawidłowych") ikona z czerwonym symbolem X reprezentuje grupę aktualizacji oprogramowania, który zawiera co najmniej jednej aktualizacji oprogramowania nieprawidłowy.  

 **Problemy operacyjne:**  

 W przypadku braku zawartości aktualizacji oprogramowania klienci nie są w stanie zainstalować aktualizacji do momentu udostępnienia zawartości w punkcie dystrybucji. Ponowną dystrybucję zawartości do punktów dystrybucji można przeprowadzić przy użyciu akcji **Ponowna dystrybucja** . Jeśli brakuje zawartości dla aktualizacji oprogramowania we wdrożeniu utworzonym w lokacji nadrzędnej, konieczna jest replikacja lub ponowna dystrybucja aktualizacji oprogramowania do lokacji podrzędnej. Aby uzyskać więcej informacji o ponownej dystrybucji zawartości, zobacz [zarządzania zawartością zostały rozproszonych](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  
