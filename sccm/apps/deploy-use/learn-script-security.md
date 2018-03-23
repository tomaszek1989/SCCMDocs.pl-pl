---
title: Dowiedz się więcej o zabezpieczeniach skrypt programu PowerShell
titleSuffix: System Center Configuration Manager
description: Zasoby pomagające Dowiedz się więcej o zabezpieczeniach skrypt programu PowerShell.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0bd093d-67a5-4f74-bf79-dd604889f5ba
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 48b3dd53ce8df097e355908237111f0d586ddd06
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="learn-more-about-powershell-script-security"></a>Dowiedz się więcej o zabezpieczeniach skrypt programu PowerShell

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jest Administratorze spoczywa odpowiedzialność za sprawdzić proponowane środowiska PowerShell i programu PowerShell użycia parametrów w swoim środowisku. Oto kilka zasobów przydatne ułatwiające Poinformuj administratorów o zasilania środowiska PowerShell i potencjalne ryzyko powierzchni. Ma to pomóc ograniczyć potencjalne ryzyko powierzchnie i bezpieczne skrypty, które mają być używane.

## <a name="powershell-script-security"></a>Skrypt programu PowerShell zabezpieczeń
Wbudowane skrypty uruchamiania to funkcja wizualnie Wyświetl i zatwierdź skrypty, które są wymagane do uruchomienia w środowisku. Administratorzy należy zwrócić uwagę, skrypty programu PowerShell można zaciemniona skryptu: skrypt, który jest złośliwe i trudne do wykrycia z visual inspekcji podczas procesu zatwierdzania skryptu. Najlepszym rozwiązaniem, przy użyciu określonych narzędziach kontroli w dodatkowej wizualnie recenzowania skryptów programu PowerShell, pomogą wykrywania problemów z podejrzanych skryptów. Te narzędzia zawsze nie może określić zamiar autora programu PowerShell, dlatego on zwrócić uwagę na podejrzane skryptu. Jednak narzędzi wymaga administratorem, aby ocenić, jeśli jest składnia skryptu złośliwego lub zamierzone.

## <a name="recommendations"></a>Zalecenia
- Zapoznaj się z programu PowerShell najlepsze rozwiązania przy użyciu różnych łączy, do których odwołuje się poniżej.
- **Zaloguj się skrypty**: Inna metoda przechowywania skryptów bezpiecznego jest wprowadzenie sprawdzane, a następnie podpisu, przed zaimportowaniem do użycia.
- Nie przechowuj klucze tajne (takie jak hasła) w skryptów programu PowerShell i Dowiedz się więcej na temat sposobu obsługi kluczy tajnych.


## <a name="general-information-about-powershell-security-best-practices"></a>Ogólne informacje o najlepszych rozwiązaniach dotyczących zabezpieczeń programu PowerShell

Wybrano tej kolekcji łącza umożliwiają administratorom programu Configuration Manager punkt początkowy szkoleniowe dotyczące najlepszych rozwiązań zabezpieczeń skrypt programu PowerShell.  

[Wprowadzenie do najlepszych rozwiązań dotyczących zabezpieczeń programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2013/12/16/powershell-security-best-practices/ )

[PowerShell zabezpieczeń najlepsze rozwiązania w zakresie PowerPoint](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/74/metablogapi/1055.PowerShell-Security-Best-Practices_3CA24C32.pptx)

<iframe src="https://channel9.msdn.com/Events/Blue-Hat-Security-Briefings/BlueHat-Security-Briefings-Fall-2013-Sessions/PowerShell-Best-Practices/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

[Defending względem programu PowerShell ataków, blog zespołu programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/10/23/defending-against-powershell-attacks/)

