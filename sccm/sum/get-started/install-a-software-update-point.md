---

title: Instalowanie i Konfigurowanie punktu aktualizacji oprogramowania | Dokumentacja firmy Microsoft
description: "Lokacje główne wymagają punktu aktualizacji oprogramowania w centralnej lokacji administracyjnej dla oceny zgodności aktualizacji oprogramowania i aby wdrożyć oprogramowanie aktualizacje klientów."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 05/30/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b099a645-6434-498f-a408-1d438e394396
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 7d369384d133c90a15e01df50ac53992d61f3873
ms.contentlocale: pl-pl
ms.lasthandoff: 06/01/2017



---


# <a name="install-and-configure-a-software-update-point"></a>Instalowanie i Konfigurowanie punktu aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


> [!IMPORTANT]  
>  Przed zainstalowaniem roli systemu lokacji punktu aktualizacji oprogramowania należy zweryfikować, że serwer spełnia wymagane zależności i ustala infrastrukturę punktu aktualizacji oprogramowania w danej lokacji. Aby uzyskać więcej informacji o sposobach planowania aktualizacji oprogramowania i ustalania infrastruktury punktu aktualizacji oprogramowania, zobacz [Planowanie aktualizacji oprogramowania](../plan-design/plan-for-software-updates.md).  

 Punkt aktualizacji oprogramowania jest wymagany w centralnej lokacji administracyjnej i w lokacjach głównych do włączenia oceny zgodności aktualizacji oprogramowania i wdrożenia aktualizacji oprogramowania na klientach. Punkt aktualizacji oprogramowania jest opcjonalny w lokacjach dodatkowych. Na serwerze, na którym są zainstalowane usługi WSUS, należy utworzyć rolę systemu lokacji punktu aktualizacji oprogramowania. Punkt aktualizacji oprogramowania prowadzi interakcję z usługami WSUS w celu skonfigurowania ustawień aktualizacji oprogramowania i żądania synchronizacji metadanych aktualizacji oprogramowania. Jeśli masz hierarchii programu Configuration Manager, najpierw zainstalować i skonfigurować punkt aktualizacji oprogramowania w centralnej lokacji administracyjnej, następnie w podrzędnych lokacjach głównych, a następnie opcjonalnie w lokacjach dodatkowych. W przypadku autonomicznej lokacji głównej, a nie centralnej lokacji administracyjnej, należy najpierw zainstalować i skonfigurować punkt aktualizacji oprogramowania w lokacji głównej, a potem — opcjonalnie — w lokacjach dodatkowych. Niektóre ustawienia są dostępne tylko podczas konfigurowania punktu aktualizacji oprogramowania w lokacji najwyższego poziomu. Istnieją różne opcje, które należy wziąć pod uwagę zależnie od miejsca instalacji punktu aktualizacji oprogramowania.  

> [!IMPORTANT]  
>  Możesz zainstalować wiele punktów aktualizacji oprogramowania w lokacji. Pierwszy zainstalowany punkt aktualizacji oprogramowania zostaje skonfigurowany jako źródło synchronizacji, które synchronizuje aktualizacje z usługi Microsoft Update lub z nadrzędnego źródła synchronizacji. Inne punkty aktualizacji oprogramowania w danej lokacji zostają skonfigurowane jako repliki pierwszego punktu aktualizacji oprogramowania. Dlatego też po zainstalowaniu i skonfigurowaniu początkowego punktu aktualizacji oprogramowania niektóre ustawienia przestają być dostępne.  

