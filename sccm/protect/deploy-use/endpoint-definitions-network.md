---
title: Definicje złośliwego oprogramowania ochrony punktu końcowego z udziału sieciowego
titleSuffix: Configuration Manager
description: Dowiedz się, jak ręcznie pobrać najnowsze aktualizacje definicji od firmy Microsoft, a następnie skonfiguruj klientom na pobieranie tych definicji.
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: ddef4d2a-f481-4020-9ddd-9cca5f9795cb
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 96fe34d713a1d9d3afb78dc59124865024e9eb77
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-a-network-share-for-configuration-manager"></a>Włącz program Endpoint Protection definicje złośliwego oprogramowania do pobrania z udziału sieciowego dla programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Możesz ręcznie pobrać najnowsze aktualizacje definicji od firmy Microsoft, a następnie skonfigurować klientów, aby pobierali te definicje z folderu udostępnionego w sieci. Użytkownicy mogą również inicjować aktualizacje definicji, korzystając z tego źródła aktualizacji.

> [!NOTE]
>  Klienci muszą mieć dostęp do odczytu do folderu udostępnionego, aby pobierać aktualizacje definicji.

 Aby uzyskać więcej informacji dotyczących sposobu pobierania aktualizacji aparatu i definicji przechowywanych w udziale plików, zobacz [zainstalować najnowsze oprogramowanie chroniące przed złośliwym kodem i antyszpiegowskich Microsoft](http://www.microsoft.com/security/portal/Definitions/HowToForeFront.aspx).

## <a name="to-configure-definition-downloads-from-a-file-share"></a>Aby skonfigurować pobieranie definicji z udziału plików

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Endpoint Protection**i kliknij pozycję **Zasady ochrony przed złośliwym kodem**.

3.  Otwórz stronę właściwości **domyślnych zasad ochrony przed złośliwym kodem** lub utwórz nowe zasady ochrony przed złośliwym kodem. Aby uzyskać więcej informacji dotyczących sposobu tworzenia zasad ochrony przed złośliwym kodem, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

4.  W sekcji **Aktualizacja definicji** okna dialogowego właściwości ochrony przed złośliwym kodem kliknij pozycję **Ustaw źródło**.

5.  W oknie dialogowym **Konfigurowanie źródeł aktualizacji definicji** wybierz pozycję **Aktualizacje z udziałów plików UNC**.

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konfigurowanie źródeł aktualizacji definicji** .

7.  Kliknij pozycję **Ustaw ścieżki**. Następnie w oknie dialogowym **Konfigurowanie ścieżek UNC aktualizacji definicji** dodaj co najmniej jedną ścieżkę UNC do lokalizacji definicji aktualizacji definicji w udziale sieciowym.

8.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konfigurowanie ścieżek UNC aktualizacji definicji** .


> [!div class="button"]
[Następny krok >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Ponownie >](endpoint-configure-alerts.md)
