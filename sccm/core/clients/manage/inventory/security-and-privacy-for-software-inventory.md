---
title: "Zachowania zabezpieczeń spisu oprogramowania | Dokumentacja firmy Microsoft"
description: "Pobierz bezpieczeństwa i ochrony prywatności informacji dotyczących spisu oprogramowania System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e68e1fb-a8ec-4543-bb8a-cbbaf184a418
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 7652e46d2168e2de623fa8e6d5b8663701764244
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-software-inventory-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność spisu oprogramowania System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera informacje o zabezpieczeniach i prywatności spisu oprogramowania System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące spisu oprogramowania  
 Poniżej przedstawiono najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zbierania danych spisu oprogramowania od klientów:  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podpisywanie i szyfrowanie danych spisu|Gdy klienci komunikują się z punktami zarządzania przy użyciu protokołu HTTPS, wszystkie wysyłane dane są szyfrowane przy użyciu protokołu SSL. Jeśli jednak komputery klienckie komunikują się z punktami zarządzania w intranecie za pomocą protokołu HTTP, dane spisu klientów i zebrane pliki mogą być wysyłane bez podpisu i szyfrowania. Upewnij się, że lokacja jest skonfigurowana w celu wymagania podpisu i szyfrowania. Ponadto w przypadku klientów obsługujących algorytm SHA-256 wybierz ustawienie wymagające algorytmu SHA-256.|  
|Nie używaj funkcji zbierania plików do zbierania plików krytycznych lub poufnych informacji|Zapasy oprogramowania Configuration Manager korzysta z praw konta System lokalny, które umożliwia zbieranie kopii krytycznych plików systemowych, takich jak rejestru lub bazy danych kont zabezpieczeń. Jeśli te pliki są dostępne na serwerze lokacji, użytkownik z prawami odczytu zasobów lub prawami systemu NTFS do lokalizacji przechowywanych plików może przeanalizować ich zawartość i rozpoznać ważne informacje dotyczące klienta, które mogą umożliwić naruszenie jego zabezpieczeń.|  
|Ograniczanie lokalnych praw administracyjnych na komputerach klienckich|Użytkownik z lokalnymi prawami administracyjnymi może wysyłać nieprawidłowe dane jako informacje dotyczące spisu.|  

### <a name="security-issues-for-software-inventory"></a>Spis oprogramowania — problemy z zabezpieczeniami  
 Zbieranie spisu ujawnia potencjalne luki w zabezpieczeniach. Osoby atakujące mogą wykonywać następujące czynności:  

-   Wysyłanie nieprawidłowych danych, które zostaną zaakceptowane przez punkt zarządzania nawet wtedy, gdy ustawienie klienta spisu oprogramowania jest wyłączone i zbieranie plików nie jest włączone.  

-   Wysyłanie bardzo dużej ilości danych w jednym pliku i w wielu plikach, co może prowadzić do odmowy usługi.  

-   Dostęp do informacji o spisie podczas transferu do programu Configuration Manager.  

 Jeśli użytkownicy wiedzą, że mogą utworzyć ukryty plik o nazwie **Skpswi.dat** i umieścić go w katalogu głównym na dysku twardym klienta w celu wykluczenia go ze spisu oprogramowania, nie będzie można zebrać danych spisu oprogramowania z tego komputera.  

 Ponieważ użytkownik z lokalnymi uprawnieniami administracyjnymi może wysyłać żadnych informacji jako magazynu danych, nie należy traktować dane spisu, które są zbierane przez program Configuration Manager jako autorytatywnych.  

 Spis oprogramowania jest domyślnie włączony w ustawieniach klienta.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Informacje o ochronie prywatności dotyczące spisu oprogramowania  
 Spis sprzętu pozwala pobrać wszystkie informacje, które są przechowywane w rejestrze i w usłudze WMI na klientach programu Configuration Manager. Spis oprogramowania pozwala odnaleźć wszystkie pliki określonego typu lub zebrać określone pliki od klientów. Analiza zasobów zwiększa możliwości spisu przez rozszerzenie spisu sprzętu i oprogramowania oraz dodanie nowych funkcji zarządzania licencjami.  

 Spis sprzętu jest domyślnie włączony w ustawieniach klienta, a zbierane informacje usługi WMI zależą od wybranych opcji. Spis oprogramowania jest domyślnie włączony, ale pliki nie są domyślnie zbierane. Zbieranie danych przez funkcję analizy zasobów jest automatycznie włączone, jednak można wybrać klasy raportowania spisu sprzętu do włączenia.  

 Informacje dotyczące spisu nie są wysyłane do firmy Microsoft. Informacje o spisie są przechowywane w bazie danych programu Configuration Manager. Jeśli klienci łączą się z punktami zarządzania przy użyciu protokołu HTTPS, dane spisu wysyłane do lokacji są szyfrowane podczas przesyłania. Jeśli klienci łączą się z punktami zarządzania przy użyciu protokołu HTTP, możesz włączyć szyfrowanie spisu. Dane spisu nie są przechowywane w zaszyfrowanym formacie w bazie danych. Informacje są przechowywane w bazie danych do czasu ich usunięcia przez uruchamiane co 90 dni zadania konserwacji lokacji **Usuń przestarzałą historię spisu** i **Usuń przestarzałe zgromadzone pliki** . Możesz skonfigurować interwał usuwania.  

 Przed skonfigurowaniem spisu sprzętu, spisu oprogramowania, zbierania plików lub zbierania danych przez funkcję analizy zasobów należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

