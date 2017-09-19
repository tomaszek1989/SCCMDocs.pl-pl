---
title: "Wprowadzenie do zarządzania aplikacjami | Dokumentacja firmy Microsoft"
description: "Wykryj podstawowe informacje, które będą potrzebne do zarządzania i wdrażania aplikacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: "18"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: d92b9098eb89b8a09c39a1df13acffe694234096
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>Wprowadzenie do zarządzania aplikacjami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie omówiono podstawowe zagadnienia, które należy wiedzieć przed rozpoczęciem pracy z aplikacjami w programie System Center Configuration Manager.  

> [!TIP]  
>  Jeśli już znasz jak zarządzać aplikacjami w programie Configuration Manager, możesz pominąć ten temat i przejść do tworzenia przykładowej aplikacji. Zobacz [Tworzenie i wdrażanie aplikacji przy użyciu programu System Center Configuration Manager](../../apps/get-started/create-and-deploy-an-application.md).  

## <a name="what-is-an-application"></a>Co to jest aplikacja?  
 Mimo że *aplikacji* różni się termin powszechnie używany w przypadku komputerów w programie Configuration Manager, oznacza to, że wystąpił. Aplikację można wyobrazić sobie jako moduł. To pole zawiera jeden lub więcej zestawów plików instalacyjnych pakietu oprogramowania (nazywane **typu wdrożenia**), oraz instrukcje dotyczące sposobu wdrażania oprogramowania.  

 Podczas wdrażania aplikacji na urządzeniach typ wdrożenia instalowany na urządzeniu jest wybierany zgodnie z **wymaganiami** .  

 Możesz to zrobić dużo więcej opcji z aplikacją. Dowiesz się, te zagadnienia omówione w tym przewodniku. W poniższej tabeli zamieszczono niektóre pojęcia, które musisz wiedzieć przed rozpoczęciem szczegółowej analizy:  

