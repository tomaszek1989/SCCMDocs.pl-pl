---
title: "Rozpoczynanie pracy z ustawieniami zgodności | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak działają ustawienia zgodności w programie System Center Configuration Manager. Poznaj także podstawowe koncepcje, które trzeba znać."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: "11"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b9f997caf5ca4753f95ab2e2cf680bdac40d29b7
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>Wprowadzenie do ustawień zgodności w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed przystąpieniem do tworzenia elementów konfiguracji programu System Center Configuration Manager, należy zapoznać się w tym temacie, aby zrozumieć, w jaki sposób działają ustawienia zgodności, a także aby dowiedzieć się więcej o podstawowych pojęciach, które będą potrzebne, aby dowiedzieć się.  

## <a name="how-compliance-settings-works"></a>Jak działają ustawienia zgodności  
 Ustawienia zgodności umożliwiają zarządzanie konfiguracją i zgodnością serwerów, laptopów, komputerów stacjonarnych i urządzeń przenośnych w organizacji.  

 Elementy konfiguracji można podzielić na dwie główne kategorie:  

-   **Ustawienia dla urządzeń, które są zarządzane przy użyciu klienta programu Configuration Manager** — zazwyczaj urządzenia, na których zainstalowane oprogramowanie klienckie programu Configuration Manager umożliwia zarządzanie urządzeniem.  

-   **Ustawienia dla urządzeń zarządzanych bez klienta programu Configuration Manager** — zwykle urządzeń, które są zarządzane w usłudze Microsoft Intune lub z programu Configuration Manager na lokalnego zarządzania urządzeniami.  

## <a name="what-devices-are-supported"></a>Obsługiwane urządzenia  


|Typ urządzenia|Więcej informacji|  
|------------|----------------------|  
|Komputery z systemem Windows (za pomocą klienta programu Configuration Manager)|Możliwe jest tworzenie niestandardowych elementów konfiguracji, które pozwalają ocenić elementy, takie jak klucze rejestru, pliki i atrybuty usługi Active Directory.<br /><br /> W przypadku używania typu elementu konfiguracji systemu Windows 10 odpowiednie ustawienia należy wybrać ze wstępnie zdefiniowanej listy.|  
|Komputery z systemem Windows (zarejestrowane w usłudze Microsoft Intune)|Wybierz potrzebne ustawienia ze wstępnie zdefiniowanej listy.|  
|urządzenia z systemem iOS (zarejestrowane w usłudze Microsoft Intune)|Wybierz potrzebne ustawienia ze wstępnie zdefiniowanej listy.|  
|Urządzenia z systemem android (zarejestrowane w usłudze Microsoft Intune)|Wybierz potrzebne ustawienia ze wstępnie zdefiniowanej listy.|  
|Urządzenia Windows Phone (zarejestrowane w usłudze Microsoft Intune)|Wybierz potrzebne ustawienia ze wstępnie zdefiniowanej listy.|  
|Komputery Mac (za pomocą klienta programu Configuration Manager)|Możliwe jest tworzenie niestandardowych elementów konfiguracji, które pozwalają ocenić elementy, takie jak wartości preferencji systemu Mac OS X (lista właściwości) oraz wyniki zwrócone przez skrypt.|  
|Komputery Mac (zarejestrowane w usłudze Microsoft Intune)|Wybierz potrzebne ustawienia ze wstępnie zdefiniowanej listy.|  

## <a name="what-is-a-configuration-item"></a>Co to jest element konfiguracji?  
 Element konfiguracji można określić jako kontener, który przechowuje następujące informacje (informacje konfigurowane w zależności od typu elementu konfiguracji):  

-   **Informacje dotyczące metody wykrywania** (dla elementów konfiguracji systemu Windows, które zawierają tylko ustawienia aplikacji) — pozwala wykryć, czy aplikacja jest zainstalowana, przez wykrycie obecności pliku Instalatora Windows aplikacji lub użycie skryptu niestandardowego.  

-   **Ustawienia** — reprezentują warunki biznesowe lub techniczne służące do oceny zgodności na urządzeniach klienckich. Możesz skonfigurować nowe ustawienie lub przejść do istniejącego ustawienia na komputerze odniesienia.  

-   **Reguły zgodności** — określają warunki, które definiują zgodność ustawienia elementu konfiguracji. Zanim będzie można ocenić ustawienie pod kątem zgodności, musi istnieć co najmniej jedna reguła zgodności. Niektóre ustawienia umożliwiają skorygowanie wartości rozpoznanych jako niezgodne. Możesz utworzyć nowe reguły lub przejść do istniejącego ustawienia w dowolnym elemencie konfiguracji, aby wybrać zawarte w nim reguły.  