> [!IMPORTANT]  
>  Zainstaluj rolę systemu lokacji punktu aktualizacji oprogramowania na serwerze, który został skonfigurowany nie jest obsługiwane i używane jako autonomiczny serwer WSUS lub przy użyciu punktu aktualizacji oprogramowania do bezpośredniego zarządzania klientami programu WSUS. Istniejące serwery usług WSUS są obsługiwane tylko jako źródła synchronizacji nadrzędnego punktu aktualizacji oprogramowania aktywnego. Zobacz [Synchronizuj z lokalizacji nadrzędnego źródła danych](#BKMK_wsussync)

 Rolę systemu lokacji punktu aktualizacji oprogramowania można dodać do istniejącego serwera systemu lokacji lub można utworzyć nowy serwer. Na stronie **Wybór roli systemu** w **Kreatorze tworzenia serwera systemu lokacji** lub **Kreatorze dodawania ról systemu lokacji** , zależnie od tego, czy rola systemu lokacji ma zostać dodana do nowego, czy do istniejącego serwera lokacji, wybierz pozycję **Punkt aktualizacji oprogramowania**, a następnie skonfiguruj ustawienia punktu aktualizacji oprogramowania w kreatorze. Te ustawienia są różne w zależności od wersji programu Configuration Manager używanej. Aby uzyskać więcej informacji o sposobach instalowania ról systemu lokacji, zobacz [zainstalować role systemu lokacji](../../core/servers/deploy/configure/install-site-system-roles.md).  

 W poniższych częściach zamieszczono informacje o ustawieniach punktu aktualizacji oprogramowania w lokacji.  

## <a name="proxy-server-settings"></a>Ustawienia serwera proxy  
 Ustawienia serwera proxy można skonfigurować na różnych stronach **lokacji Kreator tworzenia serwera systemu** lub **lokacji Kreator dodawania ról systemu** w zależności od wersji programu Configuration Manager używanej.  

-   Należy skonfigurować serwer proxy, a następnie określić, kiedy serwer proxy ma być używany do aktualizacji oprogramowania. Skonfiguruj następujące ustawienia:  

    -   Skonfiguruj ustawienia serwera proxy na stronie **Serwer proxy** kreatora lub na karcie **Serwer proxy** właściwości systemu lokacji. Ustawienia serwera proxy są właściwe dla systemu lokacji, co oznacza, że wszystkie role systemu lokacji korzystają z określonych tutaj ustawień serwera proxy.  

    -   Określ, czy można używać serwera proxy programu Configuration Manager synchronizuje oprogramowania, aktualizacji i pobierania zawartości przy użyciu reguły wdrażania automatycznego. Skonfiguruj ustawienia serwera proxy punktu aktualizacji oprogramowania na stronie **Ustawienia serwera proxy i konta** kreatora lub na karcie **Ustawienia serwera proxy i konta** właściwości punktu aktualizacji oprogramowania.  

        > [!NOTE]  
        >  Ustawienie **Używaj serwera proxy podczas pobierania zawartości za pomocą reguł wdrażania automatycznego** jest dostępne, ale nie jest używane dla punktu aktualizacji oprogramowania w lokacji dodatkowej. Zawartość ze strony Microsoft Update pobiera tylko punkt aktualizacji oprogramowania w centralnej lokacji administracyjnej i lokacji głównej.  

> [!IMPORTANT]  
>  Domyślnie do łączenia się z Internetem i pobierania aktualizacji oprogramowania podczas uruchamiania reguł wdrażania automatycznego służy konto **System lokalny** na serwerze, na którym dana reguła wdrażania automatycznego została utworzona. Gdy to konto nie ma dostępu do Internetu, aktualizacji oprogramowania nie udaje się pobrać i ruleengine.log jest rejestrowany następujący wpis: **Nie można pobrać aktualizacji z Internetu. Błąd = 12007**. Należy skonfigurować poświadczenia pozwalające połączyć się z serwerem proxy, kiedy konto System lokalny nie ma dostępu do Internetu.  


## <a name="wsus-settings"></a>Ustawienia usług WSUS  
 Ustawienia usług WSUS należy skonfigurować na różnych stronach **lokacji Kreator tworzenia serwera systemu** lub **lokacji Kreator dodawania ról systemu** w zależności od wersji programu Configuration Manager używanej, a w niektórych przypadkach tylko we właściwościach oprogramowania punktu aktualizacji, znanej także jako właściwości punktu aktualizacji oprogramowania składnika. Do konfigurowania ustawień usług WSUS służą informacje podane w poniższych częściach.  

### <a name="BKMK_wsusport"></a>Ustawienia portów dla usług WSUS  
 Ustawienia portów dla usług WSUS należy skonfigurować na stronie kreatora zatytułowanej Punkt aktualizacji oprogramowania lub we właściwościach punktu aktualizacji oprogramowania. Użyj poniższej procedury, aby określić ustawienia portów używane przez program WSUS.  

#### <a name="to-determine-the-port-settings-used-in-iis"></a>Aby określić ustawienia portów używane w programie IIS  

 1.  Otwórz Menedżera internetowych usług informacyjnych (IIS) na serwerze WSUS.  

 2.  Rozwiń pozycję **Witryny**, kliknij prawym przyciskiem myszy witrynę sieci Web serwera WSUS i kliknij opcję **Edytuj powiązania**. Wartości portów HTTP i HTTPS zostają wyświetlone w oknie dialogowym Powiązania witryny w kolumnie **Port** .


### <a name="configure-ssl-communications-to-wsus"></a>Konfigurowanie komunikacji SSL z usługami WSUS  
 Komunikację SSL można skonfigurować na stronie **Ogólne** kreatora lub na karcie **Ogólne** właściwości punktu aktualizacji oprogramowania.  

 Więcej informacji o sposobach korzystania z protokołu SSL znajduje się w temacie [Czy skonfigurować program WSUS do używania protokołu SSL](../plan-design/plan-for-software-updates.md#BKMK_WSUSandSSL).  

### <a name="wsus-server-connection-account"></a>Konto połączenia serwera WSUS  
 Można skonfigurować konto, którego będzie używał serwer lokacji podczas łączenia się z usługami WSUS uruchamianymi w punkcie aktualizacji oprogramowania. Jeśli takie konto nie jest skonfigurowane, Configuration Manager używa konta komputera serwera lokacji do nawiązania połączenia usług WSUS. Skonfiguruj ustawienia konta połączenia serwera WSUS na stronie **Ustawienia serwera proxy i konta** kreatora lub na karcie **Ustawienia serwera proxy i konta** właściwości punktu aktualizacji oprogramowania.  Konto można skonfigurować w różnych miejscach kreatora, zależnie od wersji programu Configuration Manager używanej.  

 Aby uzyskać więcej informacji o kontach programu Configuration Manager, zobacz [konta używane w programie System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md).  

## <a name="synchronization-source"></a>Źródło synchronizacji  
 Nadrzędne źródło synchronizacji dla synchronizacji aktualizacji oprogramowania można konfigurować na stronie **Źródło synchronizacji** kreatora lub na karcie **Ustawienia synchronizacji** właściwości składnika punktu aktualizacji oprogramowania. Dostępne opcje dotyczące źródła synchronizacji są różne, w zależności od lokacji.  

 W poniższej tabeli zamieszczono opcje dostępne podczas konfigurowania punktu aktualizacji oprogramowania w lokacji.  

|Lokacja|Dostępne opcje źródła synchronizacji|  
|----------|----------------------------------------------|  
|— Centralna lokacja administracyjna<br />— Autonomiczna lokacja główna|— Synchronizuj z witryny usługi Microsoft Update<br />— Synchronizuj z lokalizacji nadrzędnego źródła danych<br />— Nie synchronizuj z usługi Microsoft Update ani nadrzędnego źródła danych|  
|— Dodatkowe punkty aktualizacji oprogramowania w lokacji<br />— Podrzędna lokacja główna<br />— Lokacja dodatkowa|— Synchronizuj z lokalizacji nadrzędnego źródła danych|  

 Na liście poniżej przedstawiono więcej informacji o każdej opcji, której można użyć jako źródła synchronizacji:  

-   **Synchronizuj z usługi Microsoft Update**: To ustawienie służy do synchronizowania metadanych aktualizacji oprogramowania z witryny Microsoft Update. Centralna lokacja administracyjna musi mieć dostęp do Internetu, w przeciwnym razie synchronizacja zakończy się niepowodzeniem. To ustawienie jest dostępne tylko podczas konfigurowania punktu aktualizacji oprogramowania w lokacji najwyższego poziomu.  

    > [!NOTE]  
    >  Jeśli punkt aktualizacji oprogramowania oddziela od Internetu zapora, może być konieczne skonfigurowanie jej do akceptowania ruchu na portach HTTP i HTTPS, które są używane do komunikacji z witryną sieci Web usług WSUS. Można też zdecydować się na ograniczenie dostępu w zaporze do wybranych domen. Aby uzyskać więcej informacji o tym, jak planować zaporę obsługującą aktualizacje oprogramowania, zobacz [Konfigurowanie zapór](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls).  

-   **<a name="BKMK_wsussync"></a>Synchronizuj z lokalizacji nadrzędnego źródła danych**: To ustawienie służy do synchronizowania metadanych aktualizacji oprogramowania z nadrzędnego źródła synchronizacji. Podrzędne lokacje główne i lokacje dodatkowe są automatycznie konfigurowane tak, aby dla tego ustawienia używać adresu URL lokacji nadrzędnej. Jest dostępna opcja synchronizowania aktualizacji oprogramowania z istniejącego serwera WSUS. Należy określić adres URL, taki jak https://WSUSServer:8531, gdzie 8531 to port używany do łączenia się z serwerem usług WSUS.  

-   **Nie Synchronizuj z usługi Microsoft Update ani nadrzędnego źródła danych**: To ustawienie służy do ręcznego synchronizowania aktualizacji oprogramowania, kiedy punkt aktualizacji oprogramowania w lokacji najwyższego poziomu jest odłączony od Internetu. Aby uzyskać więcej informacji, zobacz [Synchronizowanie aktualizacji oprogramowania z odłączonego punktu aktualizacji oprogramowania](synchronize-software-updates-disconnected.md).  

> [!NOTE]  
>  Jeśli punkt aktualizacji oprogramowania oddziela od Internetu zapora, może być konieczne skonfigurowanie jej do akceptowania ruchu na portach HTTP i HTTPS, które są używane do komunikacji z witryną sieci Web usług WSUS. Można też zdecydować się na ograniczenie dostępu w zaporze do wybranych domen. Aby uzyskać więcej informacji o tym, jak planować zaporę obsługującą aktualizacje oprogramowania, zobacz [Konfigurowanie zapór](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls).  

 Użycie zdarzeń raportowania usług WSUS można skonfigurować także na stronie **Źródło synchronizacji** kreatora lub na karcie **Ustawienia synchronizacji** właściwości składnika punktu aktualizacji oprogramowania. Menedżer konfiguracji nie używa tych zdarzeń. w związku z tym zazwyczaj wybiera się ustawienie domyślne **nie twórz zdarzeń do raportowania WSUS**.  

## <a name="synchronization-schedule"></a>Harmonogram synchronizacji  
 Harmonogram synchronizacji można konfigurować na stronie **Harmonogram synchronizacji** kreatora lub we właściwościach składnika punktu aktualizacji oprogramowania. To ustawienie jest skonfigurowane tylko w punkcie aktualizacji oprogramowania należącym do lokacji najwyższego poziomu.  

 Po włączeniu harmonogramu można skonfigurować cykliczny — prosty lub niestandardowy — harmonogram synchronizacji. Podczas konfigurowania harmonogramu prostego czas rozpoczęcia jest oparty na czasie lokalnym komputera, na którym jest uruchomiona konsola programu Configuration Manager w momencie tworzenia harmonogramu. Konfigurowania harmonogramu niestandardowego czas rozpoczęcia jest oparty na czasie lokalnym komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

> [!TIP]  
>  Zaplanuj uruchamianie synchronizacji aktualizacji oprogramowania w okresie odpowiednim dla Twojego środowiska. Według jednego z typowych scenariuszy harmonogram synchronizowania aktualizacji oprogramowania uruchamia się wkrótce po regularnym wydaniu aktualizacji zabezpieczeń przez firmę Microsoft, co następuje w drugi wtorek każdego miesiąca, popularnie nazywany „wtorkiem poprawek”. Inny typowy scenariusz polega na tym, by ustawić codzienne uruchamianie harmonogramu synchronizowania aktualizacji oprogramowania podczas użycia aktualizacji oprogramowania do dostarczenia aktualizacji aparatu i definicji programu Endpoint Protection.  

> [!NOTE]  
>  W razie podjęcia decyzji o niewłączaniu harmonogramu synchronizowania aktualizacji oprogramowania można ręcznie synchronizować aktualizacje oprogramowania z węzła **Wszystkie aktualizacje oprogramowania** lub **Grupy aktualizacji oprogramowania** w obszarze roboczym Biblioteka oprogramowania. Aby uzyskać więcej informacji, zobacz [synchronizowanie aktualizacji oprogramowania](synchronize-software-updates.md).  

## <a name="supersedence-rules"></a>Reguły zastępowania  
 Ustawienia zastępowania można konfigurować na stronie **Reguły zastępowania** kreatora lub na karcie **Reguły zastępowania** właściwości składnika punktu aktualizacji oprogramowania. Zasady zastępowania można konfigurować tylko w lokacji najwyższego poziomu.  

 Na tej stronie można określić, że zastępowane aktualizacje oprogramowania mają być natychmiast uznawane za wygasłe, co zapobiega włączaniu ich w nowe wdrożenia oraz flaguje istniejące wdrożenia i wskazuje, że zastąpione aktualizacje oprogramowania zawierają co najmniej jedną wygasłą aktualizację oprogramowania. Alternatywnie można też wskazać okres czasu, jaki ma upłynąć przed uznaniem zastąpionych aktualizacji oprogramowania za wygasłe, co pozwala nadal je wdrażać. Aby uzyskać więcej informacji, zobacz [Reguły zastępowania](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

> [!NOTE]  
>  Strona **Reguły zastępowania** kreatora jest dostępna tylko podczas konfigurowania pierwszego punktu aktualizacji oprogramowania w danej lokacji. Ta strona nie jest wyświetlana po zainstalowaniu dodatkowych punktów aktualizacji oprogramowania.  

## <a name="classifications"></a>Klasyfikacje  
 Skonfiguruj ustawienia klasyfikacji na stronie **Klasyfikacje** kreatora lub na karcie **Klasyfikacje** właściwości składnika punktu aktualizacji oprogramowania. Więcej informacji o klasyfikacjach aktualizacji oprogramowania znajduje się w temacie [Klasyfikacje aktualizacji](../plan-design/plan-for-software-updates.md#BKMK_UpdateClassifications).  

> [!NOTE]  
>  Strona **Klasyfikacje** kreatora jest dostępna tylko podczas konfigurowania pierwszego punktu aktualizacji oprogramowania w danej lokacji. Ta strona nie jest wyświetlana po zainstalowaniu dodatkowych punktów aktualizacji oprogramowania.  

> [!TIP]  
>  Podczas pierwszej instalacji punktu aktualizacji oprogramowania w lokacji najwyższego poziomu wyczyść wszystkie klasyfikacje aktualizacji oprogramowania. Po początkowej synchronizacji aktualizacji oprogramowania skonfiguruj klasyfikacje ze zaktualizowanej listy, a potem ponownie zainicjuj synchronizację. To ustawienie jest skonfigurowane tylko w punkcie aktualizacji oprogramowania należącym do lokacji najwyższego poziomu.  

## <a name="products"></a>Produkty  
 Skonfiguruj ustawienia produktów na stronie **Produkty** kreatora lub na karcie **Produkty** właściwości składnika punktu aktualizacji oprogramowania.  

> [!NOTE]  
>  Strona **Produkty** kreatora jest dostępna tylko podczas konfigurowania pierwszego punktu aktualizacji oprogramowania w danej lokacji. Ta strona nie jest wyświetlana po zainstalowaniu dodatkowych punktów aktualizacji oprogramowania.  

> [!TIP]  
>  Podczas pierwszej instalacji punktu aktualizacji oprogramowania w lokacji najwyższego poziomu wyczyść wszystkie produkty. Po początkowej synchronizacji aktualizacji oprogramowania skonfiguruj produkty ze zaktualizowanej listy, a potem ponownie zainicjuj synchronizację. To ustawienie jest skonfigurowane tylko w punkcie aktualizacji oprogramowania należącym do lokacji najwyższego poziomu.  

## <a name="languages"></a>Języki  
 Ustawienia języków można konfigurować na stronie **Języki** kreatora lub na karcie **Języki** właściwości składnika punktu aktualizacji oprogramowania. Można określić języki, dla których chce się synchronizować pliki aktualizacji oprogramowania i szczegóły podsumowania. **Plik z aktualizacją oprogramowania** ustawienie jest konfigurowane w każdym punkcie aktualizacji oprogramowania w hierarchii programu Configuration Manager. Ustawienia **Szczegóły podsumowania** konfiguruje się tylko w punkcie aktualizacji oprogramowania na najwyższym poziomie. Aby uzyskać więcej informacji, zobacz [Języki](../plan-design/plan-for-software-updates.md#BKMK_UpdateLanguages).  

> [!NOTE]  
>  Strona **Języki** kreatora jest dostępna tylko podczas instalowania punktu aktualizacji oprogramowania w centralnej lokacji administracyjnej. Języki plików aktualizacji oprogramowania można konfigurować w lokacjach podrzędnych na karcie **Języki** właściwości składnika punktu aktualizacji oprogramowania.  

## <a name="next-steps"></a>Następne kroki
Punkt aktualizacji oprogramowania, zaczynając od najwyższy lokacji w hierarchii programu Configuration Manager został zainstalowany. Powtórz procedury przedstawione w tym temacie, aby zainstalować punkt aktualizacji oprogramowania w lokacjach podrzędnych.

Po utworzeniu oprogramowania punkty zainstalowanych aktualizacji, przejdź do [synchronizowanie aktualizacji oprogramowania](synchronize-software-updates.md).

