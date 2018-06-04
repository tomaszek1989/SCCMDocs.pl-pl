---
title: Planowanie wdrożenia klienta na urządzeniach Windows Embedded
titleSuffix: Configuration Manager
description: Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 038e61f9-f49d-41d1-9a9f-87bec9e00d5d
caps.latest.revision: 7
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c4f3d8a9b043707340e56d3ae483ad66ca17dc10
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2018
ms.locfileid: "23134501"
---
# <a name="planning-for-client-deployment-to-windows-embedded-devices-in-system-center-configuration-manager"></a>Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

<a name="BKMK_DeployClientEmbedded"></a> Jeśli urządzenie Windows Embedded nie zawiera klienta programu System Center Configuration Manager, można użyć dowolnej metody instalacji klienta, jeśli urządzenie spełnia wymagane zależności. Jeśli urządzenie osadzone obsługuje filtry zapisu, przed zainstalowaniem klienta konieczne jest ich wyłączenie, a następnie ponowne ich włączenie po zainstalowaniu klienta i przypisaniu go do lokacji.  

 Pamiętaj, że po wyłączeniu filtrów nie należy wyłączać sterowników filtrów. Zwykle te sterowniki są uruchamiane automatycznie podczas uruchamiania komputera. Wyłączenie tych sterowników zapobiegnie instalacji klienta albo zakłóci aranżację filtru zapisu, powodując niepowodzenie działania klienta. Oto usługi skojarzone z każdym typem filtru zapisu, który nie może zostać wyłączony:  

|Typ filtru zapisu|Sterownik|Typ|Opis|  
|-----------------------|------------|----------|-----------------|  
|EWF|EWF|Jądro|Wdraża przekierowanie We/Wy na poziomie sektora na woluminach chronionych.|  
|FBWF|FBWF|System plików|Wdraża przekierowanie We/Wy na poziomie pliku na woluminach chronionych.|  
|Ujednolicony filtr zapisu|uwfreg|Jądro|Przekierowanie rejestru UWF|  
|Ujednolicony filtr zapisu|uwfs|System plików|Przekierowanie plików UWF|  
|Ujednolicony filtr zapisu|uwfvol|Jądro|Menedżer woluminów UWF|  

 Filtry zapisu decydują o sposobie aktualizowania systemu operacyjnego na urządzeniu osadzonym przy wprowadzaniu zmian, jak instalowanie oprogramowania. Gdy filtry zapisu są włączone, zmiany nie są dokonywane bezpośrednio w systemie operacyjnym, lecz zostają przekierowane do tymczasowej nakładki. Jeśli zmiany zostaną zapisane wyłącznie w nakładce, zostaną utracone po wyłączeniu urządzenia osadzonego. Jeśli filtry zapisu zostaną jednak tymczasowo wyłączone, zmiany mogą być trwałe, aby nie trzeba było ich dokonywać ponownie (lub ponownie instalować oprogramowania) przy każdym uruchamianiu urządzenia osadzonego. Tymczasowe wyłączenie i ponowne włączenie filtrów zapisu wymaga jednak co najmniej jednego ponownego uruchomienia, użytkownik będzie więc zazwyczaj chciał określić jego czas przez skonfigurowanie okien obsługi, aby ponowne uruchomienia następowały poza godzinami pracy.  

 Można skonfigurować opcje umożliwiające automatyczne wyłączenie i ponowne włączenie filtrów zapisu w trakcie wdrażania oprogramowania, takiego jak aplikacje, sekwencje zadań, aktualizacje oprogramowania i klient programu Endpoint Protection. Wyjątkiem są linie bazowe konfiguracji zawierające elementy konfiguracji, które korzystają z automatycznego korygowania. Przy takim scenariuszu korygowanie zawsze następuje w nakładce, jest więc dostępne tylko do momentu ponownego uruchomienia urządzenia. Korygowanie zostanie zastosowane ponownie w następnym cyklu szacowania, ale tylko w nakładce, która zostanie wyczyszczona po ponownym uruchomieniu. Aby wymusić zatwierdzenie zmian korygowania przez program Configuration Manager, można wdrożyć podstawę konfiguracji, a następnie inne wdrożenie oprogramowania obsługujące zatwierdzenie zmiany najszybciej, jak to możliwe.  

 Jeśli filtry zapisu są wyłączone, można zainstalować oprogramowanie na urządzeniach Windows Embedded za pomocą Centrum oprogramowania. Jednak jeśli filtry zapisu są włączone, instalacja nie powiedzie się i programu Configuration Manager wyświetla komunikat o błędzie, że użytkownik ma niewystarczające uprawnienia do instalowania aplikacji.  

