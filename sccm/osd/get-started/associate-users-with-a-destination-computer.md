---
title: "Tworzenie skojarzeń użytkowników z komputerem docelowym | Dokumentacja firmy Microsoft"
description: "Skonfiguruj System Center Configuration Manager, aby skojarzyć użytkowników z komputerów docelowych, podczas wdrażania systemów operacyjnych."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: c0331567b94a99b29cc73c16de17a9f3bc6b9e43
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="associate-users-with-a-destination-computer-in-system-center-configuration-manager"></a>Tworzenie skojarzeń użytkowników z komputerem docelowym w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli używasz programu System Center Configuration Manager do wdrażania systemu operacyjnego można skojarzyć użytkowników z komputerem docelowym, na którym jest wdrażany system operacyjny. Taka konfiguracja obejmuje następujące elementy:  

-   Podstawowym użytkownikiem komputera docelowego jest jeden użytkownik.  

-   Podstawowymi użytkownikami komputera docelowego jest wielu użytkowników.  

 W przypadku wdrażania aplikacji koligacja urządzenia użytkownika obsługuje zarządzanie skoncentrowane na użytkownikach. Jeśli użytkownik jest kojarzony z komputerem docelowym, na którym jest instalowany system operacyjny, po wdrożeniu aplikacji dla tego użytkownika zostaną one automatycznie zainstalowane na tym komputerze. Jednak mimo że można skonfigurować obsługę koligacji urządzenia użytkownika w chwili wdrażania systemu operacyjnego, koligacji nie można używać do wdrażania systemów operacyjnych.  

 Aby uzyskać więcej informacji o koligacji urządzenia użytkownika, zobacz [łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

## <a name="how-to-specify-a-user-when-you-deploy-operating-systems"></a>Sposób określania użytkownika podczas wdrażania systemów operacyjnych  
 W poniższej tabeli znajduje się lista akcji, które można wykonać, aby zintegrować koligację urządzenia użytkownika we wdrożeniach systemu operacyjnego. Koligację urządzenia użytkownika można zintegrować we wdrożeniach środowiska PXE, wdrożeniach z nośników rozruchowych oraz wdrożeniach z wstępnie przygotowanych nośników.  

|Akcja|Więcej informacji|  
|------------|----------------------|  
|Utwórz sekwencję zadań, która obejmuje zmienną **SMSTSAssignUsersMode**|Dodaj zmienną **SMSTSAssignUsersMode** na początku sekwencji zadań za pomocą kroku [Ustaw zmienną sekwencji zadań](../../osd/understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable). Ta zmienna określa, w jaki sposób informacje o użytkowniku są obsługiwane w sekwencji zadań.<br /><br /> Ustaw zmienną na jedną z następujących wartości:<br /><br /> <br /><br /> **Automatycznie**: Sekwencja zadań automatycznie tworzy relację między użytkownikiem a docelowym komputerem i wdraża system operacyjny.<br /><br /> **Oczekujące**: Sekwencja zadań tworzy relację między użytkownikiem a komputerem docelowym, ale przed wdrożeniem systemu operacyjnego oczekuje na zatwierdzenie przez użytkownika administracyjnego.<br /><br /> **Wyłączone**: Sekwencja zadań nie kojarzy użytkowników z komputerem docelowym i kontynuuje wdrażanie systemu operacyjnego.<br /><br /> <br /><br /> Tę zmienną można również ustawić na komputerze lub kolekcji. Aby uzyskać więcej informacji na temat wbudowanych zmiennych, zobacz [wbudowane zmienne sekwencji zadań](../../osd/understand/task-sequence-built-in-variables.md).|  
|Utwórz polecenie przeduruchomieniowe zbierające informacje o użytkowniku|Poleceniem przeduruchomieniowym może być skrypt Visual Basic (VB) zawierający pole wprowadzania albo aplikacja HTML (HTA), która weryfikuje dane wprowadzane przez użytkownika.<br /><br /> Polecenie przeduruchomieniowe musi ustawiać zmienną **SMSTSUdaUsers**, która jest używana podczas uruchamiania sekwencji zadań. Tę zmienną możesz ustawić na komputerze, w kolekcji lub w zmiennej sekwencji zadań. W przypadku dodawania wielu użytkowników użyj następującego formatu: *domena\użytkownik1, domena\użytkownik2, domena\użytkownik3*.|  
|Skonfiguruj sposób kojarzenia użytkownika z komputerem docelowym za pomocą punktów dystrybucji i nośników|Podczas [konfigurowania punktu dystrybucji do akceptowania żądań rozruchu w środowisku PXE](https://technet.microsoft.com/library/mt627944\(TechNet.10\).aspx#BKMK_PXEDistributionPoint) oraz tworzenia [nośnika rozruchowego](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx) lub [wstępnie przygotowanego nośnika](https://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx) za pomocą Kreatora tworzenia nośnika sekwencji zadań możesz określić, w jaki sposób punkt dystrybucji i nośnik obsługują kojarzenie użytkowników z komputerem docelowym, na którym jest wdrażany system operacyjny.<br /><br /> Podczas konfigurowania obsługi koligacji urządzenia użytkownika nie jest dostępna wbudowana metoda weryfikacji tożsamości użytkowników. Może to być istotne, gdy technik wprowadza informacje w imieniu użytkownika podczas aprowizacji komputera. Oprócz skonfigurowania sposobu obsługi informacji o użytkowniku w sekwencji zadań skonfigurowanie tych opcji w punkcie dystrybucji i na nośniku zapewnia możliwość ograniczenia wdrożeń uruchomionych z nośnika rozruchowego w środowisku PXE lub z konkretnego typu nośnika.|  
