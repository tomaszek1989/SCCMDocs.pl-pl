---
title: "Tworzenie i stosowanie planów zasilania"
titleSuffix: Configuration Manager
description: "Tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 738eddaa-52e2-467f-b453-821ef2884d47
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: ec32a0b1591fffe77ace91f478e03302f429c957
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-and-apply-power-plans-in-system-center-configuration-manager"></a>Tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie energią w programie System Center Configuration Manager umożliwia stosowanie planów zasilania, które są dostarczane z programem Configuration Manager do kolekcji komputerów w hierarchii lub utworzyć własne niestandardowe plany zasilania. Procedura przedstawiona w tym temacie opisuje stosowanie wbudowanych lub niestandardowych planów zasilania dla komputerów.  

> [!IMPORTANT]  
>  Do kolekcji urządzeń można zastosować tylko plany zasilania programu Configuration Manager.  

 Jeśli komputer należy do wielu kolekcji, w których są stosowane różne plany zasilania, zostaną wykonane następujące akcje:  

-   Plan zasilania: Jeśli wiele wartości dla ustawień zasilania są stosowane do komputera, jest używana wartość najmniej restrykcyjna.  

-   Godzina wznowienia: Jeśli na komputerze zastosowano wiele godzin wznowienia, zostanie użyta godzina najbliższa północy.  

 Użyj raportu **Komputery z wieloma planami zasilania** , aby wyświetlić wszystkie komputery z zastosowanymi wieloma planami zasilania. Ułatwia to wykrycie komputerów z konfliktami dotyczącymi zasilania. Aby uzyskać więcej informacji o raportach dotyczących zarządzania energią, zobacz [jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  Ustawienia zasilania skonfigurowane przy użyciu zasad grupy systemu Windows przesłaniają ustawienia skonfigurowane przez zarządzania energią w programie Configuration Manager.  

 Użyj poniższej procedury, aby utworzyć i zastosować plan zasilania programu Configuration Manager.  

### <a name="to-create-and-apply-a-power-plan"></a>Tworzenie i stosowanie planu zasilania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.  

3.  Na liście **Kolekcje urządzeń** kliknij kolekcję, dla której chcesz zastosować ustawienia zarządzania energią, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

4.  W **zarządzania energią** karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, wybierz opcję **Określ ustawienia zarządzania zasilaniem dla tej kolekcji**.  

    > [!NOTE]  
    >  Możesz również kliknąć polecenie **Przeglądaj** , a następnie skopiować ustawienia zarządzania energią z wybranej kolekcji do bieżącej kolekcji.  

5.  W polach **Początek** i **Koniec** podaj godzinę rozpoczęcia i zakończenia godzin szczytu (lub pracy).  

6.  Włącz opcję **Czas wzbudzania (komputery stacjonarne)** , aby określić godzinę wybudzenia komputera ze stanu uśpienia lub hibernacji w celu zainstalowania zaplanowanych aktualizacji albo wykonania instalacji oprogramowania.  

    > [!IMPORTANT]  
    >  Funkcja zarządzania energią używa wewnętrznej funkcji czasu wzbudzania systemu Windows do wybudzania komputerów ze stanu uśpienia lub hibernacji. Ustawienia czasu wzbudzania nie są stosowane dla komputerów przenośnych w celu zapobieżenia wybudzaniu komputera przenośnego, gdy nie jest podłączony do zasilania sieciowego. Dokładny czas wybudzenia jest określany losowo — komputery będą wybudzane w ciągu godzinnego okresu rozpoczynającego się o podanej godzinie.  

7.  Jeśli chcesz skonfigurować niestandardowy plan zasilania dla godzin szczytu (lub pracy), wybierz pozycję **Dostosowany w szczycie (ConfigMgr)** z listy rozwijanej **Plan w szczycie** , a następnie kliknij polecenie **Edytuj**. Jeśli chcesz skonfigurować plan zasilania dla okresu poza godzinami szczytu (lub pracy), wybierz pozycję **Dostosowany poza szczytem (ConfigMgr)** z listy rozwijanej **Plan poza szczytem** , a następnie kliknij polecenie **Edytuj**.  

    > [!NOTE]  
    >  Podczas stosowania planów zasilania dla kolekcji komputerów możesz użyć raportu **Aktywność komputera** , aby określić harmonogramy do użycia w szczycie i poza szczytem. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

     Możesz również wybrać spośród wbudowanych planów zasilania — **Zrównoważony (ConfigMgr)**, **Wysoka wydajność (ConfigMgr)** i **Oszczędzanie energii (ConfigMgr)**— a następnie kliknąć polecenie **Wyświetl** , aby wyświetlić właściwości każdego planu zasilania.  

    > [!NOTE]  
    >  Nie możesz zmodyfikować wbudowanych planów zasilania.  

8.  W *< Nazwa planu zasilania\>***właściwości** okna dialogowego Skonfiguruj następujące ustawienia:  

    -   **Nazwa:** Określ nazwę dla tego planu zasilania lub użyj podanej wartości domyślnej.  

    -   **Opis:**  Określ opis dla tego planu zasilania lub użyj podanej wartości domyślnej.  

    -   **Określ właściwości tego planu zasilania:** Skonfiguruj właściwości planu zasilania. Aby wyłączyć właściwość, wyczyść jej pole wyboru. Aby uzyskać informacje na temat dostępnych ustawień, zobacz [Available power management plan settings](#BKMK_Plans) w tym temacie.  

        > [!IMPORTANT]  
        >  Włączone ustawienia są stosowane dla komputerów po zastosowaniu planu zasilania. Wyczyszczenie pola wyboru ustawienia zasilania nie powoduje zmiany wartości na komputerze klienckim po zastosowaniu planu zasilania. Wyczyszczenie pola wyboru nie przywraca poprzedniej wartości ustawienia zasilania (tzn. wartości sprzed zastosowania planu zasilania).  

9. Kliknij przycisk **OK** zamknąć *< Nazwa planu zasilania\>***właściwości** okno dialogowe.  

10. Kliknij przycisk **OK** zamknąć *< nazwa kolekcji\>***ustawienia** okno dialogowe i zastosować plan zasilania.  

##  <a name="BKMK_Plans"></a> Available power management plan settings  
 W poniższej tabeli wymieniono ustawienia zarządzania energią dostępne w programie Configuration Manager. Możesz skonfigurować oddzielne ustawienia dla czasu, w którym komputer jest podłączony do zasilania sieciowego, i dla czasu, w którym jest zasilany z baterii. W zależności od wersji systemu Windows niektóre ustawienia mogą nie być konfigurowalne.  

> [!NOTE]  
>  Ustawienia zasilania, które nie zostaną skonfigurowane, pozostaną bez zmian na komputerach klienckich.  

|Nazwa|Opis|  
|----------|-----------------|  
|**Wyłącz ekran po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed wyłączeniem ekranu. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma wyłączać ekranu.|  
|**Uśpij po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed uśpieniem komputera. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma usypiać komputera.|  
|**Wymagaj hasła przy wznawianiu**|A **tak** lub **nr** wartość określa, czy hasło jest wymagane do odblokowania komputera po jego wybudzeniu ze stanu uśpienia.|  
|**Akcja przycisku zasilania**|Określa akcję, która jest wykonywana po naciśnięciu przycisku zasilania komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Przycisk zasilania w menu Start**|Określa akcję wykonywaną po kliknięciu przycisku zasilania w menu **Start** komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Akcja przycisku uśpienia**|Określa akcję wykonywaną po naciśnięciu przycisku **Uśpij** komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Akcja dla zamknięcia pokrywy**|Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Wyłącz dysk twardy po (minuty)**|Określa czas braku aktywności dysku twardego komputera (w minutach) przed jego wyłączeniem. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma wyłączać dysku twardego komputera.|  
|**Hibernacja po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed jego hibernacją. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma hibernować komputera.|  
|**Akcja dla niskiego poziomu energii baterii**|Określa akcję wykonywaną, gdy poziom baterii komputera osiągnie określony poziom powiadomienia o niskim poziomie baterii. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Akcja dla krytycznego poziomu energii baterii**|Określa akcję wykonywaną, gdy poziom baterii komputera osiągnie określony poziom powiadomienia o krytycznym poziomie baterii. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **uśpienia**, **hibernacji**, i **zamknąć**.|  
|**Zezwalaj na stan uśpienia hybrydowego**|Wybieranie **na** lub **poza** wartość określa, czy system Windows zapisuje plik hibernacji, gdy przejście w tryb uśpienia, którego można użyć w celu przywrócenia stanu komputera w przypadku utraty zasilania, gdy został wprowadzony w stan uśpienia.<br /><br /> Funkcja uśpienia hybrydowego jest przeznaczona dla komputerów stacjonarnych i domyślnie nie jest włączona na komputerach przenośnych. Na komputerach z systemem Windows 7 włączenie funkcji uśpienia hybrydowego powoduje wyłączenie funkcji hibernacji.|  
|**Zezwalaj na stan gotowości podczas akcji usypiania**|Wybieranie **na** lub **poza** wartości umożliwiająca przejście komputera w stan wstrzymania, w którym nadal pobiera nieco energii, ale umożliwia szybsze wybudzenie. Jeśli to ustawienie ma wartość **Wyłączone**, komputer można tylko hibernować lub wyłączyć.|  
|**Wymagana bezczynność do uśpienia (%)**|Określa wartość procentową czasu bezczynności procesora komputera wymaganą do uśpienia komputera. Na komputerach z systemem Windows 7 ta wartość jest zawsze równa **0**.|  
|**Włącz zegar wzbudzania systemu Windows dla komputerów stacjonarnych**|Wybieranie **włączyć** lub **wyłączyć** wartości można włączyć wbudowany czasomierz systemu Windows na potrzeby zarządzania energią wybudzenia komputera stacjonarnego. Gdy komputer stacjonarny jest wybudzany za pomocą czasomierza systemu Windows, domyślnie działa przez 10 minut, aby umożliwić komputerowi zainstalowanie wszelkich aktualizacji lub odebranie zasad.<br /><br /> Czasomierze wybudzania nie są obsługiwane na komputerach przenośnych w celu zapobieżenia wybudzaniu komputera przenośnego, gdy nie jest podłączony do zasilania sieciowego.|  
