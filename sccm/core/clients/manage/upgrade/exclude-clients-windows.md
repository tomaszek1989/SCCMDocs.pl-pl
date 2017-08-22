---
title: Wyklucz uaktualnienia klienta | Windows | System Center Configuration Manager
description: "Dowiedz się, jak wyłączyć klientów systemu Windows z pobierania uaktualnienia w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: de5602179f3ac55b51133b8280a0143f1b0ff30e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>Jak wykluczyć uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1610, można wykluczyć kolekcję klientów z automatycznego instalowania wersji zaktualizowanego klienta. Dotyczy to automatycznego uaktualniania, a także innych metod, takich jak uaktualnianie oparta na aktualizacji oprogramowania, skryptów logowania i zasad grupy. Możesz użyć tego dla kolekcji komputerów, które wymagają większej szczególną uwagę podczas uaktualniania klienta. Klient, który znajduje się w wykluczonej kolekcji ignoruje żądania instalacji oprogramowania zaktualizowanego klienta.

## <a name="configure-exclusion-for-automatic-upgrades"></a>Konfigurowanie wykluczeń automatycznych uaktualnień

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, a następnie kliknij przycisk **ustawienia hierarchii**.

2. Kliknij przycisk **uaktualnienie klienta** kartę.

3. Zaznacz pole wyboru dla **Wyklucz określone klientów z uaktualnienia**i wykluczania kolekcji, wybierz kolekcję, które chcesz wykluczyć. Można wybrać tylko jednej kolekcji do wykluczenia.

4.  Kliknij przycisk **OK** zamknąć i zapisać konfigurację. Następnie po klientów aktualizacji zasad, klienci w kolekcji wykluczonych przestaną być automatycznie zainstaluje aktualizacje oprogramowania klienckiego. Aby uzyskać więcej informacji, zobacz [uaktualnianie klientów komputerów z systemem Windows](upgrade-clients-for-windows-computers.md).

![Ustawienia automatycznego uaktualniania wykluczeń](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>Chociaż interfejs użytkownika stwierdza, że klienci nie zostaną uaktualnione przy użyciu dowolnej metody, istnieją dwie metody, którą można przesłonić te ustawienia. Wypychana instalacja klienta i ręczna instalacja klienta może służyć do zastępowania tej konfiguracji. Aby uzyskać więcej informacji zobacz sekcję poniżej.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Jak uaktualnić klienta, który znajduje się w wykluczonej kolekcji

Tak długo, jak kolekcja jest skonfigurowana do wykluczenia, elementy członkowskie tej kolekcji może mieć tylko oprogramowanie klienckie, ich uaktualnić przy użyciu jednej z dwóch metod, które zastąpią wykluczenia:
 - **Wypychana instalacja klienta** — wypychana instalacja klienta służy do uaktualniania klienta, który znajduje się w wykluczonej kolekcji. To jest dozwolona, ponieważ jest on uznawany za można zamiar administratora i pozwala na uaktualnienie klientów bez usuwania całą kolekcję z wykluczeń.       

 - **Ręczna instalacja klienta** — należy ręcznie uaktualnić klientów, którzy są w wykluczonej kolekcji, gdy użytkownik korzysta z programu ccmsetup następujący przełącznik wiersza polecenia: ***/ignoreskipupgrade***

  Jeśli próba ręcznie uaktualnić klienta, który jest członkiem kolekcji wykluczonych i nie należy używać tego przełącznika, klient nie zainstaluje nowe oprogramowanie klienckie. Aby uzyskać więcej informacji, zobacz [jak zainstalować ręcznie Configuration Manager klientów](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

Aby uzyskać więcej informacji na temat metod instalacji klienta, zobacz [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).
