---
title: "Synchronizowanie aktualizacji bez połączenia internetowego "
titleSuffix: Configuration Manager
description: "Uruchom synchronizację aktualizacji oprogramowania w punkcie aktualizacji oprogramowania najwyższego poziomu jest odłączony od Internetu."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 1a997c30-8e71-4be5-89ee-41efb2c8d199
ms.openlocfilehash: e10c3b1695e3ce652559242b0248e7dc818741b7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="synchronize-software-updates-from-a-disconnected-software-update-point"></a>Synchronizowanie aktualizacji oprogramowania z odłączonego punktu aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Aby zsynchronizować metadane aktualizacji oprogramowania, gdy punkt aktualizacji w lokacji najwyższego poziomu jest odłączony od Internetu, należy użyć funkcji eksportu i importu. Jako źródło synchronizacji można wybrać istniejący serwer WSUS nie znajduje się w hierarchii programu Configuration Manager. Ten temat zawiera informacje o tym, jak używać funkcji eksportowania i importowania narzędzia WSUSUtil.  

 Aby eksportować i importować metadane aktualizacji oprogramowania, należy wyeksportować odpowiednie metadane z bazy danych programu WSUS na określony serwer eksportu, skopiować lokalnie przechowywane pliki postanowień licencyjnych do punktu aktualizacji oprogramowania, a następnie zaimportować metadane aktualizacji do bazy danych programu WSUS w odłączonym punkcie aktualizacji oprogramowania.  

 Aby określić serwer eksportu, do którego mają być eksportowane metadane aktualizacji oprogramowania, zapoznaj się z informacjami w poniższej tabeli.  

|Punkt aktualizacji oprogramowania|Nadrzędne źródło aktualizacji dla podłączonych punktów aktualizacji oprogramowania|Serwer eksportu dla odłączonego punktu aktualizacji oprogramowania|  
|---------------------------|-----------------------------------------------------------------|------------------------------------------------------------|  
|Centralna lokacja administracyjna|Microsoft Update (Internet)<br /><br /> Istniejący serwer WSUS|Wybierz serwer programu WSUS, który jest synchronizowany z Microsoft Update przy użyciu klasyfikacji aktualizacji oprogramowania, produktów i języków wymaganych w środowisku programu Configuration Manager.|  
|Autonomiczna lokacja główna|Microsoft Update (Internet)<br /><br /> Istniejący serwer WSUS|Wybierz serwer programu WSUS, który jest synchronizowany z Microsoft Update przy użyciu klasyfikacji aktualizacji oprogramowania, produktów i języków wymaganych w środowisku programu Configuration Manager.|  

 Przed rozpoczęciem eksportowania należy sprawdzić, czy synchronizacja aktualizacji oprogramowania została ukończona na wybranym serwerze eksportu, aby mieć pewność, że zsynchronizowano metadane najnowszych aktualizacji oprogramowania. Aby sprawdzić, czy synchronizacja aktualizacji oprogramowania zakończyła się powodzeniem, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-verify-that-software-updates-synchronization-has-completed-successfully-on-the-export-server"></a>Aby sprawdzić, czy synchronizacja aktualizacji oprogramowania zakończyła się powodzeniem na serwerze eksportu  

1.  Otwórz konsolę administracyjną programu WSUS i połącz się z bazą danych programu WSUS na serwerze eksportu.  

2.  W konsoli administracyjnej programu WSUS kliknij pozycję **Synchronizacje**. W okienku wyników zostanie wyświetlona lista prób synchronizacji aktualizacji oprogramowania.  

3.  Znajdź w okienku wyników ostatnią próbę synchronizacji aktualizacji oprogramowania i sprawdź, czy zakończyła się pomyślnie.  

> [!IMPORTANT]  
>  Aby wyeksportować metadane aktualizacji oprogramowania, należy uruchomić narzędzie WSUSUtil lokalnie na serwerze eksportu, a w przypadku importowania tych metadanych — również na serwerze odłączonego punktu aktualizacji oprogramowania Ponadto użytkownik uruchamiający narzędzie WSUSUtil musi należeć do lokalnej grupy administratorów na każdym serwerze.  

## <a name="export-process-for-software-updates"></a>Proces eksportowania aktualizacji oprogramowania  
 Proces eksportowania aktualizacji oprogramowania obejmuje dwa podstawowe kroki: kopiowanie lokalnie przechowywanych plików postanowień licencyjnych do odłączonego punktu aktualizacji oprogramowania oraz eksportowanie metadanych aktualizacji oprogramowania z bazy danych programu WSUS na serwer eksportu.  

 Aby skopiować lokalne metadane postanowień licencyjnych do odłączonego punktu aktualizacji oprogramowania, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-copy-local-files-from-the-export-server-to-the-disconnected-software-update-point-server"></a>Aby skopiować pliki lokalne z serwer eksportu na serwer odłączonego punktu aktualizacji oprogramowania  

