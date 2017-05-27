---
title: Klaster programu SQL Server | Dokumentacja firmy Microsoft
description: "Użyj klastra programu SQL Server do obsługi bazy danych lokacji programu System Center Configuration Manager. Zawiera informacje na temat obsługiwanych opcji."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ce0d7fc5f3d1812c4d62e551661c0ef89707567b
ms.openlocfilehash: 53f119bbb1f8827a9c23c8b747840350bbb92790
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>Używanie klastra programu SQL Server dla bazy danych lokacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Klastra programu SQL Server można użyć do obsługi bazy danych lokacji programu System Center Configuration Manager. Baza danych lokacji jest jedyną rolą systemu lokacji obsługiwaną w klastrze programu SQL Server.  

> [!IMPORTANT]  
>  Pomyślne konfigurowanie klastrów programu SQL Server zależy od dokumentacji i procedur omówionych w bibliotece dokumentacji programu SQL Server.  

 Klastra można zapewnić obsługę pracy awaryjnej i zwiększyć niezawodność bazy danych lokacji. Jednak nie zawierają dodatkowe przetwarzanie ani korzyści z równoważenia obciążenia. W rzeczywistości pogorszenie wydajności mogą wystąpić, ponieważ serwer lokacji musi znaleźć aktywnego węzła klastra programu SQL Server, zanim nawiąże połączenie bazy danych lokacji.  

 Przed zainstalowaniem programu Configuration Manager, należy przygotować klastra programu SQL Server do obsługi programu Configuration Manager. (Zobacz wymagania wstępne w dalszej części tej sekcji).  

 Składnik zapisywania usługi kopiowania woluminów w tle systemu Windows podczas instalacji programu Configuration Manager instaluje się na każdym fizycznym węźle komputera klastra systemu Microsoft Windows Server. Obejmuje to obsługę **kopii zapasowej serwera lokacji** zadań konserwacji.  

 Po zainstalowaniu lokacji programu Configuration Manager sprawdza zmiany do węzła klastra co godzinę. Program Configuration Manager automatycznie zarządza zmiany, które są wykrył, że wpływu na instalacje składników programu Configuration Manager (takie jak tryb pracy awaryjnej węzła lub dodanie nowego węzła do klastra programu SQL Server).  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>Obsługiwane opcje dotyczące korzystania z klastra pracy awaryjnej programu SQL Server

Obsługiwane są następujące opcje dla klastrów pracy awaryjnej programu SQL Server służący jako baza danych lokacji:

-   Pojedyncze wystąpienie klastra  

-   Konfiguracja z wieloma wystąpieniami  

-   Wiele aktywnych węzłów  

-   Nazwane lub domyślnego wystąpienia  

Należy zwrócić uwagę na następujące wymagania wstępne:  

-   Baza danych lokacji musi znajdować się poza serwerem lokacji. (Klaster nie może zawierać serwera systemu lokacji).  

-   Należy dodać konto komputera serwera lokacji do lokalnej grupy administratorów każdego serwera w klastrze.  

-   Do obsługi uwierzytelniania Kerberos, **TCP/IP** protokołu komunikacji sieciowej musi być włączona dla połączenia sieciowego każdego węzła klastra programu SQL Server. **Nazwane potoki** nie są wymagane, ale można ich używać do rozwiązywania problemów z uwierzytelnianiem Kerberos. Ustawienia protokołu są konfigurowane w **programu SQL Server Configuration Manager**w obszarze **konfigurację sieci programu SQL Server**.  

-   Jeśli używana jest infrastruktura PKI, zobacz wymagania dotyczące certyfikatu PKI dla programu Configuration Manager dla konkretnych wymogach certyfikatu obowiązujących używania klastra programu SQL Server dla bazy danych lokacji.  

Należy wziąć pod uwagę następujące ograniczenia:  

-   **Instalacja i konfiguracja:**  

    -   W lokacjach dodatkowych nie można używać klastra programu SQL Server.  

    -   W przypadku określenia klastra programu SQL Server nie można określić innych niż domyślne lokalizacji plików dla bazy danych lokacji.  

-   **Dostawca programu SMS:**  

    -   Instalowanie wystąpienia dostawcy programu SMS w klastrze programu SQL Server lub na komputerze z uruchomionym węzłem klastrowanego programu SQL Server nie jest obsługiwane.  

-   **Opcje replikacji danych:**  

    -   W przypadku używania **widoków rozproszonych**, nie można używać klastra programu SQL Server do obsługi bazy danych lokacji.  

-   **Tworzenie kopii zapasowej i odzyskiwanie:**  

    -   Menedżer konfiguracji nie obsługuje kopii zapasowej Data Protection Manager (DPM) dla klastra programu SQL Server używającego wystąpienia nazwanego. Jednak obsługuje kopii zapasowych programu DPM na klastrze programu SQL Server, który używa domyślnego wystąpienia programu SQL Server.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>Przygotowanie klastrowanego wystąpienia programu SQL Server dla bazy danych lokacji  

Oto główne zadania do wykonania w celu przygotowania do bazy danych:

-   Utwórz wirtualny klaster programu SQL Server na potrzeby hostowania bazy danych lokacji w istniejącym środowisku klastra systemu Windows Server. Konkretne kroki do instalowania i konfigurowania klastra programu SQL Server zobacz dokumentację specyficzne dla używanej wersji programu SQL Server. Na przykład, jeśli używasz programu SQL Server 2008 R2, zobacz [Instalowanie klastra pracy awaryjnej programu SQL Server 2008 R2](http://go.microsoft.com/fwlink/p/?LinkId=240231).  

-   Na każdym komputerze w klastrze programu SQL Server należy umieścić plik w folderze głównym każdego dysku, na którym nie ma programu Configuration Manager do zainstalowania składników lokacji. Plik powinien mieć nazwę **NO_SMS_ON_DRIVE.SMS**. Domyślnie program Configuration Manager instaluje pewne składniki w każdym fizycznym węźle do obsługi operacji, takich jak kopii zapasowej.  

-   Dodaj konto komputera serwera lokacji do grupy **Administratorzy lokalni** każdego komputera węzła klastra systemu Windows Server.  

-   W wirtualnym wystąpieniu programu SQL Server, należy przypisać **sysadmin** roli programu SQL Server do konta użytkownika, który będzie uruchamiany Instalator programu Configuration Manager.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>Aby zainstalować nową lokację przy użyciu klastrowanego programu SQL Server  
 Aby zainstalować lokacji, która korzysta z bazy danych lokacji klastrowane, uruchom Instalatora programu Configuration Manager po procesie normalnej instalacji lokacji, z następującą modyfikacją:  

-   Na stronie **Informacje o bazie danych** określ nazwę wirtualnego wystąpienia klastra programu SQL Server, które ma hostować bazę danych lokacji. Wystąpienie wirtualne zastępuje nazwę komputera, na którym działa program SQL Server.  

    > [!IMPORTANT]  
    >  Musisz wprowadzić nazwę wirtualnego wystąpienia klastra programu SQL Server, a nie wirtualną nazwę systemu Windows Server utworzoną przez klaster systemu Windows Server. Jeśli używasz wirtualną nazwę systemu Windows Server, bazy danych lokacji instaluje się na lokalnym dysku twardym aktywnego węzła klastra systemu Windows Server. Uniemożliwia to pracę w trybie failover w przypadku awarii tego węzła.  

