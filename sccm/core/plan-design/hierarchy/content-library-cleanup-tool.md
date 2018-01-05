---
title: "Narzędzie do biblioteki zawartości oczyszczania"
titleSuffix: Configuration Manager
description: "Usuwanie osieroconych zawartości nie są już skojarzone z wdrożeniem programu System Center Configuration Manager za pomocą narzędzia Oczyszczanie biblioteki zawartości."
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: "4"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 334b79e675ea7804128b0feb9678de4ad06dbc93
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>Narzędzia do oczyszczania zawartości biblioteki programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Począwszy od wersji 1702, można użyć narzędzia wiersza polecenia (**ContentLibraryCleanup.exe**) można usunąć zawartość, która jest już skojarzony z dowolnego pakietu lub aplikacji z punktu dystrybucji (oddzielony zawartości). To narzędzie jest nazywany narzędzia Oczyszczanie biblioteki zawartości i zastępuje starsze wersje podobne narzędzia wydane w ciągu ostatnich produktów Configuration Manager.  

Narzędzie dotyczy tylko zawartość w punkcie dystrybucji można określić po uruchomieniu narzędzia. Narzędzie nie usuwa zawartości z biblioteki zawartości na serwerze lokacji.

Można znaleźć **ContentLibraryCleanup.exe** w *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* folderu na serwerze lokacji w centralnej lokacji administracyjnej lub lokacji głównej.

## <a name="requirements"></a>Wymagania  
 Narzędzie można uruchomić tylko dla pojedynczego punktu dystrybucji, w czasie.  
 - Można go uruchomić bezpośrednio na komputerze, który jest hostem punktu dystrybucji, które chcesz wyczyścić lub zdalnie z innego serwera.
 - Konto użytkownika, który uruchamia narzędzie musi mieć uprawnienia bezpośredniego administracji opartej na rolach, które są równe z pełnymi uprawnieniami administratora w hierarchii programu Configuration Manager. Narzędzie nie działa, gdy konto otrzymuje uprawnienia jako członek grupy zabezpieczeń systemu Windows z uprawnieniami administratora pełnego.

## <a name="modes-of-operation"></a>Tryby operacyjne
W następujących dwóch trybów można uruchomić narzędzie. Firma Microsoft zaleca celu uruchomienia narzędzia *co jeśli* tryb, można przejrzeć wyniki, aby uruchomić narzędzie w *usunąć tryb*:
  1.    **Co jeśli tryb**:   
      Jeśli nie określisz **/delete** przełącznika, zostanie uruchomiony w trybie warunkowej narzędzie i identyfikuje zawartości, które zostaną usunięte z punktu dystrybucji.
   - Podczas działania w trybie to narzędzie nie powoduje usunięcia żadnych danych.
   - Informacje o zawartości, które zostałyby usunięte są zapisywane w pliku dziennika narzędzia, a nie monit o potwierdzenie każdego potencjalnych usunięcia.  
      </br>   

  2. **Usuń tryb**:   
    Po uruchomieniu narzędzia z **/delete** przełącznika, narzędzie jest uruchamiane w trybie delete.

     - Gdy są uruchomione w tym trybie, oddzielone zawartości, która znajduje się w określonym punkcie dystrybucji można usunąć z biblioteki zawartości w punkcie dystrybucji.
     -  Przed usunięciem każdego pliku, musisz potwierdzić, że plik powinien zostać usunięty.  Można wybrać **Y** tak, **N** na nie, lub **tak na wszystkie** pominąć dalsze monity i Usuń wszystkie oddzielone zawartość.  
     </br>

Narzędzie jest uruchamiane w trybie, automatycznie tworzy dziennik o nazwie, która obejmuje tryb, w którym narzędzie jest uruchamiane w nazwę punktu dystrybucji i daty i godziny operacji. W pliku dziennika było nawiązywane automatycznie po zakończeniu działania narzędzia.

Domyślnie plik dziennika są zapisywane do folderu tymczasowego konta użytkownika, który uruchamia narzędzie, na komputerze, na którym narzędzie jest uruchamiane. Można użyć **/log** przełącznik, aby przekierować pliku dziennika do innej lokalizacji, w tym udziale sieciowym.


