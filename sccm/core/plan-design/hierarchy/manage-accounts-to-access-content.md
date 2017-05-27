---
title: "Konta dostępu do zawartości w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat kont, których klientów mających dostęp do zawartości programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e592a732259147ee71d404a68982c28e5138e243
ms.openlocfilehash: 0e982d08d54af39b13f553fc531a200f921e94a6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-accounts-to-access-content-in-system-center-configuration-manager"></a>Zarządzanie kontami dostępu do zawartości w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed wdrożeniem zawartości w programie System Center Configuration Manager, należy rozważyć, jak klienci używają tej zawartości z punktów dystrybucji. W tym artykule opisano następujące konta używane w tym celu:

-   **Konto dostępu do sieci**. Używane przez klientów, połącz się z punktem dystrybucji oraz uzyskiwania dostępu do zawartości. Domyślnie klienci próbują najpierw konta komputera.

     To konto jest również używane przez punkty dystrybucji uzyskanie zawartości ze źródłowego punktu dystrybucji w lesie zdalnym.  

-   **Konto dostępu do pakietu**. Domyślnie program Configuration Manager udziela dostępu do zawartości w punkcie dystrybucji, aby wbudowane konta o nazwie **użytkowników** i **Administratorzy**. Można skonfigurować dodatkowe uprawnienia, aby ograniczyć dostęp.  

-   **Konto połączenia multiemisji**. Używany do wdrażania systemu operacyjnego.  

##  <a name="bkmk_NAA"></a>Konto dostępu do sieci  
 Komputery klienckie używają konta dostępu do sieci, gdy nie mogą użyć lokalnego konta komputera w celu uzyskania dostępu do zawartości w punktach dystrybucji. Dotyczy to na przykład komputerów i klientów grupy roboczej z niezaufanych domen. Tego konta można również używać podczas wdrażania systemu operacyjnego, jeżeli komputer instalujący system operacyjny nie ma jeszcze konta komputera w domenie.  

-   Klienci używają konta dostępu do sieci wyłącznie do uzyskiwania dostępu do zasobów w sieci.  

-   W każdej lokacji głównej można skonfigurować wiele kont jako konta dostępu do sieci.  

-   Klienci pierwszej próby uzyskania dostępu do zawartości w punkcie dystrybucji za pomocą ich *computername*$ konta. Jeśli to konto nie powiedzie się, klienci spróbuj użyć konta dostępu do sieci. Klienci będą próbować użyć konta dostępu do sieci, nawet jeśli została wcześniej niepowodzeniem.  

### <a name="permissions"></a>Uprawnienia
Przyznaj temu kontu najniższe odpowiednie uprawnienia dostępu do oprogramowania zawartości wymaganej przez klienta.  

-   Konto musi mieć **dostęp do tego komputera z sieci** bezpośrednio w punkcie dystrybucji.  

-   Utwórz konto w dowolnej domenie, która zapewni wymagany dostęp do zasobów. Konto dostępu do sieci zawsze musi zawierać nazwę domeny. To konto nie obsługuje przekazywanych zabezpieczeń. Jeżeli punkty dystrybucji znajdują się w wielu domenach, należy utworzyć konto w zaufanej domenie.  

> [!TIP]  
>  Aby uniknąć blokad konta, nie należy zmieniać hasła w istniejącym koncie dostępu do sieci. Zamiast tego utworzyć nowe konto i skonfigurować nowe konto w programie Configuration Manager. Po wystarczającą ilość czasu dla wszystkich klientów otrzymane pobranie szczegółów nowego konta należy usunąć stare konto z udostępnianych folderów sieciowych, a następnie usunąć konto.  

> [!IMPORTANT]  
>  Nie należy przyznawać temu kontu interaktywnych uprawnień do logowania się.  
>   
>  Nie należy przyznawać temu kontu uprawnienia do dołączania komputerów do domeny. Jeżeli musisz dołączyć komputery do domeny podczas sekwencji zadań, użyj konta dołączania do domeny edytora sekwencji zadań.  

### <a name="to-configure-the-network-access-account"></a>Aby skonfigurować konto dostępu do sieci  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >   **konfiguracja lokacji** >  **witryny**, a następnie wybierz lokację.  

2.  Na **ustawienia** grupy, wybierz **Konfiguruj składniki lokacji** > **dystrybucji oprogramowania**.  

3.  Wybierz **konta dostępu do sieci** kartę. Skonfiguruj co najmniej jednego konta, a następnie wybierz **OK**.  

