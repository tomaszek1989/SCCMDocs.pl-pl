---
title: "Scenariusz Endpoint Protection chroni komputery przed złośliwym oprogramowaniem | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zaimplementować Endpoint Protection w programie Configuration Manager do ochrony komputerów przed atakami złośliwego oprogramowania."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b98684d44874ff246e4d675039c6e443aee82a62
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Przykładowy scenariusz: Za pomocą programu System Center Endpoint Protection w celu ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera przykładowy scenariusz dla implementacji Endpoint Protection w programie Configuration Manager do ochrony komputerów w organizacji przez atakami złośliwego oprogramowania.  

 Jacek jest administratorem programu Configuration Manager w banku Woodgrove. Bank aktualnie używa programu System Center Endpoint Protection do ochrony komputera przed atakami złośliwego oprogramowania. Ponadto w banku stosowane są zasady grupy systemu Windows, dzięki czemu Zapora systemu Windows jest włączona na wszystkich komputerach w firmie, a użytkownicy są powiadamiani o zablokowaniu nowego programu przez Zaporę systemu Windows.  

 John został poproszony o uaktualnienie oprogramowania ochrony przed złośliwym oprogramowaniem banku Woodgrove do programu System Center Endpoint Protection, dzięki czemu bank mogą korzystać z najnowszych funkcji ochrony przed złośliwym oprogramowaniem i centralnie zarządzać rozwiązań chroniących przed złośliwym kodem z konsoli programu Configuration Manager. Ta implementacja musi spełniać następujące wymagania:  

-   Użyj programu Configuration Manager do zarządzania ustawieniami Zapory systemu Windows, które są obecnie zarządzane przez zasady grupy.  

-   Użyj Menedżera konfiguracji aktualizacji oprogramowania, aby pobrać aktualizacje definicji złośliwego oprogramowania na komputerach. Jeśli aktualizacje oprogramowania nie są dostępne, na przykład jeśli komputer nie jest połączony z siecią firmową, aktualizacje definicji powinny być pobierane z usługi Microsoft Update.  

-   Komputery użytkowników należy przeprowadzić skanowania w poszukiwaniu złośliwego oprogramowania szybkie codziennie. Natomiast na serwerach powinno być uruchamiane pełne skanowanie w każdą sobotę, poza godzinami pracy, o godzinie 1:00.  

-   Po wystąpieniu któregokolwiek z następujących zdarzeń powinna być wysyłana wiadomość e-mail dla alertu:  

    -   Na dowolnym komputerze wykryto złośliwe oprogramowanie.  

    -   Na więcej niż 5 procentach komputerów wykryto to samo zagrożenie złośliwym oprogramowaniem.  

    -   Wykryto to samo zagrożenie złośliwym oprogramowaniem więcej niż 5 razy w dowolnym okresie 24 godzin.  

    -   Wykryto więcej niż 3 różne rodzaje złośliwego oprogramowania w dowolnym okresie 24 godzin.  

-   Należy odinstalować istniejące rozwiązanie chroniące przed złośliwym kodem.  

 Następnie John wykonuje następujące kroki, aby zaimplementować Endpoint Protection:  

