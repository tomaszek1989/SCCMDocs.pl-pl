---
title: "Bezpieczeństwo i prywatność aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Wykonaj następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące aktualizacji oprogramowania i Dowiedz się więcej na temat obsługi informacje o ochronie prywatności w programie Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
ms.openlocfilehash: 4b4f045138abc14b6e93b3b990c5f3a8b4f2f952
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-software-updates-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera bezpieczeństwa i informacje o ochronie prywatności dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Najlepsze rozwiązania w zakresie bezpieczeństwa dotyczące aktualizacji oprogramowania  
 Podczas wdrażania aktualizacji oprogramowania na klientach należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń:  

-   Nie zmieniaj domyślnych uprawnień w pakietach aktualizacji oprogramowania.  

     Domyślnie pakiety aktualizacji oprogramowania są ustawione tak, aby zezwalać administratorom na dostęp typu **Pełna kontrola** , a użytkownikom — **Odczyt** . W przypadku zmiany tych uprawnień osoba atakująca może mieć możliwość dodawania, kasowania i usuwania aktualizacji oprogramowania.  

-   Kontroluj dostęp do lokalizacji pobierania aktualizacji oprogramowania.  

     Konta komputerów dla dostawcy programu SMS, serwera lokacji oraz użytkownika administracyjnego, który faktycznie pobiera aktualizacje oprogramowania do lokalizacji pobierania, wymagają w przypadku lokalizacji pobierania dostępu typu **Zapis** . Aby zmniejszyć ryzyko naruszenia przez osoby atakujące plików źródłowych aktualizacji oprogramowania znajdujących się w lokalizacji pobierania, należy odpowiednio ograniczyć dostęp do tej lokalizacji.  

     Dodatkowo, jeśli w lokalizacji pobierania używane są udziały UNC, należy zabezpieczyć kanał sieciowy przy użyciu protokołu IPsec lub podpisywania SMB, aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania podczas ich przesyłania przez sieć.  

-   Używaj czasu UTC podczas określania godzin wdrażania.  

     Jeśli zamiast czasu UTC używasz czasu lokalnego, może się zdarzyć, że instalacja aktualizacji oprogramowania zostanie opóźniona na komputerach użytkowników w wyniku zmiany przez nich ustawienia strefy czasowej.  

-   Włącz protokół SSL w programie WSUS i przestrzegaj najlepszych rozwiązań z zakresu zabezpieczania programu Windows Server Update Services (WSUS).  

     Określ i stosuj najlepsze rozwiązania dla wersji programu WSUS używanej z programem Configuration Manager.  

    > [!IMPORTANT]  
    >  Jeśli punkt aktualizacji oprogramowania jest skonfigurowany do komunikacji SSL z serwerem programu WSUS, na serwerze programu WSUS należy skonfigurować wirtualne katalogi główne do obsługi protokołu SSL.  

-   Włącz sprawdzanie listy CRL.  

     Domyślnie program Configuration Manager nie sprawdza listy odwołania certyfikatów (CRL) w celu weryfikacji sygnatury aktualizacji oprogramowania przed ich wdrożeniem na komputerach. Sprawdzanie listy CRL przy każdorazowym użyciu certyfikatu zapewnia lepszą ochronę przed potencjalnym użyciem odwołanego certyfikatu, jednak wprowadza opóźnienie komunikacji i konieczność dodatkowego przetwarzania danych na komputerze wykonującym weryfikację listy.  

     Aby uzyskać więcej informacji o sposobie włączania listy CRL sprawdzania dostępności aktualizacji oprogramowania, zobacz [jak włączać sprawdzanie listy CRL na potrzeby aktualizacji oprogramowania w programie System Center Configuration Manager](../get-started/manage-settings-for-software-updates.md#crl-checking-for-software-updates).  

-   Skonfiguruj program WSUS do używania niestandardowej witryny sieci web.  

     Podczas instalowania programu WSUS na punkcie aktualizacji oprogramowania jest dostępna opcja użycia istniejącej domyślnej witryny sieci Web usług IIS lub utworzenia niestandardowej witryny sieci web programu WSUS. Utwórz niestandardową witrynę sieci Web programu WSUS, tak aby usługi IIS obsługiwały usługi programu WSUS w dedykowanej wirtualnej witrynie sieci i nie udostępniały tej samej witryny sieci web, który jest używany przez inne systemy lokacji programu Configuration Manager lub inne aplikacje.  

     Aby uzyskać więcej informacji, zobacz [skonfigurować program WSUS do używania niestandardowej witryny sieci web](plan-for-software-updates.md#BKMK_CustomWebSite).  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Informacje o ochronie prywatności dotyczące aktualizacji oprogramowania  
 Aktualizacje oprogramowania skanują komputery klienckie, aby określić, które aktualizacje są wymagane, a następnie wysyłają odpowiednią informację z powrotem do bazy danych lokacji. Podczas procesu aktualizacji oprogramowania programu Configuration Manager może przesyłać informacje między klientami a serwerami, które identyfikują komputer i konta logowania.  

 Configuration Manager przechowuje informacje o stanie dotyczące procesu wdrażania oprogramowania. Informacje o stanie nie są szyfrowane podczas przesyłania ani przechowywania. Informacje o stanie są przechowywane w bazie danych programu Configuration Manager i ich usunięcia przez zadania konserwacji bazy danych. Żadne informacje o stanie nie są wysyłane do firmy Microsoft.  

 Stosowanie aktualizacji oprogramowania programu Configuration Manager do zainstalowania aktualizacji oprogramowania na komputerach klienckich mogą być narażone na postanowienia licencyjne dotyczące oprogramowania dla tych aktualizacji, które są oddzielne od postanowień licencyjnych oprogramowania System Center Configuration Manager. Zawsze przejrzeć i zaakceptować postanowienia licencyjne dotyczące oprogramowania, przed zainstalowaniem aktualizacji oprogramowania za pomocą programu Configuration Manager.  

 Menedżer konfiguracji nie implementuje aktualizacji oprogramowania domyślnie i przed zbieranych informacji wymaga podjęcia kilku czynności konfiguracyjnych.  

 Przed skonfigurowaniem aktualizacji oprogramowania należy wziąć pod uwagę wymogi związane z ochroną prywatności.  
