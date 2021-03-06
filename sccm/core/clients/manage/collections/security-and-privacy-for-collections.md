---
title: Kolekcje zabezpieczenia i prywatność
titleSuffix: Configuration Manager
description: Pobierz najlepsze rozwiązania w zakresie zabezpieczeń i prywatności w kolekcji w programie System Center Configuration Manager.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b9b19cfcddc2f477a5e70e8f3d25c3eb0c207814
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="security-and-privacy-for-collections-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera najlepsze rozwiązania i informacje o ochronie prywatności dotyczące kolekcji w programie System Center Configuration Manager.  

 Nie ma żadnych informacji prywatności dla kolekcji w programie Configuration Manager. Kolekcje są kontenerami zasobów takich jak użytkownicy i urządzenia. Członkostwo w kolekcji często zależy od informacji programu Configuration Manager zbiera podczas normalnego działania. Na przykład za pomocą informacji o zasobie, które zostały zebrane podczas odnajdywania lub spisu, kolekcję można skonfigurować w taki sposób, aby zawierała urządzenia spełniające określone kryteria. Kolekcje mogą być również tworzone na podstawie bieżących informacji o stanie operacji zarządzania klientami, takich jak wdrażanie oprogramowania i sprawdzanie zgodności. Oprócz tych kolekcji opartych na zapytaniach użytkownicy administracyjny mogą również dodawać zasoby do kolekcji.  

 Aby uzyskać więcej informacji o kolekcjach, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md). Aby uzyskać więcej informacji na temat wszelkie najlepsze rozwiązania i informacje o ochronie prywatności dla operacji programu Configuration Manager, które mogą służyć do konfigurowania członkostwa w kolekcji, zobacz [najlepszych rozwiązań dotyczących zabezpieczeń i prywatności informacji programu System Center Configuration Manager](../../../../core/plan-design/security/security-best-practices-and-privacy-information.md).  

## <a name="security-best-practices-for-collections"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące kolekcji  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące kolekcji.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas każdego eksportu lub importu kolekcji w postaci pliku MOF (Managed Object Format) zapisywanego w lokalizacji sieciowej zabezpieczaj zarówno samą lokalizację, jak i kanał sieciowy.|Ogranicz dostęp użytkowników do danego folderu sieciowego.<br /><br /> Aby zapobiec modyfikowaniu wyeksportowanych danych kolekcji przez osobę atakującą, korzystaj z podpisywania protokołu SMB lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji oraz między lokalizacją sieciową a serwerem lokacji. Używaj protokołu IPsec do szyfrowania danych w sieci, aby zapobiec ujawnieniu informacji.|  

### <a name="security-issues-for-collections"></a>Problemy z bezpieczeństwem dotyczące kolekcji  
 Z kolekcjami wiążą się następujące problemy z bezpieczeństwem:  

-   W przypadku używania zmiennych kolekcji administratorzy lokalni mogą odczytywać potencjalnie wrażliwe informacje.  

     Zmiennych kolekcji można używać podczas wdrażania systemu operacyjnego.  
