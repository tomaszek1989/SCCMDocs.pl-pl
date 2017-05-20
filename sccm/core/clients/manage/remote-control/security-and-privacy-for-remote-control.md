---
title: "Zachowania zabezpieczeń zdalnego sterowania | Dokumentacja firmy Microsoft"
description: "Uzyskaj informacje o zabezpieczeniach i prywatności dla zdalnego sterowania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 272ee86b-d3d9-4fd9-b5c4-73e490e1a1e4
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 03b8ede7fa4f4c02ffb551bb28fe2db234d39b12
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-remote-control-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera informacje o ochronie prywatności dla zdalnego sterowania w programie System Center 2012 Configuration Manager i zabezpieczeń.  

##  <a name="BKMK_Security_HardwareInventory"></a> Najlepsze rozwiązania dotyczące zdalnego sterowania  
 Podczas zarządzania komputerami klienckimi przy użyciu zdalnego sterowania należy stosować poniższe najlepsze rozwiązania w zakresie zabezpieczeń.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas nawiązywania połączenia z komputerem zdalnym nie należy kontynuować, jeśli używane jest uwierzytelnianie NTLM zamiast uwierzytelniania Kerberos.|Po Configuration Manager wykryje, że sesja zdalnego sterowania jest uwierzytelniany przy użyciu protokołu NTLM zamiast protokołu Kerberos, pojawi się monit, który ostrzega, że nie można zweryfikować tożsamości komputera zdalnego. Nie należy wtedy kontynuować sesji zdalnego sterowania. Protokół NTLM jest słabszym protokołem uwierzytelniania niż Kerberos i jest narażony na ataki metodą powtórzeń i personifikacji.|  
|Nie należy włączać udostępniania Schowka w przeglądarce zdalnego sterowania.|Schowek obsługuje obiekty, takie jak pliki wykonywalne i tekst, i może zostać użyty przez użytkownika na komputerze hosta podczas sesji zdalnego sterowania w celu uruchomienia programu na komputerze źródłowym.|  
|Podczas zdalnego administrowania komputerem nie należy wprowadzać haseł do kont uprzywilejowanych.|Hasło może zostać przechwycone przez oprogramowanie obserwujące wejście klawiatury. Jeśli program uruchomiony na komputerze klienckim jest innym programem niż zakłada użytkownik, program może przechwycić hasło. Gdy wymagane są konta i hasła, powinny one zostać wprowadzone przez użytkownika końcowego.|  
|Zablokuj klawiaturę i mysz podczas sesji zdalnego sterowania.|Jeśli Configuration Manager wykryje, że połączenie zdalnego sterowania jest zakończone, programu Configuration Manager automatycznie blokuje klawiatury i myszy tak, aby użytkownik nie może przejąć kontrolę nad sesji Otwórz zdalnego sterowania. Jednak wykrycie może nastąpić z opóźnieniem lub nie nastąpić, jeśli usługa zdalnego starowania zostanie zakończona.<br /><br /> Wybierz akcję **Zablokuj zdalną klawiaturę i mysz** w oknie **Sterowanie zdalne programem ConfigMgr** .|  
|Nie należy zezwalać użytkownikom na konfigurowanie ustawień zdalnego sterowania w programie Software Center.|Nie należy włączać ustawienia klienta **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center** , aby zapobiegać szpiegowaniu użytkowników.<br /><br /> To ustawienie jest na komputerze, a nie dla zalogowanego użytkownika.|  
|Włącz profil **Domena** zapory systemu Windows .|Włącz ustawienie klienta **Włącz zdalne sterowanie na klientach: Profile wyjątków zapory** , a następnie wybierz profil **Domena** zapory systemu Windows dla komputerów w intranecie.|  
|Jeśli wylogujesz się podczas sesji zdalnego sterowania i zalogujesz się jako inny użytkownik, to zanim odłączysz się od sesji zdalnego sterowania upewnij się, że nastąpiło wylogowanie.|Jeśli nie wylogujesz się w tym scenariuszu, sesja pozostanie otwarta.|  
|Nie przyznawaj użytkownikom praw administratora lokalnego.|Jeśli użytkownikom zostaną przyznane prawa administratora lokalnego, mogą oni przejąć kontrolę na sesją zdalnego sterowania lub naruszyć bezpieczeństwo Twoich poświadczeń.|  
|Użyj zasad grupy lub Configuration Manager do konfigurowania ustawień Pomocy zdalnej, ale nie oba.|Program Configuration Manager i zasad grupy służy do wprowadzania zmian w konfiguracji ustawień Pomocy zdalnej. Gdy zasady grupy są odświeżane na kliencie, proces jest domyślnie optymalizowany przez zmianę tylko tych zasad, które uległy zmianie na serwerze. Menedżer konfiguracji zmienia ustawienia w lokalnych zasadach zabezpieczeń, które nie mogą zostać zastąpione, chyba że jest wymuszone aktualizacji zasad grupy.<br /><br /> Ustawienie zasad w obu miejscach może prowadzić do niespójnych wyników. Wybierz jedną z tych metod, aby skonfigurować ustawienia pomocy zdalnej.|  
|Włącz ustawienie klienta **Monituj użytkownika o zezwolenie na zdalne sterowanie**.|Mimo że istnieją sposoby obejścia tego ustawienia klienta, które powoduje wyświetlenie monitu o potwierdzenie przez użytkownika sesji zdalnego sterowania, włącz to ustawienie, aby zmniejszyć prawdopodobieństwo szpiegowania podczas pracy nad poufnymi zadaniami.<br /><br /> Ponadto poinformuj użytkowników, aby weryfikowali nazwę konta wyświetlaną podczas sesji zdalnego sterowania i odłączyli się od sesji, jeśli podejrzewają, że konto nie ma autoryzacji.|  
|Ogranicz listę dopuszczonych podglądów.|Użytkownik nie musi mieć uprawnień administratora lokalnego, aby móc korzystać ze zdalnego sterowania.|  

