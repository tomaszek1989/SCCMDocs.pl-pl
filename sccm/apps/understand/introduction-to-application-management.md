---
title: "Wprowadzenie do zarządzania aplikacjami | Dokumentacja firmy Microsoft"
description: "Odnajduje podstawowe informacje, które będą potrzebne do zarządzania i wdrażania aplikacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: robstackmsft
ms.author: robstack
manager: angrobe
experimental: true
experiment_id: rob-table-161101
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5aef08865b232ff2dacec6906098bebf4e42e6b1
ms.openlocfilehash: 699adb5fac0c625c321db011af6989cc4c0778ec
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>Wprowadzenie do zarządzania aplikacjami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie dowiesz się podstawowe informacje, które należy wiedzieć przed rozpoczęciem pracy z aplikacjami programu System Center Configuration Manager.  

> [!TIP]  
>  Jeśli już znasz jak zarządzać aplikacjami w programie Configuration Manager, można pominąć ten temat i przejdź do tworzenia przykładowej aplikacji. Zobacz [Tworzenie i wdrażanie aplikacji przy użyciu programu System Center Configuration Manager](../../apps/get-started/create-and-deploy-an-application.md).  

## <a name="what-is-an-application"></a>Co to jest aplikacja?  
 Mimo że *aplikacji* to termin powszechnie używanych w przypadku komputerów w programie Configuration Manager, oznacza to coś innego. Aplikację można wyobrazić sobie jako moduł. To pole zawiera co najmniej jeden zestaw plików instalacyjnych pakietu oprogramowania (znane jako **typu wdrożenia**), oraz instrukcje dotyczące wdrażania oprogramowania.  

 Podczas wdrażania aplikacji na urządzeniach typ wdrożenia instalowany na urządzeniu jest wybierany zgodnie z **wymaganiami** .  

 Oczywiście istnieje wiele zastosowań aplikacji. Zostały one omówione w tym przewodniku. W poniższej tabeli zamieszczono informacje dotyczące pojęć, z którymi należy zapoznać się przed rozpoczęciem szczegółowej analizy. Niektóre z tych pojęć dotyczą tylko niektórych tworzonych aplikacji:  

