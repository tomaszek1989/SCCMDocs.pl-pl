---
title: Pomoc klienta programu Endpoint Protection | Dokumentacja firmy Microsoft
description: "Dowiedz się o funkcjach i rozszerzeniach w programie Endpoint Protection, które lepiej chronić komputer przed zagrożeniami."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: "6"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 212c73fcb947c3b56da6055bf47fe078301ad90d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="endpoint-protection-client-help"></a>Pomoc klienta programu Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Ta wersja programu Windows Defender lub program Endpoint Protection obejmuje następujące funkcje, aby pomóc chronić komputer przed zagrożeniami:  

-   **Integracja z zaporą systemu Windows.** Konfiguracja programu Endpoint Protection umożliwia włączenie lub wyłączenie Zapory systemu Windows.  
-   **System inspekcji sieci.** Ta funkcja podnosi poziom ochrony w czasie rzeczywistym, sprawdzając ruch sieciowy, aby pomóc aktywnie blokować wykorzystywanie znanych luk w zabezpieczeniach sieciowych.  
-   **Aparat ochrony.** Ochrona w czasie rzeczywistym znajduje i zatrzymuje złośliwego oprogramowania, instalowanie i uruchamianie na komputerze. Zaktualizowany aparat oferuje udoskonalone możliwości wykrywania i oczyszczania oraz lepszą wydajność.  

Usługa Windows Defender jest dostarczane jako część systemu operacyjnego Windows 10.  We wcześniejszych wersjach systemu Windows administrator systemu może udostępnić usługę Windows Defender lub program Endpoint Protection przy użyciu oprogramowania do zarządzania.

Możesz także znaleźć listę [często zadawane pytania dotyczące usługi Windows Defender oraz programu Endpoint Protection](endpoint-protection-client-faq.md). Aby uzyskać pomoc w rozwiązywaniu problemów, zobacz [Rozwiązywanie problemów z usługi Windows Defender lub program Endpoint Protection klienta](troubleshoot-endpoint-client.md). Aby uzyskać listę nowych funkcji, zobacz [co jest nowego klienta usługi Windows Defender](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## <a name="windows-firewall-integration"></a>Integracja z Zaporą systemu Windows  
 Zapora systemu Windows może uniemożliwiać osobom atakującym lub złośliwemu oprogramowaniu uzyskanie dostępu do komputera za pośrednictwem Internetu lub sieci. Teraz podczas instalowania programu Endpoint Protection kreator instalacji sprawdza, czy Zapora systemu Windows jest włączona. Jeśli celowo wyłączono Zaporę systemu Windows, możesz zapobiec jej włączeniu, usuwając zaznaczenie pola wyboru. Ustawienia Zapory systemu Windows możesz zmienić w dowolnym momencie za pośrednictwem ustawień System i zabezpieczenia w Panelu sterowania.  

## <a name="network-inspection-system"></a>System inspekcji sieci  
 Osoby atakujące coraz częściej przeprowadzają ataki sieciowe z wykorzystaniem ujawnionych luk w zabezpieczeniach zanim dostawcy oprogramowania zdążą opracować i rozpowszechnić aktualizacje zabezpieczeń. Badania luk w zabezpieczeniach pokazują, że może upłynąć miesiąc lub nawet dłuższy czas od pierwszego raportu o ataku do opracowania, przetestowania i wydania odpowiedniej poprawki zabezpieczeń. Ta przerwa w ochronie sprawia, że wiele komputerów jest narażonych na ataki i wykorzystanie przez długi czas. System kontroli sieci działa wraz z ochroną w czasie rzeczywistym, aby lepiej chronić przed atakami sieciowymi, znacznie skracając czas między ujawnieniem luk w zabezpieczeniach i wdrożeniem aktualizacji (z kilku tygodni do kilku godzin).  

## <a name="award-winning-protection-engine"></a>Wielokrotnie nagradzany aparat ochrony  
 Pod maską programu Windows Defender lub program Endpoint Protection jest jej wielokrotnie nagradzany aparat ochrony, który jest regularnie aktualizowany. Aparat jest wspierany przez zespół badaczy złośliwego oprogramowania z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem reagujący na najnowsze zagrożenia ze strony złośliwego oprogramowania 24 godziny na dobę.  

## <a name="windows-defender-settings"></a>Ustawienia usługi Windows Defender
Ustawienia usługi Windows Defender włączyć ustawienia, które pomagają chronić komputer przed złośliwym oprogramowaniem. Administrator może zarządzać niektóre ustawienia usługi Windows Defender. Można zarządzać za pomocą ustawień usługi Windows Defender innych użytkowników. Firma Microsoft zaleca się, że w przypadku włączenia ustawień usługi Windows Defender w celu ochrony komputera i danych.

Aby wyświetlić ustawienia usługi Windows Defender, wyszukaj `Windows Defender` na komputerze. Otwórz **usługa Windows Defender** i wybierz **ustawienia**. Ustawienia usługi Windows Defender obejmują:
- **Ochrona w czasie rzeczywistym** — Znajdź i Zatrzymaj złośliwego oprogramowania, instalowanie i uruchamianie na komputerze.
- **Ochrony opartej na chmurze** — usługa Windows Defender wysyła informacje do firmy Microsoft o potencjalnych zagrożeniach.
- **Automatyczne przesyłanie próbek** — Zezwalaj usłudze Windows Defender Wyślij próbki plików podejrzane do firmy Microsoft, aby pomóc w udoskonalaniu wykrywania złośliwego oprogramowania.
- **Wykluczenia** — można wykluczyć określone pliki, foldery, rozszerzeń plików i procesy skanowania usługa Windows Defender.
- **Ulepszone powiadomień** — umożliwia powiadomień, które informują o kondycję komputera. Nawet **poza** będzie otrzymywał powiadomienia krytyczne.
- **Windows Defender Offline** — można uruchomić Windows Defender offline w celu łatwiejszego znajdowania i usuwania złośliwego oprogramowania. Ten tryb skanowania uruchomi ponownie komputer i może potrwać około 15 minut.

### <a name="see-also"></a>Zobacz także  
 [Klient programu Endpoint Protection — często zadawane pytania](endpoint-protection-client-faq.md)   
 [Rozwiązywanie problemów z klientem usługi Windows Defender lub program Endpoint Protection](troubleshoot-endpoint-client.md)