[Holmes Lewandowski wspierają defending przed atakami PowerShell twitter, PowerShell firmy Microsoft i zabezpieczeń](https://twitter.com/Lee_Holmes/status/922462821081694208)

[Ochrona przed złośliwym kodem iniekcji](https://blogs.msdn.microsoft.com/powershell/2006/11/22/protecting-against-malicious-code-injection/)

[Informacje na temat zabezpieczeń z galerii programu PowerShell](https://blogs.msdn.microsoft.com/powershell/2015/08/06/powershell-gallery-new-security-scan/)

[Niebieski zespołu programu PowerShell, w tym artykule omówiono bloku skryptu głębokie rejestrowania chronione rejestrowania zdarzeń, interfejs skanowanie ochrony przed złośliwym kodem, Secure API generowania kodu](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

[W systemie Windows 10 jest interfejs API dla interfejsu skanowania przed złośliwym oprogramowaniem](https://cloudblogs.microsoft.com/microsoftsecure/2015/06/09/windows-10-to-offer-application-developers-new-malware-defenses/?source=mmpc)

## <a name="powershell-parameters-security"></a>Zabezpieczenia parametry programu PowerShell
Przekazywanie parametrów to sposób elastyczność za pomocą tych skryptów i odroczenie decyzji do czasu wykonywania. Otwartej również innego powierzchni ryzyka. Najlepsze rozwiązania dotyczące zapobiegania parametry złośliwego lub uruchomienie skryptu są:

- Zezwalaj tylko na użycie wstępnie zdefiniowanych parametrów.
- Funkcja wyrażenia regularnego, aby sprawdzić poprawność parametrów, które są dozwolone.
    - Przykład: Jeśli zakres wartości są dozwolone tylko, użycie wyrażenia regularnego, aby wyszukać tylko znaków lub wartości, które można uzupełnić zakresu.
    - Sprawdzanie poprawności parametrów mogą pomagać w zapobieganiu próby użycia pewnych znaków, które można anulowane, takich jak cudzysłowy użytkowników. Należy pamiętać, że może istnieć wiele typów ofert, więc za pomocą wyrażeń regularnych do sprawdzania poprawności znaków decydujesz się dopuszczalne są często jest łatwiejsze niż w trakcie definiowania wszystkie dane wejściowe który nie jest dopuszczalna.
- Wykorzystać moduł PowerShell ["iniekcji myśliwego"](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0) w galerii programu PowerShell.
    - Może być fałszywych alarmów, tak wyszukuj zamiar, gdy coś jest oznaczony jako podejrzanej do określenia, czy lub nie jest prawdziwe problem. 
- Microsoft Visual Studio ma analizatora skryptu, który może pomóc sprawdzanie składni programu PowerShell.
- Ten film wideo zatytułowany: "DEF CON 25 - Lewandowski Holmes — Pobierz $pwnd: Do zaatakowania bitwy zaostrzonym systemu Windows Server"umożliwia identyfikowanie rodzaje problemów, które można zabezpieczyć przed (szczególnie sekcji 12:20-17:50):     <iframe width="560" height="315" src="https://www.youtube.com/embed/ahxMOAAani8" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="environment-recommendations"></a>Zalecenia dotyczące środowiska
Ogólne zalecenia dla administratorów programu PowerShell.
1. Wdrożyć najnowszą wersję programu PowerShell, takie jak 5 lub nowszego, wbudowane w system Windows 10. Alternatywnie można wdrożyć [Windows Management Framework](https://www.microsoft.com/en-us/download/details.aspx?id=54616), w dół i w tym systemu Windows 7 i Windows Server 2008 R2. 
2. Włącz i zbierania dzienników programu PowerShell, opcjonalnie tym chronione rejestrowania zdarzeń. Uwzględnienie tych dzienników do podpisów, polowania i przepływów pracy w odpowiedzi na zdarzenia.
3. Implementowanie tylko tyle administrowania w systemach wysokiej wartości, aby wyeliminować lub Zmniejsz nieograniczonego dostępu administracyjnego do tych systemów.
4. Wdrożenie zasad kontroli aplikacji/Guard urządzeń umożliwia wstępnie zatwierdzonych zadań administracyjnych, aby użyć pełne możliwości języka programu PowerShell, jednocześnie ograniczając interakcyjne i niezatwierdzonych umożliwia ograniczonym podzbiorem języka programu PowerShell.
5. Wdrażanie systemu Windows 10 umożliwiają dostawcy programu antywirusowego pełny dostęp do całej zawartości (w tym zawartości wygenerowany lub cofnąć zaciemnionego na środowisko uruchomieniowe) przetworzonych przez hosty skryptów systemu Windows w tym programu PowerShell.