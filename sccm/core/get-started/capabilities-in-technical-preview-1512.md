---
title: "Możliwości w Technical Preview 1512 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1512."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5cf8d54fbaa98a75ac2a875a23a43b1d3e5be0dd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1512 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1512. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="bkmk_devicehealth"></a> Zaświadczanie o kondycji urządzenia  
 Począwszy od Technical Preview 1512, Administratorzy mogą wyświetlać stan systemu Windows 10 urządzenia kondycji zaświadczania w konsoli programu Configuration Manager.  Ta funkcja jest dostępna dla programu Configuration Manager i Configuration Manager w usłudze Microsoft Intune. Zaświadczanie kondycji urządzeń umożliwia administratorowi upewnij się, że klienta komputerów ma wiarygodnego systemu BIOS modułu TPM i ich konfiguracji oprogramowania. Do obsługi urządzeń kondycji zaświadczania, urządzeń klienckich musi być uruchomiona Win10 z włączoną 2 modułu TPM. Poświadczenie zdrowia urządzenia Wyświetla liczbę urządzeń włączone dla każdego z następujących czynności:  

-   Wczesne uruchamiania ochrony przed złośliwym oprogramowaniem  

-   Funkcja BitLocker  

-   Bezpieczny rozruch  

-   Integralności kodu  

W konsoli są wyświetlani również pierwsze brakujące ustawienia zaświadczania kondycji z liczbę urządzeń.  

Aby wyświetlić podgląd widoku zaświadczania kondycji urządzeń, w konsoli programu Configuration Manager przejdź do **monitorowanie** roboczym kliknij **zabezpieczeń** węzeł, a następnie kliknij **zaświadczania kondycji**.  

##  <a name="bkmk_viewterms"></a>W konsoli monitorowania warunki i postanowienia  
Technical Preview 1512, począwszy od po zintegrowaniu programu Configuration Manager w usłudze Microsoft Intune, można użyć konsoli programu Configuration Manager Aby wyświetlić użytkowników, którzy zaakceptowali warunki i postanowienia skonfigurowane przez dział IT i użytkowników, którzy nie mają.  

**Aby wyświetlić informacje podsumowania:**  

-   W konsoli programu Configuration Manager przejdź do **monitorowanie** > **Przegląd** > **wdrożeń** i wybierz warunki i postanowienia wdrożenie do wyświetlenia.  

**Aby wyświetlić szczegółowe informacje:**  

1.  W konsoli programu Configuration Manager przejdź do **zasoby i zgodność** > **Przegląd** > **ustawień zgodności** > **warunków i postanowień**, a następnie wybierz warunki i postanowienia, które chcesz wyświetlić.  

2.  W dolnej części konsoli, wybierz **wdrożeń** , wybierz wdrożenie, a następnie kliknij **Wyświetl stan.**  

##  <a name="bkmk_EPpolicy"></a>Ulepszenia ustawienia zasad programu Endpoint Protection  
W 1512 Technical Preview dodaliśmy następujące nowe ustawienia w zasadach ochrony przed złośliwym oprogramowaniem Endpoint Protection:  

-   Ochrona w czasie rzeczywistym: **Blokuj potencjalnie niechciane aplikacje podczas pobierania i przed instalacją**  

    -   Potencjalnie niechciane aplikacje to klasyfikacja zagrożeń opierająca się na reputacji i wspieranej badaniami identyfikacji. Najczęściej są to niechciane narzędzia tworzące pakiety aplikacji lub pakiety aplikacji.  

    -   To ustawienie zasad ochrony jest domyślnie włączona (wartość "Yes"). Po włączeniu to ustawienie blokuje potencjalnie niechciane aplikacje podczas pobierania i instalowania. Jednak można wykluczyć określone pliki lub foldery do potrzeb danego środowiska.  

-   Ustawienia skanowania: **Skanuj zamapowane dyski sieciowe podczas pełnego skanowania**  

    -   To ustawienie zapewnia większy poziom szczegółowości dla administratora zezwolić na żądanie skanowania plików sieciowych bez ryzyka zawsze skanowanie zamapowanych dyskach sieciowych podczas zaplanowanego pełnego skanowania.  

    -   Ustawienie **skanowanie plików sieciowych** najpierw musi być włączona ("tak"), to ustawienie można skonfigurować.  

    -   Domyślnie to ustawienie jest "Nie" co oznacza, że pełne skanowanie nie będzie miał dostęp do zamapowanych dyskach sieciowych.  

-   Ustawienia przesyłania plików próbki automatycznie:  

     Aparat ochrony przed złośliwym oprogramowaniem może zażądać próbki plików do wysłania do firmy Microsoft do dalszej analizy. Domyślnie przed wysłaniem takich próbek zawsze wyświetlany jest monit. Administratorzy mogą teraz zarządzać następującymi ustawieniami w celu skonfigurowania tego zachowania:  

    -   Zaawansowane: **Włącz automatyczne przesyłanie plików próbek pomóc firmie Microsoft ustalić, czy niektóre elementy wykryte złośliwym kodem**:  Zmienić to ustawienie, aby "Tak", aby włączyć automatyczne przesyłanie plików próbek. Domyślnie to ustawienie jest "Nie", która oznacza, że automatyczne przesyłanie plików próbek jest wyłączona i zostanie wyświetlony monit przed wysłaniem przykłady.   (To ustawienie było najpierw wprowadzone w programie System Center 2012 R2 Configuration Manager SP1)  

    -   Zaawansowane: **Zezwalaj użytkownikom na modyfikowanie ustawień przesyłania pliku próbki automatycznie**: To ustawienie określa, czy użytkownik z uprawnieniami lokalnego administratora na urządzeniu mogą zmieniać ustawienie przesyłanie plików próbki automatycznie interfejsu klienta. Domyślnie to ustawienie jest "Nie", która oznacza, że ustawienia można zmienić tylko z konsoli programu Configuration Manager, a administratorzy lokalni na urządzeniu nie można zmienić tej konfiguracji.  

         Na przykład poniższy kod przedstawia ustawienia usługi Windows Defender w systemie Windows 10 ustawionych przez administratora jako włączone, a użytkownik nie może zmodyfikować go:  

         ![TechRef &#95; WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    Ponadto istniejące **wykluczyć pliki i foldery** ustawienia w sekcji "Ustawienia wykluczania" endpoint protection ochrony przed złośliwym oprogramowaniem zwiększona zasady umożliwiające urządzenie wyłączenia. Obecnie możesz na przykład określić następujące wykluczenie: **\device\mvfs** (dla systemu plików Multiversion File System). Zasady nie sprawdza poprawność ścieżki urządzenia; zasady ochrony punktu końcowego jest przekazywany do aparatu ochrony przed złośliwym oprogramowaniem na komputerze klienckim, który musi być w stanie zinterpretować ciąg urządzenia.  

**Wymagania wstępne dotyczące za pomocą zasad programu Endpoint Protection:**  

Aby móc używać zasad Endpoint Protection należy zainstalować i zarządzania klientem programu Endpoint Protection przy użyciu ustawień klienta Endpoint Protection. Odbywa się to przy użyciu klienta programu System Center Endpoint Protection dla systemu Windows 7, Windows 8, Windows 8.1 lub zarządzanych Windows Defender w systemie Windows 10. Zobacz [ochrony punktu końcowego programu System Center Configuration Manager](../../protect/deploy-use/endpoint-protection.md).  