1.  Na serwerze eksportu przejdź do folderu, w którym są przechowywane aktualizacje oprogramowania i powiązane z nimi postanowienia licencyjne. Serwer programu WSUS domyślnie przechowuje pliki w folderze <*dysk_instalacyjny_WSUS*>\WSUS\WSUSContent\\\, gdzie *dysk_instalacyjny_WSUS* to dysk, na którym zainstalowano program WSUS.  

2.  Skopiuj wszystkie pliki i foldery z tej lokalizacji do folderu WSUSContent na serwerze odłączonego punktu aktualizacji oprogramowania.  

 Aby wyeksportować metadane aktualizacji oprogramowania z bazy danych programu WSUS na serwer eksportu, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-export-software-updates-metadata-from-the-wsus-database-on-the-export-server"></a>Aby wyeksportować metadane aktualizacji oprogramowania z bazy danych programu WSUS na serwer eksportu  

1.  W wierszu polecenia na serwerze eksportu przejdź do folderu, który zawiera plik WSUSutil.exe. Domyślnie to narzędzie znajduje się w folderze %*ProgramFiles*%\Update Services\Tools. Jeśli na przykład narzędzie znajduje się w domyślnej lokalizacji, wpisz polecenie **cd %ProgramFiles%\Update Services\Tools**.  

2.  Aby wyeksportować metadane aktualizacji oprogramowania do pliku pakietu, wpisz następujące polecenie:  

     **wsusutil.exe export**  *nazwa_pakietu*  *plik_dziennika*  

     Na przykład:  

     **wsusutil.exe export eksport.cab eksport.log**  

     Ten format można podsumować w następujący sposób: WSUSutil.exe występuje opcja eksportowania, nazwa pliku .cab eksportu utworzonego w ramach operacji eksportowania oraz nazwa pliku dziennika. Narzędzie WSUSutil.exe eksportuje metadane z serwera eksportu i tworzy plik dziennika dotyczący tej operacji.  

    > [!NOTE]  
    >  Pakiet (plik .cab) i nazwa pliku dziennika muszą być unikatowe w bieżącym folderze.  

3.  Przenieś pakiet eksportu do folderu zawierającego narzędzie WSUSutil.exe na serwerze importu programu WSUS.  

    > [!NOTE]  
    >  Przeniesienie pakietu do tego folderu ułatwia proces importowania. Pakiet można przenieść do dowolnej lokacji, do której serwer importu ma dostęp, a następnie określić tę lokalizację po uruchomieniu narzędzia WSUSutil.exe.  

## <a name="import-software-updates-metadata"></a>Importowanie metadanych aktualizacji oprogramowania  
 Aby zaimportować metadane aktualizacji oprogramowania z serwera eksportu do odłączonego punktu aktualizacji oprogramowania, wykonaj czynności opisane w poniższej procedurze.  

> [!IMPORTANT]  
>  Nie należy importować żadnych wyeksportowanych danych z niezaufanego źródła. Zaimportowanie zawartości z niezaufanego źródła może spowodować naruszenie zabezpieczeń serwera programu WSUS.  

#### <a name="to-import-metadata-to-the-database-of-the-import-server"></a>Aby zaimportować metadane do bazy danych serwera importu  

1.  W wierszu polecenia na serwerze importu programu WSUS przejdź do folderu, który zawiera plik WSUSutil.exe. Domyślnie to narzędzie znajduje się w folderze %*ProgramFiles*%\Update Services\Tools.  

2.  Wpisz następujące polecenie:  

     **wsusutil.exe import**  *nazwa_pakietu*  *plik_dziennika*  

     Na przykład:  

     **wsusutil.exe import eksport.cab import.log**  

     Ten format można podsumować w następujący sposób: WSUSutil.exe występuje polecenie importowania, nazwa pliku pakietu (.cab) utworzonego w ramach operacji eksportowania, ścieżka do pliku pakietu, jeśli znajduje się w innym folderze, a nazwa pliku dziennika. Narzędzie WSUSutil.exe importuje metadane z serwera eksportu i tworzy plik dziennika dotyczący tej operacji.  

## <a name="next-steps"></a>Następne kroki
Po zsynchronizowaniu aktualizacji oprogramowania po raz pierwszy lub po dostępnych nowych klasyfikacji lub produktów, należy [konfigurowanie nowych klasyfikacji i produktów](configure-classifications-and-products.md) synchronizowania aktualizacji oprogramowania do nowych kryteriów.

Po wykonaniu zsynchronizować aktualizacje oprogramowania z kryteriami, które są potrzebne [Zarządzanie ustawieniami aktualizacji oprogramowania](manage-settings-for-software-updates.md).  
