---
title: "Kolekcje bezpieczeństwo i prywatność | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania w zakresie bezpieczeństwa i ochrony prywatności w kolekcji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 0cade975e96220e193db1de92816f97cd253532d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-collections-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność kolekcje w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera najlepsze praktyki dotyczące zabezpieczeń i ochrony prywatności dla kolekcji w programie System Center Configuration Manager.  

 Nie ma żadnych informacji prywatności specjalnie dla kolekcji w programie Configuration Manager. Kolekcje są kontenerami zasobów takich jak użytkownicy i urządzenia. Członkostwo w kolekcji często zależy od informacji programu Configuration Manager zbiera podczas normalnego działania. Na przykład za pomocą informacji o zasobie, które zostały zebrane podczas odnajdywania lub spisu, kolekcję można skonfigurować w taki sposób, aby zawierała urządzenia spełniające określone kryteria. Kolekcje mogą być również tworzone na podstawie bieżących informacji o stanie operacji zarządzania klientami, takich jak wdrażanie oprogramowania i sprawdzanie zgodności. Oprócz tych kolekcji opartych na zapytaniach użytkownicy administracyjny mogą również dodawać zasoby do kolekcji.  

 Aby uzyskać więcej informacji na temat kolekcji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md). Więcej informacji na temat wszelkie najlepsze rozwiązania i informacje o ochronie prywatności dla operacji programu Configuration Manager, których można używać do konfigurowania członkostwa w kolekcji, zobacz [najlepszych praktyk dotyczących zabezpieczeń i ochrony prywatności dla programu System Center Configuration Manager](../../../../core/plan-design/security/security-best-practices-and-privacy-information.md).  

## <a name="security-best-practices-for-collections"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące kolekcji  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące kolekcji.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas każdego eksportu lub importu kolekcji w postaci pliku MOF (Managed Object Format) zapisywanego w lokalizacji sieciowej zabezpieczaj zarówno samą lokalizację, jak i kanał sieciowy.|Ogranicz dostęp użytkowników do danego folderu sieciowego.<br /><br /> Aby zapobiec modyfikowaniu wyeksportowanych danych kolekcji przez osobę atakującą, korzystaj z podpisywania protokołu SMB lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji oraz między lokalizacją sieciową a serwerem lokacji. Używaj protokołu IPsec do szyfrowania danych w sieci, aby zapobiec ujawnieniu informacji.|  

### <a name="security-issues-for-collections"></a>Problemy z bezpieczeństwem dotyczące kolekcji  
 Z kolekcjami wiążą się następujące problemy z bezpieczeństwem:  

-   W przypadku używania zmiennych kolekcji administratorzy lokalni mogą odczytywać potencjalnie wrażliwe informacje.  

     Zmiennych kolekcji można używać podczas wdrażania systemu operacyjnego.  