> [!WARNING]  
>  Nawet jeśli nie wybierzesz opcji programu Configuration Manager, aby zatwierdzić zmiany, zmiany mogą zostać zatwierdzone, jeśli inna instalacja oprogramowania lub zmiana zatwierdzi zmiany. Przy takim scenariuszu oprócz nowych zmian zostaną również zatwierdzone pierwotne zmiany.  

 Gdy program Configuration Manager wyłączy filtry zapisu, aby zmiany były trwałe, tylko użytkownicy z lokalnymi uprawnieniami administracyjnymi może zalogować się i korzystać z urządzenia osadzonego. W tym okresie użytkownicy z niskimi uprawnieniami będą zablokowani i zobaczą komunikat, że komputer jest niedostępny z powodu trwającego serwisowania, co pomaga chronić urządzenie w stanie, w którym zmiany mogą być trwale zastosowane. Ta blokada w trybie obsługi jest kolejnym powodem, dla którego należy skonfigurować okno obsługi w okresie, w którym użytkownicy nie będą logować się na tych urządzeniach.  

 Program Configuration Manager obsługuje zarządzanie następującymi typami filtrów zapisu:  

-   Na podstawie pliku filtru zapisu (FBWF) — Aby uzyskać więcej informacji, zobacz [filtrów zapisu opartych na plikach](http://go.microsoft.com/fwlink/?LinkID=204717).  

-   Rozszerzony zapisu filtru (EWF) pamięci RAM — Aby uzyskać więcej informacji, zobacz [Enhanced Write Filter](http://go.microsoft.com/fwlink/?LinkId=204718).  

-   Ujednolicony filtr zapisu (UWF) — Aby uzyskać więcej informacji, zobacz [ujednolicony filtr zapisu](http://go.microsoft.com/fwlink/?LinkId=309236).  

 Gdy urządzenie Windows Embedded jest w trybie EWF RAM reg. programu Configuration Manager nie obsługuje operacji filtrów zapisu.  

> [!IMPORTANT]  
>  Jeśli jest to możliwe, Użyj filtrów zapisu opartych na plikach (FBWF) z programu Configuration Manager w celu zwiększenia wydajności i skalowalności.
>
> **Urządzenia używające tylko plikach:** Skonfiguruj następujące wyjątki, aby zachować stan klienta i dane spisu między ponownymi uruchomieniami urządzeń:  
>   
>  -   CCMINSTALLDIR\\\*.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
>  Urządzenia z systemem Windows Embedded 8.0 i nowszym nie obsługują wykluczeń zawierających symbole wieloznaczne. Na tych urządzeniach musisz pojedynczo skonfigurować następujące wykluczenia:  
>   
>  -   Wszystkie pliki w lokalizacji CCMINSTALLDIR z rozszerzeniem sdf. Zwykle są to:  
>   
>     -   UserAffinityStore.sdf  
>     -   InventoryStore.sdf  
>     -   CcmStore.sdf  
>     -   StateMessageStore.sdf  
>     -   CertEnrollmentStore.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
> **Urządzenia używające plikach i UWF tylko:** Gdy klienci w grupie roboczej korzystają z certyfikatów do uwierzytelniania punktów zarządzania, musisz również wykluczyć klucz prywatny, aby upewnić się, że klient w dalszym ciągu do komunikowania się z punktem zarządzania. Na tych urządzeniach skonfiguruj następujące wyjątki:  
>   
>  -   c:\Windows\System32\Microsoft\Protect  
> -   c:\ProgramData\Microsoft\Crypto  
> -   HKEY_LOCAL_MACHINE\Software\Microsoft\SystemCertificates\SMS\Certificates  

 Przykładowy scenariusz wdrażania i zarządzania nimi włączonymi filtrami zapisu Windows Embedded, zobacz urządzeń w programie Configuration Manager [przykładowy scenariusz wdrażania i zarządzania klientami programu System Center Configuration Manager na urządzeniach Windows Embedded](../../../../core/clients/deploy/example-scenario-for-deploying-and-managing-clients-on-windows-embedded-devices.md).  

 Więcej informacji o sposobie tworzenia obrazów dla urządzeń Windows Embedded i konfigurowania filtrów zapisu znajduje się w dokumentacji platformy Windows Embedded. Odpowiednie informacje można także uzyskać od producenta OEM.  

> [!NOTE]  
>  Po wybraniu odpowiednich platform wdrażania oprogramowania i elementów konfiguracji zamiast określonych wersji zostaną wyświetlone rodziny Windows Embedded. Należy użyć następującej listy, aby przypisać określoną wersję platformy Windows Embedded do opcji w polu listy.  
>   
>  -   **Wbudowane systemy operacyjne oparte na systemie Windows XP (32-bitowym)** :  
>   
>      -   Windows XP Embedded  
>     -   Windows Embedded for Point of Service  
>     -   Windows Embedded Standard 2009  
>     -   Windows Embedded POSReady 2009  
> -   **Wbudowane systemy operacyjne oparte na systemie Windows 7 (32-bitowym)** :  
>   
>      -   Windows Embedded Standard 7 (32-bitowy)  
>     -   Windows Embedded POSReady 7 (32-bitowy)  
>     -   Windows ThinPC  
> -   **Wbudowane systemy operacyjne oparte na systemie Windows 7 (64-bitowym)** :  
>   
>      -   Windows Embedded Standard 7 (64-bitowy)  
>     -   Windows Embedded POSReady 7 (64-bitowy)
