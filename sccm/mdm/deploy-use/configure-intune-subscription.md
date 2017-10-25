---
title: "Skonfiguruj subskrypcję usługi Intune przy użyciu programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Skonfiguruj subskrypcję usługi Intune przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99de8fe7-560e-401a-8ab2-6d87d091be17
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 22d890c972d3166f9c7b583d8d3fa917c1897880
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>Skonfiguruj subskrypcję usługi Intune z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Subskrypcję usługi Intune umożliwia zarządzanie urządzeniami za pośrednictwem Internetu. Obejmuje to określenie, którą kolekcję użytkownika można zarejestrować urządzenia i definiowanie informacje widoczne dla użytkowników. Podczas tworzenia subskrypcji usługi Intune, można również dodać znakowanie firmowe do portalu firmy usługi Intune z logo firmy i kolorów niestandardowych schematów.

Subskrypcja usługi Intune wykonuje następujące działania:

-   Pobiera certyfikat wymagany przez punkt połączenia z usługą do nawiązania połączenia z usługą Intune.
-   Definiuje kolekcję użytkowników, która umożliwia użytkownikom rejestrowanie urządzeń przenośnych.
-   Definiuje i konfiguruje platformy przenośne, które mają być obsługiwane.

> [!IMPORTANT]
>  Tworzenie subskrypcji usługi Microsoft Intune w programie Configuration Manager umieści punkt połączenia z usługą sieci Web w "tryb online". Zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../core/servers/deploy/configure/about-the-service-connection-point.md).

## <a name="to-create-the-microsoft-intune-subscription"></a>Aby utworzyć subskrypcję usługi Microsoft Intune

1.  Załóż konto w usłudze a Microsoft Intune (jeśli jeszcze nie masz takiego konta), korzystając z linku [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216).  Po utworzeniu konta usługi Intune, nie trzeba dodawać żadnych użytkowników do konta usługi Intune lub wykonaj dodatkowe ustawienia konfiguracji.

2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Na karcie **Narzędzia główne** kliknij opcję **Dodaj subskrypcję usługi Microsoft Intune**.

![Utwórz subskrypcję usługi Intune](../media/mdm-set-intune.png)

4.  Zapoznaj się z treścią tekstu wyświetlanego na stronie **Wprowadzenie** kreatora tworzenia subskrypcji usługi Microsoft Intune, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Subskrypcja** kliknij przycisk **Zaloguj się** i zaloguj się za pomocą danych uwierzytelniania swojego konta firmowego lub szkolnego. W **ustaw urząd zarządzania urządzeniami przenośnymi** okno dialogowe, zaznacz pole wyboru, aby tylko zarządzanie urządzeniami przenośnymi za pomocą programu Configuration Manager za pośrednictwem konsoli programu Configuration Manager. Musisz wybrać tę opcję, aby kontynuować subskrypcję.

    > [!IMPORTANT]
    >  Po wybraniu programu Configuration Manager jako swój urząd zarządzania, można zmienić swój urząd zarządzania Microsoft Intune w 1610 wersji programu Configuration Manager lub nowszego i Microsoft Intune version 1705 bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Aby uzyskać więcej informacji, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](/sccm/mdm/deploy-use/change-mdm-authority).

6.  Kliknij linki do zasad zachowania poufności informacji, aby się z nimi zapoznać, a następnie kliknij przycisk **Dalej**.

7.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.

  -   **Kolekcja**: Określ kolekcję użytkowników obejmującą tych użytkowników, którzy będą rejestrować swoje urządzenia przenośne.

      > [!NOTE]
      >  Jeśli użytkownik został usunięty z kolekcji, urządzenia użytkownika będą nadal podlegać zarządzaniu jeszcze przez do 24 godzin, jeśli rekord użytkownika zostanie usunięty z bazy danych użytkownika.

  -   **Nazwa firmy**: Podaj nazwę swojej firmy.

  -   **Adres URL dokumentacji ochrony prywatności**: W przypadku publikowania informacji o prywatności firmie łącza, który jest dostępny z Internetu, podaj łącze, które użytkownicy mogą uzyskać dostęp z portalu firmy, na przykład http://www.contoso.com/CP_privacy.html. W informacjach o zasadach zachowania poufności można objaśnić, jakiego rodzaju informacje użytkownicy udostępniają danej firmie.

  -   **Schemat kolorów portalu firmy**: Opcjonalnie można zmienić domyślny kolor niebieski portali firmy.

  -   **Kod lokacji programu Configuration Manager**: Określ kod lokacji dla lokacji głównej do zarządzania urządzeniami przenośnymi.

    > [!NOTE]
    >  Zmiana kodu lokacji wpływa tylko na nowe rejestracje i nie ma wpływu na istniejące już, zarejestrowane urządzenia.

8.  Na **informacje kontaktowe firmy** Podaj informacje kontaktowe firmy, który będzie wyświetlany użytkownikom w obszarze **kontakt z działem IT** w aplikacji Portal firmy. Podaj informacje kontaktowe firmy, a następnie kliknij przycisk **dalej**.

9. Na **Logo firmy** strony, można wybrać, czy wyświetlane logo w portalu firmy, a następnie kliknij przycisk **dalej**.

10. Ukończ pracę kreatora.

> [!div class="button"]
[< Wstecz krok](confirm-dns.md)[następny krok >  ](terms-and-conditions.md)
