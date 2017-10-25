---
title: "Klient testowy uaktualnia kolekcji środowiska przedprodukcyjnego | Dokumentacja firmy Microsoft"
description: "Testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: "10"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5b6e60e7c6225e37dd345e99c703505e346cd0a4
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="how-to-test-client-upgrades-in-a-pre-production-collection-in-system-center-configuration-manager"></a>Testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można przetestować nową wersję klienta programu Configuration Manager w kolekcji przedprodukcyjnej przed uaktualnieniem pozostałej części lokacji.  Gdy to zrobisz, tylko urządzenia, które są częścią kolekcji testu są uaktualniane. Gdy już przetestujesz klienta, możesz podwyższyć poziom klienta, który udostępnia nową wersję oprogramowania klienta w pozostałej części lokacji.

> [!NOTE]
> Aby podwyższyć poziom klienta testowego do środowiska produkcyjnego, użytkownik musi być zalogowany jako użytkownik z rolą zabezpieczeń **administrator o pełnych uprawnieniach** i zakres zabezpieczeń **wszystkich**. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration). Możesz także zalogować się do serwera podłączona do centralnej lokacji administracyjnej lub najwyższego poziomu autonomicznej lokacji głównej.

 Istnieją 3 podstawowe kroki, aby klienci w środowisku przedprodukcyjnym.  

1.  Konfigurowanie automatycznych uaktualnień klienta do użycia kolekcji przedprodukcyjnej.  

2.  Instalowanie aktualizacji programu Configuration Manager, która obejmuje nową wersję klienta.  

3.  Podwyższ poziom nowego klienta do środowiska produkcyjnego.  

##  <a name="to-configure-automatic-client-upgrades-to-use-a-pre-production-collection"></a>Aby skonfigurować automatyczne uaktualnienia klienta do użycia kolekcji przedprodukcyjnej  

1. [Konfigurowanie kolekcji](..\collections\create-collections.md) zawierającą komputery, którą chcesz wdrożyć klienta przedprodukcyjnego do. Nie dołączaj komputerów grupy roboczej w kolekcji przedprodukcyjnej. Uwierzytelniania wymagany dla punktu dystrybucji korzystają nie może uzyskać dostępu do pakietu klienta środowiska przedprodukcyjnego.   

1.  W konsoli programu Configuration Manager Otwórz **administracji** > **konfiguracja lokacji** > **witryny**i wybierz polecenie **ustawienia hierarchii**.  

     Na karcie **Uaktualnienie klienta** obszaru **Właściwości ustawień hierarchii**:  

    -   Wybierz pozycję **Uaktualnij automatycznie wszystkich klientów w kolekcji przedprodukcyjnej przy użyciu klienta przedprodukcyjnego**  

    -   Wprowadź nazwę kolekcji, która ma być używana jako kolekcja środowiska przedprodukcyjnego.  

![Testowanie uaktualnień klienta](media/test-client-upgrades.png)

>[!NOTE]
>Aby zmienić te ustawienia, Twoje konto musi być członkiem **administrator o pełnych uprawnieniach** roli zabezpieczeń i **wszystkie** zakresu zabezpieczeń.


##  <a name="to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a>Instalowanie aktualizacji programu Configuration Manager, która obejmuje nową wersję klienta  

1.  W konsoli programu Configuration Manager, otwórz **administracji** > **aktualizacje i obsługa**, wybierz pozycję **dostępne** aktualizacji, a następnie wybierz pozycję **Instaluj pakiet aktualizacji**. (Przed wersji 1702, aktualizacje i obsługa znajdowało się pod **administracji** > **usługi w chmurze**.)

     Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md)  

2.  Podczas instalowania aktualizacji na **opcje klienta** strony kreatora wybierz pozycję **testu w kolekcji środowiska przedprodukcyjnego**.  

3.  Wykonaj pozostałe kroki kreatora i zainstaluj pakiet aktualizacji.  

     Po ukończeniu pracy kreatora rozpocznie się wdrażanie zaktualizowanego klienta na klientach w kolekcji środowiska przedprodukcyjnego. Wdrożenia uaktualnionych klientów można monitorować w sekcji **Monitorowanie** > **Stan klienta** > **Przedprodukcyjne wdrożenie klienta**. Aby uzyskać więcej informacji, zobacz [Jak monitorować stan wdrażania klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/monitor-client-deployment-status.md).

    > [!NOTE]
    > Stan wdrożenia na komputerach hostujących role systemu lokacji w kolekcji środowiska przedprodukcyjnego mogą być zgłaszane jako **niezgodnych** nawet jeśli klient został pomyślnie wdrożony. W przypadku podwyższania poziomu klienta do produkcji stan wdrożenia jest zgłaszany prawidłowo.

##  <a name="to-promote-the-new-client-to-production"></a>Podwyższenie poziomu nowego klienta do środowiska produkcyjnego  

1.  W konsoli programu Configuration Manager, otwórz **administracji** > **aktualizacje i obsługa**i wybierz polecenie **promowanie klienta przedprodukcyjnego**. (Przed wersji 1702, aktualizacje i obsługa znajdowało się pod **administracji** > **usługi w chmurze**.)

    > [!TIP]
    > Przycisk **Podwyższ poziom przedprodukcyjnego klienta** jest też dostępny w przypadku monitorowania wdrożeń klienta w konsoli w pozycji **Monitorowanie** > **Stan klienta** > **Przedprodukcyjne wdrożenie klienta**.

2.  Przejrzyj wersje klienta w środowisku produkcyjnym i produkcji wstępnej należy upewnić się, poprawny kolekcji środowiska przedprodukcyjnego jest określona, a następnie kliknij przycisk **Podnieś poziom**, następnie **tak**.  

3.  Po zamknięciu okna dialogowego zaktualizowaną wersję klienta zastąpi wersję klienta w hierarchii. Następnie możesz uaktualnić klientów w całej lokacji. Zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md), aby uzyskać więcej informacji.  

>[!NOTE]
>Aby włączyć klienta przedprodukcyjnego lub podwyższyć poziom klienta przedprodukcyjnego do klienta produkcyjnego, Twoje konto musi być członkiem roli zabezpieczeń, która ma **odczytu** i **Modyfikuj** uprawnienia dla **pakietów aktualizacji** obiektu.
>Uaktualnienia klienta honoruje oknami obsługi programu Configuration Manager, które zostały skonfigurowane.
