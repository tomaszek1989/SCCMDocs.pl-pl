---
title: "System Center Configuration Manager privacy statement — informacje dodatkowe | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak firma Microsoft zbiera i korzysta z danych z wdrożenia programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
caps.latest.revision: 5
caps.handback.revision: 0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 47d473b3884c3cd2ff7516629a7c32d4e52ac39b
ms.openlocfilehash: ef7b3656f9b4a31e07227aa4e864448d0dd1fcdc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>Dodatkowe informacje o prywatności dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


## <a name="updates-and-servicing"></a>Obsługa
System Center Configuration Manager wprowadza nowy model aktualizacji, ułatwiająca aktualizował wdrożenia programu Configuration Manager za pomocą najnowszej aktualizacji i funkcji. Po zainstalowaniu tej funkcji dodaje nowa rola systemu lokacji, który wywołał punkt połączenia usługi na serwerze lokacji, która wybiera administrator. Szczegółowe informacje na temat zbieranych informacji i sposobie ich użycia zobacz sekcję danych użycia w tym artykule.


## <a name="usage-data"></a>Dane użycia
System Center Configuration Manager umożliwia zbieranie diagnostyki i danych użycia o całości, używanym przez firmę Microsoft do poprawy obsługi instalacji, jakość i bezpieczeństwo w przyszłych wersjach.
Diagnostyka i danych użycia jest włączona dla każdej hierarchii programu System Center Configuration Manager. Składa się on z kwerend programu SQL Server, uruchamiane co tydzień w każdej lokacji głównej i centralnej lokacji administracyjnej. Jeśli hierarchia używa centralnej lokacji administracyjnej, dane z lokacji głównych są replikowane do tej lokacji. W lokacji najwyższego poziomu w hierarchii punkt połączenia usługi przesyła te informacje podczas sprawdzania aktualizacji. Jeśli punkt połączenia usługi jest w trybie offline, dane te są przenoszone przy użyciu narzędzia połączenia usługi.

Menedżer konfiguracji zbiera dane tylko z bazy danych lokacji programu SQL server, a nie zbiera danych bezpośrednio od klientów lub serwerów lokacji.

Administratorzy mogą zmienić poziom danych, które są zbierane, przechodząc do **dane użycia** części konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz "Więcej" artykułów na temat poziomów danych użycia i ustawienia w [diagnostyki i danych użycia programu System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626566) artykułu.


## <a name="customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta
Program poprawy jakości obsługi klienta (CEIP) zbiera podstawowe informacje z konsoli programu Configuration Manager o konfiguracji sprzętu i sposobie korzystania z naszego oprogramowania i usług w celu identyfikacji trendów i wzorców użycia. Program CEIP zbiera również typ i liczbę napotkanych błędów, wydajności oprogramowania i sprzętu oraz szybkości działania usług. Nie gromadzimy nazwisk, adresów ani innych informacji kontaktowych. Z komputerów klientów nie są zbierane żadne dane programu CEIP.

Używamy tych informacji w celu poprawienia jakości, niezawodności i wydajności oprogramowania i usług firmy Microsoft.

