---
title: "Potwierdź wymagania dotyczące nazw domen za pomocą programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Potwierdź wymagania dotyczące nazw domen za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 35b24294073956a6bdb14cae07705f56d31e00a9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="confirm-domain-name-requirements-with-system-center-configuration-manager-and-microsoft-intune"></a>Potwierdź wymagania dotyczące nazw domen za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Jeśli to konieczne, wykonaj następujące kroki do zaspokojenia wszelkich zależności zewnętrznych do programu Configuration Manager:

1. Każdy użytkownik musi mieć licencję Intune przypisane do rejestracji urządzeń. Aby skojarzyć licencji usługi Intune dla użytkowników, każdy użytkownik musi mieć główna nazwa użytkownika (UPN), który może zostać rozwiązany publicznie (na przykład johndoe@contoso.com) lub identyfikator logowania alternatywnej skonfigurowane w usłudze Azure Active Directory. Konfigurowanie Identyfikatora logowania alternatywnego umożliwia użytkownikom zalogować się przy użyciu adresu e-mail, na przykład, nawet jeśli jest ich nazwy UPN w formacie NetBIOS (na przykład CONTOSO\johndoe).

  - Jeśli firma korzysta z możliwej do rozpoznania publicznie UPN (tj. johndoe@contoso.com), nie trzeba już nic jest wymagany.
  - Jeśli firma korzysta z innych niż możliwej do rozpoznania nazwy UPN (tj. CONTOSO\johndoe), należy najpierw [skonfigurować alternatywny identyfikator w usłudze Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync).

2.  Wdrażanie i konfigurowanie usługi Active Directory Federation Services (AD FS). (opcjonalnie)

     Po skonfigurowaniu rejestracji jednokrotnej, użytkownicy mogą się logować za pomocą firmowych poświadczeń dostępu do usług w usłudze Intune.

     Więcej informacji znajduje się w następujących tematach:
    -   [Przygotowanie do rejestracji jednokrotnej](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Planowanie i wdrażanie usług AD FS 2.0 do użytku z rejestracji jednokrotnej](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  Wdrożenie i skonfigurowanie synchronizacji katalogów

     Synchronizacja katalogów pozwala wypełnić Intune z synchronizowane konta użytkowników. Synchronizowane konta użytkowników i grupy zabezpieczeń są dodawane do usługi Intune. Niewłączenie synchronizacji katalogów jest częstą przyczyną niemożności zarejestrowania urządzeń podczas konfigurowania funkcji zarządzania urządzeniami przenośnymi programu Configuration Manager w usłudze Microsoft Intune.

     Więcej informacji znajduje się w temacie [Integracja katalogu](http://go.microsoft.com/fwlink/?LinkID=271120) w bibliotece dokumentacji usługi Active Directory.

4.  Opcjonalne, niezalecane: Jeśli nie używasz usług federacyjnych Active Directory, zresetuj hasła użytkowników witryny Microsoft Online.

     Jeśli nie używasz usług AD FS, musisz ustawić hasło dla każdego użytkownika witryny Microsoft Online.

> [!div class="button"]
[< Wstecz kroku](create-mdm-collection.md)[następny krok >  ](configure-intune-subscription.md)

