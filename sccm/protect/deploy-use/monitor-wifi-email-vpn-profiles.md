---
title: Monitorowanie profili poczty E-mail, sieci Wi-Fi i sieci VPN | Dokumentacja firmy Microsoft
description: "Informacje o sposobie monitorowania stanu zgodności poczty e-mail, sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2315b8b-98bc-40e1-8ef9-bfb5e69ab109
caps.latest.revision: 4
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 73d941633d270cf9628f8be14e1e56f3c78624b6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="monitor-email-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Monitorowanie profili poczty E-mail, sieci Wi-Fi i sieci VPN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po wdrożeniu System Center Configuration Manager w wiadomości E-mail, sieci Wi-Fi lub profile sieci VPN dla użytkowników w hierarchii, można użyć poniższych procedur do monitorowania stanu zgodności profilu:  

-   [Jak wyświetlać wyniki zgodności w konsoli programu Configuration Manager](#BKMK_console)  

-   [Jak wyświetlać wyniki zgodności przy użyciu raportów](#BKMK_Reports)  

##  <a name="BKMK_console"></a> Jak wyświetlać wyniki zgodności w konsoli programu Configuration Manager  
 Użyj tej procedury, aby wyświetlić szczegółowe informacje o zgodności wdrożonych profili w konsoli programu System Center Configuration Manager.  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Aby wyświetlić wyniki zgodności w konsoli programu Configuration Manager  

1.  W konsoli programu System Center Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij przycisk **Wdrożenia**.  

3.  W **wdrożeń** , wybierz wdrożenie profilu, dla którego chcesz przejrzeć informacje o zgodności.  

4.  Można przejrzeć podsumowanie informacji o zgodności wdrożenia profilu na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie profilu, a następnie na **Home** karcie w **wdrożenia** , kliknij przycisk **Wyświetl stan** otworzyć **stan wdrożenia** strony.  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodne:** Zawiera informacje o zgodności profilu, która jest oparta na liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** w obszarze roboczym **Zasoby i zgodność** zawierającym wszystkich użytkowników, którzy są zgodni z tym profilem. **Szczegóły zasobu** okienko Wyświetla użytkowników, którzy są zgodni z danym profilem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić informacje dodatkowe.  

        > [!IMPORTANT]  
        >  Profil nie jest oceniany, jeśli nie dotyczy urządzenia klienckiego; Jednakże jest zwracany jako zgodny.  

    -   **Błąd:** Wyświetla listę wszystkich błędów dla wdrożenia wybranego profilu, który jest oparty na liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** zawierającego wszystkich użytkowników, którzy wygenerowali błąd w tym profilu. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić informacje dodatkowe o danym problemie.  

    -   **Niezgodne:** Wyświetla listę wszystkich niezgodnych zasad w profilu, który jest oparty na liczby wykorzystywanych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** zawierającego wszystkich użytkowników, którzy nie są zgodni z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji o danym problemie.  

    -   **Nieznany:** Wyświetla listę wszystkich użytkowników, którzy nie zgłosili zgodności dla wybranego profilu wdrożenia wraz z bieżącym stanem klienta urządzeń.  

5.  Na **stan wdrożenia** strony, można przejrzeć szczegółowe informacje o zgodności wdrożonego profilu. W węźle **Wdrożenia** jest tworzony węzeł tymczasowy, który ułatwia szybkie znalezienie tych informacji ponownie.  

##  <a name="BKMK_Reports"></a> Jak wyświetlać wyniki zgodności przy użyciu raportów  
 Ustawienia zgodności, które dotyczą profili w programie System Center Configuration Manager, zawiera także szereg wbudowanych raportów umożliwiających monitorowanie informacji o profilach. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów **Filtr urządzenia** i **Filtr użytkownika** w raportach ustawień zgodności należy użyć symbolu wieloznacznego (%).  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie System Center Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

