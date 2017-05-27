---
title: "Zarządzanie aktualizacjami | Dokumentacja firmy Microsoft"
description: "Zarządzanie aktualizacji, wdrażanie i tworzenie za pomocą programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 1d6c3b1db14867bdbc5cae8ded099d9024a79549
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-updates-in-updates-publisher"></a>Zarządzanie aktualizacjami oprogramowania w Updates Publisher

*Dotyczy: System Center Updates Publisher*     

W programie System Center Updates Publisher, użyj **obszar roboczy aktualizacje** do zarządzania aktualizacjami oprogramowania i pakiety, które zostały zaimportowane do repozytorium.  

Zadania zarządzania obejmują powielanie, edytowania i wygasa lub ponowne uaktywnianie aktualizacje i pakiety i przypisywanie aktualizacje i pakiety do publikacji. Można także eksportować niestandardowe katalogi do użytku z innych instalacji Updates Publisher.

Aby uzyskać aktualizacje, którymi można zarządzać:
-  [Dodawanie aktualizacji katalogu](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) do instalacji aktualizacji wydawcy
-  [Importuj](/sccm/sum/tools/updates-publisher-catalogs#import-updates) aktualizacje z tego katalogu do repozytorium.

Możesz również [tworzenia własnych aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher).



## <a name="create-a-duplicate-of-an-update"></a>Utwórz duplikat aktualizacji
Można utworzyć duplikaty lub kopie aktualizacje, które znajdują się w repozytorium. Następnie można zmodyfikować kopiowania zamiast modyfikowania oryginalnej aktualizacji. Nie można utworzyć kopii pakiety aktualizacji.

Utwórz kopię, wybierz aktualizację w **aktualizacje obszaru roboczego**, a następnie wybierz **zduplikowane**. Kopiuj aktualizacji pojawi się w tej samej lokalizacji, w obszarze roboczym aktualizacje z *kopię* dodane do jego nazwy.

Możesz utworzyć nową kopię ma stan **Unexpired**, ale w przeciwnym razie zachowuje ustawienia oryginalne.

## <a name="edit-updates-and-bundles"></a>Edytuj pakiety i aktualizacje
Można wybrać aktualizacje i pakiety znajdujące się w repozytorium ich modyfikować.

W **obszar roboczy aktualizacje** wybierz aktualizacji lub pakietu, a następnie wybierz **edytować** z **Home** kartę, aby otworzyć Kreatora edycji. Aktualizacje, jak i zestawy mają oddzielnej, ale blisko związane kreatorów, które są dostępne te same opcje co [tworzenie aktualizacji](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) lub [Utwórz pakiet](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard) kreatorów.

Podczas edycji, można zmienić wszystkie dostępne szczegóły dotyczące aktualizacji lub pakietu, dzięki czemu mogą być używane w danym środowisku. Na przykład możesz edytować zasady stosowania lub priorytet lub zmień język. Można również zmienić produktu i dostawcy, aby przenieść aktualizacji lub pakietu do folderu niestandardowego do grupy aktualizacji na własny użytek.

## <a name="assign-updates-and-bundles-to-a-publication"></a>Przypisz aktualizacje i pakiety do publikacji
Można wybrać aktualizacje i pakiety w **obszar roboczy aktualizacje** , a następnie wybierz **przypisać** z **Home** karta na Wstążce, aby dodać je do publikacji. Spowoduje to uruchomienie **przypisać aktualizacje oprogramowania** kreatora.
-  Zobacz [opublikować aktualizacje i pakiety](#publish-updates-and-bundles-from-the-updates-workspace) informacji na temat wybierz i opublikować aktualizacje i pakiety jako pojedyncze zadanie.
-  Zobacz [Zarządzanie publikacje](/sccm/sum/tools/updates-publisher-publications) informacji na temat sposobu zarządzania grupami aktualizacji i pakiety jako pojedynczy obiekt. Po przypisaniu aktualizacje do publikacji, można zarządzać publikacji i z kolei zawiera wszystkie przypisane aktualizacje.

Po przypisaniu aktualizacje do publikacji:

-   Może zawierać wygasłe i wygasłe aktualizacje i pakiety w jednej publikacji.

-   Określ typ publikacji:

    -   **Pełna zawartość** — publikuje Pełna zawartość aktualizacji z serwerem WSUS. Obejmuje to metadane i pliki binarne aktualizacji.

    -   **Tylko metadane** — to publikuje tylko metadane; pliki binarne aktualizacji nie są publikowane. Może być wybierz tę opcję, jeśli chcesz zebrać dane zgodności.

    -   **Automatyczne** — w tym trybie jest dostępna tylko po połączeniu wydawcy aktualizacji programu Configuration Manager (zobacz [serwera programu ConfigMgr](/sccm/sum/tools/updates-publisher-options#configmgr-server) opcję.)

    W przypadku tego typu Updates Publisher kwerendę programu Configuration Manager w celu ustalenia, czy aktualizacje lub pakiety ma być publikowane z pełnej zawartości lub jedynie metadane. Całej zawartości dla aktualizacji została opublikowana tylko wtedy, gdy aktualizacji, spełnia **Próg liczby klienta żądanego** i **próg wielkości źródło pakietu,** określono na **serwera programu ConfigMgr** strony Opcje aktualizacji wydawcy.

-   Wybierz publikacji:

    -   Użyj **przypisać aktualizacji oprogramowania do istniejącej publikacji** podczas została już utworzona publikacji, która ma być używana. Ta opcja nie jest dostępne, dopóki nie istnieje co najmniej jednej publikacji.

    -   Użyj **przypisać aktualizacji oprogramowania do nowej publikacji** gdy nie ma odpowiednich publikacji. Spowoduje to utworzenie nowej publikacji o określonej nazwie.

Po przypisaniu aktualizacje do publikacji, można użyć **obszaru roboczego publikacji** do [publikowania](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) lub [wyeksportować](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) publikacji jako grupa.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>Publikowanie aktualizacji i pakiety z obszaru roboczego aktualizacje
Po opublikowaniu aktualizacji i pakiety, Updates Publisher dodaje informacje o tych aktualizacjach i pakiety (metadane) i prawdopodobnie plików binarnych aktualizacji (pełna zawartość), na serwerze aktualizacji do wdrożenia na urządzeniach.

Zanim opcji publikowania, należy skonfigurować [serwera aktualizacji](/sccm/sum/tools/updates-publisher-options#update-server) opcję Updates Publisher. Aby otworzyć ta opcja konfiguracji, przejdź do **obszar roboczy aktualizacje** &gt; **Przegląd** i wybierz **konfigurowania programu WSUS i certyfikat podpisywania.** Możesz również do strony serwera aktualizacji w opcjach programu Updates Publisher.

Istnieją dwa sposoby publikowania aktualizacji i pakiety:
-   Bezpośrednio w obszarze roboczym aktualizacje. (Zobacz procedurę, *publikowania aktualizacji i pakiety*.)
-   Jako [publikacji](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) z obszaru roboczego publikacji.  

> [!NOTE]   
> Updates Publisher można publikować tylko aktualizacje, które są 375 megabajtów (MB) lub mniej w rozmiarze.

### <a name="to-publish-updates-and-bundles"></a>Aby opublikować pakiety i aktualizacje
1.  Przejdź do **obszar roboczy aktualizacje** i wybierz co najmniej jeden aktualizacje i pakiety, które chcesz opublikować. Następnie wybierz **publikowania** z **Home** karty wstążki.

2.  Na **wybierz** strony **publikowania** kreatora, wybierz jak chcesz opublikować aktualizacje. Opcje są takie same jak w przypadku [przypisanie aktualizacji](#assign-updates-and-bundles-to-a-publication): **Pełna zawartość**, **tylko metadane**, lub **automatyczne**.

    Można też zarejestrować wszystkie aktualizacje przy użyciu nowego certyfikatu publikowania.

3.  Ukończ pracę kreatora.

Jeśli publikowanie zakończy się niepowodzeniem, zostanie wyświetlona łącze do pliku UpdatesPublisher.log, który może zawierać dodatkowe informacje.

## <a name="export-updates"></a>Eksportuj aktualizacji
Pakiety i aktualizacje można eksportować z repozytorium Updates Publisher, aby utworzyć niestandardowe aktualizacji katalogu. Następnie można [dodać](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) i następnie [importowania](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) tego katalogu do innego wystąpienia programu Updates Publisher. (Możesz też [wyeksportować aktualizacje jako publikację](/sccm/sum/tools/updates-publisher-publications##export-a-publication).)

Aby wyeksportować bezpośrednio, przejdź do **obszar roboczy aktualizacje** > **wszystkie aktualizacje oprogramowania** i wybierz jedną lub więcej aktualizacji i pakiety. Nie można wyeksportować dostawcy lub folder produktu, ale można wybierz folder, a następnie wybierz aktualizacje w tym folderze do eksportu.

Wybrano co najmniej jednej aktualizacji, wybierz polecenie **wyeksportować** z **Home** karty wstążki, a następnie podaj ścieżkę i nazwę pliku eksportu katalogu.

Trzeba będzie opcji eksportu (Dołącz) aktualizacje oprogramowania zależne.

## <a name="delete-updates-and-bundles"></a>Usuń pakiety i aktualizacje
Aktualizacje i pakiety aktualizacji, aby usunąć je z repozytorium Updates Publisher, można usunąć.

Przejdź do **obszar roboczy aktualizacje** > **wszystkie aktualizacje oprogramowania** i wybierz co najmniej jeden poszczególnych aktualizacji. Następnie wybierz **usunąć** z **Home** karty wstążki.

-   Jeśli wybór zawiera tylko aktualizacje lub pakiety, które nie zostały opublikowane lub które wygasły, pojawi się monit o potwierdzenie usunięcia są usuwane.

-   Jeśli wybór zawiera pakiet, który został opublikowany i jeszcze nie wygasł lub aktualizacji, otrzymają ostrzeżenie. Należy [wygaśnie](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles) te aktualizacje, a następnie opublikować zmiany przed ich usunięciem z repozytorium.  

W przypadku usuwania aktualizacji lub pakietu od dostawcy, a następnie ponownie zaimportować ten katalog, aktualizacja została przywrócona do repozytorium.

## <a name="manage-vendor-and-product-folders"></a>Zarządzanie dostawcy i foldery produktu
Aby wyświetlić listę dostawców i produktów dla każdego dostawcy, dla której zostały zaimportowane lub utworzone aktualizacji, przejdź do **obszar roboczy aktualizacje** > **Przegląd** > **wszystkie aktualizacje oprogramowania**.

Foldery dla dostawców i produktów są tworzone automatycznie przez Updates Publisher, korzystając z Kreatora importowania lub tworzenia aktualizacji oprogramowania lub pakietu. Można również utworzyć te foldery ręcznie.

-   Aby utworzyć folder dostawcy, w okienku nawigacji **obszar roboczy aktualizacje**, kliknij prawym przyciskiem myszy **wszystkie aktualizacje oprogramowania**, a następnie wybierz **Tworzenie dostawcy**.

-   Aby utworzyć folder produktu w folderze dostawcy, kliknij prawym przyciskiem myszy w folderze dostawcy, a następnie wybierz **tworzenia produktu**.

Oprócz tworzenia folderów, można zmienić lub usunąć wszystkie dostawcy lub folder produktu w repozytorium. Aby to zrobić, kliknij prawym przyciskiem myszy folder i wybierz odpowiednią opcję, **zmienić** lub **usunąć**. Usunięcie folderu spowoduje usunięcie wszystkich aktualizacji i pakiety w tym folderze i jego folderów produktu z repozytorium Updates Publisher.

Aktualizacje można przełączać się między dostawcy i folderów produktu, w tym do folderów, które można utworzyć. Aby przenieść aktualizacji lub pakietu do nowego folderu, należy wybrać a następnie **edytować** pakietu lub aktualizacji. Następnie na **informacji** strony Kreatora edycji aktualizacji można ponownie przypisać dostawcy i produktu. Gdy **edytować aktualizacji** Kreator zakończy pracę, dotyczy i aktualizacja zostanie przeniesiona do nowego folderu.

## <a name="view-the-xml-of-an-update-or-bundle"></a>Wyświetl plik XML pakietu lub aktualizacji
Można wybrać jedną aktualizację lub pakietu w **aktualizacje obszaru roboczego** , a następnie wybierz **widoku** XML, aby wyświetlić strukturę XML aktualizacji. Nie istnieją żadne opcje bezpośredniego edytowania struktury XML.

