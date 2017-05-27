---
title: "Ograniczyć dostęp oparty na ryzyko | Dokumentacja firmy Microsoft"
description: "Ograniczanie dostępu do zasobów firmy, oparte na ryzyko urządzeń, sieci i aplikacji."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 21841d97387f07f53993d957641f9ad892d723c2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Zarządzanie dostępem do zasobów firmy na podstawie urządzeń, sieci i aplikacji ryzyko

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można kontrolować dostęp do zasobów firmy, oparte na ocenie ryzyka prowadzonych przez szczególną, rozwiązania ochrony zagrożenia urządzenia, które jest zintegrowany z programem Microsoft Intune z urządzeń przenośnych. Ryzyko opiera się na dane usługi ewentualnym zbiera z urządzeń luki w zabezpieczeniach systemu operacyjnego (OS), zainstalowane aplikacje złośliwego i profilów sieci złośliwy. 

Oparte na ocenie ryzyka zgłoszone przez ewentualnym włączana za pomocą zasady zgodności System center configuration manager (SCCM), można skonfigurować zasady dostępu warunkowego i umożliwić lub urządzenia, które zostały uznane za niezgodne z powodu zagrożenia wykryte na tych urządzeniach.

[Hybrydowe wdrażania oprogramowania MDM (SCCM za pomocą usługi Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) rozwiązań ochrony jak zapewnia ewentualnym zagrożenia daje możliwość kontrolowania dostępu do zasobów firmy i danych jest oparty na ocenie ryzyka tego urządzenia.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>Jak wdrożenie hybrydowe MDM i ochroną urządzenia ewentualnym pomaga chronić zasobów firmy?
Ewentualnym w aplikacji mobilnej (szukać pracy), uruchomiony na urządzeniach przenośnych, przechwytuje systemu plików, stos sieci telemetrii urządzeniami i aplikacjami (jeśli jest dostępna) i wysyła je do ewentualnym urządzenia zagrożenia ochrony usługę w chmurze do obliczania ryzyko agregacji urządzeń przenośnych zagrożenia. Można również zmienić klasyfikacji poziom ryzyka w przypadku zagrożeń w konsoli ewentualnym zgodnie ze swoimi potrzebami.  

Zasady zgodności w SCCM zawiera teraz nową regułę dla ewentualnym przenośnych ochroną opartą na ocenie ryzyka zagrożenia ewentualnym urządzenia. Gdy ta zasada jest włączona, urządzenia jest sprawdzany pod kątem zgodności.

Jeśli urządzenie jest określana jako niezgodne z zasadami zgodności, dostępu do zasobów, takich jak Exchange Online i SharePoint Online można zablokowane, za pomocą zasad dostępu warunkowego. Gdy dostęp jest zablokowany, użytkownicy końcowi są dostarczane z przewodnikiem, aby rozwiązać ten problem i uzyskać dostęp do zasobów firmy. W tym instruktażu jest uruchamiany za pośrednictwem szukać pracy aplikacji.

## <a name="supported-platforms"></a>Obsługiwane platformy:
* **System android 4.1 lub nowszy**i zarejestrowanych w programie Microsoft Intune.
* **iOS 8 i nowsze**i zarejestrowanych w programie Microsoft Intune.
Aby uzyskać informacje o platformach i języki, które obsługuje ewentualnym, zobacz [artykuł](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Wymagania wstępne:
* [Hybrydowe wdrażania oprogramowania MDM](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Subskrypcja Microsoft Intune i Azure Active Directory.
* Subskrypcja enterprise ewentualnym Mobile punktu końcowego zabezpieczeń.  Aby uzyskać więcej informacji, zobacz [ewentualnym Mobile punktu końcowego zabezpieczeń](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="example-scenarios"></a>Przykładowe scenariusze
Poniżej przedstawiono kilka typowych scenariuszy:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>Kontrola dostępu oparte na zagrożenia z złośliwy aplikacji:
Po wykryciu złośliwego aplikacji, takich jak złośliwe oprogramowanie na urządzeniu, można zablokować takie urządzenia z:
* Łączenie z firmowej poczty e-mail przed rozpoznawanie zagrożenia.
* Synchronizowania plików firmowych za pomocą usługi OneDrive dla aplikacji do pracy.
* Uzyskiwanie dostępu do aplikacji biznesowych o znaczeniu krytycznym.

**Zablokowany po wykryciu złośliwego aplikacji dostęp do:**

![Diagram przedstawiający blokowanie dostępu zasad dostępu warunkowego, gdy urządzenie zostanie uznane za niezgodny z powodu złośliwy aplikacji na urządzeniu](media/config-mgr-maliciousapps_blocked.png)

**Urządzenie odblokowany i może uzyskać dostępu do zasobów firmy, po skorygowaniu zagrożenie:**

![Diagram przedstawiający udzielania dostępu, gdy urządzenie jest uznany za zgodny po skorygowaniu zasad dostępu warunkowego](media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>Kontrola dostępu oparte na zagrożenie dla sieci:
Wykrywanie zagrożenia do sieci, takich jak ataki Man-in--middle i ograniczyć dostęp do sieci Wi-Fi oparte na ryzyko urządzenia.

**Zablokowanie dostępu do sieci za pośrednictwem sieci Wi-Fi:**

![Diagram przedstawiający warunkowego dostępu do blokowania dostępu sieci Wi-Fi, oparte na sieci zagrożenia](media/config-mgr-network-wifi-blocked.png)

**Dostęp udzielany na korygowania:**

![Diagram przedstawiający zezwoleniem na dostęp na korygowanie zagrożenia dostępu warunkowego](media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrola dostępu do usługi SharePoint Online oparte na zagrożenie dla sieci:

Wykrywa zagrożenia do sieci, takich jak ataki Man-in--middle i zapobiec synchronizacji plików firmowych oparte na ryzyko urządzenia.

**Dostęp zablokowany usługi SharePoint Online oparte na sieci zagrożeń wykrytych w urządzeniu:**

![Diagram przedstawiający dostępu warunkowego blokuje dostęp do urządzeń do usługi SharePoint Online w oparciu wykrywania zagrożeń](media/config-mgr-network-spo-blocked.png)


**Dostęp udzielany na korygowania:**

![Diagram przedstawiający zezwoleniem na dostęp po skorygowaniu zagrożenia sieci dostępu warunkowego](media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>Następne kroki
Oto główne kroki, które należy wykonać, aby zaimplementować to rozwiązanie:
1.    [Konfigurowanie subskrypcji z przenośnych szczególną ochroną](set-up-your-subscription-with-lookout.md)
2.    [Włącz połączenie MTP ewentualnym w usłudze Intune](enable-lookout-connection-in-intune.md)
3.  [Konfigurowanie i wdrażanie ewentualnym pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md)
4.    [Konfigurowanie zasad zgodności](enable-device-threat-protection-rule-compliance-policy.md)
5.    [Rozwiązywanie problemów z integracją ewentualnym](troubleshoot-lookout-integration.md)