### <a name="security-issues-for-remote-control"></a>Problemy z zabezpieczeniami dotyczące zdalnego sterowania  
 W przypadku zarządzania komputerami klienckimi przy użyciu zdalnego sterowania występują następujące problemy z zabezpieczeniami:  

-   Nie należy przyjmować, że komunikaty inspekcji zdalnego sterowania są wiarygodne.  

     Jeśli rozpoczniesz sesję zdalnego sterowania, a następnie zalogujesz się przy użyciu alternatywnych poświadczeń, komunikaty inspekcji będą wysyłane z pierwotnego konta, a nie z konta, które korzysta z alternatywnych poświadczeń.  

     Po skopiowaniu plików binarnych do zdalnego sterowania, zamiast instalowania konsoli programu Configuration Manager, a następnie uruchom zdalnego sterowania w wierszu polecenia nie są przesyłane komunikaty inspekcji.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Informacje dotyczące poufności zdalnego sterowania  
 Zdalne sterowanie pozwala wyświetlić aktywne sesje na komputerach klienckich programu Configuration Manager oraz potencjalnie wszystkie informacje przechowywane na tych komputerach. Domyślnie zdalne sterowanie nie jest włączone.  

 Mimo że można skonfigurować zdalne sterowanie, aby zapewnić wyraźne powiadomienie i uzyskać zgodę od użytkownika przed rozpoczęciem sesji zdalnego sterowania, umożliwia ono również monitorowanie użytkowników bez ich zgody lub świadomości. Można skonfigurować poziom dostępu Tylko wyświetlanie, aby nie można było wprowadzać żadnych zmian przy użyciu zdalnego sterowania, lub poziom Pełna kontrola. Konto połączonego administratora jest wyświetlane w sesji zdalnego sterowania, aby ułatwić użytkownikom identyfikację osób połączonych z ich komputerem.  

 Domyślnie programu Configuration Manager daje administratorom lokalnym uprawnienia grupy zdalnego sterowania.  

 Przed skonfigurowaniem zdalnego sterowania należy rozważyć wymagania dotyczące poufności.  

