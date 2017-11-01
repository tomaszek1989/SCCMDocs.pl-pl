---
title: "System Center Configuration Manager privacy statement — informacje dodatkowe"
description: "Więcej informacji na temat jak firma Microsoft zbiera i korzysta z danych z wdrożenia programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 28caf163507692ad7d7b3cfa85536a88d94584ec
ms.sourcegitcommit: 18ac58374d2d513fe2a197c80f7c8c6890a7d612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2017
---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>Dodatkowe informacje o ochronie prywatności dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="updates-and-servicing"></a>Aktualizacje i obsługa
System Center Configuration Manager wprowadzono nowy model aktualizacji, która ułatwia dbanie o najnowsze aktualizacje i funkcje wdrożenia programu Configuration Manager. Podczas instalacji, ta funkcja dodaje nowa rola systemu lokacji, która została wywołana punkt połączenia usługi na serwerze lokacji, który wybiera administrator. Aby uzyskać więcej informacji o zebranych informacji i sposobie ich użycia zobacz sekcję danych użycia w tym artykule.


## <a name="usage-data"></a>Dane użycia
System Center Configuration Manager zbiera dane diagnostyczne i dane użycia o sobie, które firma Microsoft używa do poprawy obsługi instalacji, jakości i bezpieczeństwa przyszłych wersji.
Dane diagnostyczne i dane użycia jest włączone dla każdej hierarchii programu System Center Configuration Manager. Składa się z zapytań programu SQL Server, które są uruchamiane co tydzień w każdej lokacji głównej i centralnej lokacji administracyjnej. Jeśli hierarchia używa centralnej lokacji administracyjnej, dane z lokacji głównych są replikowane do tej lokacji. W lokacji najwyższego poziomu w hierarchii punkt połączenia usługi przesyła te informacje podczas sprawdzania aktualizacji. Jeśli punkt połączenia usługi jest w trybie offline, dane te są przenoszone przy użyciu narzędzia połączenia usługi.

Menedżer konfiguracji zbiera dane tylko z bazy danych serwera SQL dla lokacji i nie zbiera danych bezpośrednio od klientów lub serwerów lokacji.

Administratorzy mogą zmieniać poziom danych, które są zbierane, przechodząc do **dane użycia** sekcji konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz "Dowiedz się więcej" artykuły dotyczące poziomy użycia danych i ustawień w [diagnostycznych i danych użycia programu System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626566) artykułu.


## <a name="customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta
Program poprawy jakości obsługi klienta (CEIP) zbiera podstawowe informacje z konsoli programu Configuration Manager o konfiguracji sprzętu i sposobie używania naszego oprogramowania i usług w celu identyfikacji trendów i wzorców użytkowania. Program CEIP zbiera również typ i liczbę napotkanych błędów, wydajności oprogramowania i sprzętu oraz szybkości usług. Nie gromadzimy nazwę, adres lub inne informacje kontaktowe. Z komputerów klientów nie są zbierane żadne dane programu CEIP.

Używamy tych informacji w celu poprawienia jakości, niezawodności i wydajności oprogramowania i usług firmy Microsoft.

