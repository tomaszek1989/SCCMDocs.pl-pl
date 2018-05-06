---
title: Role systemu lokacji dla klientów
titleSuffix: Configuration Manager
description: Określanie ról systemu lokacji dla klientów w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: eac38757ed2147d664b3bdbf2f7e0eb11947dcac
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>Określanie ról systemu lokacji dla klientów programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie mogą pomóc w określeniu role systemu lokacji, które są potrzebne do wdrożenia klientów programu Configuration Manager:  

 Aby uzyskać więcej informacji o miejscu instalacji wymagane role systemu lokacji w hierarchii, zobacz [Projektowanie hierarchii lokacji programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

 Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania ról systemu lokacji, które są potrzebne, zobacz [zainstalować role systemu lokacji](../../../../core/servers/deploy/configure/install-site-system-roles.md).  

##  <a name="determine-if-you-need-a-management-point"></a>Określenia, czy muszą punktu zarządzania  
 Domyślnie wszystkie komputery klienckie z systemem Windows punktu dystrybucji należy zainstalować klienta programu Configuration Manager i mogą wrócić do punktu zarządzania, gdy punkt dystrybucji jest niedostępny. Jednak można zainstalować klientów systemu Windows na komputerach ze źródła alternatywnego, jeśli używana jest właściwość wiersza polecenia programu CCMSetup **/source: < ścieżka\>**. Na przykład zrobić to w przypadku instalacji klientów w Internecie. Inny scenariusz jest należy unikać wysyłania pakietów sieciowych między komputerem a punktem zarządzania podczas instalacji klienta, być może Zapora blokuje porty wymagane lub mieć połączenie o niskiej przepustowości. Wszyscy klienci muszą jednak komunikować się z punktem zarządzania, aby przypisać do lokacji i mają być zarządzane przez program Configuration Manager.  

 Aby uzyskać więcej informacji na temat właściwości wiersza polecenia CCMSetup **/source: < ścieżka\>**, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

 Po zainstalowaniu więcej niż jeden punkt zarządzania w hierarchii, klienci będą automatycznie łączyć się z jednym punktem na podstawie ich lokalizacji członkostwa i sieci lasu. Nie można zainstalować więcej niż jeden punkt zarządzania w lokacji dodatkowej.  

 Klienci na komputerach Mac i klientów urządzeń przenośnych, które zawsze rejestrowane przez program Configuration Manager wymagają punktu zarządzania do instalacji klienta. Ten punkt zarządzania musi znajdować się w lokacji głównej, musi być skonfigurowana do obsługi urządzeń przenośnych i musi akceptować połączenia klientów z Internetu. Ci klienci nie mogą używać punktów zarządzania w lokacjach dodatkowych lub łączą się z punktami zarządzania w innych lokacjach głównych.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>Określenia, czy muszą rezerwowy punkt stanu  
 Rezerwowy punkt stanu umożliwia monitorowanie wdrożeń klienta na komputerach z systemem Windows. Można również zidentyfikować komputery klienckie z systemem Windows, które nie są zarządzane, ponieważ nie mogli komunikować się z punktem zarządzania. Komputery Mac, urządzenia przenośne zarejestrowane przez program Configuration Manager i urządzeń przenośnych, które są zarządzane przy użyciu łącznika serwera Exchange należy używać rezerwowy punkt stanu.  

 Rezerwowy punkt stanu nie jest wymagane do monitorowania aktywności i kondycji klienta.  

 Rezerwowy punkt stanu zawsze komunikuje się z klientami za pośrednictwem protokołu HTTP, który wykorzystuje nieuwierzytelnione połączenia i wysyła dane w postaci zwykłego tekstu. Dzięki temu można podatny na atak, szczególnie, gdy jest używana z zarządzania klientami internetowymi rezerwowy punkt stanu. Aby zmniejszyć obszar ataków, zawsze należy wyznaczyć serwer do uruchomionego rezerwowy punkt stanu i nie należy instalować innych ról systemu lokacji na tym samym serwerze w środowisku produkcyjnym.  

 Zainstalować rezerwowy punkt stanu, gdy wszystkie następujące zastosowania:  

-   Ma błędy komunikacji klienta z komputerów z systemem Windows do wysłania do lokacji, nawet jeśli te komputery klienckie nie mogą komunikować się z punktem zarządzania.  

-   Chcesz użyć raportów wdrażania klienta programu Configuration Manager, które przedstawiają dane wysyłane przez rezerwowy punkt stanu.  

-   Istnieje dedykowany serwer dla tej roli systemu lokacji i zastosowano dodatkowe zabezpieczenia, aby chronić serwer na ataki.  

-   Korzyści wynikające ze stosowania rezerwowy punkt stanu przeważają zagrożenia bezpieczeństwa związane z nieuwierzytelnionymi połączeniami i przesyłem jawnego tekstu przez ruch HTTP.  

 Nie należy instalować rezerwowy punkt stanu, jeśli zagrożenia bezpieczeństwa związane z witryny sieci Web z nieuwierzytelnionymi połączeniami i przesyłem jawnego tekstu przeważają korzyści związane z identyfikowaniem problemów z komunikacją klientów.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>Zadecyduj, czy raportowania punktu usług  
 Configuration Manager udostępnia wiele raportów, które pomagają monitorować instalację, przypisywanie oraz zarządzanie klientami w konsoli programu Configuration Manager. Niektóre raporty wdrożenia klientów wymagają przypisania klientów do rezerwowego punkt stanu.  

 Mimo że raporty nie są wymagane do wdrożenia klientów i można zobaczyć niektóre informacje na temat wdrażania w konsoli programu Configuration Manager lub użyj plików dziennika klienta, aby uzyskać szczegółowe informacje, ale raporty klientów zapewniają cenne informacje, które pomagają monitorować i rozwiązywanie problemów z wdrażaniem klientów.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>Stwierdzić, czy wymagane punkt rejestracyjny oraz punkt proxy rejestracji  
 Configuration Manager wymaga punktu rejestracyjnego i punktu proxy rejestracji do rejestrowania urządzeń przenośnych oraz rejestrowania certyfikatów dla komputerów Mac. Te role systemu lokacji nie są wymagane, jeśli będą zarządzać urządzeniami przenośnymi za pomocą łącznika serwera Exchange lub po zainstalowaniu starszego klienta urządzenia przenośnego (na przykład dla systemu Windows CE), czy żądania i instalowania certyfikatu klienta na komputerach Mac niezależnie od programu Configuration Manager.  

##  <a name="determine-if-you-need-a-distribution-point"></a>Określenia, czy muszą punktu dystrybucji  
 Punkt dystrybucji, aby zainstalować klientów programu Configuration Manager na komputerach z systemem Windows nie jest konieczne. Domyślnie programu Configuration Manager korzysta z punktu dystrybucji do instalacji plików źródłowych klienta na komputerach z systemem Windows ale może przełączyć się na pobieranie tych plików z punktu zarządzania. Punkty dystrybucji nie są używane do instalowania klientów urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager, ale są stosowane po zainstalowaniu starszego klienta urządzenia przenośnego. Po zainstalowaniu klienta programu Configuration Manager jako część wdrożenia systemu operacyjnego, obraz systemu operacyjnego są przechowywane i pobierane z punktu dystrybucji.  

 Mimo że punkty dystrybucji do zainstalowania większości klientów programu Configuration Manager nie może być konieczne, należy je do instalacji oprogramowania, takiego jak aplikacje i aktualizacje oprogramowania na klientach.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>Określenia, czy należy punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci Web katalogu aplikacji  
 Punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci Web katalogu aplikacji nie są wymagane dla wdrożenia klienta. Jednak można je zainstalować jako część procesu wdrażania klientów, dzięki czemu użytkownicy mogą wykonywać następujące czynności natychmiast po zainstalowaniu klienta programu Configuration Manager na komputerach z systemem Windows:  

-   Czyszczenie urządzeń przenośnych.  

-   wyszukiwanie i instalowanie aplikacji z katalogu aplikacji,  

-   Wdrażanie aplikacji dla użytkowników i urządzeń z celem wdrożenia **dostępne**.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>Określanie, czy jest wymagany punkt łącznika bramy zarządzania w chmurze 

Należy punkt łącznika chmury zarządzania bramy, jeśli konfigurujesz usługę [brama zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway) do [zarządzać klientami w Internecie](/sccm/core/clients/manage/manage-clients-internet).


 