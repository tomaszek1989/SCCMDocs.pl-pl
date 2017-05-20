---
title: "Klient zarządzania podstawy | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zadań uruchamianych na zarządzanie klientami programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86b90b8e591e1ae4f58cb361a5e544db6b09cce1
ms.openlocfilehash: 0fee4f4ba462e59859ac93c4218b67cb26bdd6f6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>Podstawy zadań zarządzania klientami dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zainstalowaniu klientów programu System Center Configuration Manager, istnieje kilka zadań uruchamianych w celu zarządzania klientami.  Niektóre zadania są uruchamiane z konsoli programu Configuration Manager. Inne zadania są uruchamiane z aplikacji klienckich programu Configuration Manager. Aplikacja klienta programu Configuration Manager jest zainstalowany w oprogramowaniu klienckim programu Configuration Manager.

## <a name="configuration-manager-console-tasks"></a>Zadania konsoli programu Configuration Manager
 W konsoli programu Configuration Manager można wykonywać różne zadania zarządzania klientami:  

-   Wdrażanie aplikacji, aktualizacji oprogramowania, skryptów konserwacji i systemów operacyjnych. Skonfiguruj instalację dla określonej daty i godziny, udostępnić oprogramowanie dla użytkowników do instalowania na żądanie lub konfigurować aplikacje przeznaczone do odinstalowania.  

-   Poprawa ochrony komputerów przed złośliwym oprogramowaniem i zagrożeniami bezpieczeństwa oraz powiadamianie o wykryciu problemów.  

-   Definiowanie ustawień konfiguracji klienta, które chcesz monitorować, a Rozwiązywanie problemów w przypadku niezgodności.  

-   Zbieranie informacji o spisie sprzętu i oprogramowania, w tym informacji o monitorowaniu i uzgadnianiu licencji firmy Microsoft.  

-   Rozwiązywanie problemów z komputerami przy użyciu zdalnego sterowania.  

-   Implementowanie ustawień zarządzania energią w celu zarządzania i monitorowania zużycia energii przez komputery.  

Konsoli programu Configuration Manager monitoruje poprzednich zadań niemal w czasie rzeczywistym. Powiadomienia oraz informacje o stanie dla każdego zadania jest dostępna w konsoli programu Configuration Manager. Do przechwytywania danych i historycznej analizy trendów, Użyj zintegrowanego możliwości raportowania usług SQL Server Reporting Services. Klienci przesyłają dane do lokacji w formie stanu klienta.  Informacje o stanie klienta dostarcza dane o kondycji i aktywności klienta i są wyświetlane w konsoli lub za pomocą wbudowanych raportów programu Configuration Manager. Te dane ułatwiają identyfikację komputerów, które nie odpowiadają, a w niektórych przypadkach problemy są rozwiązywane automatycznie.  

 Więcej informacji o zadaniach zarządzania dla klientów znajduje się w tematach [Jak zarządzać klientami w programie System Center Configuration Manager](../../core/clients/manage/manage-clients.md) i [Jak zarządzać klientami dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md). Aby dowiedzieć się więcej o używaniu raportów, zobacz   
            [Wprowadzenie do raportowania w programie System Center Configuration Manager](../../core/servers/manage/introduction-to-reporting.md).  

## <a name="configuration-manager-client-application"></a>Aplikacja klienta programu Configuration Manager  
 Po zainstalowaniu oprogramowania klienckiego programu Configuration Manager zainstalowano zbyt aplikacji klienta programu Configuration Manager. W przeciwieństwie do programu Software Center aplikacji klienta programu Configuration Manager jest przeznaczony dla działu pomocy technicznej, a nie dla użytkownika końcowego. Niektóre opcje konfiguracji wymagają posiadania lokalnych uprawnień administracyjnych, a inne wymagają technicznej wiedzy o sposób działania aplikacji klienta programu Configuration Manager. Za pomocą tej aplikacji można wykonywać na kliencie następujące zadania:  

-   Wyświetlanie właściwości klienta, takich jak numer kompilacji, przypisana lokacja, zarządzanie punkt go komunikuje się z i tego, czy klient używa certyfikatów infrastruktury kluczy publicznych (PKI) lub certyfikatu z podpisem własnym.  

-   Upewnij się, że klient pomyślnie pobrał zasadę klienta po zainstalowaniu klienta po raz pierwszy. Upewnij się również, czy ustawienia klienta są włączone lub wyłączone zgodnie z oczekiwaniami, zgodnie z ustawieniami klienta, które są konfigurowane w konsoli programu Configuration Manager.  

-   Uruchamianie akcji klienta. Na przykład można pobrać zasad klienta, jeśli wystąpił ostatnich zmian konfiguracji w konsoli programu Configuration Manager i nie chcesz czekać na następną zaplanowaną czasu.  

-   Ręczne przypisywanie klienta do lokacji programu Configuration Manager lub spróbuj znaleźć lokację. Następnie określ sufiks systemu nazw domen (DNS) dla punktów zarządzania, które publikują w systemie DNS.  

-   Konfigurowanie pamięci podręcznej klienta do tymczasowego przechowywania plików. Usuń pliki z pamięci podręcznej, jeśli potrzebujesz więcej miejsca na dysku do zainstalowania oprogramowania.  

-   Konfigurowanie ustawień dla internetowego zarządzania klientami  

-   Wyświetlanie linii bazowych konfiguracji, które zostały wdrożone na klientach, inicjowanie oceny zgodności i wyświetlanie raportów zgodności  