##  <a name="bkmk_Paa"></a>Konta dostępu do pakietu  
 Konta dostępu do pakietu pozwalają ustawiać uprawnienia systemu plików NTFS w celu określenia użytkowników i grup użytkowników mogących uzyskiwać dostęp do zawartości pakietu w punktach dystrybucji. Domyślnie program Configuration Manager przypisuje dostęp tylko do ogólnej **użytkowników** i **Administratorzy** kont. Można jednak sterować dostępem dla komputerów klienckich przy użyciu dodatkowych kont systemu Windows lub grup. Urządzenia przenośne nie należy używać konta dostępu do pakietu, ponieważ te urządzenia zawsze pobierają zawartość pakietów anonimowo.  

 Domyślnie, gdy program Configuration Manager kopiuje pliki zawartości w pakiecie do punktu dystrybucji przyznaje **odczytu** dostęp do lokalnej **użytkowników** grupy i **Pełna kontrola** do lokalnej **Administratorzy** grupy. Rzeczywiste wymagane uprawnienia są uzależnione od pakietu. Klienci w grupach roboczych lub lasach niezaufanych uzyskują dostęp do zawartości pakietu przy użyciu konta dostępu do sieci. Upewnij się, że konto dostępu do sieci ma uprawnienia do pakietu przy użyciu zdefiniowanych kont dostępu do pakietu.  

 Należy użyć kont w domenie mającej dostęp do punktów dystrybucji. W przypadku utworzenia lub zmodyfikowania konta po utworzeniu pakietu należy go ponownie rozesłać. Aktualizacja pakietu nie zmienia uprawnień systemu plików NTFS w pakiecie.  

 Nie ma konieczności dodawania konta dostępu do sieci jako konta dostępu do pakietu, ponieważ członkostwo **użytkowników** ono dodane automatycznie. Ograniczenie konta dostępu do pakietu wyłącznie do konta dostępu do sieci nie uniemożliwi klientom uzyskania dostępu do pakietu.  

### <a name="to-manage-access-accounts"></a>Aby zarządzać kontami dostępu  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, określ typ zawartości, która ma zarządzać kontami dostępu i postępuj zgodnie z krokami opisanymi:  

    -   **Aplikacje**: Rozwiń węzeł **zarządzania aplikacjami**, wybierz **aplikacji**, a następnie wybierz aplikacje, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety**: Rozwiń węzeł **zarządzania aplikacjami**, wybierz **pakiety**, a następnie wybierz pakiety, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania**, wybierz **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, do których chcesz zarządzać kontami dostępu.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, wybierz **pakiety sterowników**, a następnie wybierz pakiety sterowników, do których chcesz zarządzać kontami dostępu.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, wybierz **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, do których chcesz zarządzać kontami dostępu.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, wybierz **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, do których chcesz zarządzać kontami dostępu.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, wybierz **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, do których chcesz zarządzać kontami dostępu.  

3.  Kliknij prawym przyciskiem myszy wybrany obiekt, a następnie wybierz **Zarządzaj kontami dostępu**.  

4.  W **Dodawanie konta** okna dialogowego określ typ konta, które zostanie przyznany dostęp do zawartości, a następnie określ prawa dostępu powiązane z kontem.  

    > [!NOTE]  
    >  Dodaj nazwę użytkownika dla konta, gdy Menedżer konfiguracji umożliwia znalezienie zarówno konto użytkownika lokalnego, jak i konto użytkownika domeny o tej samej nazwie, program Configuration Manager Ustawia prawa dostępu do konta użytkownika domeny.  

##  <a name="bkmk_multi"></a>Konto połączenia multiemisji  
 Konta połączenia multiemisji jest używany przez punkty dystrybucji, które są skonfigurowane do multiemisji w celu odczytywania informacji z bazy danych lokacji.  

-   Określ konto do użycia podczas konfigurowania połączenia bazy danych programu Configuration Manager do multiemisji.  

-   Domyślnie jest używane konto komputera punktu dystrybucji, ale można skonfigurować konto użytkownika zamiast tego.  

-   Konto użytkownika należy zawsze określić, gdy baza danych lokacji znajduje się w niezaufanym lesie.  

-   Konto musi mieć **odczytu** uprawnień do bazy danych lokacji.  

Jeżeli na przykład centrum danych ma sieć obwodową w lesie innym niż serwer lokacji i baza danych lokacji, tego konta można używać do odczytywania informacji o multiemisji z bazy danych lokacji.

W przypadku utworzenia tego konta, należy go utworzyć jako niskim poziomem uprawnień, lokalnego konta na komputerze z uruchomionym programem Microsoft SQL Server.  

> [!IMPORTANT]  
>  Nie należy przyznawać temu kontu interaktywnych uprawnień do logowania się.  

