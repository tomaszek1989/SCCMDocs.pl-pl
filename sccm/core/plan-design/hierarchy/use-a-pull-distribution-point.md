---
title: "Ściągający punkt dystrybucji | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat konfiguracji i ograniczenia dotyczące korzystania z punktu dystrybucji z System Center Configuration Manager."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9b366262ae59a8cb57c0f1760b961194d17bcf52
ms.openlocfilehash: db5039ff6cb93e3099b096196d49a1f06c315a6b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="use-a-pull-distribution-point-with-system-center-configuration-manager"></a>Korzystanie z punktu dystrybucji ściągania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Punkt dystrybucji programu System Center Configuration Manager jest standardowy punkt dystrybucji uzyskuje treści, pobierając go z lokalizacji źródłowej, takich jak klienta, zamiast zawartości przekazania jej z serwera lokacji.  

 Podczas wdrażania zawartości do dużej liczby punktów dystrybucji w lokacji, punktów dystrybucji ściągania pomaga ograniczyć obciążenie związane z przetwarzaniem na serwerze lokacji oraz przyspieszeniu przesyłania zawartości do poszczególnych punktów dystrybucji. Takie zwiększenie efektywności można osiągnąć, odciążając proces przesyłania zawartości do poszczególnych punktów dystrybucji przez proces zarządzania dystrybucją na serwerze lokacji.  

-   Można konfigurować poszczególne punkty dystrybucji do punktu dystrybucji.  

-   Dla każdego punktu dystrybucji należy określić co najmniej jeden źródłowych punktów dystrybucji z których można uzyskać wdrożeń (punkt dystrybucji może uzyskiwać zawartość wyłącznie z punktu dystrybucji określonego jako źródłowy punkt dystrybucji).  

-   Podczas dystrybucji zawartości do punktu dystrybucji serwer lokacji powiadamia ściągający punkt dystrybucji, który następnie inicjuje pobieranie (transfer) zawartości ze źródłowego punktu dystrybucji. Punkt dystrybucji ściągania zarządza indywidualnie przesyłaniem zawartości, pobierając ją z punktu dystrybucji, na którym już istnieje kopia zawartości.  

Punkty dystrybucji obsługują te same konfiguracje i funkcje, co typowe punkty dystrybucji programu Configuration Manager. Na przykład punkt dystrybucji skonfigurowany jako ściągający punkt dystrybucji obsługuje konfiguracje multiemisji i środowiska PXE, weryfikację zawartości oraz dystrybucję zawartości na żądanie. Ściągający punkt dystrybucji obsługuje komunikację z klientami przy użyciu protokołu HTTP lub HTTPS, obsługuje te same opcje certyfikatów, co inne punkty dystrybucji, oraz może być zarządzany indywidualnie lub jako członek grupy punktów dystrybucji.  

> [!IMPORTANT]
> Choć ściągający punkt dystrybucji obsługuje protokoły komunikacyjne HTTP i HTTPS, jeśli korzystasz z programu Configuration Manager, można określić jedynie źródłowe punkty dystrybucji, które są skonfigurowane dla protokołu HTTP. Zestaw SDK programu Configuration Manager można użyć do określenia źródłowego punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS.  

 **Podczas dystrybucji zawartości do punktu dystrybucji ściągania ma miejsce następująca sekwencja zdarzeń.**  

-   Po przesłaniu zawartości do punktu dystrybucji ściągania Menedżer transferu pakietów na serwerze lokacji sprawdzi bazę danych lokacji w celu potwierdzenia, czy zawartość jest dostępna w źródłowym punkcie dystrybucji. Jeśli nie będzie można potwierdzić dostępności zawartości w źródłowym punkcie dystrybucji dla ściągającego punktu dystrybucji, kontrola będzie ponawiana co 20 minut do momentu potwierdzenia dostępności zawartości.  

-   Gdy Menedżer transferu pakietów potwierdzi dostępność zawartości, powiadomi ściągający punkt dystrybucji o możliwości rozpoczęcia pobierania zawartości. Po otrzymaniu tego powiadomienia ściągający punkt dystrybucji podejmie próbę pobrania zawartości ze źródłowych punktów dystrybucji.  

