---
title: "Ściągający punkt dystrybucji"
titleSuffix: Configuration Manager
description: "Informacje o konfiguracji i ograniczenia dotyczące używania punktu dystrybucji ściągania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
caps.latest.revision: "9"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: ea8eead4706472a02f216b432ea9f2e6bdf23f66
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="use-a-pull-distribution-point-with-system-center-configuration-manager"></a>Korzystanie z punktu dystrybucji ściągania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Punkt dystrybucji ściągania dla programu System Center Configuration Manager to standardowy punkt dystrybucji uzyskujący zawartość rozproszoną przez pobieranie jej z lokalizacji źródłowej jako klient zamiast zawartość nie jest wypychana do niego z serwera lokacji.  

 Podczas wdrażania zawartości do dużej liczby punktów dystrybucji w lokacji ściągające punkty dystrybucji mogą pomóc w zmniejszeniu obciążenia na serwerze lokacji oraz przyspieszeniu przesyłania zawartości do poszczególnych punktów dystrybucji. Takie zwiększenie efektywności można osiągnąć, odciążając proces przesyłania zawartości do poszczególnych punktów dystrybucji przez proces zarządzania dystrybucją na serwerze lokacji.  

-   Można konfigurować poszczególne punkty dystrybucji jako ściągające punkty dystrybucji.  

-   Dla każdego punktu dystrybucji ściągania należy określić co najmniej jeden źródłowe punkty dystrybucji z których mogą być pobierane wdrożenia (punkt dystrybucji ściągania może uzyskiwać zawartość wyłącznie z punktu dystrybucji określonego jako źródłowy punkt dystrybucji).  

-   Podczas dystrybucji zawartości do punktu dystrybucji ściągania serwer lokacji powiadamia ściągający punkt dystrybucji, który następnie inicjuje pobieranie (transfer) zawartości ze źródłowego punktu dystrybucji. Punkt dystrybucji ściągania zarządza indywidualnie przesyłaniem zawartości, pobierając ją z punktu dystrybucji, na którym już istnieje kopia zawartości.  

Ściągające punkty dystrybucji obsługują te same konfiguracje i funkcje co typowe punkty dystrybucji programu Configuration Manager. Na przykład punkt dystrybucji skonfigurowany jako ściągający punkt dystrybucji obsługuje konfiguracje multiemisji i środowiska PXE, weryfikację zawartości oraz dystrybucję zawartości na żądanie. Ściągający punkt dystrybucji obsługuje komunikację z klientami przy użyciu protokołu HTTP lub HTTPS, obsługuje te same opcje certyfikatów, co inne punkty dystrybucji, oraz może być zarządzany indywidualnie lub jako członek grupy punktów dystrybucji.  

> [!IMPORTANT]
> Chociaż punkt dystrybucji ściągania obsługuje komunikację za pośrednictwem protokołu HTTP i HTTPS, korzystając z programu Configuration Manager, można określić tylko źródłowe punkty dystrybucji, które są skonfigurowane dla protokołu HTTP. Zestaw SDK programu Configuration Manager można użyć do określenia punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS.  

 **Podczas dystrybucji zawartości do punktu dystrybucji ściągania ma miejsce następująca sekwencja zdarzeń.**  

-   Po przesłaniu zawartości do punktu dystrybucji ściągania Menedżer transferu pakietów na serwerze lokacji sprawdzi bazę danych lokacji w celu potwierdzenia, czy zawartość jest dostępna w źródłowym punkcie dystrybucji. Jeśli nie będzie można potwierdzić dostępności zawartości w źródłowym punkcie dystrybucji dla ściągającego punktu dystrybucji, kontrola będzie ponawiana co 20 minut do momentu potwierdzenia dostępności zawartości.  

-   Gdy Menedżer transferu pakietów potwierdzi dostępność zawartości, powiadomi ściągający punkt dystrybucji o możliwości rozpoczęcia pobierania zawartości. Po otrzymaniu tego powiadomienia ściągający punkt dystrybucji podejmie próbę pobrania zawartości ze źródłowych punktów dystrybucji.  

