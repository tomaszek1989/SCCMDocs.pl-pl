---
title: "Konfigurowanie subskrypcji usługi Intune przy użyciu programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Skonfiguruj subskrypcję usługi Intune przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99de8fe7-560e-401a-8ab2-6d87d091be17
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 10cc64ae7e4d91f53201c2896b359e77ef04d32d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie subskrypcji usługi Intune z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Subskrypcję usługi Intune umożliwia zarządzanie urządzeniami przez internet. W tym określać kolekcję użytkowników, w których mogą rejestrować urządzenia oraz definiować informacje wyświetlone dla użytkowników. Podczas tworzenia subskrypcji usługi Intune, można również dodać logo do portalu firmy usługi Intune z logo firmy i niestandardowego koloru systemów firmy.

Subskrypcja usługi Intune wykonuje następujące działania:

-   Pobiera certyfikat wymagany przez punkt połączenia z usługą do nawiązania połączenia z usługą Intune.
-   Definiuje kolekcję użytkowników, która umożliwia użytkownikom rejestrowanie urządzeń przenośnych.
-   Definiuje i konfiguruje platformy przenośne, które mają być obsługiwane.

> [!IMPORTANT]
>  Tworzenie subskrypcji usługi Microsoft Intune w programie Configuration Manager będzie pracować punktu połączenia usługi sieci Web w "trybie online." Zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../core/servers/deploy/configure/about-the-service-connection-point.md).

## <a name="to-create-the-microsoft-intune-subscription"></a>Aby utworzyć subskrypcję usługi Microsoft Intune

1.  Załóż konto w usłudze a Microsoft Intune (jeśli jeszcze nie masz takiego konta), korzystając z linku [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216).  Po utworzeniu konta usługi Intune, nie trzeba dodawać żadnych użytkowników do konta usługi Intune lub wykonywania dodatkowych ustawień konfiguracyjnych.

2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Na karcie **Narzędzia główne** kliknij opcję **Dodaj subskrypcję usługi Microsoft Intune**.

![Utwórz subskrypcję usługi Intune](../media/mdm-set-intune.png)

4.  Zapoznaj się z treścią tekstu wyświetlanego na stronie **Wprowadzenie** kreatora tworzenia subskrypcji usługi Microsoft Intune, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Subskrypcja** kliknij przycisk **Zaloguj się** i zaloguj się za pomocą danych uwierzytelniania swojego konta firmowego lub szkolnego. W **ustaw urząd zarządzania urządzeniami przenośnymi** okno dialogowe, wybierz pole wyboru, aby tylko zarządzanie urządzeniami przenośnymi za pomocą programu Configuration Manager za pośrednictwem konsoli programu Configuration Manager. Musisz wybrać tę opcję, aby kontynuować subskrypcję.

    > [!IMPORTANT]
    >  Po wybraniu programu Configuration Manager jako urzędu zarządzania, nie można zmienić urzędu zarządzania Microsoft Intune w przyszłości.

6.  Kliknij linki do zasad zachowania poufności informacji, aby się z nimi zapoznać, a następnie kliknij przycisk **Dalej**.

7.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.

  -   **Kolekcja**: Określ kolekcję użytkownika, która zawiera użytkowników, którzy będą rejestrować urządzenia przenośne.

      > [!NOTE]
      >  Jeśli jakiś użytkownik zostanie usunięty z kolekcji, jego urządzenie będzie podlegać zarządzaniu jeszcze przez do 24 godzin, dopóki rekord użytkownika nie zostanie usunięty z bazy danych użytkownika.

  -   **Nazwa firmy**: Podaj nazwę swojej firmy.

  -   **Adres URL dokumentacji ochrony prywatności**: Jeśli informacje o prywatności firmy są publikowane łącze, które jest dostępny z Internetu, podaj łącze, które użytkownicy mogą korzystać z portalu firmy, na przykład http://www.contoso.com/CP_privacy.html. W informacjach o zasadach zachowania poufności można objaśnić, jakiego rodzaju informacje użytkownicy udostępniają danej firmie.

  -   **Schemat kolorów portalu firmy**: Opcjonalnie można zmienić domyślny kolor niebieski portali firmy.

  -   **Kod lokacji programu Configuration Manager**: Określ kod lokacji dla lokacji głównej do zarządzania urządzeniami przenośnymi.

    > [!NOTE]
    >  Zmiana kodu lokacji wpływa tylko na nowe rejestracje i nie ma wpływu na istniejące już, zarejestrowane urządzenia.

8.  Na **informacje kontaktowe firmy** Określ informacje kontaktowe firmy będzie wyświetlany użytkownikom w ramach **kontakt z działem IT** w aplikacji Portal firmy. Podaj informacje o kontakcie dla swojej firmy, a następnie kliknij przycisk **dalej**.

9. Na **Logo firmy** strony, można wybrać, czy wyświetlić logo w portalu firmy, a następnie kliknij przycisk **dalej**.

10. Ukończ pracę kreatora.

> [!div class="button"]
[< Wstecz kroku](confirm-dns.md)[następny krok >  ](terms-and-conditions.md)

