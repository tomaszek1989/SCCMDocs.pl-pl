---
title: Importuj dane konfiguracji | Dokumentacja firmy Microsoft
description: "Importuje dane konfiguracji, jeśli jest zawarty w formacie pliku cabinet zgodna obsługiwane schematu Usługa język modelowania."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 60d0642618a3074fc50a848f1189f4d6559ca916
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>Importowanie danych konfiguracji z programem System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Oprócz tworzenia linie bazowe konfiguracji i pozycje konfiguracji w konsoli programu System Center Configuration Manager, można zaimportować konfiguracja danych, jeśli jest on zawarty w pliku cab format pliku i jest zgodna obsługiwane schematu usługi modelowania języka (SML). Można zaimportować danych konfiguracji z:  

-   Dane konfiguracji najlepszych rozwiązań (pakiety konfiguracyjne) pobrane z witryny firmy Microsoft lub witryn innych dostawców oprogramowania.  

-   Dane konfiguracyjne, które zostały wyeksportowane z programu System Center 2012 Configuration Manager, a następnie.  

-   Dane konfiguracyjne, które zostało utworzone zewnętrznie i który jest zgodny ze schematem SML.  

 Aby uzyskać przykładowy pakiet konfiguracyjny ułatwiający zarządzanie zgodnością ról serwera lokacji programu System Center 2012 Configuration Manager, zobacz [pakiet konfiguracyjny programu System Center 2012 Configuration Manager](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all).  

W przypadku importowania linii bazowej konfiguracji niektóre lub wszystkie elementy konfiguracji, do których odwołania zawiera linia bazowa konfiguracji, mogą również zostać dołączone do pliku cabinet. Podczas procesu importowania programu Configuration Manager weryfikuje, czy wszystkie elementy konfiguracji, które są wywoływane w linii bazowej konfiguracji albo znajdują się również w pliku cabinet lub już istnieje w lokacji programu Configuration Manager. Proces importowania kończy się niepowodzeniem, jeśli zostanie próba zaimportowania linii bazowej konfiguracji, który odwołuje się do danych konfiguracji, który nie może zlokalizować programu Configuration Manager.  

Proces importowania może zakończyć się niepowodzeniem także w następujących scenariuszach:  

-   Dane konfiguracyjne odwołuje się do danych konfiguracji programu Configuration Manager nie może zlokalizować w swojej bazie danych lub w samym pliku cabinet.  

-   Dane konfiguracji jest już obecny w bazie danych programu Configuration Manager o tej samej nazwie i wersji danych konfiguracji, ale różni się numer wersji zawartości.  

-   Dane konfiguracji jest już obecny w bazie danych programu Configuration Manager za pomocą tej samej wersji zawartości, ale obliczenia mieszania identyfikuje go jako różne.  

-   Nowsza wersja danych konfiguracji o tej samej nazwie jest już obecny lub niedawno został usunięty w bazie danych programu Configuration Manager.  

-   W hierarchii wielu lokacji programu Configuration Manager dane konfiguracyjne pierwotnie zaimportowanych z lokacji nadrzędnej. Należy zaktualizować je z tej samej lokacji, a nie z lokacji podrzędnej.  

### <a name="import-configuration-data"></a>Importowanie danych konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **elementy konfiguracji** lub **linie bazowe konfiguracji**
2.  W **Home** w karcie **Utwórz** , kliknij przycisk **importu danych konfiguracyjnych**.  
3.  Na stronie **Wybierz pliki** w **Kreatorze importowania danych konfiguracyjnych**kliknij przycisk **Dodaj**, a następnie w oknie dialogowym **Otwieranie** wybierz pliki cab, które chcesz zaimportować.  
4.  Wybierz **Utwórz nową kopię zaimportowanych linii bazowych i elementów konfiguracji** pole wyboru, jeśli chcesz konfiguracji importowanych danych można edytować w konsoli programu Configuration Manager.  
5.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

Wyświetla dane konfiguracyjne importowanych w **ustawień zgodności** węzła **zasoby i zgodność** obszaru roboczego.  