|Pojęcie|Opis|    
|-|-|  
|**Requirements**|W poprzednich wersjach programu Configuration Manager często tworzono kolekcję zawierającą urządzenia, aby wdrożyć aplikację w. Mimo że nadal można utworzyć kolekcję, można określić bardziej szczegółowe kryteria dla wdrożenia aplikacji z wymaganiami.<br /><br /> Na przykład możesz określić, że aplikację można zainstalować tylko na urządzeniach z systemem Windows 10. Następnie możesz wdrożyć aplikację na urządzeniach, ale zostanie zainstalowana tylko na urządzeniach z systemem Windows 10.<br /><br /> Program Configuration Manager ocenia wymagania, aby określić, czy aplikacja oraz jej typy wdrożenia zostanie zainstalowany. Następnie program ustala odpowiedni typ wdrożenia służący do zainstalowania aplikacji. W celu zapewnienia zgodności reguły wymagań są ponownie oceniane co siedem dni, zgodnie z ustawieniem klienta **Zaplanuj ponowną ocenę dla wdrożeń**.<br /><br /> Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie aplikacji](../../apps/get-started/create-and-deploy-an-application.md).|  
|**Warunki globalne**|Wymagania są używane z określonym typem wdrożenia w pojedynczej aplikacji, można też utworzyć warunki globalne. Te są biblioteką wstępnie zdefiniowanych wymagań korzystających z dowolną aplikacją i typ wdrożenia.<br /><br /> Menedżer konfiguracji zawiera zestaw wbudowanych warunków globalnych i można także tworzyć własne.<br /><br /> Aby uzyskać więcej informacji, zobacz [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).|  
|**Wdrożenie symulowane**|Ocenia wymagania, metodę wykrywania i zależności dla aplikacji. Raportuje wyniki bez instalowania aplikacji.<br /><br /> Aby uzyskać więcej informacji, zobacz [symulowanie wdrożenia aplikacji](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Akcja wdrożenia**|Określa, czy chcesz zainstalować lub odinstalować (jeśli są obsługiwane), aplikacji jest wdrażany.<br /><br /> Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|**Cel wdrożenia**|Określa, czy wdrożenie aplikacji będzie **Wymagane**czy **Dostępne**.<br /><br /> **Wymagane** oznacza, że aplikacja zostanie wdrożona automatycznie zgodnie z harmonogramem, który został skonfigurowany. Użytkownik może jednak śledzić stan wdrożenia aplikacji (jeśli nie jest ukryty) i zainstalować aplikację przed upływem ostatecznego terminu przy użyciu programu Software Center.<br /><br /> **Dostępne** — oznacza, że jeśli aplikacja jest wdrażana dla użytkownika, użytkownik widzi opublikowaną aplikację w programie Software Center i może zainstalować ją na żądanie.<br /><br /> Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|**Poprawki**|Po wprowadzeniu zmian w aplikacji lub w typie wdrożenia, który jest zawarty w aplikacji, programu Configuration Manager utworzy nową wersję aplikacji. Można wyświetlić historię każdej poprawki aplikacji, wyświetlić jego właściwości, przywrócenie poprzedniej wersji aplikacji lub usuń starą wersję.<br /><br /> Aby uzyskać więcej informacji, zobacz [aktualizacji i wycofywanie aplikacji](../../apps/deploy-use/update-and-retire-applications.md).|  
|**Metoda wykrywania**|Metody wykrywania są używane do sprawdzania, czy wdrażana aplikacja została już zainstalowana. Jeśli metoda wykrywania potwierdza, że aplikacja jest zainstalowana, programu Configuration Manager nie próbuje zainstalować ją ponownie.<br /><br /> Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zależności**|Zależności definiują jeden lub więcej typów wdrożeń z innej aplikacji, którą należy zainstalować przed zainstalowaniem typu wdrożenia. Można ustawić zależnych typów wdrożeń można automatycznie zainstalować przed zainstalowaniem typu wdrożenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zastępowanie**|Menedżer konfiguracji umożliwia uaktualnianie lub zastępowanie istniejących aplikacji przy użyciu relacji zastępowania. Podczas zastępowania aplikacji można określić nowy typ wdrożenia w celu zastąpienia typu wdrożenia zastępowanej aplikacji. Można również określić, czy uaktualnić lub odinstalować przed aplikacji zastępującej zastępowanej aplikacji jest zainstalowana.<br /><br /> Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md).|  
|**Zarządzanie skoncentrowane na użytkowniku**|Aplikacji programu Configuration Manager obsługuje zarządzanie skoncentrowane na użytkownikach, dzięki czemu można skojarzyć określonych użytkowników z określonymi urządzeniami. Nie trzeba pamiętać nazwy urządzenia użytkownika — aplikacje można wdrożyć w ramach użytkownika i urządzenia. Ta funkcja daje pewność, że najważniejsze aplikacje zawsze są dostępne na każdym urządzeniu, do którego określony użytkownik ma dostęp. Gdy użytkownik nabędzie nowy komputer, można automatycznie zainstalować aplikacje użytkownika na urządzeniu aby zalogować się.<br /><br /> Aby uzyskać więcej informacji, zobacz [łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).|  

## <a name="what-application-types-can-you-deploy"></a>Jakiego typu aplikacje można wdrażać?  
 Menedżer konfiguracji umożliwia wdrażanie następujących typów aplikacji:  

- Instalator Windows (plik *.msi)
- Pakiet aplikacji systemu Windows (*.appx, *.appxbundle)
- Pakiet aplikacji systemu Windows (w Sklepie Windows)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Plik cabinet systemu Windows Mobile
- System macOS  


Ponadto podczas zarządzania urządzeniami za pomocą programu Microsoft Intune lub programu Configuration Manager zarządzanie urządzeniami lokalnymi, można zarządzać te dodatkowe typy aplikacji:

- Pakiet aplikacji systemu Windows Phone (plik *.xap)
- Pakiet aplikacji dla systemu iOS (plik *.ipa)
- Pakiet aplikacji dla systemu Android (plik *.apk)
- Pakiet aplikacji dla systemu Android w sklepie Google Play
- Pakiet aplikacji systemu Windows Phone (w sklepie Windows Phone Store)
- Instalator systemu Windows korzystający z funkcji zarządzania urządzeniami przenośnymi (MDM)
- Aplikacja sieci Web



