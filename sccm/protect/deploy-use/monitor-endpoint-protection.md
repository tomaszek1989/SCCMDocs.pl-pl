---
title: Monitorowanie stanu programu Endpoint Protection
titleSuffix: Configuration Manager
description: Dowiedz się, jak monitorować program Endpoint Protection w hierarchii programu System Center Configuration Manager.
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f4e1ea4cb097381467774af9c3161079419d6840
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-monitor-endpoint-protection-status"></a>Jak monitorować stan programu Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można monitorować program Endpoint Protection w hierarchii programu Microsoft System Center Configuration Manager za pomocą **stan programu Endpoint Protection** węźle **zabezpieczeń** w **monitorowanie** obszaru roboczego, **programu Endpoint Protection** w węźle **zasoby i zgodność** obszaru roboczego oraz za pomocą raportów.  

##  <a name="BKMK_1"></a> Jak monitorować program Endpoint Protection przy użyciu węzła stan ochrony punktu końcowego  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **zabezpieczeń** , a następnie kliknij przycisk **stan programu Endpoint Protection**.  

3.  W **kolekcji** listy, wybierz kolekcję, dla którego chcesz wyświetlić informacje o stanie.  

    > [!IMPORTANT]  
    >  Kolekcje są dostępne do wyboru w następujących przypadkach:  
    >   
    >  -   Po wybraniu **Wyświetl tę kolekcję na pulpicie nawigacyjnym programu Endpoint Protection** na **alerty** karcie *< nazwa kolekcji\>*** właściwości** okna dialogowego pole.  
    > -   Podczas wdrażania zasad ochrony przed złośliwym kodem programu Endpoint Protection w kolekcji.  
    > -   Po włączeniu i wdrożeniu ustawień klienta programu Endpoint Protection w kolekcji.  

4.  Przejrzyj informacje wyświetlane w **stan zabezpieczeń** i **stanu operacyjnego** sekcje. Możesz kliknąć dowolny link stanu, aby utworzyć tymczasową kolekcję w węźle **Urządzenia** obszaru roboczego **Zasoby i zgodność** . Tymczasowa kolekcja zawiera komputery z wybranym stanem.  

    > [!IMPORTANT]  
    >  Informacje wyświetlane w **stan programu Endpoint Protection** są oparte na ostatnio dane zostały zagregowane z bazy danych programu Configuration Manager i mogą być nieaktualne. Jeśli chcesz pobrać najnowsze dane, na karcie **Narzędzia główne** kliknij pozycję **Uruchom podsumowanie**lub kliknij pozycję **Zaplanuj podsumowanie** , aby dostosować interwał podsumowania.  

##  <a name="BKMK_2"></a> Jak monitorować program Endpoint Protection w roboczym zasoby i zgodność  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, wykonaj jedną z następujących czynności:  

    -   Kliknij przycisk **urządzeń**. Na liście **Urządzenia** wybierz komputer, a następnie kliknij kartę **Szczegóły złośliwego oprogramowania** .  

    -   Kliknij przycisk **kolekcje urządzeń**. Na liście **Kolekcję urządzeń** wybierz kolekcję zawierającą komputer, który chcesz monitorować, a następnie na karcie **Narzędzia główne** w grupie **Kolekcje** kliknij pozycję **Pokaż elementy członkowskie**.  

3.  W *< nazwa kolekcji\>*  listy, wybierz komputer, a następnie kliknij przycisk **szczegóły złośliwego oprogramowania** kartę.  

##  <a name="BKMK_3"></a> Jak monitorować program Endpoint Protection przy użyciu raportów  
 Za pomocą następujących raportów, aby wyświetlić informacje o programie Endpoint Protection w hierarchii. Umożliwia także tych raportów do rozwiązywania problemów programu Endpoint Protection. Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md) i [pliki dziennika w programie System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md). Raporty programu Endpoint Protection znajdują się w folderze programu Endpoint Protection.  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport działania oprogramowania chroniącego przed złośliwym kodem**|Wyświetla przegląd działań ochrony przed złośliwym kodem dla określonej kolekcji.|  
|**Zainfekowane komputery**|Wyświetla listę komputerów, na których wykryto określone zagrożenie.|  
|**Użytkownicy z największą liczbą zagrożeń**|Wyświetla listę użytkowników z największą liczbą wykrytych zagrożeń.|  
|**Lista zagrożeń użytkownika**|Wyświetla listę zagrożeń znalezionych na określonym koncie użytkownika.|  

## <a name="malware-alert-levels"></a>Poziomy alertów dotyczących złośliwego oprogramowania  
 Poniższa tabela umożliwia zidentyfikowanie różne poziomy alertów programu Endpoint Protection, które mogą być wyświetlane w raportach lub konsoli programu Configuration Manager.  

|Poziom alertu|Opis|  
|-----------------|-----------------|  
|**Niepowodzenie**|Program Endpoint Protection nie może skorygować złośliwego kodu. Sprawdź dzienniki, aby uzyskać szczegóły błędu.<br /><br /> **Uwaga:** Listę programu Configuration Manager i Endpoint Protection plików dziennika, zobacz sekcję "Program Endpoint Protection" w [pliki dziennika w programie System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md) tematu.|  
|**Zostaną usunięte**|Program Endpoint Protection pomyślnie usunął złośliwy kod.|  
|**Kwarantanna**|Program Endpoint Protection złośliwego oprogramowania została przeniesiona do bezpiecznej lokalizacji i uniemożliwia jego uruchomienie do czasu usunięcia go lub zezwolenie na uruchamianie.|  
|**Oczyszczone**|Zainfekowany plik został oczyszczony ze złośliwego kodu.|  
|**Dozwolone**|Użytkownik administracyjny użył opcji zezwolenia na uruchomienie oprogramowania zawierającego złośliwy kod.|  
|**Brak akcji**|Program Endpoint Protection nie wykonał żadnej akcji związanych ze złośliwym oprogramowaniem. Taka sytuacja może wystąpić, jeśli komputer zostanie uruchomiony ponownie po wykryciu złośliwego kodu i ten kod nie będzie już wykrywany — na przykład jeśli zamapowany dysk sieciowy, na którym wykryto złośliwy kod, nie jest podłączany ponownie po ponownym uruchomieniu komputera.|  
|**Zablokowane**|Program Endpoint Protection zablokował uruchomienie złośliwego kodu uruchamiania. Taka sytuacja może wystąpić w przypadku znalezienia złośliwego kodu w ramach procesu na komputerze.|
