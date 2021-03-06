---
title: Potwierdź wymagania dotyczące nazw domen
titleSuffix: Configuration Manager
description: Potwierdź wymagania dotyczące nazw domen przy użyciu programu System Center Configuration Manager.
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f82f8e782446035ffdf3910cb591e07f61fbfb47
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="confirm-domain-name-requirements-with-system-center-configuration-manager-and-microsoft-intune"></a>Potwierdź wymagania dotyczące nazw domen z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli to konieczne, wykonaj następujące kroki, aby uzgodnić wszelkie zależności zewnętrznych do programu Configuration Manager:

1. Każdy użytkownik musi mieć licencję usługi Intune, przypisać do rejestracji urządzeń. Aby skojarzyć licencji usługi Intune dla użytkowników, każdy użytkownik musi mieć nazwę podmiotu zabezpieczeń użytkownika (UPN), które może przyjąć publicznie (na przykład johndoe@contoso.com) lub alternatywnego Identyfikatora logowania skonfigurowane w usłudze Azure Active Directory. Konfigurowanie alternatywnego Identyfikatora logowania umożliwia użytkownikom logowanie za pomocą adresu e-mail, na przykład, nawet jeśli ich nazwy UPN w formacie NetBIOS (na przykład CONTOSO\johndoe).

  - Jeśli firma korzysta z publicznie rozwiązywanej nazwy UPN (tj. johndoe@contoso.com), jest wymagana żadna dalsza konfiguracja.
  - Jeśli firma korzysta z nie można rozpoznać nazwy UPN (tj. CONTOSO\johndoe), należy najpierw [Konfigurowanie alternatywnego Identyfikatora w usłudze Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync).

2.  Wdrażanie i konfigurowanie usługi Active Directory Federation Services (AD FS). (opcjonalnie)

     Po skonfigurowaniu logowania jednokrotnego, użytkownicy będą mogli logować się przy użyciu swoich poświadczeń firmowych w celu uzyskiwania dostępu do usług w usłudze Intune.

     Więcej informacji znajduje się w następujących tematach:
    -   [Przygotowanie do rejestracji jednokrotnej](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Planowanie i wdrażanie usług AD FS 2.0 do użytku z logowania jednokrotnego](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  Wdrożenie i skonfigurowanie synchronizacji katalogów

     Synchronizacja katalogów pozwala wypełnić usługę Intune z synchronizowane konta użytkowników. Synchronizowane konta użytkowników i grupy zabezpieczeń zostaną dodane do usługi Intune. Niewłączenie synchronizacji katalogów jest częstą przyczyną niemożności zarejestrowania urządzeń podczas konfigurowania funkcji zarządzania urządzeniami przenośnymi programu Configuration Manager w usłudze Microsoft Intune.

     Więcej informacji znajduje się w temacie [Integracja katalogu](http://go.microsoft.com/fwlink/?LinkID=271120) w bibliotece dokumentacji usługi Active Directory.

4.  Opcjonalne, niezalecane: Jeśli nie używasz usług federacyjnych Active Directory, zresetuj hasła użytkowników witryny Microsoft Online.

     Jeśli nie używasz usług AD FS, musisz ustawić hasło dla każdego użytkownika witryny Microsoft Online.

> [!div class="button"]
[< Wstecz krok](create-mdm-collection.md)[następny krok >](configure-intune-subscription.md)
