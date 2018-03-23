---
title: Wprowadzenie do ustawień zgodności
titleSuffix: Configuration Manager
description: Dowiedz się więcej o podstawowych pojęć i w jaki sposób działają ustawienia zgodności
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a8f672d4d92db8f1bd6e19c4a483b5b3107ad703
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>Wprowadzenie do ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed utworzeniem ustawień zgodności programu Configuration Manager, Dowiedz się więcej o podstawowych pojęć i zrozumieć, jak działają.  



## <a name="how-compliance-settings-work"></a>Jak działają ustawienia zgodności  
 Ustawienia zgodności umożliwiają zarządzanie konfiguracją i zgodnością klientów w organizacji.  

 Elementy konfiguracji można podzielić na dwie główne kategorie:  

-   **Ustawienia dla urządzeń, które są zarządzane przy użyciu klienta programu Configuration Manager** — zazwyczaj urządzenia, na których zainstalowane oprogramowanie klienckie programu Configuration Manager umożliwia zarządzanie urządzeniem.  

-   **Ustawienia dla urządzeń zarządzanych bez klienta programu Configuration Manager** — zwykle urządzeń, które są zarządzane w usłudze Microsoft Intune lub z programu Configuration Manager na lokalnego zarządzania urządzeniami.  



## <a name="what-devices-are-supported"></a>Obsługiwane urządzenia  

| Typ urządzenia | Więcej informacji |  
|------------|----------------------|  
| Komputery z systemem Windows (za pomocą klienta programu Configuration Manager) | Tworzenie niestandardowych elementów konfiguracji do oceny obiekty, takie jak klucze rejestru, pliki i atrybutów usługi Active Directory.<br /><br /> Użycie typu elementu konfiguracji systemu Windows 10, wybierz ustawienia ze wstępnie zdefiniowanej listy. |  
| Komputery z systemem Windows (zarejestrowane w usłudze Microsoft Intune) | Wybierz ustawienia ze wstępnie zdefiniowanej listy. |  
| urządzenia z systemem iOS (zarejestrowane w usłudze Microsoft Intune) | Wybierz ustawienia ze wstępnie zdefiniowanej listy. |  
| Urządzenia z systemem android (zarejestrowane w usłudze Microsoft Intune) | Wybierz ustawienia ze wstępnie zdefiniowanej listy. |  
| Urządzenia Windows Phone (zarejestrowane w usłudze Microsoft Intune) | Wybierz ustawienia ze wstępnie zdefiniowanej listy. |  
| Komputery Mac (za pomocą klienta programu Configuration Manager) | Tworzenie niestandardowych elementów konfiguracji do oceny obiekty, takie jak preferencje macOS i wyników zwróconych przez skrypt. |  
| Komputery Mac (zarejestrowane w usłudze Microsoft Intune) | Wybierz ustawienia ze wstępnie zdefiniowanej listy. |  



## <a name="what-is-a-configuration-item"></a>Co to jest element konfiguracji?  
 Element konfiguracji jest kontenerem, który przechowuje określone informacje. Informacje, które można skonfigurować, zależy od typu elementu konfiguracji. Elementy konfiguracji może zawierać następujące informacje:

-   **Informacje dotyczące metody wykrywania** dotyczy tylko systemu Windows elementami konfiguracji zawierającymi ustawienia aplikacji. Wykrywa, czy aplikacja jest zainstalowana. Wykrywanie używa pliku Instalatora Windows aplikacji lub przy użyciu skryptu niestandardowego.  

-   **Ustawienia** reprezentują warunki biznesowe lub techniczne oceny zgodności na urządzeniach klienckich. Skonfiguruj nowe ustawienie lub przejść do istniejącego ustawienia na komputerze odniesienia.  

-   **Zasady zgodności** określają warunki, które definiują zgodność ustawienia elementu konfiguracji. Zanim klient oceni ustawienia zgodności, musi istnieć co najmniej jedna reguła zgodności. Niektóre ustawienia korygujący niezgodne wartości. Utwórz nowe reguły lub przejść do istniejącego ustawienia w dowolnym elemencie konfiguracji i wybierz zasady w nim.  

-   **Obsługiwane platformy** są platformy urządzeń, należy zdefiniować, na którym klient oceni zgodności elementów konfiguracji. Jeśli element konfiguracji zostanie wdrożony na urządzeniu, który nie jest na liście obsługiwanych platform, nie może oszacować zgodności.  