|Pojęcie|Opis|    
|-|-|  
|**Requirements**|W poprzednich wersjach programu Configuration Manager należy utworzyć często zawierająca urządzenia chcesz wdrożyć aplikację w kolekcji. Nadal można to robić, ale obecnie jest to rzadziej potrzebne, ponieważ można bardziej szczegółowo określać kryteria instalowania aplikacji.<br /><br /> Na przykład możesz określić, że aplikację można zainstalować tylko na urządzeniach z systemem Windows 10. Następnie możesz wdrożyć aplikację na wszystkich swoich urządzeniach, ale zostanie ona zainstalowana tylko na urządzeniach z systemem Windows 10.<br /><br /> Program Configuration Manager ocenia wymagania, aby określić, czy aplikacja oraz jej typy wdrożenia zostanie zainstalowany. Następnie program ustala odpowiedni typ wdrożenia służący do zainstalowania aplikacji. W celu zapewnienia zgodności reguły wymagań są ponownie oceniane co siedem dni, zgodnie z ustawieniem klienta **Zaplanuj ponowną ocenę dla wdrożeń**.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [tworzenia i wdrażania aplikacji](../../apps/get-started/create-and-deploy-an-application.md).|  
|**Warunki globalne**|Gdy wymagania są używane w ramach określonego typu wdrożenia w jednej aplikacji, można również utworzyć warunków globalnych. Są to biblioteka wstępnie zdefiniowanych wymagań, które można używać z dowolnej aplikacji i typu wdrożenia.<br /><br /> Menedżer konfiguracji zawiera zestaw wbudowanych warunki globalne, a można także tworzyć własne.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).|  
|**Wdrożenie symulowane**|Oblicza wymagania, metoda wykrywania i zależności dla aplikacji. Raportuje wyniki bez faktycznego instalowania aplikacji.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [symulowania wdrożenia aplikacji](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Akcja wdrożenia**|Określa, czy chcesz zainstalować lub odinstalować (jeśli są obsługiwane), wdrażania aplikacji.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|**Cel wdrożenia**|Określa, czy wdrożenie aplikacji będzie **Wymagane**czy **Dostępne**.<br /><br /> **Wymagane** oznacza, że aplikacja jest wdrożona automatycznie zgodnie z harmonogramem, który został skonfigurowany. Użytkownik może jednak śledzić stan wdrożenia aplikacji (jeśli nie jest ukryty) i zainstalować aplikację przed upływem ostatecznego terminu przy użyciu programu Software Center.<br /><br /> **Dostępne** — oznacza, że jeśli aplikacja jest wdrażana dla użytkownika, użytkownik widzi opublikowaną aplikację w programie Software Center i może zainstalować ją na żądanie.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|**Poprawki**|Po wprowadzeniu zmian w aplikacji lub w typie wdrożenia, który jest zawarty w aplikacji, Configuration Manager utworzy nową wersję aplikacji. Można wyświetlić historię każdej poprawki aplikacji, wyświetlając jego właściwości, przywrócenie poprzedniej wersji aplikacji lub usuń starą wersję.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [aktualizacji i wycofywania aplikacji](../../apps/deploy-use/update-and-retire-applications.md).|  
|**Metoda wykrywania**|Metody wykrywania są używane do sprawdzania, czy wdrażana aplikacja została już zainstalowana. Jeśli metoda wykrywania wskazuje, że aplikacja jest zainstalowana, Menedżer konfiguracji nie próbuje zainstalować ją ponownie.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zależności**|Zależności definiują jeden lub więcej typów wdrożeń z innej aplikacji, którą należy zainstalować przed zainstalowaniem typu wdrożenia. Można ustawić zależnych typów wdrożeń można automatycznie zainstalować przed zainstalowaniem typu wdrożenia.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zastępowanie**|Menedżer konfiguracji umożliwia uaktualnianie lub zastępowanie istniejących aplikacji przy użyciu relacji zastępowania. Podczas zastępowania aplikacji można określić nowy typ wdrożenia w celu zastąpienia typu wdrożenia zastępowanej aplikacji. Można również określić, czy należy uaktualnić lub odinstalować przed aplikacji zastępującej zastępowanej aplikacji jest zainstalowana.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zarządzanie skoncentrowane na użytkowniku**|Aplikacji programu Configuration Manager obsługuje zarządzanie skoncentrowane na użytkowniku, umożliwiając można skojarzyć określonych użytkowników z określonymi urządzeniami. Nie trzeba pamiętać nazwy urządzenia użytkownika — aplikacje można wdrożyć w ramach użytkownika i urządzenia. Ta funkcja daje pewność, że najważniejsze aplikacje zawsze są dostępne na każdym urządzeniu, do którego określony użytkownik ma dostęp. Gdy użytkownik nabędzie nowy komputer, można automatycznie zainstalować jego aplikacje na urządzeniu aby zalogować się.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [łącze użytkowników i urządzeń dzięki koligacji urządzenia użytkownika](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).|  

## <a name="what-application-types-can-you-deploy"></a>Jakiego typu aplikacje można wdrażać?  
 Menedżer konfiguracji umożliwia wdrażanie następujących typów aplikacji:  

- Instalator Windows (plik *.msi)
- Pakiet aplikacji systemu Windows (*.appx, *.appxbundle)
- Pakiet aplikacji systemu Windows (w Sklepie Windows)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Plik cabinet systemu Windows Mobile
- macOS  


Ponadto podczas zarządzania urządzeniami za pośrednictwem Microsoft Intune lub programu Configuration Manager lokalnego zarządzania urządzeniami można zarządzać te dodatkowe typy aplikacji:

- Pakiet aplikacji systemu Windows Phone (plik *.xap)
- Pakiet aplikacji dla systemu iOS (plik *.ipa)
- Pakiet aplikacji dla systemu Android (plik *.apk)
- Pakiet aplikacji dla systemu Android w sklepie Google Play
- Pakiet aplikacji systemu Windows Phone (w sklepie Windows Phone Store)
- Instalator systemu Windows korzystający z funkcji zarządzania urządzeniami przenośnymi (MDM)
- Aplikacja sieci Web



## <a name="state-based-applications"></a>Aplikacje oparte na stanie  
 Aplikacje programu Configuration Manager korzystają z monitorowanie oparte na stanie, za pomocą którego można śledzić ostatni stan wdrożenia aplikacji dla użytkowników i urządzeń. Komunikaty o stanie zawierają informacje o poszczególnych urządzeniach. Na przykład jeśli aplikacja jest wdrażana w kolekcji użytkowników, w konsoli programu Configuration Manager można wyświetlić stan zgodności oraz cel wdrożenia. Można monitorować wdrażanie każdego oprogramowania za pomocą **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager. Wdrożenia oprogramowania obejmują aktualizacje oprogramowania, ustawienia zgodności, aplikacje, sekwencje zadań oraz pakiety i programy. Aby uzyskać więcej informacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Aplikacja regularnie ponownie ocenia wdrożenia przez program Configuration Manager. Na przykład:  

-   Użytkownik końcowy odinstalował wdrożoną aplikację. W następnym cyklu oceny program Configuration Manager wykryje, aplikacja nie jest obecny i zainstaluje go ponownie.  

-   Aplikacja nie została zainstalowana na urządzeniu, ponieważ nie spełnia ono wymagań. Później na urządzeniu wprowadzono zmianę i teraz spełnia ono wymagania. Menedżer konfiguracji wykrywa te zmiany, a aplikacja jest zainstalowana.  


 Interwał ponownej oceny wdrożenia aplikacji można ustawić za pomocą **Zaplanuj ponowną ocenę dla wdrożeń** ustawienia klienta. Aby uzyskać więcej informacji, zobacz [informacje o ustawieniach klienta](../../core/clients/deploy/about-client-settings.md).  

## <a name="get-started-creating-an-application"></a>Wprowadzenie do tworzenia aplikacji  
 Jeśli chcesz razu i rozpocząć tworzenie aplikacji znajdują się wskazówki do tworzenia prostej aplikacji w [tworzenia i wdrażania aplikacji](../../apps/get-started/create-and-deploy-an-application.md) tematu.  

 Jeśli znasz już podstawy i wyszukiwania, aby uzyskać szczegółowe informacje na temat wszystkich dostępnych opcji, Rozpocznij od [tworzenia aplikacji](/sccm/apps/deploy-use/create-applications).  

## <a name="software-center-and-the-application-catalog"></a>Program Software Center i katalog aplikacji  
 W poprzednich wersjach programu Configuration Manager Centrum oprogramowania zostało użyte do zainstalowania i zaplanować instalacji oprogramowania, skonfigurować ustawienia zdalnego sterowania i ustawienia zarządzania energią. Użytkowników można połączyć z katalogu aplikacji wyszukiwanie i wysyłać żądania dotyczące oprogramowania, ustawić niektóre preferencje i zdalne czyszczenie urządzeń przenośnych.  

 Te ustawienia są nadal dostępne w programie System Center Configuration Manager, nowa wersja programu Software Center jest teraz dostępna które pozwala przeglądać w poszukiwaniu aplikacji. Nie trzeba używać katalogu aplikacji, co wymaga przeglądarki sieci web obsługującej program Silverlight. Jednak role systemu lokacji punktu witryny sieci Web wykazu aplikacji i punktu usługi sieci Web wykazu aplikacji są nadal wymagane dla aplikacji dostępnych dla użytkowników, które mają być widoczne w Centrum oprogramowania.  

 Aby uzyskać więcej informacji, zobacz [planowanie i skonfigurować zarządzanie aplikacjami](../../apps/plan-design/plan-for-and-configure-application-management.md).  

## <a name="configuration-manager-packages-and-programs"></a>Menedżer konfiguracji pakietów i programów  
 Menedżer konfiguracji nadal obsługuje pakiety i programy, które były używane w poprzednich wersjach produktu. Wdrożenie korzystające z pakietów i programów może być odpowiedniejsze od wdrożenia korzystającego z aplikacji, gdy wdraża się poniższe elementy:  

-   Skrypty nieinstalujące aplikacji na komputerze, na przykład skrypt defragmentacji dysku komputera.  

-   „Jednorazowe” skrypty, które nie muszą być stale monitorowane.  

-   Skrypty uruchamiane zgodnie z cyklicznym harmonogramem, które nie mogą korzystać z globalnej ewaluacji.

 Aby uzyskać więcej informacji, zobacz [pakietów i programów](../../apps/deploy-use/packages-and-programs.md).  

