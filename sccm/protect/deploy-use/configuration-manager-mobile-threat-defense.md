---
title: "Ochrona przed zagrożeniami przenośnych | System Center Configuration Manager"
description: "Ograniczanie dostępu do zasobów firmy, oparte na ryzyko urządzeń, sieci i aplikacji, korzystając z programu Configuration Manager i przed zagrożeniami Intune Mobile partnerów"
ms.custom: na
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 266897b7ac674a369931e8ed63ff464edc10c9d8
ms.openlocfilehash: 298d879638a2d20d421b19752cb5f20f6725df14
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Przed zagrożeniami Intune Mobile łączniki w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

[Hybrydowe wdrażania oprogramowania MDM (SCCM za pomocą usługi Intune)](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) i integrację między Intune i partnerów przed zagrożeniami Mobile dają możliwość kontrolowania dostępu do zasobów firmy i danych oparte na ocenie ryzyka urządzenia.

Łączniki przed zagrożeniami Intune Mobile umożliwiają wykorzystanie wybranym dostawcą przed zagrożeniami Mobile jako źródło informacji dla zasady zgodności i zasady dostępu warunkowego. To umożliwia administratorom IT dodać warstwę ochrony do ich zasobów firmy, takich jak Exchange i Sharepoint, w szczególności z złamania zabezpieczeń urządzeń przenośnych.

## <a name="what-problem-does-this-solve"></a>Jaki problem to rozwiązuje?

Firmy muszą ochronę danych poufnych przed zagrożeniami, w tym zagrożenia fizyczne, na podstawie aplikacji i opartych na sieci, a także luki w zabezpieczeniach systemu operacyjnego.
Historycznie firm zostały aktywnego podczas ochrony komputerów przed atakiem, gdy urządzenia przenośne Przejdź bez monitorowanych i niechronionych. Platform przenośnych ma wbudowane ochronę takich jak izolacja aplikacji i sprawdzonych i doświadczonych konsumentów sklepów, ale te platformy pozostają narażony na ataki zaawansowane. Obecnie pracownicy więcej użyć urządzenia do pracy i muszą mieć dostęp do poufnych informacji. Urządzenia muszą być chronione przed atakami coraz bardziej zaawansowane.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Sposób działania łączników przed zagrożeniami Mobile Intune?

Łącznik chroni zasoby firmy przez tworzenie kanału komunikacji między Intune a wybranym dostawcą przed zagrożeniami Mobile. Partnerzy przed zagrożeniami Intune Mobile oferują intuicyjne i łatwy do wdrożenia aplikacji dla urządzeń przenośnych, które aktywnie skanowania i analizowania informacji zagrożenia mogą udostępniać usługi Intune, do celów raportowania lub wymuszania. Na przykład, jeśli połączonych aplikacji przed zagrożeniami Mobile raportuje do dostawcy przed zagrożeniami Mobile czy telefon w sieci jest podłączony do sieci, co jest narażony na człowieka w ataki, te informacje jest udostępniane i podzielone na poziomie odpowiednich (niski/średniej/dużej) —, której następnie można porównać z swoje dodatki poziomu ryzyka skonfigurowany w usłudze Intune, aby określić, czy dostęp do niektórych zasobów dowolnego należy odwołany podczas urządzenie zostanie naruszony.

## <a name="sample-scenarios"></a>Przykładowe scenariusze

Gdy urządzenie jest uznawany za zainfekowany przez rozwiązanie przed zagrożeniami Mobile:

![](http://i.imgur.com/Li1WUOU.png)

Dostęp jest udzielany po skorygowaniu urządzenia:

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Partnerzy przed zagrożeniami telefon komórkowy

Informacje o sposobie ochrony dostępu do zasobów firmy na podstawie urządzeń, sieci i ryzykiem aplikacji przy użyciu:

- [Ewentualnym](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