-   Gdy ściągający punkt dystrybucji ukończy pobieranie zawartości, prześle powiadomienie o stanie do punktu zarządzania. Jednak jeśli po 60 minut, ten stan nie został odebrany, Menedżer transferu pakietów budzi i sprawdza z punktu dystrybucji, aby potwierdzić, czy punkt dystrybucji ściągania pobranie zawartości. Jeśli pobieranie zawartości będzie w trakcie wykonywania, Menedżer transferu pakietów zostanie uśpiony na 60 minut, po upływie których ponownie sprawdzi stan ściągającego punktu dystrybucji. Ten cykl będzie wykonywany do momentu ukończenia pobierania zawartości przez punkt dystrybucji ściągania.  

**Punkt dystrybucji ściągania można skonfigurować** podczas instalowania punktu dystrybucji lub po jego zainstalowaniu, edytując właściwości roli systemu lokacji punktu dystrybucji.  

**Konfigurację punktu dystrybucji można usunąć** , edytując właściwości punktu dystrybucji. Kiedy usunąć konfigurację punktu dystrybucji zwraca punkt dystrybucji do normalnego działania i serwerze lokacji zarządzającym zawartością przyszłych przesyła do punktu dystrybucji.  

## <a name="limitations-for-pull-distribution-points"></a>Ograniczenia dotyczące punktów dystrybucji ściągania  

-   Punktu dystrybucji w chmurze nie można skonfigurować jako punktu dystrybucji ściągania.  

-   Punktu dystrybucji na serwerze lokacji nie można skonfigurować jako punktu dystrybucji ściągania.  

-   **Konfiguracja wstępnie przygotowanej zawartości zastępuje konfigurację punktu dystrybucji ściągania**. Punkt dystrybucji ściągania skonfigurowany do obsługi wstępnie przygotowanej zawartości będzie oczekiwać na tę zawartość. Nie będzie ściągać zawartości z punktu dystrybucji i, podobnie jak standardowy rozkład punktu obsługi wstępnie przygotowanej zawartości, nie otrzymywać zawartości z serwera lokacji.  

-   **Punkt dystrybucji ściągania nie używa ustawień limitów szybkości** podczas przesyłania zawartości. W przypadku skonfigurowania uprzednio zainstalowanego punktu dystrybucji jako punktu dystrybucji ściągania konfiguracje limitów szybkości zostaną zapisane, lecz nie będą używane. Jeśli później usunąć konfigurację punktu dystrybucji, ustawienia limitów szybkości zostaną zastosowane zgodnie z wcześniejszą konfiguracją.  

    > [!NOTE]  
    >  Po skonfigurowaniu punktu dystrybucji jako punktu dystrybucji ściągania karta **Limity szybkości** nie będzie widoczna w oknie właściwości punktu dystrybucji.  

-   Punkt dystrybucji ściągania nie używa opcji **Ustawienia ponawiania** do dystrybucji zawartości. Opcję**Ustawienia ponawiania** można skonfigurować w ramach ustawień **Właściwości składnika dystrybucji oprogramowania** poszczególnych lokacji. Aby wyświetlić lub skonfigurować te właściwości w **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz **witryny**. Następnie w okienku wyników wybierz lokację, a następnie na **Home** zaznacz **Konfiguruj składniki lokacji**. Wreszcie, wybierz **dystrybucji oprogramowania**.  

-   Aby przesłać zawartość ze źródłem punkt dystrybucji w lesie zdalnym komputera obsługującego ściągający punkt dystrybucji musi mieć zainstalowanego klienta programu Configuration Manager. Konto dostępu do sieci, które ma dostęp do źródłowego punktu dystrybucji należy skonfigurować do użytku.  

-   Na komputerze, który jest skonfigurowany jako dystrybucji ściągania punktu i z uruchomionym klientem programu Configuration Manager, wersja klienta musi być wersji zgodnej z wersją lokacji programu Configuration Manager, który instaluje ściągający punkt dystrybucji. Jest to wymagane dla punktu dystrybucji do użycia CCMFramework wspólnego zarówno ściągający punkt dystrybucji, jak i klienta programu Configuration Manager.  

