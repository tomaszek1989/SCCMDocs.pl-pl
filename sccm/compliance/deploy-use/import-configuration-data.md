---
title: Importowanie danych konfiguracji | Dokumentacja firmy Microsoft
description: "Importowanie danych konfiguracji, jeśli jest zawarty w formacie pliku cabinet i jest zgodna ze schematem obsługiwanych Service Modeling Language."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 60d0642618a3074fc50a848f1189f4d6559ca916
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>Importowanie danych konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Oprócz tworzenia linii bazowych konfiguracji i elementy konfiguracji w konsoli programu System Center Configuration Manager, można zaimportować konfigurację danych, jeśli jest on zawarty w pliku cabinet (cab) format pliku i są zgodne z obsługiwanym schematem usługi modelowania języka (SML). Można importować dane konfiguracji od:  

-   Dane konfiguracji najlepszych rozwiązań (pakiety konfiguracyjne) pobrane z witryny firmy Microsoft lub witryn innych dostawców oprogramowania.  

-   Dane konfiguracji, które zostały wyeksportowane z programu System Center 2012 Configuration Manager i nowszych.  

-   Dane konfiguracji, które zostały utworzone zewnętrznie, zgodne ze schematem SML.  

 Aby uzyskać przykładowy pakiet konfiguracyjny ułatwiający zarządzanie zgodnością ról serwera lokacji programu System Center 2012 Configuration Manager, zobacz [pakiet konfiguracyjny programu System Center 2012 Configuration Manager](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all).  

W przypadku importowania linii bazowej konfiguracji niektóre lub wszystkie elementy konfiguracji, do których odwołania zawiera linia bazowa konfiguracji, mogą również zostać dołączone do pliku cabinet. Podczas procesu importowania programu Configuration Manager weryfikuje, czy wszystkie elementy konfiguracji, do których odwołuje się linia bazowa konfiguracji są zawarte w pliku cabinet lub już istnieje w lokacji programu Configuration Manager. Proces importowania kończy się niepowodzeniem, jeśli próby zaimportowania linii bazowej konfiguracji, który odwołuje się do danych konfiguracji programu Configuration Manager nie można zlokalizować.  

Proces importowania może zakończyć się niepowodzeniem także w następujących scenariuszach:  

-   Dane konfiguracji odwołują się dane konfiguracji programu Configuration Manager nie można zlokalizować w swojej bazie danych lub w samym pliku cabinet.  

-   Dane konfiguracji jest już obecny w bazie danych programu Configuration Manager o tej samej nazwie i wersji danych konfiguracji, ale numer wersji zawartości różni się.  

-   Dane konfiguracji jest już obecny w bazie danych programu Configuration Manager o tej samej wersji zawartości, ale identyfikuje ją jako inne obliczania skrótu.  

-   Nowsza wersja danych konfiguracji o tej samej nazwie istnieje już lub została ostatnio usunięta w bazie danych programu Configuration Manager.  

-   W hierarchii wielu lokacji programu Configuration Manager dane konfiguracji pierwotnie została zaimportowana z lokacji nadrzędnej. Należy zaktualizować je z tej samej lokacji, a nie z lokacji podrzędnej.  

### <a name="import-configuration-data"></a>Importuj dane konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **elementy konfiguracji** lub **linii bazowych konfiguracji**
2.  W **Home** karcie **Utwórz** kliknij przycisk **Importuj dane konfiguracji**.  
3.  Na stronie **Wybierz pliki** w **Kreatorze importowania danych konfiguracyjnych**kliknij przycisk **Dodaj**, a następnie w oknie dialogowym **Otwieranie** wybierz pliki cab, które chcesz zaimportować.  
4.  Wybierz **Utwórz nową kopię zaimportowanych linii bazowych i elementów konfiguracji** pole wyboru, jeśli chcesz, aby zaimportowane dane konfiguracji można edytować w konsoli programu Configuration Manager.  
5.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

Zaimportowane dane konfiguracji wyświetla w **ustawień zgodności** węzła **zasoby i zgodność** obszaru roboczego.  
