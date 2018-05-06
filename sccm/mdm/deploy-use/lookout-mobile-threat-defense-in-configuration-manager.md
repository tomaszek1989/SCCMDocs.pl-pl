---
title: Ograniczanie dostępu oparte na ryzyko
titleSuffix: Configuration Manager
description: Ograniczanie dostępu do zasobów firmy, w oparciu o ryzyka urządzeń, sieci i aplikacji.
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d0843fcc0956cf65da27ad10c19e59d97b60f16a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Zarządzanie dostępem do zasobów firmy na podstawie urządzeń, sieci i ryzyka aplikacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można kontrolować dostęp do zasobów firmy, na podstawie oceny ryzyka przeprowadzonych przez aplikację Lookout, rozwiązania ochrony zagrożeń urządzenia, które jest zintegrowana w usłudze Microsoft Intune z urządzeniami przenośnymi. Ryzyko jest oparta na dane telemetryczne usługę Lookout zbiera dane z urządzeń luk w zabezpieczeniach systemu operacyjnego (OS), aplikacje złośliwe zainstalowanych i profilów sieci złośliwe. 

W oparciu o oceny ryzyka zgłoszonych przez aplikację Lookout włączona przy użyciu zasady zgodności System center configuration manager (SCCM), należy skonfigurować zasady dostępu warunkowego i zezwala lub blokuje urządzenia, które zostały uznane za niezgodne z powodu zagrożenia wykryte na tych urządzeniach.

[Hybrydowego wdrożenia zarządzania urządzeniami Przenośnymi (SCCM przy użyciu usługi Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) rozwiązań do ochrony jak zapewnia Lookout zagrożenia daje możliwość kontrolowania dostępu do zasobów firmy i danych jest oparty na oceny ryzyka tego urządzenia.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>Jak hybrydowego wdrożenia zarządzania urządzeniami Przenośnymi i ochrony Lookout urządzenia przed zagrożeniami ochrona zasobów firmy?
Lookout w aplikacji mobilnej (aplikację Lookout for work) uruchomiony na urządzeniach przenośnych, przechwytuje stos sieciowy systemu plików, urządzeniami i aplikacjami telemetrii (jeśli jest dostępna) i wysyła je do Lookout urządzenia zagrożenia ochrony usługa w chmurze do obliczania ryzyka urządzenia agregacji dla przenośnych zagrożeń. Można również zmienić klasyfikacji poziom ryzyka dla zagrożenia w konsoli Lookout ze swoimi potrzebami.  

Zasady zgodności w SCCM zawiera teraz nową regułę dla Lookout przenośnych ochroną opartą na oceny ryzyka Lookout urządzenia zagrożeń. Gdy ta zasada jest włączona, urządzenie jest oceniane pod kątem zgodności.

Jeśli urządzenie jest określany jako niezgodne z zasadami zgodności, dostępu do zasobów, takich jak Exchange Online i SharePoint Online można zablokowane, za pomocą zasad dostępu warunkowego. Gdy dostęp zostanie zablokowany, użytkownicy końcowi otrzymują wskazówki pomagające rozwiązać ten problem i uzyskać dostęp do zasobów firmy. Ten przewodnik jest uruchamiana przez aplikację Lookout for work aplikacji.

## <a name="supported-platforms"></a>Obsługiwane platformy:
* **System android 4.1 lub nowszy**i zarejestrowanych w programie Microsoft Intune.
* **System iOS 8 i nowsze**i zarejestrowanych w programie Microsoft Intune.
Aby uzyskać informacje o platformach i językach obsługiwanych przez usługę Lookout, zobacz ten [artykułu](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Wymagania wstępne:
* [Wdrożenia hybrydowego zarządzania urządzeniami Przenośnymi](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Subskrypcja Microsoft Intune i Azure Active Directory.
* Subskrypcja enterprise Lookout Mobile punktu końcowego zabezpieczeń.  Aby uzyskać więcej informacji, zobacz [Lookout Mobile punktu końcowego zabezpieczeń](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="example-scenarios"></a>Przykładowe scenariusze
Poniżej przedstawiono kilka typowych scenariuszy:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>Kontroli dostępu oparte na ryzyko ze strony złośliwych aplikacji:
Po wykryciu złośliwego aplikacji, takich jak złośliwego oprogramowania na urządzeniu możesz zablokować tych urządzeń z:
* Łączenie z firmowej poczty e-mail przed rozpoznawania zagrożenia.
* Synchronizowanie plików firmy przy użyciu usługi OneDrive dla pracy aplikacji.
* Dostęp do aplikacji biznesowych o znaczeniu krytycznym.

**Zablokowany po wykryciu złośliwego aplikacji dostęp do:**

![Diagram przedstawiający blokowanie dostępu zasad dostępu warunkowego, gdy urządzenie zostanie uznane za niezgodne z powodu złośliwe aplikacje na urządzeniu](media/config-mgr-maliciousapps_blocked.png)

**Urządzenie odblokowany i jest w stanie uzyskać dostępu do zasobów firmy to zagrożenie jest korygowana:**

![Diagram przedstawiający zasady dostępu warunkowego udzielanie dostępu, gdy urządzenie jest uznany za zgodny po skorygowaniu](media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>Kontroli dostępu w oparciu o zagrożenie dla sieci:
Wykrywanie zagrożeń bezpieczeństwa sieci, takich jak ataki Man-in--middle i ograniczanie dostępu do sieci Wi-Fi w oparciu ryzyka dotyczącego urządzenia.

**Zablokowanie dostępu do sieci za pośrednictwem sieci Wi-Fi:**

![Diagram przedstawiający warunkowego dostępu blokowanie dostępu WiFi oparte na zagrożenia sieciowe](media/config-mgr-network-wifi-blocked.png)

**Dostęp przyznane środki zaradcze:**

![Diagram przedstawiający zezwalania na dostęp na korygowania zagrożenia dostępu warunkowego](media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrolowanie dostępu do usługi SharePoint Online oparte na zagrożenie dla sieci:

Wykrywanie zagrożeń bezpieczeństwa sieci, takich jak ataki Man-in--middle i uniemożliwić synchronizację plików firmowych w oparciu o ryzyka dotyczącego urządzenia.

**Zablokowanie dostępu usługi SharePoint Online oparte na sieci zagrożeń wykrytych w urządzeniu:**

![Diagram przedstawiający dostępu warunkowego, blokuje dostęp do urządzeń do usługi SharePoint Online oparte na wykrywanie zagrożeń](media/config-mgr-network-spo-blocked.png)


**Dostęp przyznane środki zaradcze:**

![Diagram przedstawiający zezwalania na dostęp po zagrożeń sieci jest korygowana dostępu warunkowego](media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>Następne kroki
Oto główne kroki, które należy wykonać, aby wdrożyć to rozwiązanie:
1.  [Konfigurowanie subskrypcji z ochrony przed zagrożeniami przenośnych Lookout](set-up-your-subscription-with-lookout.md)
2.  [Włącz połączenie z usługą Lookout MTP w usłudze Intune](enable-lookout-connection-in-intune.md)
3.  [Konfigurowanie i wdrażanie Lookout pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md)
4.  [Konfigurowanie zasad zgodności](enable-device-threat-protection-rule-compliance-policy.md)
5.  [Rozwiązywanie problemów dotyczących integracji z usługą Lookout](troubleshoot-lookout-integration.md)
