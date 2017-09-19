---
title: "Właściwości instalacji klienta w usługach domenowych w usłudze Active Directory | Dokumentacja firmy Microsoft"
description: "Użyj właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 73e6b8c39b08bb661cb7ac66dad3c47d4abd09b0
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="about-client-installation-properties-published-to-active-directory-domain-services"></a>Informacje o właściwościach instalacji klienta publikowanych w usługach Active Directory Domain Services

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po rozszerzeniu schematu usługi Active Directory dla programu System Center Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory, wiele właściwości instalacji klienta są publikowane w usługach domenowych w usłudze Active Directory. Jeżeli komputer może zlokalizować te właściwości instalacji klienta, może ich użyć podczas wdrażania klienta programu Configuration Manager.  

 Zalety użycia usług domenowych w usłudze Active Directory w celu publikacji właściwości instalacji klienta są następujące:  

-   Instalacje klienta oparta na punkcie aktualizacji oprogramowania i instalacje klienta zasad grupy nie wymagają parametrów instalacji można skonfigurować na każdym komputerze.  

-   Ponieważ te informacje są generowane automatycznie, eliminuje to ryzyko błędu ludzkiego związanego z ręcznym wprowadzaniem właściwości instalacji.  

> [!NOTE]  
>  Aby uzyskać więcej informacji na temat rozszerzania schematu usługi Active Directory dla programu Configuration Manager oraz publikowania lokacji, zobacz [rozszerzenia schematu dla programu System Center Configuration Manager](../../plan-design/network/schema-extensions.md).  

## <a name="client-installation-properties-published-to-active-directory-domain-services"></a>Właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory  
Poniżej znajduje się lista właściwości instalacji klienta. Aby uzyskać więcej informacji na temat każdego z elementów wymienionych poniżej, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   Kod lokacji programu Configuration Manager.  

-   Certyfikat podpisywania serwera lokacji.  

-   Zaufany klucz główny.  

-   Porty komunikacyjne klienta dla protokołu HTTP i HTTPS.  

-   Rezerwowy punkt stanu. Jeśli lokacja ma kilka rezerwowych punktów stanu, tylko pierwszy z nich została zainstalowana jest publikowana w usługach domenowych w usłudze Active Directory.  

-   Ustawienie oznaczające, że klient musi się komunikować tylko przy użyciu protokołu HTTPS.  

-   Ustawienia dotyczące certyfikatów PKI:  

   -   Określa, czy ma być używany certyfikat PKI klienta.  

   -   Kryteria wyboru certyfikatu. Może to być wymagane, ponieważ klient ma więcej niż jeden ważny certyfikat PKI, który może służyć do programu Configuration Manager.  

   -   Ustawienie określające, który certyfikat ma zostać użyty, jeżeli po zakończeniu procesu wyboru certyfikatu klient ma kilka ważnych certyfikatów.  

   -   Lista wydawców certyfikatów zawierająca zaufane certyfikaty głównego urzędu certyfikacji.  

-   Właściwości instalacji pliku Client.msi określone na karcie **Klient** w oknie dialogowym **Właściwości instalacji klienta w trybie push** .

Instalacja klienta (CCMSetup) wykorzystuje właściwości, które są publikowane w usługach domenowych w usłudze Active Directory, tylko wtedy, gdy nie innych są określone właściwości przy użyciu jednej z następujących czynności:  

-   Metoda instalacji ręcznej (opisane w dalszej części tego artykułu)

-   Metody instalacji zasad grupy (opisane w dalszej części tego artykułu)

> [!NOTE]  
>  Właściwości instalacji klienta służą do instalowania klienta. Te właściwości mogą zastąpione nowymi ustawieniami z przypisanej do niego lokacji po zainstalowaniu klienta i jego pomyślnym przypisaniu do lokacji programu Configuration Manager.  

 Użyj szczegółowe informacje w poniższych sekcjach, aby określić, które metody instalacji klienta programu Configuration Manager używać usług domenowych w usłudze Active Directory w celu uzyskania właściwości instalacji klienta.  

