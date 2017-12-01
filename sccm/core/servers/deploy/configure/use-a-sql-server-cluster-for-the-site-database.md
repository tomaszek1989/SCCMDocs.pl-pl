---
title: Klaster programu SQL Server
titleSuffix: Configuration Manager
description: "Używać klastra programu SQL Server do hostowania bazy danych lokacji programu System Center Configuration Manager. Zawiera informacje na temat opcje są obsługiwane."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: "10"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: ec6749548b8354177b8b2ba6efcbf7ffe98e2869
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>Używanie klastra programu SQL Server dla bazy danych lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 Klastra programu SQL Server służy do obsługi bazy danych lokacji programu System Center Configuration Manager. Baza danych lokacji jest jedyną rolą systemu lokacji obsługiwaną w klastrze programu SQL Server.  

> [!IMPORTANT]  
>  Pomyślne zestawu klastrów programu SQL Server korzysta z dokumentacji i procedur dostępnych w bibliotece dokumentacji programu SQL Server.  

 Klastra można zapewnić obsługę pracy awaryjnej i zwiększyć niezawodność bazy danych lokacji. Jednak nie zapewniają dodatkowego przetwarzania ani korzyści z funkcji równoważenia obciążenia. W rzeczywistości spadek wydajności może wystąpić, ponieważ zanim łączy się bazy danych lokacji z serwera lokacji musi najpierw odnaleźć aktywny węzeł klastra programu SQL Server.  

 Przed zainstalowaniem programu Configuration Manager, należy przygotować klastra programu SQL Server do obsługi programu Configuration Manager. (Zobacz wymagania wstępne w dalszej części tej sekcji).  

 Podczas instalacji programu Configuration Manager składnik zapisywania usługi kopiowania woluminów w tle systemu Windows jest instalowana na każdym fizycznym węźle komputera klastra systemu Microsoft Windows Server. W ten sposób realizowany **Utwórz kopię zapasową serwera lokacji** zadań konserwacji.  

 Po zainstalowaniu lokacji programu Configuration Manager sprawdza zmiany węzła klastra co godzinę. Menedżer konfiguracji automatycznie zarządza wszelkie zmiany, które zostały znalezione, które wpływają na instalacje składników programu Configuration Manager (na przykład węzła trybu failover, lub dodanie nowego węzła do klastra programu SQL Server).  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>Obsługiwane opcje używania klastra pracy awaryjnej programu SQL Server

Obsługiwane są następujące opcje dla klastrów trybu failover programu SQL Server używany jako bazy danych lokacji:

-   Klaster z pojedynczym wystąpieniem  

-   Konfiguracja z wieloma wystąpieniami  

-   Wiele aktywnych węzłów  

-   Nazwane lub domyślnego wystąpienia  

Należy zwrócić uwagę na następujące wymagania wstępne:  

-   Baza danych lokacji musi znajdować się poza serwerem lokacji. (Klaster nie może zawierać serwera systemu lokacji).  

-   Należy dodać konto komputera serwera lokacji do grupy Administratorzy lokalni każdego serwera w klastrze.  

-   Aby zapewnić obsługę uwierzytelniania Kerberos **TCP/IP** musi być włączony protokół komunikacji sieciowej dla połączenia sieciowego każdego węzła klastra programu SQL Server. **Nazwane potoki** nie są wymagane, ale można ich używać do rozwiązywania problemów z uwierzytelnianiem Kerberos. Ustawienia protokołu sieciowego są konfigurowane w **SQL Server Configuration Manager**w obszarze **konfigurację sieci programu SQL Server**.  

-   Jeśli korzystasz z infrastruktury kluczy publicznych, zobacz wymagania dotyczące certyfikatu PKI dla programu Configuration Manager dla konkretnych wymogach certyfikatu obowiązujących używania klastra programu SQL Server dla bazy danych lokacji.  

Należy wziąć pod uwagę następujące ograniczenia:  

-   **Instalacja i konfiguracja:**  

    -   W lokacjach dodatkowych nie można używać klastra programu SQL Server.  

    -   W przypadku określenia klastra programu SQL Server nie można określić innych niż domyślne lokalizacji plików dla bazy danych lokacji.  

-   **Dostawca programu SMS:**  

    -   Instalowanie wystąpienia dostawcy programu SMS w klastrze programu SQL Server lub na komputerze, który działa jako węzeł klastra programu SQL Server nie jest obsługiwane.  

-   **Opcje replikacji danych:**  

    -   Jeśli użyjesz **widoków rozproszonych**, nie można używać klastra programu SQL Server do hostowania bazy danych lokacji.  

-   **Tworzenie kopii zapasowej i odzyskiwanie:**  

    -   Dla klastra programu SQL Server używającego wystąpienia nazwanego programu Configuration Manager nie obsługuje tworzenia kopii zapasowej Data Protection Manager (DPM). Jednak obsługuje kopii zapasowych programu DPM na klastrze programu SQL Server, który korzysta z domyślnego wystąpienia programu SQL Server.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>Przygotowanie klastrowanego wystąpienia programu SQL Server dla bazy danych lokacji  

Poniżej przedstawiono główne zadania do wykonania w celu przygotowania bazy danych lokacji:

-   Utwórz wirtualny klaster programu SQL Server na potrzeby hostowania bazy danych lokacji w istniejącym środowisku klastra systemu Windows Server. Określone kroki instalowania i konfigurowania klastra programu SQL Server w dokumentacji danej wersji programu SQL Server. Na przykład, jeśli używasz programu SQL Server 2008 R2, zobacz [Instalowanie klastra pracy awaryjnej programu SQL Server 2008 R2](http://go.microsoft.com/fwlink/p/?LinkId=240231).  

-   Na każdym komputerze w klastrze programu SQL Server możesz umieścić plik w folderze głównym każdego dysku, na których nie chcesz instalować składników lokacji program Configuration Manager. Plik powinien mieć nazwę **NO_SMS_ON_DRIVE.SMS**. Domyślnie program Configuration Manager instaluje pewne składniki w każdym fizycznym węźle do obsługi operacji, takich jak kopii zapasowej.  

-   Dodaj konto komputera serwera lokacji do grupy **Administratorzy lokalni** każdego komputera węzła klastra systemu Windows Server.  

-   W wirtualnym wystąpieniu programu SQL Server, należy przypisać **sysadmin** roli programu SQL Server do konta użytkownika, który zostanie uruchomiony Instalator programu Configuration Manager.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>Aby zainstalować nową lokację przy użyciu klastrowanego programu SQL Server  
 Aby zainstalować lokację, która korzysta z klastrowanej bazy danych lokacji, uruchom Instalatora programu Configuration Manager po zakończeniu procesu zwykłej instalacji lokacji, z następującą modyfikacją:  

-   Na stronie **Informacje o bazie danych** określ nazwę wirtualnego wystąpienia klastra programu SQL Server, które ma hostować bazę danych lokacji. Wystąpienie wirtualne zastępuje nazwę komputera, na którym działa program SQL Server.  

    > [!IMPORTANT]  
    >  Musisz wprowadzić nazwę wirtualnego wystąpienia klastra programu SQL Server, a nie wirtualną nazwę systemu Windows Server utworzoną przez klaster systemu Windows Server. Jeśli użyjesz wirtualnej nazwy systemu Windows Server, bazy danych lokacji są instalowane na lokalnym dysku twardym aktywnego węzła klastra systemu Windows Server. Uniemożliwia to pracę w trybie failover w przypadku awarii tego węzła.  
