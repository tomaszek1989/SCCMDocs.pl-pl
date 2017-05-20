---
title: "Używanie klienta rozszerzonej współpracy z bieżącej gałęzi | Dokumentacja firmy Microsoft"
description: "Informacje o używaniu klienta z długoterminowe obsługi gałęzi z programu Configuration Manager za pomocą witryny bieżącej gałęzi."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: 0
author: robstackmsft
ms.author: robstack
Robots: NOINDEX,NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 4cc339e28110a3097c318b61224ae7692c47a31a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-client-software-from-the-version-1606-baseline-media-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>Użyj oprogramowania klienckiego z nośnika linii bazowej 1606 wersji rozszerzonej współdziałanie z przyszłych wersji lokacji bieżącej gałęzi

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi) (długoterminowej obsługi oddziału)*  

Można użyć programu Configuration Manager oprogramowanie klienckie dla komputerów z systemem Windows (client.msi) z nośnika linii bazowej wersji 1606 DVD można uzyskać za pomocą programu System Center 2016 lub z lub wersji programu System Center Configuration Manager (bieżącej gałęzi i długoterminowe obsługi 1606 gałęzi) do zarządzania urządzeniami, które należą do lokacji bieżącej gałęzi. Ten klient jest nazywany rozszerzonej współdziałanie klienta.

## <a name="how-this-scenario-works"></a>Jak działa ten scenariusz:
Zazwyczaj po zainstalowaniu nowej aktualizacji w konsoli dla bieżącej gałęzi klienci automatycznie aktualizuje swoje oprogramowanie klienckie, mogą korzystać z tych nowych funkcji.

W tym scenariuszu należy użyć bieżącej gałęzi i odbieranie nowych funkcji i aktualizacji. Większość klientów Uruchom oprogramowanie klienckie z bieżącego rozgałęzienia i zaktualizować przy każdej aktualizacji wersji, które należy zainstalować oprogramowanie klienta. Jednak na podzbioru krytyczne systemów, które chcesz odbierać aktualizacje oprogramowania klienta, należy zainstalować klienta rozszerzonej współpracy. Tacy klienci nie zostaną zainstalowane nowe oprogramowanie klienckie, dopóki jawnie wdrożenia nowej wersji oprogramowania klienckiego do nich.

Więcej informacji na temat uniemożliwić klientom bieżącej gałęzi automatycznej aktualizacji po zainstalowaniu nowej wersji programu Configuration Manager będzie dostępne w wersji bieżącej gałęzi 1610.

Lokacji bieżącej gałęzi musi być zainstalowana wersja 1606 lub nowszej.

## <a name="the-extended-interoperability-client-software"></a>Oprogramowanie klienckie rozszerzonej współdziałanie
Korzystając z klienta rozszerzonej współpracy z 2016 Center systemu lub wersji programu System Center Configuration Manager (bieżącej gałęzi i długoterminowe obsługi gałęzi 1606) z lokacji bieżącej gałęzi, klient jest obsługiwana przez dwa lata po powszechnym udostępnieniu wersję, która jest 12 października 2016.

Planowanie aktualizacji klienta współdziałanie rozszerzonej na urządzeniach zarządzanych za pomocą bieżącej gałęzi przed pomocy technicznej dla klienta wygaśnie. W tym celu pobrać nową wersję klienta firmy Microsoft, a następnie wdrożyć ten zaktualizowanego oprogramowania klienckiego na urządzeniach korzystających z bieżącego rozszerzone współdziałanie klienta.

**Ograniczenia klienta rozszerzonej współpracy:**
-     Za pomocą aktualizacji w konsoli nie są dostępne aktualizacje dla oprogramowania klienckiego rozszerzonej współpracy. Dodatkowe szczegóły dotyczące wdrażania oprogramowania klienckiego zaktualizowane zostanie dostarczona podczas zwalniania zaktualizowanego klienta.

## <a name="identify-the-client-version-you-use"></a>Identyfikowania używanej wersji klienta
Poniżej przedstawiono dostępne zarówno dla bieżącej gałęzi i LTSB wersje główne klienta:

|Wersja klienta|Tworzyć gałęzie i wersji |  
|----------------|---------------------|
|5.00.8325.xxxx |    -Bieżącej gałęzi 1511|
|5.00.8355.xxxx    |-Bieżącej gałęzi 1602|
|5.00.8412.1307    |-Bieżącej gałęzi 1606 </br> -Bieżącej gałęzi 1606 z listą poprawkę 1606 (KB3186654)</br>-klienta rozszerzonej współpracy z wersji 1606 nośnika linii bazowej|  

Wersja klienta na kliencie można przeglądać na **ogólne** kartę programu Configuration Manager w Panelu sterowania.

Na **składniki** kartę apletu, niektóre składniki pokazują różne wartości. Na przykład wersję klienta 8412.1307, niektóre składniki mogą zostać wyświetlone 5.00.8412. **1000** lub 5.00.8412. **1006**.  Inny w cztery ostatnie cyfry dla niektórych składników jest normalnym i nie wskazuje błąd składnika, aby zaktualizować bieżącą wersję klienta.

