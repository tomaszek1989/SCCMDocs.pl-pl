---
title: Scenariusz Endpoint Protection chroni komputery przed złośliwym oprogramowaniem
titleSuffix: Configuration Manager
description: Dowiedz się, jak implementacji programu Endpoint Protection w programie Configuration Manager do ochrony komputerów przed atakami złośliwego oprogramowania.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: doubeby
ms.openlocfilehash: 36f63a585fdcdc00d6ace9ea1ac6941aead5fce2
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Przykładowy scenariusz: Używanie programu System Center Endpoint Protection do ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera przykładowy scenariusz dla implementacji programu Endpoint Protection w programie Configuration Manager do ochrony komputerów w organizacji przez atakami złośliwego oprogramowania.  

 Jan jest administratorem programu Configuration Manager w banku Woodgrove Bank. Bank aktualnie używa programu System Center Endpoint Protection do ochrony komputerów przed atakami złośliwego oprogramowania. Ponadto w banku stosowane są zasady grupy systemu Windows, dzięki czemu Zapora systemu Windows jest włączona na wszystkich komputerach w firmie, a użytkownicy są powiadamiani o zablokowaniu nowego programu przez Zaporę systemu Windows.  

 Jan został poproszony o uaktualnienie oprogramowania chroniącego Woodgrove Bank do programu System Center Endpoint Protection, aby bank mogli korzystać z najnowszych funkcji ochrony przed złośliwym oprogramowaniem i centralnie zarządzać rozwiązania chroniące przed złośliwym kodem z konsoli programu Configuration Manager. Ta implementacja musi spełniać następujące wymagania:  

-   Użyj programu Configuration Manager do zarządzania ustawieniami Zapory systemu Windows, które są obecnie zarządzane przez zasady grupy.  

-   Użyj Menedżera konfiguracji aktualizacji oprogramowania można pobrać definicji złośliwego oprogramowania na komputerach. Jeśli aktualizacje oprogramowania nie są dostępne, na przykład jeśli komputer nie jest połączony z siecią firmową, aktualizacje definicji powinny być pobierane z usługi Microsoft Update.  

-   Komputerów należy wykonać skanowania codziennie szybkie złośliwego oprogramowania. Natomiast na serwerach powinno być uruchamiane pełne skanowanie w każdą sobotę, poza godzinami pracy, o godzinie 1:00.  

-   Po wystąpieniu któregokolwiek z następujących zdarzeń powinna być wysyłana wiadomość e-mail dla alertu:  

    -   Na dowolnym komputerze wykryto złośliwe oprogramowanie.  

    -   Na więcej niż 5 procentach komputerów wykryto to samo zagrożenie złośliwym oprogramowaniem.  

    -   To samo zagrożenie złośliwym oprogramowaniem wykryto więcej niż 5 razy w dowolnym okresie 24 godzin  

    -   Wykryto więcej niż 3 różne rodzaje złośliwego oprogramowania w dowolnym okresie 24 godzin  

-   Należy odinstalować istniejące rozwiązanie chroniące przed złośliwym kodem.  

 Jan następnie wykonuje następujące czynności w celu implementacji programu Endpoint Protection:  