-   Gdy ściągający punkt dystrybucji ukończy pobieranie zawartości, prześle powiadomienie o stanie do punktu zarządzania. Jednak jeśli po 60 minutach, ten stan nie został odebrany, Menedżer transferu pakietów zostanie wznowiona i sprawdza z punktu dystrybucji ściągania, aby upewnić się, czy punkt dystrybucji ściągania została pobrana zawartość. Jeśli pobieranie zawartości będzie w trakcie wykonywania, Menedżer transferu pakietów zostanie uśpiony na 60 minut, po upływie których ponownie sprawdzi stan ściągającego punktu dystrybucji. Ten cykl będzie wykonywany do momentu ukończenia pobierania zawartości przez punkt dystrybucji ściągania.  

**Punkt dystrybucji ściągania można skonfigurować** podczas instalowania punktu dystrybucji lub po jego zainstalowaniu, edytując właściwości roli systemu lokacji punktu dystrybucji.  

**Konfigurację punktu dystrybucji ściągania można usunąć** , edytując właściwości punktu dystrybucji. Po usunięciu konfiguracji punktu dystrybucji ściągania, zwraca punkt dystrybucji do normalnego działania i serwera lokacji zarządza przyszłych zawartości przesyła do punktu dystrybucji.  

## <a name="limitations-for-pull-distribution-points"></a>Ograniczenia dotyczące punktów dystrybucji ściągania  

-   Punktu dystrybucji w chmurze nie można skonfigurować jako punktu dystrybucji ściągania.  

-   Punktu dystrybucji na serwerze lokacji nie można skonfigurować jako punktu dystrybucji ściągania.  

-   **Konfiguracja wstępnie przygotowanej zawartości zastępuje konfigurację punktu dystrybucji ściągania**. Punkt dystrybucji ściągania skonfigurowany do obsługi wstępnie przygotowanej zawartości będzie oczekiwać na tę zawartość. Nie ściąga zawartości ze źródłowego punktu dystrybucji i, podobnie jak standardowy rozkład punktu Konfiguracja wstępnie przygotowanej zawartości, nie będzie otrzymywać zawartości z serwera lokacji.  

-   **Punkt dystrybucji ściągania nie używa ustawień limitów szybkości** podczas przesyłania zawartości. W przypadku skonfigurowania uprzednio zainstalowanego punktu dystrybucji jako punktu dystrybucji ściągania konfiguracje limitów szybkości zostaną zapisane, lecz nie będą używane. Jeśli okaże się usunięcie konfiguracji punktu dystrybucji ściągania, wcześniej skonfigurowane ustawienia limitów szybkości są implementowane.  

    > [!NOTE]  
    >  Po skonfigurowaniu punktu dystrybucji jako punktu dystrybucji ściągania karta **Limity szybkości** nie będzie widoczna w oknie właściwości punktu dystrybucji.  

-   Punkt dystrybucji ściągania nie używa opcji **Ustawienia ponawiania** do dystrybucji zawartości. Opcję**Ustawienia ponawiania** można skonfigurować w ramach ustawień **Właściwości składnika dystrybucji oprogramowania** poszczególnych lokacji. Aby wyświetlić lub skonfigurować te właściwości, w **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz **witryny**. Następnie w okienku wyników wybierz lokację, a następnie na **Home** wybierz opcję **Konfiguruj składniki lokacji**. Na koniec wybierz **dystrybucji oprogramowania**.  

-   Do przesłania zawartości ze źródłowego punktu dystrybucji w lesie zdalnym, komputera obsługującego punkt dystrybucji ściągania musi mieć zainstalowanego klienta programu Configuration Manager. Konto dostępu do sieci, które mogą uzyskiwać dostęp do źródłowego punktu dystrybucji musi być skonfigurowana do użycia.  

-   Na komputerze, który jest skonfigurowany jako dystrybucji ściągania punkt i, na którym działa klient programu Configuration Manager, wersja klienta musi być w wersji zgodnej z wersją lokacji programu Configuration Manager, który instaluje punkt dystrybucji ściągania. Jest to wymagane dla punktu dystrybucji ściągania można użyć CCMFramework wspólnego zarówno dla punktu dystrybucji ściągania, jak i klienta programu Configuration Manager.  

