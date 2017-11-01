---
title: Monitor klientom module analiz systemu Windows
titleSuffix: Configuration Manager
description: "Module analiz systemu Windows to zestaw rozwiązań działające na Operations Management Suite, które zezwala na rysowanie wartościowe informacje do bieżącego stanu środowiska dzięki wykorzystaniu danych telemetrycznych Windows zgłaszany przez urządzenia w danym środowisku."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
caps.latest.revision: "23"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 99c65b876f4a2424db5dd4d2943f8ea3edfb1227
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="use-windows-analytics-with-configuration-manager"></a>Użyj module analiz systemu Windows z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

[Module analiz systemu Windows](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) to zestaw rozwiązań, które są uruchamiane na [Operations Management Suite](/azure/operations-management-suite/operations-management-suite-overview). Rozwiązania umożliwiają formularza wgląd w bieżący stan środowiska. Urządzenia w danym środowisku zgłaszać dane telemetryczne systemu Windows. Te dane można uzyskać dostępu do i analizowane za pomocą rozwiązania w [portalu sieci web usługi Operations Management Suite](https://mms.microsoft.com). W przypadku liczby [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) danych można również bezpośrednio dostępne w węźle monitorowanie konsoli programu Configuration Manager, nawiązując połączenie gotowości do uaktualnienia do programu Configuration Manager.

Dane telemetryczne systemu Windows używane w module analiz systemu Windows nie jest przekazywane bezpośrednio na serwerze lokacji programu Configuration Manager. Komputery klienckie wysyłania danych telemetrycznych systemu Windows z usługą telemetrii. Odpowiednich danych jest następnie przetransferowane na module analiz systemu Windows rozwiązań hostowanych w jednym z obszarów roboczych OMS Twojej organizacji. Menedżer konfiguracji mogą być następnie zarówno bezpośredniego odpowiednie dane w portalu sieci web z łączami w kontekście lub bezpośrednio wyświetlanie danych, która jest częścią rozwiązania podłączonymi do programu Configuration Manager. Można również bezpośrednio odpytywać danych z portalu sieci web operacji Management Suite.

>[!Important]
>[Dane diagnostyczne i użycia programu Configuration Manager](../../plan-design/diagnostics/diagnostics-and-usage-data.md), który zgłoszone do firmy Microsoft, z serwerem lokacji programu Configuration Manager jest całkowicie niezależna od systemu Windows, analizy i telemetrię systemu Windows.

## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Konfigurowanie klientów do danych raportu do analiz systemu Windows

W kolejności, w przypadku urządzeń klienckich do raportu, dane do analiz systemu Windows, urządzenia musi być skonfigurowana z Identyfikatorem komercyjnych klucz skojarzony z obszaru roboczego usługi Operations Management Suite obsługującego danych analiz systemu Windows w Twojej organizacji. Urządzenia muszą być również skonfigurowane do telemetrii raportu na poziomie telemetrii odpowiednich dla konkretne rozwiązanie lub rozwiązania, które chcesz użyć. 

### <a name="configure-windows-analytics-client-settings"></a>Konfigurowanie ustawień klienta w module analiz systemu Windows
Aby skonfigurować module analiz systemu Windows, w konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta**, kliknij dwukrotnie **Tworzenie ustawień klienta urządzenia niestandardowe**, a następnie sprawdź **module analiz systemu Windows**.  

Po nawigowania do **module analiz systemu Windows** karcie Ustawienia, skonfiguruj następujące opcje:
  -  **Identyfikator komercyjnych**  
Klucz identyfikator komercyjnych mapuje informacje z urządzeń, które można zarządzać w obszarze roboczym pakietu OMS obsługującego danych organizacji w module analiz systemu Windows. Jeśli skonfigurowano już program komercyjnych identyfikator klucza do użycia z gotowości do uaktualnienia, używają tego identyfikatora. Jeśli nie masz jeszcze komercyjnych klucza Identyfikatora, zobacz [generowanie klucza komercyjnych identyfikator]( https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

  -  **Poziom dane telemetryczne dla urządzeń z systemem Windows 10**   
Aby uzyskać informacje, jakie informacje są zbierane na każdym poziomie telemetrii systemu Windows 10, zobacz [telemetrii Konfigurowanie systemu Windows w Twojej organizacji](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

  -  **Zgódź się na komercyjnych danych kolekcji urządzeń z systemem Windows 7, 8 i 8.1**   
Dla informacje o danych zbieranych z tych systemów operacyjnych po możesz zdecydować się na, zobacz Pobierz [pola i Windows 7, Windows 8 i Windows 8.1 zdarzenia telemetrii appraiser](https://go.microsoft.com/fwlink/?LinkID=822965) plik pdf firmy Microsoft.

  -  **Konfigurowanie zbierania danych Internet Explorer**  
Na urządzeniach z systemem Windows 8.1 lub starszy, Internet Explorer danych kolekcji umożliwiają uaktualnienie gotowości do wykrycia niezgodności aplikacji sieci web, które mogą uniemożliwić sprawnego przebiegu uaktualnienia do systemu Windows 10. Zbieranie danych z programu Internet Explorer można włączyć dla poszczególnych strefy internet. Aby uzyskać więcej informacji o strefach internetowych, zobacz [o strefach zabezpieczeń adresu URL](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx).

## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>Użyj gotowości do uaktualnienia do identyfikowania problemów ze zgodnością systemu Windows 10

Gotowości do uaktualnienia (dawniej uaktualnienia Analytics) umożliwia analizowania gotowości urządzenia i zgodności z systemem Windows 10. Ocena ta umożliwia płynniejszy uaktualnienia. Po połączeniu programu Configuration Manager z gotowości do uaktualnienia, można uzyskać dostępu do tych danych zgodności z uaktualnieniem klienta bezpośrednio w konsoli programu Configuration Manager. Następnie będzie możliwe na urządzenia docelowe dla uaktualnienia lub korygowanie z listy urządzeń.

Aby uzyskać więcej informacji oraz szczegółowe informacje na temat konfigurowania i połącz się gotowości do uaktualnienia, zobacz [gotowości do uaktualnienia](../../clients/manage/upgrade/upgrade-analytics.md).

## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Module analiz systemu Windows używana do określania luk w zasadach ochrony informacji systemu Windows

Urządzenia 1703 lub nowszy w wersji systemu Windows 10, które są skonfigurowane przy użyciu [Windows Information Protection](https://docs.microsoft.com/en-us/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) (pracy w toku) zasad raport telemetrii w aplikacji, które uzyskują dostęp do danych firmowych w danym środowisku, ale które nie są uwzględnione w pracy w toku reguły aplikacji. Są one potencjalnie aplikacji, które użytkownicy w środowisku musi być wydajność, ale które są zablokowane dostępu, więc wiedzy czy uzyskują dostęp do danych firmowych mogą być przydatne w trybie konserwacji zasad Windows Information Protection w programie Configuration Manager. 

Te dane rozwiązanie Windows Information Protection jest możliwy za pomocą tej [zapytania Operations Management Suite](https://go.microsoft.com/fwlink/?linkid=849952).