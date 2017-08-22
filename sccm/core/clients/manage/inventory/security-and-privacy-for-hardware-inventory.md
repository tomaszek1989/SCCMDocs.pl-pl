---
title: "Ochrona prywatności zabezpieczeń spisu sprzętu | Dokumentacja firmy Microsoft"
description: "Pobierz informacje o bezpieczeństwie i prywatności dotyczące spisu sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62e20d86-db6d-4a1f-b14a-905a9de31698
caps.latest.revision: "6"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: ec182ec3102e0f4ae8bcf3d1ef843b25510b6ce6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-hardware-inventory-in-system-center-configuration-manager"></a>Zabezpieczenia i prywatność spisu sprzętu w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera informacje o bezpieczeństwie i prywatności dotyczące spisu sprzętu w programie System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Najlepsze rozwiązania dotyczące zabezpieczeń spisu sprzętu  
 Poniżej przedstawiono najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zbierania danych spisu sprzętu od klientów:  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podpisywanie i szyfrowanie danych spisu|Gdy klienci komunikują się z punktami zarządzania przy użyciu protokołu HTTPS, wszystkie wysyłane dane są szyfrowane przy użyciu protokołu SSL. Jeśli jednak komputery klienckie komunikują się z punktami zarządzania w intranecie za pomocą protokołu HTTP, dane spisu klientów i zebrane pliki mogą być wysyłane bez podpisu i szyfrowania. Upewnij się, że lokacja jest skonfigurowana w celu wymagania podpisu i szyfrowania. Ponadto w przypadku klientów obsługujących algorytm SHA-256 wybierz opcję określającą, że jest wymagany algorytm SHA-256.|  
|Nie zbieraj plików IDMIF i NOIDMIF w środowiskach o wysokim poziomie zabezpieczeń|Dzięki zbieraniu plików IDMIF i NOIDMIF można rozszerzyć zbieranie spisu sprzętu. W razie potrzeby programu Configuration Manager tworzy nowe tabele lub modyfikuje istniejące tabele w bazie danych programu Configuration Manager, aby zapewnić dostosowanie do właściwości w plikach IDMIF i NOIDMIF. Jednak programu Configuration Manager nie można zweryfikować pliki IDMIF i NOIDMIF, dlatego tych plików może służyć do zmodyfikowania tabel, których nie chcesz zmienić. Prawidłowe dane mogą zostać zastąpione przez nieprawidłowe dane. Ponadto można było dodać dużych ilości danych i przetwarzanie tych danych może powodować opóźnienia wszystkich funkcji programu Configuration Manager. Aby ograniczyć te zagrożenia, należy skonfigurować ustawienie klienta spisu sprzętu **Zbierz pliki MIF** na wartość **Brak**.|  

### <a name="security-issues-for-hardware-inventory"></a>Problemy z zabezpieczeniami dotyczące spisu sprzętu  
 Zbieranie spisu powoduje wystąpienie potencjalnych luk w zabezpieczeniach. Osoby atakujące mogą wykonywać następujące czynności:  

-   Wysyłanie nieprawidłowych danych, które zostaną zaakceptowane przez punkt zarządzania nawet wtedy, gdy ustawienie klienta spisu oprogramowania jest wyłączone i zbieranie plików nie jest włączone.  

-   Wysyłanie bardzo dużej ilości danych w jednym pliku i w wielu plikach, co może prowadzić do odmowy usługi.  

-   Dostęp do informacji o spisie podczas ich wysyłania do programu Configuration Manager.  

 Ponieważ użytkownik z lokalnymi uprawnieniami administracyjnymi może wysłać dowolne informacje jako dane spisu, nie należy traktować danych spisu, zebranych przez program Configuration Manager jako wiarygodnych.  

 Spis sprzętu jest domyślnie włączony w ustawieniach klienta.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Informacje o ochronie prywatności dotyczące spisu sprzętu  
 Spis sprzętu umożliwia pobieranie dowolnych informacji przechowywanych w rejestrze i w usłudze WMI na klientach programu Configuration Manager. Spis oprogramowania pozwala odnaleźć wszystkie pliki określonego typu lub zebrać określone pliki od klientów. Analiza zasobów zwiększa możliwości spisu przez rozszerzenie spisu sprzętu i oprogramowania oraz dodanie nowych funkcji zarządzania licencjami.  

 Spis sprzętu jest domyślnie włączony w ustawieniach klienta, a zbierane informacje usługi WMI zależą od wybranych opcji. Spis oprogramowania jest domyślnie włączony, ale pliki nie są domyślnie zbierane. Zbieranie danych przez funkcję analizy zasobów jest automatycznie włączone, jednak można wybrać klasy raportowania spisu sprzętu do włączenia.  

 Informacje dotyczące spisu nie są wysyłane do firmy Microsoft. Informacje dotyczące spisu są przechowywane w bazie danych programu Configuration Manager. Jeśli klienci łączą się z punktami zarządzania przy użyciu protokołu HTTPS, dane spisu wysyłane do lokacji są szyfrowane podczas przesyłania. Jeśli klienci łączą się z punktami zarządzania przy użyciu protokołu HTTP, możesz włączyć szyfrowanie spisu. Dane spisu nie są przechowywane w zaszyfrowanym formacie w bazie danych. Informacje są przechowywane w bazie danych do czasu ich usunięcia przez uruchamiane co 90 dni zadania konserwacji lokacji **Usuń przestarzałą historię spisu** i **Usuń przestarzałe zgromadzone pliki** . Możesz skonfigurować interwał usuwania.  

 Przed skonfigurowaniem spisu sprzętu, spisu oprogramowania, zbierania plików lub zbierania danych przez funkcję analizy zasobów należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  
