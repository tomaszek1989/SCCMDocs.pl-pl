---
title: Przykład przejść stanu weryfikacji dla analizy zasobów
titleSuffix: Configuration Manager
description: Przykłady przejść stanu weryfikacji dla analizy zasobów w programie System Center Configuration Manager.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6230a6e5-a1f6-459b-84f1-07fbde0e70f0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cd4d2075e7980361d341a6ed71ff151ada997060
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="example-validation-state-transitions-for-asset-intelligence-in-system-center-configuration-manager"></a>Przykład przejść stanu weryfikacji dla analizy zasobów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Stany weryfikacji analizy zasobów w programie System Center Configuration Manager nie są statyczne i może zostać zmieniony z działania administracyjne, które należy wykonać w celu modyfikacji danych, które są przechowywane w katalogu analizy zasobów. W tym temacie przedstawiono przykłady weryfikacji możliwych przejść stanu.

##  <a name="BKMK_UncategorizedIsCategorized"></a> Element katalogu bez kategorii jest kategoryzowany przez użytkownika administracyjnego  

|**Przejście stanu**|**Opis przejścia stanu**|  
|--------------------------|--------------------------------------|  
|**Bez kategorii**|Tytuł oprogramowania znajdującego się w spisie, dla którego usługa System Center Online nie określiła wcześniej kategorii lub które użytkownik administracyjny wprowadził do katalogu analizy zasobów.|  
|**Bez kategorii** do **Zdefiniowany przezużytkownika**|Element bez kategorii jest kategoryzowany przez użytkownika administracyjnego.|  

##  <a name="BKMK_CategorizedIsReCategorized"></a> Element katalogu z kategorią jest ponownie kategoryzowany przez użytkownika administracyjnego  

|**Przejście stanu**|**Opis przejścia stanu**|  
|--------------------------|--------------------------------------|  
|**Zweryfikowane**|Element katalogu został zdefiniowany przez badaczy usługi System Center Online i znajduje się w katalogu analizy zasobów.|  
|**Zweryfikowane** do **Zdefiniowane przez użytkownika**|Zweryfikowany element katalogu jest ponownie kategoryzowany przez użytkownika administracyjnego|  

> [!NOTE]  
>  Ponieważ informacje o kategorii uzyskane z usługi System Center Online są przechowywane w bazie danych i nie można ich usunąć, użytkownik administracyjny może przywrócić kategorię określoną przez usługę System Center Online później.  

##  <a name="BKMK_UserDefinedIsRecategorized"></a> Element katalogu zdefiniowany przez użytkownika jest ponownie kategoryzowany przez usługę System Center Online  

|**Przejście stanu**|**Opis przejścia stanu**|  
|--------------------------|--------------------------------------|  
|**Bez kategorii**|Tytuł oprogramowania znajdującego się w spisie jest wprowadzany do katalogu analizy zasobów, przy czym nie był on poprzednio skategoryzowany przez usługę System Center Online ani użytkownika administracyjnego.|  
|**Zdefiniowane przez użytkownika**|Element bez kategorii jest kategoryzowany przez użytkownika administracyjnego.|  
|**Zdefiniowane przez użytkownika** do **Można aktualizować**|Element katalogu zdefiniowany przez użytkownika został skategoryzowany inaczej przez usługę System Center Online podczas kolejnych zbiorczych aktualizacji katalogu analizy zasobów.<br /><br /> Użytkownik administracyjny może użyć okna dialogowego **Rozwiązywanie konfliktów dotyczących szczegółów oprogramowania** do określenia, czy użyć nowych informacji o kategorii, czy poprzedniej wartości zdefiniowanej przez użytkownika.|  
|**Można aktualizować** do **Zweryfikowane**|Użytkownik administracyjny może użyć okna dialogowego **Rozwiązywanie konfliktów dotyczących szczegółów oprogramowania** , aby użyć nowych informacji o kategorii odebranych z usługi System Center Online podczas poprzedniej aktualizacji katalogu.|  
|lub||  
|**Można aktualizować** do **Zdefiniowane przez użytkownika**|Użytkownik administracyjny może użyć okna dialogowego **Rozwiązywanie konfliktów dotyczących szczegółów oprogramowania** , aby użyć poprzedniej wartości zdefiniowanej przez użytkownika.|  