## <a name="about-source-distribution-points"></a>Informacje o współużytkowanych punktach dystrybucji  
 Podczas konfigurowania punktu dystrybucji ściągania należy określić co najmniej jeden źródłowy punkt dystrybucji:  

-   Tylko punkty dystrybucji spełniające kryteria źródłowego punktu dystrybucji będą wyświetlane.  

-   Ściągający punkt dystrybucji można wskazać jako źródłowy punkt dystrybucji dla innego ściągającego punktu dystrybucji.  

-   Tylko te punkty dystrybucji, które obsługują HTTP można określić jako źródłowe punkty dystrybucji, korzystając z programu Configuration Manager.  

-   Zestaw SDK programu Configuration Manager można użyć do określenia punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS. Aby użyć źródłowego punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS, ściągający punkt dystrybucji musi znajdować się na komputerze, na którym działa klient programu Configuration Manager.  

Każdemu źródłowemu punktowi dystrybucji na liście w punkcie dystrybucji ściągania można przypisać priorytet:  

-   Każdemu źródłowemu punktowi dystrybucji można przypisać inny priorytet; można też przypisać jeden priorytet wielu takim punktom.  

-   Priorytet określa kolejność, w jakiej ściągający punkt dystrybucji będzie żądał zawartości od danego źródłowego punktu dystrybucji.  

-   Ściągające punkty dystrybucji kontaktują się w pierwszej kolejności ze źródłowym punktem dystrybucji o najniższej wartości priorytetu.  Jeśli na liście znajduje się wiele źródłowych punktów dystrybucji o takim samym priorytecie, punkt dystrybucji ściągania w sposób niejednoznaczny wybierze jeden z nich.  

-   Gdy zawartość nie będzie dostępna w wybranym źródle, punkt dystrybucji ściągania podejmie próbę pobrania zawartości z innego punktu dystrybucji o takim samym priorytecie.  

-   Jeśli zawartość nie będzie dostępna w żadnym z punktów dystrybucji o danym priorytecie, punkt dystrybucji ściągania będzie podejmować próby pobrania zawartości z punktu dystrybucji z priorytetem o wyższej wartości do momentu zlokalizowania zawartości lub uśpienia punktu dystrybucji ściągania na 30 minut przed ponownym rozpoczęciem procesu.  

Podczas pobierania zawartości ze źródłowego punktu dystrybucji punkt dystrybucji ściągania będzie traktowany jako klient w kolumnie **Klienci, do których uzyskano dostęp (unikatowi)** raportu **Podsumowanie użycia punktu dystrybucji** .  

 Punkt dystrybucji ściągania używa domyślnie swojego **konta komputera** do przesłania zawartości ze źródłowego punktu dystrybucji. Jednak jeśli punkt dystrybucji ściągania przesyła zawartość ze źródłowego punktu dystrybucji, który znajduje się w lesie zdalnym, punkt dystrybucji ściągania zawsze używać konta dostępu do sieci. Ten proces wymaga, czy komputer ma zainstalowany klient programu Configuration Manager oraz że konto dostępu do sieci jest skonfigurowana do użycia ma dostęp do źródłowego punktu dystrybucji.  

## <a name="about-content-transfers"></a>Informacje o przesyłaniu zawartości  
 Aby zarządzać transferem zawartości, należy użyć ściągające punkty dystrybucji **CCMFramework** składnika oprogramowania klienckiego programu Configuration Manager.  

-   Ta struktura jest instalowana przez **Pulldp.msi** podczas konfigurowania punktu dystrybucji do punktu dystrybucji ściągania. Platformę nie wymaga klienta programu Configuration Manager.  

-   Aby umożliwić działanie ściągającego punktu dystrybucji po jego zainstalowaniu na komputerze punktu dystrybucji musi być dostępna usługa CCMExec.  

-   Zawartość będzie przesyłana do punktu dystrybucji ściągania przy użyciu **usługi inteligentnego transferu w tle (BITS)** , a działanie punktu dystrybucji ściągania będzie rejestrowane na komputerze punktu dystrybucji w plikach **datatransferservice.log** oraz **pulldp.log** .  

## <a name="see-also"></a>Zobacz także  
 [Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   