Aby uzyskać więcej informacji o informacjach zbieranych, przetwarzanych lub przesyłanych przez funkcję CEIP, patrz [zasady zachowania poufności informacji programu CEIP](http://go.microsoft.com/fwlink/?LinkID=525211).

## <a name="operations-management-suite-connector"></a>Łącznik programu Operations Management Suite
Łącznik pakiet zarządzania Operations Microsoft synchronizuje dane, takie jak kolekcje, z System Center Configuration Manager do pakietu zarządzania Operations firmy Microsoft. Identyfikator subskrypcji Microsoft Azure i klucz tajny są przechowywane w bazie danych programu Configuration Manager, gdy administrator skonfiguruje tę funkcję. Zarówno klucz tajny klienta usługi Azure Active Directory, jak i klucz udostępnionego obszaru roboczego pakietu zarządzania Microsoft Operations są przechowywane w bazie danych programu System Center Configuration Manager lokalnie. Cała komunikacja między programu System Center Configuration Manager i pakiet zarządzania Operations Microsoft protokołu HTTPS. Żadne dodatkowe informacje dotyczące kolekcji jest przekazywany do firmy Microsoft poza dane telemetryczne losowego. Szczegółowe informacje na temat pakietu zarządzania Operations Microsoft zbiera informacje, zobacz [rejestrować analytics](http://go.microsoft.com/fwlink/?LinkId=823545).

## <a name="asset-intelligence"></a>Analiza zasobów
Funkcja analizy zasobów umożliwia administratorom IT definiowanie, śledzenie i aktywne Zarządzanie zgodnością ze standardami konfiguracji. Pomiary i raporty dotyczące wdrażania i używania zarówno aplikacji fizycznych, jak i wirtualnych pomagają organizacjom podejmować lepsze decyzje biznesowe dotyczące licencji na oprogramowanie oraz zachować zgodność z umowami licencyjnymi. Po zebraniu danych użycia od klientów programu Configuration Manager, Administratorzy mogą użyć różnych funkcji do wyświetlania danych łącznie z kolekcjami, zapytaniami i raportowaniem.

Podczas każdej synchronizacji katalog znanego oprogramowania zostanie pobrany od firmy Microsoft. Administratorzy IT mogą wysłać do firmy Microsoft informacje o tytułach nieskategoryzowanego oprogramowania, które zostały wykryte w swojej organizacji do zbadania i dodania do katalogu. Przed przesłaniem tych informacji, okno dialogowe zawiera dane, które przechodzi do przesłania. Przesłanych danych nie można wycofać. Funkcja analizy zasobów nie wysyła do firmy Microsoft informacji o użytkownikach i komputerach ani o wykorzystaniu licencji.

Po przesłaniu tytułu oprogramowania pracownicy naukowo-badawczy firmy Microsoft zidentyfikować, skategoryzować i następnie udostępnią tę wiedzę wszystkim innym klientom, którzy korzystają z tej funkcji oraz innym klientom katalogu. Każdy tytuł oprogramowania przekazane staje się publiczny. Aplikacji i jej kategoryzacji stanie się częścią katalogu, a następnie może zostać pobrana przez innych klientów katalogu. Przed skonfigurowaniem zbierania danych przez funkcję analizy zasobów i podjęciem decyzji o tym, czy należy przesłać informacje do firmy Microsoft, należy uwzględnić wymagania ochrony prywatności danej organizacji.

Analiza zasobów nie jest włączona w programie System Center Configuration Manager domyślnie. Przesłanie nieskategoryzowanych tytułów nigdy nie następuje automatycznie i system nie został zaprojektowany do automatyzacji tego zadania. Użytkownik musi ręcznie wybrać i zatwierdzić przesłanie każdego tytułu oprogramowania.

## <a name="endpoint-protection"></a>Program Endpoint Protection
Usługa ochrony chmury Microsoft była wcześniej znana jako usługa Microsoft Active Protection lub mapy.
Objęte produkty są System Center Endpoint Protection i funkcję ochrony punktu końcowego programu System Center Configuration Manager (do zarządzania programu System Center Endpoint Protection i programu Windows Defender w systemie Windows 10). Ta funkcja nie jest zaimplementowana dla programu System Center Endpoint Protection dla systemu Linux lub System Center Endpoint Protection dla komputerów Macintosh.

Usługa ochrony chmury Microsoft społeczność ochrony przed złośliwym oprogramowaniem jest dobrowolne społeczności online na całym świecie której wchodzą użytkownicy programu System Center Endpoint Protection. Po dołączeniu usługi ochrony chmury Microsoft System Center Endpoint Protection automatycznie wysyła informacje do firmy Microsoft. Firma Microsoft używa tych informacji do określenia program wymaga zbadania pod kątem potencjalnych zagrożeń, a także do poprawy skuteczności programu System Center Endpoint Protection. Społeczność ta pomaga zatrzymać rozprzestrzenianie się nowych infekcji złośliwym oprogramowaniem. Jeśli raport usługi ochrony w chmurze firmy Microsoft zawiera szczegółowe informacje o złośliwym oprogramowaniu lub potencjalnie niechciane oprogramowanie, które klient Endpoint Protection może usunąć, Usługa ochrony chmury Microsoft pobierze najnowszy plik z sygnaturami jego rozwiązania. Usługa ochrony chmury Microsoft może również znaleźć "fałszywych alarmów" (gdy coś, co zostało wstępnie zidentyfikowane jako złośliwe oprogramowanie, okaże się nie powinien być) i usunąć je.

Usługa ochrony w chmurze firmy Microsoft raporty zawierają informacje o potencjalnych plików złośliwego oprogramowania, takich jak nazwy pliku, skrót kryptograficzny, dostawca, rozmiar i oznaczenie daty. Ponadto usługa ochrony chmury Microsoft może zbierać pełne adresy URL w celu wskazania pochodzenia pliku. Te adresy URL od czasu do czasu może być informacje osobiste, takie jak warunki wyszukiwania lub dane, które wprowadzono w formularzach. Raporty mogą również obejmować akcje, które miały po Endpoint Protection powiadomienia o niechcianego oprogramowania. Raporty usługi ochrony chmury Microsoft zawierają takie informacje, aby pomóc firmie Microsoft, jak efektywnie wykryć Endpoint Protection i usuwania złośliwego oprogramowania i potencjalnie niechcianego oprogramowania i próbuje identyfikować nowe złośliwe oprogramowanie.

Jeśli masz członkostwo podstawowe i zaawansowane można przyłączyć usługi ochrony w chmurze firmy Microsoft. Raporty członków poziomu podstawowego zawierają informacje opisane wcześniej. Zaawansowany element członkowski raporty są bardziej obszerne i mogą zawierać dodatkowe informacje dotyczące oprogramowania, które Endpoint Protection wykryje, lokalizacji takiego oprogramowania, nazwach plików, sposobie działania oprogramowania oraz jego wpływ komputera. Te raporty i raporty od innych użytkowników programu Endpoint Protection, którzy uczestniczą w Pomocy usługi ochrony chmury Microsoft pracownicy naukowo-badawczy firmy Microsoft wykrywaniu nowych zagrożeń. Następnie dla programów spełniających kryteria analizy tworzone są definicje złośliwego oprogramowania i zaktualizowane definicje są udostępniane wszystkim użytkownikom za pośrednictwem witryny Microsoft Update.

Aby łatwiej wykryć i usunąć niektóre rodzaje infekcji złośliwym oprogramowaniem, produkt regularnie wysyła usługi ochrony w chmurze firmy Microsoft informacji o stanie zabezpieczeń komputera. Obejmuje to informacje o ustawieniach zabezpieczenia komputera i pliki dziennika, opisujące sterowniki i inne oprogramowanie obciążenia podczas uruchamiania komputera.
Wysyłany jest także numer, który unikatowo identyfikuje komputer. Usługa ochrony chmury Microsoft może także zbierać adresy IP, które łączą się z potencjalnymi pliki złośliwego oprogramowania.

Raporty usługi ochrony w chmurze firmy Microsoft są wykorzystywane do ulepszania oprogramowania i usług. Raporty mogą również do celów statystycznych, testowych lub analitycznych, a także do generowania definicji. Tylko Microsoft pracownicy, partnerzy, partnerzy oraz dostawcy, którzy zgłoszą uzasadnioną potrzebę biznesową do korzystania z raportów można uzyskiwać do nich dostęp.

Usługa ochrony chmury Microsoft nie zbiera celowo informacji osobistych. W zakresie, w jakim usługi ochrony chmury Microsoft zbiera żadnych informacji osobistych, Microsoft nie będzie używać informacji do identyfikacji użytkownika lub skontaktować się z Tobą.

Dodatkowe szczegóły dotyczące zebranych danych można znaleźć w dokumentacji produktu w [Endpoint Protection w programie System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=823547).

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>Hierarchia lokacji — widok geograficzny przy użyciu map Bing
Hierarchia lokacji — widok geograficzny umożliwia używanie map mapy Bing firmy Microsoft dostępnych do wyświetlania topologii fizycznej serwera programu Configuration Manager. Aby włączyć tę funkcję, podane informacje o lokalizacji są wysyłane z serwera do usługi sieci Web mapy Bing.

Firma Microsoft używa tych informacji do obsługi i ulepszania usługi Mapy Bing firmy Microsoft oraz innych witryn i usług firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zasady zachowania poufności informacji firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=823548).
Można zrezygnować z używania widoku geograficznego hierarchii lokacji. Widok diagramu hierarchii umożliwia zobaczenie hierarchii i nie używa usługi mapy Bing.

## <a name="microsoft-intune-subscription"></a>Subskrypcja usługi Microsoft Intune
Klienci, którzy kupili subskrypcję Microsoft Intune można użyć programu Configuration Manager do zarządzania urządzeniami przenośnymi podłączonymi za pomocą programu Microsoft Intune. [Microsoft Online Services Privacy Statement](http://go.microsoft.com/fwlink/?LinkId=262214) ma zastosowanie do usług online firmy Microsoft, w tym Microsoft Intune. Jeśli klienci mają też subskrypcję Microsoft Intune [Microsoft Online Services Privacy Statement](http://go.microsoft.com/fwlink/?LinkId=262214) należy przeczytać łącznie z niniejszych zasad.

Cała komunikacja z usługą Microsoft Intune protokołu HTTPS. Aby skonfigurować subskrypcję Microsoft Intune i pobrać żądanie podpisania certyfikatu (CSR) potrzebne do skonfigurowania obsługi systemu iOS, administrator musi się zarejestrować w usłudze Microsoft Intune za pomocą konta organizacyjnego i hasła. Te poświadczenia nie są przechowywane w programie Configuration Manager. Cała pozostała komunikacja z Microsoft Intune jest uwierzytelniana za pomocą certyfikatów PKI, które automatycznie generuje Microsoft Intune.

Do zarządzania urządzeniami, które są podłączone do Microsoft Intune, niektóre informacje są wysyłane do i odbierane z firmy Microsoft Intune. Informacje te obejmują główną nazwę użytkownika (UPN) wszystkich użytkowników, którzy są przypisani do usługi i informacje spisu urządzeń dla tych urządzeń, które są zarządzane przez program Microsoft Intune. Metadane, takie jak nazwa aplikacji, Wydawca i wersja, dla zawartości przypisanych do punktów dystrybucji Manage.Microsoft.com są wysyłane do firmy Microsoft Intune. Rzeczywista zawartość binarna przypisanej do punktu dystrybucji Manage.Microsoft.com jest szyfrowana przed przesłaniem do Microsoft Intune.

Ta funkcja nie jest domyślnie konfigurowana. Administratorzy kontrolować zawartość przesyłaną do punktu dystrybucji Manage.Microsoft.com i użytkowników, którzy są przypisani do usługi. Tę funkcję można usunąć w dowolnej chwili.

