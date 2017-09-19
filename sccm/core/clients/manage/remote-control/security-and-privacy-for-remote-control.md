---
title: "Zdalne sterowanie zabezpieczeń prywatności | Dokumentacja firmy Microsoft"
description: "Pobierz informacje o zabezpieczeniach i poufności zdalnego sterowania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 272ee86b-d3d9-4fd9-b5c4-73e490e1a1e4
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d2f12805017517db803bc7d1942aa1ea2d752ec7
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="security-and-privacy-for-remote-control-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera bezpieczeństwa i informacje o ochronie prywatności dla zdalnego sterowania w programie System Center 2012 Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Najlepsze rozwiązania dotyczące zdalnego sterowania  
 Podczas zarządzania komputerami klienckimi przy użyciu zdalnego sterowania należy stosować poniższe najlepsze rozwiązania w zakresie zabezpieczeń.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas nawiązywania połączenia z komputerem zdalnym nie należy kontynuować, jeśli używane jest uwierzytelnianie NTLM zamiast uwierzytelniania Kerberos.|Gdy program Configuration Manager wykryje, że sesja zdalnego sterowania jest uwierzytelniany przy użyciu protokołu NTLM zamiast protokołu Kerberos, zostanie wyświetlony monit z ostrzeżeniem, że nie można zweryfikować tożsamości komputera zdalnego. Nie należy wtedy kontynuować sesji zdalnego sterowania. Protokół NTLM jest słabszym protokołem uwierzytelniania niż Kerberos i jest narażony na ataki metodą powtórzeń i personifikacji.|  
|Nie należy włączać udostępniania Schowka w przeglądarce zdalnego sterowania.|Schowek obsługuje obiekty, takie jak pliki wykonywalne i tekst, i może zostać użyty przez użytkownika na komputerze hosta podczas sesji zdalnego sterowania w celu uruchomienia programu na komputerze źródłowym.|  
|Podczas zdalnego administrowania komputerem nie należy wprowadzać haseł do kont uprzywilejowanych.|Hasło może zostać przechwycone przez oprogramowanie obserwujące wejście klawiatury. Jeśli program uruchomiony na komputerze klienckim jest innym programem niż zakłada użytkownik, program może przechwycić hasło. Gdy wymagane są konta i hasła, powinny one zostać wprowadzone przez użytkownika końcowego.|  
|Zablokuj klawiaturę i mysz podczas sesji zdalnego sterowania.|Jeśli program Configuration Manager wykryje, że połączenie zdalnego sterowania zostało zakończone, programu Configuration Manager blokuje automatycznie klawiaturę i mysz, dzięki czemu użytkownik nie może przejąć kontrolę nad otwartą sesją zdalnego sterowania. Jednak wykrycie może nastąpić z opóźnieniem lub nie nastąpić, jeśli usługa zdalnego starowania zostanie zakończona.<br /><br /> Wybierz akcję **Zablokuj zdalną klawiaturę i mysz** w oknie **Sterowanie zdalne programem ConfigMgr** .|  
|Nie należy zezwalać użytkownikom na konfigurowanie ustawień zdalnego sterowania w programie Software Center.|Nie należy włączać ustawienia klienta **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center** , aby zapobiegać szpiegowaniu użytkowników.<br /><br /> To ustawienie jest na danym komputerze, nie zalogowanego użytkownika.|  
|Włącz profil **Domena** zapory systemu Windows .|Włącz ustawienie klienta **Włącz zdalne sterowanie na klientach: Profile wyjątków zapory** , a następnie wybierz profil **Domena** zapory systemu Windows dla komputerów w intranecie.|  
|Jeśli wylogujesz się podczas sesji zdalnego sterowania i zalogujesz się jako inny użytkownik, to zanim odłączysz się od sesji zdalnego sterowania upewnij się, że nastąpiło wylogowanie.|Jeśli nie wylogujesz się w tym scenariuszu, sesja pozostanie otwarta.|  
|Nie przyznawaj użytkownikom praw administratora lokalnego.|Jeśli użytkownikom zostaną przyznane prawa administratora lokalnego, mogą oni przejąć kontrolę na sesją zdalnego sterowania lub naruszyć bezpieczeństwo Twoich poświadczeń.|  
|Aby skonfigurować ustawienia pomocy zdalnej, ale nie oba na raz, należy użyć zasad grupy lub programu Configuration Manager.|Configuration Manager i zasad grupy służy do wprowadzania zmian w konfiguracji ustawień Pomocy zdalnej. Gdy zasady grupy są odświeżane na kliencie, proces jest domyślnie optymalizowany przez zmianę tylko tych zasad, które uległy zmianie na serwerze. Menedżer konfiguracji zmienia ustawienia w zasadach zabezpieczeń lokalnych, które nie mogą zostać zastąpione, jeśli wymuszono aktualizacji zasad grupy.<br /><br /> Ustawienie zasad w obu miejscach może prowadzić do niespójnych wyników. Wybierz jedną z tych metod, aby skonfigurować ustawienia pomocy zdalnej.|  
|Włącz ustawienie klienta **Monituj użytkownika o zezwolenie na zdalne sterowanie**.|Mimo że istnieją sposoby obejścia tego ustawienia klienta, które powoduje wyświetlenie monitu o potwierdzenie przez użytkownika sesji zdalnego sterowania, włącz to ustawienie, aby zmniejszyć prawdopodobieństwo szpiegowania podczas pracy nad poufnymi zadaniami.<br /><br /> Ponadto poinformuj użytkowników, aby weryfikowali nazwę konta wyświetlaną podczas sesji zdalnego sterowania i odłączyli się od sesji, jeśli podejrzewają, że konto nie ma autoryzacji.|  
|Ogranicz listę dopuszczonych podglądów.|Użytkownik nie musi mieć uprawnień administratora lokalnego, aby móc korzystać ze zdalnego sterowania.|  

