---
title: "Uaktualnianie klientów | Dokumentacja firmy Microsoft"
description: "Uaktualnij klientów na komputerach z systemem Windows w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
caps.latest.revision: "11"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 319fbbf8ef70cb9b8a055b610828d1a2503c4689
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-upgrade-clients-for-windows-computers-in-system-center-configuration-manager"></a>Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można uaktualnić klienta na komputerach z systemem Windows przy użyciu metody instalacji klienta lub funkcje uaktualnienia klienta w programie Configuration Manager. Następujące metody instalacji klientów to prawidłowe metody uaktualniania oprogramowania klienta na komputerach z systemem Windows:  

-   Instalacja zasad grupy  

-   Instalacja skryptu logowania  

-   Instalacja ręczna  

-   Instalacja uaktualnienia  

 Jeśli interesuje Cię do uaktualniania klienta przy użyciu metody instalacji klienta, więcej informacji na temat korzystania z tych metod w [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).

 Począwszy od wersji 1610, można wykluczyć z uaktualniany, określając grupę wykluczeń klientów. Aby uzyskać więcej informacji, zobacz [jak wykluczyć uaktualnianie klientów komputerów z systemem Windows](exclude-clients-windows.md).  


> [!TIP]  
>  Jeśli uaktualniasz infrastrukturę serwera z poprzedniej wersji programu Configuration Manager \(takiej jak Configuration Manager 2007 lub System Center 2012 Configuration Manager\), zaleca się wykonanie uaktualnień serwera, łącznie z zainstalowaniem wszystkich bieżących aktualizacji gałęzi przed uaktualnieniem klientów programu Configuration Manager.   Najnowsza aktualizacja bieżącej gałęzi zawiera najnowszą wersję klienta, dlatego najlepszym rozwiązaniem jest uaktualnienie klientów po zainstalowaniu wszystkich aktualizacji programu Configuration Manager, których chcesz użyć.

