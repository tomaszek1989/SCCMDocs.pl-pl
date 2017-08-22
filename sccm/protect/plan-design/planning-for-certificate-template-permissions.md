---
title: "Planowanie uprawnień szablonów certyfikatów | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat planowania uprawnień, które należy skonfigurować szablony certyfikatów, które korzysta z programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 832be8c9fda727804f57e83768cd8799db722c67
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="planning-for-certificate-template-permissions-for-certificate-profiles-in-system-center-configuration-manager"></a>Planowanie dotyczące uprawnień szablonów certyfikatów dla profilów certyfikatów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Poniższe informacje ułatwiają planowanie konfigurowania uprawnień dla szablonów certyfikatów, które System Center Configuration Manager korzysta podczas wdrażania profilów certyfikatów.  

## <a name="default-security-permissions-and-considerations"></a>Domyślne uprawnienia zabezpieczeń i kwestie związane z zabezpieczeniami  
 Domyślne uprawnienia zabezpieczeń, które są wymagane dla szablonów certyfikatów, które System Center Configuration Manager będzie używać do żądania certyfikatów dla użytkowników i urządzeń, są następujące:  

-   Odczytaj i Zarejestruj w przypadku konta, które jest używane przez pulę aplikacji usługi rejestracji urządzeń sieciowych  

-   Odczytu dla konta, na którym jest uruchomiona konsola programu System Center Configuration Manager  

 Aby uzyskać więcej informacji o tych uprawnieniach zabezpieczeń, zobacz [Konfigurowanie infrastruktury certyfikatów](../deploy-use/certificate-infrastructure.md).  

 W przypadku używania tej domyślnej konfiguracji użytkownicy i urządzenia nie mogą bezpośrednio żądać certyfikatów z szablonów certyfikatów, a wszystkie żądania muszą być inicjowane przez usługę rejestracji urządzeń sieciowych. Jest to ważne ograniczenie, ponieważ te szablony certyfikatów muszą zostać skonfigurowane z podmiotem **Dostarcz w żądaniu** , który oznacza, że istnieje ryzyko, iż certyfikatu żąda użytkownik podszywający się pod innego użytkownika lub urządzenie ze złamanymi zabezpieczeniami. W domyślnej konfiguracji takie żądanie musi być inicjowane przez usługę rejestracji urządzeń sieciowych. Jednak ryzyko podszywania się nadal istnieje, jeśli zostaną naruszone zabezpieczenia usługi, która uruchamia usługę rejestracji urządzeń sieciowych. Aby uniknąć tego ryzyka, należy przestrzegać wszystkich najlepszych rozwiązań z zakresu bezpieczeństwa związanych z usługą rejestracji urządzeń sieciowych oraz komputerem, na którym jest uruchomiona ta usługa roli.  

 Jeśli domyślne uprawnienia zabezpieczeń nie spełniają wymagań biznesowych, istnieje inna opcja konfigurowania uprawnień zabezpieczeń w szablonach certyfikatów: Możesz dodać odczytu i rejestrowania uprawnień dla użytkowników i komputerów.  

## <a name="adding-read-and-enroll-permissions-for-users-and-computers"></a>Dodawanie uprawnień Odczytaj i Zarejestruj dla użytkowników i komputerów  
 Dodawanie do odczytu i uprawnień Zarejestruj dla użytkowników i komputerów może być odpowiednie, jeśli zarządza oddzielny zespół zespołu infrastruktury urzędu certyfikacji i który oddzielnych zespół chce System Center Configuration Manager, aby sprawdzić, czy użytkownicy mają prawidłowe konto usług domenowych w usłudze Active Directory przed wysłaniem do nich profilu certyfikatu w celu zażądania certyfikatu użytkownika. W przypadku tej konfiguracji należy określić co najmniej jedną grupę zabezpieczeń, która zawiera użytkowników, a następnie przydzielić im uprawnienia Odczytaj i Zarejestruj względem szablonów certyfikatów. W tym scenariuszu kontrolą zabezpieczeń zarządza administrator urzędu certyfikacji.  

 Również w tym przypadku można określić co najmniej jedną grupę zabezpieczeń, która zawiera konta komputerów, a następnie przydzielić tym grupom uprawnienia Odczytaj i Zarejestruj względem szablonów certyfikatów. W przypadku wdrożenia profilu certyfikatu komputera na komputerze, który jest członkiem domeny, konto tego komputera musi mieć przydzielone uprawnienia Odczytaj i Zarejestruj. Te uprawnienia nie są wymagane, jeśli komputer nie jest częścią domeny memberâ€ "na przykład, jeśli jest to komputer grupy roboczej lub osobiste urządzenie przenośne.  

 Mimo ze w tej konfiguracji są stosowane dodatkowe kontrole bezpieczeństwa, nie zalecamy jej jako najlepszego rozwiązania. Przyczyną jest to, że zdefiniowani użytkownicy lub właściciele tych urządzeń mogą żądać certyfikatów niezależnie z programu System Center Configuration Manager i podaj wartości dla podmiotu certyfikatu, które mogą być wykorzystane do podszywania się pod innego użytkownika lub urządzenia.  

 Dodatkowo, jeśli zostaną wskazane konta, których nie można uwierzytelnić w momencie odebrania żądania certyfikatu, takie żądanie domyślnie zakończy się niepowodzeniem. Na przykład żądanie certyfikatu nie powiedzie się, jeśli serwer, na którym jest uruchomiona usługa rejestracji urządzeń sieciowych, znajduje się w niezaufanym lesie usługi Active Directory zawierającym serwer systemu lokacji punktu rejestracji certyfikatu. Punkt rejestracji certyfikatu można skonfigurować tak, aby kontynuował pracę w sytuacji, gdy konta nie można uwierzytelnić z powodu braku odpowiedzi z kontrolera domeny. Nie jest to jednak najlepsze rozwiązanie bezpieczeństwa.  

 Należy pamiętać, że jeśli punkt rejestracji certyfikatu jest skonfigurowany do sprawdzania uprawnień konta, a kontroler domeny jest dostępny i odrzuca żądanie uwierzytelnienia (na przykład jeśli konto jest zablokowane lub zostało usunięte), żądanie rejestracji certyfikatu zakończy się niepowodzeniem.  

#### <a name="to-check-for-read-and-enroll-permissions-for-users-and-domain-member-computers"></a>Aby sprawdzić uprawnienia Odczytaj i Zarejestruj dla użytkowników i komputerów będących członkami domeny  

1.  Na serwerze systemu lokacji, który jest hostem punktu rejestracji certyfikatu Utwórz następujący klucz rejestru DWORD o wartości 0: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  

2.  Jeśli konta nie można uwierzytelnić z powodu braku odpowiedzi z kontrolera domeny, ale chcesz ominąć sprawdzanie uprawnień:  

    -   Na serwerze systemu lokacji, który jest hostem punktu rejestracji certyfikatu Utwórz następujący klucz rejestru DWORD o wartości 1: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  

3.  Na urzędzie wystawiającym certyfikaty, na karcie **Zabezpieczenia** we właściwościach szablonu certyfikatu, dodaj co najmniej jedną grupę zabezpieczeń, aby przydzielić kontom użytkowników lub urządzeń uprawnienia Odczytaj i Zarejestruj.  
