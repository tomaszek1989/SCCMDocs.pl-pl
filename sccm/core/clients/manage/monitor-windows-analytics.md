---
title: Monitor klientom module analiz systemu Windows
titleSuffix: Configuration Manager
description: Module analiz systemu Windows to zestaw rozwiązań działające na Operations Management Suite, które zezwala na rysowanie wartościowe informacje do bieżącego stanu środowiska dzięki wykorzystaniu danych telemetrycznych Windows zgłaszany przez urządzenia w danym środowisku.
ms.date: 01/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e792f421520798a0e000384aafcb99f31dc8eb14
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-windows-analytics-with-configuration-manager"></a>Użyj module analiz systemu Windows z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

[Module analiz systemu Windows](https://www.microsoft.com/WindowsForBusiness/windows-analytics) to zestaw rozwiązań, które są uruchamiane na [Operations Management Suite](/azure/operations-management-suite/operations-management-suite-overview) (OMS). Te rozwiązania pozwalają uzyskiwać wgląd w bieżący stan środowiska. Urządzenia w danym środowisku zgłaszać dane telemetryczne systemu Windows i te dane można uzyskać dostępu do i analizowane za pomocą rozwiązania w [portalu sieci web usługi Operations Management Suite](https://mms.microsoft.com). Łącząc [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) do programu Configuration Manager, możesz bezpośrednio dostępu do danych w **monitorowanie** węzła konsoli programu Configuration Manager.

Dane telemetryczne systemu Windows używane w module analiz systemu Windows nie jest przekazywane bezpośrednio na serwerze lokacji programu Configuration Manager. Komputery klienckie wysyłania danych telemetrycznych systemu Windows z usługą telemetrii systemu Windows. Ta usługa następnie przesyła odpowiednie dane do rozwiązań w module analiz systemu Windows hostowanej w jednym z obszarów roboczych OMS Twojej organizacji. Menedżer konfiguracji można przekierować użytkownika do odpowiednich danych w portalu sieci web z łączami w kontekście lub bezpośrednio wyświetlania danych, która jest częścią rozwiązania podłączonymi do programu Configuration Manager. Można również bezpośrednio odpytywać danych z portalu sieci web operacji Management Suite.

>[!Important]
>[Dane diagnostyczne i użycia programu Configuration Manager](../../plan-design/diagnostics/diagnostics-and-usage-data.md), które serwer lokacji programu Configuration Manager raporty do firmy Microsoft, są oddzielne od systemu Windows, analizy i telemetrię systemu Windows.

## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Konfigurowanie klientów do danych raportu do analiz systemu Windows

W przypadku urządzeń klienckich z danymi raportu w celu module analiz systemu Windows należy skonfigurować urządzenia z kluczem komercyjnych identyfikator skojarzony z obszarem roboczym pakietu OMS służącą do hostowania danych analiz systemu Windows. Można również skonfigurować urządzenia do danych telemetrycznych raportu na poziomie telemetrii odpowiednie dla określonego rozwiązania, które ma być używany. 

### <a name="configure-windows-analytics-client-settings"></a>Konfigurowanie ustawień klienta w module analiz systemu Windows
Aby skonfigurować module analiz systemu Windows, w konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta**, kliknij dwukrotnie **Tworzenie ustawień klienta urządzenia niestandardowe**, a następnie sprawdź **module analiz systemu Windows**.  

Po nawigowania do **module analiz systemu Windows** karcie Ustawienia, skonfiguruj następujące ustawienia:
  -  **Komercyjnych klucza Identyfikatora**  
Klucz identyfikator komercyjnych mapuje informacje z urządzeń, które można zarządzać w obszarze roboczym pakietu OMS obsługującego danych organizacji w module analiz systemu Windows. Jeśli skonfigurowano już program komercyjnych identyfikator klucza do użycia z gotowości do uaktualnienia, używają tego identyfikatora. Jeśli nie masz jeszcze komercyjnych klucza Identyfikatora, zobacz [generowanie klucza komercyjnych identyfikator]( https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

  -  **Poziom dane telemetryczne dla urządzeń z systemem Windows 10**   
Aby uzyskać więcej informacji o każdym poziomie telemetrii systemu Windows 10, zobacz [telemetrii Konfigurowanie systemu Windows w Twojej organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

   > [!Note]
   > Aktualizacja 1710, można ustawić zbieranie danych telemetrii systemu Windows 10 do poziomu **rozszerzony (ograniczony)**. To ustawienie umożliwia uzyskania przydatnych wyników informacje na temat urządzeń w środowisku bez urządzenia podlegające wszystkie dane w **rozszerzony** telemetrii poziomu z systemem Windows 10 w wersji 1709 lub nowszej. Poziom telemetria rozszerzony (ograniczony) zawiera metryki z poziomu podstawowego, jak również podzbiór danych zebranych z poziomu rozszerzony zastosowanie w module analiz systemu Windows.


  -  **Zgódź się na komercyjnych danych kolekcji urządzeń z systemem Windows 7, 8 i 8.1**   
Aby uzyskać więcej informacji, zobacz [pola i Windows 7, Windows 8 i Windows 8.1 zdarzenia telemetrii appraiser](https://go.microsoft.com/fwlink/?LinkID=822965).

  -  **Konfigurowanie zbierania danych Internet Explorer**  
Na urządzeniach z systemem Windows 8.1 lub starszy, Internet Explorer danych kolekcji umożliwiają uaktualnienie gotowości do wykrycia niezgodności aplikacji sieci web, które mogą uniemożliwić sprawnego przebiegu uaktualnienia do systemu Windows 10. Zbieranie danych z programu Internet Explorer można włączyć dla poszczególnych strefy internet. Aby uzyskać więcej informacji o strefach internetowych, zobacz [o strefach zabezpieczeń adresu URL](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx).

## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>Użyj gotowości do uaktualnienia do identyfikowania problemów ze zgodnością systemu Windows 10

Gotowości do uaktualnienia (dawniej uaktualnienia Analytics) umożliwia analizowania gotowości urządzenia i zgodności z systemem Windows 10. Ocena ta umożliwia płynniejszy uaktualnienia. Po połączeniu programu Configuration Manager z gotowości do uaktualnienia, dostęp do tych danych zgodności z uaktualnieniem klienta bezpośrednio w konsoli programu Configuration Manager. Następnie urządzeń docelowych dla uaktualnienia lub korygowanie z listy urządzeń.

Aby uzyskać więcej informacji oraz szczegółowe informacje na temat konfigurowania i połącz się gotowości do uaktualnienia, zobacz [gotowości do uaktualnienia](../../clients/manage/upgrade/upgrade-analytics.md).

## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Module analiz systemu Windows używana do określania luk w zasadach ochrony informacji systemu Windows

Wersji systemu Windows 10 1703 i skonfigurowana z urządzenia z nowszymi wersjami [Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) nie telemetrii raport zasad (pracy w toku) w przypadku aplikacji, które uzyskują dostęp do danych firmowych w środowisku, ale reguły aplikacji zasad pracy w toku obejmują. Użytkownicy mogą potrzebować tych aplikacji w celu zwiększenia wydajności pracy, ale pracy w toku blokuje dostęp użytkowników. Wiedzy, że użytkownicy uzyskują dostęp do danych firmowych jest przydatne w trybie konserwacji zasad Windows Information Protection w programie Configuration Manager. 

Dostęp do tych danych systemu Windows Information Protection, za pomocą tej [zapytania Operations Management Suite](https://go.microsoft.com/fwlink/?linkid=849952).