---
title: Składniki lokacji
titleSuffix: Configuration Manager
description: Dowiedz się, jak skonfigurować składniki lokacji, aby zmodyfikować zachowanie ról systemu lokacji i raportowania stanu lokacji.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: da7537ff9cda198f938eafdfc5db198e79a2cb5b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="site-components-for-system-center-configuration-manager"></a>Składniki lokacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W każdej lokacji programu System Center Configuration Manager można skonfigurować składniki lokacji, aby zmodyfikować zachowanie ról systemu lokacji i raportowania stanu lokacji. Konfiguracje składników lokacji mają zastosowanie do witryny i do każdego wystąpienia odpowiedniej roli systemu lokacji w lokacji.  

## <a name="about-site-components"></a>Składniki lokacji — informacje  
 Większość opcji dotyczących różnych składników lokacji nie wymaga wyjaśnień wyświetlony w konsoli programu Configuration Manager. Jednak następujące informacje mogą pomóc, wyjaśniają niektóre z bardziej złożonych konfiguracji lub przekierować użytkownika do dokumentów zawierających dodatkowe objaśnienia.  

### <a name="software-distribution"></a>Dystrybucja oprogramowania  

-   **Ustawienia dystrybucji zawartości:**  Można określić ustawienia umożliwiające modyfikowanie sposobu przesyłania zawartości serwera lokacji do punktów dystrybucji. Zwiększenie używanych wartości ustawień dystrybucji współbieżnej spowoduje, że podczas dystrybucji zawartości można będzie używać większej przepustowości sieci.  