> [!NOTE]
> Jeśli planujesz ponowne przypisanie lokacji dla klientów podczas uaktualniania, możesz określić nowej lokacji za pomocą właściwości client.msi SMSSITECODE. Jeśli używasz AUTOMATYCZNIE SMSSITECODE, należy także określić SITEREASSIGN = TRUE, aby umożliwić ponowne przypisanie lokacji automatyczne występuje podczas uaktualniania. Aby uzyskać więcej informacji, zobacz [SMSSITECODE](../../deploy/about-client-installation-properties.md#smssitecode).

## <a name="use-automatic-client-upgrade"></a>Użycie automatycznego uaktualnienia klienta  
 Istnieje również możliwość skonfigurowania programu Configuration Manager, aby automatycznie uaktualniał oprogramowanie klienta do najnowszej wersji klienta programu Configuration Manager, gdy program Configuration Manager identyfikuje klienta, który jest przypisany do hierarchii programu Configuration Manager jest niższa niż wersja programu używana w hierarchii. Taki scenariusz obejmuje uaktualnienie klienta do najnowszej wersji, podczas próby jego przypisania do lokacji programu Configuration Manager.  

 Klient może zostać automatycznie uaktualniony w następujących sytuacjach:  

-   Wersja klienta jest starsza niż wersja używana w hierarchii.  

-   Klient w centralnej lokacji administracyjnej ma zainstalowany pakiet językowy, a istniejący klient go nie ma.  

-   Wymaganiem wstępnym klienta w hierarchii jest inna wersja niż zainstalowana na kliencie.  

-   Co najmniej jeden z plików instalacyjnych klienta jest w innej wersji.  

> [!NOTE]  
>  Można uruchomić raport **klientów liczba programu Configuration Manager według wersji klienta** w folderze raportu **lokacja — informacje o kliencie** można określić różne wersje klienta programu Configuration Manager w hierarchii.  

 Configuration Manager tworzy pakiet uaktualnienia domyślnie, który jest automatycznie przesyłany do wszystkich punktów dystrybucji w hierarchii. Wprowadzenie zmian do pakietu klienta w centralnej lokacji administracyjnej, na przykład dodać pakiet językowy klienta programu Configuration Manager automatycznie aktualizuje pakiet i przesłanie go do wszystkich punktów dystrybucji w hierarchii. Jeśli automatyczne uaktualnianie klienta jest włączone, każdy klient automatycznie zainstaluje nowy pakiet językowy klienta.  

> [!NOTE]  
>  Menedżer konfiguracji nie wysyła automatycznie uaktualnienie klienta pakietu do punktów dystrybucji w chmurze programu Configuration Manager.  

 Zaleca się włączenie automatycznych uaktualnień klienta w hierarchii. Dzięki temu klienci zaktualizowany o koszty administracyjne do minimum.  

 Poniższa procedura pozwala skonfigurować automatyczne uaktualnienia klienta. Automatyczne uaktualnienia klienta należy skonfigurować w centralnej lokacji administracyjnej, a utworzona konfiguracja dotyczy wszystkich klientów w hierarchii.  

### <a name="to-configure-automatic-client-upgrades"></a>Aby skonfigurować automatyczne uaktualnienia klienta  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.  

3.  Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.  

4.  Na karcie **Uaktualnienie klienta** okna dialogowego **Właściwości ustawień hierarchii** sprawdź wersję i datę klienta produkcyjnego oraz upewnij się, że jest to wersja, której chcesz użyć do uaktualnienia komputerów z systemem Windows.  Jeśli nie jest to oczekiwana wersja klienta, konieczne może być promowanie klienta przedprodukcyjnego na produkcyjnego. Aby uzyskać więcej informacji, zobacz [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md).  

5.  Kliknij pozycję **Uaktualnij wszystkich klientów w hierarchii przy użyciu klienta produkcyjnego** i kliknij przycisk **OK** w oknie dialogowym potwierdzenia.  

6.  Jeśli nie chcesz stosować uaktualnień klienta do serwerów, kliknij przycisk **Nie uaktualniaj serwerów**.  

7.  Określ liczbę dni, w ciągu których komputery muszą uaktualnić klienta po otrzymaniu zasad klienta. Klient zostanie uaktualniony w ciągu określonej liczby dni z losowo wybranym interwałem. Takie rozwiązanie zapobiega jednoczesnemu uaktualnianiu dużej liczby komputerów klienckich.

    > [!NOTE]
    > Komputer musi działać w celu uaktualnienia klienta. Jeśli komputer nie jest uruchomiona w chwili zostało zaplanowane to zrobić, uaktualnienie nie występuje. Zamiast tego, po ponownym uruchomieniu komputera, uaktualnienie innego zaplanowano losowe raz w ciągu określonej liczby dni dozwolone. Jeśli ten problem wystąpi, po upływie liczbę dni, aby uaktualnić, uaktualnienie zostanie zaplanowane występuje losowych momencie w ciągu 24 godzin, po ponownym uruchomieniu komputera.
    >     
    > Ze względu na to zachowanie komputery, które są regularnie zamknięte po zakończeniu pracy może potrwać dłużej do uaktualnienia, niż oczekiwano, jeśli losowo zaplanowanym terminie uaktualnienia nie jest w normalnych godzinach pracy.

7. Począwszy od wersji 1610, jeśli chcesz wykluczyć klientów z Trwa uaktualnianie, kliknij przycisk **Wyklucz określone klientów z uaktualnienia** i określ kolekcję do wykluczenia.

8.  Jeśli chcesz, by pakiet instalacyjny klienta był kopiowany do punktów dystrybucji dozwolonych dla wstępnie przygotowanej zawartości, kliknij przycisk **Automatycznie dystrybuuj pakiet instalacyjny klienta do punktów dystrybucji, które aktywowano na potrzeby wstępnie przygotowanej zawartości**.  

9. Kliknij przycisk **OK** , aby zapisać ustawienia i zamknąć okno dialogowe **Właściwości ustawień hierarchii** . Klienci otrzymają te ustawienia przy kolejnym pobraniu zasad.

>[!NOTE]
>Uaktualnienia klienta honoruje oknami obsługi programu Configuration Manager, które zostały skonfigurowane.