## <a name="run-the-tool"></a>Uruchom narzędzie
Aby uruchomić narzędzie:
1. Otwórz administracyjny wiersz polecenia w folderze, który zawiera **ContentLibraryCleanup.exe**.  
2. Następnie wprowadź wiersz polecenia, który zawiera przełączniki wiersza polecenia wymagane i opcjonalne przełączniki, którego chcesz użyć.

**Znany problem** po uruchomieniu narzędzia dowolnego pakietu lub wdrożenia nie powiodło się lub jest w toku może być zwracany błąd podobnie do następującej:
-  *System.InvalidOperationException: Ta biblioteka zawartości nie można oczyścić teraz ponieważ pakietu <packageID> nie jest w pełni zainstalowany.*

**Obejście problemu:** Brak. Narzędzie nie niezawodnej zidentyfikować osieroconych plików, gdy zawartość jest w toku lub nie powiodła się do wdrożenia. W związku z tym narzędzie nie pozwoli do czyszczenia zawartości do momentu rozwiązania problemu.

### <a name="command-line-switches"></a>Przełączniki wiersza polecenia  
Następujące przełączniki wiersza polecenia mogą być używane w dowolnej kolejności.   

|Przełącznik|Szczegóły|
|---------|-------|
|**/ DELETE**  |**Opcjonalne** </br> Użyj tego przełącznika, jeśli chcesz usunąć zawartość z punktu dystrybucji. Zostanie wyświetlony monit, przed usunięciem zawartości. </br></br> Gdy ta opcja nie jest używany, narzędzie rejestruje wyniki dotyczące zawartości zostaną usunięte, ale nie powoduje usunięcia zawartości z punktu dystrybucji. </br></br> Przykład: ***/ Delete server1.contoso.com /dp ContentLibraryCleanup.exe*** |
| **/q**       |**Opcjonalne** </br> Ta opcja uruchamia narzędzie w trybie cichym, pomija wszystkie monity (na przykład z monitami, aby usunąć zawartość), a nie automatycznie otworzyć plik dziennika. </br></br> Przykład: ***ContentLibraryCleanup.exe /q /dp serwer1.contoso.com*** |
| **/dp &lt;FQDN punktów dystrybucji >**  | **Wymagane** </br> Określ w pełni kwalifikowaną nazwę (FQDN) punktu dystrybucji, które chcesz wyczyścić. </br></br> Przykład:  ***ContentLibraryCleanup.exe /dp serwer1.contoso.com***|
| **/PS &lt;lokacji głównej nazwy FQDN >**       | **Opcjonalne** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br>Narzędzie łączy do nadrzędnej lokacji głównej do wykonywania kwerend do SMS_Provider. Pozwalają one zapytania narzędzie określają zawartość powinna być w punkcie dystrybucji, ale pozwala wykryć zawartość, która jest oddzielona i może zostać usunięta. To połączenie nadrzędnej lokacji głównej muszą być wprowadzane do punktów dystrybucji w lokacji dodatkowej, ponieważ wymagane szczegóły nie są dostępne bezpośrednio z lokacji dodatkowej.</br></br> Określ nazwę FQDN należącą do punktu dystrybucji lokacji głównej lub podstawowej nadrzędnego elementu nadrzędnego, gdy punkt dystrybucji znajduje się w lokacji dodatkowej. </br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;kod lokacji głównej >**  | **Opcjonalne** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ kod lokacji w lokacji głównej, należącego do punktu dystrybucji lub nadrzędnej lokacji głównej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej.</br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Opcjonalne** </br> Określ lokalizację, w której narzędzie zapisuje plik dziennika. Może to być lokalny lub w sieci, należy udostępnić.</br></br> Gdy ta opcja nie jest używana, plik dziennika znajduje się w folderze tymczasowym użytkownika, na komputerze, na którym działa narzędzie.</br></br> Przykład dysku lokalnym: ***/ ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Przykład z udziału sieciowego: ***/ Log server1.contoso.com /dp ContentLibraryCleanup.exe \\ &lt;udostępnianie >\&< folder >***|
