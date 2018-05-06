---
title:
- Tytuł artykułu 35 znaków lub mniej
titleSuffix: Configuration Manager
description: ''
ms.date: mm/dd/yyyy
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid:
- GET ONE FROM guidgenerator.com
author:
- GITHUB USERNAME
ms.author:
- ALIAS
manager:
- ALIAS
ms.openlocfilehash: bb0a23b8870d31136967b1bc594580bcc2cd0cd9
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="metadata-and-markdown-template"></a>Metadane i szablon Markdown

Ten szablon docs.ms zawiera przykłady składni języka markdown, a także wskazówki dotyczące konfiguracji metadanych. Jest dostępny w katalogu głównym każdego repozytorium pilotażu EM (np. ~/Azure-rmsdocs-pr/template.MD ~/Azure-RMSDocs-pr) i należy go odczytywać jako plik markdown, mimo że można się odwoływać do [opublikowanej wersji](https://stage.docs.microsoft.com/en-us/rights-management/template) aby zobaczyć, jak przykłady składni języka markdown.

Podczas tworzenia pliku markdown należy skopiować szablon do nowego pliku, uzupełnić metadane jako opisany poniżej, ustawić nagłówek H1 powyżej jako tytuł artykułu i usunąć zawartość.


## <a name="metadata"></a>Metadane

Pełen blok metadanych jest powyżej, podzielony na pola wymagane i opcjonalne pola; zobacz [porad związanych z metadanymi OPS](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) więcej szczegółów. Ważne uwagi:

- Możesz **musi** spacją między dwukropkiem (:) a wartością elementu metadanych.
- Jeśli opcjonalny element metadanych nie ma wartość, komentarz poprzedzając symbolem # (nie należy pozostawiać pustego elementu ani używać "Brak"); Jeśli wartość jest dodawane do elementu, który został opatrzony, należy usunąć symbol #.
- Dwukropki w wartości (np. tytule) Podziel analizatora składni metadanych. Zamiast nich należy użyć kodu HTML &#58; (np. "tytuł: Usługa Azure Rights Management&#58; podstawy | Usługi Azure RMS").
- **Tytuł**: Ten tytuł pojawi się w wynikach aparatu wyszukiwania. Tytuł powinien kończyć się symbolem kreski pionowej (|) i nazwa usługi (np. zobacz powyżej). Tytuł nie musi i prawdopodobnie nie powinien być taki sam jak tytuł w nagłówku H1. Powinien zawierać około 65 znaków (łącznie z | NAZWA USŁUGI)
- **Autor**, **Menedżera**, **Weryfikacja**: W polu Autor powinien zawierać **nazwę użytkownika usługi Github** autora, a nie jego alias.  Z drugiej strony, pola "manager" i "reviewer" powinny zawierać aliasy. Wartość MS.Reviewer Określa nazwę Powiązanego z artykułem lub usługą.
- **MS.AssetID**: Jest to identyfikator GUID artykułu z witryny CAPS. Podczas tworzenia nowego pliku markdown Uzyskaj identyfikator GUID z [ https://www.guidgenerator.com ](https://www.guidgenerator.com).
- **MS.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm** : Możliwe wartości tych elementów można znaleźć [tutaj](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## <a name="basic-markdown-and-gfm"></a>Podstawowe języka Markdown i GFM

Wszystkie podstawowe i usługą Github markdown jest obsługiwana. Aby uzyskać więcej informacji o tych zobacz:

- [Podstawowa składnia języka markdown](https://daringfireball.net/projects/markdown/syntax)
- [Dokumentacja markdown z usługą Github (GFM)](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Nagłówki

Przykłady nagłówków pierwszego i drugiego stopnia znajdują się powyżej.

Brak **musi** można tylko jeden nagłówek pierwszego stopnia w temacie, który będzie wyświetlany jako tytuł na stronie.  

Nagłówki drugiego stopnia spowoduje wygenerowanie na stronie spisu treści, która pojawia się w sekcji "w tym artykule" pod tytułem strony.

### <a name="third-level-heading"></a>Nagłówek trzeciego stopnia
#### <a name="fourth-level-heading"></a>Nagłówek czwartego stopnia
##### <a name="fifth-level-heading"></a>Nagłówek piątego stopnia
###### <a name="sixth-level-heading"></a>Nagłówek szóstego stopnia

## <a name="text-styling"></a>Style tekstu

*Italics*

**Bold**

~~Przekreślenia~~



## <a name="links"></a>Łącza

Aby utworzyć link do pliku markdown w tym samym repozytorium, użyj [linków względnych](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2).

- Przykład: [Co to jest usługa Azure Rights Management](./understand-explore/what-is-azure-rights-management.md)

Aby utworzyć link do nagłówka w tym samym pliku markdown, Wyświetl źródło opublikowanego artykułu, wyszukaj identyfikator nagłówka (np. `id="blockquote"`i Utwórz link według schematu # + identyfikator (np. `#blockquote`).

- Przykład: [Cytaty](#blockquote)

Aby utworzyć link do nagłówka w pliku markdown w tym samym repozytorium, użyj względny + Link z hasztagiem.

- Przykład: [techniczny procesu rejestracji](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Aby utworzyć link do pliku zewnętrznego, użyj pełnego adresu URL jako łącze.

- Przykład: [Github](http://www.github.com)

Jeśli w pliku markdown występuje adres URL, zostanie on przekształcony w link możliwy do kliknięcia.

- Przykład: http://www.github.com

## <a name="lists"></a>Wyświetla listę

### <a name="ordered-lists"></a>Listy uporządkowane

1. To
1. jest
1. Wystąpił
1. uporządkowane
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Lista uporządkowana z osadzoną listą

1. Tutaj
1. pochodzi
1. Wystąpił
1. osadzone
    1. Julia
    1. Romeo
1. uporządkowane
1. Lista


### <a name="unordered-lists"></a>Listy nieuporządkowane

- To
- jest
- a
- Lista punktowana
- Lista


##### <a name="unordered-list-with-an-embedded-lists"></a>Lista nieuporządkowana z osadzonymi listami

- To
- Lista punktowana
- Lista
    - Rozalina
    - Merkucjo
- zawiera  
- Inne
    1. Tybalt
    1. Marta
- Wyświetla listę


## <a name="horizontal-rule"></a>Linia pozioma

---

## <a name="tables"></a>Tabele

| Tabele        | Czy           | Cool  |
| ------------- |:-------------:| -----:|
| Kolumna 3 jest      | wyrównana do prawej | $1600 |
| Kolumna 2 jest      | wyśrodkowany      |   $12 |
| Kolumna 1 jest domyślnie | wyrównana do lewej     |    $1 |


## <a name="code"></a>kod

### <a name="codeblock"></a>Blok kodu

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>W wierszu kodu

To jest przykład `in-line code`.

## <a name="blockquotes"></a>Cytaty

> Susza trwała już dziesięć milionów lat. i panowanie olbrzymich jaszczurów dawno miał dobiegło końca. Tutaj na równiku — na kontynencie, który będzie kiedyś będzie znany jako Afryka bitwy pod kątem istnienia osiągnął coraz bardziej zaciekła walka o przetrwanie, a zwycięzcę trudno było przewidzieć. W tej jałowej i wyschniętej ziemi tylko małym, szybkim i dzikim można mogli lub liczyć na przetrwanie.

## <a name="images"></a>Obrazy

### <a name="static-image"></a>Obraz statyczny

![to jest tekst alternatywny](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Obraz połączony

[![tekst alternatywny połączonego obrazu](./media/AzRMS_elements.png)](https://azure.microsoft.com)

### <a name="animated-gif"></a>Animowany plik gif

![Animowany plik gif](./media/hololens.gif)

## <a name="alerts"></a>Alerty

### <a name="note"></a>Uwaga

> [!NOTE]
> To jest Uwaga

### <a name="warning"></a>Ostrzeżenie

> [!WARNING]
> To jest ostrzeżenie

### <a name="tip"></a>Porada

> [!TIP]
> To jest porada

### <a name="important"></a>Ważne

> [!IMPORTANT]
> To jest informacja ważne

## <a name="videos"></a>Filmy wideo

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>Youtube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>rozszerzenia docs.MS

### <a name="button"></a>Przycisk

> [!div class="button"]
[linki przycisków](/rights-management)

### <a name="selector"></a>Selektor

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [Pasek](/rights-management/scratch.md)

### <a name="step-by-step"></a>Krok po kroku

>[!div class="step-by-step"]
[Wstępnie](https://www.example.com)
[dalej](https://www.example.com)
