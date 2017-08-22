---
title: Funkcje w wersji zapoznawczej Technical Preview 1611 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1611."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5e77ebbfd3f3d573d903fe58024a22feb9884e4a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1611 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*



W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1611. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    

**Znane problemy w tej wersji Technical Preview:**   
- ***Stan wymagań wstępnych***: Po zainstalowaniu wersji 1611 ogólny stan wymagań wstępnych mogą być wyświetlane zgodnie z ostrzeżeniami, ale nie ma wstępnie wymagane składniki spowodował ostrzeżenia. Może to być spowodowane następujące dwa warunki wstępne:
  - Opcje pamięci utworzyć indeks SQL
  - Sprawdza, czy obsługiwana wersja programu SQL Server  

 Ponieważ są one tylko ostrzeżenia, możesz go zignorować.

- ***PowerShell***: Po podłączeniu do środowiska Windows PowerShell z poziomu konsoli programu Configuration Manager może zostać wyświetlony następujący błąd: **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml nie jest podpisany cyfrowo**.  

   Aby rozwiązać ten problem, należy zastępując podpisem wersji z wersji 1610 niektórych plików. Skopiuj wszystkie pliki z następującymi rozszerzeniami z **&lt;katalog instalacji > \AdminConsole\bin\**  folder instalacji wersji 1610: **psd1**, **.ps1xml**, i **.psm1**. Wklej te pliki do **&lt;katalog instalacji > \AdminConsole\bin\**  folderu w instalacji Technical Preview 1611, zastępując wersję 1611 plików.


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Wstępne wypełnienie pamięci podręcznej dla wdrożeń dostępnych i sekwencji zadań
W tym technical preview do wdrożeń dostępnych i sekwencji zadań można korzystać z funkcji wstępne pamięci podręcznej klienci Pobierz tylko odpowiedniej zawartości, zanim użytkownik instaluje zawartości.

Załóżmy na przykład, że chcesz wdrożyć sekwencję zadań uaktualnienia w miejscu systemu Windows 10, tylko pojedynczej sekwencji zadań dla wszystkich użytkowników i mieć wiele architektur i języków. W bieżącej gałęzi, jeśli utworzenie dostępne wdrożenia, a następnie użytkownik klika polecenie **zainstalować** w Centrum oprogramowania, pobranie zawartości w tym czasie. Spowoduje to dodanie dodatkowych czas instalacji jest gotowy do uruchomienia. Alternatywnie w wersji Current Branch po utworzeniu wdrożenie dostępnej sekwencji zadań, cała zawartość, do którego odwołuje się sekwencja zadań zostanie pobrana. W tym pakiecie uaktualnienia systemu operacyjnego dla wszystkich języków i architektury. W przypadku każdego około 3 GB rozmiar, może być dość duży pakiet do pobrania.

Funkcja zawartości pamięci podręcznej przed udostępnia opcję, aby umożliwić klientom pobieranie tylko zawartość dotyczy zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie **zainstalować** w programie Software Center zawartości są gotowe, a instalacja uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym.

### <a name="to-configure-the-pre-cache-feature"></a>Aby skonfigurować funkcję wstępne pamięci podręcznej

1. Utwórz pakiety uaktualnień dla określonych architektur i języków systemu operacyjnego. Określ architekturę i język na **źródła danych** pakietu. Dla języka, użyj konwersji dziesiętne (na przykład 1033 jest dziesiętnego dla języka angielskiego i 0x0409 jest odpowiednikiem szesnastkowym). Aby uzyskać więcej informacji, zobacz [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Wartości architekturę i język są używane do dopasowania warunków krok sekwencji zadań, utworzonych w następnym kroku w celu ustalenia, czy pakiet uaktualnienia systemu operacyjnego mają być buforowane wstępnie.
2. Tworzenie sekwencji zadań z warunkowego kroki dla innych języków i architektur. Na przykład dla angielskiej wersji można utworzyć krok podobne do poniższych:

    ![właściwości przed pamięci podręcznej](media/precacheproperties2.png)

    ![opcje wstępne pamięci podręcznej](media/precacheoptions2.png)  

3. Wdróż sekwencję zadań. Dla funkcji wstępne pamięci podręcznej skonfiguruj następujące ustawienia:
    - Na **ogólne** wybierz opcję **wstępnie pobrać zawartość do tej sekwencji zadań**.
    - Na **ustawienia wdrażania** skonfiguruj sekwencji zadań z **dostępne** dla **celu**. W przypadku utworzenia **wymagane** wdrożenia, funkcje pamięci podręcznej wstępne nie będą działać.
    - Na **Planowanie** karcie dla **Zaplanuj, kiedy to wdrożenie będzie dostępne** ustawienie, wybierz czas w przyszłości, zapewniająca klientów wystarczająco dużo czasu na wstępnie buforują zawartość przed udostępnieniem wdrożenia dla użytkowników. Na przykład można ustawić czas dostępności jako 3 godziny w przyszłości poczekać na wstępnie pamięci podręcznej zawartości.  
    - Na **punktów dystrybucji** skonfiguruj **opcje wdrażania** ustawienia. Jeśli zawartość nie jest wstępnie buforowane na kliencie, zanim użytkownik uruchamia proces instalacji, te ustawienia są używane.


### <a name="user-experience"></a>Środowisko użytkownika
- Gdy klient odbierze zasady wdrażania, zostanie ona rozpoczęta wstępnie buforowania zawartości. Zawiera wszystkie przywoływanej zawartości (wszystkie inne typy pakietów) oraz tylko pakiet uaktualnienia systemu operacyjnego zgodny klienta na podstawie wybranych warunków ustawienie w sekwencji zadań.
- Gdy wdrożenie jest udostępniane użytkownikom (ustawienie **Planowanie** kartę wdrożenia), wyświetlane jest powiadomienie informować użytkowników o nowego wdrożenia i wdrożenie staje się widoczna w Centrum oprogramowania. Użytkownik może przejść do Centrum oprogramowania i kliknij przycisk **zainstalować** do rozpoczęcia instalacji.
- Jeśli zawartość nie jest w pełni wstępnie pamięci podręcznej, a następnie będzie używać ustawień określonych w **opcji wdrażania** kartę wdrożenia. Zaleca się, czy jest wystarczająco dużo czasu między po utworzeniu wdrożenia i czasu, w którym wdrożenia staną się dostępne dla użytkowników, aby umożliwić klientom wystarczająco dużo czasu na wstępnie buforują zawartość.


## <a name="see-also"></a>Zobacz też
[Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md)
