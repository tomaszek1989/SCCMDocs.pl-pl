---
title: "Narzędzie do biblioteki zawartości oczyszczania | Dokumentacja firmy Microsoft"
description: "Usuń oddzielone zawartości nie są już skojarzone z wdrożeniem programu System Center Configuration Manager za pomocą narzędzia Oczyszczanie biblioteki zawartości."
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 32f7fc4ef9c8e8d3c2ec8eeaf9a3174bad992ffb
ms.openlocfilehash: 76e6772bdd5cbd32d525e728f6ebc988b045da78
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>Narzędzie oczyszczania zawartości biblioteki programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Począwszy od wersji 1702, można użyć narzędzia wiersza polecenia (**ContentLibraryCleanup.exe**) aby usunąć zawartość, która jest już skojarzony z dowolnego pakietu lub aplikacji z punktu dystrybucji (oddzielony zawartości). To narzędzie jest wywoływana narzędzia Oczyszczanie biblioteki zawartości i zastępuje starsze wersje podobne narzędzia opublikowany dla wcześniejszej produktów Configuration Manager.  

Narzędzie dotyczy wyłącznie zawartość w punkcie dystrybucji można określić po uruchomieniu narzędzia. Narzędzie nie usuwa zawartość z biblioteki zawartości na serwerze lokacji.

Można znaleźć **ContentLibraryCleanup.exe** w *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* folder na serwerze lokacji w centralnej lokacji administracyjnej lub lokacji głównej.

## <a name="requirements"></a>Wymagania  
 Narzędzie można uruchamiać tylko dla pojedynczego punktu dystrybucji w czasie.  
 - Można ją uruchamiać bezpośrednio na komputerze, który obsługuje punkt dystrybucji, które chcesz wyczyścić lub zdalnie z innego serwera.
 - Konto użytkownika, który uruchomił narzędzie musi mieć uprawnienia bezpośrednie administracji opartej na rolach, które są równe pełny Administrator w hierarchii programu Configuration Manager. Narzędzie nie działa, gdy konto otrzymuje uprawnienia jako członek grupy zabezpieczeń systemu Windows z uprawnieniami pełnego dostępu administratora.

## <a name="modes-of-operation"></a>Tryby operacyjne
W następujących dwóch trybów można uruchomić narzędzie. Zaleca się uruchomienie narzędzia *symulacji* trybu, więc możesz przejrzeć wyniki, przed uruchomieniem narzędzia *usunąć tryb*:
  1.    **Tryb symulacji**:   
      Jeśli nie określisz **/delete** przełącznika, narzędzie działa w trybie symulacji i identyfikuje zawartość, do której zostaną usunięte z punktu dystrybucji.
   - Podczas pracy w tym trybie narzędzie nie usunie żadnych danych.
   - Informacje o zawartości, które zostałyby usunięte są zapisywane do pliku dziennika narzędzia, a nie monit o potwierdzenie każdej operacji usunięcia potencjalnych.  
      </br>   

  2. **Usuń tryb**:   
    Po uruchomieniu narzędzia z **/delete** przełącznika, narzędzie działa w trybie delete.

     - Podczas pracy w tym trybie, oddzielone zawartość, która znajduje się w punkcie dystrybucji określonego mogą zostać usunięte z biblioteki zawartości w punkcie dystrybucji.
     -     Przed usunięciem każdego pliku, musisz potwierdzić, że należy usunąć plik.  Możesz wybrać **Y** tak, **N** nie, lub **tak na wszystkie** Aby pominąć dalsze monity i usuń zawartość wszystkich oddzielone.  
     </br>

Po uruchomieniu narzędzia w trybie, automatycznie tworzy plik dziennika o nazwę, która zawiera tryb, który działa w nazwę punktu dystrybucji i daty i godziny operacji. Plik dziennika nawiązywane automatycznie po zakończeniu działania narzędzia.

Domyślnie plik dziennika zostanie zapisany w folderze tymczasowym konta użytkownika, który uruchomił narzędzie, na komputerze, na którym uruchomiono narzędzie. Można użyć **/log** przełącznikowi sieciowemu przekierowywanie pliku dziennika do innej lokalizacji, w tym udziale sieciowym.


