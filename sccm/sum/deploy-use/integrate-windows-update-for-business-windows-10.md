---

title: "Integracja z usługą Windows Update dla firmy w systemie Windows 10 | Dokumentacja firmy Microsoft"
description: "Usługi Windows Update dla firm umożliwia aktualizowanie urządzenia z systemem Windows 10 w organizacji dla urządzeń połączonych z usługą Windows Update."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 8bdbacd54632475ac69a0d0a9a34b2567c3daa13
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Integracja z usługą Windows Update dla Firm w systemie Windows 10

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Usługa Windows Update dla firm (WUfB) pozwala instalować na urządzeniach z systemem Windows 10 w organizacji najnowsze zabezpieczenia i funkcje systemu Windows, gdy te urządzenia łączą się bezpośrednio z usługą Windows Update (WU). Program Configuration Manager ma możliwość rozróżniania systemu Windows 10 komputerów, które używają WUfB i WSUS dotyczące pobierania aktualizacji oprogramowania.  

 Niektóre funkcje programu Configuration Manager nie są już dostępne w przypadku klientów programu Configuration Manager są skonfigurowane do otrzymywania aktualizacji z usługi Windows Update, która obejmuje WUfB lub wewnętrznych systemu Windows:  

-   Raportowanie zgodności z usługą Windows Update:  

    -   Program Configuration Manager będzie świadomości aktualizacji, które są opublikowane usługi Windows Update. Klienci programu Configuration Manager skonfigurowano w celu aktualizacji odebranych z usługi Windows Update będzie wyświetlana **nieznany** dla tych aktualizacji w konsoli programu Configuration Manager.  

    -   Rozwiązywanie problemów dotyczących ogólnego stan zgodności jest trudne, ponieważ stan **nieznane** był używany tylko w przypadku klientów, którzy nie zgłosili stanu skanowanie z powrotem z usług WSUS.  Teraz obejmuje również klientów programu Configuration Manager, które odbierają aktualizacje z usługi Windows Update.  

    -   Funkcja dostępu warunkowego (dla zasobów firmy) na podstawie stanu zgodności aktualizacji nie będzie działać zgodnie z oczekiwaniami w przypadku klientów, którzy otrzymywać aktualizacje z usługi Windows Update, ponieważ nigdy nie będą one spełnia zgodności z programu Configuration Manager.  

    -   Zgodność z aktualizacjami definicji jest zgłaszana w ramach raportowania ogólnej zgodności z aktualizacjami i nie będzie działać zgodnie z oczekiwaniami.  Zgodność aktualizacji definicji jest również częścią oceny dostępu warunkowego  

-   Oparte na stanie zgodności aktualizacji ogólne raportowanie programu Endpoint Protection dla programu Defender nie będzie zwracać prawidłowych wyników z powodu brakujących danych skanowania.  

-   Menedżer konfiguracji nie będzie wdrażać aktualizacje firmy Microsoft, takich jak Office, programu Internet Explorer i Visual Studio do klientów, które są połączone z WUfB otrzymywać aktualizacje.  

-   Programu Configuration Manager nie będzie można wdrożyć aktualizacje strony 3, opublikowane w programie WSUS i zarządzane za pomocą programu Configuration Manager do klientów, które są połączone z WUfB otrzymywać aktualizacje.  

-   Wdrożenie pełnego klienta programu Configuration Manager, z użyciem infrastruktury aktualizacji oprogramowania nie będzie działać dla klientów, którzy są połączone z WUfB otrzymywać aktualizacje.  

## <a name="identify-clients-that-use--wufb-for-windows-10-updates"></a>Identyfikacja klientów używających usług WUfB w celu otrzymywania aktualizacji dla systemu Windows 10  
 Użyj poniższej procedury, aby zidentyfikować klientów, którzy używają usług WUfB w celu uzyskiwania aktualizacji i uaktualnień systemu Windows 10, skonfigurować tych klientów, aby przestały używać usług WSUS w celu uzyskiwania aktualizacji i aby wdrożyć ustawienie agenta klienta w celu wyłączenia przepływu pracy aktualizacji oprogramowania dla tych klientów.  

 **Wymagania wstępne**  

-   Klienci z systemem Windows 10 Desktop Pro lub Windows 10 Enterprise Edition w wersji 1511 lub nowszej  

-   Usługi[Windows Update dla Firm](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) są wdrożone, a klienci używają usług WUfB w celu uzyskiwania aktualizacji i uaktualnień systemu Windows 10.  

#### <a name="to-identify-clients-that-use-wufb"></a>Aby zidentyfikować klientów, którzy używają usług WUfB  

1.  Wyłącz usługę Windows Update Agent, aby nie skanowała usług WSUS, jeśli była wcześniej włączona.   
    Klucz rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer** może być równe wskazują, czy komputer jest skanowanie względem WSUS lub usługi Windows Update.  Gdy wartość jest równa 2, nie jest skanowania dla usług WSUS.  

2.  Istnieje nowy atrybut **UseWUServer**w obszarze **usługi Windows Update** węzła w Eksploratorze zasobów programu Configuration Manager.  

3.  Na podstawie atrybutu **UseWUServer** utwórz kolekcję dla wszystkich komputerów połączonych za pośrednictwem usługi Windows Update dla Firm w celu uzyskiwania aktualizacji i uaktualnień.  

4.  Utwórz ustawienie agenta klienta wyłączające przepływ pracy aktualizacji oprogramowania i wdróż ustawienie w kolekcji komputerów, które są połączone bezpośrednio z usługą Windows Update dla Firm.  

5.  Komputery, które są zarządzane przez WUfB spowoduje wyświetlenie **nieznany** w stan zgodności i nie będą liczone jako część ogólnej procent.  