### <a name="security-issues-for-remote-control"></a>Problemy z zabezpieczeniami dotyczące zdalnego sterowania  
 W przypadku zarządzania komputerami klienckimi przy użyciu zdalnego sterowania występują następujące problemy z zabezpieczeniami:  

-   Nie należy przyjmować, że komunikaty inspekcji zdalnego sterowania są wiarygodne.  

     Jeśli rozpoczniesz sesję zdalnego sterowania, a następnie zalogujesz się przy użyciu alternatywnych poświadczeń, komunikaty inspekcji będą wysyłane z pierwotnego konta, a nie z konta, które korzysta z alternatywnych poświadczeń.  

     Komunikaty inspekcji nie są wysyłane, jeśli należy skopiować pliki binarne zdalnego sterowania, zamiast instalowania konsoli programu Configuration Manager, a następnie uruchom zdalnego sterowania w wierszu polecenia.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Informacje dotyczące poufności zdalnego sterowania  
 Zdalne sterowanie umożliwia wyświetlanie aktywnych sesji na komputerach klienckich programu Configuration Manager i potencjalne wyświetlanie wszystkich informacji przechowywanych na tych komputerach. Domyślnie zdalne sterowanie nie jest włączone.  

 Mimo że można skonfigurować zdalne sterowanie, aby zapewnić wyraźne powiadomienie i uzyskać zgodę od użytkownika przed rozpoczęciem sesji zdalnego sterowania, umożliwia ono również monitorowanie użytkowników bez ich zgody lub świadomości. Można skonfigurować poziom dostępu Tylko wyświetlanie, aby nie można było wprowadzać żadnych zmian przy użyciu zdalnego sterowania, lub poziom Pełna kontrola. Konto połączonego administratora jest wyświetlane w sesji zdalnego sterowania, aby ułatwić użytkownikom identyfikację osób połączonych z ich komputerem.  

 Domyślnie program Configuration Manager uprawnienia administratorów lokalnych grupy zdalnego sterowania.  

 Przed skonfigurowaniem zdalnego sterowania należy rozważyć wymagania dotyczące poufności.  
