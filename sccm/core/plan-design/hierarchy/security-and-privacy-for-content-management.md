---
title: "Zawartość zarządzania bezpieczeństwo i prywatność | Dokumentacja firmy Microsoft"
description: "Optymalizuj bezpieczeństwo i prywatność zarządzania zawartością w programie System Center Configuration Manager."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 46af86ef8b18a8a7c4dfa593b3daf8235081b104
ms.openlocfilehash: c4b9d13079c313879c6d43b10867c616fa962668
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>Zabezpieczenia i prywatność zarządzania zawartością w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera informacje o zabezpieczeniach i prywatności dotyczące zarządzania zawartością w programie System Center Configuration Manager. Należy go czytać w połączeniu z następującymi tematami:  

-   [Bezpieczeństwo i prywatność zarządzania aplikacjami w programie System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [Bezpieczeństwo i prywatność aktualizacji oprogramowania System Center Configuration Manager](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [Bezpieczeństwo i ochrona prywatności dotyczące wdrażania systemu operacyjnego w programie System Center Configuration Manager](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="BKMK_Security_ContentManagement"></a> Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zarządzania zawartością  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zarządzania zawartością:  

 **Punkty dystrybucji w intranecie, należy rozważyć wady i zalety korzystania z protokołu HTTPS i HTTP**: W większości przypadków korzystanie z protokołu HTTP i pakietu kont dostępu autoryzacji zapewnia lepsze bezpieczeństwo niż używanie protokołu HTTPS z szyfrowaniem bez autoryzacji. Jeśli jednak zawartość zawiera dane poufne, które chcesz szyfrować podczas przesyłania, należy korzystać z protokołu HTTPS.  

-   **Gdy jest używany protokół HTTPS dla punktu dystrybucji**, Menedżer konfiguracji nie używa konta dostępu do pakietu do autoryzowania dostępu do zawartości, ale zawartość jest zaszyfrowana, jest przesyłana przez sieć.  

-   **Gdy z punktem dystrybucji jest używany protokół HTTP**, do autoryzacji dostępu można używać kont dostępu do pakietu, ale zawartość przesyłana przez sieć nie jest zaszyfrowana.  


**Jeśli punkt dystrybucji jest używany z certyfikatem uwierzytelniania klienta PKI, a nie z certyfikatem z podpisem własnym, plik certyfikatu (pfx) należy chronić silnym hasłem. W przypadku przechowywania plików w sieci, należy zabezpieczyć kanał sieci podczas importowania pliku do programu Configuration Manager**: Wymagaj hasła do importowania certyfikatu uwierzytelniania klienta, który korzysta z punktu dystrybucji do komunikowania się z punktami zarządzania, ułatwia ochronę certyfikatów przez atakującymi. Aby zapobiec naruszeniu pliku certyfikatu przez osobę atakującą, użyj podpisywania bloku komunikatów serwera (SMB) lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji.  

**Usuń rolę punktu dystrybucji z serwera lokacji**: Domyślnie punkt dystrybucji jest zainstalowany na tym samym serwerze co serwer lokacji. Klienci nie muszą komunikować się bezpośrednio z serwerem lokacji, zatem w celu ograniczenia obszaru narażonego na ataki należy przypisać rolę punktu dystrybucji do innego systemu lokacji i usunąć go z serwera lokacji.  

**Zabezpiecz zawartość na poziomie dostępu do pakietu**: Udział punktu dystrybucji umożliwia dostęp do odczytu dla wszystkich użytkowników. Aby zmniejszyć liczbę użytkowników, którzy mają dostęp do zawartości, w czasie konfigurowania punktu dystrybucji z protokołem HTTP należy włączyć konta dostępu do pakietu. To nie ma zastosowania do punktów dystrybucji w chmurze, które nie obsługują kont dostępu do pakietu. Aby uzyskać więcej informacji dotyczących kont dostępu do pakietu, zobacz [Zarządzanie kontami dostępu do zawartości](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).


**Jeśli program Configuration Manager instaluje usługi IIS podczas dodawania roli systemu lokacji punktu dystrybucji, Usuń Przekierowanie HTTP lub skrypty zarządzania usługami IIS i narzędzia po zakończeniu instalacji punktu dystrybucji**: Punkt dystrybucji nie wymaga Przekierowanie HTTP lub narzędzia i skrypty zarządzania usług IIS. Aby zmniejszyć obszar ataków, należy usunąć te usługi roli dla roli Serwer sieci Web (IIS).  Aby uzyskać więcej informacji dotyczących usługi roli dla roli sieci web server (IIS) dla punktów dystrybucji, zobacz [lokacji i wymagań wstępnych systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).  

**Ustaw uprawnienie dostępu do pakietu podczas tworzenia pakietu**: Ponieważ zmiany w kontach dostępu do plików pakietu zaczynają obowiązywać tylko wtedy, gdy ponownej dystrybucji pakietu, pakietu dostępu należy ostrożnie przydzielać uprawnienia podczas pierwszego tworzenia pakietu. Jest to szczególnie ważne, gdy pakiet jest duży lub dystrybuowany do wielu punktów dystrybucji i gdy przepustowość sieci na potrzeby dystrybucji zawartości jest ograniczona.  

**Implementowanie kontroli dostępu w celu ochrony nośników zawierających wstępnie przygotowaną zawartość**: Wstępnie przygotowana zawartość jest skompresowana, ale nie są szyfrowane. Osoba atakująca może odczytać i zmodyfikować pliki, które zostaną następnie pobrane przez urządzenia. Klienci programu Configuration Manager odrzucić zawartość, która jest naruszone, jednak ją pobierają.  

**Importowanie wstępnie przygotowanej zawartości przy użyciu tylko narzędzia wiersza polecenia ExtractContent (ExtractContent.exe), który jest dostarczany z programem Configuration Manager i upewnij się, że jest ono podpisane przez firmę Microsoft**: Aby uniknąć naruszenia danych i podniesienia uprawnień, należy używać wyłącznie autoryzowanego narzędzia wiersza polecenia dostarczonego z programem Configuration Manager.  

**Zabezpiecz kanał komunikacji między serwerem lokacji a lokalizacją źródłową pakietu**: Używaj protokołu IPsec lub podpisywania SMB między serwerem lokacji a lokalizacją źródłową pakietu podczas tworzenia aplikacji i pakietów. Utrudni to osobie atakującej naruszenie plików źródłowych.  

**Zmiana opcji konfiguracji lokacji do używania niestandardowej witryny sieci Web zamiast domyślnej witryny sieci Web po zainstalowaniu roli punktu dystrybucji, usuń domyślne katalogi wirtualne**: Po przełączeniu z domyślnej witryny sieci Web do niestandardowej witryny sieci Web programu Configuration Manager nie usuwa starych katalogów wirtualnych. Należy usunąć katalogi wirtualne, które utworzył jako domyślne witryny sieci Web programu Configuration Manager:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Dla punktów dystrybucji w chmurze, Chroń Szczegóły subskrypcji i certyfikaty**: Korzystając z punktów dystrybucji w chmurze, chronić elementy o wysokiej wartości w tym nazwę użytkownika i hasło dla Twojej subskrypcji platformy Azure, certyfikat zarządzania Azure i certyfikat usługi punktu dystrybucji w chmurze. Certyfikaty przechowuj w bezpieczny sposób. W przypadku przeglądania ich przez sieć podczas konfigurowania chmurowego punktu dystrybucji używaj protokołu IPsec lub podpisywania SMB między serwerem systemu lokacji a lokalizacją źródłową.  

**Punkty dystrybucji w chmurze: Aby utrzymać ciągłość usługi, Monitoruj daty wygaśnięcia certyfikatów**: Configuration Manager nie ostrzega, że gdy zaimportowane certyfikaty zarządzania chmurowych punktów dystrybucji, punkt usług jesteś wygaśnie. Należy monitorować daty wygaśnięcia niezależnie od programu Configuration Manager i upewnij się, że odnowić, a następnie zaimportować nowe certyfikaty przed upływem daty wygaśnięcia. Jest to szczególnie ważne w przypadku zakupu programu Configuration Manager chmurze certyfikat usługi punktu dystrybucji z zewnętrznego urzędu certyfikacji (CA), ponieważ wtedy uzyskanie odnowionego certyfikatu może być konieczne.  

 Jeśli jakikolwiek certyfikat wygaśnie, Menedżer usług w chmurze generuje identyfikator komunikatu o stanie **9425** i plik CloudMgr.log zawiera wpis, aby wskazać, że certyfikat **jest w stanie wygaśnięcia**, oraz datę wygaśnięcia także rejestrowane w formacie UTC.  

## <a name="security-considerations-for-content-management"></a>Zagadnienia dotyczące bezpieczeństwa zarządzania zawartością  
Planowanie zarządzania zawartością, Uwzględnij następujące kwestie:  

-   Klienci weryfikują zawartość dopiero po jej pobraniu.  

     Klienci programu Configuration Manager weryfikują wartość skrótu zawartości dopiero po pobraniu jej do swojej pamięci podręcznej. Jeśli osoba atakująca naruszy listę pobieranych plików lub za pomocą samej zawartości, proces pobierania może zająć większej przepustowości sieci, tylko klient musiał odrzucić zawartość po napotkaniu nieprawidłowej wartości skrótu.  

-   Korzystając z punktów dystrybucji w chmurze, dostępu do zawartości jest automatycznie ograniczany do przedsiębiorstwa i nie można go ograniczyć dalej według wybranych użytkowników i grup.  

-   Korzystając z punktów dystrybucji w chmurze, klienci są uwierzytelniani przez punkt zarządzania, a następnie użyj tokenu programu Configuration Manager dostępu do punktów dystrybucji w chmurze. Token jest ważny przez 8 godzin. Oznacza to, że jeśli klient jest zablokowany, ponieważ nie jest już zaufany, może kontynuować pobieranie zawartości z punktu dystrybucji w chmurze dopiero po wygaśnięciu okresu ważności tokenu. W tym momencie punkt zarządzania nie wydaje klientowi kolejnego tokenu dla klienta, ponieważ klient jest zablokowany.  

     Aby uniknąć pobierania zawartości w tym 8 godzinnym przedziale zablokowanego klienta, można zatrzymać usługę chmury w **chmury** węzła, **Konfiguracja hierarchii**w **administracji** obszaru roboczego w konsoli programu Configuration Manager.  

##  <a name="BKMK_Privacy_ContentManagement"></a> Informacje o ochronie prywatności dotyczące zarządzania zawartością  
 Menedżer konfiguracji nie ma żadnych danych użytkownika do plików zawartości, jednak użytkownik administracyjny może określić w tym celu.  

 Przed skonfigurowaniem zarządzania zawartością należy wziąć pod uwagę wymogi związane z ochroną prywatności.  

