---
title: "Zarządzanie aktualizacjami"
titleSuffix: Configuration Manager
description: "Zarządzanie aktualizacji wdrożenia i Utwórz z programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: "1"
author: mstewart
ms.author: mstewart
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: e6a74030d937c41cfaa328a386daea8760bb01e5
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="manage-software-updates-in-updates-publisher"></a>Zarządzanie aktualizacjami oprogramowania w programie Updates Publisher

*Dotyczy: Program System Center Updates Publisher*     

W System Center Updates Publisher, możesz użyć **roboczym aktualizacje** do zarządzania aktualizacjami oprogramowania i pakietów, które zostały zaimportowane do repozytorium.  

Zadania zarządzania obejmują duplikowania, edycji i wygasa lub ponowne uaktywnianie aktualizacje i pakiety, przypisywania i aktualizacje pakietów do publikacji. Można także wyeksportować niestandardowe katalogi do użycia z innymi instalacjami Updates Publisher.

Aby pobrać aktualizacje, którymi można zarządzać:
-  [Dodaj katalog aktualizacji](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) do instalacji programu Updates Publisher
-  [Importuj](/sccm/sum/tools/updates-publisher-catalogs#import-updates) aktualizacji z tego katalogu do repozytorium.

Możesz również [tworzenie własnych aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher).



## <a name="create-a-duplicate-of-an-update"></a>Utwórz duplikat aktualizacji
Można utworzyć duplikatów ani kopie aktualizacje, które znajdują się w repozytorium. Następnie można zmodyfikować kopię modyfikowanie oryginalnego aktualizacji. Nie można utworzyć kopie pakietów aktualizacji.

Aby utworzyć kopię, wybierz aktualizację w **aktualizacji obszaru roboczego**, a następnie wybierz pozycję **zduplikowane**. Kopiuj aktualizacji pojawia się w tej samej lokalizacji, w obszarze roboczym aktualizacje z *kopię* dodane do jego nazwy.

Możesz utworzyć nową kopię ma stan **Unexpired**, ale w przeciwnym razie zachowuje ustawienia oryginalne.

## <a name="edit-updates-and-bundles"></a>Edytowanie aktualizacji i pakietów
Można wybrać aktualizacje i pakiety, które znajdują się w repozytorium, aby zmodyfikować je.

W **roboczym aktualizacje** wybierz aktualizacji lub pakietu, a następnie wybierz **Edytuj** z **Home** kartę, aby otworzyć Kreatora edycji. Aktualizacje, jak i pakiety mają oddzielne, ale blisko związane kreatorów, które zapewniają te same opcje jako [utworzyć zaktualizować](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) lub [Tworzenie pakietu](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard) kreatorów.

Podczas edytowania, można zmienić wszystkie dostępne szczegóły dotyczące aktualizacji lub pakietu, dzięki czemu mogą być używane w danym środowisku. Na przykład możesz edytować zastosowania lub pierwszeństwo reguły lub zmienić język. Możesz również zmienić produktu i dostawcy, aby przenieść aktualizacji lub pakietu do folderu niestandardowego do grupy aktualizacji na własny użytek.

## <a name="assign-updates-and-bundles-to-a-publication"></a>Przypisz do publikacji aktualizacji i pakietów
Można wybrać aktualizacje i pakiety w **roboczym aktualizacje** , a następnie wybierz **przypisać** z **Home** kartę na Wstążce, aby dodać je do publikacji. Spowoduje to uruchomienie **przypisać aktualizacji oprogramowania** kreatora.
-  Zobacz [opublikować aktualizacje i pakiety](#publish-updates-and-bundles-from-the-updates-workspace) informacji na temat wybierz i opublikować aktualizacje i pakiety jako pojedyncze zadanie.
-  Zobacz [Zarządzanie publikacji](/sccm/sum/tools/updates-publisher-publications) informacji na temat zarządzania grup aktualizacji oraz pakiety jako pojedynczego obiektu. Po aktualizacji można przypisać do publikacji, można zarządzać tej publikacji, który z kolei zawiera wszystkie przypisane aktualizacje.

Po przypisaniu aktualizacji do publikacji:

-   W tej samej publikacji mogą obejmować aktualizacje wygasła i nie wygasł i pakietów.

-   Określ typ publikacji:

    -   **Pełna zawartość** — publikuje Pełna zawartość aktualizacji z serwerem WSUS. W tym metadane i pliki binarne aktualizacji.

    -   **Tylko metadane** — publikuje jedynie metadane; pliki binarne aktualizacji nie są publikowane. Może być wybierz tę opcję, jeśli chcesz zbierać dane zgodności.

    -   **Automatyczne** — ten tryb jest dostępna tylko, gdy nawiązano połączenie Updates Publisher dla programu Configuration Manager (zobacz [serwera programu ConfigMgr](/sccm/sum/tools/updates-publisher-options#configmgr-server) opcję.)

    W przypadku tego typu Updates Publisher kwerendę programu Configuration Manager w celu ustalenia, czy aktualizacje lub pakiety ma być publikowane z pełnej zawartości lub tylko metadane. Całej zawartości podczas aktualizacji są publikowane tylko wtedy, gdy aktualizacji, spełnia **Próg liczby klientów żądana** i **próg rozmiaru źródła pakietu,** określono na **serwera programu ConfigMgr** strona Opcje Updates Publisher.

-   Wybierz publikacji:

    -   Użyj **przypisania aktualizacji oprogramowania do istniejącej publikacji** Jeśli utworzono już publikacji, w której chcesz użyć. Ta opcja nie jest dostępne, dopóki istnieje co najmniej jednej publikacji.

    -   Użyj **przypisania aktualizacji oprogramowania do nowej publikacji** Jeśli nie masz odpowiedniego publikacji. Spowoduje to utworzenie nowej publikacji o określonej nazwie.

Po aktualizacji można przypisać do publikacji, można użyć **roboczym publikacji** do [publikowania](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) lub [wyeksportować](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) publikacji jako grupa.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>Publikowanie aktualizacji i pakiety w obszarze roboczym aktualizacje
Po opublikowaniu aktualizacji i pakiety, Updates Publisher dodaje informacji na temat tych aktualizacji i pakietów (metadanymi) i prawdopodobnie plików binarnych aktualizacji (pełna zawartość), do wdrożenia na urządzeniach z serwera aktualizacji.

Aby mieć możliwość publikowania, należy skonfigurować [serwera aktualizacji](/sccm/sum/tools/updates-publisher-options#update-server) opcję dla programu Updates Publisher. Aby otworzyć tej opcji konfiguracji, przejdź do **roboczym aktualizacje** &gt; **omówienie** i wybierz **skonfigurować serwer WSUS i certyfikat podpisywania.** Można także przejść do strony serwera aktualizacji w opcjach programu Updates Publisher.

Istnieją dwa sposoby publikowania aktualizacji i pakiety:
-   Bezpośrednio w obszarze roboczym aktualizacje. (Zobacz poniższą procedurę *do publikowania aktualizacji i pakiety*.)
-   Jako [publikacji](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) z obszaru roboczego publikacji.  

> [!NOTE]   
> Updates Publisher można publikować tylko aktualizacje, które są 375 megabajtów (MB) lub mniejszy rozmiar w.

### <a name="to-publish-updates-and-bundles"></a>Aby opublikować aktualizacje i pakiety
1.  Przejdź do **roboczym aktualizacje** i wybierz co najmniej jeden aktualizacje i pakiety, które chcesz opublikować. Następnie wybierz pozycję **publikowania** z **Home** karty wstążki.

2.  Na **wybierz** strony **publikowania** kreatora, wybierz jak chcesz opublikować aktualizacje. Opcje są takie same, jak w przypadku [przypisywanie aktualizacje](#assign-updates-and-bundles-to-a-publication): **Pełna zawartość**, **tylko metadane**, lub **automatyczne**.

    Można również podpisać wszystkie aktualizacje przy użyciu nowego certyfikatu publikowania.

3.  Ukończ pracę kreatora.

Jeżeli publikowanie nie powiedzie się, zostanie mu przedstawiona Link do pliku UpdatesPublisher.log, który może dostarczyć więcej informacji.

## <a name="export-updates"></a>Aktualizacje eksportu
Aktualizacje i pakietów można eksportować z repozytorium Updates Publisher, aby utworzyć katalog niestandardowych aktualizacji. Następnie można [dodać](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) , a następnie [zaimportować](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) tego katalogu do innego wystąpienia programu Updates Publisher. (Możesz również [wyeksportować aktualizacji jako publikacji](/sccm/sum/tools/updates-publisher-publications##export-a-publication).)

Aby wyeksportować bezpośrednio, przejdź do **roboczym aktualizacje** > **wszystkie aktualizacje oprogramowania** i wybierz co najmniej jeden aktualizacji i pakietów. Nie można wyeksportować dostawcy lub folder produktu, ale można wybrać folder, a następnie wybierz aktualizacje tego folderu eksportu.

Wybrano co najmniej jednej aktualizacji, wybierz polecenie **wyeksportować** z **Home** karty wstążki, a następnie podaj ścieżkę i nazwę pliku eksportu katalogu.

Konieczne będzie opcji eksportu (Dołącz) aktualizacje oprogramowania zależnych.

## <a name="delete-updates-and-bundles"></a>Usuń aktualizacje i pakiety
Można usunąć aktualizacji i pakietów aktualizacji, aby usunąć je z repozytorium Updates Publisher.

Przejdź do **roboczym aktualizacje** > **wszystkie aktualizacje oprogramowania** i wybierz co najmniej jeden poszczególne aktualizacje. Następnie wybierz pozycję **usunąć** z **Home** karty wstążki.

-   Jeśli zaznaczenie zawiera tylko aktualizacji lub pakietów, które nie zostały opublikowane lub które są uznawane za wygasłe, zostanie wyświetlona prośba o potwierdzenie usunięcia, zanim zostaną one usunięte.

-   Jeśli zaznaczenie zawiera aktualizację lub pakiet, który został opublikowany i nie jest jeszcze wygasła, otrzymają ostrzeżenie. Należy [wygaśnie](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles) te aktualizacje, a następnie opublikować tej zmiany przed ich usunięciem z repozytorium.  

Po usunięciu aktualizacji lub pakietu od dostawcy i ponownie zaimportować ten katalog, aktualizacja zostanie przywrócona do repozytorium.

## <a name="manage-vendor-and-product-folders"></a>Zarządzanie dostawcą i foldery produktu
Aby wyświetlić listę dostawców i produktów dla każdego dostawcy, dla którego zostały zaimportowane lub utworzone aktualizacji, przejdź do **roboczym aktualizacje** > **omówienie** > **wszystkie aktualizacje oprogramowania**.

Foldery dla dostawców i produktów są tworzone automatycznie przez Updates Publisher, korzystając z kreatora do zaimportowania albo do tworzenia, aktualizacji oprogramowania lub pakietu. Można również utworzyć te foldery ręcznie.

-   Aby utworzyć folder dostawcy, w okienku nawigacji **roboczym aktualizacje**, kliknij prawym przyciskiem myszy **wszystkie aktualizacje oprogramowania**, a następnie wybierz pozycję **Tworzenie dostawcy**.

-   Aby utworzyć folder produktu w folderze dostawcy, kliknij prawym przyciskiem myszy folder na dostawcy, a następnie wybierz pozycję **Utwórz produkt**.

Oprócz tworzenia folderów, można Zmień lub usuń dowolnego dostawcy lub folder produktu w repozytorium. Aby to zrobić, kliknij prawym przyciskiem folder i wybierz odpowiednią opcję, **zmienić** lub **usunąć**. Usunięcie folderu spowoduje usunięcie wszystkich aktualizacji i pakietów w tym folderze i jego folderów produktu z repozytorium Updates Publisher.

Aktualizacje można przenosić między dostawcy i foldery produktu, w tym do folderów, które można utworzyć. Aby przenieść aktualizacji lub pakietu do nowego folderu, należy zaznaczyć, a następnie **Edytuj** aktualizacji lub pakietu. Następnie na **informacji** strony Kreatora edycji aktualizacji można ponownie przypisać dostawcy i produkt. Gdy **Edytuj zaktualizować** Kreator zakończy pracę, stosuje zmiany i aktualizacja przenosi do nowego folderu.

## <a name="view-the-xml-of-an-update-or-bundle"></a>Wyświetlanie pliku XML pakietu lub aktualizacji
Można wybrać jedną aktualizację lub pakietu w **aktualizacji obszaru roboczego** , a następnie wybierz **widoku** XML do wyświetlenia struktury XML aktualizacji. Brak opcji do bezpośredniej edycji struktury XML.
