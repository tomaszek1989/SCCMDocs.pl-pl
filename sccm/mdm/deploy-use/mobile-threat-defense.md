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
ms.openlocfilehash: 250671660c1c6da0ca9b593b06b8f344dfe17ad6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Zarządzanie dostępem do zasobów firmy na podstawie urządzeń, sieci i aplikacji ryzyko

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Łączniki przed zagrożeniami Mobile umożliwiają wykorzystanie wybranym dostawcą przed zagrożeniami Mobile jako źródło informacji dla zasady zgodności i zasady dostępu warunkowego. To umożliwia administratorom IT dodać warstwę ochrony do ich zasobów firmy, takich jak Exchange i Sharepoint, w szczególności z złamania zabezpieczeń urządzeń przenośnych.

## <a name="what-problem-does-this-solve"></a>Jaki problem to rozwiązuje?

Firmy muszą ochronę danych poufnych przed zagrożeniami, w tym zagrożenia fizyczne, na podstawie aplikacji i opartych na sieci, a także luki w zabezpieczeniach systemu operacyjnego.
Historycznie firm zostały aktywnego podczas ochrony komputerów przed atakiem, gdy urządzenia przenośne Przejdź bez monitorowanych i niechronionych. Platform przenośnych mają wbudowanej ochrony, takich jak izolacja aplikacji i sprawdzonych i doświadczonych konsumentów sklepów, ale nadal narażony na ataki doświadczonej tych platform. Obecnie pracownicy więcej użyć urządzenia do pracy i muszą mieć dostęp do poufnych informacji. Urządzenia muszą być chronione przed atakami coraz bardziej zaawansowane.

[Hybrydowe wdrażania oprogramowania MDM (SCCM za pomocą usługi Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) daje możliwość kontrolowania dostępu do zasobów firmy i danych oparte na ocenie ryzyka, zapewnienie urządzenia zagrożenia ochrony, takiego jak przed zagrożeniami Mobile partnerów.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Sposób działania łączników przed zagrożeniami Mobile Intune?

Łącznik chroni zasoby firmy przez tworzenie kanału komunikacji między Intune a wybranym dostawcą przed zagrożeniami Mobile. Partnerzy przed zagrożeniami Intune Mobile oferują intuicyjne i łatwy do wdrożenia aplikacji dla urządzeń przenośnych, które aktywnie skanowania i analizowania informacji zagrożenia mogą udostępniać usługi Intune, do celów raportowania lub wymuszania. Na przykład, jeśli połączonych aplikacji przed zagrożeniami Mobile raportuje do dostawcy przed zagrożeniami Mobile czy telefon w sieci jest podłączony do sieci, co jest narażony na człowieka w ataki, te informacje jest udostępniane i podzielone na poziomie odpowiednich (niski/średniej/dużej) —, której następnie można porównać z swoje dodatki poziomu ryzyka skonfigurowany w usłudze Intune, aby określić, czy dostęp do niektórych zasobów dowolnego należy odwołany podczas urządzenie zostanie naruszony.

## <a name="sample-scenarios"></a>Przykładowe scenariusze

Gdy urządzenie jest uznawany za zainfekowany przez rozwiązanie przed zagrożeniami Mobile:

![Urządzenia przenośnego przed zagrożeniami zainfekowany](../media/mtp/MTD-image-1.png)

Dostęp jest udzielany po skorygowaniu urządzenia:

![Udzielono dostępu obrony zagrożenia telefon komórkowy](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>Następne kroki

Informacje o sposobie ochrony dostępu do zasobów firmy na podstawie urządzeń, sieci i ryzykiem aplikacji przy użyciu:

- [Ewentualnym](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
