---
title: "Omówienie certyfikatów CNG"
titleSuffix: Configuration Manager
description: "Omówienie CNG certyfikatów w programie Configuration Manager"
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.openlocfilehash: f5f5138270d4f14b76b2c41e41ec034a0c12a932
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cng-certificates-overview"></a>Omówienie certyfikatów CNG
<!-- 1356191 --> 

Menedżer konfiguracji ma ograniczoną obsługę szyfrowania: Certyfikaty następnej generacji (CNG). Klienci programu Configuration Manager mogą używać certyfikatu uwierzytelniania klienta PKI z kluczem prywatnym w dostawcy magazynu kluczy CNG (KSP). Dostawcy magazynu KLUCZY, z obsługą klientów programu Configuration Manager obsługuje oparte na sprzęcie klucza prywatnego, takich jak moduł TPM dostawcy magazynu KLUCZY dla certyfikatów uwierzytelniania klienta PKI.

## <a name="supported-scenarios"></a>Scenariusze obsługiwane
Można użyć [Cryptography API: Nowej generacji (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certyfikatu szablonów w następujących scenariuszach:

- Rejestracja klienta i komunikacji z punktem zarządzania HTTPS.   
- Oprogramowanie dystrybucji i wdrażania aplikacji z punktem dystrybucji HTTPS.   
- Wdrożenie systemu operacyjnego  
- Klient SDK (z najnowszej aktualizacji) oraz Proxy niezależnego dostawcy oprogramowania do obsługi komunikatów.   
- Konfiguracja zarządzania bramy chmury.  

> [!NOTE]
> CNG jest zgodne z interfejsu API kryptografii (CAPI). Certyfikaty CAPI w dalszym ciągu obsługiwana nawet wtedy, gdy obsługa CNG jest włączona na komputerze klienckim.

## <a name="unsupported-scenarios"></a>Scenariusze nieobsługiwane

Obecnie nie są obsługiwane następujące scenariusze:

- Usługa sieci Web katalogu aplikacji, witryny sieci Web katalogu aplikacji, punkt rejestracyjny i punktu proxy rejestracji ról nie działa podczas zainstalowany w trybie HTTPS przy użyciu certyfikatu CNG powiązany z witryny sieci web w Internet Information Services (IIS). Program Software Center nie jest wyświetlany w aplikacji i pakietów w zależności od dostępności, które zostały wdrożone dla użytkownika lub kolekcje grupy użytkowników.

- Punkt migracji stanu nie działa podczas instalacji w trybie HTTPS przy użyciu certyfikatu CNG powiązany z witryny sieci web w usługach IIS.

- Aby utworzyć punkt dystrybucji w chmurze przy użyciu certyfikatów CNG.

- Składnika NDES Policy Module komunikacja punkt rejestracji certyfikatu (CRP) kończy się niepowodzeniem, jeśli składnika NDES Policy Module używa certyfikatów CNG certyfikatu uwierzytelniania klienta.

- Tworzenia nośnika sekwencji zadań nie powiedzie się utworzyć nośnik rozruchowy, jeśli określono certyfikatów CNG.

## <a name="to-use-cng-certificates"></a>Aby korzystać z certyfikatów CNG

Aby korzystać z certyfikatów CNG, urząd certyfikacji (CA) należy podać CNG szablonów certyfikatów dla komputerów docelowych. Szczegóły szablonu różne w zależności od scenariusza; Jednakże wymagane są następujące właściwości:

- **Zgodność** kartę

    - **Certyfikat urzędu** musi być system Windows Server 2008 lub nowszym. (System Windows Server 2012 jest zalecane).

    - **Odbiorca certyfikatu** musi być Windows Vista/Server 2008 lub nowszym. (System Windows 8/Windows Server 2012 jest zalecane).

- **Kryptografia** kartę

    - **Kategoria dostawcy** musi być **dostawcy magazynu kluczy**. (wymagane)

> [!NOTE]
> Wymagania dotyczące Twoje środowisko lub organizacji mogą się różnić. Skontaktuj się z ekspertem infrastruktury kluczy publicznych. Szablon certyfikatu musi używać dostawcy magazynu kluczy przeprowadzać CNG jest ważnym wziąć pod uwagę.

Aby uzyskać najlepsze wyniki zaleca się tworzenia nazwy podmiotu, na podstawie informacji usługi Active Directory. Użyj nazwy DNS dla **format nazwy podmiotu** i Dołącz nazwy DNS alternatywnej nazwy podmiotu. W przeciwnym razie należy podać te informacje podczas rejestrowania urządzenia w usłudze na profil certyfikatu.