-   **Obsługiwane platformy** — są to platformy urządzeń definiowane przez użytkownika, na których elementy konfiguracji będą oceniane pod kątem zgodności. Jeśli element konfiguracji zostanie wdrożony na urządzeniu, które nie znajduje się na liście obsługiwanych platform, nie zostanie on oceniony pod kątem zgodności.  

## <a name="what-is-a-configuration-baseline"></a>Co to jest linia bazowa konfiguracji?  
 Zgodność jest oceniana przez zdefiniowanie linii bazowej konfiguracji zawierającej elementy konfiguracji, które mają zostać ocenione, a także ustawienia i reguły, które opisują poziom zgodności, który musi zostać osiągnięty. Te dane konfiguracyjne można zaimportować z sieci web w Microsoft System Center Configuration Manager pakiety konfiguracyjne jako najlepsze rozwiązania, które są zdefiniowane przez firmę Microsoft i innych dostawców w programie Configuration Manager i że, a następnie zaimportować do programu Configuration Manager. Innym rozwiązaniem jest utworzenie nowych elementów konfiguracji i linii bazowych konfiguracji.  

 Po zdefiniowaniu linii bazowej konfiguracji można wdrożyć ją dla użytkowników i urządzeń za pomocą kolekcji, a następnie ocenić jej ustawienia zgodności na podstawie harmonogramu. Urządzenia mogą mieć wdrożonych wiele linii bazowych konfiguracji. Zapewnia to wysoki poziom kontroli.  

 Urządzenia klienckie oceniają swoją zgodność z każdą wdrożoną linią bazową konfiguracji i natychmiast raportują wyniki w lokacji za pomocą komunikatów o stanie i komunikatów o statusie. Jeśli urządzenie klienckie nie jest obecnie połączone z siecią, ale pobrało elementy konfiguracji, do których odwołuje się wdrożona linia bazowa konfiguracji, to linia bazowa konfiguracji jest oceniana pod kątem zgodności. Informacje o zgodności są wysyłane po ponownym nawiązaniu połączenia.  

 Można monitorować wyników zgodności oceny linii bazowej konfiguracji z **wdrożeń** w węźle **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager w celu wyświetlenia najczęstszych przyczyn braku zgodności, błędów oraz liczby użytkowników i urządzeń, których dotyczy problem. Możliwe jest również uruchomienie raportów ustawień zgodności w celu znalezienia dodatkowych szczegółów, czyli na przykład informacji o tym, które urządzenia są zgodne, a które niezgodne, a także o tym, który element linii bazowej konfiguracji powoduje, że komputer jest uznawany za niezgodny. Możesz również wyświetlić wyniki oceny zgodności z uruchomionym oprogramowaniem klienckim programu Configuration Manager za pomocą komputerów z systemem Windows **konfiguracje** karcie **programu Configuration Manager** w Panelu sterowania.  

## <a name="user-data-and-profiles-configuration-items"></a>Elementy konfiguracji danych użytkownika i profilów  
 Elementy konfiguracji danych i profilów użytkownika zawierają ustawienia określające, jak użytkownicy w hierarchii zarządzają Przekierowanie folderu, plikami trybu offline i profilami mobilnymi na komputerach z systemem Windows 8 lub nowszy. Można je wdrożyć w kolekcjach użytkowników, a następnie monitorować ich zgodność z **monitorowanie** węzła konsoli programu Configuration Manager. W przeciwieństwie do innych elementów konfiguracji, te elementy nie są dodawane do linii bazowych konfiguracji przed wdrożeniem. Możesz wdrożyć je bezpośrednio za pomocą okna dialogowego **Wdrażanie elementu konfiguracji danych użytkownika i profilów** :  

 Aby uzyskać więcej informacji, zobacz [utworzyć elementy konfiguracji danych użytkownika i profile](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

## <a name="remote-connection-profiles"></a>Profile połączenia zdalnego  
 Profile połączenia zdalnego udostępniają zestaw narzędzi i zasobów ułatwiających tworzenie, wdrażanie i monitorowanie ustawień połączeń zdalnych na urządzeniach w organizacji. Wdrażając te ustawienia, można zminimalizować działania użytkowników końcowych wymagane w celu połączenia ich komputerów z siecią firmową.  

Aby uzyskać więcej informacji, zobacz [utworzyć profile połączenia zdalnego](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

## <a name="windows-edition-upgrade"></a>Uaktualnienie wersji systemu Windows
Zasady uaktualniania wersji umożliwia automatyczne uaktualnianie urządzeń z systemem określonych wersji systemu Windows 10 do nowszej wersji, podając nowy plik licencji lub klucza produktu.

Aby uzyskać więcej informacji, zobacz [urządzenia Windows uaktualnienia z wersji uaktualnienia zasad](/sccm/compliance/deploy-use/upgrade-windows-version)
