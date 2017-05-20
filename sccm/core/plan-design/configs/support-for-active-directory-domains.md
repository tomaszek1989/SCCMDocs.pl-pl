---
title: "Obsługiwane w domenach usługi Active Directory | Dokumentacja firmy Microsoft"
description: "Pobierz wymagania dotyczące członkostwa systemu lokacji programu System Center Configuration Manager w domenie usługi Active Directory."
ms.custom: na
ms.date: 3/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f397efe458fd85124d2a83d4a869642015fd4a5
ms.openlocfilehash: 2654ab4eaaaf6a4bf3bd7dca9908e7033647dc2c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-active-directory-domains-for-system-center-configuration-manager"></a>Obsługiwane domeny usługi Active Directory dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wszystkie systemy lokacji programu System Center Configuration Manager muszą być członkami obsługiwanych domeny usługi Active Directory systemu Windows Server. Komputery klienckie programu Configuration Manager może być członków domeny lub grupy roboczej.  

 **Wymagania i ograniczenia:**  

-   Członkostwo w domenie mają zastosowanie do systemów lokacji obsługujących zarządzanie klientami w sieci obwodowej (znanej także jako strefa DMZ, strefą zdemilitaryzowaną i podsiecią ekranowaną).  

-   Nie jest obsługiwane dla komputera, który jest hostem roli systemu lokacji następujące zmiany:  

    -   Członkostwo w domenie  

    -   Nazwa domeny  

    -   Nazwa komputera  

Rola systemu lokacji (łącznie lokacji, jeśli jest serwerem lokacji) należy odinstalować przed wprowadzeniem tych zmian.  

**Obsługiwane są domeny z następującymi poziomami funkcjonalności domeny:**  
- Windows Server 2016

- Windows Server 2012 R2  

- Windows Server 2012

- Windows Server 2008 R2

- Windows Server 2008  







##  <a name="bkmk_Disjoint"></a> Rozłączne przestrzenie nazw  
Program Configuration Manager obsługuje instalowanie systemów lokacji i klientów w domenie, która ma rozłącznego obszaru nazw.  

Scenariusz rozłącznego obszaru nazw jest jeden w którym sufiksu podstawowej domeny systemu nazw domen (DNS) komputera nie pasuje do nazwy domeny DNS usługi Active Directory, w których znajduje się ten komputer. Komputera, który używa główny sufiks DNS, która nie jest zgodna jest określany jako odłączony. Inny scenariusz rozłączna przestrzeń nazw występuje, jeśli nazwa domeny NetBIOS kontrolera domeny nie pasuje do nazwy domeny DNS usługi Active Directory.  

Poniższa tabela zawiera informacje o obsługiwanych scenariuszach rozłącznej przestrzeni nazw.  

|Scenariusz|Więcej informacji|  
|--------------|----------------------|  
|**Scenariusz 1:**<br /><br /> Sufiks podstawowej domeny DNS kontrolera domeny różni się od nazwy domeny DNS usługi Active Directory. Komputery należące do domeny mogą być rozłączne lub nierozłączne.|W tym scenariuszu sufiks podstawowej domeny DNS kontrolera domeny różni się od nazwy domeny DNS usługi Active Directory. W tym scenariuszu kontroler domeny jest rozłączny. Komputery należące do domeny, na przykład komputery i serwery lokacji, mogą mieć sufiks podstawowej domeny DNS, który jest zgodny z sufiksem podstawowej domeny DNS kontrolera domeny lub jest zgodny z nazwą domeny DNS usługi Active Directory.|  
|**Scenariusz 2:**<br /><br /> Komputer należący do domeny usługi Active Directory jest rozłączny, nawet jeśli kontroler domeny nie jest rozłączny.|W tym scenariuszu sufiks podstawowej domeny DNS komputera członkowskiego, na którym jest zainstalowany system lokacji, różni się od nazwy domeny DNS usługi Active Directory, chociaż sufiks podstawowej domeny DNS kontrolera domeny jest taki sam jak nazwa domeny DNS usługi Active Directory. W tym scenariuszu kontroler domeny nie jest rozłączny, a komputer członkowski jest rozłączny. Element członkowski komputerach klienta programu Configuration Manager może mieć podstawowy sufiks DNS, która odpowiada sufiksu podstawowej domeny DNS serwera systemu lokacji rozłącznego lub zgodny z nazwą domeny DNS usługi Active Directory.|  

 Aby umożliwić komputerowi dostęp do kontrolerów domeny, które są rozłączne, musisz zmienić atrybut **msDS-AllowedDNSSuffixes** usługi Active Directory dla kontenera obiektu domeny. Należy dodać zarówno sufiksy DNS do atrybutu.  

 Ponadto aby upewnić się, że lista wyszukiwania sufiksów DNS zawiera wszystkie przestrzenie nazw DNS wdrożonych w organizacji, należy skonfigurować listy wyszukiwania dla każdego komputera w domenie, która jest odłączony. Upewnij się, są następujące obszary nazw na liście: sufiksu podstawowej domeny DNS kontrolera domeny, nazwa domeny DNS i wszelkie dodatkowe przestrzenie nazw dla innych serwerów, które program Configuration Manager może współpracować z. **Listę wyszukiwania sufiksów DNS** możesz skonfigurować za pomocą konsoli zarządzania zasadami grupy.  

> [!IMPORTANT]  
>  Gdy odwołujesz komputera w programie Configuration Manager, wprowadź komputera przy użyciu jego sufiks podstawowej domeny DNS. Ten sufiks powinny odpowiadać w pełni kwalifikowanej nazwy domeny, który jest zarejestrowany jako **dnsHostName** atrybutu w domenie usługi Active Directory i głównej nazwy usługi skojarzonej z systemem.  

##  <a name="bkmk_SLD"></a> Domeny z nazwą bez rozszerzenia  
 Programu Configuration Manager obsługuje systemów lokacji i klientów w domenie pojedynczej etykiecie, gdy są spełnione następujące warunki:  

-   Domeny pojedynczej etykiecie w usługach domenowych w usłudze Active Directory musi być skonfigurowany z rozłącznego obszaru nazw DNS, który ma prawidłową domenę najwyższego poziomu.  

     **Na przykład:** Domeny pojedynczej etykiecie Contoso jest skonfigurowana z rozłącznego obszaru nazw w systemie DNS contoso.com. W związku z tym gdy określono sufiks DNS w programie Configuration Manager na komputerze w domenie firmy Contoso, należy określić "ciąg Contoso.com" i nie "Contoso".  

-   Obiekt modelu DCOM (Distributed Component) połączeń między serwerami lokacji w kontekście systemu konieczne jest pomyślne przy użyciu uwierzytelniania Kerberos.  

