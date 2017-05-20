---
title: "Wdrażanie aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Wybierz aktualizacje oprogramowania w konsoli programu Configuration Manager, aby ręcznie uruchomić proces wdrażania lub automatycznego wdrażania aktualizacji."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 04536d51-3bf7-45e5-b4af-36ceed10583d
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 70a0ad1da03a7ca88df206fec683ab1df2b531e1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

#  <a name="BKMK_SUMDeploy"></a> Wdrażanie aktualizacji oprogramowania  

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Faza wdrożenia aktualizacji oprogramowania polega na wdrożeniu aktualizacji oprogramowania. Niezależnie od tego, w jaki sposób wdrażania aktualizacji oprogramowania aktualizacje są zwykle dodawane do grupy aktualizacji oprogramowania, aktualizacje oprogramowania zostaną pobrane do punktów dystrybucji i wdrożeniu grupy aktualizacji do klientów. Po utworzeniu wdrożenia zasady aktualizacji oprogramowania są wysyłane do komputerów klienckich, zawartości, pliki są pobierane z punktu dystrybucji do lokalnej pamięci podręcznej na komputerach klienckich, a następnie aktualizacje oprogramowania są dostępne z klienta w celu instalacji aktualizacji oprogramowania. Klienci połączeni z Internetem pobierają zawartość z usługi Microsoft Update.  

> [!NOTE]  
>  Klienta można skonfigurować w sieci intranet w celu pobierania aktualizacji oprogramowania z usługi Microsoft Update, gdy punkt dystrybucji jest niedostępny.  

> [!NOTE]  
>  W przeciwieństwie do innych typów wdrożeń wszystkie aktualizacje oprogramowania są pobierane do pamięci podręcznej klienta niezależnie od jej skonfigurowanego maksymalnego rozmiaru. Więcej informacji o ustawieniu pamięci podręcznej klienta znajduje się w sekcji [Konfigurowanie pamięci podręcznej klienta dla klientów programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_ClientCache).  

