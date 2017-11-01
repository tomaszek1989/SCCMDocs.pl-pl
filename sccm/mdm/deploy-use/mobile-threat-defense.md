---
title: "Ograniczanie dostępu oparte na ryzyko"
titleSuffix: Configuration Manager
description: "Ograniczanie dostępu do zasobów firmy, w oparciu o ryzyka urządzeń, sieci i aplikacji."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e013c2a3758685aacdacf0707ca0df2c258976b2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Zarządzanie dostępem do zasobów firmy na podstawie urządzeń, sieci i ryzyka aplikacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Łączniki przed zagrożeniami Mobile pozwala korzystać z wybranym dostawcą przed zagrożeniami Mobile jako źródło informacji dla zasady zgodności i zasad dostępu warunkowego. To pozwala administratorom IT dodać warstwę ochrony do ich zasobów firmy, takich jak programy Exchange i Sharepoint, w szczególności z naruszenia zabezpieczeń urządzeń przenośnych.

## <a name="what-problem-does-this-solve"></a>Jaki problem to rozwiązuje?

Firmy muszą chronić poufne dane z zagrożenia pojawiające się tym zagrożenia fizyczne, na podstawie aplikacji i opartych na sieci, a także luk w zabezpieczeniach systemu operacyjnego.
W przeszłości najczęściej firm były aktywne podczas ochrony komputerów przed atakami, gdy urządzenia przenośne Przejdź cofanie monitorowanych i niechronione. Platformy urządzeń przenośnych mają wbudowaną ochronę, takich jak izolacja aplikacji i sklepów z aplikacjami sprawdzonych i doświadczonych konsumenta, ale tych platform nadal narażony na ataki zaawansowane. Obecnie pracownicy więcej użycia urządzeń do pracy i potrzebują dostępu do poufnych informacji. Urządzenia muszą być chronione przed atakami coraz bardziej zaawansowane.

[Hybrydowego wdrożenia zarządzania urządzeniami Przenośnymi (SCCM przy użyciu usługi Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) daje możliwość kontrolowania dostępu do zasobów firmy i danych na podstawie oceny ryzyka, dostarczające rozwiązań do ochrony zagrożeń urządzeń jak partnerów przed zagrożeniami Mobile.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Sposób działania łączników przed zagrożeniami Mobile w usłudze Intune?

Łącznik chroni zasobów firmy przez tworzenie kanału komunikacji między usługą Intune i z wybranym dostawcą Mobile przed zagrożeniami. Ochrona przed zagrożeniami Mobile Intune partnerzy oferują intuicyjny, łatwa do wdrożenia aplikacji dla urządzeń przenośnych, których aktywnie skanowanie i analizowanie informacje dotyczące zagrożeń na udostępnianie usługi Intune, dla celów raportowania lub wymuszania. Na przykład, jeśli połączonej aplikacji mobilnych przed zagrożeniami zgłasza dostawcy przed zagrożeniami Mobile, że phone w sieci jest podłączony do sieci, które są narażone na Man w ataki, te informacje są udostępniane i skategoryzowane do poziomu ryzyka odpowiednie (niski/średnia liczba godzin/wysoka) —, który można porównać z Twojej dodatki poziomu ryzyka skonfigurowany w usłudze Intune, aby określić, czy można odwołać dostęp do niektórych zasobów wybranych przez użytkownika podczas urządzenie zostanie naruszony.

## <a name="sample-scenarios"></a>Przykładowe scenariusze

Gdy urządzenie jest uznawane za zainfekowanych przez rozwiązanie przed zagrożeniami Mobile:

![Przed zagrożeniami Mobile zainfekowanych urządzeń](../media/mtp/MTD-image-1.png)

Gdy urządzenie jest korygowana, zostanie przyznany dostęp:

![Udzielono dostępu obrony zagrożeń Mobile](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>Następne kroki

Informacje o sposobie ochrony dostępu do zasobów firmy na podstawie urządzeń, sieci i ryzyka aplikacji z:

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)