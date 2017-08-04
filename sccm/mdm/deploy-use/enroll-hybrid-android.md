---
title: "Konfigurowanie systemu Android hybrydowego zarządzania urządzeniami z programu System Center Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Przygotowanie do zarządzania urządzeniami przenośnymi dla systemu Android za pomocą programu Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: b47ecd1754a623b1b57dc5c5ecb42a6b0b64404e
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami z systemem Android za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie opisano włączyć rejestrowanie hybrydowego Android i Android urządzeń pracy administratora IT. Administrator IT może następnie użyć programu System Center Configuration Manager do zarządzania urządzeniami za pomocą skonfigurowanych subskrypcję Microsoft Intune. Z witryny Google Play użytkownicy mogą pobrać aplikacji portal firmy dla systemu Android, umożliwiającą rejestrowanie urządzeń w pracy Android (w tym Samsung KNOX Standard) i Android.

Jako administrator programu Configuration Manager można zarządzać ustawieniami zgodności, czyszczenia lub usuwać urządzenia Android, wdrażać aplikacje i spisów sprzętu i oprogramowania. Aplikacji Portal firmy dla systemu Android zainstalowane na urządzeniu nie ma możliwości zarządzania, takich jak ustawienia spisów i zgodności, ale nadal można wdrażać aplikacje na urządzeniach z systemem Android.  

## <a name="enable-android-enrollment"></a>Włączanie rejestracji systemu Android  
Poniższe kroki programowi Configuration Manager zarządzanie urządzeniami z systemem Android bez profilu pracy (to znaczy rejestracji "Android klasycznego").

1. Przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy, Zakończ warunki wstępne i procedur w [Instalatora hybrydowego zarządzania urządzeniami Przenośnymi](setup-hybrid-mdm.md).  
2. W konsoli programu Configuration Manager w **administracji** obszaru roboczego wybierz **omówienie** > **usługi w chmurze** > **subskrypcję usługi Microsoft Intune** i wybierz swoją subskrypcję usługi Intune.  
3. Na **Home** karcie **subskrypcji** grupy, wybierz **Konfiguruj platformy** > **Android**.  
4. W **właściwości subskrypcji usługi Microsoft Intune** okno dialogowe Wybierz **Android** i sprawdź **włączyć Android rejestracji** pole.  

> [!NOTE]
>  **Osobiście urządzenia należące do bloku** funkcja jest niedostępna w tej chwili. 

 Po skonfigurowaniu, należy poinformować użytkowników, jak zarejestrować swoje urządzenia. Zobacz [Co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

## <a name="enable-android-for-work-enrollment"></a>Włącz systemu Android dla rejestracji pracy
Poniższe kroki umożliwiają zarządzanie urządzeniami z systemem Android za pomocą profilu pracy w programie Configuration Manager.

1. Utwórz konto Google na https://accounts.google.com/SignUp do użycia jako dla systemu Android dla konta administratora pracy. Lub zaloguj się przy użyciu konta skojarzonego z wszystkich systemu Android dla zadań zarządzania dla tej dzierżawy usługi Intune. To konto może być kontem Google użytkowany przez administratorów, którzy zarządzać urządzeniami z systemem Android. To jest konto Google, używana do zarządzania i publikowanie aplikacji w Play dla konsoli pracy w organizacji. To konto służy do zatwierdzenia aplikacji w Play pracy magazynu, aby zachować informacje o nazwę konta i hasło.
2. Włączanie rejestracji systemu Android przez powiązanie konto Google do dzierżawy usługi Intune, który jest zarządzany w programie Configuration Manager:
   1. W konsoli programu Configuration Manager w **administracji** obszaru roboczego wybierz **omówienie** > **usługi w chmurze** > **subskrypcje usługi Microsoft Intune** i wybierz swoją subskrypcję usługi Intune.
   2. Na **Home** karcie **subskrypcji** grupy, wybierz **Konfiguruj platformy** > **Android for Work**.
   3. W oknie dialogowym wybierz **skonfigurować Android for Work, w konsoli usługi Intune**. W przeglądarce sieci web zostanie otwarta konsola usługi Intune.
   4. Użyj poświadczeń administratora usługi Intune logować się do portalu usługi Intune.
   5. Wybierz **Konfiguruj** otworzyć Android ze sklepu Google Play pracy witryny sieci Web.
   6. Na firmy Google rejestracji wprowadź poświadczenia konta Google z kroku 1, a następnie podaj informacje o Twojej firmie.
3. Po powrocie do portalu usługi Intune Android for Work jest włączony i ma trzy opcje rejestracji dla systemu Android dla pracy urządzeń:
   - **Zarządzanie wszystkimi urządzeniami jako Android** (wyłączone). Wszystkie urządzenia Android, łącznie z urządzeń, które obsługują Android for Work, są rejestrowane jako z konwencjonalnej urządzeń z systemem Android.
   - **Zarządzanie urządzeniami obsługiwane jako Android for Work** (włączone). Wszystkie urządzenia Android for Work są rejestrowane jako systemu Android dla urządzeń w pracy. Urządzenia Android, która nie obsługuje Android for Work jest zarejestrowany jako urządzenie Android konwencjonalnych.
   - **Zarządzanie urządzenia obsługiwane przez użytkowników tylko w tych grupach jako Android for Work** (dla niektórych grup tylko włączone). Umożliwia target Android do zarządzania pracą do określonych użytkowników. Urządzenia, które obsługują Android for Work są rejestrowane jako Android pracy urządzeń tylko wtedy, gdy ich rejestracji członków wybranych grup. Wszystkie inne urządzenia są zarejestrowane jako urządzenia z systemem Android.

> [!NOTE]
> Zapobiega to znany problem **Zarządzaj obsługiwanych urządzeniach użytkowników tylko w tych grupach jako Android for Work** opcję działać zgodnie z oczekiwaniami. Urządzenia użytkowników w określonym zarejestrować grup usługi Azure AD jako Android zamiast Android for Work. Aby włączyć Android for Work, należy użyć **Zarządzanie wszystkich obsługiwanych urządzeń jako Android for Work** opcji.


Po skonfigurowaniu, należy poinformować użytkowników, jak zarejestrować swoje urządzenia. Zobacz [Co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

Po zakończeniu wiązania, zobacz nazwę konta i nazwę organizacji w portalu usługi Intune. W tej chwili możesz zamknąć obie przeglądarki.

### <a name="enroll-an-android-for-work-device"></a>Rejestrowanie dla systemu Android dla pracy urządzenia
Jak rejestrować Twoi użytkownicy systemu Android dla urządzeń pracy jest podobny do rejestracji dla systemu Android. Użytkownicy mogą pobrać i zainstalować aplikację Portal firmy dla systemu Android na swoich urządzeniach przenośnych. Aplikacja wyświetli je, aby utworzyć profil pracy w ramach procesu rejestracji. Po utworzeniu profilu pracy użytkowników przełączyć się do zarządzanej wersji portalu firmy. Zarządzane Portal firmy jest oznaczane małych Aktówki pomarańczowy w prawym dolnym rogu.

### <a name="manage-android-for-work-devices"></a>Zarządzanie Android pracy urządzeń
Po włączeniu systemu Android dla rejestracji pracy można wykonać następujące zadania zarządzania dla systemu Android dla pracy urządzeń:
- [Zatwierdzenie aplikacji](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Tworzenie elementów konfiguracji](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Zarządzanie ustawieniami zgodności](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Zarządzanie profilami poczty e-mail](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Selektywne czyszczenie profilu pracy](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< Wstecz krok](create-service-connection-point.md)[następny krok >  ](set-up-additional-management.md)