W przypadku skonfigurowania wymaganego wdrożenia aktualizacji oprogramowania aktualizacje są instalowane automatycznie zgodnie z zaplanowanym terminem ostatecznym. Użytkownik może ewentualnie zaplanować lub zainicjować instalację aktualizacji oprogramowania na komputerze klienckim przed terminem ostatecznym. Po próbie instalacji komputery klienckie wysyłają na serwer lokacji zwrotne komunikaty o stanie, aby zgłosić, czy instalacja aktualizacji oprogramowania zakończyła się pomyślnie. Więcej informacji o wdrożeniach aktualizacji oprogramowania znajduje się w sekcji [Przepływy pracy wdrożeń aktualizacji oprogramowania](../understand/software-updates-introduction.md#BKMK_DeploymentWorkflows).  

Istnieją dwa główne scenariusze wdrażania aktualizacji oprogramowania: wdrażanie ręczne i wdrażanie automatyczne. Zazwyczaj zostanie uruchomione przez ręczne wdrażanie aktualizacji oprogramowania, aby utworzyć linię bazową klienckich komputerów, a następnie będzie zarządzać aktualizacjami oprogramowania na klientach za pomocą wdrażania automatycznego.  

## <a name="BKMK_ManualDeployment"></a>Ręczne wdrażanie aktualizacji oprogramowania
Można wybrać aktualizacje oprogramowania w konsoli programu Configuration Manager i ręcznie uruchomić procesu wdrażania. Tę metodę wdrażania stosuje się najczęściej po to, aby uaktualnić komputery klienckie za pomocą wymaganych aktualizacji oprogramowania przed utworzeniem zasad wdrażania automatycznego, zarządzających ciągłymi comiesięcznymi wdrożeniami aktualizacji oprogramowania, i aby wdrożyć wymagania aktualizacji oprogramowania poza pasmem. Na poniższej liście przedstawiono ogólny przepływ pracy ręcznego wdrażania aktualizacji oprogramowania:  

1. Odfiltrowanie aktualizacji oprogramowania, które korzystają z określonych wymagań. Można na przykład podać kryteria pozwalające pobrać wszystkie aktualizacje oprogramowania zabezpieczeń lub krytyczne aktualizacje oprogramowania, jakie są wymagane na ponad 50 komputerach klienckich.  
2. Tworzenie grupy aktualizacji oprogramowania, zawierającej aktualizacje oprogramowania.  
3. Pobranie zawartości dla aktualizacji oprogramowania należących do grupy aktualizacji oprogramowania.  
4. Ręczne wdrożenie grupy aktualizacji oprogramowania.

Aby uzyskać szczegółowy opis kroków, zobacz [Ręczne wdrażanie aktualizacji oprogramowania](manually-deploy-software-updates.md).

## <a name="automatically-deploy-software-updates"></a>Automatyczne wdrażanie aktualizacji oprogramowania
Automatyczne wdrażanie aktualizacji oprogramowania konfiguruje się za pomocą reguły wdrażania automatycznego (ADR). Ta metoda jest często wdrożenia co miesiąc aktualizacji oprogramowania (zwykle nazywane "Wtorek poprawek") i zarządzania aktualizacjami definicji. Po uruchomieniu reguły aktualizacje oprogramowania są usuwane z grupy aktualizacji oprogramowania (w przypadku korzystania z istniejącej grupie aktualizacji), aktualizacje oprogramowania, które spełniają określone kryteria (na przykład wszystkie aktualizacje oprogramowania zabezpieczeń wydane w ciągu ostatniego miesiąca) są dodawane do grupy aktualizacji oprogramowania, pliki zawartości aktualizacji oprogramowania są pobierane i kopiowane do punktów dystrybucji, a aktualizacje oprogramowania są wdrażane na klientach w kolekcji docelowej. Na poniższej liście przedstawiono ogólny przepływ pracy do automatycznego wdrażania aktualizacji oprogramowania:  

1.  Utwórz ADR, określającą ustawienia wdrożenia.
2.  Aktualizacje oprogramowania zostają dodane do grupy aktualizacji oprogramowania.  
3.  Grupa aktualizacji oprogramowania jest wdrażana na komputerach klienckich w kolekcji docelowej, jeśli została określona.  

Należy ustalić, jaką strategię wdrażania zastosować w danym środowisku. Można na przykład utworzyć regułę ADR, obierając za cel kolekcję klientów testowych. Po zweryfikowaniu, że aktualizacje oprogramowania zostały zainstalowane w tej grupie testowej, można dodać nowe wdrożenie do reguły lub zmienić kolekcję w istniejącym wdrożeniu na kolekcję docelową obejmującą większy zestaw klientów. Obiekty aktualizacji oprogramowania tworzone przez reguły ADR są interaktywne.  

-   Aktualizacje oprogramowania wdrożone za pomocą reguły ADR są automatycznie wdrażane na nowych klientach dodawanych do kolekcji docelowej.  
-   Nowe aktualizacje oprogramowania dodawane do grupy aktualizacji oprogramowania są automatycznie wdrażane na klientach w kolekcji docelowej.  
-   Wdrożenia na użytek reguły ADR można w każdej chwili włączać lub wyłączać.  

Po utworzeniu reguły ADR można dodać do niej dodatkowe wdrożenia. Dzięki temu można uprościć wdrażanie różnych aktualizacji w różnych kolekcjach. Dla każdego nowego wdrożenia dostępny jest pełny zakres funkcji wraz z możliwością monitorowania wdrożenia, a każde nowe dodane wdrożenie:  

-   Używa tej samej grupy aktualizacji i tego samego pakietu utworzonego przy pierwszym uruchomieniu reguły wdrażania automatycznego.  
-   Możliwość określenia innej kolekcji.  
-   Obsługa unikatowych właściwości wdrożenia, w tym poniższych:  
   -   Czas aktywacji  
   -   Termin  
   -   Włączenie lub wyłączenie czynności użytkownika  
   -   Oddzielne alerty dla wdrożenia  

Aby uzyskać szczegółowy opis kroków, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](automatically-deploy-software-updates.md)

<!-- ###  <a name="BKMK_ClientCache"></a> Client cache setting  
The Configuration Manager client downloads the content for required software updates to the local client cache soon after it receives the deployment. However, the client waits to download the content until after the **Software available time** setting for the deployment. The client does not download software updates in optional deployments (deployments that do not have a scheduled installation deadline) until the user manually starts the installation. When the configured deadline passes, the software updates client agent performs a scan to verify that the software update is still required, then the software updates client agent checks the local cache on the client computer to verify that the software update source file is still available, and then installs the software update. If the content was deleted from the client cache to make room for another deployment, the client downloads the software updates to the cache. Software updates are always downloaded to the client cache regardless of the configured maximum client cache size. For other deployments, such as applications or packages, the client only downloads content that is within the maximum cache size that you configure for the client. Cached content is not automatically deleted, but it remains in the cache for at least one day after the client used that content.  -->


 <!-- For more information about the deployment process, see [Software update deployment process](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).  -->

