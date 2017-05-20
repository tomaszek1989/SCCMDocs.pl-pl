---
title: "Utwórz punkt połączenia usługi za pomocą programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Utwórz punkt połączenia usługi za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 9a21d02cb2a50162e5de50481f0f27f2dd7a616c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>Utwórz punkt połączenia usługi z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po utworzeniu subskrypcji można zainstalować rolę systemu lokacji punktu połączenia z usługą, która umożliwia nawiązanie połączenia z usługą Intune. Ta rola systemu lokacji przeprowadzi wypychanie ustawień i aplikacji do usługi Intune.

 Punkt połączenia usługi wysyła ustawienia i informacje o wdrożeniu oprogramowania Configuration Manager i pobiera komunikaty o stanie i spisie z urządzeń przenośnych. Usługi programu Configuration Manager działa jak brama komunikuje się z urządzeniami przenośnymi i przechowująca ustawienia.

> [!NOTE]
>  Rolę systemu lokacji punktu połączenia z usługą można zainstalować tylko w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Punkt połączenia z usługą musi mieć dostęp do Internetu.


## <a name="configure-the-service-connection-point-role"></a>Skonfigurować rolę punktu połączenia usługi

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **witryny**, a następnie kliknij przycisk **serwery i role systemu lokacji**.

3.  Dodaj rolę **Punkt połączenia z usługą** do nowego lub istniejącego serwera systemu lokacji, wykonując odpowiedni krok:

    -   Nowy serwer systemu lokacji: Na **Home** w karcie **Utwórz** , kliknij przycisk **Utwórz serwer systemu lokacji** do uruchomienia Kreatora tworzenia serwera systemu lokacji.

    -   Istniejący serwer systemu lokacji: Kliknij serwer, na którym chcesz zainstalować rolę punktu połączenia usługi. Następnie na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**, aby uruchomić Kreatora dodawania ról systemu lokacji.

4.  Na stronie **Wybór roli systemu** wybierz pozycję **Punkt połączenia z usługą**, a następnie kliknij przycisk **Dalej**.
![Utwórz punkt połączenia usługi](../media/mdm-service-connection-point.png)

* Ukończ pracę kreatora.

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>W jaki sposób punkt połączenia z usługą jest uwierzytelniany w usłudze Microsoft Intune?
 Punkt połączenia usługi rozszerza program Configuration Manager, nawiązując połączenie oparte na chmurze usługi Intune, która zarządza urządzeniami przenośnymi przez Internet. Punkt połączenia usługi uwierzytelniania w usłudze Intune:

1.  Podczas tworzenia subskrypcji usługi Intune w konsoli programu Configuration Manager, administrator programu Configuration Manager jest uwierzytelniany przez łączenie z Azure Active Directory, która przekierowuje do odpowiedniego serwera usług AD FS na monit o podanie nazwy użytkownika i hasła. Następnie Intune wystawia certyfikat dzierżawcy.

2.  Certyfikat z kroku 1 jest instalowany w roli lokacji punktu połączenia z usługą i jest używany w celu uwierzytelniania i autoryzowania całej dalszej komunikacji z usługą Microsoft Intune.

> [!div class="button"]
[< Wstecz kroku](terms-and-conditions.md)[następny krok >  ](enable-platform-enrollment.md)