## <a name="what-is-a-configuration-baseline"></a>Co to jest linii bazowej konfiguracji?  
 Definiowanie linii bazowej konfiguracji, który zawiera elementy konfiguracji do oceny. Także ustawienia i reguły, które opisują wymagany poziom zgodności. Importuj dane konfiguracji z pakietów konfiguracyjnych programu Configuration Manager. Firma Microsoft i innych dostawców zdefiniować te pakiety konfiguracyjne. Lub Utwórz nowe elementy konfiguracji i linie bazowe konfiguracji.  

 Po zdefiniowaniu linii bazowej konfiguracji należy wdrożyć ją do użytkowników i kolekcji urządzeń. Klient następnie oblicza podstawowe ustawienia zgodności na podstawie harmonogramu. Więcej niż jedną linię bazową konfiguracji można wdrożyć na urządzeniach. Ten poziom szczegółowości zapewnia większą kontrolę nad zgodności. 

 Urządzenia klienckie oceniają swoją zgodność z każdej linii bazowej konfiguracji wdrożonej i natychmiast raportują wyniki do witryny za pomocą komunikatów o stanie i komunikatów o stanie. Jeśli urządzenie jest obecnie połączony z siecią, ale pobrane linii bazowej konfiguracji, nadal ocenia zgodność elementów konfiguracji. Po wznowieniu połączenia wysyła informacje o zgodności.  

### <a name="monitoring-configuration-baselines"></a>Monitorowanie linii bazowych konfiguracji
- W obszarze monitorowania wyniki oceny zgodności w konsoli programu Configuration Manager **monitorowanie** obszaru roboczego w **wdrożeń** węzła. Na przykład:
    - Typowych przyczyn braku zgodności
    - błędy
    - Liczba użytkowników i urządzeń
- Uruchom raportach ustawień zgodności z dodatkowymi informacjami. Na przykład:
    - Które urządzenia są zgodne lub niezgodne
    - Który element linii bazowej konfiguracji jest powoduje, że komputer z systemem innym niż zgodności
- Wyświetl wyniki oceny zgodności systemu Windows z komputerów z zainstalowanym klientem programu Configuration Manager. Otwórz **programu Configuration Manager** panel sterowania i przejdź do **konfiguracje** kartę.  



## <a name="user-data-and-profiles-configuration-items"></a>Elementy konfiguracji danych użytkownika i profilów  
 Elementy konfiguracji danych użytkownika i profilów zawierają ustawienia określające sposób zarządzania przez użytkowników na komputerach z systemem Windows 8 lub nowszy:  
   - Przekierowanie folderu
   - Pliki trybu offline
   - Profile mobilne  

Wdróż te elementy konfiguracji do kolekcji użytkowników. Monitorować ich zgodność z **monitorowanie** węzła konsoli programu Configuration Manager. W przeciwieństwie do innych elementów konfiguracji nie należy dodawać je do linii bazowych konfiguracji przed ich wdrożeniem. Wdrożyć je bezpośrednio przez kliknięcie przycisku **Wdróż** na Wstążce.  

 Aby uzyskać więcej informacji, zobacz [utworzyć elementy konfiguracji danych użytkownika i profile](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  



## <a name="remote-connection-profiles"></a>Profile połączenia zdalnego  
 Profile połączenia zdalnego udostępniają zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie ustawień połączeń zdalnych. Przez wdrożenie tych ustawień na urządzeniach, można zminimalizować działania użytkowników końcowych wymagane w celu połączenia ich komputerów do sieci firmowej.  

Aby uzyskać więcej informacji, zobacz [utworzyć profile połączenia zdalnego](/sccm/compliance/deploy-use/create-remote-connection-profiles).  



## <a name="windows-edition-upgrade"></a>Uaktualnienie wersji systemu Windows
Zasady uaktualniania wydania automatycznie uaktualnia urządzeń, które korzystają z określonych wersji systemu Windows 10 do nowszej wersji. Ta zasada zapewnia nowego produktu licencji lub klucza pliku korzystającą z urządzenia do uaktualnienia.

Aby uzyskać więcej informacji, zobacz [urządzenia Windows uaktualnienia z wersji uaktualnienia zasad](/sccm/compliance/deploy-use/upgrade-windows-version)



## <a name="microsoft-edge-browser-profiles"></a>Profile przeglądarki Microsoft Edge
<!-- 1357310 -->
Począwszy od wersji 1802, dla klientów, którzy korzystają z [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) sieci web w przeglądarce na klientach systemu Windows 10, należy utworzyć zasady ustawień zgodności, aby skonfigurować kilka ustawień Microsoft Edge. 

Aby uzyskać więcej informacji, zobacz [profile przeglądarki Microsoft Edge](/sccm/compliance/deploy-use/browser-profiles).

