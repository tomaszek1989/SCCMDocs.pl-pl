---
title: "Konfigurowanie zarządzania urządzeniami hybrydowe Android za pomocą programu System Center Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Przygotowanie do zarządzania Android urządzeniami przenośnymi za pomocą programu Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 03/27/2017
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: 0e93cd55ce49afb6395dcbe758c933bf509dd367
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami z systemem Android za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie opisano administratora IT, Włącz rejestrowanie hybrydowe Android i Android pracy urządzeń. Administrator IT można następnie użyć programu System Center Configuration Manager do zarządzania urządzeniami za pośrednictwem skonfigurowany subskrypcję Microsoft Intune. Z witryny Google Play użytkownicy mogą pobrać aplikację portalu firmy Android, umożliwiającą rejestrowanie pracy urządzeń Android (w tym Samsung KNOX Standard) i Android. 

Jako administrator programu Configuration Manager można zarządzać ustawieniami zgodności, czyścić lub usuwać urządzenia Android, wdrażać aplikacje i spisów sprzętu i oprogramowania. Jeśli aplikacja portalu firmy Android nie jest zainstalowany na urządzeniach, następnie nie ma możliwości zarządzania (takich jak ustawienia spisów i zgodności), ale nadal można wdrażać aplikacje na urządzeniach Android.  

## <a name="enable-android-enrollment"></a>Włącz rejestrowanie dla systemu Android  
Następujące kroki umożliwiają zarządzanie urządzeniami systemu Android, bez profilu pracy (czyli rejestracji "Android klasycznego") programu Configuration Manager.

1. Przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy, Zakończ warunki wstępne i procedur w [Instalatora hybrydowe MDM](setup-hybrid-mdm.md).  
2. W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, wybierz **Przegląd** > **usług w chmurze** > **subskrypcja usługi Microsoft Intune** i wybierz subskrypcję usługi Intune.  
3. Na **Home** karcie w **subskrypcji** grupy, wybierz **Konfiguruj platformy** > **Android**.  
4. W **właściwości subskrypcji usługi Microsoft Intune** okno dialogowe Wybierz **Android** i sprawdź **rejestracji włączyć Android** pole.  

 Po skonfigurowaniu, należy umożliwić użytkownikom wiedzieć, jak zarejestrować swoje urządzenia. Zobacz [Co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

## <a name="enable-android-for-work-enrollment"></a>Włącz Android do pracy rejestracji
Następujące kroki umożliwiają zarządzanie urządzeniami systemu Android, bez profilu pracy (czyli rejestracji "Android klasycznego") programu Configuration Manager.

1. Utwórz konto Google w https://accounts.google.com/SignUp do użycia jako Android Twoje konto administratora pracy. Lub zaloguj się przy użyciu konta, które zostaną skojarzone z wszystkich Android dla zadania zarządzania dla tej dzierżawy usługi Intune. Może to być konto Google współużytkowany Administratorzy, którzy zarządzanie urządzeniami z systemem Android. To konto Google, używana do zarządzania i publikowania aplikacji w Play dla konsoli pracy w organizacji. Aby zatwierdzić aplikacje w grę dla sklepu pracy, więc śledzić wpisywane nazwę konta i hasło będzie używał tego konta.
2. Włączanie rejestracji Android przez powiązanie konta Google dzierżawcy usługi Intune, który jest zarządzany w programie Configuration Manager:
   1. W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, wybierz **Przegląd** > **usług w chmurze** > **subskrypcje usługi Microsoft Intune** i wybierz subskrypcję usługi Intune.
   2. Na **Home** karcie w **subskrypcji** grupy, wybierz **Konfiguruj platformy** > **Android pracy**.
   3. W oknie dialogowym wybierz **skonfigurować Android do pracy w konsoli usługi Intune**. W przeglądarce sieci web zostanie otwarta konsola usługi Intune.
   4. Użyj poświadczeń administratora usługi Intune do logowania się do portalu Intune.
   5. Wybierz **Konfiguruj** otworzyć Android Google Play dla pracy witryny sieci Web.
   6. Firmy Google logowania na stronie wprowadź poświadczenia konta Google z kroku 1, a następnie podaj informacje o firmie.
3. Po powrocie do portalu Intune Android pracy jest włączona i ma trzy opcje rejestracji dla systemu Android dla pracy urządzeń:
   - **Zarządzanie urządzeniami wszystkie jako Android** (wyłączony). Wszystkie urządzenia Android, w tym urządzeń, które obsługują Android do pracy, są rejestrowane jako konwencjonalne urządzenia z systemem Android.
   - **Zarządzanie urządzeniami obsługiwane jako Android pracy** (włączona). Wszystkie urządzenia Android do pracy są rejestrowane jako Android dla urządzeń w pracy. Wszelkie urządzenia Android, który nie obsługuje Android do pracy jest zarejestrowany jako urządzenie konwencjonalnych Android.
   - **Zarządzanie obsługiwane urządzenia dla użytkowników tylko w tych grupach jako Android pracy** (dla niektórych grup tylko włączone). Umożliwia Android są przeznaczone do pracy zarządzania ograniczony zestaw użytkowników. Urządzenia obsługujące Android do pracy są rejestrowane jako Android urządzeń pracy tylko wtedy, gdy członków wybranych grup zarejestrować je. Wszystkie inne urządzenia są rejestrowane jako urządzenia z systemem Android.

> [!NOTE]
> Zapobiega to znany problem **Zarządzaj obsługiwane urządzenia dla użytkowników tylko w tych grupach jako Android pracy** opcję działać zgodnie z oczekiwaniami. Urządzenia użytkowników w określonej usłudze Azure AD będą rejestrować grup jako Android zamiast Android do pracy. Aby włączyć Android do pracy, należy użyć **Zarządzanie wszystkich obsługiwanych urządzeń jako Android pracy** opcji.


Po skonfigurowaniu, należy umożliwić użytkownikom wiedzieć, jak zarejestrować swoje urządzenia. Zobacz [Co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

Nazwa konta i nazwę organizacji w portalu Intune zostaną wyświetlone po zakończeniu powiązanie. W tym momencie możesz zamknąć obie przeglądarki.

### <a name="enroll-an-android-for-work-device"></a>Rejestrowanie Android pracy urządzenia
Jak użytkownicy rejestrują Android urządzeń pracy jest podobne do rejestracji dla systemu Android. Użytkownicy mogą pobrać i zainstalować aplikację Portal firmy dla systemu Android na swoich urządzeniach przenośnych. Aplikacja wyświetli je w celu utworzenia profilu pracy w ramach procesu rejestracji. Po utworzeniu profilu pracy użytkowników musi przełączyć się do zarządzanego wersji portalu firmy. Zarządzanych aplikacji Portal firmy jest oznaczane małe Aktówki pomarańczowy w prawym dolnym rogu.

### <a name="manage-android-for-work-devices"></a>Zarządzanie Android pracy urządzeń
Po włączeniu Android do rejestracji pracy można wykonać następujące zadania zarządzania dla systemu Android dla pracy urządzeń:
- [Zatwierdzenie aplikacji](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Tworzenie elementów konfiguracji](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Zarządzanie ustawieniami zgodności](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Zarządzaj profilami e-mail](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Selektywnie wyczyść profilu pracy](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< Wstecz kroku](create-service-connection-point.md)[następny krok >  ](set-up-additional-management.md)