## <a name="client-push-installation"></a>Wypychana instalacja klienta  
 Wypychana instalacja klienta nie korzysta z usług domenowych w usłudze Active Directory w celu uzyskania właściwości instalacji.  

 Zamiast tego można określić właściwości instalacji klienta w **klienta** karcie **właściwości instalacji wypychanej klienta** okno dialogowe. Te opcje i ustawienia lokacji dotyczące klienta są przechowywane w pliku odczytywanym przez klienta podczas instalacji.  

> [!NOTE]  
>  Na karcie **Klient** nie jest konieczne określanie żadnych właściwości CCMSetup instalacji wypychanej klienta, rezerwowego punkt stanu ani zaufanego klucza głównego. Te ustawienia są automatycznie udostępniane klientom w przypadku ich instalacji wypychanej.  

 Wszystkie właściwości, które określisz w **klienta** karcie są publikowane w usługach domenowych w usłudze Active Directory, jeśli lokacja jest opublikowana w usługach domenowych w usłudze Active Directory. Te ustawienia są odczytywane przez instalacje klientów po uruchomieniu programu CCMSetup bez właściwości instalacji.  

## <a name="software-update-point-based-installation"></a>Instalacja oparta na punkcie aktualizacji oprogramowania  
 Metoda instalacji oparta na punkcie aktualizacji oprogramowania nie obsługuje dodawania właściwości instalacji do wiersza polecenia programu CCMSetup.  

 Jeżeli nie udostępniono właściwości wiersza polecenia na komputerze klienckim, używając zasad grupy, program CCMSetup wyszukuje właściwości instalacji w usługach domenowych w usłudze Active Directory.  

## <a name="group-policy-installation"></a>Instalacja zasad grupy  
 Metoda instalacji wykorzystująca zasady grupy nie obsługuje dodawania właściwości instalacji do wiersza polecenia programu CCMSetup.  

 Jeżeli nie udostępniono właściwości wiersza polecenia na komputerze klienckim, program CCMSetup wyszukuje właściwości instalacji w usługach domenowych w usłudze Active Directory.  

## <a name="manual-installation"></a>Instalacja ręczna  
 Program CCMSetup wyszukuje w usługach domenowych w usłudze Active Directory właściwości instalacji w następujących okolicznościach:  

-   Nie określono właściwości wiersza polecenia po poleceniu CCMSetup.exe.  

-   Komputerowi nie zostały udostępnione właściwości instalacji przy użyciu zasad grupy.  

## <a name="logon-script-installation"></a>Instalacja skryptu logowania  
 Program CCMSetup wyszukuje w usługach domenowych w usłudze Active Directory właściwości instalacji w następujących okolicznościach:  

-   Nie określono właściwości wiersza polecenia po poleceniu CCMSetup.exe.  

-   Komputerowi nie zostały udostępnione właściwości instalacji przy użyciu zasad grupy.  

## <a name="software-distribution-installation"></a>Instalacja dystrybucji oprogramowania  
 Program CCMSetup wyszukuje w usługach domenowych w usłudze Active Directory właściwości instalacji w następujących okolicznościach:  

-   Nie określono właściwości wiersza polecenia po poleceniu CCMSetup.exe.  

-   Komputerowi nie zostały udostępnione właściwości instalacji przy użyciu zasad grupy.  

## <a name="installations-for-clients-that-cannot-access-active-directory-domain-services"></a>Instalacje w przypadku klientów, których nie można uzyskać dostępu do usług domenowych w usłudze Active Directory  
Te komputery klienckie nie może odczytać lub uzyskać dostępu do opublikowanych właściwości instalacji z usług domenowych w usłudze Active Directory.

 Ci klienci obejmują:  

-   Komputery grupy roboczej.  

-   Klienci, którzy są przypisane do lokacji programu Configuration Manager, który nie jest opublikowana w usługach domenowych w usłudze Active Directory.  

-   Klienci, którzy są instalowane, gdy są one połączone z Internetem.  
