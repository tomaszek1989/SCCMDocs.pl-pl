---
title: "Możliwości w Technical Preview 1611 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1611."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 5e77ebbfd3f3d573d903fe58024a22feb9884e4a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1611 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*



Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1611. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    

**Znane problemy w tym Technical Preview:**   
- ***Stan wymagań wstępnych***: Po zainstalowaniu wersji 1611 ogólny stan wymagań wstępnych może pokazać, jak z ostrzeżeniami, ale nie ma wstępnie wymagane składniki spowodował ostrzeżeń. Może to być spowodowane przez dwa następujące wymagania wstępne:
  - Opcje pamięci Utwórz indeks SQL
  - Sprawdza, czy obsługiwana wersja programu SQL Server  

 Ponieważ są one tylko ostrzeżenia, można go zignorować.

- ***PowerShell***: Po podłączeniu do środowiska Windows PowerShell z konsoli programu Configuration Manager może zostać wyświetlony następujący błąd: **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml nie jest podpisany cyfrowo**.  

   Aby rozwiązać ten problem, należy zastępowanie wersji podpisanych z wersji 1610 niektórych plików. Skopiuj wszystkie pliki z następującymi rozszerzeniami z **&lt;katalog instalacji > \AdminConsole\bin\**  folder do instalacji wersji 1610: **psd1**, **.ps1xml**, i **.psm1**. Wklej te pliki do **&lt;katalog instalacji > \AdminConsole\bin\**  folder do instalacji Technical Preview 1611, zastępując wersję 1611 plików.


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Wstępnie buforowanie zawartości dla wdrożeń o dostępności i sekwencji zadań
W tym technical preview dla wdrożeń o dostępności i sekwencji zadań można użyć funkcji wstępne pamięci podręcznej klienci Pobierz tylko odpowiednich treści, zanim użytkownik instaluje zawartość.

Na przykład załóżmy, że chcesz wdrożyć sekwencję zadań uaktualnienia w miejscu systemu Windows 10, tylko pojedynczą sekwencję zadań dla wszystkich użytkowników i mieć wiele architektury i języków. W bieżącej gałęzi, jeśli tworzysz dostępne wdrożenie, a użytkownik kliknie **zainstalować** w programie Software Center pobranie zawartości w tym czasie. Spowoduje to dodanie dodatkowych sprzed instalacji jest gotowy do uruchomienia. Alternatywnie w bieżącej gałęzi w przypadku utworzenia wdrożenia sekwencji zadań dostępnych całej zawartości, do którego odwołuje się sekwencja zadań zostanie pobrana. W tym pakiet uaktualnienia systemu operacyjnego dla wszystkich języków i architektury. W przypadku każdego około 3 GB rozmiar, może być dość duży pakiet do pobrania.

Funkcja zawartości pamięci podręcznej przed zapewnia opcję, aby umożliwić klientowi tylko pobierania zawartości odpowiednich zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie przycisk **zainstalować** w Centrum oprogramowania, zawartość jest gotowa i instalacji uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym.

### <a name="to-configure-the-pre-cache-feature"></a>Aby skonfigurować funkcję wstępne pamięci podręcznej

1. Utwórz pakiety uaktualnienia języków i określonej architektury systemu operacyjnego. Określ architekturę i języka na **źródła danych** pakietu. Dla języka, użyj decimal konwersji (na przykład 1033 jest dziesiętnych dla języka angielskiego i 0x0409 jest odpowiednikiem szesnastkowej). Aby uzyskać szczegółowe informacje, zobacz [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Architektura i języka wartości są używane do spełniają warunki kroku sekwencji zadań, tworzonych w następnym kroku w celu ustalenia, czy pakiet uaktualnienia systemu operacyjnego mają być buforowane wstępnie.
2. Tworzenie sekwencji zadań kroki warunkowego dla różnych języków i architektury. Na przykład dla angielskiej wersji można utworzyć krok zbliżoną do następującej:

    ![właściwości wstępne pamięci podręcznej](media/precacheproperties2.png)

    ![Opcje pamięci podręcznej wstępnego](media/precacheoptions2.png)  

3. Wdrożenie sekwencji zadań. Dla funkcji wstępne pamięci podręcznej skonfiguruj następujące ustawienia:
    - Na **ogólne** zaznacz **wstępnie pobierania zawartości dla tej sekwencji zadań**.
    - Na **ustawienia wdrażania** skonfiguruj sekwencję zadań z **dostępne** dla **celu**. W przypadku utworzenia **wymagane** wdrożenia, funkcje wstępne pamięci podręcznej nie będą działać.
    - Na **Planowanie** karcie dla **Zaplanuj, kiedy to wdrożenie będą dostępne** ustawienie, wybierz odpowiedni czas w przyszłości zapewnia klientom wystarczająco dużo czasu na wstępnie buforowanie zawartości przed udostępnieniem wdrożenia dla użytkowników. Na przykład można ustawić czas dostępności do 3 godzin w przyszłości, aby umożliwić wystarczająco dużo czasu na wstępnie buforowaną zawartości.  
    - Na **punktów dystrybucji** skonfiguruj **opcje wdrażania** ustawienia. Jeśli zawartość nie jest wstępnie buforowana na komputerze klienckim, zanim użytkownik uruchamia proces instalacji, te ustawienia są używane.


### <a name="user-experience"></a>Środowisko użytkownika
- Gdy klient odbierze zasady wdrażania, rozpocznie się wstępnie buforowania zawartości. Obejmuje całą zawartość odwołania (wszystkie inne typy pakietów) oraz tylko pakiet uaktualnienia systemu operacyjnego zgodnym klienta na podstawie warunków ustawienie w sekwencji zadań.
- Podczas wdrażania zostanie udostępniona użytkownikom (ustawienie na **Planowanie** kartę wdrożenia), wyświetla powiadomienia informują użytkowników o nowego wdrożenia i wdrożenie stanie się widoczna w Centrum oprogramowania. Użytkownik może przejść do Centrum oprogramowania i kliknij przycisk **zainstalować** aby rozpocząć instalację.
- Jeśli zawartość nie jest w pełni wstępnie pamięci podręcznej, a następnie go użyje ustawień określonych w **opcji wdrożenia** kartę wdrożenia. Zaleca się, że jest wystarczająco dużo czasu między po utworzeniu wdrożenia i czasu, w którym wdrożenie staje się dostępny dla użytkowników, aby umożliwić klientom wystarczająco dużo czasu na wstępnie buforowanie zawartości.


## <a name="see-also"></a>Zobacz też
[Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md)

