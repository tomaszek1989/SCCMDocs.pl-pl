---
title: "Certyfikatów, profil bezpieczeństwo i prywatność | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zabezpieczenia najlepszych rozwiązań do zarządzania profilami certyfikatów użytkowników i urządzeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3393db41-900a-44c5-b950-2d46a35a198c
caps.latest.revision: 7
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8a5dc7361da34f3e6b926acd35c72c0c0767ce70
ms.openlocfilehash: c51787ad3fa0bdb285017cfab1ca6931afba9ea6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-certificate-profiles-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność profilów certyfikatów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


##  <a name="security-best-practices-for-certificate-profiles"></a>Najlepsze rozwiązania dotyczące zabezpieczeń profili certyfikatów  
 Podczas zarządzania profilami certyfikatów użytkowników i urządzeń należy stosować poniższe najlepsze rozwiązania.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Należy określić i stosować wszelkie najlepsze rozwiązania dotyczące usługi rejestracji urządzeń sieciowych, co obejmuje skonfigurowanie witryny sieci Web usługi rejestracji urządzeń sieciowych w programie Internet Information Services (IIS) w celu wymagania protokołu SSL i ignorowania certyfikatów klientów.|Należy zapoznać się z tematem [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Wskazówki dotyczące usługi rejestracji urządzeń sieciowych) w bibliotece Active Directory Certificate Services w witrynie TechNet.|  
|Podczas konfigurowania profili certyfikatów SCEP należy wybrać najbardziej bezpieczne opcje obsługiwane przez urządzenia i infrastrukturę.|Należy określić, wdrożyć i stosować wszelkie najlepsze rozwiązania dotyczące bezpieczeństwa zalecone dla używanych urządzeń i infrastruktury.|  
|Należy określić koligację urządzenia użytkownika zamiast zezwalać użytkownikom na identyfikację ich urządzenia podstawowego. Ponadto nie należy włączać konfiguracji opartej na użyciu.|W przypadku kliknięcia opcji **Zezwalaj na rejestrację certyfikatu tylko na podstawowym urządzeniu użytkownika** w profilu certyfikatu SCEP nie należy traktować informacji zebranych od użytkowników lub z urządzenia jako autorytatywnych. Jeżeli po wdrożeniu profili certyfikatów SCEP z tą konfiguracją zaufany użytkownik administracyjny nie określi koligacji urządzenia użytkownika, nieautoryzowani użytkownicy mogą uzyskać podniesione uprawnienia i otrzymać certyfikaty na potrzeby uwierzytelniania.<br /><br /> **Uwaga:** Po włączeniu konfiguracji opartej na użyciu te informacje są zbierane za pomocą komunikatów stanu, które nie są zabezpieczane przez program System Center Configuration Manager. Aby ułatwić uniknięcie tego zagrożenia, należy użyć podpisywania bloku komunikatów serwera (SMB) lub protokołu IPsec między komputerami klienckimi a punktem zarządzania.|  
|Nie należy dodawać do szablonów certyfikatów uprawnień Odczytaj i Zarejestruj dla użytkowników ani konfigurować punktu rejestracji certyfikatu do pomijania sprawdzania szablonu certyfikatu.|Mimo że programu Configuration Manager obsługuje dodatkowe sprawdzanie w przypadku dodania uprawnień zabezpieczeń Odczytaj i zarejestruj dla użytkowników i konfigurowania punktu rejestracji certyfikatu do pomijania tego sprawdzania, jeśli uwierzytelnianie nie jest możliwe, żadna z tych konfiguracji jest ze względów bezpieczeństwa. Aby uzyskać więcej informacji, zobacz [Planowanie dotyczące uprawnień szablonów certyfikatów dla profilów certyfikatów w programie System Center Configuration Manager](../../protect/plan-design/planning-for-certificate-template-permissions.md).|  

## <a name="privacy-information-for-certificate-profiles"></a>Informacje o ochronie prywatności dotyczące profili certyfikatów  
 Profile certyfikatów umożliwiają wdrażanie certyfikatów głównego urzędu certyfikacji i certyfikatów klientów, a następnie ocenę, czy te urządzenia będą zgodne po zastosowaniu profili. Punkt zarządzania wysyła informacje o zgodności do serwera lokacji, a System Center Configuration Manager zapisuje je w bazie danych lokacji. Informacje o zgodności zawierają właściwości certyfikatu, takie jak nazwa podmiotu i odcisk palca. Informacje są szyfrowane, gdy urządzenia wysyłają je do punktu zarządzania. Nie są one jednak przechowywane w zaszyfrowanej postaci w bazie danych lokacji. Baza danych zachowuje te informacje do momentu usunięcia ich przez zadanie obsługi lokacji **Usuń przestarzałe dane zarządzania konfiguracją** i usuwa je po upływie domyślnego interwału wynoszącego 90 dni. Możesz skonfigurować interwał usuwania. Informacje o zgodności nie są wysyłane do firmy Microsoft.  

 Certyfikatów, profile zawierają informacje, czy program Configuration Manager zbiera przy użyciu odnajdywania. Więcej informacji dotyczących prywatności podczas odnajdywania znajduje się w sekcji **Informacje dotyczące prywatności podczas odnajdywania** w temacie [Bezpieczeństwo i ochrona prywatności w programie System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

> [!NOTE]  
>  Certyfikaty wydane użytkownikom lub urządzeniom mogą zezwalać na dostęp do poufnych informacji.  

 Domyślnie urządzenia nie oceniają profili certyfikatów. Ponadto należy skonfigurować profile certyfikatów, a następnie wdrożyć je dla użytkowników lub urządzeń.  

 Przed skonfigurowaniem profili certyfikatów należy uwzględnić wymagania dotyczące ochrony prywatności.  