## <a name="about-source-distribution-points"></a>Informacje o współużytkowanych punktach dystrybucji  
 Podczas konfigurowania punktu dystrybucji ściągania należy określić co najmniej jeden źródłowy punkt dystrybucji:  

-   Tylko punkty dystrybucji spełniające kryteria źródłowego punktu dystrybucji będą wyświetlane.  

-   Ściągający punkt dystrybucji można wskazać jako źródłowy punkt dystrybucji dla innego ściągającego punktu dystrybucji.  

-   Jeśli korzystasz z programu Configuration Manager można określić tylko te punkty dystrybucji, które obsługują protokół HTTP jako źródłowe punkty dystrybucji.  

-   Zestaw SDK programu Configuration Manager można użyć do określenia źródłowego punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS. Aby użyć źródłowego punktu dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS, ściągający punkt dystrybucji musi być się na komputerze z uruchomionym klientem programu Configuration Manager.  

Każdemu źródłowemu punktowi dystrybucji na liście w punkcie dystrybucji ściągania można przypisać priorytet:  

-   Każdemu źródłowemu punktowi dystrybucji można przypisać inny priorytet; można też przypisać jeden priorytet wielu takim punktom.  

-   Priorytet określa kolejność, w jakiej ściągający punkt dystrybucji będzie żądał zawartości od danego źródłowego punktu dystrybucji.  

-   Ściągające punkty dystrybucji kontaktują się w pierwszej kolejności ze źródłowym punktem dystrybucji o najniższej wartości priorytetu.  Jeśli na liście znajduje się wiele źródłowych punktów dystrybucji o takim samym priorytecie, punkt dystrybucji ściągania w sposób niejednoznaczny wybierze jeden z nich.  

-   Gdy zawartość nie będzie dostępna w wybranym źródle, punkt dystrybucji ściągania podejmie próbę pobrania zawartości z innego punktu dystrybucji o takim samym priorytecie.  

-   Jeśli zawartość nie będzie dostępna w żadnym z punktów dystrybucji o danym priorytecie, punkt dystrybucji ściągania będzie podejmować próby pobrania zawartości z punktu dystrybucji z priorytetem o wyższej wartości do momentu zlokalizowania zawartości lub uśpienia punktu dystrybucji ściągania na 30 minut przed ponownym rozpoczęciem procesu.  

Podczas pobierania zawartości ze źródłowego punktu dystrybucji punkt dystrybucji ściągania będzie traktowany jako klient w kolumnie **Klienci, do których uzyskano dostęp (unikatowi)** raportu **Podsumowanie użycia punktu dystrybucji** .  

 Punkt dystrybucji ściągania używa domyślnie swojego **konta komputera** do przesłania zawartości ze źródłowego punktu dystrybucji. Jeśli jednak przesyła punktu dystrybucji zawartość ze źródłowego punktu dystrybucji w lesie zdalnym, ściągający punkt dystrybucji zawsze używa konta dostępu do sieci. Ten proces wymaga, czy na komputerze jest zainstalowany klient programu Configuration Manager i że konto dostępu do sieci jest skonfigurowana do użycia i ma dostęp do źródłowego punktu dystrybucji.  

## <a name="about-content-transfers"></a>Informacje o przesyłaniu zawartości  
 Aby zarządzać transferem zawartości, użyj ściągające punkty dystrybucji **CCMFramework** składnika oprogramowania klienckiego programu Configuration Manager.  

-   Ta struktura jest instalowana przez **plik Pulldp.msi** podczas konfigurowania punktu dystrybucji do punktu dystrybucji. Struktura nie wymaga klienta programu Configuration Manager.  

-   Aby umożliwić działanie ściągającego punktu dystrybucji po jego zainstalowaniu na komputerze punktu dystrybucji musi być dostępna usługa CCMExec.  

-   Zawartość będzie przesyłana do punktu dystrybucji ściągania przy użyciu **usługi inteligentnego transferu w tle (BITS)** , a działanie punktu dystrybucji ściągania będzie rejestrowane na komputerze punktu dystrybucji w plikach **datatransferservice.log** oraz **pulldp.log** .  

## <a name="see-also"></a>Zobacz także  
 [Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   

