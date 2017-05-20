---
title: "Tworzenie i stosowanie planów zasilania | Dokumentacja firmy Microsoft"
description: "Utwórz i Zastosuj planów zasilania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 738eddaa-52e2-467f-b453-821ef2884d47
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: de81da31b524cebe8e820766a64ecc5fdb7e4771
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-and-apply-power-plans-in-system-center-configuration-manager"></a>Sposób tworzenia i stosowania planów zasilania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarządzanie energią w programie System Center Configuration Manager umożliwia do zastosowania planów zasilania, które są dostarczane z programem Configuration Manager do kolekcji komputerów w hierarchii, lub do tworzenia własnych niestandardowych planów zasilania. Procedura przedstawiona w tym temacie opisuje stosowanie wbudowanych lub niestandardowych planów zasilania dla komputerów.  

> [!IMPORTANT]  
>  Planów zasilania programu Configuration Manager można zastosować tylko do kolekcji urządzeń.  

 Jeśli komputer należy do wielu kolekcji, w których są stosowane różne plany zasilania, zostaną wykonane następujące akcje:  

-   Plan zasilania: Jeśli wiele wartości dla ustawień zasilania są stosowane do komputera, najmniej restrykcyjnego wartość jest używana.  

-   Godzina wznowienia: Jeśli wiele razy wznowienia są stosowane do komputera stacjonarnego, używana jest najbliższe północ czasu.  

 Użyj raportu **Komputery z wieloma planami zasilania** , aby wyświetlić wszystkie komputery z zastosowanymi wieloma planami zasilania. Ułatwia to wykrycie komputerów z konfliktami dotyczącymi zasilania. Aby uzyskać więcej informacji o raportach zarządzania energią, zobacz [monitora i planu na potrzeby zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  Ustawienia zasilania skonfigurowane przy użyciu zasad grupy systemu Windows zastępują ustawienia skonfigurowane przez Menedżera konfiguracji zarządzania energią.  

 Użyj poniższej procedury do tworzenia i stosowania plan zasilania programu Configuration Manager.  

### <a name="to-create-and-apply-a-power-plan"></a>Tworzenie i stosowanie planu zasilania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.  

3.  Na liście **Kolekcje urządzeń** kliknij kolekcję, dla której chcesz zastosować ustawienia zarządzania energią, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

4.  W **zarządzania energią** na karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, wybierz opcję **określa ustawienia zarządzania energią dla tej kolekcji**.  

    > [!NOTE]  
    >  Możesz również kliknąć polecenie **Przeglądaj** , a następnie skopiować ustawienia zarządzania energią z wybranej kolekcji do bieżącej kolekcji.  

5.  W polach **Początek** i **Koniec** podaj godzinę rozpoczęcia i zakończenia godzin szczytu (lub pracy).  

6.  Włącz opcję **Czas wzbudzania (komputery stacjonarne)** , aby określić godzinę wybudzenia komputera ze stanu uśpienia lub hibernacji w celu zainstalowania zaplanowanych aktualizacji albo wykonania instalacji oprogramowania.  

    > [!IMPORTANT]  
    >  Funkcja zarządzania energią używa wewnętrznej funkcji czasu wzbudzania systemu Windows do wybudzania komputerów ze stanu uśpienia lub hibernacji. Ustawienia czasu wzbudzania nie są stosowane dla komputerów przenośnych w celu zapobieżenia wybudzaniu komputera przenośnego, gdy nie jest podłączony do zasilania sieciowego. Dokładny czas wybudzenia jest określany losowo — komputery będą wybudzane w ciągu godzinnego okresu rozpoczynającego się o podanej godzinie.  

7.  Jeśli chcesz skonfigurować niestandardowy plan zasilania dla godzin szczytu (lub pracy), wybierz pozycję **Dostosowany w szczycie (ConfigMgr)** z listy rozwijanej **Plan w szczycie** , a następnie kliknij polecenie **Edytuj**. Jeśli chcesz skonfigurować plan zasilania dla okresu poza godzinami szczytu (lub pracy), wybierz pozycję **Dostosowany poza szczytem (ConfigMgr)** z listy rozwijanej **Plan poza szczytem** , a następnie kliknij polecenie **Edytuj**.  

    > [!NOTE]  
    >  Podczas stosowania planów zasilania dla kolekcji komputerów możesz użyć raportu **Aktywność komputera** , aby określić harmonogramy do użycia w szczycie i poza szczytem. Aby uzyskać więcej informacji, zobacz [monitora i planu na potrzeby zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

     Możesz również wybrać spośród wbudowanych planów zasilania — **Zrównoważony (ConfigMgr)**, **Wysoka wydajność (ConfigMgr)** i **Oszczędzanie energii (ConfigMgr)**— a następnie kliknąć polecenie **Wyświetl** , aby wyświetlić właściwości każdego planu zasilania.  

    > [!NOTE]  
    >  Nie możesz zmodyfikować wbudowanych planów zasilania.  

8.  W *< Nazwa planu zasilania\>***właściwości** okna dialogowego Skonfiguruj następujące ustawienia:  

    -   **Nazwa:** Określ nazwę dla tego planu zasilania lub użyj wartością domyślną dostarczony.  

    -   **Opis:**  Określ opis dla tego planu zasilania lub użyj wartością domyślną dostarczony.  

    -   **Określ właściwości tego planu zasilania:** Skonfiguruj właściwości planu zasilania. Aby wyłączyć właściwość, wyczyść jej pole wyboru. Aby uzyskać informacje na temat dostępnych ustawień, zobacz [Available power management plan settings](#BKMK_Plans) w tym temacie.  

        > [!IMPORTANT]  
        >  Włączone ustawienia są stosowane dla komputerów po zastosowaniu planu zasilania. Wyczyszczenie pola wyboru ustawienia zasilania nie powoduje zmiany wartości na komputerze klienckim po zastosowaniu planu zasilania. Wyczyszczenie pola wyboru nie przywraca poprzedniej wartości ustawienia zasilania (tzn. wartości sprzed zastosowania planu zasilania).  

9. Kliknij przycisk **OK** zamknąć *< Nazwa planu zasilania\>***właściwości** okno dialogowe.  

10. Kliknij przycisk **OK** zamknąć *< nazwa kolekcji\>***ustawienia** okno dialogowe i zastosować planu zasilania.  

##  <a name="BKMK_Plans"></a> Available power management plan settings  
 Poniższa tabela zawiera listę ustawień zarządzania energią dostępne w programie Configuration Manager. Możesz skonfigurować oddzielne ustawienia dla czasu, w którym komputer jest podłączony do zasilania sieciowego, i dla czasu, w którym jest zasilany z baterii. W zależności od wersji systemu Windows niektóre ustawienia mogą nie być konfigurowalne.  

> [!NOTE]  
>  Ustawienia zasilania, które nie zostaną skonfigurowane, pozostaną bez zmian na komputerach klienckich.  

|Nazwa|Opis|  
|----------|-----------------|  
|**Wyłącz ekran po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed wyłączeniem ekranu. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma wyłączać ekranu.|  
|**Uśpij po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed uśpieniem komputera. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma usypiać komputera.|  
|**Wymagaj hasła przy wznawianiu**|A **tak** lub **nr** wartość określa, czy hasło jest wymagane w celu odblokowania komputera, gdy wejdzie ona wznawiania ze stanu uśpienia.|  
|**Akcja przycisku zasilania**|Określa akcję, która jest wykonywana po naciśnięciu przycisku zasilania komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Przycisk zasilania w menu Start**|Określa akcję wykonywaną po kliknięciu przycisku zasilania w menu **Start** komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Akcja przycisku uśpienia**|Określa akcję wykonywaną po naciśnięciu przycisku **Uśpij** komputera. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Akcja dla zamknięcia pokrywy**|Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Wyłącz dysk twardy po (minuty)**|Określa czas braku aktywności dysku twardego komputera (w minutach) przed jego wyłączeniem. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma wyłączać dysku twardego komputera.|  
|**Hibernacja po (minuty)**|Określa czas braku aktywności komputera (w minutach) przed jego hibernacją. Określ wartość **0** , jeśli funkcja zarządzania energią nie ma hibernować komputera.|  
|**Akcja dla niskiego poziomu energii baterii**|Określa akcję wykonywaną, gdy poziom baterii komputera osiągnie określony poziom powiadomienia o niskim poziomie baterii. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości **nic nie rób**, **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Akcja dla krytycznego poziomu energii baterii**|Określa akcję wykonywaną, gdy poziom baterii komputera osiągnie określony poziom powiadomienia o krytycznym poziomie baterii. Określa akcję wykonywaną po zamknięciu pokrywy komputera przenośnego przez użytkownika. Możliwe wartości to **uśpienia**, **Hibernacja**, i **Zamknij**.|  
|**Zezwalaj na stan uśpienia hybrydowego**|Wybieranie **na** lub **poza** wartość określa, czy system Windows do trybu uśpienia, którego można użyć, aby przywrócić stan komputera w przypadku utraty zasilania podczas została wprowadzona uśpienia, zapisuje plik hibernacji.<br /><br /> Funkcja uśpienia hybrydowego jest przeznaczona dla komputerów stacjonarnych i domyślnie nie jest włączona na komputerach przenośnych. Na komputerach z systemem Windows 7 włączenie funkcji uśpienia hybrydowego powoduje wyłączenie funkcji hibernacji.|  
|**Zezwalaj na stan gotowości podczas akcji usypiania**|Wybieranie **na** lub **poza** wartość włącza ten komputer w stan wstrzymania, w którym nadal pobiera niektórych energii, ale umożliwia szybsze wznawiania pracy komputera. Jeśli to ustawienie ma wartość **Wyłączone**, komputer można tylko hibernować lub wyłączyć.|  
|**Wymagana bezczynność do uśpienia (%)**|Określa wartość procentową czasu bezczynności procesora komputera wymaganą do uśpienia komputera. Na komputerach z systemem Windows 7, ta wartość jest zawsze równa **0**.|  
|**Włącz zegar wzbudzania systemu Windows dla komputerów stacjonarnych**|Wybieranie **włączyć** lub **wyłączyć** wartości można włączyć wbudowanych czasomierza systemu Windows do użycia przez zarządzanie energią wznowienie pracy komputera stacjonarnego. Gdy komputer stacjonarny jest wybudzany za pomocą czasomierza systemu Windows, domyślnie działa przez 10 minut, aby umożliwić komputerowi zainstalowanie wszelkich aktualizacji lub odebranie zasad.<br /><br /> Czasomierze wybudzania nie są obsługiwane na komputerach przenośnych w celu zapobieżenia wybudzaniu komputera przenośnego, gdy nie jest podłączony do zasilania sieciowego.|  

