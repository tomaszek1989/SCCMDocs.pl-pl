---
title: "Lokacji programu Configuration Manager składniki | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie konfigurowania składników lokacji, aby zmodyfikować zachowanie ról systemu lokacji oraz raportowania stanu lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 83550fbf0ef1f9adb0bb2c51a4f3c26a7500d352
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="site-components-for-system-center-configuration-manager"></a>Składniki programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W każdej lokacji programu System Center Configuration Manager można skonfigurować składniki lokacji, aby zmodyfikować zachowanie ról systemu lokacji oraz raportowania stanu lokacji. Konfiguracje składników lokacji mają zastosowanie do lokacji i do każdego wystąpienia odpowiednią rolę systemu lokacji w lokacji.  

## <a name="about-site-components"></a>Składniki lokacji — informacje  
 Większość opcji dla różnych składników lokacji nie wymaga wyjaśnień wyświetlony w konsoli programu Configuration Manager. Jednak następujące szczegóły pomóc objaśniono niektóre konfiguracje bardziej złożonych lub ich do dodatkowej zawartości, który objaśnia je.  

### <a name="software-distribution"></a>Dystrybucja oprogramowania  

-   **Ustawienia dystrybucji zawartości:**  Można określić ustawienia, które modyfikują, jak serwer lokacji przesyła zawartość do punktów dystrybucji. Zwiększenie używanych wartości ustawień dystrybucji współbieżnej spowoduje, że podczas dystrybucji zawartości można będzie używać większej przepustowości sieci.  