> [!NOTE]  
>  Ponieważ informacje o kategorii uzyskane z usługi System Center Online są przechowywane w bazie danych i nie można ich usunąć, użytkownik administracyjny może przywrócić kategorię określoną przez usługę System Center Online później.  

##  <a name="BKMK_UncategorizedIsSubmitted"></a> Element katalogu bez kategorii jest przesyłany do usługi System Center Online w celu określenia kategorii  

|**Przejście stanu**|**Opis przejścia stanu**|  
|--------------------------|--------------------------------------|  
|**Bez kategorii**|Tytuł oprogramowania znajdującego się w spisie jest wprowadzany do bazy danych analizy zasobów, przy czym nie był on poprzednio skategoryzowany przez usługę System Center Online ani użytkownika administracyjnego.|  
|**Bez kategorii** do **Oczekujące**|Element bez kategorii jest przesyłany do usługi System Center Online przez użytkownika administracyjnego w celu określenia kategorii.|  
|**Oczekujące** do **Zweryfikowane**|Element jest kategoryzowany przez usługę System Center Online. Użytkownik administracyjny importuje element do katalogu analizy zasobów za pomocą aktualizacji zbiorczej katalogu lub funkcji synchronizacji katalogu analizy zasobów. Obie te metody są dostępne za pomocą roli systemu lokacji punktu synchronizacji analizy zasobów.|  

##  <a name="BKMK_UserDefinedIsSubmitted"></a> Element katalogu zdefiniowany przez użytkownika jest przesyłany do usługi System Center Online w celu określenia kategorii  

|**Przejście stanu**|**Opis przejścia stanu**|  
|--------------------------|--------------------------------------|  
|**Bez kategorii**|Tytuł oprogramowania znajdującego się w spisie jest wprowadzany do bazy danych analizy zasobów, przy czym nie był on poprzednio skategoryzowany przez usługę System Center Online ani użytkownika administracyjnego.|  
|**Zdefiniowane przez użytkownika**|Dla elementu bez kategorii została określona kategoria.|  
|**Zdefiniowane przez użytkownika** do **Oczekujące**|Przesyłasz element zdefiniowany przez użytkownika do usługi System Center Online w celu określenia kategorii.|  
|**Oczekujące** do **Można aktualizować**|Obiekty zdefiniowane przez użytkownika katalogu zostały skategoryzowane inaczej przez usługę System Center Online podczas kolejnej synchronizacji katalogu. Akcja **Rozwiąż konflikt** umożliwia określenie, czy mają zostać użyte nowe informacje o kategorii, czy poprzednia wartość zdefiniowana przez użytkownika. Aby uzyskać więcej informacji na temat rozwiązywania konfliktów, zobacz [rozwiązać konflikt szczegółów oprogramowania](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  
|**Można aktualizować** do **Zweryfikowane**|Akcja **Rozwiąż konflikt** umożliwia wybranie nowych informacji o kategorii odebranych z usługi System Center Online podczas poprzedniej aktualizacji katalogu. Aby uzyskać więcej informacji na temat rozwiązywania konfliktów, zobacz [rozwiązać konflikt szczegółów oprogramowania](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  
|lub||  
|**Można aktualizować** do **Zdefiniowane przez użytkownika**|Akcja **Rozwiąż konflikt** umożliwia użycie poprzedniej wartości zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji na temat rozwiązywania konfliktów, zobacz [rozwiązać konflikt szczegółów oprogramowania](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  

> [!NOTE]  
>  Ponieważ informacje o kategorii uzyskane z usługi System Center Online są przechowywane w bazie danych i nie można ich usunąć, możesz przywrócić kategorię określoną przez usługę System Center Online później.  
