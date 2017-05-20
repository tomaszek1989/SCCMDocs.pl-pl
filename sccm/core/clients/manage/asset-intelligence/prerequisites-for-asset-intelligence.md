---
title: "Wymagania wstępne analizy zasobów | Dokumentacja firmy Microsoft"
description: "Pobierz wymagania wstępne związane z analizą zasobów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 23ab4f94-7bfe-436e-8a6a-029409a2730c
caps.latest.revision: 10
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 2bcc6dd84b236187ea9cbfa0b85c25e7ec25719c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-asset-intelligence-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące analizy zasobów programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Analiza zasobów w programie System Center Configuration Manager ma zależności zewnętrzne i zależności w obrębie produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  
 Poniższa tabela zawiera zależności analizy zasobów, które są poza programem Configuration Manager.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Wymagania wstępne dotyczące inspekcji zdarzeń pomyślnego logowania|W czterech raportach analizy zasobów są wyświetlane informacje zebrane z dzienników zdarzeń zabezpieczeń systemu Windows na komputerach klienckich. Jeśli nie skonfigurowano ustawień dziennika zdarzeń zabezpieczeń w celu rejestrowania wszystkich pomyślnych zdarzeń logowania, te raporty nie zawierają danych, nawet gdy odpowiednia klasa raportowania spisu sprzętu jest włączona.<br /><br /> Następujące raporty analizy zasobów zależą od zebranych informacji dziennika zdarzeń zabezpieczeń systemu Windows:<br /><br /> -Sprzęt 03A - użytkownicy podstawowi komputerów<br />-Sprzęt 03B - komputery określonego użytkownika podstawowego konsoli<br />-Oprogramowanie 04a - udostępnione komputery (wielu użytkowników)<br />-Sprzęt 05A - użytkownicy konsoli na określonym komputerze<br /><br /> Aby włączyć agenta klienta spisu sprzętu w celu spisu informacji wymaganych do obsługi tych raportów, należy najpierw zmodyfikować ustawienia dziennika zdarzeń zabezpieczeń systemu Windows na klientach, włączając rejestrowanie wszystkich zdarzeń pomyślnego logowania oraz klasę raportowania spisu sprzętu **SMS_SystemConsoleUser** . Aby uzyskać więcej informacji dotyczących modyfikowania ustawień dziennika zdarzeń zabezpieczeń wszystkie zdarzenia logowania Powodzenie logowania, zobacz [włączyć inspekcję zdarzeń logowania na powodzenie](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableSuccessLogonEvents).|  

> [!NOTE]  
>  Klasa raportowania spisu sprzętu **SMS_SystemConsoleUser** przechowuje dane dotyczące zdarzeń pomyślnego logowania tylko z ostatnich 90 dni dziennika zdarzeń zabezpieczeń, niezależnie od długości dziennika. Jeśli w dzienniku zdarzeń zabezpieczeń znajdują się dane z okresu krótszego niż 90 dni, odczytywany jest cały dziennik.  

## <a name="dependencies-internal-to-configuration-manager"></a>Zależności w programie Configuration Manager  
 Poniższa tabela zawiera zależności analizy zasobów, które są w programie Configuration Manager.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Wymagania wstępne dotyczące agenta klienta|Raporty analizy zasobów są zależne od informacji uzyskiwanych za pomocą raportów spisu sprzętu i oprogramowania klienta. Aby można było uzyskać informacje wymagane do wygenerowania wszystkich raportów analizy zasobów, muszą być włączeni następujący agenci klientów:<br /><br /> -Agent klienta spisu sprzętu<br />-Agent klienta pomiaru oprogramowania|  
|Zależności agenta klienta spisu sprzętu|Aby możliwe było zbieranie danych spisu wymaganych na potrzeby niektórych raportów analizy danych, musi być włączony agent klienta spisu sprzętu. Ponadto niektóre klasy raportowania spisu sprzętu, od których jest zależna analiza zasobów, muszą być włączone na serwerach lokacji głównej.<br /><br /> Aby uzyskać informacje na temat włączania agenta klienta zapasów sprzętu, zobacz [sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).|  
|Zależności agenta klienta pomiaru użytkowania oprogramowania|Wiele raportów analizy zasobów dotyczących oprogramowania jest zależnych od agenta klienta pomiaru użytkowania oprogramowania. Aby uzyskać informacje na temat włączania agenta klienta pomiaru oprogramowania, zobacz [monitorowania użycia aplikacji za pomocą zliczania oprogramowania System Center Configuration Manager](../../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).<br /><br /> Następujące raporty analizy zasobów są zależne od danych zapewnianych przez agenta klienta pomiaru użytkowania oprogramowania:<br /><br /> -Oprogramowanie 07A - ostatnio używane pliki wykonywalne według liczby komputerów<br />-Oprogramowanie 07B - komputery, których był ostatnio używany określony plik wykonywalny<br />-Oprogramowanie 07C - ostatnio używane pliki wykonywalne na określonym komputerze<br />-Oprogramowanie 08A - ostatnio używane pliki wykonywalne według liczby użytkowników<br />-Oprogramowanie 08B - użytkownicy, których był ostatnio używany określony plik wykonywalny<br />-Oprogramowanie 08C - ostatnio używane pliki wykonywalne przez określonego użytkownika|  
|Wymagania wstępne dotyczące klas raportowania spisu sprzętu analizy zasobów|Raporty analizy zasobów w programie Configuration Manager zależą od klas raportowania inwentaryzacji sprzętu. Dopóki klasy raportowania spisu sprzętu nie zostaną włączone, a klienci nie zgłoszą spisu sprzętu na podstawie tych klas, skojarzone raporty analizy zasobów nie będą zawierać żadnych danych. Możesz włączyć następujące klasy raportowania spisu sprzętu w celu spełnienia wymagań raportowania analizy zasobów:<br /><br /> -SMS_SystemConsoleUsage<sup>1</sup><br />-SMS_SystemConsoleUser<sup>1</sup><br />-SMS_InstalledSoftware<br />-SMS_AutoStartSoftware<br />-SMS_BrowserHelperObject<br />-Win32_USBDevice<br />-SMS_InstalledExecutable<br />-SMS_SoftwareShortcut<br />-SoftwareLicensingService<br />-SoftwareLicensingProduct<br />-SMS_SoftwareTag<br /><br /> <sup>1</sup> Domyślnie klasy raportowania spisu sprzętu analizy zasobów **SMS_SystemConsoleUsage** i **SMS_SystemConsoleUser** są włączone.<br /><br /> Można edytować spisu sprzętu analizy zasobów raportowania klas w konsoli programu Configuration Manager w programie **zasoby i zgodność** obszaru roboczego, po kliknięciu **analizy zasobów** węzła. Aby uzyskać więcej informacji, zobacz [klas raportowania inwentaryzacji sprzętu Włączanie analizy zasobów](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableAssetIntelligence) w sekcji [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md) tematu.|  
|Punkt usług raportowania|Aby mogły zostać wyświetlone raporty dotyczące aktualizacji oprogramowania, należy zainstalować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji o tworzeniu punktu usług raportowania, zobacz [Konfigurowanie raportowania w programie Configuration Manager](http://go.microsoft.com/fwlink/p/?LinkId=232661).|  