##  <a name="steps-to-implement-endpoint-protection"></a>Kroki implementacji programu Endpoint Protection  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jan przegląda dostępne informacje o podstawowych koncepcjach dla programu Endpoint Protection w programie Configuration Manager.|Informacje o programie Endpoint Protection, zobacz [programu Endpoint Protection w programie System Center Configuration Manager](endpoint-protection.md).|  
|Jan przegląda i implementuje wymagania wstępne, aby używać programu Endpoint Protection.|Aby uzyskać informacje o wymaganiach wstępnych dotyczących programu Endpoint Protection, zobacz [planowanie programu Endpoint Protection](../plan-design/planning-for-endpoint-protection.md).|  
|Jan instaluje rolę systemu lokacji programu Endpoint Protection na jednym serwerze systemu lokacji tylko na szczycie hierarchii banku Woodgrove.|Aby uzyskać więcej informacji o instalowaniu roli systemu lokacji programu Endpoint Protection, zobacz "Wymagania wstępne" w [skonfigurować program Endpoint Protection](configure-endpoint-protection.md).|  
|Jan konfiguruje programu Configuration Manager do korzystania z serwera SMTP do wysyłania alertów e-mail.<br /><br /> **Uwaga:** Serwer SMTP należy skonfigurować tylko wtedy, gdy chcesz otrzymać powiadomienie e-mail po wygenerowaniu alertu programu Endpoint Protection.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie alertów programu Endpoint Protection](endpoint-configure-alerts.md).|  
|Jan tworzy kolekcję urządzeń zawierającą wszystkie komputery i serwery do zainstalowania klienta programu Endpoint Protection. Nadaje jej nazwę tej kolekcji **wszystkie komputery chronione przez program Endpoint Protection**.<br /><br /> **Porada:** Nie można skonfigurować alertów dla kolekcji użytkowników.|Aby uzyskać więcej informacji o sposobach tworzenia kolekcji, zobacz [jak tworzyć kolekcje w programie System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Konfigurowane są następujące alerty dla kolekcji: <br /><br />1) **złośliwe oprogramowanie zostanie wykryte**: Jan konfiguruje alert o ważności **krytyczny**. <br /><br />2) **na wielu komputerach wykryto ten sam typ złośliwego oprogramowania**: Jan konfiguruje alert o ważności **krytyczny** i określa, czy alert zostanie wygenerowany, gdy więcej niż 5 procentach komputerów wykryto złośliwy kod. <br /><br />3) **ten sam typ złośliwego oprogramowania zostało wielokrotnie wykryte w określonym interwale na komputerze**: Jan konfiguruje alert o ważności **krytyczny** i określa, czy alert będzie generowany po wykryciu złośliwego oprogramowania więcej niż 5 razy w okresie 24 godzin. <br /><br />(4) **Wykryto wiele typów złośliwego oprogramowania na tym samym komputerze w określonym interwale**: Jan konfiguruje alert o ważności **krytyczny** i określa, czy alert zostanie wygenerowany, gdy więcej niż 3 rodzajów złośliwego oprogramowania są generowane w okresie 24 godzin.<br /><br /> Wartość **ważności alertu** wskazuje poziom alertu, który będzie wyświetlany w konsoli programu Configuration Manager i w alertach otrzymywanych w wiadomości e-mail.<br /><br /> Ponadto wybierana jest opcja **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** , która umożliwia monitorowanie alertów w konsoli programu Configuration Manager.|Zobacz temat "Konfigurowanie alertów dla programu Endpoint Protection" w [Konfigurowanie programu Endpoint Protection w programie System Center Configuration Manager](endpoint-configure-alerts.md).|  
|Jan konfiguruje aktualizacje oprogramowania Configuration Manager, aby pobrać i wdrożyć aktualizacje definicji trzy razy dziennie przy użyciu reguły wdrażania automatycznego.|Aby uzyskać więcej informacji, zobacz sekcję "Przy użyciu konfiguracji Menedżera aktualizacji do dostarczenia aktualizacji definicji oprogramowania" w [aktualizacji oprogramowania za pomocą Menedżera konfiguracji w celu dostarczenia aktualizacji definicji](endpoint-definitions-configmgr.md).|  
|Jan sprawdza ustawienia w domyślnych zasadach ochrony przed złośliwym kodem, które zawierają zalecane ustawienia zabezpieczeń firmy Microsoft. Dla komputerów, na których codziennie ma być wykonywane szybkie skanowanie, zmieniane są następujące ustawienia:<br /><br /> 1) **uruchamianie codzienne szybkie skanowanie na komputerach klienckich**: **Tak**.<br /><br /> 2) **godzina harmonogramu codziennego szybkiego skanowania**:  **9:00 AM**.<br /><br /> Opcja **Aktualizacje dystrybuowane za pomocą usługi Microsoft Update** jest wybrana domyślnie jako źródło aktualizacji definicji. Dzięki temu spełnione jest wymaganie biznesowe, w którym komputery powinny pobierać definicje z witryny Microsoft Update, gdy nie mogą pobrać aktualizacje oprogramowania Configuration Manager.|Zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan tworzy kolekcję o nazwie **Serwery banku Woodgrove Bank**, która zawiera tylko serwery banku Woodgrove Bank.|Zobacz [Jak tworzyć kolekcje w programie System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Jan tworzy niestandardowe zasady ochrony przed złośliwym kodem o nazwie **Zasady serwera banku Woodgrove Bank**. Dodaje tylko ustawienia w obszarze **Skany zaplanowane** , wprowadzając następujące zmiany:<br /><br /> **Typ skanowania**:  **Full**<br /><br /> **Dzień skanowania**:  **Sobota**<br /><br /> **Data i godzina skanowania**: **1:00:00**<br /><br /> **Uruchamianie codzienne szybkie skanowanie na komputerach klienckich**:  **Nie**.|Zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan wdraża niestandardowe zasady ochrony przed złośliwym kodem **Zasady serwera banku Woodgrove Bank** w kolekcji **Serwery banku Woodgrove Bank** .|Zobacz "Aby wdrożyć zasady ochrony przed złośliwym kodem na komputerach klienckich" [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection](endpoint-antimalware-policies.md) artykułu.|  
|Jan tworzy nowy zestaw klienta niestandardowe ustawienia urządzenia dla programu Endpoint Protection i nadaje mu nazwę **ustawienia ochrony punktu końcowego banku Woodgrove Bank**.<br /><br /> **Uwaga:** Jeśli nie chcesz zainstalować i włączyć program Endpoint Protection na wszystkich klientach w hierarchii, upewnij się, że opcje **klienta zarządzania Endpoint Protection na komputerach klienckich** i **klienta zainstaluj program Endpoint Protection na komputerach klienckich** obydwa są skonfigurowane jako **nr** w domyślnych ustawieniach klienta.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md).|  
|Konfiguruje następujące ustawienia programu Endpoint Protection:<br /><br /> **Zarządzanie klientem programu Endpoint Protection na komputerach klienckich**:  **Tak**<br /><br /> To ustawienie i jego wartość gwarantuje, że ewentualny istniejący klient programu Endpoint Protection, który jest zainstalowany jest zarządzane przez program Configuration Manager.<br /><br /> **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**:  **Tak**.</br></br>**Uwaga** począwszy od programu Configuration Manager 1802 urządzeń z systemem Windows 10 nie musi być zainstalowany agent programu Endpoint Protection. Jeśli jest już zainstalowany na urządzeniach z systemem Windows 10, Menedżer konfiguracji nie zostanie on usunięty. Administratorzy mogą usunąć agenta programu Endpoint Protection na urządzeniach z systemem Windows 10, które są co najmniej z wersją klienta 1802.<br /><br /> **Automatycznie usuwaj wcześniej zainstalowane oprogramowanie chroniące przed złośliwym kodem przed zainstalowaniem programu Endpoint Protection**:  **Tak**.<br /><br /> To ustawienie i jego wartość spełniają wymaganie biznesowe usunięcie istniejące oprogramowanie chroniące przed złośliwym kodem, zanim program Endpoint Protection jest zainstalowany i włączony.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md).|  
|Jan wdraża **ustawienia ochrony punktu końcowego banku Woodgrove Bank** ustawienia klienta, aby **wszystkie komputery chronione przez program Endpoint Protection** kolekcji.|Zobacz temat "Konfigurowanie niestandardowych ustawień klienta dla programu Endpoint Protection" w [Konfigurowanie programu Endpoint Protection w programie Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan tworzy zasady w Kreatorze tworzenia zasad zapory systemu Windows, konfigurując następujące ustawienia w profilu domeny:<br /><br /> 1) **włączenie zapory systemu Windows**: **Tak**<br /><br /> 2)<br />                    **Powiadamiaj użytkownika, gdy Zapora systemu Windows zablokuje nowy program**: **Tak**|Zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](../../protect/deploy-use/create-windows-firewall-policies.md)|  
|Jan wdraża nowe zasady zapory w kolekcji **wszystkie komputery chronione przez program Endpoint Protection** utworzonej wcześniej.|Zobacz sekcję "Aby wdrożyć zasady zapory systemu Windows" w [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](create-windows-firewall-policies.md)|  
|Jan używa dostępnych zadań zarządzania dla programu Endpoint Protection, aby zarządzać ochrony przed złośliwym kodem i zasadami zapory systemu Windows, wykonywać skanowanie na żądanie z komputerami, jeśli jest to konieczne, wymuszać komputery, aby pobrać najnowsze definicje i określa dalsze działania w sytuacji, gdy złośliwe oprogramowanie zostanie wykryte.|Zobacz [jak zarządzać zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-firewall.md)|  
|Jacek korzysta z poniższych metod, aby monitorować stan programu Endpoint Protection i akcje podejmowane przez program Endpoint Protection:<br /><br /> 1) przy użyciu **stan programu Endpoint Protection** węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego.<br /><br /> 2) przy użyciu **programu Endpoint Protection** w węźle **zasoby i zgodność** obszaru roboczego.<br /><br /> 3) przy użyciu wbudowanych programu Configuration Manager raportów.|Zobacz [jak monitorować program Endpoint Protection w programie System Center Configuration Manager](monitor-endpoint-protection.md)|  

 Jan zgłasza Menedżerowi pomyślne zaimplementowanie programu Endpoint Protection i potwierdza, że komputery w banku Woodgrove Bank są teraz chronione przed złośliwym oprogramowaniem zgodnie z podanymi wymagania biznesowe.
