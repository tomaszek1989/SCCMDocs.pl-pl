---
title: Testowy klient uaktualnia kolekcji przedprodukcyjnej | Dokumentacja firmy Microsoft
description: Testowanie uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 572ef13883f7930e69ec1f1f53c9bfe029898c81
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-test-client-upgrades-in-a-pre-production-collection-in-system-center-configuration-manager"></a>Jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można przetestować nową wersję klienta programu Configuration Manager w kolekcji przedprodukcyjnej przed uaktualnieniem reszty witryny z nim.  Gdy to zrobisz, są uaktualniane tylko te urządzenia, które są częścią Kolekcja testów. Gdy już mieli Państwo okazję do testowania klienta, możesz podwyższyć poziom klienta, który udostępnia nową wersję oprogramowania klienckiego do pozostałych lokacji.

> [!NOTE]
> Wspieranie klienta testów do produkcji, użytkownik musi być zalogowany jako użytkownika z rolą zabezpieczeń **administrator o pełnych uprawnieniach** i zakres zabezpieczeń **wszystkich**. Aby uzyskać więcej informacji, zobacz [podstawy administracji opartej na rolach](/sccm/core/understand/fundamentals-of-role-based-administration). Również użytkownik musi być zalogowany do serwera połączone z centralnej lokacji administracyjnej lub lokacji głównej autonomiczny najwyższego poziomu.

 Istnieją 3 podstawowe kroki, aby klienci w produkcji wstępnej.  

1.  Skonfiguruj automatyczne uaktualnienia klienta należy używać kolekcji przedprodukcyjnej.  

2.  Zainstaluj aktualizację programu Configuration Manager, która obejmuje nową wersję klienta.  

3.  Przyczyniają się do nowego klienta do środowiska produkcyjnego.  

##  <a name="to-configure-automatic-client-upgrades-to-use-a-pre-production-collection"></a>Aby skonfigurować automatyczne uaktualnienia klienta należy używać kolekcji przedprodukcyjnej  

1. [Konfigurowanie kolekcji](..\collections\create-collections.md) zawierający komputerów do wdrożenia klienta przedprodukcyjnego do. Nie dołączaj komputerów grupy roboczej w kolekcji przedprodukcyjnej. Aby uzyskać dostęp do pakietu klienta przedprodukcyjnego nie mogą używać uwierzytelniania wymagane dla punktu dystrybucji.   

1.  W konsoli programu Configuration Manager Otwórz **Administracja** > **konfiguracja lokacji** > **witryny**i wybierz polecenie **ustawienia hierarchii**.  

     Na karcie **Uaktualnienie klienta** obszaru **Właściwości ustawień hierarchii**:  

    -   Wybierz pozycję **Uaktualnij automatycznie wszystkich klientów w kolekcji przedprodukcyjnej przy użyciu klienta przedprodukcyjnego**  

    -   Wprowadź nazwę kolekcji, która ma być używana jako kolekcja środowiska przedprodukcyjnego.  

![Testowanie uaktualnienia klienta](media/test-client-upgrades.png)

>[!NOTE]
>Aby zmienić te ustawienia, Twoje konto musi być członkiem **administrator o pełnych uprawnieniach** rolę zabezpieczeń i **wszystkie** zakresu zabezpieczeń.


##  <a name="to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a>Instalowanie aktualizacji programu Configuration Manager, która obejmuje nową wersję klienta  

1.  W konsoli programu Configuration Manager, otwórz **Administracja** > **aktualizacji i obsługi**, wybierz opcję **dostępne** aktualizacji, a następnie wybierz **zainstalować pakiet aktualizacji**. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.)

     Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md)  

2.  Podczas instalacji aktualizacji na **opcje klienta** w kreatorze Wybierz **testu w kolekcji przedprodukcyjnej**.  

3.  Wykonaj pozostałe kroki kreatora i zainstaluj pakiet aktualizacji.  

     Po ukończeniu pracy kreatora rozpocznie się wdrażanie zaktualizowanego klienta na klientach w kolekcji środowiska przedprodukcyjnego. Wdrożenia uaktualnionych klientów można monitorować w sekcji **Monitorowanie** > **Stan klienta** > **Przedprodukcyjne wdrożenie klienta**. Aby uzyskać więcej informacji, zobacz [Jak monitorować stan wdrażania klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/monitor-client-deployment-status.md).

    > [!NOTE]
    > Stan wdrożenia na komputerach obsługujących ról systemu lokacji w kolekcji przedprodukcyjnej może być zgłaszany jako **niezgodnych** nawet jeśli klient został pomyślnie wdrożony. W przypadku podwyższania poziomu klienta do produkcji stan wdrożenia jest zgłaszany prawidłowo.

##  <a name="to-promote-the-new-client-to-production"></a>Podwyższenie poziomu nowego klienta do środowiska produkcyjnego  

1.  W konsoli programu Configuration Manager, otwórz **Administracja** > **aktualizacji i obsługi**i wybierz polecenie **podwyższyć klienta przedprodukcyjnego**. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.)

    > [!TIP]
    > Przycisk **Podwyższ poziom przedprodukcyjnego klienta** jest też dostępny w przypadku monitorowania wdrożeń klienta w konsoli w pozycji **Monitorowanie** > **Stan klienta** > **Przedprodukcyjne wdrożenie klienta**.

2.  Przejrzyj wersje klienta w środowisku produkcyjnym i produkcji wstępnej, sprawdź poprawne kolekcji przedprodukcyjnej jest określony, a następnie kliknij **Podwyższ poziom**, następnie **tak**.  

3.  Po zamknięciu okna dialogowego, wersja zaktualizowanego klienta spowoduje zastąpienie wersji klienta używany w hierarchii. Następnie możesz uaktualnić klientów w całej lokacji. Zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md), aby uzyskać więcej informacji.  

>[!NOTE]
>Aby włączyć klienta przedprodukcyjnego lub wspierania produkcji wstępnej klientowi klienta produkcji, Twoje konto musi być członkiem roli zabezpieczeń, która ma **odczytu** i **Modyfikuj** uprawnienia dla **pakiety aktualizacji** obiektu.
>Aktualizacje klienta uznawać dowolnego okna obsługi programu Configuration Manager skonfigurowane.

