---
title: Monitorowanie profili poczty E-mail, sieci Wi-Fi i sieci VPN
titleSuffix: Configuration Manager
description: Informacje o sposobie monitorowania stanu zgodności poczty e-mail, sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e2315b8b-98bc-40e1-8ef9-bfb5e69ab109
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 47b5bb12a89143a0c7e6d16a3252948b955b8ff3
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="monitor-email-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Monitorowanie profili poczty E-mail, sieci Wi-Fi i sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po wdrożeniu System Center Configuration Manager w wiadomości E-mail, sieci Wi-Fi lub profilów sieci VPN dla użytkowników w hierarchii, można użyć poniższych procedur do monitorowania stanu zgodności profilu:  

-   [Jak wyświetlać wyniki zgodności w konsoli programu Configuration Manager](#BKMK_console)  

-   [Jak wyświetlać wyniki zgodności przy użyciu raportów](#BKMK_Reports)  

##  <a name="BKMK_console"></a> Jak wyświetlać wyniki zgodności w konsoli programu Configuration Manager  
 Ta procedura umożliwia wyświetlenie szczegółowych informacji o zgodności wdrożonych profili w konsoli programu System Center Configuration Manager.  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Aby wyświetlić wyniki zgodności w konsoli programu Configuration Manager  

1.  W konsoli programu System Center Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij przycisk **Wdrożenia**.  

3.  W **wdrożeń** listy, wybierz wdrożenie profilu, dla którego chcesz przejrzeć informacje o zgodności.  

4.  Możesz przejrzeć podsumowanie informacji o zgodności wdrożenia profilu na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie profilu, a następnie na **Home** karcie **wdrożenia** kliknij przycisk **Wyświetl stan** otworzyć **stan wdrożenia** strony.  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodne:** Zawiera informacje o zgodności profilu, który jest na podstawie liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** w obszarze roboczym **Zasoby i zgodność** zawierającym wszystkich użytkowników, którzy są zgodni z tym profilem. **Szczegóły zasobu** okienko przedstawia użytkowników, którzy są zgodni z danym profilem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić informacje dodatkowe.  

        > [!IMPORTANT]  
        >  Profil nie jest oceniany, jeśli nie dotyczy urządzenia klienckiego; Jednakże jest zwracany jako zgodny.  

    -   **Błąd:** Wyświetla listę wszystkich błędów dla wybranego profilu wdrożenia jest na podstawie liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** zawierającego wszystkich użytkowników, którzy wygenerowali błąd w tym profilu. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić informacje dodatkowe o danym problemie.  

    -   **Niezgodne:** Wyświetla listę wszystkich niezgodnych reguł w profilu, który jest na podstawie liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** zawierającego wszystkich użytkowników, którzy nie są zgodni z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji o danym problemie.  

    -   **Nieznany:** Wyświetla listę wszystkich użytkowników, którzy nie zgłosili zgodności dla wybranego profilu wdrożenia wraz z bieżącym stanem klienta urządzeń.  

5.  Na **stan wdrożenia** strony, można przejrzeć szczegółowe informacje o zgodności wdrożonego profilu. W węźle **Wdrożenia** jest tworzony węzeł tymczasowy, który ułatwia szybkie znalezienie tych informacji ponownie.  

##  <a name="BKMK_Reports"></a> Jak wyświetlać wyniki zgodności przy użyciu raportów  
 Ustawienia zgodności, które dotyczą profili w programie System Center Configuration Manager, obejmują także szereg wbudowanych raportów umożliwiających monitorowanie informacji o profilach. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów **Filtr urządzenia** i **Filtr użytkownika** w raportach ustawień zgodności należy użyć symbolu wieloznacznego (%).  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie System Center Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  