-   **Konto dostępu do sieci:**  Informacje o konfigurowaniu i używaniu konta dostępu do sieci, zobacz [konta dostępu do sieci](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

### <a name="software-update-point"></a>Punkt aktualizacji oprogramowania  

-   Aby uzyskać informacje o opcjach konfiguracji składnika punktu aktualizacji oprogramowania, zobacz [zainstalować punkt aktualizacji oprogramowania](../../../../sum/get-started/install-a-software-update-point.md).  

### <a name="management-point"></a>Punkt zarządzania  

-   **Punkty zarządzania:** Witrynę można skonfigurować do publikowania informacji o jego punktów zarządzania do usług domenowych w usłudze Active Directory.  

     Klienci programu Configuration Manager używać punktów zarządzania do lokalizowania usług i znalezienia informacji o członkostwie w grupach granic oraz opcji wyboru certyfikatu PKI lokacji. Klienci używają również punktów zarządzania w celu znalezienia innych punktów zarządzania w lokacji, a także punkty dystrybucji do pobrania oprogramowania. Punkty zarządzania również ułatwić klientom przypisania lokacji i pobrania zasad klienta oraz przesłania informacji klienta.  

     Najbezpieczniejszą metodą wyszukiwania punktów zarządzania przez klientów jest publikowanie ich w usługach Active Directory Domain Services. Dlatego zazwyczaj do opublikowania w usługach Active Directory Domain Services wybiera się wszystkie działające punkty zarządzania. Jednak tej metody lokalizacji usługi wymaga spełnienia następujących:

     - Schemat został rozszerzony dla programu Configuration Manager.
     - Istnieje **System zarządzania** kontenera odpowiednie uprawnienia zabezpieczeń dla serwera lokacji do publikowania do tego kontenera.
     - Lokacja programu Configuration Manager jest skonfigurowany do publikowania w usługach domenowych w usłudze Active Directory.
     - Klienci muszą należeć do tego samego lasu usługi Active Directory co serwer lokacji.  

     Gdy klienci w intranecie nie mogą wyszukiwać punkty zarządzania przy użyciu usług domenowych w usłudze Active Directory, użyj [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) zamiast publikowania.  

 Aby uzyskać ogólne informacje o lokalizacji usługi, zobacz [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

-   **Publikuj wybrane punkty zarządzania intranetem w systemie DNS:** Tę opcję należy określić, gdy klienci w intranecie nie może znaleźć punkty zarządzania z usług domenowych w usłudze Active Directory. Zamiast tego umożliwia im DNS rekord zasobów lokalizacji usługi (SRV RR) do znalezienia punktu zarządzania w przypisanej lokacji.  

    Dla programu Configuration Manager publikować punkty zarządzania intranetem w systemie DNS, muszą być spełnione następujące warunki:  

    -   Na serwerach DNS zainstalowano oprogramowanie BIND w wersji 8.1.2 lub nowszej.  

    -   Serwery DNS są skonfigurowane aktualizacje automatyczne i obsługują rekordy zasobów lokalizacji usługi.  

    -   Określony w pełni kwalifikowanych nazw domen (FQDN) dla punktów zarządzania w programie Configuration Manager mają wpisy hosta (rekordy A lub AAA) w systemie DNS.  

    > [!WARNING]  
    >  Aby klienci mogli wyszukiwać punkty zarządzania, które zostały opublikowane w systemie DNS należy przypisać klientów do określonej lokacji (zamiast używać automatycznego przypisania lokacji). Konfigurowanie tych klientów do używania kodu lokacji z sufiksem domeny punktu zarządzania. Aby uzyskać więcej informacji, zobacz [lokalizowanie punktów zarządzania](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](/sccm/core/clients/deploy/assign-clients-to-a-site).  

     Jeśli klienci programu Configuration Manager nie można używać usług domenowych w usłudze Active Directory lub systemu DNS do wyszukiwania punktów zarządzania w intranecie, używają [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins). Pierwszy punkt zarządzania, który jest zainstalowany w lokacji jest automatycznie publikowany w usłudze WINS podczas jej jest skonfigurowany do akceptowania połączeń klienta HTTP w sieci intranet.  

### <a name="status-reporting"></a>Raportowanie stanu  

-   Te ustawienia skonfigurowane bezpośrednio poziom szczegółowości, który jest dołączony do raporty o stanie z lokacji i klientów.  

### <a name="email-notification"></a>Powiadomienia e-mail  

-   Określ konto i wiadomości e-mail szczegóły serwera, aby program Configuration Manager do wysyłania powiadomień e-mail dla alertów.  

### <a name="collection-membership-evaluation"></a>Ocena członkostwa w kolekcji  

-   Za pomocą tego zadania można zmienić częstotliwość oceny członkostwa w kolekcji. Ocena przyrostowa aktualizuje członkostwo kolekcji tylko nowymi i zmienionymi zasobami.  

### <a name="edit-the-site-components-at-a-site"></a>Edytowanie składników lokacji w lokacji  

Aby edytować składniki lokacji, wykonaj następujące kroki:

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie wybierz lokację zawierającą składniki lokacji, które chcesz skonfigurować.  

2.  Na **Home** w karcie **ustawienia** , kliknij przycisk **Konfiguruj składniki lokacji**. Następnie wybierz składnik lokacji, który chcesz skonfigurować.  

##  <a name="BKMK_ServiceMgr"></a> Używanie Menedżera usług programu Configuration Manager do zarządzania składnikami lokacji  
Można użyć Menedżera usług programu Configuration Manager do sterowania usług programu Configuration Manager i wyświetlić stan usługi programu Configuration Manager lub wątków roboczych (określanych zbiorczo jako składniki programu Configuration Manager). Zrozumieć następujące o składnikach programu Configuration Manager:  

-   Składniki można uruchomić w każdym systemie lokacji.  

-   Składniki są zarządzane w taki sam sposób można zarządzać usługami w systemie Windows. Można uruchomić, zatrzymać, wstrzymać, wznowić lub zapytanie składniki programu Configuration Manager.  

Usługa programu Configuration Manager działa w przypadku otrzymania żądania wykonania (zazwyczaj gdy plik konfiguracji zostanie zapisany w skrzynce odbiorczej składnika). Jeśli zachodzi potrzeba zidentyfikowania składnika uwzględnionego w operacji, można użyć Menedżera usług programu Configuration Manager do manipulowania różnymi usługami i wątków. Można następnie zobaczyć wynikową zmianę zachowania programu Configuration Manager. Na przykład można zatrzymać usług programu Configuration Manager jeden w czasie, aż do wyeliminowania określonej odpowiedzi. Pozwala to ustalić, która usługa powoduje dane zachowanie.  

> [!TIP]  
>  Poniższa procedura może służyć do manipulowania operacji składników programu Configuration Manager.  

### <a name="use-the-configuration-manager-service-manager"></a>Użyj Menedżera usług programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie** >  **stan systemu**, a następnie kliknij przycisk **stan składnika**.  

2.  Na **Home** w karcie **składnika** , kliknij przycisk **Start**. Następnie wybierz **usług programu Configuration Manager**.  

3.  Po otwarciu Menedżera usług programu Configuration Manager połącz się z lokacją, którą chcesz zarządzać.  

     Jeżeli lokacja do zarządzania nie jest wyświetlana, kliknij kolejno przyciski **Lokacja**i **Połącz**, a następnie wprowadź nazwę serwera odpowiedniej lokacji.  

4.  Rozwiń lokację i przejdź do węzła **Składniki** lub **Serwery** w zależności od lokalizacji składników, którymi chcesz zarządzać.  

5.  W prawym okienku wybierz jeden lub więcej składników. Następnie na **składnika** menu, kliknij przycisk **kwerendy** zaktualizować stan wybranego elementu.  

6.  Po zaktualizowaniu stanu składnika użyj jednej z czterech opcji akcji w **składnika** menu do modyfikowania działania składnika. Po zażądaniu akcji należy wysłać do składnika kwerendę w celu wyświetlenia jego nowego stanu.  

7.  Po zakończeniu modyfikowania stanu operacyjnego składników, Zamknij Menedżera usług programu Configuration Manager.  

