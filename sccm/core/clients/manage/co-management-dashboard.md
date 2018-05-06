---
title: Pulpit nawigacyjny zarządzania wspólnej
titleSuffix: Configuraton Manager
description: Przejrzyj informacje dotyczące zarządzania wspólnej przy użyciu pulpitu nawigacyjnego.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cdf073aa3e9ca3be6062ea0e5e0528bb97937989
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="co-management-dashboard-in-system-center-configuration-manager"></a>Pulpit nawigacyjny wspólnej zarządzania w programie System Center Configuration Manager
*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1802, możesz wyświetlić pulpit nawigacyjny z informacjami o wspólnej zarządzania. Pulpit nawigacyjny pomaga Przejrzyj maszyny, które są zarządzane wspólnie w danym środowisku. Wykresy ułatwiają identyfikowanie urządzeń, które mogą wymagać uwagi.<!--1356648-->

## <a name="open-the-co-management-dashboard"></a>Otwórz pulpit nawigacyjny zarządzania wspólnej
Aby otworzyć pulpit nawigacyjny zarządzania wspólnej, wykonaj następujące kroki: 

1. Otwórz konsolę programu Configuration Manager. 
2. Polecenie **monitorowanie** węzła. 
3. Aby załadować pulpitu nawigacyjnego, kliknij na **zarządzania wspólnej**.

## <a name="reviewing-information-in-the-co-management-dashboard"></a>Przeglądanie informacji na pulpicie nawigacyjnym zarządzania wspólnej

Pulpit nawigacyjny zarządzania wspólnej zawiera cztery wykresy dla danego środowiska. 

- **Urządzenia zarządzane wspólnie** — umożliwia procent wspólnie zarządzanych urządzeń w całym środowisku.

    ![Wykres wspólnie zarządzanych urządzeń](media\co-management-dashboard\Percent-Co-managed-graph.PNG)

- **System operacyjny klienta dystrybucji** — pokazuje liczbę klientów urządzeń dla każdego systemu operacyjnego w wersji. Używane są następujące grupowania: </br>
    - Windows 7 & 8.x
    - Niższe niż 1709 systemu Windows 10
    - Windows 10 1709 i powyżej.

         > [!NOTE] 
         > Windows 10, wersja 1709 i nowsze, jest wymagane w przypadku zarządzania wspólnej.

     Ustawiając kursor nad sekcji wykresu zapewni odsetek urządzeń w grupowanie wybranego systemu operacyjnego.

     ![Wykres dystrybucji systemu operacyjnego klienta](media\co-management-dashboard\Co-management-OS-distribution-graph.PNG)

- **Stan zarządzania wspólnej**-podział urządzenia powodzenie lub Niepowodzenie w ramach następujących kategorii:
    - Sukces, hybrydowego Joined usługi Azure AD
    - Sukces, usługi Azure AD dołączony
    - Wystąpił błąd: Automatyczna rejestracja nie powiodła się
    
     Ustawiając kursor nad sekcji wykres umożliwia odsetek urządzeń w kategorii. 

     ![Stan wykresu dla zarządzania wspólnej](media\co-management-dashboard\Co-management-status-graph.PNG)

     Kliknij sekcję wykresu przejście do listę urządzeń dla kategorii.
 
     ![Lista urządzeń błąd rejestracji](media\co-management-dashboard\Enrollment-Failure_Device-List.PNG)


- **Przejście obciążenia**-Wyświetla wykres słupkowy o liczbie urządzeń, które są przenoszone do Microsoft Intune dla obciążeń dostępne cztery:
    - Zasady zgodności
    - Dostęp do zasobów
    - Windows Update dla firm
    - Program Endpoint Protection

     Ustawiając kursor nad sekcji wykresu zapewni liczbę urządzeń, które są przenoszone do obciążenia. 
     ![Obciążenie przejście wykres słupkowy](media\co-management-dashboard\Workload-Transition.PNG)


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat zarządzania wspólnej zobacz:
 - [Współzarządzanie urządzeniami z systemem Windows 10](/sccm/core/clients/manage/co-management-overview.md)
 - [Przygotowywanie urządzeń z systemem Windows 10 pod kątem współzarządzania](/sccm/core/clients/manage/co-management-prepare.md)

    
