---
title: "Utwórz punkt połączenia usługi"
titleSuffix: Configuration Manager
description: "Utwórz punkt połączenia usługi przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 9ae26c55cf92c954a54311e2e698353bbe359a83
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>Utwórz punkt połączenia usługi z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po utworzeniu subskrypcji można zainstalować rolę systemu lokacji punktu połączenia z usługą, która umożliwia nawiązanie połączenia z usługą Intune. Ta rola systemu lokacji przeprowadzi wypychanie ustawień i aplikacji do usługi Intune.

 Punkt połączenia z usługą wysyła ustawienia i informacje o wdrożeniu oprogramowania do programu Configuration Manager i pobiera komunikaty o stanie i spisie z urządzeń przenośnych. Usługi programu Configuration Manager działa jak brama komunikująca się z urządzeniami przenośnymi i przechowująca ustawienia.

> [!NOTE]
>  Rolę systemu lokacji punktu połączenia z usługą można zainstalować tylko w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Punkt połączenia z usługą musi mieć dostęp do Internetu.


## <a name="configure-the-service-connection-point-role"></a>Skonfiguruj rolę punktu połączenia usługi

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W **administracji** obszaru roboczego, rozwiń węzeł **witryny**, a następnie kliknij przycisk **serwery i role systemu lokacji**.

3.  Dodaj rolę **Punkt połączenia z usługą** do nowego lub istniejącego serwera systemu lokacji, wykonując odpowiedni krok:

    -   Nowy serwer systemu lokacji: Na **Home** karcie **Utwórz** kliknij przycisk **Utwórz serwer systemu lokacji** można uruchomić Kreatora tworzenia serwera systemu lokacji.

    -   Istniejący serwer systemu lokacji: Kliknij serwer, na którym chcesz zainstalować rolę punktu połączenia usługi. Następnie na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**, aby uruchomić Kreatora dodawania ról systemu lokacji.

4.  Na stronie **Wybór roli systemu** wybierz pozycję **Punkt połączenia z usługą**, a następnie kliknij przycisk **Dalej**.
![Utwórz punkt połączenia usługi](../media/mdm-service-connection-point.png)

* Ukończ pracę kreatora.

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>W jaki sposób punkt połączenia z usługą jest uwierzytelniany w usłudze Microsoft Intune?
 Punkt połączenia z usługą rozszerza program Configuration Manager, nawiązując połączenie do usługi Intune w opartej na chmurze, która zarządza urządzeniami przenośnymi za pośrednictwem Internetu. Punkt połączenia usługi służy do uwierzytelniania w usłudze Intune w następujący sposób:

1.  Podczas tworzenia subskrypcji usługi Intune w konsoli programu Configuration Manager, administrator programu Configuration Manager jest uwierzytelniany przez nawiązanie połączenia usługi Azure Active Directory, która przekierowuje do odpowiedniego serwera ADFS w celu monitowania o nazwę użytkownika i hasło. Następnie Intune wystawia certyfikat dzierżawcy.

2.  Certyfikat z kroku 1 jest instalowany w roli lokacji punktu połączenia z usługą i jest używany w celu uwierzytelniania i autoryzowania całej dalszej komunikacji z usługą Microsoft Intune.

> [!div class="button"]
[< Wstecz krok](terms-and-conditions.md)[następny krok >  ](enable-platform-enrollment.md)
