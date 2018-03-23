---
title: Pulpit nawigacyjny powierzchni urządzenia
titleSuffix: System Center Configuration Manager
description: Przejrzyj informacje na temat powierzchni urządzeń przy użyciu pulpitu nawigacyjnego.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-other
ms.assetid: 7397fc17-3ae8-4525-8386-aea8a9cffa06
ms.openlocfilehash: c39798573966037b6d27afe6844a7f88450a4528
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="surface-device-dashboard-in-system-center-configuration-manager"></a>Urządzenie powierzchni pulpitu nawigacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1802, pulpit nawigacyjny powierzchni urządzenia zawiera informacje dotyczące powierzchni znalezione w danym środowisku, w skrócie pojedynczego urządzenia. <!--1355788-->

## <a name="open-the-surface-device-dashboard"></a>Otwórz pulpit nawigacyjny powierzchni urządzenia

Aby otworzyć pulpit nawigacyjny powierzchni urządzenia, wykonaj następujące kroki: 

1. Otwórz konsolę programu Configuration Manager. 
2. Polecenie **monitorowanie** węzła. 
3. Aby załadować pulpitu nawigacyjnego, kliknij na **urządzeń Surface**.

**Pulpit nawigacyjny powierzchni urządzenia**
![powierzchni urządzenia pulpitu nawigacyjnego](media\Surface-device-dashboard.PNG)



## <a name="reviewing-information-in-the-surface-device-dashboard"></a>Przeglądanie informacji na pulpicie nawigacyjnym powierzchni urządzenia

Pulpit nawigacyjny powierzchni urządzenia zawiera trzy wykresy dla danego środowiska. 

- **Procent powierzchni urządzeń** — umożliwia odsetek urządzeń powierzchni w całym środowisku.

    ![Procent urządzeń powierzchni wykresu](media\Percent-Surface-Devices.PNG)
- **Modele powierzchni** — pokazuje liczbę urządzeń na powierzchni modelu. 
    - Ustawiając kursor nad sekcji wykres zapewni procent powierzchni urządzenia, które są wybrany model. 

         ![Modele powierzchni wykresu](media\Surface-Models-Hover.PNG)
    - Kliknij sekcję wykresu spowoduje przejście do listy urządzeń dla modelu. 
        ![Lista urządzeń powierzchni modelu](media\Surface-Model-Device-List.PNG)

- **Z góry pięć wersji oprogramowania układowego**— wykres z modelami oprogramowania układowego 5 w danym środowisku. 
    - Ustawiając kursor nad sekcji wykres zapewni liczba powierzchni urządzenia, które są wybrana wersja oprogramowania układowego. 
       ![Lista urządzeń powierzchni modelu](media\Surface-Firmware-Hover.PNG)


## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji o urządzeniach powierzchni zobacz:
 - [Powierzchni]( https://go.microsoft.com/fwlink/?linkid=861998) witryny sieci Web.
    




