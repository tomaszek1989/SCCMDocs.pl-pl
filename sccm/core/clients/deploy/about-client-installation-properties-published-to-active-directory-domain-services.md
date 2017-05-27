---
title: "Właściwości instalacji klienta w usługach domenowych w usłudze Active Directory | Dokumentacja firmy Microsoft"
description: "Użyj właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 744bc3792a02f13d3cf940cd1a4f2fd8749ee2f4
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-installation-properties-published-to-active-directory-domain-services"></a>Informacje o właściwościach instalacji klienta publikowanych w usługach Active Directory Domain Services

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po rozszerzeniu schematu usługi Active Directory dla programu System Center Configuration Manager, a lokacja jest opublikowana w usługach domenowych w usłudze Active Directory, wiele właściwości instalacji klienta są publikowane w usługach domenowych w usłudze Active Directory. Jeżeli komputer może zlokalizować te właściwości instalacji klienta, może ich użyć podczas wdrażania klienta programu Configuration Manager.  

 Zalety użycia usług domenowych w usłudze Active Directory w celu publikacji właściwości instalacji klienta są następujące:  

-   Instalacje klientów oparta na punkcie aktualizacji oprogramowania i instalacje klienta zasad grupy nie wymagają parametrów instalacji można skonfigurować na każdym komputerze.  

-   Ponieważ te informacje są generowane automatycznie, eliminuje to ryzyko błędu ludzkiego związanego z ręcznym wprowadzaniem właściwości instalacji.  

> [!NOTE]  
>  Aby uzyskać więcej informacji na temat rozszerzania schematu usługi Active Directory dla programu Configuration Manager oraz publikowania lokacji zobacz [rozszerzenia schematu dla programu System Center Configuration Manager](../../plan-design/network/schema-extensions.md).  

## <a name="client-installation-properties-published-to-active-directory-domain-services"></a>Właściwości instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory  
Oto lista właściwości instalacji klienta. Aby uzyskać więcej informacji o każdym elemencie wymienione poniżej, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   Kod lokacji programu Configuration Manager.  

-   Certyfikat podpisywania serwera lokacji.  

-   Zaufany klucz główny.  

-   Porty komunikacyjne klienta dla protokołu HTTP i HTTPS.  

-   Rezerwowy punkt stanu. Jeżeli lokacja ma kilka rezerwowych punktów stanu, tylko pierwszy z nich zainstalowany jest opublikowana w usługach domenowych w usłudze Active Directory.  

-   Ustawienie oznaczające, że klient musi się komunikować tylko przy użyciu protokołu HTTPS.  

-   Ustawienia dotyczące certyfikatów PKI:  

   -   Określa, czy ma być używany certyfikat PKI klienta.  

   -   Kryteria wyboru certyfikatu. Może to być wymagane, ponieważ klient ma więcej niż jeden ważny certyfikat PKI, który może służyć do programu Configuration Manager.  

   -   Ustawienie określające, który certyfikat ma zostać użyty, jeżeli po zakończeniu procesu wyboru certyfikatu klient ma kilka ważnych certyfikatów.  

   -   Lista wydawców certyfikatów zawierająca zaufane certyfikaty głównego urzędu certyfikacji.  

-   Właściwości instalacji pliku Client.msi określone na karcie **Klient** w oknie dialogowym **Właściwości instalacji klienta w trybie push** .

Instalacja klienta (CCMSetup) wykorzystuje właściwości, które są publikowane w usługach domenowych w usłudze Active Directory, tylko wtedy, gdy nie inne są określone właściwości przy użyciu jednej z następujących czynności:  

-   Metoda instalacji ręcznej (opisane w dalszej części tego artykułu)

-   Metoda instalacji zasad grupy (opisane w dalszej części tego artykułu)

> [!NOTE]  
>  Właściwości instalacji klienta służą do instalowania klienta. Te właściwości mogą zostać zastąpione nowymi ustawieniami z przypisanej lokacji, po zainstalowaniu klienta i jego pomyślnym przypisaniu do lokacji programu Configuration Manager.  

 Użyj szczegółowe informacje w poniższych sekcjach, aby ustalić, które metody instalacji klienta programu Configuration Manager usług domenowych w usłudze Active Directory w celu uzyskania właściwości instalacji klienta.  

## <a name="client-push-installation"></a>Wypychana instalacja klienta  
 Wypychana instalacja klienta nie korzysta z usług domenowych w usłudze Active Directory w celu uzyskania właściwości instalacji.  

 Zamiast tego można określić właściwości instalacji klienta w **klienta** na karcie **właściwości instalacji wypychanej klienta** okno dialogowe. Te opcje i ustawienia lokacji dotyczące klienta są przechowywane w pliku odczytywanym przez klienta podczas instalacji.  

> [!NOTE]  
>  Na karcie **Klient** nie jest konieczne określanie żadnych właściwości CCMSetup instalacji wypychanej klienta, rezerwowego punkt stanu ani zaufanego klucza głównego. Te ustawienia są automatycznie udostępniane klientom w przypadku ich instalacji wypychanej.  

 Wszystkie właściwości, które są określone w **klienta** kartę są publikowane w usługach domenowych w usłudze Active Directory, jeśli lokacja jest opublikowana w usługach domenowych w usłudze Active Directory. Te ustawienia są odczytywane przez instalacje klientów po uruchomieniu programu CCMSetup bez właściwości instalacji.  

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

## <a name="installations-for-clients-that-cannot-access-active-directory-domain-services"></a>Instalacje w przypadku klientów, którzy nie mogą uzyskać dostęp do usług domenowych w usłudze Active Directory  
Te komputery klienckie nie może odczytać lub uzyskać dostęp do opublikowanych właściwości instalacji z usług domenowych w usłudze Active Directory.

 Ci klienci są:  

-   Komputery grupy roboczej.  

-   Klienci, którzy są przypisane do lokacji programu Configuration Manager, który nie jest publikowana w usługach domenowych w usłudze Active Directory.  

-   Klienci, którzy są instalowane, gdy są one połączone z Internetem.  

