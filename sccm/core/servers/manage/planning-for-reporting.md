---
title: Planowanie raportowania | Dokumentacja firmy Microsoft
description: "Z szczegóły instalacji zabezpieczeń i przepustowości sieci warto planowanie raportowania w programie Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ff920c84-d5c8-458c-b67f-bc7219b05690
caps.latest.revision: "6"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 119f501057bf44e483be31db20b88326b3d05ebb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="planning-for-reporting-in-system-center-configuration-manager"></a>Planowanie raportowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Raportowanie w programie System Center Configuration Manager udostępnia zestaw narzędzi i zasobów, które ułatwiają korzystanie z zaawansowanych możliwości raportowania usług SQL Server Reporting Services. Użyj następujące sekcje zawierają informacje ułatwiające planowanie raportowania w programie Configuration Manager.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> Określenie miejsca instalacji punktu usług raportowania  
 Po uruchomieniu raportów programu Configuration Manager w lokacji mają dostęp do informacji w bazie danych lokacji, z którą się łączą. W poniższych sekcjach znajdują się informacje ułatwiające określenie używanego źródła danych oraz miejsca instalacji punktu usług raportowania.  

> [!NOTE]  
>  Aby uzyskać więcej informacji o planowaniu systemów lokacji w programie Configuration Manager, zobacz [Dodaj role systemu lokacji](../deploy/configure/add-site-system-roles.md).  

###  <a name="BKMK_SupportedSiteServers"></a> Obsługiwane serwery systemu lokacji  
 Punkt usług raportowania można zainstalować w centralnej lokacji administracyjnej i lokacjach głównych, jak również w wielu systemach lokacji w lokacji oraz w innych lokacjach w hierarchii. Punkt usług raportowania nie jest obsługiwany w lokacjach dodatkowych. Pierwszy punkt usług raportowania w lokacji jest skonfigurowany jako domyślny serwer raportów. Można dodać więcej punktów usług raportowania w lokacji, ale domyślny serwer raportów każdej lokacji jest aktywnie używany dla raportów programu Configuration Manager. Punkt usług raportowania można zainstalować na serwerze lokacji lub zdalnym systemie lokacji. Jednak ze względu na wydajność najlepszym rozwiązaniem jest używanie usług raportowania na serwerze zdalnego systemu lokacji.  

###  <a name="BKMK_DataReplication"></a> Uwagi dotyczące replikacji danych  
 Menedżer konfiguracji klasyfikuje dane replikowane jako dane globalne lub dane lokacji. Dane globalne dotyczą obiektów, które zostały utworzone przez użytkowników administracyjnych i które są replikowane do wszystkich lokacji w hierarchii. Lokacje dodatkowe odbierają tylko podzestaw danych globalnych. Przykłady danych globalnych to między innymi wdrożenia oprogramowania, aktualizacje oprogramowania, kolekcje oraz zakresy zabezpieczeń administracji opartej na rolach. Dane lokacji odwołuje się do informacji operacyjnych tej lokacji podstawowej programu Configuration Manager i klienci, którzy utworzyć raport do lokacji głównych. Dane lokacji są replikowane do centralnej lokacji administracyjnej, ale nie do innych lokacji głównych. Przykłady danych lokacji to między innymi dane dotyczące zapasów sprzętu, komunikaty o stanie, alerty i wyniki kolekcji opartych na kwerendach. Dane lokacji są widoczne tylko w centralnej lokacji administracyjnej i lokacji głównej, z której pochodzą dane.  

 Aby ułatwić określenie miejsca instalacji punktu usług raportowania, należy wziąć pod uwagę poniższe kwestie:  

-   Punkt usług raportowania z bazy danych witryny Administracja centralna źródłem danych raportowania ma dostęp do wszystkich globalnych i danych lokacji w hierarchii programu Configuration Manager. Jeśli są wymagane raporty zawierające dane lokacji w wielu lokacjach w hierarchii, należy wziąć pod uwagę instalowania usług raportowania punkt w systemie lokacji w centralnej lokacji administracyjnej, a jako źródła danych raportowania użyć bazy witryny Administracja centralna.  

