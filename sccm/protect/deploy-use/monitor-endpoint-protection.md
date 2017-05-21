---
title: "Monitorować stan programu Endpoint Protection | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak monitorować program Endpoint Protection w hierarchii programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b5771f4faebc06076bdbf84727848c881fc1dfb4
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-endpoint-protection-status"></a>Jak monitorować stan programu Endpoint Protection

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można monitorować Endpoint Protection w hierarchii programu Microsoft System Center Configuration Manager za pomocą **stanu ochrony punktu końcowego** węzeł w węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego, **Endpoint Protection** w węźle **zasoby i zgodność** obszaru roboczego i za pomocą raportów.  

##  <a name="BKMK_1"></a>Jak monitorować program Endpoint Protection przy użyciu węzła stan ochrony punktu końcowego  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **zabezpieczeń** , a następnie kliknij przycisk **stanu ochrony punktu końcowego**.  

3.  W **kolekcji** listy, wybierz kolekcję, dla którego chcesz wyświetlić informacje o stanie.  

    > [!IMPORTANT]  
    >  Kolekcje są dostępne do wyboru w następujących przypadkach:  
    >   
    >  -   Po wybraniu **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** na **alerty** na karcie *< nazwa kolekcji\>***właściwości** okno dialogowe.  
    > -   Podczas wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w kolekcji.  
    > -   Po włączeniu funkcji, a wdrożenie ustawień klienta Endpoint Protection w kolekcji.  

4.  Przejrzyj informacje wyświetlane w **stan zabezpieczeń** i **stanu operacyjnego** sekcjach. Możesz kliknąć dowolny link stanu, aby utworzyć tymczasową kolekcję w węźle **Urządzenia** obszaru roboczego **Zasoby i zgodność** . Tymczasowe kolekcja zawiera komputery z wybranego stanu.  

    > [!IMPORTANT]  
    >  Informacje wyświetlane w **stanu ochrony punktu końcowego** węzła opiera się na ostatnich danych, które zostały zagregowane z bazy danych programu Configuration Manager i mogą być nieaktualne. Jeśli chcesz pobrać najnowsze dane, na karcie **Narzędzia główne** kliknij pozycję **Uruchom podsumowanie**lub kliknij pozycję **Zaplanuj podsumowanie** , aby dostosować interwał podsumowania.  

##  <a name="BKMK_2"></a>Jak monitorować program Endpoint Protection w roboczego zasoby i zgodność  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, wykonaj jedną z następujących czynności:  

    -   Kliknij przycisk **urządzeń**. Na liście **Urządzenia** wybierz komputer, a następnie kliknij kartę **Szczegóły złośliwego oprogramowania** .  

    -   Kliknij przycisk **kolekcji urządzeń**. Na liście **Kolekcję urządzeń** wybierz kolekcję zawierającą komputer, który chcesz monitorować, a następnie na karcie **Narzędzia główne** w grupie **Kolekcje** kliknij pozycję **Pokaż elementy członkowskie**.  

3.  W *< nazwa kolekcji\>*  listy, wybierz komputer, a następnie kliknij przycisk **szczegółów złośliwego oprogramowania** kartę.  

##  <a name="BKMK_3"></a>Jak monitorować program Endpoint Protection przy użyciu raportów  
 Za pomocą następujących raportów do przeglądania informacji o programie Endpoint Protection w hierarchii. Można również używać tych raportów do rozwiązywania problemów Endpoint Protection. Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md) i [pliki dziennika w programie System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md). Raporty programu Endpoint Protection znajdują się w folderze Endpoint Protection.  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport działania oprogramowania chroniącego przed złośliwym kodem**|Wyświetla przegląd działań ochrony przed złośliwym kodem dla określonej kolekcji.|  
|**Zainfekowane komputery**|Wyświetla listę komputerów, na których wykryto określone zagrożenie.|  
|**Użytkownicy z największą liczbą zagrożeń**|Wyświetla listę użytkowników z największą liczbą wykrytych zagrożeń.|  
|**Lista zagrożeń użytkownika**|Wyświetla listę zagrożeń znalezionych na określonym koncie użytkownika.|  

## <a name="malware-alert-levels"></a>Poziomy alertów złośliwego oprogramowania  
 Skorzystaj z poniższej tabeli, aby zidentyfikować różnych poziomów alertów ochrony punktu końcowego, które mogą być wyświetlane w raportach lub konsoli programu Configuration Manager.  

|Poziom alertu|Opis|  
|-----------------|-----------------|  
|**Niepowodzenie**|Endpoint Protection korygowanie nie powiodło się złośliwe oprogramowanie. Sprawdź dzienniki szczegóły błędu.<br /><br /> **Uwaga:** Lista programu Configuration Manager i Endpoint Protection plików dziennika, zobacz sekcję "Endpoint Protection" w [pliki dziennika w programie System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md) tematu.|  
|**Zostaną usunięte**|Endpoint Protection pomyślnie usunął złośliwego oprogramowania.|  
|**Kwarantanna**|Endpoint Protection i uniemożliwia uruchamianie aż do usunięcia go lub zezwolić na uruchamianie przeniesione złośliwe oprogramowanie do bezpiecznej lokalizacji.|  
|**Oczyszczone**|Zainfekowany plik został oczyszczony ze złośliwego kodu.|  
|**Dozwolone**|Użytkownik administracyjny użył opcji zezwolenia na uruchomienie oprogramowania zawierającego złośliwy kod.|  
|**Brak akcji**|Endpoint Protection miały żadnych działań związanych ze złośliwym oprogramowaniem. Taka sytuacja może wystąpić, jeśli komputer zostanie uruchomiony ponownie po wykryciu złośliwego kodu i ten kod nie będzie już wykrywany — na przykład jeśli zamapowany dysk sieciowy, na którym wykryto złośliwy kod, nie jest podłączany ponownie po ponownym uruchomieniu komputera.|  
|**Zablokowane**|Endpoint Protection zablokowane uruchomienie złośliwego oprogramowania. Taka sytuacja może wystąpić w przypadku znalezienia złośliwego kodu w ramach procesu na komputerze.|