## <a name="run-the-tool"></a>Uruchom narzędzie
Aby uruchomić narzędzie:
1. Otwórz wiersz polecenia administracyjne z folderu, który zawiera **ContentLibraryCleanup.exe**.  
2. Następnie wprowadź wiersz polecenia, który zawiera przełączników wiersza polecenia wymagane i opcjonalne przełączniki, którego chcesz użyć.

**Znany problem** po uruchomieniu narzędzia, gdy wdrażanie lub pakietu nie powiodło się lub jest w toku może zwrócony błąd podobnie do poniższego:
-  *System.InvalidOperationException: Ta biblioteka zawartości nie można oczyścić teraz ponieważ pakiet <packageID> nie jest w pełni zainstalowany.*

**Obejście problemu:** Brak. Narzędzie nie niezawodne identyfikować oddzielone pliki, gdy zawartość jest w toku lub nie udało się wdrożyć. W związku z tym narzędzie nie pozwoli do czyszczenia zawartości do momentu rozwiązania problemu.

### <a name="command-line-switches"></a>Przełączniki wiersza polecenia  
Następujące przełączniki wiersza polecenia można użyć w dowolnej kolejności.   

|Przełącznik|Szczegóły|
|---------|-------|
|**/ DELETE**  |**Opcjonalne** </br> Użyj tego przełącznika, jeśli chcesz usunąć zawartość z punktu dystrybucji. Zostanie wyświetlony monit, przed usunięciem zawartości. </br></br> Jeśli ten przełącznik nie jest używany, narzędzie rejestruje wyniki o tym, jaka zawartość zostaną usunięte, ale nie powoduje usunięcia zawartości z punktu dystrybucji. </br></br> Przykład: ***/ Delete server1.contoso.com /dp ContentLibraryCleanup.exe*** |
| **/q**       |**Opcjonalne** </br> Ten przełącznik uruchamia narzędzie w trybie cichym pomija wszystkie monity (np. z monitami, aby usunąć zawartość), a nie automatycznie otworzyć plik dziennika. </br></br> Przykład: ***ContentLibraryCleanup.exe /q /dp serwer1.contoso.com*** |
| **/dp &lt;FQDN punktu dystrybucji >**  | **Wymagane** </br> Podaj pełną nazwę domeny (FQDN) punktu dystrybucji, które chcesz wyczyścić. </br></br> Przykład:  ***ContentLibraryCleanup.exe /dp serwer1.contoso.com***|
| **/PS &lt;lokacji głównej nazwy FQDN >**       | **Opcjonalny** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br>Narzędzie łączy do nadrzędnej lokacji głównej do uruchamiania kwerend SMS_Provider. Pozwalają one zapytania narzędzie określić zawartość powinna być w punkcie dystrybucji, można określić zawartość, która jest oddzielona i może zostać usunięta. To połączenie do nadrzędnej lokacji głównej musi podlegać dla punktów dystrybucji w lokacji dodatkowej, ponieważ wymagane szczegóły nie są dostępne bezpośrednio z lokacji dodatkowej.</br></br> Określ nazwę FQDN punktu dystrybucji należy do lokacji głównej lub elementu nadrzędnego głównej nadrzędnej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej. </br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;kod lokacji głównej >**  | **Opcjonalny** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ kod lokacji punktu dystrybucji należy do lokacji głównej lub z nadrzędnej lokacji głównej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej.</br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Opcjonalne** </br> Określ lokalizację, w której narzędzie zapisuje plik dziennika. Może to być lokalny lub w sieci udział.</br></br> Kiedy ten przełącznik nie jest używany, plik dziennika jest umieszczany w folderze tymczasowym użytkownika na komputerze, na którym działa.</br></br> Przykład dysku lokalnego: ***/ ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Przykład udziału sieciowego: ***/ Log server1.contoso.com /dp ContentLibraryCleanup.exe \\ &lt;udostępnić >\&< folder >***|

