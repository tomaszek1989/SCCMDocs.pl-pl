---
title: Wyklucz uaktualnienia klienta | Windows | System Center Configuration Manager
description: "Dowiedz się, jak wyłączyć klientów systemu Windows z pobieranie uaktualnione w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: de5602179f3ac55b51133b8280a0143f1b0ff30e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>Jak wyłączyć uaktualnianie klientów dla komputerów z systemem Windows w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1610, można wykluczyć kolekcję klientów z automatycznie instalowanie klienta zaktualizowanej wersji. Dotyczy to automatyczne uaktualnianie, jak również innych metod, takich jak uaktualnienie oparta na aktualizacji oprogramowania, skryptów logowania i zasad grupy. Możesz użyć tego dla kolekcji komputerów, które muszą opieka większe w przypadku uaktualniania klienta. Klient, który znajduje się w kolekcji wykluczonych ignoruje żądania do zainstalowania zaktualizowanego oprogramowania klienckiego.

## <a name="configure-exclusion-for-automatic-upgrades"></a>Konfigurowanie wykluczeń automatycznych uaktualnień

1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie kliknij przycisk **ustawienia hierarchii**.

2. Kliknij przycisk **uaktualnienie klienta** kartę.

3. Kliknij pole wyboru obok pozycji **Wyklucz określone klientów z uaktualnienia**, a następnie wybierz kolekcję, aby wykluczyć dla kolekcji wykluczeń. Możesz wybrać tylko jedną kolekcję do wykluczenia.

4.  Kliknij przycisk **OK** zamknąć i zapisać konfigurację. Następnie po klientów aktualizacji zasad, klienci w kolekcji wykluczonych nie będzie automatycznie zainstaluje aktualizacje oprogramowania klienckiego. Aby uzyskać więcej informacji, zobacz [sposobu uaktualniania klientów na komputerach z systemem Windows](upgrade-clients-for-windows-computers.md).

![Ustawienia automatycznego uaktualniania wykluczeń](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>Chociaż interfejs użytkownika stwierdza, że klienci nie zostaną uaktualnione przy użyciu dowolnej metody, istnieją dwie metody używanej do zastąpienia tych ustawień. Instalację wypychaną klienta i ręcznej instalacji klienta może służyć do zastąpienia tej konfiguracji. Aby uzyskać więcej informacji zobacz sekcję następujące.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Jak uaktualnić klienta, który jest wykluczony kolekcji

Tak długo, jak długo kolekcja jest skonfigurowana do wykluczenia, Członkowie tej kolekcji może mieć tylko uaktualnić przy użyciu jednej z dwóch metod, które zastąpią wykluczeń oprogramowania klienta:
 - **Instalację wypychaną klienta** — instalacji wypychanej klienta służy do uaktualniania klienta, który znajduje się w kolekcji wykluczonych. Dozwolone jest uznawane za zamiar administratora i umożliwia uaktualnienie klientów bez usuwania całą kolekcję z wykluczeń.       

 - **Ręczna instalacja klienta** — można ręcznie uaktualnić klientów, którzy są w kolekcji wykluczonych, korzystając z następującego przełącznika wiersza polecenia przy użyciu programu ccmsetup: ***/ignoreskipupgrade***

  Jeśli próba ręcznie uaktualnić klienta, który jest członkiem kolekcji wykluczone i nie należy używać tego przełącznika, klient nie zainstaluje nowe oprogramowanie klienckie. Więcej informacji można znaleźć w temacie [jak instalować klientów programu Configuration Manager ręcznie](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

Aby uzyskać więcej informacji na temat metod instalacji klienta można znaleźć w temacie [sposobu wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

