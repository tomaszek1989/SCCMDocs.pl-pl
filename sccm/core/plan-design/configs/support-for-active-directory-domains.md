---
title: "Obsługiwane domeny usługi Active Directory"
titleSuffix: Configuration Manager
description: "Pobierz wymagania dotyczące członkostwa systemu lokacji programu System Center Configuration Manager w domenie usługi Active Directory."
ms.custom: na
ms.date: 9/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d4862a3354717a603535b6ad0de42f24c67cc314
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="supported-active-directory-domains-for-system-center-configuration-manager"></a>Obsługiwane domeny usługi Active Directory dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wszystkie systemy lokacji programu System Center Configuration Manager muszą być elementami członkowskimi obsługiwanej domeny usługi Active Directory systemu Windows Server. Komputery klienckie programu Configuration Manager może być członkami domeny lub grupy roboczej.  

 **Wymagania i ograniczenia:**  

-   Członkostwo w domenie dotyczy systemów lokacji, które obsługują zarządzanie klientami internetowymi w sieci obwodowej (znanej także jako strefa DMZ, strefą zdemilitaryzowaną i podsiecią ekranowaną).  

-   Zmień następujące dla komputera, na którym jest uruchomiona rola systemu lokacji nie jest obsługiwana:  

    -   Członkostwo w domenie *(dotyczy to również usunięcie systemu lokacji znajdują się w domenie i ponowne przyłączanie tej samej domenie.)*

    -   Nazwa domeny  

    -   Nazwa komputera  

Przed wprowadzeniem tych zmian należy odinstalować rolę systemu lokacji (łącznie z lokacją, jeśli jest to serwer lokacji).  

**Obsługiwane są domeny z następującymi poziomami funkcjonalności domeny:**  
- Windows Server 2016

- Windows Server 2012 R2  

- Windows Server 2012

- Windows Server 2008 R2

- Windows Server 2008  







##  <a name="bkmk_Disjoint"></a> Rozłączne przestrzenie nazw  
Program Configuration Manager obsługuje instalowanie systemów lokacji i klientów w domenie z rozłączną przestrzenią nazw.  

Scenariuszu rozłącznej przestrzeni nazw jest jednym w którym sufiks podstawowej domeny systemu nazw domen (DNS, Domain Name System) komputera nie pasuje do nazwy domeny DNS usługi Active Directory, w której znajduje się tego komputera. Komputera, który używa główny sufiks DNS, który nie jest zgodny, jest określany jako rozłączny. Innym scenariuszu rozłącznej przestrzeni nazw występuje, jeśli nazwa domeny NetBIOS kontrolera domeny nie pasuje do nazwy domeny DNS usługi Active Directory.  

Poniższa tabela zawiera informacje o obsługiwanych scenariuszach rozłącznej przestrzeni nazw.  

|Scenariusz|Więcej informacji|  
|--------------|----------------------|  
|**Scenariusz 1:**<br /><br /> Sufiks podstawowej domeny DNS kontrolera domeny różni się od nazwy domeny DNS usługi Active Directory. Komputery należące do domeny mogą być rozłączne lub nierozłączne.|W tym scenariuszu sufiks podstawowej domeny DNS kontrolera domeny różni się od nazwy domeny DNS usługi Active Directory. W tym scenariuszu kontroler domeny jest rozłączny. Komputery należące do domeny, na przykład komputery i serwery lokacji, mogą mieć sufiks podstawowej domeny DNS, który jest zgodny z sufiksem podstawowej domeny DNS kontrolera domeny lub jest zgodny z nazwą domeny DNS usługi Active Directory.|  
|**Scenariusz 2:**<br /><br /> Komputer należący do domeny usługi Active Directory jest rozłączny, nawet jeśli kontroler domeny nie jest rozłączny.|W tym scenariuszu sufiks podstawowej domeny DNS komputera członkowskiego, na którym jest zainstalowany system lokacji, różni się od nazwy domeny DNS usługi Active Directory, chociaż sufiks podstawowej domeny DNS kontrolera domeny jest taki sam jak nazwa domeny DNS usługi Active Directory. W tym scenariuszu kontroler domeny nie jest rozłączny, a komputer członkowski jest rozłączny. Komputery członkowskie z systemem klienta programu Configuration Manager może mieć główny sufiks DNS, który jest zgodny sufiks podstawowej domeny DNS rozłącznego serwera systemu lokacji lub jest zgodny z nazwą domeny DNS usługi Active Directory.|  

 Aby umożliwić komputerowi dostęp do kontrolerów domeny, które są rozłączne, musisz zmienić atrybut **msDS-AllowedDNSSuffixes** usługi Active Directory dla kontenera obiektu domeny. Należy dodać oba sufiksy DNS do atrybutu.  

 Ponadto aby upewnić się, że lista wyszukiwania sufiksów DNS zawiera wszystkie nazw DNS, które są wdrażane w organizacji, należy skonfigurować listę wyszukiwania dla każdego komputera w domenie, która jest rozłączna. Upewnij się, Uwzględnij następujące elementy na liście przestrzeni nazw: sufiks podstawowej domeny DNS kontrolera domeny, nazwę domeny DNS i wszelkie dodatkowe przestrzenie nazw innych serwerów, które programu Configuration Manager mogą współpracować ze. **Listę wyszukiwania sufiksów DNS** możesz skonfigurować za pomocą konsoli zarządzania zasadami grupy.  

> [!IMPORTANT]  
>  W przypadku odwoływania się do komputera w programie Configuration Manager, należy wprowadzić komputera przy użyciu jego sufiks podstawowej domeny DNS. Ten sufiks powinien być zgodny w pełni kwalifikowanej nazwy domeny, który jest zarejestrowany jako **dnsHostName** atrybutu w domenie usługi Active Directory oraz główną nazwą usługi skojarzoną z systemem.  

##  <a name="bkmk_SLD"></a> Domeny z nazwą bez rozszerzenia  
 Program Configuration Manager obsługuje systemy lokacji i klientów w domenie o pojedynczej etykiecie, gdy są spełnione poniższe kryteria:  

-   Domena nazwą bez rozszerzenia w usługach domenowych w usłudze Active Directory musi być skonfigurowany z rozłącznego obszaru nazw DNS, który ma prawidłową domenę najwyższego poziomu.  

     **Na przykład:** Domena nazwą bez rozszerzenia contoso skonfigurowano do rozłącznego obszaru nazw w systemie DNS contoso.com. W związku z tym podczas określania sufiksu DNS w programie Configuration Manager na komputerze w domenie Contoso, należy określić "Contoso.com", a nie "Contoso".  

-   Połączenia Distributed Component Object Model (DCOM) między serwerami lokacji w kontekście systemu musi być pomyślnie za pomocą uwierzytelniania Kerberos.  
