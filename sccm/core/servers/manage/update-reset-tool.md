---
title: "Narzędzie do resetowania aktualizacji | Dokumentacja firmy Microsoft"
description: "Narzędzie aktualizacji resetowania aktualizacji w konsoli programu System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25fa89d6-7e47-45a6-8f4e-70b77560fba6
caps.latest.revision: 0
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 1960f86e98a957559f379b9eeb6d293f7e4182e5
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="update-reset-tool"></a>Narzędzie resetowania aktualizacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*  


Począwszy od wersji 1706, lokacji głównej programu Configuration Manager i centralne Lokacje administracyjne obejmują Configuration Manager Zresetuj narzędzie aktualizacji, **CMUpdateReset.exe**. Narzędzie do Rozwiązywanie problemów w przypadku problemów z pobieraniem lub replikowanie aktualizacje w konsoli. Narzędzie znajduje się w ***\cd.latest\SMSSETUP\TOOLS*** folderów serwera lokacji.

Za pomocą tego narzędzia, z dowolną wersją current branch, który pozostaje w pomocy technicznej.

Użyj tego narzędzia, gdy [aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates) nie został jeszcze zainstalowany i jest w stanie niepowodzenia. Błąd oznacza, że pobierania aktualizacji w toku, ale zablokowane lub zbyt długiego czasu. Długi czas jest uważana za godziny dłużej niż historycznych oczekiwania dla pakietów aktualizacji podobne rozmiaru. Można też Niepowodzenie replikacji aktualizacji do podrzędnych lokacji głównych.  

Po uruchomieniu narzędzia jest uruchamiana dla aktualizacji, który określisz. Domyślnie narzędzie nie powoduje usunięcia pomyślnie zainstalowane lub pobrane aktualizacje.  

### <a name="prerequisites"></a>Wymagania wstępne
Konto, którego używasz do uruchamiania narzędzia musi mieć następujące uprawnienia:
-   **Odczyt** i **zapisu** uprawnień do bazy danych lokacji z centralnej lokacji administracyjnej i każdej lokacji głównej w hierarchii. Aby ustawić te uprawnienia, musisz dodać konto użytkownika jako element członkowski **db_datawriter** i **db_datareader** [stałych ról bazy danych](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles) w bazie danych programu Configuration Manager dla każdej lokacji. Narzędzie nie współdziała z lokacji dodatkowych.
-   **Administrator lokalny** w lokacji najwyższego poziomu w hierarchii.
-   **Administrator lokalny** na komputerze, który hostuje punkt połączenia usługi.

Potrzebny jest identyfikator GUID pakietu aktualizacji, który chcesz zresetować. Aby uzyskać identyfikator GUID:
  1.   W konsoli przejdź do **administracji** > **aktualizacje i obsługa**.
  2.   W okienku wyświetlania kliknij prawym przyciskiem myszy nagłówek kolumny (takich jak **stanu**), a następnie wybierz pozycję **identyfikator Guid pakietu** można dodać kolumny do wyświetlenia.
  3.   Kolumna zawiera obecnie identyfikator GUID pakietu aktualizacji.

> [!TIP]  
> Aby skopiować identyfikator GUID, wybierz wiersz dla pakietu aktualizacji, który chcesz przywrócić, a następnie użyj klawiszy CTRL + C, aby skopiować tego wiersza. Jeśli wybór skopiowanych wkleić do edytora tekstu, można następnie skopiować tylko identyfikator GUID używany jako parametr wiersza polecenia, po uruchomieniu narzędzia.

### <a name="run-the-tool"></a>Uruchom narzędzie    
Narzędzie musi działać w lokacji najwyższego poziomu w hierarchii.

Po uruchomieniu narzędzia umożliwia określenie parametrów wiersza polecenia:
  -   SQL Server w lokacji najwyższego poziomu w hierarchii.
  -   Nazwa bazy danych lokacji w lokacji najwyższego poziomu.
  -   Identyfikator GUID pakietu aktualizacji, które chcesz zresetować.

Na podstawie stanu aktualizacji, narzędzie identyfikuje dodatkowych serwerów wymaganych do uzyskania dostępu.   

Jeśli pakiet aktualizacji *post pobierania* stanu, narzędzie oczyszczania nie zapasowej pakietu. Opcjonalnie możesz wymusić usunięcie pomyślnie pobranej aktualizacji za pomocą parametru delete force (zobacz parametry wiersza polecenia w dalszej części tego tematu).

Po uruchomieniu narzędzia:
-   Jeśli pakiet został usunięty, uruchom ponownie usługę SMS_Executive w lokacji najwyższego poziomu. Następnie sprawdź, czy aktualizacje, należy ponownie pobrać pakiet.
-   Pakiet nie został usunięty, nie trzeba podejmować żadnych działań. Aktualizacja ponownie inicjuje i następnie ponowne uruchomienie replikacji lub instalacji.

**Parametry wiersza polecenia:**  

| Parametr        |Opis                 |  
|------------------|----------------------------|  
|**-S &lt;nazwa FQDN programu SQL Server w lokacji najwyższego poziomu >** | *Wymagane* <br> Określ nazwę FQDN programu SQL Server, który jest hostem bazy danych lokacji dla lokacji najwyższego poziomu w hierarchii.    |  
| **-D &lt;Nazwa bazy danych >**                        | *Wymagane* <br> Określ nazwę bazy danych lokacji najwyższego poziomu.  |  
| **-P &lt;identyfikator GUID pakietu >**                         | *Wymagane* <br> Określ identyfikator GUID pakietu aktualizacji, które chcesz zresetować.   |  
| **- &lt;Nazwa wystąpienia programu SQL Server >**             | *Opcjonalne* <br> Określ wystąpienie programu SQL Server, który jest hostem bazy danych lokacji. |
| **-FDELETE**                              | *Opcjonalne* <br> Wymuszanie usunięcia pomyślnie pobrany pakiet aktualizacji. |  
 **Przykłady:**  
 W typowym scenariuszu chcesz zresetować aktualizacji, która ma problemy z pobieraniem. Nazwa FQDN programu SQL serwerów jest *server1.fabrikam.com*, bazy danych lokacji jest *CM_XYZ*i pakietu, identyfikator GUID jest *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  Uruchom: ***CMUpdateReset.exe -S server1.fabrikam.com -D CM_XYZ 61F16B3C-F1F6-4F9F-8647-2A524B0C802C -P***

 W przypadku bardziej skrajne chcesz wymusić usunięcie pakietu aktualizacji powodować problemy. Nazwa FQDN programu SQL serwerów jest *server1.fabrikam.com*, bazy danych lokacji jest *CM_XYZ*i pakietu, identyfikator GUID jest *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  Uruchom: ***CMUpdateReset.exe - FDELETE -S server1.fabrikam.com -D CM_XYZ 61F16B3C-F1F6-4F9F-8647-2A524B0C802C -P***

