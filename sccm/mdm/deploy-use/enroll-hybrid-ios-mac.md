---
title: "Konfigurowanie iOS i Mac hybrydowe zarządzanie urządzeniami za pomocą programu System Center Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Konfigurowanie zarządzania urządzeniami systemu iOS w programie System Center Configuration Manager i Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
caps.latest.revision: 10
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 02af275ede0ab8578adb0615458b285819d65c9c
ms.openlocfilehash: 848721b564316234ad900fcbf968098002a4bb4e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami w systemie iOS za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Korzystając z programu Configuration Manager i usługi Intune, możesz włączyć PRZYNIEŚ rejestracji urządzeń systemu Mac OS X, aby udzielić dostępu do firmowej poczty e-mail i zasobów potrzebnych do iPhone, iPad i użytkowników komputerów Mac i iOS (strategię "Przynieś własne urządzenie"). Gdy użytkownicy zainstalują aplikację portalu firmy usługi Intune, będzie można zastosować zasady dla ich urządzeń. Aby zarządzać urządzeniami z systemem iOS i komputerami Mac, musisz zaimportować certyfikat firmy Apple dla usługi Apple Push Notification service (APNs). Ten certyfikat umożliwia usłudze Intune zarządzanie urządzeniami z systemem iOS i komputerami Mac oraz ustanawianie akredytowanego i zaszyfrowanego połączenia IP z usługami urzędu zarządzania urządzeniami przenośnymi.  

 Możesz także rejestrować firmowe urządzenia z systemem iOS.  Zobacz [rejestrowanie firmowych urządzeń](enroll-company-owned-devices.md).  

## <a name="enable-ios-device-enrollment"></a>Włączanie rejestracji urządzeń z systemem iOS  
 Aby rejestrować urządzenia z systemem iOS, wykonaj następujące kroki:  

#### <a name="set-up-ios-device-enrollment-in-configuration-manager"></a>Konfigurowanie rejestrowania urządzeń z systemem iOS w programie Configuration Manager  

1.  **Wymagania wstępne** — przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy zakończenia wymagania wstępne i procedur w [Instalatora hybrydowe MDM](setup-hybrid-mdm.md).    

2.  **Pobierz żądanie podpisania certyfikatu** — plik żądania podpisania certyfikatu (plik csr) jest wymagany do zażądania certyfikatu usługi APNs od firmy Apple.  

    1.  W konsoli programu Configuration Manager, w obszarze roboczym **Administracja** , wybierz pozycję **Usługi w chmurze**> **Subskrypcje usługi Microsoft Intune**.  

    2.  Na karcie **Narzędzia główne** kliknij pozycję **Utwórz żądanie certyfikatu usługi APNs**. Zostanie otwarte okno dialogowe **Zgłaszanie żądania podpisania certyfikatu usługi wypychania powiadomień firmy Apple** .  

    3.  Kliknij przycisk**Przeglądaj** i przejdź do ścieżki, w której ma zostać zapisany plik nowego żądania podpisania certyfikatu (csr). Zapisz lokalnie plik żądania podpisania certyfikatu (CSR).  

    4.  Kliknij przycisk **Pobierz**. Nowy plik .csr usługi Microsoft Intune zostanie pobrany i zapisany przez program Configuration Manager. Plik CSR jest używany na potrzeby żądania certyfikatu relacji zaufania w portalu Apple Push Certficates.  

3.  **Zamów certyfikat usługi APNs w firmie Apple** — certyfikat usługi Apple Push Notification service (APNs) służy do ustanawiania relacji zaufania między usługą zarządzania, usługą Intune i zarejestrowanymi urządzeniami przenośnymi z systemem iOS.  

    1.  W przeglądarce przejdź do portalu [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) i zaloguj się przy użyciu identyfikatora Apple ID firmy. Ten identyfikator Apple ID musi być w przyszłości używany do odnawiania certyfikatu usługi APN.  

    2.  Zakończ pracę kreatora, używając pliku żądania podpisania certyfikatu (pliku csr). Pobierz certyfikat usługi APNs i zapisz plik pem lokalnie. Ten plik certyfikatu (PEM) usługi APN jest używany do ustanawiania relacji zaufania między serwerem Apple Push Notification i urzędem zarządzania urządzeniami przenośnymi usługi Intune.  

4.  **Włącz rejestrowanie i przekazywanie certyfikatu usługi APNs** — w celu włączenia rejestrowania urządzeń z systemem iOS przekaż certyfikat usługi APNs.  

    1.  W konsoli programu Configuration Manager, w obszarze roboczym **Administracja** , wybierz pozycję **Usługi w chmurze** > **Subskrypcja usługi Microsoft Intune**.  

    2.  Na karcie **Narzędzia główne** w grupie **Subskrypcja** kliknij pozycję **Konfiguruj platformy** > **iOS**.  

        > [!NOTE]  
        >  Nie przekazuj certyfikatu usługi APNs (Apple Push Notification service) przed włączeniem rejestrowania urządzeń z systemem iOS w konsoli programu Configuration Manager.  

    3.  W oknie dialogowym **Właściwości subskrypcji usługi Microsoft Intune** wybierz kartę **iOS** i kliknij, aby zaznaczyć pole wyboru **Włącz rejestrowanie dla systemu iOS** .  

    4.  Kliknij polecenie **Przeglądaj**i przejdź do pliku certyfikatu (cer) usługi APNs, który został pobrany od firmy Apple. Program Configuration Manager wyświetli informacje o certyfikacie usługi APNs. Kliknij przycisk **OK** , aby zapisać certyfikat APNs w usłudze Intune.  

 Po zakończeniu konfiguracji musisz poinformować użytkowników, jak mogą rejestrować swoje urządzenia. Zobacz [Co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

> [!div class="button"]
[< Wstecz kroku](create-service-connection-point.md)[następny krok >  ](set-up-additional-management.md)

