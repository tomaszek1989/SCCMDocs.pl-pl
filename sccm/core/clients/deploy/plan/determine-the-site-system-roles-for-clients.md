---
title: "Role systemu lokacji dla klientów | Dokumentacja firmy Microsoft"
description: "Określanie ról systemu lokacji dla klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9f2dda834f23b2ee85c4c301c7e1b6a3a54ebc97
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie mogą ułatwić ustalenie ról systemu lokacji, które są potrzebne do wdrożenia klientów programu Configuration Manager:  

 Aby uzyskać więcej informacji o miejscu instalacji wymagane role systemu lokacji w hierarchii, zobacz [projektowania hierarchii lokacji programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

 Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania ról systemu lokacji, które są potrzebne, można znaleźć w temacie [zainstalować role systemu lokacji](../../../../core/servers/deploy/configure/install-site-system-roles.md).  

##  <a name="determine-if-you-need-a-management-point"></a>Określ, czy wymagane punktu zarządzania  
 Domyślnie wszystkie komputery klienckie systemu Windows należy zainstalować klienta programu Configuration Manager punkt dystrybucji i przełączają do punktu zarządzania, gdy punkt dystrybucji jest niedostępny. Jednak można zainstalować klientów systemu Windows na komputerach ze źródła alternatywnego, jeśli używana jest właściwość wiersza polecenia CCMSetup **/źródło: < ścieżka\>**. Na przykład może w tym przypadku instalacji klientów w Internecie. Inny scenariusz czyli umożliwia unikanie wysyłania pakietów sieciowych między komputerem a punktem zarządzania podczas instalacji klienta, przykład zapora blokuje porty wymagane jest połączenie o niskiej przepustowości. Wszyscy klienci muszą jednak komunikować się z punktem zarządzania, aby przypisać do lokacji i mają być zarządzane przez program Configuration Manager.  

 Aby uzyskać więcej informacji o właściwości wiersza polecenia programu CCMSetup **/źródło: < ścieżka\>**, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

 Po zainstalowaniu więcej niż jeden punkt zarządzania w hierarchii, klienci będą automatycznie łączyć się z jednym punktem na podstawie ich lokalizacji członkostwa i sieci lasu. Nie można zainstalować więcej niż jeden punkt zarządzania w lokacji dodatkowej.  

 Klienci na komputerach Mac oraz klientów urządzeń przenośnych, które rejestrują się w programie Configuration Manager zawsze wymagają punktu zarządzania dla instalacji klienta. Ten punkt zarządzania musi znajdować się w lokacji głównej, musi być skonfigurowany do obsługi urządzeń przenośnych i musi akceptować połączenia klientów z Internetu. Ci klienci nie można używać punktów zarządzania w lokacjach dodatkowych ani łączyć się z punktami zarządzania w innych lokacjach głównych.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>Określ, czy wymagane rezerwowy punkt stanu  
 Rezerwowy punkt stanu służy do monitorowania wdrażania klientów na komputerach z systemem Windows. Można również zidentyfikować Windows komputerów klienckich, które są zarządzane, ponieważ nie mogli komunikować się z punktem zarządzania. Mac komputerów, urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager i urządzeń przenośnych, które są zarządzane przy użyciu łącznika serwera Exchange należy używać rezerwowego punktu stanu.  

 Punkt stanu powrotu nie jest zobowiązana do monitorowania aktywności i kondycji klienta.  

 Rezerwowy punkt stanu zawsze komunikuje się z klientami za pośrednictwem protokołu HTTP, który wykorzystuje nieuwierzytelnione połączenia i wysyła dane w postaci zwykłego tekstu. Dzięki temu rezerwowy punkt stanu podatny na atak, szczególnie, gdy jest używany do zarządzania klientami. Aby zmniejszyć obszar ataków, zawsze należy wyznaczyć serwer do punktu stanu powrotu i nie należy instalować innych ról systemu lokacji na tym samym serwerze w środowisku produkcyjnym.  

 Należy zainstalować rezerwowy punkt stanu, gdy spełnione wszystkie następujące warunki:  

-   Ma błędy komunikacji klienta z komputerów z systemem Windows do wysłania do lokacji, nawet jeśli te komputery klienckie nie mogą komunikować się z punktem zarządzania.  

-   Chcesz użyć raportów wdrażania klienta programu Configuration Manager, które przedstawiają dane wysyłane przez rezerwowy punkt stanu.  

-   Istnieje dedykowany serwer dla tej roli systemu lokacji i zastosowano dodatkowe zabezpieczenia w celu ochrony serwera przed atakiem.  

-   Korzyści wynikające z użycia rezerwowego punkt stanu przeważają zagrożenia bezpieczeństwa związane z nieuwierzytelnionymi połączeniami i przesyłem jawnego tekstu przez ruch HTTP.  

 Nie należy instalować rezerwowy punkt stanu w przypadku zagrożenia zabezpieczeń związane z działaniem witryny sieci Web z nieuwierzytelnionymi połączeniami i przesyłem jawnego tekstu przeważają korzyści związane z identyfikowaniem problemów z komunikacją klientów.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>Określ, czy potrzebujesz raportowania punkt usług  
 Program Configuration Manager udostępnia wiele raportów, które pomagają monitorować instalację, przypisania i zarządzać klientami w konsoli programu Configuration Manager. Niektóre raporty wdrożenia klientów wymagają przypisania klientów do rezerwowego punktu stanu.  

 Mimo że raporty nie są wymagane do wdrożenia klientów i można zobaczyć niektóre informacje na temat wdrażania w konsoli programu Configuration Manager lub użyć plików dziennika klienta szczegółowe informacje, ale raporty klientów zapewniają cenne informacje, które pomagają monitorować i rozwiązywanie problemów z wdrażaniem klientów.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>Określ, czy wymagane punkt rejestracyjny oraz punkt proxy rejestracji  
 Punkt rejestracji i punktu proxy rejestracji do rejestrowania urządzeń przenośnych oraz rejestrowania certyfikatów dla komputerów Mac wymaga programu Configuration Manager. Te role systemu lokacji nie są wymagane, jeśli będą zarządzać urządzeniami przenośnymi za pomocą łącznika serwera Exchange lub po zainstalowaniu starszych klientów urządzeń przenośnych (na przykład dla systemu Windows CE) lub żądania i instalowania certyfikatu klienta na komputerach Mac niezależnie od programu Configuration Manager.  

##  <a name="determine-if-you-need-a-distribution-point"></a>Określ, czy wymagane punktu dystrybucji  
 Nie trzeba instalować klientów programu Configuration Manager na komputerach z systemem Windows w punkcie dystrybucji. Domyślnie program Configuration Manager korzysta z punktu dystrybucji w celu instalacji plików źródłowych klienta na komputerach z systemem Windows ale może przełączyć się na pobieranie tych plików z punktem zarządzania. Punkty dystrybucji nie są używane do instalowania klientów urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager, ale są używane w przypadku instalowania starszych klientów urządzeń przenośnych. Po zainstalowaniu klienta programu Configuration Manager w ramach wdrożenia systemu operacyjnego, obraz systemu operacyjnego są przechowywane i pobierane z punktu dystrybucji.  

 Mimo że nie może być konieczne do instalacji większości klientów programu Configuration Manager, należy je zainstalować oprogramowanie, takie jak aplikacje i aktualizacje oprogramowania na komputerach klienckich.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>Określ, czy wymagane punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci Web katalogu aplikacji  
 Punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci Web katalogu aplikacji nie są potrzebne do wdrożenia klienta. Jednak można je zainstalować w ramach procesu wdrażania klienta, tak aby użytkownicy mogą wykonywać następujące czynności natychmiast po zainstalowaniu klienta programu Configuration Manager na komputerach z systemem Windows:  

-   Czyszczenie urządzeń przenośnych.  

-   wyszukiwanie i instalowanie aplikacji z katalogu aplikacji,  

-   Wdrażanie aplikacji dla użytkowników i urządzeń z celem wdrożenia **dostępne**.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>Ustalenia, czy jest wymagany punkt łącznik bramy zarządzania chmury 

Należy punkt łącznik chmury zarządzania bramą, jeśli konfigurujesz usługę [brama zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway) do [zarządzać klientami w Internecie](/sccm/core/clients/manage/manage-clients-internet).


 
