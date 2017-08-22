---
title: "Konta dostępu do zawartości w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat kont, których klienci uzyskują dostęp do zawartości programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0e982d08d54af39b13f553fc531a200f921e94a6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-accounts-to-access-content-in-system-center-configuration-manager"></a>Zarządzanie kontami dostępu do zawartości w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed wdrożeniem zawartości w programie System Center Configuration Manager, należy rozważyć sposób klienci będą uzyskiwać dostęp do tej zawartości z punktów dystrybucji. W tym artykule opisano następujące konta używane w tym celu:

-   **Konto dostępu do sieci**. Używany przez klientów, aby podłączyć się do punktu dystrybucji i uzyskiwać dostęp do zawartości. Domyślnie klienci spróbuj najpierw swoich kont komputerowych.

     To konto jest również używane przez punkty dystrybucji ściągania pobierać zawartość ze źródłowego punktu dystrybucji w lesie zdalnym.  

-   **Konto dostępu do pakietu**. Domyślnie program Configuration Manager udziela dostępu do zawartości w punkcie dystrybucji, do wbudowanych kont o nazwie **użytkowników** i **Administratorzy**. Można skonfigurować dodatkowe uprawnienia, aby ograniczyć dostęp.  

-   **Konto połączenia multiemisji**. Użyć wdrożeń systemu operacyjnego.  

##  <a name="bkmk_NAA"></a>Konto dostępu do sieci  
 Komputery klienckie używają konta dostępu do sieci, gdy nie mogą użyć lokalnego konta komputera na dostęp do zawartości w punktach dystrybucji. Dotyczy to na przykład komputerów i klientów grupy roboczej z niezaufanych domen. Tego konta można również używać podczas wdrażania systemu operacyjnego, jeżeli komputer instalujący system operacyjny nie ma jeszcze konta komputera w domenie.  

-   Klienci używają konta dostępu do sieci wyłącznie do uzyskiwania dostępu do zasobów w sieci.  

-   W każdej lokacji głównej można skonfigurować wiele kont do użycia jako konto dostępu do sieci.  

-   Klienci próbują najpierw uzyskać dostępu do zawartości w punkcie dystrybucji przy użyciu ich *computername*$ konta. Jeśli to konto nie powiedzie się, klienci próbują używać konta dostępu do sieci. Klienci kontynuują próby użycia konta dostępu do sieci, nawet jeśli jego wcześniej nie powiodła się.  

### <a name="permissions"></a>Uprawnienia
Przyznaj temu kontu najniższe odpowiednie uprawnienia dostępu do oprogramowania zawartości wymaganej przez klienta.  

-   Konto musi mieć **dostęp do tego komputera z sieci** bezpośrednio w punkcie dystrybucji.  

-   Utwórz konto w dowolnej domenie, która zapewni wymagany dostęp do zasobów. Konto dostępu do sieci zawsze musi zawierać nazwę domeny. Przekazywanych zabezpieczeń nie jest obsługiwana dla tego konta. Jeżeli punkty dystrybucji znajdują się w wielu domenach, należy utworzyć konto w zaufanej domenie.  

> [!TIP]  
>  Aby uniknąć blokad konta, nie należy zmieniać hasła w istniejącym koncie dostępu do sieci. Zamiast tego utworzyć nowe konto i skonfigurować nowe konto w programie Configuration Manager. Po upłynięciu wystarczającego czasu dla wszystkich klientów na pobranie szczegółów nowego konta, Usuń stare konto z udostępnianych folderów sieciowych, a następnie usunąć konto.  

> [!IMPORTANT]  
>  Nie przyznawaj temu kontu interaktywnych uprawnień do logowania.  
>   
>  Nie należy przyznawać temu kontu uprawnienia do dołączania komputerów do domeny. Jeżeli musisz dołączyć komputery do domeny podczas sekwencji zadań, użyj konta dołączania do domeny edytora sekwencji zadań.  

### <a name="to-configure-the-network-access-account"></a>Aby skonfigurować konto dostępu do sieci  

1.  W konsoli programu Configuration Manager wybierz **administracji** >   **konfiguracja lokacji** >  **witryny**, a następnie wybierz lokację.  

2.  Na **ustawienia** grupy, wybierz **Konfiguruj składniki lokacji** > **dystrybucji oprogramowania**.  

3.  Wybierz **konta dostępu do sieci** kartę. Skonfiguruj co najmniej jednego konta, a następnie wybierz **OK**.  