-   **Konto dostępu do sieci:**  Aby uzyskać informacje dotyczące konfigurowania i korzystania z konta dostępu do sieci, zobacz [konta dostępu do sieci](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

### <a name="software-update-point"></a>Punkt aktualizacji oprogramowania  

-   Aby uzyskać informacje o opcjach konfiguracji składnika punktu aktualizacji oprogramowania, zobacz [instalacji punktu aktualizacji oprogramowania](../../../../sum/get-started/install-a-software-update-point.md).  

### <a name="management-point"></a>Punkt zarządzania  

-   **Punkty zarządzania:** Witrynę można skonfigurować do publikowania informacji o jej punktach zarządzania w usługach domenowych w usłudze Active Directory.  

     Klienci programu Configuration Manager używać punktów zarządzania do lokalizowania usług i Znajdź informacje o lokacji, takich jak członkostwo grupy granic oraz opcje wyboru certyfikatu PKI. Klienci używają również punktów zarządzania do znalezienia innych punktów zarządzania w lokacji, a także punktów dystrybucji, z którego ma zostać pobrane oprogramowanie. Punkty zarządzania również pomóc klientom przypisania lokacji i pobrania zasad klienta i przekazać informacje o kliencie.  

     Najbezpieczniejszą metodą wyszukiwania punktów zarządzania przez klientów jest publikowanie ich w usługach Active Directory Domain Services. Dlatego zazwyczaj do opublikowania w usługach Active Directory Domain Services wybiera się wszystkie działające punkty zarządzania. Następujące polecenie, aby mieć wartości true wymaga jednak tej metody lokalizowania usługi:

     - Schemat jest rozszerzony dla programu Configuration Manager.
     - Brak **System zarządzania** kontenera odpowiednie uprawnienia zabezpieczeń dla serwera lokacji do publikowania w tym kontenerze.
     - Lokacja programu Configuration Manager został skonfigurowany do publikowania w usługach domenowych w usłudze Active Directory.
     - Klienci należą do tego samego lasu usługi Active Directory, co lasem serwera lokacji.  

     Gdy klienci w intranecie, nie można użyć usług domenowych w usłudze Active Directory pod kątem wyszukiwania punktów zarządzania, należy użyć [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) publikowania zamiast tego.  

 Aby uzyskać ogólne informacje o lokalizacji usługi, zobacz [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

-   **Publikuj wybrane punkty zarządzania intranetem w systemie DNS:** Tę opcję należy określić, gdy klienci w intranecie, nie może znaleźć punkty zarządzania z usług domenowych w usłudze Active Directory. Zamiast tego użyciem rekord zasobów lokalizacji usługi DNS (SRV RR) do znalezienia punktu zarządzania w przypisanej lokacji.  

    Configuration Manager ma publikować punkty zarządzania intranetem w systemie DNS, muszą być spełnione następujące warunki:  

    -   Na serwerach DNS zainstalowano oprogramowanie BIND w wersji 8.1.2 lub nowszej.  

    -   Serwery DNS są skonfigurowane aktualizacje automatyczne i obsługują rekordy zasobów lokalizacji usługi.  

    -   W określonym pełni kwalifikowane nazwy domeny (FQDN) dla punktów zarządzania w programie Configuration Manager mają wpisy hosta (rekordy A lub AAA) w systemie DNS.  

    > [!WARNING]  
    >  Dla klientów do wyszukiwania punktów zarządzania, które są publikowane w systemie DNS należy przypisać klientów do określonej witryny (zamiast używać automatycznego przypisania lokacji). Skonfigurować tych klientów do używania kodu lokacji z sufiksem domeny swoim punktem zarządzania. Aby uzyskać więcej informacji, zobacz [lokalizowanie punktów zarządzania](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](/sccm/core/clients/deploy/assign-clients-to-a-site).  

     Jeśli klienci programu Configuration Manager nie można użyć usług domenowych w usłudze Active Directory i DNS do wyszukiwania punktów zarządzania w intranecie, używają [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins). Pierwszy punkt zarządzania jest zainstalowany w lokacji jest automatycznie publikowany w usłudze WINS podczas jego został skonfigurowany do akceptowania połączeń klienta HTTP w sieci intranet.  

### <a name="status-reporting"></a>Raportowanie stanu  

-   Te ustawienia bezpośrednio skonfigurować poziom szczegółowości, który znajduje się w raportach o stanie z lokacji i klientów.  

### <a name="email-notification"></a>Powiadomienia e-mail  

-   Określ konto i wiadomości e-mail szczegóły serwera, aby program Configuration Manager do wysyłania powiadomień e-mail dla alertów.  

### <a name="collection-membership-evaluation"></a>Ocena członkostwa w kolekcji  

-   Za pomocą tego zadania można zmienić częstotliwość oceny członkostwa w kolekcji. Ocena przyrostowa aktualizuje członkostwo kolekcji tylko nowymi i zmienionymi zasobami.  

### <a name="edit-the-site-components-at-a-site"></a>Edytuj składników lokacji w lokacji  

Aby edytować składniki lokacji, wykonaj następujące kroki:

1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** > **witryny**, a następnie wybierz lokację zawierającą składniki lokacji, które chcesz skonfigurować.  

2.  Na **Home** karcie **ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**. Następnie wybierz składnik lokacji, który chcesz skonfigurować.  

##  <a name="BKMK_ServiceMgr"></a> Używanie Menedżera usług programu Configuration Manager do zarządzania składnikami lokacji  
Menedżera usług programu Configuration Manager umożliwia kontrolowanie usług programu Configuration Manager i wyświetlić stan usługi programu Configuration Manager lub wątków roboczych (określanych zbiorczo jako składniki programu Configuration Manager). Zrozumieć następujące kwestie dotyczące składników programu Configuration Manager:  

-   Składniki można uruchomić w każdym systemie lokacji.  

-   Składnikami zarządza się taki sam sposób jak usługami w systemie Windows. Można uruchomić, zatrzymać, wstrzymać, wznowić lub składników programu Configuration Manager.  

Usługa programu Configuration Manager działa w przypadku otrzymania żądania wykonania (zazwyczaj gdy plik konfiguracji jest zapisany w skrzynce odbiorczej składnika). Jeśli masz potrzeby zidentyfikowania składnika uwzględnionego w operacji można użyć Menedżera usług programu Configuration Manager do manipulowania różnych usług i wątków. Można następnie zobaczyć wynikową zmianę zachowania programu Configuration Manager. Na przykład można zatrzymać usług programu Configuration Manager, co w chwili, aż do wyeliminowania określonej odpowiedzi. Pozwala to ustalić, która usługa powoduje dane zachowanie.  

> [!TIP]  
>  Poniższa procedura może służyć do modyfikowania działaniem składnika programu Configuration Manager.  

### <a name="use-the-configuration-manager-service-manager"></a>Użyj Menedżera usług programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie** >  **stan systemu**, a następnie kliknij przycisk **stan składnika**.  

2.  Na **Home** karcie **składnika** kliknij przycisk **Start**. Następnie wybierz **Menedżera usług programu Configuration Manager**.  

3.  Po otwarciu Menedżera usług programu Configuration Manager połącz się z lokacją, którą chcesz zarządzać.  

     Jeżeli lokacja do zarządzania nie jest wyświetlana, kliknij kolejno przyciski **Lokacja**i **Połącz**, a następnie wprowadź nazwę serwera odpowiedniej lokacji.  

4.  Rozwiń lokację i przejdź do węzła **Składniki** lub **Serwery** w zależności od lokalizacji składników, którymi chcesz zarządzać.  

5.  W prawym okienku wybierz jeden lub więcej składników. Następnie na **składnika** menu, kliknij przycisk **zapytania** Aby zaktualizować stan wybranego elementu.  

6.  Po zaktualizowaniu stanu składnika użyj jednej z czterech opcji akcji dostępnych w **składnika** menu do modyfikowania działania składnika. Po zażądaniu akcji należy wysłać do składnika kwerendę w celu wyświetlenia jego nowego stanu.  

7.  Po zakończeniu modyfikowania stanu operacyjnego składników, Zamknij Menedżera usług programu Configuration Manager.  
