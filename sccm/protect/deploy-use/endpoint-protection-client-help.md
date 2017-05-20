---
title: Pomoc klienta programu Endpoint Protection | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat funkcji i ulepszeń Endpoint Protection pomagające lepiej chronić komputer przed zagrożeniami."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: 6
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 212c73fcb947c3b56da6055bf47fe078301ad90d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection-client-help"></a>Pomoc klienta programu Endpoint Protection

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Ta wersja programu Windows Defender lub Endpoint Protection zawiera następujące funkcje pomagające chronić komputer przed zagrożeniami:  

-   **Integracja z zaporą systemu Windows.** Konfiguracja programu Endpoint Protection umożliwia włączenie lub wyłączenie Zapory systemu Windows.  
-   **System inspekcji sieci.** Ta funkcja podnosi poziom ochrony w czasie rzeczywistym, sprawdzając ruch sieciowy, aby pomóc aktywnie blokować wykorzystywanie znanych luk w zabezpieczeniach sieciowych.  
-   **Aparat ochrony.** Ochrona w czasie rzeczywistym na znajdowaniu i zatrzymuje złośliwego oprogramowania, instalowanie i uruchamianie na komputerze. Zaktualizowany aparat oferuje udoskonalone możliwości wykrywania i oczyszczania oraz lepszą wydajność.  

Usługa Windows Defender jest dostarczane jako część systemu operacyjnego Windows 10.  W przypadku wcześniejszych wersji systemu Windows administrator systemu może udostępnić Windows Defender lub Endpoint Protection za pomocą oprogramowania do zarządzania.

Można również znaleźć listę [często zadawane pytania dotyczące programu Windows Defender i ochrony punktu końcowego](endpoint-protection-client-faq.md). Aby uzyskać pomoc dotyczącą rozwiązywania problemów, zobacz [klienta Endpoint Protection lub Rozwiązywanie problemów z usługą Windows Defender](troubleshoot-endpoint-client.md). Aby uzyskać listę nowych funkcji, zobacz [co jest nowego klienta usługi Windows Defender](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## <a name="windows-firewall-integration"></a>Integracja z Zaporą systemu Windows  
 Zapora systemu Windows może uniemożliwiać osobom atakującym lub złośliwemu oprogramowaniu uzyskanie dostępu do komputera za pośrednictwem Internetu lub sieci. Teraz podczas instalowania programu Endpoint Protection kreator instalacji sprawdza, czy Zapora systemu Windows jest włączona. Jeśli celowo wyłączono Zaporę systemu Windows, możesz zapobiec jej włączeniu, usuwając zaznaczenie pola wyboru. Ustawienia Zapory systemu Windows możesz zmienić w dowolnym momencie za pośrednictwem ustawień System i zabezpieczenia w Panelu sterowania.  

## <a name="network-inspection-system"></a>System inspekcji sieci  
 Osoby atakujące coraz częściej przeprowadzają ataki sieciowe z wykorzystaniem ujawnionych luk w zabezpieczeniach zanim dostawcy oprogramowania zdążą opracować i rozpowszechnić aktualizacje zabezpieczeń. Badania luk w zabezpieczeniach pokazują, że może upłynąć miesiąc lub nawet dłuższy czas od pierwszego raportu o ataku do opracowania, przetestowania i wydania odpowiedniej poprawki zabezpieczeń. Ta przerwa w ochronie sprawia, że wiele komputerów jest narażonych na ataki i wykorzystanie przez długi czas. System kontroli sieci działa wraz z ochroną w czasie rzeczywistym, aby lepiej chronić przed atakami sieciowymi, znacznie skracając czas między ujawnieniem luk w zabezpieczeniach i wdrożeniem aktualizacji (z kilku tygodni do kilku godzin).  

## <a name="award-winning-protection-engine"></a>Wielokrotnie nagradzany aparat ochrony  
 Pod wyciągiem Windows Defender lub Endpoint Protection jest jego aparatu ochrony cenionych, który jest regularnie aktualizowany. Aparat jest wspierany przez zespół badaczy złośliwego oprogramowania z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem reagujący na najnowsze zagrożenia ze strony złośliwego oprogramowania 24 godziny na dobę.  

## <a name="windows-defender-settings"></a>Ustawienia usługi Windows Defender
Ustawienia usługi Windows Defender, Włącz ustawienia, które pomagają chronić komputer przed złośliwym oprogramowaniem. Administrator może zarządzać niektóre ustawienia usługi Windows Defender. Można zarządzać inne osoby za pomocą ustawień usługi Windows Defender. Zaleca się włączyć ustawienia usługi Windows Defender, aby pomóc chronić komputer i dane.

Aby wyświetlić ustawienia usługi Windows Defender, wyszukaj `Windows Defender` na komputerze. Otwórz **programu Windows Defender** i wybierz **ustawienia**. Usługa Windows Defender ustawienia obejmują:
- **Ochrona w czasie rzeczywistym** — Znajdź i Zatrzymaj złośliwego oprogramowania, instalowanie i uruchamianie na komputerze.
- **Ochrona oparta na chmurze** — usługa Windows Defender wysyła informacje do firmy Microsoft o potencjalne zagrożenia bezpieczeństwa.
- **Automatyczne przesyłanie próbek** — usługa Windows Defender Zezwalaj na wysyłanie przykłady podejrzanych plików do firmy Microsoft do poprawy wykrywania złośliwego oprogramowania.
- **Wykluczenia** — można wykluczyć określone pliki, foldery, rozszerzenia plików i procesy ze skanowania programu Windows Defender.
- **Ulepszone powiadomień** -włącza powiadomień informujących o kondycji komputera. Nawet **poza** mają otrzymywać powiadomienia krytyczne.
- **Windows Defender Offline** — można uruchomić Windows Defender Offline w celu łatwiejszego znajdowania i usuwania złośliwego oprogramowania. Ten tryb skanowania uruchomi ponownie komputer i może potrwać około 15 minut.

### <a name="see-also"></a>Zobacz także  
 [Często zadawane pytania dotyczące klienta Endpoint Protection](endpoint-protection-client-faq.md)   
 [Rozwiązywanie problemów z klientem programu Windows Defender lub Endpoint Protection](troubleshoot-endpoint-client.md)

