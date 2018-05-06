---
title: Ściągający punkt dystrybucji
titleSuffix: Configuration Manager
description: Informacje o konfiguracji i ograniczenia dotyczące używania punktu dystrybucji ściągania w programie System Center Configuration Manager.
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d6d6f68e913d261a5a23db85707ea0c9ac965cbd
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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

-   Gdy Menedżer transferu pakietów potwierdzi dostępność zawartości, powiadomi ściągający punkt dystrybucji o możliwości rozpoczęcia pobierania zawartości. Jeśli ta kończy się niepowodzeniem powiadomień będzie ponawiał próby oparte na składnika dystrybucji oprogramowania **ustawienia ponawiania** dla ściągających punktów dystrybucji. Po otrzymaniu tego powiadomienia ściągający punkt dystrybucji podejmie próbę pobrania zawartości ze źródłowych punktów dystrybucji.  

-   Gdy ściągający punkt dystrybucji pobiera zawartość Menedżer transferu pakietów zostanie sondowania stanu składnika dystrybucji oprogramowania w oparciu **sondowania ustawienia stanu** dla ściągających punktów dystrybucji.  Po ukończeniu pobierania zawartości punkt dystrybucji ściągania przesyła ten stan do punktu zarządzania.

**Punkt dystrybucji ściągania można skonfigurować** podczas instalowania punktu dystrybucji lub po jego zainstalowaniu, edytując właściwości roli systemu lokacji punktu dystrybucji.  

**Konfigurację punktu dystrybucji ściągania można usunąć** , edytując właściwości punktu dystrybucji. Po usunięciu konfiguracji punktu dystrybucji ściągania, zwraca punkt dystrybucji do normalnego działania i serwera lokacji zarządza przyszłych zawartości przesyła do punktu dystrybucji.  

## <a name="to-configure-software-distribution-component-for-pull-distribution-points"></a>Aby skonfigurować składnika dystrybucji oprogramowania dla punktów dystrybucji ściągania

1.  W konsoli programu Configuration Manager wybierz **administracji** > **witryny**.  

2.  Wybierz odpowiednią witrynę i wybierz **Konfiguruj składniki lokacji** > **dystrybucji oprogramowania**

3. Wybierz **ściągający punkt dystrybucji** kartę.  

4.  W **ustawienia ponawiania** listy, skonfiguruj następujące wartości:  

    -   **Liczba ponownych prób** -liczbę prób Menedżer transferu pakietów powiadamia ściągający punkt dystrybucji pobierania zawartości.  Po przekroczeniu tej liczby Menedżer transferu pakietów spowoduje anulowanie transferu.

    -   **Opóźnienie przed ponowną próbą wykonania (w minutach)** -liczbę minut oczekiwania Menedżer transferu pakietów między próbami. 

5.  W **sondowania ustawienia stanu** listy, skonfiguruj następujące wartości:  

    -   **Liczba sond** -liczbę razy, że Menedżer transferu pakietów kontaktuje się z punktem dystrybucji ściągania można pobrać stanu zadania.  Po przekroczeniu tej liczby ukończenia zadanie Menedżera transferu pakietów spowoduje anulowanie transferu.

    -   **Opóźnienie przed ponowną próbą wykonania (w minutach)** -liczbę minut oczekiwania Menedżer transferu pakietów między próbami. 
    
    > [!NOTE]  
    >  Gdy Menedżer transferu pakietów anuluje zadania, ponieważ przekroczono liczby ponownych prób sondowania stanu punktu dystrybucji ściągania będzie pobierania zawartości.  Po zakończeniu komunikatu o stanie odpowiednie będą wysyłane do Menedżera transferu pakietów i konsolę będzie odzwierciedlać nowy stan.
    
## <a name="limitations-for-pull-distribution-points"></a>Ograniczenia dotyczące punktów dystrybucji ściągania  

-   Punktu dystrybucji w chmurze nie można skonfigurować jako punktu dystrybucji ściągania.  

-   Punktu dystrybucji na serwerze lokacji nie można skonfigurować jako punktu dystrybucji ściągania.  

-   **Konfiguracja wstępnie przygotowanej zawartości zastępuje konfigurację punktu dystrybucji ściągania**. Punkt dystrybucji ściągania skonfigurowany do obsługi wstępnie przygotowanej zawartości będzie oczekiwać na tę zawartość. Nie ściąga zawartości ze źródłowego punktu dystrybucji i, podobnie jak standardowy rozkład punktu Konfiguracja wstępnie przygotowanej zawartości, nie będzie otrzymywać zawartości z serwera lokacji.  

-   **Punkt dystrybucji ściągania nie używa ustawień limitów harmonogram i częstotliwość** podczas przesyłania zawartości. Jeśli skonfigurujesz uprzednio zainstalowanego punktu dystrybucji do punktu dystrybucji ściągania konfiguracje limitów harmonogram i częstotliwość są zapisane, lecz nie jest używane. Jeśli okaże się usunięcie konfiguracji punktu dystrybucji ściągania, harmonogram i częstotliwość konfiguracje limit są implementowane zgodnie z wcześniejszą konfiguracją.  

    > [!NOTE]  
    >  Jeśli punkt dystrybucji jest skonfigurowany jako punkt dystrybucji ściągania **harmonogram** i **limity szybkości** karty nie są widoczne we właściwościach punktu dystrybucji.  

-   Ściągające punkty dystrybucji nie używaj ustawienia na **ogólne** karcie **właściwości składnika dystrybucji oprogramowania** dla każdej lokacji.  Obejmuje to **dystrybucji współbieżnej** i **ponawiania multiemisji** ustawienie.  Użyj **ściągający punkt dystrybucji** kartę, aby skonfigurować ustawienia dla ściągających punktów dystrybucji.

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
<!--sms.503672 -Clarified BITS use-->
-   Gdy punkt dystrybucji ściągania przesyła zawartość, przesyłania przy użyciu **Usługa inteligentnego transferu w tle** (BITS) wbudowane w system operacyjny Windows. Punkt dystrybucji ściągania nie wymaga opcjonalna funkcja rozszerzenie serwera IIS usługi BITS do zainstalowania.

-  Punkt dystrybucji ściągania zaloguje się jego operacji **datatransferservice.log** i **pulldp.log** na komputerze punktu dystrybucji.

## <a name="see-also"></a>Zobacz także  
 [Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   