##  <a name="steps-to-implement-endpoint-protection"></a>Kroki w celu wdrożenia programu Endpoint Protection  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jacek przegląda dostępne informacje o podstawowych pojęciach dotyczących ochrony punktu końcowego w programie Configuration Manager.|Informacje ogólne dotyczące ochrony punktu końcowego, zobacz [Endpoint Protection w programie System Center Configuration Manager](endpoint-protection.md).|  
|Jacek sprawdza i implementuje wymagania wstępne ochrony punktu końcowego.|Aby uzyskać informacje o wymaganiach wstępnych dotyczących ochrony punktu końcowego, zobacz [planowanie Endpoint Protection](../plan-design/planning-for-endpoint-protection.md).|  
|Jan instaluje rolę systemu lokacji Endpoint Protection na serwerze systemu lokacji jeden tylko u góry hierarchii banku Woodgrove.|Aby uzyskać więcej informacji na temat instalowania roli systemu lokacji programu Endpoint Protection można znaleźć w temacie "Wymagania wstępne" w [konfiguracji ochrony punktu końcowego](configure-endpoint-protection.md).|  
|Jacek konfiguruje programu Configuration Manager do korzystania z serwera SMTP do wysyłania wiadomości e-mail dla alertów.<br /><br /> **Uwaga:** Tylko wtedy, gdy chcesz otrzymywać powiadomienia pocztą e-mail, po wygenerowaniu alertu Endpoint Protection, należy skonfigurować serwer SMTP.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie alertów w Endpoint Protection](endpoint-configure-alerts.md).|  
|Jacek tworzy kolekcję urządzeń zawierającą wszystkie komputery i serwery do zainstalowania klienta programu Endpoint Protection. Nadaje jej nazwę **wszystkie komputery chronione przez program Endpoint Protection**.<br /><br /> **Porada:** Nie można skonfigurować alertów dla kolekcji użytkowników.|Aby uzyskać więcej informacji o sposobie tworzenia kolekcji, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Konfiguruje następujące alertów dla kolekcji: <br /><br />(1) **wykrycia złośliwego oprogramowania**: Jan konfiguruje ważność alertu **krytyczny**. <br /><br />(2) **wykryto ten sam typ złośliwego oprogramowania na kilku komputerach** : Jan konfiguruje ważność alertu **krytyczny** i określa, czy alert zostanie wygenerowany, jeśli więcej niż 5 procent komputerów wykryto złośliwe oprogramowanie. <br /><br />(3) **ten sam typ złośliwego oprogramowania są ponownie wykrywane w określonym interwale na komputerze**: Jan konfiguruje ważność alertu **krytyczny** i określa, czy alert zostanie wygenerowany wykryciu złośliwego oprogramowania więcej niż 5 razy w okresie 24 godzin. <br /><br />(4) **Wykryto wiele typów złośliwego oprogramowania na tym samym komputerze w określonym interwale**: Jan konfiguruje ważność alertu **krytyczny** i określa, czy alert zostanie wygenerowany, gdy więcej niż 3 typów złośliwego oprogramowania są generowane w okresie 24 godzin.<br /><br /> Wartość **ważności alertu** wskazuje poziom alertu, który będzie wyświetlany w konsoli programu Configuration Manager i alerty, które otrzyma w wiadomości e-mail.<br /><br /> Ponadto wybiera opcję **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** tak, aby alerty w konsoli programu Configuration Manager może monitorować.|Zobacz "Konfigurowanie alertów dotyczących ochrony punktu końcowego" w [konfigurowaniu ochrony punktu końcowego programu System Center Configuration Manager](endpoint-configure-alerts.md).|  
|Jacek konfiguruje aktualizacje oprogramowania Configuration Manager, aby pobrać i zainstalować aktualizacje definicji trzy razy dziennie, przy użyciu reguły wdrażania automatycznego.|Aby uzyskać więcej informacji, zobacz sekcję "Przy użyciu konfiguracji Menedżera aktualizacji do dostarczenia definicji aktualizacji oprogramowania" w [Użyj Menedżera konfiguracji aktualizacji oprogramowania do dostarczenia aktualizacji](endpoint-definitions-configmgr.md).|  
|Jan sprawdza ustawienia w domyślnych zasadach ochrony przed złośliwym kodem, które zawierają zalecane ustawienia zabezpieczeń firmy Microsoft. Dla komputerów, na których codziennie ma być wykonywane szybkie skanowanie, zmieniane są następujące ustawienia:<br /><br /> (1) **uruchomić codziennego szybkiego skanowania na komputerach klienckich**: **Yes**.<br /><br /> (2) **codzienne szybkie skanowanie zaplanowany termin**:  **9:00 AM**.<br /><br /> Opcja **Aktualizacje dystrybuowane za pomocą usługi Microsoft Update** jest wybrana domyślnie jako źródło aktualizacji definicji. To spełnia wymagania biznesowe, że komputery pobrać aktualizacje definicji z witryny Microsoft Update, gdy nie otrzymają aktualizacje oprogramowania Configuration Manager.|Zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan tworzy kolekcję o nazwie **Serwery banku Woodgrove Bank**, która zawiera tylko serwery banku Woodgrove Bank.|Zobacz [Jak tworzyć kolekcje w programie System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Jan tworzy niestandardowe zasady ochrony przed złośliwym kodem o nazwie **Zasady serwera banku Woodgrove Bank**. Dodaje tylko ustawienia w obszarze **Skany zaplanowane** , wprowadzając następujące zmiany:<br /><br /> **Typ skanowania**:  **Pełna**<br /><br /> **Skanowanie dzień**:  **Sobota**<br /><br /> **Skanowanie czasu**: **1:00:00**<br /><br /> **Uruchom codziennego szybkiego skanowania na komputerach klienckich**:  **No**.|Zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan wdraża niestandardowe zasady ochrony przed złośliwym kodem **Zasady serwera banku Woodgrove Bank** w kolekcji **Serwery banku Woodgrove Bank** .|Zobacz "Aby wdrożyć zasady ochrony przed złośliwym oprogramowaniem na komputerach klienckich" [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection](endpoint-antimalware-policies.md) tematu.|  
|Jan tworzy nowy zestaw klientów niestandardowych ustawień urządzenia dotyczących ochrony punktu końcowego i nazwy te **ustawienia ochrony punktu końcowego banku Woodgrove**.<br /><br /> **Uwaga:** Jeśli nie chcesz zainstalować i włączyć program Endpoint Protection na wszystkich klientach w hierarchii, upewnij się, że opcje **klienta zarządzania Endpoint Protection na komputerach klienckich** i **klienta zainstaluj program Endpoint Protection na komputerach klienckich** obydwa są skonfigurowane jako **nr** w domyślnych ustawieniach klienta.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md).|  
|Konfiguruje następujące ustawienia dla programu Endpoint Protection:<br /><br /> **Zarządzanie klientem programu Endpoint Protection na komputerach klienckich**:  **Tak**<br /><br /> To ustawienie, aby wartość zapewnia, że ewentualny istniejący klient Endpoint Protection, który jest zainstalowany staje się zarządzane przez program Configuration Manager.<br /><br /> **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**:  **Yes**.<br /><br /> **Automatycznie usuwaj wcześniej zainstalowane oprogramowanie chroniące przed złośliwym kodem przed zainstalowaniem programu Endpoint Protection**:  **Yes**.<br /><br /> To ustawienie, aby wartość spełnia wymagania biznesowe usunięcie istniejące oprogramowanie chroniące przed złośliwym kodem, zanim Endpoint Protection jest zainstalowany i włączony.|Aby uzyskać więcej informacji, zobacz [Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection](endpoint-protection-configure-client.md).|  
|Jacek wdraża **ustawienia ochrony punktu końcowego banku Woodgrove** ustawień klienta, aby **wszystkie komputery chronione przez program Endpoint Protection** kolekcji.|Zobacz "Konfigurowanie niestandardowych ustawień klienta programu Endpoint Protection" w [konfigurowaniu ochrony punktu końcowego w programie Configuration Manager](endpoint-antimalware-policies.md).|  
|Jan tworzy zasady w Kreatorze tworzenia zasad zapory systemu Windows, konfigurując następujące ustawienia w profilu domeny:<br /><br /> (1) **Zapora systemu Windows**: **Tak**<br /><br /> 2)<br />                    **Powiadom użytkownika, gdy Zapora systemu Windows zablokuje nowy program**: **Tak**|Zobacz [sposobu tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](../../protect/deploy-use/create-windows-firewall-policies.md)|  
|Jacek wdraża nowe zasady zapory w kolekcji **wszystkie komputery chronione przez program Endpoint Protection** on utworzony wcześniej.|Zobacz "Aby wdrożyć zasady zapory systemu Windows" w [sposób tworzenia i wdrażania zasad zapory systemu Windows dla programu Endpoint Protection w programie System Center Configuration Manager](create-windows-firewall-policies.md)|  
|Jacek korzysta dostępnych zadania zarządzania dla programu Endpoint Protection, aby zarządzać ochrony przed złośliwym oprogramowaniem i zasad zapory systemu Windows, wykonaj skanowanie na żądanie z komputerami, jeśli jest to konieczne, wymusić komputerów, aby pobrać najnowsze definicje i określ dalszych działań do wykonania po wykryciu złośliwego oprogramowania.|Zobacz [jak zarządzać zasadami ochrony przed złośliwym oprogramowaniem i zapory ustawienia Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-firewall.md)|  
|Jacek korzysta z następujących metod do monitorowania stanu ochrony punktu końcowego i akcji wykonywanych przez program Endpoint Protection:<br /><br /> (1) przy użyciu **stanu ochrony punktu końcowego** węzeł w węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego.<br /><br /> (2) za pomocą **Endpoint Protection** w węźle **zasoby i zgodność** obszaru roboczego.<br /><br /> (3) za pomocą wbudowanych programu Configuration Manager raporty.|Zobacz [jak monitorować program Endpoint Protection w programie System Center Configuration Manager](monitor-endpoint-protection.md)|  

 Jacek zgłasza Menedżerowi pomyślnego wdrożenia programu Endpoint Protection i potwierdza, że komputery w banku Woodgrove są teraz chronione przed ochrony przed złośliwym oprogramowaniem, zgodnie z wymagań biznesowych, z których został on podany.