Aby uzyskać więcej informacji o informacje zbierane, przetwarzane lub przekazywane przez program CEIP, zobacz [zasady zachowania poufności informacji programu CEIP](http://go.microsoft.com/fwlink/?LinkID=525211).

## <a name="operations-management-suite-connector"></a>Łącznik programu Operations Management Suite
Łącznika pakiet Microsoft Operations Management synchronizuje dane, takie jak kolekcje, programu System Center Configuration Manager do programu Microsoft Operations Management Suite. Identyfikator subskrypcji Microsoft Azure i klucz tajny są przechowywane w bazie danych programu Configuration Manager, gdy administrator skonfiguruje tę funkcję. Zarówno klucz tajny klienta usługi Azure Active Directory, jak i klucz udostępniony obszaru roboczego programu Microsoft Operations Management Suite są przechowywane w bazie danych programu System Center Configuration Manager lokalnie. Cała komunikacja między System Center Configuration Manager i Microsoft Operations Management Suite za pośrednictwem protokołu HTTPS. Brak dodatkowych informacji o kolekcjach znajduje się do firmy Microsoft poza dane telemetryczne losowego. Aby uzyskać szczegółowe informacje, która gromadzi programu Microsoft Operations Management Suite, zobacz [rejestrować analytics](http://go.microsoft.com/fwlink/?LinkId=823545).

## <a name="asset-intelligence"></a>Analiza zasobów
Funkcja analizy zasobów umożliwia Administratorzy IT definiowanie, śledzenie i aktywne Zarządzanie zgodnością ze standardami konfiguracji. Pomiary i raporty dotyczące wdrażania i używania zarówno aplikacji fizycznych, jak i wirtualnych pomagają organizacjom podejmować lepsze decyzje biznesowe dotyczące licencji na oprogramowanie oraz zachować zgodność z umowami licencyjnymi. Po zebraniu danych użycia od klientów programu Configuration Manager, Administratorzy można użyć różnych funkcji, aby wyświetlić dane, włącznie z kolekcji, zapytań i raportowania.

Podczas każdej synchronizacji katalog znanego oprogramowania zostanie pobrana z firmy Microsoft. Administratorzy IT mogą być wysyłanie informacji firmy Microsoft dotyczących tytułów oprogramowania bez kategorii, odnalezionych w organizacji do zbadania i dodania do katalogu. Przed przesłaniem tych informacji, okno dialogowe zawiera dane, które ma zostać przekazany. Przesłanych danych nie można wycofać. Funkcja analizy zasobów nie wysyła do firmy Microsoft informacji o użytkownikach i komputerach ani o wykorzystaniu licencji.

Po przesłaniu tytułu oprogramowania pracownicy naukowo-badawczy firmy Microsoft zidentyfikować, kategoryzowanie, a następnie udostępnią tę wiedzę wszystkim klientom, którzy korzystają z tej funkcji oraz innym klientom katalogu. Każdy tytuł oprogramowania przekazane staje się publiczny. Aplikacji i jej kategoryzacji staną się częścią katalogu, a następnie może być pobierany na innych użytkowników wykazu. Przed skonfigurowaniem zbierania danych przez funkcję analizy zasobów i podjęciem decyzji o tym, czy należy przesłać informacje do firmy Microsoft, należy uwzględnić wymagania ochrony prywatności danej organizacji.

Analiza zasobów nie jest domyślnie włączona w programie System Center Configuration Manager. Przesłanie nieskategoryzowanych tytułów nigdy nie następuje automatycznie i system nie został zaprojektowany do automatyzacji tego zadania. Użytkownik musi ręcznie wybrać i zatwierdzić przesłanie każdego tytułu oprogramowania.

## <a name="endpoint-protection"></a>Program Endpoint Protection
Usługa ochrony chmury firmy Microsoft była wcześniej znana jako usługa Microsoft Active Protection lub mapy.
Objęte produkty są System Center Endpoint Protection i funkcję ochrony punktu końcowego programu System Center Configuration Manager (zarządzanie, System Center Endpoint Protection i programu Windows Defender dla systemu Windows 10). Ta funkcja nie jest zaimplementowany dla programu System Center Endpoint Protection dla systemu Linux lub System Center Endpoint Protection dla komputerów Mac.

Społeczność ochrony przed złośliwym kodem usługi ochrony w chmurze firmy Microsoft jest dobrowolne społeczności online na całym świecie zawierającego użytkowników programu System Center Endpoint Protection. Po dołączeniu do usługi ochrony chmury Microsoft System Center Endpoint Protection automatycznie wysyła informacje do firmy Microsoft. Firma Microsoft używa informacji do określenia program wymaga zbadania pod kątem potencjalnych zagrożeń, a także aby pomóc w poprawie skuteczności programu System Center Endpoint Protection. Społeczność ta pomaga zatrzymać rozprzestrzenianie się nowych infekcji złośliwym oprogramowaniem. Jeśli raport usługi ochrony w chmurze firmy Microsoft zawiera szczegółowe informacje o złośliwym oprogramowaniu lub potencjalnie niechciane oprogramowanie klienta programu Endpoint Protection można usunąć, Usługa ochrony firmy Microsoft w chmurze pobiera najnowsze podpisu, aby rozwiązać ten. Usługa ochrony chmury firmy Microsoft znajduje się też "fałszywych alarmów" (gdy coś zostało wstępnie zidentyfikowane jako złośliwe oprogramowanie, okaże się nie powinien być) i popraw je.

Usługa ochrony chmury firmy Microsoft raporty zawierają informacje o potencjalnych pliki złośliwego oprogramowania, takich jak nazwy pliku, skrót kryptograficzny, dostawca, rozmiar i oznaczenie daty. Ponadto usługa ochrony chmury firmy Microsoft może zbierać pełne adresy URL w celu wskazania pochodzenia pliku. Tych adresów URL od czasu do czasu może być informacji osobistych, takich jak warunki wyszukiwania lub dane, które wprowadzono w formularzach. Raporty mogą również obejmować akcje, które miały po Endpoint Protection powiadomienia o niechcianego oprogramowania. Usługa ochrony chmury firmy Microsoft raporty zawierają te informacje, aby pomóc firmie Microsoft, jak skutecznie Endpoint Protection wykrywa i usuwania złośliwego oprogramowania i potencjalnie niechcianego oprogramowania i próbuje identyfikować nowe złośliwe oprogramowanie.

W przypadku członkostwa podstawowego lub zaawansowanego można przyłączyć usługi ochrony w chmurze firmy Microsoft. Podstawowy element członkowski raporty zawierają informacje opisane wcześniej. Zaawansowane elementu członkowskiego, raporty są bardziej obszerne i mogą zawierać dodatkowe szczegóły dotyczące programu Endpoint Protection wykrywa oprogramowanie, takie jak lokalizacji takiego oprogramowania, nazwach plików, sposobie działania oprogramowania oraz jego wpływ komputera. Te raporty i raporty od innych użytkowników programu Endpoint Protection, którzy biorą udział w Pomocy usługi Microsoft Cloud Protection pracownicy naukowo-badawczy firmy Microsoft szybciej odnajdywać nowych zagrożeń. Następnie dla programów spełniających kryteria analizy tworzone są definicje złośliwego oprogramowania i zaktualizowane definicje są udostępniane wszystkim użytkownikom za pośrednictwem usługi Microsoft Update.

Aby ułatwić wykrycie i usunąć niektóre rodzaje infekcji złośliwym oprogramowaniem, produkt regularnie wysyła usługi ochrony w chmurze firmy Microsoft informacje o stanie zabezpieczeń komputera. Obejmuje to informacje dotyczące ustawień zabezpieczeń komputera i pliki dziennika, które opisują sterowniki i inne oprogramowanie załadować podczas uruchamiania komputera.
Numer, który unikatowo identyfikuje komputer zostanie także wysłana. Ponadto usługa ochrony chmury firmy Microsoft może zbierać adresy IP, które łączą się potencjalne pliki złośliwego oprogramowania.

Usługa ochrony chmury firmy Microsoft raporty są wykorzystywane do ulepszania oprogramowania i usług. Raporty mogą również dla statystycznych lub innych celach analitycznych bądź i generowania definicji. Tylko pracownicy firmy Microsoft, wykonawców, partnerzy i dostawcy, którzy zgłoszą uzasadnioną potrzebę biznesową do użycia raporty mogą uzyskiwać do nich dostęp.

Usługa ochrony chmury firmy Microsoft nie zbiera celowo informacji osobistych. W zakresie, w jakim usługi Microsoft Cloud Protection zbiera żadnych informacji osobistych, Microsoft nie używa informacji do identyfikacji użytkownika lub skontaktowania się z Tobą.

Dodatkowe szczegóły dotyczące zebranych danych można znaleźć w dokumentacji produktu w [programu Endpoint Protection w programie System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=823547).

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>Hierarchia lokacji — widok geograficzny przy użyciu map Bing
Hierarchia lokacji — widok geograficzny umożliwia używanie mapy, mapy Bing firmy Microsoft dostępnych do wyświetlenia topologii fizycznej serwera programu Configuration Manager. Aby włączyć tę funkcję, podane informacje o lokalizacji są wysyłane z serwera z usługą sieci Web mapy Bing.

Firma Microsoft używa tych informacji do obsługi i ulepszania usługi Mapy Bing firmy Microsoft oraz innych witryn i usług firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zasady zachowania poufności informacji firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=823548).
Można zrezygnować z używania widoku geograficznego hierarchii lokacji. Widok diagramu hierarchii umożliwia zobaczenie hierarchii i nie używa usługi mapy Bing.

## <a name="microsoft-intune-subscription"></a>Subskrypcja usługi Microsoft Intune
Klienci, którzy kupili subskrypcję Microsoft Intune można używać programu Configuration Manager do zarządzania urządzeniami przenośnymi podłączonymi przy użyciu programu Microsoft Intune. [Microsoft Online Services Privacy Statement](http://go.microsoft.com/fwlink/?LinkId=262214) ma zastosowanie do usług online firmy Microsoft, w tym programu Microsoft Intune. Jeśli klienci mają też subskrypcję Microsoft Intune [Microsoft Online Services Privacy Statement](http://go.microsoft.com/fwlink/?LinkId=262214) należy przeczytać łącznie z te zasady zachowania poufności.

Cała komunikacja z usługą Microsoft Intune używać protokołu HTTPS. Aby skonfigurować subskrypcję Microsoft Intune i pobrać podpisywania żądanie certyfikatu (CSR) potrzebne do skonfigurowania obsługi systemu iOS, administrator zalogować się do programu Microsoft Intune za pomocą konta służbowego i hasła. Te poświadczenia nie są przechowywane w programie Configuration Manager. Cała pozostała komunikacja w usłudze Microsoft Intune jest uwierzytelniana za pomocą certyfikatów PKI, które automatycznie generuje Microsoft Intune.

Do zarządzania urządzeniami, które są połączone w usłudze Microsoft Intune, niektóre informacje są wysyłane do i odbierane z firmy Microsoft Intune. Informacje te obejmują główną nazwę użytkownika (UPN) wszystkich użytkowników, którzy są przypisani do usługi i informacje spisu urządzeń dla tych urządzeń, które są zarządzane przez program Microsoft Intune. Metadane, takie jak nazwa aplikacji, Wydawca i wersja, dla zawartości przypisanych do punktów dystrybucji Manage.Microsoft.com są wysyłane do firmy Microsoft Intune. Rzeczywista zawartość binarna przypisana do punktu dystrybucji Manage.Microsoft.com jest szyfrowana przed przesłaniem do firmy Microsoft Intune.

Ta funkcja nie jest domyślnie konfigurowana. Administratorzy kontrolować zawartość przesyłaną do punktu dystrybucji Manage.Microsoft.com i użytkowników, którzy są przypisane do usługi. Tę funkcję można usunąć w dowolnej chwili.
