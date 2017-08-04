---
title: "Konfigurowanie systemu iOS i Mac hybrydowego zarządzania urządzeniami za pomocą programu System Center Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Konfigurowanie zarządzania urządzeniami z systemem iOS z programu System Center Configuration Manager i Microsoft Intune."
ms.custom: na
ms.date: 07/31/2017
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
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 1a93a542f55d02df20865fa4ae8d7590dd9be753
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami w systemie iOS za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programu Configuration Manager i usługi Intune można włączyć rejestrowanie urządzeń z systemami iOS i macOS udzielić dostępu do firmowej poczty e-mail i zasobów potrzebnych do iPhone, iPad oraz użytkowników komputerów Mac. Gdy użytkownicy zainstalują aplikację portalu firmy usługi Intune, będzie można zastosować zasady dla ich urządzeń. Aby zarządzać urządzeniami z systemem iOS i komputerami Mac, musisz zaimportować certyfikat firmy Apple dla usługi Apple Push Notification service (APNs). Ten certyfikat umożliwia zarządzanie, nawiązując połączenie z usługą zarządzania urządzeniami firmy Apple iOS i Mac urządzeń usługi Intune.  

 Możesz także rejestrować firmowe urządzenia z systemem iOS.  Zobacz [rejestrować urządzenia należące do firmy](enroll-company-owned-devices.md).  

**Wymagania wstępne**<br>
Przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy, spełnić wymagania wstępne i procedur w [Instalatora hybrydowego zarządzania urządzeniami Przenośnymi](setup-hybrid-mdm.md).

Aby rejestrować urządzenia z systemem iOS, wykonaj następujące kroki:  

## <a name="download-a-certificate-signing-request"></a>Pobierz żądanie podpisania certyfikatu
Plik żądania podpisania certyfikatu jest wymagane do zażądania certyfikatu APNs firmy Apple.  

1.  W konsoli programu Configuration Manager, w obszarze roboczym **Administracja** , wybierz pozycję **Usługi w chmurze**> **Subskrypcje usługi Microsoft Intune**.  

2.  Na karcie **Narzędzia główne** kliknij pozycję **Utwórz żądanie certyfikatu usługi APNs**. Zostanie otwarte okno dialogowe **Zgłaszanie żądania podpisania certyfikatu usługi wypychania powiadomień firmy Apple** .  

3.  **Przeglądaj** na ścieżkę, aby zapisać nowy plik żądania podpisania certyfikatu. Zapisz lokalnie plik żądania podpisania certyfikatu.  

4.  Kliknij przycisk **Pobierz**. Nowe Microsoft Intune certyfikatu podpisywania żądania pobierania plików i jest zapisany przez program Configuration Manager. Plik żądania podpisania certyfikatu jest używany do żądania certyfikatu relacji zaufania z portalu Apple Push Certificates.  

## <a name="request-an-mdm-push-certificate-from-apple"></a>Zamów certyfikat usługi wypychania MDM firmy Apple
Certyfikat zarządzania urządzeniami Przenośnymi Push służy do ustanawiania relacji zaufania między usługą zarządzania, Intune i urządzeń przenośnych zarejestrowanych dla systemu iOS.  

1.  W przeglądarce przejdź do portalu [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) i zaloguj się przy użyciu identyfikatora Apple ID firmy. Ten identyfikator Apple ID musi być w przyszłości używany do odnawiania certyfikatu usługi APN.  

2.  Zakończ pracę kreatora, używając pliku żądania podpisania certyfikatu (pliku csr). Pobierz certyfikat zarządzania urządzeniami Przenośnymi wypychania i Zapisz plik pem lokalnie. Ten plik certyfikatu (PEM) jest używany do ustanawiania relacji zaufania między serwerem Apple Push Notification i urzędem zarządzania urządzeniami przenośnymi usługi Intune.  

> [!NOTE]  
>  Nie przekazuj certyfikatu Apple Push Notification service (APN) do usługi Intune, dopóki nie zostanie włączona rejestracja systemu iOS w konsoli programu Configuration Manager.  

## <a name="enable-enrollment-and-upload-the-mdm-push-certificate"></a>Włącz rejestrowanie i przekazywanie certyfikatu wypychania MDM
Aby włączyć rejestrowanie dla systemu iOS, Przekaż certyfikat APNs.  

1.  W konsoli programu Configuration Manager, w obszarze roboczym **Administracja** , wybierz pozycję **Usługi w chmurze** > **Subskrypcja usługi Microsoft Intune**.  

2.  Na karcie **Narzędzia główne** w grupie **Subskrypcja** kliknij pozycję **Konfiguruj platformy** > **iOS**.  

3.  W oknie dialogowym **Właściwości subskrypcji usługi Microsoft Intune** wybierz kartę **iOS** i kliknij, aby zaznaczyć pole wyboru **Włącz rejestrowanie dla systemu iOS** .  
4.  Kliknij polecenie **Przeglądaj**i przejdź do pliku certyfikatu (cer) usługi APNs, który został pobrany od firmy Apple. Program Configuration Manager wyświetli informacje o certyfikacie usługi APNs. Kliknij przycisk **OK** , aby zapisać certyfikat APNs w usłudze Intune.  

> [!NOTE]
> **Ograniczenia rejestracji** możliwości nie jest dostępny w tej chwili. 

> [!div class="button"]
[< Wstecz krok](create-service-connection-point.md)[następny krok >  ](set-up-additional-management.md)

