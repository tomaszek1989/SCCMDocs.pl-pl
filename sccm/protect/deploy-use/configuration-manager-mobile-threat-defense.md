---
title: Ochrona przed zagrożeniami przenośnych
titleSuffix: Configuration Manager
description: Ograniczanie dostępu do zasobów firmy, w oparciu o ryzyka urządzeń, sieci i aplikacji przy użyciu programu Configuration Manager i przed zagrożeniami Intune Mobile partnerów
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6aeed0c7e509ee96b226f5d1c7649bcf84af3af8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Ochrona przed zagrożeniami Mobile Intune łączniki w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

[Hybrydowego wdrożenia zarządzania urządzeniami Przenośnymi (SCCM przy użyciu usługi Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) i integrację między usługami Intune i partnerów przed zagrożeniami Mobile zapewniają możliwość kontrolowania dostępu do zasobów firmy i danych na podstawie oceny ryzyka urządzenia.

Łączniki przed zagrożeniami Intune Mobile pozwala korzystać z wybranym dostawcą przed zagrożeniami Mobile jako źródło informacji dla zasady zgodności i zasad dostępu warunkowego. To pozwala administratorom IT dodać warstwę ochrony do ich zasobów firmy, takich jak programy Exchange i Sharepoint, w szczególności z naruszenia zabezpieczeń urządzeń przenośnych.

## <a name="what-problem-does-this-solve"></a>Jaki problem to rozwiązuje?

Firmy muszą chronić poufne dane z zagrożenia pojawiające się tym zagrożenia fizyczne, na podstawie aplikacji i opartych na sieci, a także luk w zabezpieczeniach systemu operacyjnego.
W przeszłości najczęściej firm były aktywne podczas ochrony komputerów przed atakami, gdy urządzenia przenośne Przejdź cofanie monitorowanych i niechronione. Platformy urządzeń przenośnych mają wbudowaną ochronę, takich jak izolacja aplikacji i sklepów z aplikacjami sprawdzonych i doświadczonych konsumenta, ale tych platform nadal narażony na ataki zaawansowane. Obecnie pracownicy więcej użycia urządzeń do pracy i potrzebują dostępu do poufnych informacji. Urządzenia muszą być chronione przed atakami coraz bardziej zaawansowane.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Sposób działania łączników przed zagrożeniami Mobile w usłudze Intune?

Łącznik chroni zasobów firmy przez tworzenie kanału komunikacji między usługą Intune i z wybranym dostawcą Mobile przed zagrożeniami. Ochrona przed zagrożeniami Mobile Intune partnerzy oferują intuicyjny, łatwa do wdrożenia aplikacji dla urządzeń przenośnych, których aktywnie skanowanie i analizowanie informacje dotyczące zagrożeń na udostępnianie usługi Intune, dla celów raportowania lub wymuszania. Na przykład, jeśli połączonej aplikacji mobilnych przed zagrożeniami zgłasza dostawcy przed zagrożeniami Mobile, że phone w sieci jest podłączony do sieci, które są narażone na Man w ataki, te informacje są udostępniane i skategoryzowane do poziomu ryzyka odpowiednie (niski/średnia liczba godzin/wysoka) —, który można porównać z Twojej dodatki poziomu ryzyka skonfigurowany w usłudze Intune, aby określić, czy można odwołać dostęp do niektórych zasobów wybranych przez użytkownika podczas urządzenie zostanie naruszony.

## <a name="sample-scenarios"></a>Przykładowe scenariusze

Gdy urządzenie jest uznawane za zainfekowanych przez rozwiązanie przed zagrożeniami Mobile:

![](http://i.imgur.com/Li1WUOU.png)

Gdy urządzenie jest korygowana, zostanie przyznany dostęp:

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Ochrona przed zagrożeniami Mobile partnerów

Informacje o sposobie ochrony dostępu do zasobów firmy na podstawie urządzeń, sieci i ryzyka aplikacji z:

- [Lookout](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
