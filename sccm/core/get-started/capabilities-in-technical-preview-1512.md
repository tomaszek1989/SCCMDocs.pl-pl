---
title: Funkcje w wersji zapoznawczej Technical Preview 1512
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersji 1512."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 7fc8729509bebdfa85efc3e181d3878f2ede620f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1512 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersji 1512. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="bkmk_devicehealth"></a> Zaświadczanie o kondycji urządzenia  
 Począwszy od wersji Technical Preview 1512, Administratorzy mogą wyświetlać stan zaświadczania o kondycji urządzenia systemu Windows 10 w konsoli programu Configuration Manager.  Ta funkcja jest dostępna dla programu Configuration Manager i Configuration Manager w usłudze Microsoft Intune. Zaświadczanie o kondycji urządzenia umożliwia administratorowi upewnienie klienta komputery mają zaufany system BIOS, modułu TPM i rozruchowe konfiguracji oprogramowania. W celu obsługi zaświadczania o kondycji urządzeń klienckich musi działać Windows 10 z włączonym modułem TPM 2. Zaświadczanie o kondycji urządzenia Wyświetla liczbę urządzeń obsługujących następujące czynniki:  

-   Usługa wczesnej ochrony przed złośliwym oprogramowaniem  

-   Funkcja BitLocker  

-   Bezpieczny rozruch  

-   Integralność kodu  

W konsoli są wyświetlane również najważniejsze brakujące ustawienia zaświadczania o kondycji z liczbą urządzeń.  

Wyświetlenie podglądu widoku zaświadczania o kondycji urządzeń, w konsoli programu Configuration Manager przejdź do **monitorowanie** roboczym kliknij **zabezpieczeń** węzeł, a następnie kliknij przycisk **zaświadczania o kondycji**.  

##  <a name="bkmk_viewterms"></a>Monitorowanie warunków i postanowień w konsoli  
Technical Preview 1512, począwszy od po zintegrowaniu programu Configuration Manager w usłudze Microsoft Intune, można użyć konsoli programu Configuration Manager, aby wyświetlić użytkowników, którzy zaakceptowali warunki i postanowienia skonfigurowane przez dział IT i użytkowników, którzy nie mają.  

**Aby wyświetlić informacje podsumowujące:**  

-   W konsoli programu Configuration Manager przejdź do **monitorowanie** > **omówienie** > **wdrożeń** i wybierz wdrożenie warunków i postanowień, który chcesz wyświetlić.  

**Aby wyświetlić szczegółowe informacje:**  

1.  W konsoli programu Configuration Manager przejdź do **zasoby i zgodność** > **omówienie** > **ustawień zgodności** > **warunków i postanowień**, a następnie wybierz warunki i postanowienia, które chcesz wyświetlić.  

2.  W dolnej części konsoli, wybierz **wdrożeń** , wybierz wdrożenie, a następnie kliknij **stanu widoku.**  

##  <a name="bkmk_EPpolicy"></a>Udoskonalenia ustawień zasad programu Endpoint Protection  
W wersji 1512 Technical Preview dodaliśmy następujące nowe ustawienia w zasadach ochrony przed złośliwym kodem Endpoint Protection:  

-   Ochrona w czasie rzeczywistym: **Blokuj potencjalnie niechciane aplikacje podczas pobierania i przed instalacją**  

    -   Potencjalnie niechciane aplikacje to klasyfikacja zagrożeń opierająca się na reputacji i wspieranej badaniami identyfikacji. Najczęściej są to niechciane narzędzia tworzące pakiety aplikacji lub pakiety aplikacji.  

    -   Ustawienie zasad ochrony jest domyślnie włączona (wartość "Tak"). Po włączeniu to ustawienie blokuje potencjalnie niechciane aplikacje podczas pobierania i instalowania. Jednak można wykluczać określonych plików lub folderów w celu spełnienia specyficznych potrzeb danego środowiska.  

-   Ustawienia skanowania: **Skanuj zamapowane dyski sieciowe podczas pełnego skanowania**  

    -   To ustawienie zapewnia większy poziom szczegółowości administratorowi dopuszczając skanowanie na żądanie plików sieciowych bez ryzyka stałego skanowania zamapowanych dysków sieciowych podczas zaplanowanego pełnego skanowania.  

    -   Ustawienie **Skanuj pliki sieciowe** najpierw musi być włączona (wartość "tak") dla tego ustawienia można było skonfigurować.  

    -   Domyślnie to ustawienie jest "Nie", co oznacza, że pełne skanowanie nie uzyska dostępu do zamapowanych dyskach sieciowych.  

-   Plik ustawień automatycznego przesyłania przykładowych:  

     Aparat ochrony przed złośliwym kodem może prosić o przesyłanie plików próbek do firmy Microsoft w celu dalszej analizy. Domyślnie przed wysłaniem takich próbek zawsze wyświetlany jest monit. Administratorzy mogą teraz zarządzać następującymi ustawieniami w celu skonfigurowania tego zachowania:  

    -   Zaawansowane: **Włącz automatyczne przesyłanie plików próbek pomóc firmie Microsoft w określeniu, czy konkretne wykryte elementy są złośliwym kodem**:  Zmień to ustawienie na "Tak", aby włączyć automatyczne przesyłanie plików próbek. Domyślnie to ustawienie jest "Nie", co oznacza, że automatyczne przesyłanie plików próbek jest wyłączone, a użytkownicy otrzymują monit przed przesłaniem próbek.   (To ustawienie została wprowadzona w System Center 2012 R2 Configuration Manager SP1)  

    -   Zaawansowane: **Zezwalaj użytkownikom na modyfikowanie ustawień automatycznego przesyłania plików przykładowych**: To ustawienie określa, czy użytkownik z uprawnieniami administratora lokalnego na urządzeniu może zmieniać ustawienie automatycznego przykładowy plik przesyłania w interfejsie klienta. Domyślnie to ustawienie jest "Nie", co oznacza, że ustawienia można zmienić tylko z poziomu konsoli programu Configuration Manager, a administratorzy lokalni na urządzeniu nie można zmienić tej konfiguracji.  

         Na przykład poniżej przedstawiono ustawienie usługi Windows Defender w systemie Windows 10 ustawionych przez administratora, jak włączone i użytkownik nie może go zmodyfikować:  

         ![TechRef &#95; WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    Ponadto istniejące **wykluczyć pliki i foldery** ustawienia w sekcji "Ustawienia wykluczania" przed złośliwym kodem endpoint protection zasad została poprawiona w celu umożliwia teraz wykluczanie urządzeń. Obecnie możesz na przykład określić następujące wykluczenie: **\device\mvfs** (dla systemu plików Multiversion File System). Zasady nie weryfikują ścieżki urządzenia; zasada programu endpoint protection są przekazywane aparatowi ochrony przed złośliwym kodem na kliencie, który musi być w stanie zinterpretować ciąg urządzenia.  

**Wymagania wstępne dotyczące korzystania z zasad programu Endpoint Protection:**  

Zanim będzie możliwe użycie zasad programu Endpoint Protection należy zainstalować i Zarządzaj klientem programu Endpoint Protection przy użyciu ustawień klienta programu Endpoint Protection. Jest to realizowane za pomocą klienta programu System Center Endpoint Protection dla systemu Windows 7, Windows 8, Windows 8.1 lub zarządzanej Windows Defender dla systemu Windows 10. Zobacz [programu Endpoint Protection w programie System Center Configuration Manager](../../protect/deploy-use/endpoint-protection.md).  
