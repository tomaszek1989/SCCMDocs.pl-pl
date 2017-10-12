---
title: "Klient programu Endpoint Protection — często zadawane pytania | Dokumentacja firmy Microsoft"
description: "Odpowiedzi na często zadawane pytania dotyczące usługi Windows Defender oraz programu Endpoint Protection."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3aaa9d2-a40e-42b1-ad75-5a115351729e
caps.latest.revision: "15"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: b88bc5f734b85527b81e5848deb0617db4c8dfbc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="endpoint-protection-client-frequently-asked-questions"></a>Klient programu Endpoint Protection — często zadawane pytania

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Te informacje dotyczące często zadawanych pytań są przeznaczone dla użytkowników komputerów, dla których administrator IT wdrożył usługę Windows Defender lub program Endpoint Protection na komputerze zarządzanym. Zawartość tego tematu nie mogą być stosowane na inne oprogramowanie ochrony przed złośliwym oprogramowaniem. Microsoft System Center Endpoint Protection zarządza usługa Windows Defender w systemie Windows 10. Można także wdrożyć i zarządzania klientem programu Endpoint Protection na komputerach przed systemem Windows 10. Ten artykuł zawiera opis usługi Windows Defender, jednak te informacje dotyczą również programu Endpoint Protection.  

-   [Dlaczego muszę wirusami i programami szpiegującymi?](#why-do-i-need-antivirus-and-antispyware-software)  
-   [Jak sprawdzić, czy komputer jest zainfekowany złośliwym oprogramowaniem?](#how-can-i-tell-if-my-computer-is-infected-with-malicious-software)
-   [Jak można znaleźć wersji usługi Windows Defender?](#how-can-i-find-the-version-of-windows-defender)
-   [Co należy zrobić, jeśli usługa Windows Defender lub program Endpoint Protection wykryje złośliwe oprogramowanie na komputerze?](#what-should-i-do-if-windows-defender-or-endpoint-protection-detects-software-on-my-computer)  
-   [Co to jest wirus?](#what-is-a-virus)  
-   [Co to jest program szpiegujący?](#what-is-spyware)  
-   [Jaka jest różnica między wirusy, programy szpiegujące lub inne potencjalnie szkodliwe oprogramowanie?](#hat-s-the-difference-between-viruses-spyware-and-other-potentially-harmful-software)  
-   [Skąd wirusy, programy szpiegujące lub inne potencjalnie niechciane oprogramowanie pochodzą?](#where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from)  
-   [Czy można uzyskać złośliwe oprogramowanie, bez wiedzy użytkownika?](#can-i-get-malicious-software-without-knowing-it)  
-   [Dlaczego jest ważne, aby przejrzeć umowami licencyjnymi przed zainstalowaniem oprogramowania?](#why-is-it-important-to-review-license-agreements-before-installing-software)  
-   [Jaka jest różnica między ochroną punktu końcowego i usługa Windows Defender?](#what-s-the-difference-between-endpoint-protection-and-windows-defender)  
-   [Dlaczego usługa Windows Defender nie wykrywa plików cookie?](#why-doesn-t-windows-defender-detect-cookies)  
-   [Jak ochronić się przed złośliwym oprogramowaniem?](#how-can-i-prevent-malware)  
-   [Co to są definicje wirusów i programów szpiegujących?](#what-are-virus-and-spyware-definitions)  
-   [Jak aktualizować definicje wirusów i programów szpiegujących aktualne?](#how-do-i-keep-virus-and-spyware-definitions-up-to-date)  
-   [Jak usunąć lub przywrócić elementy poddane kwarantannie przez usługę Windows Defender lub program Endpoint Protection?](#how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection)  
-   [Co to jest ochrona w czasie rzeczywistym?](#what-is-real-time-protection)  
-   [Jak sprawdzić, czy na tym komputerze działa usługa Windows Defender lub program Endpoint Protection?](#how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer)
-   [Jak skonfigurować alerty usługi Windows Defender lub program Endpoint Protection?](#how-to-set-up-windows-defender-or-endpoint-protection-alerts)  

##  <a name="why-do-i-need-antivirus-and-antispyware-software"></a>Dlaczego muszę wirusami i programami szpiegującymi?  

 Bardzo istotne jest, aby upewnić się, że na komputerze działa oprogramowanie chroniące przed złośliwym oprogramowaniem. Złośliwe oprogramowanie, które obejmuje wirusy, programy szpiegujące lub inne potencjalnie niechciane oprogramowanie, może próbować instalować się na komputerze za każdym razem, gdy łączy się on z Internetem. Może również zainfekować komputer podczas instalacji programu przy użyciu dysku CD, DVD lub innego nośnika wymiennego. Złośliwe oprogramowanie może być również zaprogramowane w taki sposób, aby uruchamiało się w nieoczekiwanym czasie, a nie tylko podczas instalacji.  

 Usługa Windows Defender lub program Endpoint Protection oferują trzy sposoby pomagające zapobiec zainfekowaniu komputera przez złośliwe oprogramowanie:  

-   **Przy użyciu ochrony w czasie rzeczywistym** — ochrona w czasie rzeczywistym umożliwia usłudze Windows Defender monitorowanie komputera przez cały czas i alertów, gdy złośliwe oprogramowanie, w tym wirusy, programy szpiegujące lub inne potencjalnie niechciane oprogramowanie próbuje się zainstalować lub uruchomić na komputerze. Następnie usługa Windows Defender wstrzymuje wykonywanie oprogramowania i umożliwia wykonanie względem niego zalecanego działania lub działania alternatywnego.  

    |**Opcja ochrony w czasie rzeczywistym** |**cel** |

    |-|-|  
    | Skanuj wszystkie pobrane pliki | Ta opcja monitoruje plików i programów, które są pobierane, w tym pliki, które są automatycznie pobierane za pomocą programu Windows Internet Explorer oraz Microsoft Outlook® Express, takie jak kontrolki ActiveX® i programy instalacyjne. Te pliki mogą być pobierane, instalowane lub uruchamiane samodzielnie przez przeglądarkę. Złośliwe oprogramowanie, w tym wirusy, programy szpiegujące i inne potencjalnie niechciane oprogramowanie, może być dołączone do tych plików i instalowane bez wiedzy użytkownika.<br /><br /> Przy użyciu opcji ochrony w czasie rzeczywistym usługa Windows Defender monitoruje komputer przez cały czas i sprawdza, czy wśród pobranych plików występują złośliwe pliki lub programy. Ta funkcja monitorowania oznacza, że usługa Windows Defender nie musi spowalniać przeglądania sieci lub obsługi poczty e-mail, wymagając sprawdzania dowolnego pliki lub programy mogą chcieć pobrać. |  
    | Monitoruj działanie plików i programów na moim komputerze | Ta opcja monitoruje pliki i programy uruchomione na komputerze, a następnie powiadamia o wszelkich akcje, które wykonują i wykonywanych na nich. Jest to istotne, ponieważ złośliwe oprogramowanie może wykorzystywać luki w zabezpieczeniach zainstalowanych programów w celu uruchamiania złośliwego lub niechcianego oprogramowania bez wiedzy użytkownika. Na przykład programy szpiegujące mogą być uruchamiane samoczynnie w tle podczas uruchamiania często używanego programu. Usługa Windows Defender monitoruje programy i powiadamia w przypadku wykrycia podejrzanych działań. |  
    | Włącz monitorowanie zachowania | Ta opcja monitoruje kolekcje zachowań pod kątem podejrzanych wzorców, które mogą nie zostać wykryte przy użyciu metod tradycyjnych wykrywania oprogramowania antywirusowego. |  

    | Włącz System inspekcji sieci | Ta opcja pomaga chronić komputer przed programami wykorzystującymi znane luki w zabezpieczeniach "zero day", skracając czas między odnalezieniem luki w zabezpieczeniach został odnaleziony i stosowania aktualizacji. |  

-   **Opcje skanowania** — można użyć usługi Windows Defender do skanowania pod kątem potencjalnych zagrożeń, takich jak wirusy, programy szpiegujące lub inne złośliwe oprogramowanie, które może zagrożenie komputera. Umożliwia także zaplanowanie regularnych operacji skanowania oraz usuwanie złośliwego oprogramowania wykrytego podczas skanowania.  

-   **Społeczności Microsoft Active Protection Service** — społeczność online Microsoft Active Protection Service pomaga w ustaleniu, jak reagowania przez inne osoby do oprogramowania, które nie zostało jeszcze sklasyfikowane pod względem zagrożeń. Na podstawie tych informacji można zdecydować, czy zezwalać na uruchamianie tego oprogramowania na komputerze. Z kolei uczestnictwo umożliwia dodawanie ocen społeczności w celu ułatwienia innym osobom podjęcia decyzji.  

##  <a name="how-can-i-tell-if-my-computer-is-infected-with-malicious-software"></a>Jak sprawdzić, czy komputer jest zainfekowany złośliwym oprogramowaniem?  

 Na komputerze może znajdować się złośliwe oprogramowanie, takie jak wirusy, programy szpiegujące lub inne potencjalnie niechciane oprogramowanie, jeśli:  

-   Można zauważyć nowe paski narzędzi, linki lub Ulubione, które nie zostały celowo dodane do przeglądarki sieci Web.  

-   Strona główna, wskaźnik myszy lub program do wyszukiwania nieoczekiwanie ulega zmianie.  

-   Po wpisaniu adresu określonej strony, na przykład wyszukiwarki, bez powiadomienia wyświetlana jest inna witryna sieci Web.  

-   Pliki są automatycznie usuwane z komputera.  

-   Komputer jest używany do atakowania innych komputerów.  

-   Wyświetlane są wyskakujące okienka reklam, nawet jeśli nie jesteś w Internecie.  

-   Komputer nagle działa wolniej niż zwykle. Nie wszystkie problemy z wydajnością komputera są powodowane przez złośliwe oprogramowanie, ale złośliwe oprogramowanie, szczególnie programy szpiegujące, mogą powodować zauważalne zmiany.  

Na komputerze może znajdować się złośliwe oprogramowanie, nawet jeśli żadne objawy nie są zauważalne. Tego rodzaju oprogramowanie może zbierać informacje o Tobie i Twoim komputerze bez Twojej wiedzy czy zgody. W celu zapewnienia ochrony Twojej prywatności oraz Twojego komputera usługa Windows Defender lub program Endpoint Protection powinien być uruchomiony przez cały czas.  

## <a name="how-can-i-find-the-version-of-windows-defender"></a>Jak można znaleźć wersji usługi Windows Defender?
 Aby wyświetlić wersję programu Windows Defender uruchomionych na komputerze, Otwórz program Windows Defender (kliknij **Start** , a następnie wyszukaj **usługa Windows Defender**), kliknij przycisk **ustawienia**i przewiń w dół ustawienia usługi Windows Defender, aby znaleźć **informacji o wersji**.

##  <a name="what-should-i-do-if-windows-defender-or-endpoint-protection-detects-malicious-software-on-my-computer"></a>Co należy zrobić, jeśli usługa Windows Defender lub program Endpoint Protection wykryje złośliwe oprogramowanie na komputerze?  

 Jeśli usługa Windows Defender wykryje złośliwe lub potencjalnie niepożądanie oprogramowanie na komputerze (podczas monitorowania komputera przy użyciu ochrony w czasie rzeczywistym lub po uruchomieniu skanowania), powiadomi użytkownika o wykrytym elemencie poprzez wyświetlenie komunikatu powiadomienia w prawym dolnym rogu ekranu.  

 Komunikat powiadomienia zawiera przycisk **Oczyść komputer** oraz link **Pokaż szczegóły** , który pozwala na wyświetlanie dodatkowych informacji na temat wykrytego elementu. Kliknij link **Pokaż szczegóły** w celu otwarcia okna **Szczegóły dotyczące potencjalnego zagrożenia** , aby uzyskać dodatkowe informacje na temat wykrytego elementu. Teraz można zdecydować, którą akcję zastosować do elementu, lub kliknąć przycisk **Oczyść komputer**. Jeśli potrzebujesz pomocy przy ustaleniu, którą akcję zastosować do wykrytego elementu, użyj poziomu alertu, który usługa Windows Defender przypisała do elementu jako wskazówkę (aby uzyskać więcej informacji, zobacz temat Omówienie poziomów alertów).  

 Poziomy alertów pomagają w określeniu, jak reagować na wirusy, programy szpiegujące lub inne potencjalnie niepożądane oprogramowanie. Chociaż usługa Windows Defender zaleci usunięcie wszystkich wirusów i programów szpiegujących, nie wszystkie oflagowane programy są złośliwe lub niepożądane. Poniższe informacje mogą pomóc zdecydować, co należy zrobić, jeśli usługa Windows Defender wykryje potencjalnie niepożądane oprogramowanie na komputerze.  

 W zależności od poziomu alertu można wybrać jedną z następujących akcji do zastosowania wobec wykrytego elementu:  

-   **Usuń** — ta akcja trwale usuwa oprogramowanie z komputera.  

-   **Kwarantanny** -poddaje oprogramowanie kwarantannie tej akcji, aby nie można go uruchomić. Gdy usługa Windows Defender poddaje oprogramowanie kwarantannie, przenosi je do innej lokalizacji na komputerze, a następnie nie dopuszcza do uruchomienia oprogramowania, dopóki użytkownik nie zdecyduje się je przywrócić lub usunąć z komputera.  

-   **Zezwalaj na** — ta akcja powoduje dodanie oprogramowania do listy dozwolonych w usłudze Windows Defender i umożliwia jego uruchomienie na komputerze. Usługa Windows Defender przestanie wysyłać alerty o zagrożeniu, jakie to oprogramowanie może stanowić dla prywatności lub komputera użytkownika.  

 Jeśli dla elementu, takiego jak oprogramowanie, zostanie wybrana opcja **Zezwalaj** , usługa Windows Defender przestanie wysyłać alerty o zagrożeniu, jakie to oprogramowanie może stanowić dla prywatności lub komputera użytkownika. W związku z tym użytkownik powinien dodawać oprogramowanie do listy dozwolonych tylko jeśli ma zaufanie do oprogramowania i wydawcy oprogramowania.  

### <a name="how-to-remove-potentially-harmful-software"></a>Sposób usuwania potencjalnie szkodliwego oprogramowania

Aby szybko i łatwo usunąć wszystkie niechciane i potencjalnie szkodliwe elementy wykryte przez usługę Windows Defender, użyj opcji **Oczyść komputer** .  

1.  Gdy po wykryciu potencjalnych zagrożeń w obszarze powiadomień zostanie wyświetlony komunikat powiadomienia, kliknij pozycję **Oczyść komputer**.  

2.  Usługa Windows Defender usuwa potencjalne zagrożenie (lub zagrożenia), a następnie powiadamia o zakończeniu czyszczenia komputera.  

3.  Aby uzyskać więcej informacji o wykrytych zagrożeniach, kliknij kartę **Historia** , a następnie wybierz pozycję **Wszystkie wykryte elementy**.  

4.  Jeśli wszystkie wykryte elementy nie są widoczne, kliknij pozycję **Wyświetl szczegóły**. Jeśli zostanie wyświetlony monit o hasło administratora lub potwierdzenie, wpisz hasło lub potwierdź akcję. Na komputerach z systemem Windows XP może być konieczne zalogowanie się jako administrator komputera.  

> [!NOTE]  
>  Jeśli to możliwe, podczas czyszczenia komputera usługa Windows Defender usuwa tylko zainfekowaną część pliku, a nie cały plik.  

##  <a name="what-is-a-virus"></a>Co to jest wirus?  
 Wirusy komputerowe to programy zaprojektowane specjalnie, aby zakłócać działanie komputera, rejestrować, uszkadzać lub usuwać dane bądź infekować inne komputery w Internecie. Wirusy często spowalniają działanie, jednocześnie powodując inne problemy.  

##  <a name="what-is-spyware"></a>Co to jest program szpiegujący?  
 Programy szpiegujące to oprogramowanie, które może instalować się samoczynnie lub uruchamiać na komputerze bez zgody użytkownika ani odpowiedniego powiadomienia czy możliwości kontroli. W przypadku programów szpiegujących mogą nie występować żadne objawy zainfekowania komputera, ale wiele złośliwych lub niechcianych programów może mieć wpływ na działanie komputera. Na przykład programy szpiegujące mogą monitorować Twoje zachowanie w trybie online lub zbierać informacje o Tobie (w tym informacje umożliwiające identyfikację użytkownika lub inne poufne informacje), zmieniać ustawienia komputera lub powodować spowolnienie jego działania.  

##  <a name="whats-the-difference-between-viruses-spyware-and-other-potentially-harmful-software"></a>Jaka jest różnica między wirusy, programy szpiegujące lub inne potencjalnie szkodliwe oprogramowanie?  
 Zarówno wirusy, jak i programy szpiegujące są instalowane na komputerze bez wiedzy użytkownika, a ich działanie może być inwazyjne i destrukcyjne. Mogą również zbierać informacje o komputerze i uszkadzać lub usuwać te informacje. Oba rodzaje programów mogą negatywnie wpływać na wydajność komputera.  

 Wirusy i programy szpiegujące różnią się głównie zachowaniem na komputerze. Wirusy, jak żywe organizmy, chcą zainfekować komputer, zreplikować się, a następnie rozpowszechnić na jak największej liczbie innych komputerów. Jednak programy szpiegujące są jak kret — chce "wprowadzić się" komputera i tam pozostać tak długo, jak to możliwe, wysyłania cenne informacje o komputerze do źródła zewnętrznego czasie, gdy jest.  

##  <a name="where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from"></a>Skąd wirusy, programy szpiegujące lub inne potencjalnie niechciane oprogramowanie pochodzą?  
 Niechciane oprogramowanie, takie jak wirusy, może być instalowane przez witryny sieci Web lub pobierane programy bądź oprogramowanie instalowane przy użyciu dysku CD lub DVD, zewnętrznego dysku twardego czy urządzenia. Programy szpiegujące są najczęściej instalowane przez bezpłatne oprogramowanie, takie jak programy do udostępniania plików, wygaszacze ekranu lub paski wyszukiwania.  

##  <a name="can-i-get-malicious-software-without-knowing-it"></a>Czy można uzyskać złośliwe oprogramowanie, bez wiedzy użytkownika?  
 Tak, niektóre złośliwe oprogramowanie może zostać zainstalowane z witryny sieci Web za pomocą skryptu lub programu osadzonego w stronie sieci Web. Do zainstalowania niektórych złośliwych programów wymagany jest udział użytkownika. To oprogramowanie używa wyskakujących okienek sieci Web lub bezpłatnego oprogramowania wymagającego zaakceptowania plików do pobrania. Jeśli jednak system Microsoft Windows® jest aktualny, a użytkownik nie zmniejsza poziomu ustawień zabezpieczeń, można zminimalizować prawdopodobieństwo infekcji.  

##  <a name="why-is-it-important-to-review-license-agreements-before-installing-software"></a>Dlaczego jest ważne, aby przejrzeć umowami licencyjnymi przed zainstalowaniem oprogramowania?  
 Podczas odwiedzania witryn sieci Web nie należy automatycznie akceptować wszystkich elementów oferowanych w witrynie do pobrania. W przypadku pobrania bezpłatnego oprogramowania, takiego jak programy do udostępniania plików lub wygaszacze ekranu, należy uważnie przeczytać umowę licencyjną. Należy zwrócić uwagę na klauzule dotyczące konieczności zaakceptowania reklam lub wyskakujących okienek danej firmy, bądź oprogramowania, które wysyła określone informacje z powrotem do wydawcy oprogramowania.  

##  <a name="whats-the-difference-between-endpoint-protection-and-windows-defender"></a>Jaka jest różnica między ochroną punktu końcowego i usługa Windows Defender?  
 Endpoint Protection jest programem do ochrony przed złośliwym oprogramowaniem, co oznacza, że zostało zaprojektowane do wykrywania i ochrony komputera przed różnorodnym złośliwym oprogramowaniem, w tym przed wirusami, programami szpiegującymi i innym potencjalnie niechcianym oprogramowaniem. Usługa Windows Defender instalowana automatycznie z systemem operacyjnym Windows jest oprogramowaniem służącym do wykrywania i zatrzymywania programów szpiegujących.  

##  <a name="why-doesnt-windows-defender-detect-cookies"></a>Dlaczego usługa Windows Defender nie wykrywa plików cookie?  
 Pliki cookie są niewielkimi plikami tekstowymi umieszczanymi na tym komputerze do przechowywania informacji o użytkowniku i jego preferencjach. Pliki cookie służą witryn sieci Web, aby oferować spersonalizowane środowisko i zbierać informacje na temat używania witryny sieci Web. Usługa Windows Defender nie wykrywa plików cookie, ponieważ nie uznaje ich zagrożenie dla prywatności lub bezpieczeństwa komputera. Większość przeglądarek internetowych umożliwia blokowanie plików cookie.  

##  <a name="how-can-i-prevent-malware"></a>Jak ochronić się przed złośliwym oprogramowaniem?  
 Obecnie dwoma z największych zmartwień użytkowników komputerów są wirusy i programy szpiegujące. W obu przypadkach, choć mogą one stanowić problem, możesz bronić się przed nimi samodzielnie. Wymaga to niewielkiej ilości planowania:  

-   Aktualność oprogramowania komputera i pamiętaj, aby instalować wszystkie poprawki. Pamiętaj, aby regularnie aktualizować system operacyjny.  

-   Upewnij się, że oprogramowanie do ochrony przed wirusami i programami szpiegującymi (Windows Defender) używa najnowszych aktualizacji dotyczących potencjalnych zagrożeń (zobacz temat Jak zapewnić aktualność definicji wirusów i programów szpiegujących?). Upewnij się również, że zawsze korzystasz z najnowszej wersji usługi Windows Defender.  

-   Pobieraj aktualizacje tylko z zaufanych źródeł. Dla systemów operacyjnych Windows, zawsze przejdź do [Microsoft Update](http://go.microsoft.com/fwlink/?LinkID=96304) (http://go.microsoft.com/fwlink/?LinkID=96304) i innego oprogramowania zawsze używaj wiarygodnych witryn sieci Web firmy lub osoby, która je tworzy.  

-   Jeśli otrzymasz wiadomość e-mail z załącznikiem, której źródło budzi Twoje wątpliwości, niezwłocznie ją usuń. Nie pobieraj żadnych aplikacji ani plików z nieznanych źródeł i Zachowaj ostrożność podczas wymiany plików z innymi użytkownikami.  

-   Zainstaluj zaporę i używaj jej. Zalecane jest włączenie Zapory systemu Windows.  

##  <a name="what-are-virus-and-spyware-definitions"></a>Co to są definicje wirusów i programów szpiegujących?  
 Podczas korzystania z usługi Windows Defender lub programu Endpoint Protection należy mieć aktualne definicje wirusów i programów szpiegujących. Definicje to pliki pełniące funkcję stale rozwijanej encyklopedii potencjalnie groźnego oprogramowania. Usługa Windows Defender lub program Endpoint Protection używa definicji do określania, czy wykryte oprogramowanie jest wirusem, programem szpiegującym czy innym potencjalnie niechcianym oprogramowaniem, a następnie powiadamia użytkownika o potencjalnych zagrożeniach. Aby ułatwić zachowanie aktualności definicji, usługa Windows Defender lub program Endpoint Protection współpracuje z usługą Microsoft Update w celu automatycznego instalowania nowych definicji po ich wydaniu. Można również ustawić, aby usługa Windows Defender lub program Endpoint Protection sprawdzał w Internecie dostępność aktualizacji definicji przed rozpoczęciem skanowania.  

##  <a name="how-do-i-keep-virus-and-spyware-definitions-up-to-date"></a>Jak aktualizować definicje wirusów i programów szpiegujących aktualne?  
 Definicje wirusów i programów szpiegujących przypominają encyklopedię znanego złośliwego oprogramowania, w tym wirusów, programów szpiegujących lub innego potencjalnie niechcianego oprogramowania. Z względu na to, że złośliwe oprogramowanie jest stale tworzone, usługa Windows Defender lub program Endpoint Protection polega na aktualnych definicjach, aby określać, czy oprogramowanie, które podejmuje próbę instalacji, uruchomienia lub zmiany ustawień komputera, jest wirusem, programem szpiegującym czy innym niechcianym oprogramowaniem.  

### <a name="to-automatically-check-for-new-definitions-before-scheduled-scans-recommended"></a>Aby automatycznie sprawdzać dostępność nowych definicji przed każdym zaplanowanym skanowaniem (zalecane)  

1.  Otwórz klienta usługi Windows Defender lub programu Endpoint Protection, klikając ikonę w obszarze powiadomień lub uruchamiając go z poziomu menu **Start** .  

2.  Kliknij pozycję **Ustawienia**, a następnie kliknij pozycję **Skanowanie zaplanowane**.  

3.  Upewnij się, że pole wyboru **Wyszukaj najnowsze definicje wirusów i programów szpiegujących przed rozpoczęciem zaplanowanego skanowania** jest zaznaczone, a następnie kliknij przycisk **Zapisz zmiany**. Jeśli zostanie wyświetlony monit o hasło administratora lub potwierdzenie, wpisz hasło lub potwierdź akcję.  

### <a name="to-check-for-new-definitions-manually"></a>Aby ręcznie sprawdzić dostępność nowych definicji

 Usługa Windows Defender lub program Endpoint Protection automatycznie aktualizuje definicje wirusów i programów szpiegujących. Jeśli definicje nie zostały zaktualizowane przez ponad siedem dni (na przykład, jeśli nie zostały wyłączone na tym komputerze, na tydzień), usługa Windows Defender lub program Endpoint Protection wyświetli powiadomienie że definicje są nieaktualne.  

1.  Otwórz klienta usługi Windows Defender lub programu Endpoint Protection, klikając ikonę w obszarze powiadomień lub uruchamiając go z poziomu menu **Start** .  

2.  Aby ręcznie sprawdzić dostępność nowych definicji, kliknij kartę **Aktualizuj** , a następnie kliknij przycisk **Aktualizuj definicje**.  

##  <a name="how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Jak usunąć lub przywrócić elementy poddane kwarantannie przez usługę Windows Defender lub program Endpoint Protection?  

 Gdy usługa Windows Defender lub program Endpoint Protection poddaje oprogramowanie kwarantannie, przenosi je do innej lokalizacji na komputerze, a następnie nie dopuszcza do uruchomienia oprogramowania, dopóki użytkownik nie zdecyduje się je przywrócić lub usunąć z komputera.  

 W przypadku wszystkich czynności wymienionych w tej procedurze, jeśli zostanie wyświetlony monit o hasło administratora lub potwierdzenie, wpisz hasło lub potwierdź działanie.  

###  <a name="to-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Aby usunąć lub przywrócić elementy poddane kwarantannie przez usługę Windows Defender lub program Endpoint Protection


1.  Kliknij kartę **Historia** , wybierz pozycję **Elementy poddane kwarantannie**, a następnie wybierz opcję **Elementy poddane kwarantannie** .  

2.  Kliknij przycisk **Wyświetl szczegóły** , aby wyświetlić wszystkie elementy.  

3.  Przejrzyj poszczególne elementy, a następnie kliknij przycisk **Usuń** lub **Przywróć**. Aby usunąć z komputera wszystkie elementy poddane kwarantannie, kliknij przycisk **Usuń wszystkie**.  

##  <a name="what-is-real-time-protection"></a>Co to jest ochrona w czasie rzeczywistym?  

 Ochrona w czasie rzeczywistym umożliwia usłudze Windows Defender monitorowanie komputera przez cały czas i powiadamianie o próbie instalacji lub uruchomienia potencjalnie groźnego oprogramowania, takiego jak wirusy lub programy szpiegujące. Ponieważ ta funkcja stanowi istotny element metody używanej przez usługę Windows Defender w celu ułatwienia ochrony komputera, należy upewnić się, że ochrona w czasie rzeczywistym jest zawsze włączona. Jeżeli ochrony w czasie rzeczywistym jest wyłączona, usługa Windows Defender powiadamia użytkownika, a Twoje komputerze€™ â €œAt riskâ€ stan s.  

 Zawsze gdy ochrona w czasie rzeczywistym wykryje zagrożenie lub potencjalne zagrożenie, usługa Windows Defender wyświetli powiadomienie. Możesz wybrać następujące opcje:  

-   Kliknij pozycję **Oczyść komputer** , aby usunąć wykryty element. Usługa Windows Defender automatycznie usunie element z komputera.  

-   Kliknij link **Pokaż szczegóły** , aby wyświetlić okno Szczegóły dotyczące potencjalnego zagrożenia, a następnie wybierz akcję, która ma zostać zastosowana dla wykrytego elementu.  

 Możesz wybrać oprogramowanie i ustawienia, które mają być monitorowane przez usługę Windows Defender, jednak zalecane jest włączenie ochrony w czasie rzeczywistym oraz wszystkich opcji ochrony w czasie rzeczywistym. Poniższa tabela zawiera objaśnienie dostępnych opcji.  

|||  
|-|-|  
|**Opcja ochrony w czasie rzeczywistym**|**Cel**|  
|Skanuj wszystkie pobrane pliki|Ta opcja monitoruje pobierane pliki i programy, w tym pliki pobierane automatycznie przez programy Windows Internet Explorer oraz Microsoft Outlook® Express, takie jak kontrolki ActiveX® i programy instalacyjne. Te pliki mogą być pobierane, instalowane lub uruchamiane samodzielnie przez przeglądarkę. Złośliwe oprogramowanie, w tym wirusy, programy szpiegujące i inne potencjalnie niechciane oprogramowanie, może być dołączone do tych plików i instalowane bez wiedzy użytkownika.<br /><br /> Przy użyciu opcji ochrony w czasie rzeczywistym usługa Windows Defender monitoruje komputer przez cały czas i sprawdza, czy wśród pobranych plików występują złośliwe pliki lub programy. Użycie tej funkcji monitorowania sprawia, że usługa Windows Defender nie musi spowalniać przeglądania stron sieci Web lub wiadomości e-mail, wymagając sprawdzania pobieranych plików lub programów.|  
|Monitorowanie aktywności plików i programów na komputerze|Ta opcja monitoruje uruchamianie plików i programów na komputerze, a następnie powiadamia o wykonywanych przez nie akcjach i umożliwia podejmowanie działań. Jest to istotne, ponieważ złośliwe oprogramowanie może wykorzystywać luki w zabezpieczeniach zainstalowanych programów w celu uruchamiania złośliwego lub niechcianego oprogramowania bez wiedzy użytkownika. Na przykład programy szpiegujące mogą być uruchamiane samoczynnie w tle podczas uruchamiania często używanego programu. Usługa Windows Defender monitoruje programy i powiadamia w przypadku wykrycia podejrzanych działań.|  
|Włącz monitorowanie zachowania|Ta opcja monitoruje kolekcje zachowań pod kątem podejrzanych wzorców, które mogą nie zostać wykryte przy użyciu tradycyjnych metod wykrywania stosowanych w oprogramowaniu antywirusowym.|  
|Włącz system inspekcji sieci|Ta opcja pomaga chronić komputer przed â €œzero dayâ€ luki w zabezpieczeniach znanych luk w zabezpieczeniach, skracając czas między odnalezieniem luki w zabezpieczeniach został odnaleziony i stosowania aktualizacji.|  

### <a name="to-turn-off-real-time-protection"></a>Aby wyłączyć ochronę w czasie rzeczywistym  

1.  Kliknij kartę **Ustawienia**, a następnie kliknij pozycję **Ochrona w czasie rzeczywistym**.  

2.  Wyczyść opcje ochrony w czasie rzeczywistym, które chcesz wyłączyć, a następnie kliknij przycisk **Zapisz zmiany**. Jeśli zostanie wyświetlony monit o hasło administratora lub potwierdzenie, wpisz hasło lub potwierdź akcję.  

##  <a name="how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer"></a>Jak sprawdzić, czy na tym komputerze działa usługa Windows Defender lub program Endpoint Protection?  

 Po zainstalowaniu usługi Windows Defender na komputerze można zamknąć główne okno i pozwolić na ciche działanie usługi Windows Defender w tle. Usługa Windows Defender będzie nadal uruchomiona na komputerze i będzie monitorować go oraz chronić przed zagrożeniami.  

 Oczywiście będzie wiadomo, że usługa Windows Defender jest uruchomiona, gdy w obszarze powiadomień będą wyświetlane komunikaty powiadomień. Te powiadomienia informują o potencjalnych zagrożeniach wykrytych przez usługę Windows Defender.  

 Otrzymasz również inne powiadomienia, na przykład gdy z jakiegoś powodu ochrona w czasie rzeczywistym została wyłączona, definicje wirusów i programów szpiegujących nie były aktualizowane przez określoną liczbę dni lub dostępne są uaktualnienia programu. Usługa Windows Defender wyświetla również krótkie powiadomienie, że trwa skanowanie komputera.  

> [!TIP]  

>Jeśli nie widzisz ikonę usługi Windows Defender w obszarze powiadomień, kliknij strzałkę w obszarze powiadomień, aby wyświetlić ukryte ikony, w tym ikonę usługi Windows Defender.  


 Kolor ikony zależy od bieżącego stanu komputera:  

-   Zielony oznacza, że komputer jest chroniony.  

-   Żółty oznacza, że komputer jest potencjalnie bez ochrony.  

-   Czerwony oznacza, że komputer jest zagrożony.  

##  <a name="how-to-set-up-windows-defender-or-endpoint-protection-alerts"></a>Jak skonfigurować alerty usługi Windows Defender lub program Endpoint Protection?  
 Kiedy usługa Windows Defender jest uruchomiona na komputerze, automatycznie ostrzega użytkownika o wykryciu wirusów, programów szpiegujących lub innego potencjalnie niechcianego oprogramowania. Można również ustawić usługę Windows Defender, aby powiadamiała o wykryciu oprogramowania, które nie zostało jeszcze przeanalizowane, oraz o zmianach wprowadzanych na komputerze przez oprogramowanie.  

### <a name="to-set-up-alerts"></a>Aby skonfigurować alerty  

1.  Kliknij kartę **Ustawienia**, a następnie kliknij pozycję **Ochrona w czasie rzeczywistym**.  

2.  Upewnij się, że pole wyboru **Włącz ochronę w czasie rzeczywistym (zalecane)** jest zaznaczone.  

3.  Zaznacz pola wyboru obok opcji ochrony w czasie rzeczywistym, które chcesz uruchomić, a następnie kliknij przycisk **Zapisz zmiany**. Jeśli zostanie wyświetlony monit o hasło administratora lub potwierdzenie, wpisz hasło lub potwierdź akcję.  

### <a name="see-also"></a>Zobacz także  
 [Rozwiązywanie problemów z klientem usługi Windows Defender lub program Endpoint Protection](troubleshoot-endpoint-client.md)   

 [Pomoc klienta programu Endpoint Protection](endpoint-protection-client-help.md)