##  <a name="bkmk_Paa"></a>Konta dostępu do pakietu  
 Konta dostępu do pakietu pozwalają ustawić uprawnienia systemu plików NTFS w celu określenia użytkowników i grup użytkowników, którzy mają dostęp do zawartości pakietu w punktach dystrybucji. Domyślnie program Configuration Manager przypisuje dostęp tylko do ogólnych **użytkowników** i **Administratorzy** kont. Możesz jednak kontroli dostępu dla komputerów klienckich przy użyciu dodatkowych kont systemu Windows lub grup. Urządzenia przenośne nie używają kont dostępu do pakietu, ponieważ te urządzenia zawsze pobierają zawartość pakietów anonimowo.  

 Domyślnie, gdy programu Configuration Manager skopiuje pliki zawartości pakietu do punktu dystrybucji, domyślnie przyzna **odczytu** dostęp do lokalnego **użytkowników** grupy i **Pełna kontrola** do lokalnej **Administratorzy** grupy. Rzeczywiste uprawnienia, które są wymagane są zależne od pakietu. Klienci w grupach roboczych lub lasach niezaufanych uzyskują dostęp do zawartości pakietu przy użyciu konta dostępu do sieci. Upewnij się, że konto dostępu do sieci ma uprawnienia do pakietu przy użyciu zdefiniowanych kont dostępu do pakietu.  

 Należy użyć kont w domenie mającej dostęp do punktów dystrybucji. W przypadku utworzenia lub zmodyfikowania konta po utworzeniu pakietu należy go ponownie rozesłać. Aktualizacja pakietu nie zmienia uprawnień systemu plików NTFS w pakiecie.  

 Nie trzeba dodać konto dostępu do sieci jako konta dostępu do pakietu, ponieważ członkostwo **użytkowników** ono dodane automatycznie. Ograniczenie konta dostępu do pakietu wyłącznie do konta dostępu do sieci nie uniemożliwi klientom uzyskania dostępu do pakietu.  

### <a name="to-manage-access-accounts"></a>Aby zarządzać kontami dostępu  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** roboczym ustalić typu zawartości, dla której chcesz zarządzać kontami dostępu i postępuj zgodnie z krokami opisanymi:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami**, wybierz **aplikacji**, a następnie wybierz aplikacje, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami**, wybierz **pakiety**, a następnie wybierz pakiety, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania**, wybierz **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, wybierz **pakiety sterowników**, a następnie wybierz pakiety sterowników, do których chcesz zarządzać kontami dostępu.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, wybierz **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, do których chcesz zarządzać kontami dostępu.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, wybierz **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, do których chcesz zarządzać kontami dostępu.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, wybierz **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, do których chcesz zarządzać kontami dostępu.  

3.  Kliknij prawym przyciskiem myszy wybrany obiekt, a następnie wybierz pozycję **Zarządzaj kontami dostępu**.  

4.  W **Dodaj konto** oknie dialogowym Określ typ konta, które otrzyma prawa dostępu do zawartości, a następnie określ prawa dostępu skojarzone z kontem.  

    > [!NOTE]  
    >  Gdy zostanie dodana nazwa użytkownika dla konta, a Configuration Manager znajduje się zarówno konto użytkownika lokalnego, jak i konto użytkownika domeny o tej samej nazwie, programu Configuration Manager określa prawa dostępu do konta użytkownika domeny.  

##  <a name="bkmk_multi"></a>Konto połączenia multiemisji  
 Konto połączenia multiemisji jest używany przez punkty dystrybucji, które są skonfigurowane do multiemisji w celu odczytywania informacji z bazy danych lokacji.  

-   Należy określić konto do użycia podczas konfigurowania połączenia z bazą danych programu Configuration Manager do multiemisji.  

-   Domyślnie jest używane konto komputera punktu dystrybucji, ale można skonfigurować konto użytkownika zamiast tego.  

-   Konto użytkownika należy zawsze określić, gdy baza danych lokacji znajduje się w niezaufanym lesie.  

-   Konto musi mieć **odczytu** uprawnień do bazy danych lokacji.  

Jeżeli na przykład centrum danych ma sieć obwodową w lesie innym niż serwer lokacji i baza danych lokacji, tego konta można używać do odczytywania informacji o multiemisji z bazy danych lokacji.

Jeśli tworzysz konto, należy go utworzyć jako z niskimi uprawnieniami, konta lokalnego na komputerze z uruchomionym programem Microsoft SQL Server.  

> [!IMPORTANT]  
>  Nie przyznawaj temu kontu interaktywnych uprawnień do logowania.  
