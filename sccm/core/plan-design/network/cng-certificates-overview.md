---
title: Omówienie certyfikatów CNG
titleSuffix: Configuration Manager
description: Więcej informacji na temat obsługi kryptografii nowej generacji (CNG) certyfikatów dla serwerów i klientów programu Configuration Manager.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: dba904ae-7c44-46db-ae63-999b9821cb46
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4a4f37330f94111bcc41b81d9127039056f69e2b
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cng-certificates-overview"></a>Omówienie certyfikatów CNG
<!-- 1356191 --> 

Menedżer konfiguracji ma ograniczoną obsługę szyfrowania: Certyfikaty następnej generacji (CNG). Klienci programu Configuration Manager mogą używać certyfikatu uwierzytelniania klienta PKI z kluczem prywatnym w dostawcy magazynu kluczy CNG (KSP). Dostawcy magazynu KLUCZY, z obsługą klientów programu Configuration Manager obsługuje oparte na sprzęcie klucza prywatnego, takich jak moduł TPM dostawcy magazynu KLUCZY dla certyfikatów uwierzytelniania klienta PKI.

## <a name="supported-scenarios"></a>Scenariusze obsługiwane
Można użyć [Cryptography API: Nowej generacji (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certyfikatu szablonów w następujących scenariuszach:

- Rejestracja klienta i komunikacji z punktem zarządzania HTTPS   
- Oprogramowanie dystrybucji i wdrażania aplikacji z punktem dystrybucji HTTPS   
- Wdrożenie systemu operacyjnego  
- Wysyłania wiadomości SDK (z najnowszej aktualizacji) oraz Proxy niezależnego dostawcy oprogramowania przez klienta   
- Konfiguracja zarządzania bramy chmury  

Począwszy od wersji 1802, należy użyć certyfikatów CNG dla następujących ról serwera obsługującego protokół HTTPS: <!-- 1357314 -->   
- Punkt zarządzania
- Punkt dystrybucji
- Punkt aktualizacji oprogramowania
- punkt migracji stanu     

> [!NOTE]
> CNG jest zgodne z interfejsu API kryptografii (CAPI). Certyfikaty CAPI w dalszym ciągu obsługiwana nawet wtedy, gdy obsługa CNG jest włączona na komputerze klienckim.

## <a name="unsupported-scenarios"></a>Scenariusze nieobsługiwane

Następujące scenariusze nie są obecnie obsługiwane:

- Następujące role serwera nie są operacyjne zainstalowany w trybie HTTPS przy użyciu certyfikatu CNG powiązany z witryny sieci web w Internet Information Services (IIS): 
    - Usługa sieci web wykazu aplikacji
    - Witryny sieci Web katalogu aplikacji
    - Punkt rejestracji  
    - Punkt proxy rejestracji  

- Program Software Center nie jest wyświetlany w aplikacji i pakietów w zależności od dostępności, które zostały wdrożone dla użytkownika lub kolekcje grupy użytkowników.

- Aby utworzyć punkt dystrybucji w chmurze przy użyciu certyfikatów CNG.

- Jeśli składnika NDES policy module używa certyfikatów CNG do uwierzytelniania klientów, komunikacji z punktu rejestracji certyfikatu zakończy się niepowodzeniem.

- Jeśli określisz certyfikatów CNG, podczas tworzenia nośnika sekwencji zadań, Kreator nie powiodło się tworzenie nośnika rozruchowego.

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