## <a name="state-based-applications"></a>Aplikacje oparte na stanie  
 Aplikacji programu Configuration Manager używa monitorowanie oparte na stanie, za pomocą którego można śledzić ostatni stan wdrożenia aplikacji dla użytkowników i urządzeń. Komunikaty o stanie zawierają informacje o poszczególnych urządzeniach. Na przykład jeśli aplikacja jest wdrażana w kolekcji użytkowników, w konsoli programu Configuration Manager można wyświetlić stan zgodności oraz cel wdrożenia. Można monitorować wdrażanie każdego oprogramowania za pomocą **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager. Wdrożenia oprogramowania obejmują aktualizacje oprogramowania, ustawienia zgodności, aplikacje, sekwencje zadań oraz pakiety i programy. Aby uzyskać więcej informacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Aplikacja regularnie ponownie ocenia wdrożenia przez program Configuration Manager. Na przykład:  

-   Użytkownik końcowy odinstalował wdrożoną aplikację. W następnym cyklu oceny program Configuration Manager wykryje, że aplikacja nie jest obecny i instaluje ją ponownie.  

-   Aplikacja nie została zainstalowana na urządzeniu, ponieważ nie spełnia ono wymagań. Później na urządzeniu wprowadzono zmianę i teraz spełnia ono wymagania. Program Configuration Manager wykryje tę zmianę i aplikacja jest zainstalowana.  


 Należy określić interwał ponownej oceny wdrożenia aplikacji przy użyciu **Zaplanuj ponowną ocenę dla wdrożeń** ustawienia klienta. Aby uzyskać więcej informacji, zobacz [informacje o ustawieniach klienta](../../core/clients/deploy/about-client-settings.md).  

## <a name="get-started-creating-an-application"></a>Wprowadzenie do tworzenia aplikacji  
 Jeśli chcesz od razu i rozpoczęcie tworzenia aplikacji, można znaleźć Przewodnik tworzenia prostej aplikacji w [tworzenie i wdrażanie aplikacji](../../apps/get-started/create-and-deploy-an-application.md) tematu.  

 Jeśli znasz już podstawy i wyszukiwania, aby uzyskać szczegółowe informacje na temat wszystkich opcji dostępnych dla użytkownika, Rozpocznij od [tworzenie aplikacji](/sccm/apps/deploy-use/create-applications).  

## <a name="software-center-and-the-application-catalog"></a>Program Software Center i katalog aplikacji  
 W poprzednich wersjach programu Configuration Manager Centrum oprogramowania służyło do instalowania i planowania instalacji oprogramowania, konfigurowania ustawień zdalnego sterowania i ustawienia zarządzania energią. Użytkownicy, można połączyć z katalogu aplikacji, wyszukaj i żądania oprogramowania, ustawienie niektórych preferencji i zdalnie wyczyścić swoje urządzenia przenośne.  

 Te ustawienia są nadal dostępne w programie System Center Configuration Manager, nowa wersja programu Software Center jest teraz dostępna które pozwala przeglądać aplikacje. Nie trzeba używać katalogu aplikacji, co wymaga przeglądarki sieci web obsługującą program Silverlight. Jednak role systemu lokacji punktu witryny sieci Web wykazu aplikacji i punktu usługi sieci Web wykazu aplikacji są nadal wymagane dla aplikacji dostępnych dla użytkowników, które mają być widoczne w Centrum oprogramowania.  

 Aby uzyskać więcej informacji, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami](../../apps/plan-design/plan-for-and-configure-application-management.md).  

## <a name="configuration-manager-packages-and-programs"></a>Menedżer konfiguracji pakiety i programy  
 Menedżer konfiguracji nadal obsługuje pakiety i programy używane w poprzednich wersjach produktu. Wdrożenie korzystające z pakietów i programów może być odpowiedniejsze od wdrożenia korzystającego z aplikacji, gdy wdraża się poniższe elementy:  

-   Skrypty nieinstalujące aplikacji na komputerze, na przykład skrypt defragmentacji dysku komputera.  

-   „Jednorazowe” skrypty, które nie muszą być stale monitorowane.  

-   Skrypty uruchamiane zgodnie z cyklicznym harmonogramem, które nie mogą korzystać z globalnej ewaluacji.

 Aby uzyskać więcej informacji, zobacz [pakiety i programy](../../apps/deploy-use/packages-and-programs.md).  
