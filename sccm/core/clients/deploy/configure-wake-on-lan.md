---
title: Konfigurowanie funkcji Wake on LAN | Dokumentacja firmy Microsoft
description: Wybierz ustawienia funkcji Wake On LAN w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9c920651ba1dc6e0a28df458d28956126ddbaff0
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>Jak skonfigurować funkcję Wake on LAN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Określ wznawiania na ustawienia sieci LAN dla programu System Center Configuration Manager, aby wznowić pracę komputerów ze stanu uśpienia w celu zainstalowania wymaganego oprogramowania, takie jak aktualizacje oprogramowania, aplikacje, sekwencje zadań i programy.

Funkcji Wake on LAN można uzupełnić ustawieniami klienta serwera proxy wznawiania. Jednak aby używać serwera proxy wznawiania, należy włączyć funkcję Wake on LAN dla lokacji i określić **Użyj tylko pakietów wznawiania** i **emisji pojedynczej** opcję Wake na metodę transmisji w sieci LAN. To rozwiązanie wznawiania obsługuje również połączenia ad-hoc, takie jak połączenia pulpitu zdalnego.

Aby skonfigurować lokację główną dla funkcji Wake on LAN, należy użyć pierwszej procedury. Następnie należy użyć drugiej procedury konfigurowania ustawień klienta serwera proxy wznawiania. Ta druga procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla ustawień serwera proxy wznawiania miały zastosowanie do wszystkich komputerów w hierarchii. Jeśli chcesz, aby te ustawienia dotyczyły tylko do wybranych komputerów, utworzyć niestandardowe ustawienie urządzenia i przypisać je do kolekcji, która zawiera komputery, które mają być skonfigurowane dla serwera proxy wznawiania. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).

Komputer, który otrzyma ustawień klienta serwera proxy wznawiania prawdopodobnie spowoduje wstrzymanie połączenia sieciowego dla 1-3 sekundy. Dzieje się tak, ponieważ klient musi zresetować karty interfejsu sieciowego, aby włączyć serwer proxy wznawiania na nim.

> [!WARNING]
> Aby uniknąć nieoczekiwanych zakłóceń działania usługi sieciowej, należy najpierw ocenić serwera proxy wznawiania w izolowanej i reprezentatywnej infrastrukturze sieci. Następnie użyj niestandardowych ustawień klienta, aby rozszerzyć test na wybraną grupę komputerów w kilku podsieciach. Aby uzyskać więcej informacji o działaniu serwera proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

## <a name="to-configure-wake-on-lan-for-a-site"></a>Aby skonfigurować funkcję Wake on LAN dla lokacji

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Konfiguracja lokacji > witryny**.
2. Kliknij lokację podstawową do skonfigurowania, a następnie kliknij przycisk **właściwości**.
3. Kliknij przycisk **funkcji Wake on LAN** i ustaw opcje, które wymagają dla tej lokacji. Do obsługi serwera proxy wznawiania, upewnij się, możesz wybrać **Użyj tylko pakietów wznawiania** i **emisji pojedynczej**. Aby uzyskać więcej informacji, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).
4. Kliknij przycisk **OK** i powtórzyć tę procedurę dla wszystkich lokacji głównych w hierarchii.

## <a name="to-configure-wake-up-proxy-client-settings"></a>Aby skonfigurować ustawienia klienta serwera proxy wznawiania

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Ustawienia klienta**.
2. Kliknij przycisk **domyślne ustawienia klienta**, a następnie kliknij przycisk **właściwości**.
3. Wybierz **zarządzania energią** , a następnie wybierz **tak** dla **włączyć serwer proxy wznawiania**.
4. Przejrzyj i w razie potrzeby skonfiguruj inne ustawienia serwera proxy wznawiania. Więcej informacji o tych ustawieniach [zarządzania zasilaniem](../../../core/clients/deploy/about-client-settings.md#power-management).
5. Kliknij przycisk **OK** zamknąć okno dialogowe, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe domyślne ustawienia klienta.

Za pomocą następujących raportów funkcji Wake On LAN monitorować instalację i konfigurację serwera proxy wznawiania:

- Podsumowanie stanu wdrażania serwera proxy wznawiania
- Szczegóły stanu wdrażania serwera proxy wznawiania

> [!TIP]
> Aby sprawdzić, czy serwer proxy wznawiania działa, należy przetestować połączenie uśpiony komputer. Na przykład połączyć się z folderem udostępnionym na tym komputerze lub spróbować połączyć się z komputerem za pomocą pulpitu zdalnego. Jeśli używasz bezpośredni dostęp, należy sprawdzić, czy działają prefiksy IPv6, wykonując te same testy względem uśpionego komputera, który jest obecnie połączony z Internetem.