-   Punkt usług raportowania, którego źródłem danych raportowania jest baza danych podrzędnej lokacji głównej, ma dostęp do danych globalnych i danych lokacji wyłącznie lokalnej lokacji głównej i wszystkich podrzędnych lokacji dodatkowych. Dane lokacji innych lokacji głównych w hierarchii programu Configuration Manager nie są replikowane do lokacji głównej i w związku z tym usług Reporting Services nie można do niego dostęp. Jeśli wymagane raporty zawierające dane konkretnej lokacji głównej lokacji lub danych globalnych, ale nie chcesz, aby użytkownik raportu miał dostęp do danych z innych lokacji głównych, zainstaluj punkt usług raportowania w systemie lokacji w lokacji głównej i użyj bazy danych lokacji głównej jako źródła danych raportowania.  

###  <a name="BKMK_NetworkBandwidth"></a> Uwagi dotyczące przepustowości sieci  
 W zależności od konfiguracji lokacji serwery systemu lokacji z tej samej lokacji komunikują się ze sobą za pomocą bloków komunikatów serwera (SMB), protokołu HTTP lub protokołu HTTPS. Ponieważ ta komunikacja nie jest zarządzana i może się odbywać w dowolnym czasie bez kontroli przepustowości sieci, przed zainstalowaniem roli punktu usług raportowania w systemie lokacji należy sprawdzić dostępną przepustowość sieci.  

> [!NOTE]  
>  Aby uzyskać więcej informacji o planowaniu systemów lokacji, zobacz [Dodaj role systemu lokacji](../deploy/configure/add-site-system-roles.md).  

##  <a name="BKMK_RoleBaseAdministration"></a> Planowanie administracji opartej na rolach dla raportów  
 Zabezpieczenia raportów są podobne jak w przypadku innych obiektów w programie Configuration Manager można przypisywać role zabezpieczeń i uprawnienia użytkownikom administracyjnym. Użytkownicy administracyjni mogą uruchamiać i modyfikować tylko te raporty, względem których mają odpowiednie uprawnienia zabezpieczeń. Aby uruchamiać raporty w konsoli programu Configuration Manager, musisz mieć **odczytu** prawa do **lokacji** uprawnień oraz mieć skonfigurowane uprawnienia dotyczące konkretnych obiektów.  

 Jednak w przeciwieństwie do innych obiektów w programie Configuration Manager prawa zabezpieczeń, które można ustawić dla użytkowników administracyjnych w konsoli programu Configuration Manager należy również skonfigurować w usługach Reporting Services. Podczas konfigurowania uprawnień zabezpieczeń w konsoli programu Configuration Manager, punkt usług raportowania łączy się z usługami raportowania i ustawia odpowiednie uprawnienia dostępu do raportów. Na przykład z rolą zabezpieczeń **Menedżer aktualizacji oprogramowania** są skojarzone uprawnienia **Uruchom raport** i **Modyfikuj raport** . Użytkownicy administracyjni, którzy mają przypisaną tylko rolę **Menedżer aktualizacji oprogramowania** , mogą uruchamiać i modyfikować wyłącznie raporty dotyczące aktualizacji oprogramowania. Raporty dotyczące innych obiektów nie są wyświetlane w konsoli programu Configuration Manager. Wyjątkiem jest to, że niektóre raporty nie są skojarzone z określonym obiektów zabezpieczanych programu Configuration Manager. W przypadku takich raportów użytkownik administracyjny musi mieć uprawnienie **Odczytaj** dotyczące **Lokacji** , aby uruchamiać raporty, oraz uprawnienie **Modyfikuj** dotyczące **Lokacji** , aby modyfikować raporty.  

 Raporty są włączone w pełnym zakresie dla administracji opartej na rolach. Dane dla wszystkich raportów uwzględnionych w programie Configuration Manager są filtrowane zgodnie z uprawnieniami użytkownika administracyjnego, który uruchamia raport. Użytkownicy administracyjni z określonymi rolami mogą wyświetlać tylko informacje zdefiniowane dla ich ról.  

 Aby uzyskać więcej informacji o uprawnieniach zabezpieczeń dotyczących raportowania patrz [Konfiguruj raportowanie](configuring-reporting.md).  

 Aby uzyskać więcej informacji na temat administracji opartej na rolach w programie Configuration Manager, zobacz [Konfigurowanie administracji opartej na rolach](../deploy/configure/configure-role-based-administration.md).  

## <a name="next-steps"></a>Następne kroki  
 Użyj następujących dodatkowe tematy ułatwiające planowanie raportowania w programie Configuration Manager:  

-   [Wymagania wstępne dotyczące raportowania w programie System Center Configuration Manager](../../../core/servers/manage/prerequisites-for-reporting.md)  
-   [Najlepsze rozwiązania w zakresie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/best-practices-for-reporting.md)  
