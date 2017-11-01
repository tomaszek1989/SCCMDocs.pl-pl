---
title: "Zarządzanie zawartością zabezpieczenia i prywatność"
titleSuffix: Configuration Manager
description: "Optymalizuj bezpieczeństwo i prywatność zarządzania zawartością w programie System Center Configuration Manager."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3c8bea4fde630115cfa9407822cf2313c49a60ee
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>Zabezpieczenia i prywatność zarządzania zawartością w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera informacje o bezpieczeństwie i prywatności dotyczące zarządzania zawartością w programie System Center Configuration Manager. Należy go czytać w połączeniu z następującymi tematami:  

-   [Bezpieczeństwo i prywatność zarządzania aplikacjami w programie System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [Bezpieczeństwo i prywatność aktualizacji oprogramowania w programie System Center Configuration Manager](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [Bezpieczeństwo i ochrona prywatności dotyczące wdrażania systemu operacyjnego w programie System Center Configuration Manager](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="BKMK_Security_ContentManagement"></a> Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zarządzania zawartością  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zarządzania zawartością:  

 **Punkty dystrybucji w intranecie, należy rozważyć zalety i wady używania protokołu HTTPS i HTTP**: W większości przypadków korzystanie z protokołu HTTP i pakietu kont dostępu autoryzacji zapewnia lepsze bezpieczeństwo niż używanie protokołu HTTPS z szyfrowaniem i bez autoryzacji. Jeśli jednak zawartość zawiera dane poufne, które chcesz szyfrować podczas przesyłania, należy korzystać z protokołu HTTPS.  

-   **Gdy jest używany protokół HTTPS dla punktu dystrybucji**, programu Configuration Manager za pomocą kont dostępu pakietu do autoryzowania dostępu do zawartości, ale dane są szyfrowane, gdy są przesyłane za pośrednictwem sieci.  

-   **Gdy z punktem dystrybucji jest używany protokół HTTP**, do autoryzacji dostępu można używać kont dostępu do pakietu, ale zawartość przesyłana przez sieć nie jest zaszyfrowana.  


**Jeśli punkt dystrybucji jest używany z certyfikatem uwierzytelniania klienta PKI, a nie z certyfikatem z podpisem własnym, plik certyfikatu (pfx) należy chronić silnym hasłem. W przypadku przechowywania plików w sieci, należy zabezpieczyć kanał sieci podczas importowania pliku do programu Configuration Manager**: Wymagaj hasła do importowania certyfikatu uwierzytelniania klienta, który korzysta z punktu dystrybucji do komunikowania się z punktami zarządzania, ułatwia ochronę certyfikatów przez osobę atakującą. Użyj podpisywania bloku komunikatów serwera (SMB) lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji, aby zapobiec naruszeniu pliku certyfikatu.  

**Usuń rolę punktu dystrybucji z serwera lokacji**: Domyślnie punkt dystrybucji jest zainstalowany na tym samym serwerze co serwer lokacji. Klienci nie muszą komunikować się bezpośrednio z serwerem lokacji, zatem w celu ograniczenia obszaru narażonego na ataki należy przypisać rolę punktu dystrybucji do innego systemu lokacji i usunąć go z serwera lokacji.  

**Zabezpiecz zawartość na poziomie dostępu do pakietu**: Udział punktu dystrybucji umożliwia dostęp do odczytu do wszystkich użytkowników. Aby zmniejszyć liczbę użytkowników, którzy mają dostęp do zawartości, w czasie konfigurowania punktu dystrybucji z protokołem HTTP należy włączyć konta dostępu do pakietu. To nie ma zastosowania do punktów dystrybucji w chmurze, które nie obsługują kont dostępu do pakietów. Aby uzyskać więcej informacji dotyczących kont dostępu do pakietu, zobacz [Zarządzanie kontami dostępu do zawartości](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).


**Jeśli program Configuration Manager instaluje usługi IIS podczas dodawania roli systemu lokacji punktu dystrybucji, usunąć Przekierowanie HTTP i skrypty zarządzania usługami IIS i narzędzia po ukończeniu instalacji punktu dystrybucji**: Punkt dystrybucji nie wymaga Przekierowanie HTTP i skrypty zarządzania usługami IIS i narzędzia. Aby zmniejszyć obszar ataków, należy usunąć te usługi roli dla roli Serwer sieci Web (IIS).  Aby uzyskać więcej informacji o usługach roli dla roli sieci web server (IIS) dla punktów dystrybucji, zobacz [lokacji i wymagania wstępne systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).  

**Ustaw uprawnienia dostępu do pakietu podczas tworzenia pakietu**: Ponieważ zmiany w kontach dostępu do plików pakietu zaczynają obowiązywać tylko wtedy, gdy redystrybucji pakietu, ustaw pakietu uprawnienia dostępu dokładnie podczas pierwszego tworzenia pakietu. Jest to szczególnie ważne, gdy pakiet jest duży lub dystrybuowany do wielu punktów dystrybucji i gdy przepustowość sieci na potrzeby dystrybucji zawartości jest ograniczona.  

**Wdrożenie kontroli dostępu w celu ochrony nośników zawierających wstępnie przygotowaną zawartość**: Wstępnie przygotowaną zawartość jest skompresowana, ale nie jest zaszyfrowany. Osoba atakująca może odczytać i zmodyfikować pliki, które zostaną następnie pobrane przez urządzenia. Klienci programu Configuration Manager odrzucają naruszoną zawartość naruszenia, jednak ją pobierają.  

**Importowanie z wstępnie przygotowanej zawartości przy użyciu tylko narzędzia wiersza polecenia ExtractContent (ExtractContent.exe) dostarczonego z programem Configuration Manager i upewnij się, że jest ono podpisane przez firmę Microsoft**: Aby uniknąć naruszenia danych i podniesienia uprawnień, należy używać wyłącznie autoryzowanego narzędzia wiersza polecenia dostarczonego z programem Configuration Manager.  

**Bezpieczny kanał komunikacji między serwerem lokacji a lokalizacją źródłową pakietu**: Za pomocą protokołu IPsec lub podpisywania SMB między serwerem lokacji a lokalizacją źródłową pakietu podczas tworzenia aplikacji i pakietów. Utrudni to osobie atakującej naruszenie plików źródłowych.  

**Jeśli zmienisz opcję konfiguracji lokacji do używania niestandardowej witryny sieci Web zamiast domyślnej witryny sieci Web po zainstalowaniu roli punktu dystrybucji, usuń domyślne katalogi wirtualne**: Po przełączeniu z domyślnej witryny sieci Web na niestandardową witrynę sieci Web programu Configuration Manager nie usuwa starych katalogów wirtualnych. Należy usunąć katalogi wirtualne, które utworzył jako domyślne witryny sieci Web programu Configuration Manager:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Dla punktów dystrybucji w chmurze, Chroń Szczegóły subskrypcji i certyfikaty**: Korzystając z punktów dystrybucji w chmurze, należy chronić elementy wartościowe, łącznie z nazwą użytkownika i hasło dla Twojej subskrypcji platformy Azure, certyfikat zarządzania platformy Azure i certyfikat usługi punktu dystrybucji w chmurze. Certyfikaty przechowuj w bezpieczny sposób. W przypadku przeglądania ich przez sieć podczas konfigurowania chmurowego punktu dystrybucji używaj protokołu IPsec lub podpisywania SMB między serwerem systemu lokacji a lokalizacją źródłową.  

**Dla punktów dystrybucji w chmurze: Aby utrzymać ciągłość usługi, Monitoruj daty wygaśnięcia certyfikatów**: Menedżer konfiguracji nie Ostrzegaj w przypadku importowanych certyfikatów do zarządzania chmurowych punktów dystrybucji punktu usług zbliża się termin wygaśnięcia. Należy monitorować daty wygaśnięcia niezależnie od programu Configuration Manager i upewnij się, że odnowić, a następnie zaimportować nowe certyfikaty przed datą wygaśnięcia. Jest to szczególnie ważne w przypadku zakupu programu Configuration Manager oparta na chmurze certyfikat usługi punktu dystrybucji z zewnętrznego urzędu certyfikacji (CA), ponieważ wtedy uzyskanie odnowionego certyfikatu może być konieczne.  

 Jeśli jakikolwiek certyfikat wygaśnie, Menedżer usług w chmurze generuje identyfikator komunikatu o stanie **9425** i CloudMgr.log zawierający wpis z informacją, że certyfikat **jest w stanie wygaśnięcia**, oraz datę wygaśnięcia również rejestrowane w formacie UTC.  

## <a name="security-considerations-for-content-management"></a>Zagadnienia dotyczące bezpieczeństwa zarządzania zawartością  
Podczas planowania zarządzania zawartością należy wziąć pod uwagę następujące:  

-   Klienci nie weryfikują zawartość dopiero po pobraniu jej.  

     Klienci programu Configuration Manager weryfikują wartość skrótu zawartości dopiero po pobraniu jej do swojej pamięci podręcznej. Jeśli osoba atakująca naruszy listę plików do pobrania lub samej zawartości, proces pobierania może zająć większej przepustowości sieci, tylko klientowi musiał odrzucić zawartość po napotkaniu nieprawidłowej wartości skrótu.  

-   Korzystając z punktów dystrybucji w chmurze, dostęp do zawartości jest automatycznie ograniczany do przedsiębiorstwa i nie można go ograniczyć dalej według wybranych użytkowników i grup.  

-   Korzystając z punktów dystrybucji w chmurze, klienci są uwierzytelniani przez punkt zarządzania, a następnie używają tokenu programu Configuration Manager można uzyskać dostęp do punktów dystrybucji w chmurze. Token jest ważny przez 8 godzin. Oznacza to, że jeśli zostanie zablokowany klient, ponieważ nie jest już zaufany, może kontynuować pobieranie zawartości z punktu dystrybucji w chmurze, dopóki nie upłynął okres ważności tego tokenu. W tym momencie punktu zarządzania nie będzie wystawiać inny token dla klienta, ponieważ klient jest zablokowany.  

     Aby uniknąć pobierania zawartości w tym 8 godzinnym przedziale zablokowany klient, można zatrzymać usługę chmury w **chmury** węzła, **Konfiguracja hierarchii**w **administracji** obszaru roboczego w konsoli programu Configuration Manager.  

##  <a name="BKMK_Privacy_ContentManagement"></a> Informacje o ochronie prywatności dotyczące zarządzania zawartością  
 Menedżer konfiguracji nie ma żadnych danych użytkownika do plików zawartości, jednak użytkownik administracyjny może określić w tym.  

 Przed skonfigurowaniem zarządzania zawartością należy wziąć pod uwagę wymogi związane z ochroną prywatności.  
