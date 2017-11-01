---
title: "Rozwiązywanie problemów z integracją Lookout"
titleSuffix: Configuration Manager
description: "W tym temacie opisano rozwiązywania problemów, które występują najczęściej w przypadku integracji Lookout."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 244d32e98ad863f6c9ea1747b4f786c3a1279fc0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Rozwiązywanie problemów z integracją Lookout przy użyciu usługi Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

## <a name="troubleshoot-login-errors"></a>Rozwiązywanie problemów z błędami logowania
### <a name="403-errors"></a>błędy 403
Po zalogowaniu się do może zostać wyświetlony błąd 403 [konsoli Lookout MTP](https://aad.lookout.com): **nie masz uprawnień do uzyskania dostępu do usługi** może się to zdarzyć, jeśli podana nazwa użytkownika nie jest członkiem grupy usługi Azure Active Directory (Azure AD), która jest skonfigurowana do dostępu Lookout MTP.

Lookout MTP jest skonfigurowany do zezwalania na grupy tylko użytkownicy z skonfigurowane usługi Azure AD na dostęp. Jeśli nie wiesz, której grupy skonfigurowano dostęp do Lookout MTP, skontaktuj się z obsługą Lookout.

Można się z pomocą techniczną Lookout za pomocą następujących metod:

* Adres e-mail:enterprisesupport@lookout.com
* Zaloguj się do [konsoli z MTP](http://aad.lookout.com), a następnie przejdź do **pomocy technicznej** modułu.
* Przejdź do: https://enterprise.support.lookout.com/hc/requests i Utwórz żądanie obsługi.

### <a name="unable-to-sign-in"></a>Nie można zalogować
Może zostać wyświetlony następujący błąd podczas użytkownika administratora globalnego usługi Azure AD nie zaakceptował początkowej konfiguracji Lookout.

![Zrzut ekranu przedstawiający ekran logowania Lookout przedstawiający logowania z błędami](media/lookout-consent-not-accepted-error.png)

Aby rozwiązać ten problem, administrator globalny musi logowanie do https://aad.lookout.com/les?action=consent i zaakceptować monit do inicjowania instalacji. Bardziej szczegółowe informacje można znaleźć w [konfigurowania subskrypcji z usługą Lookout MTP](set-up-your-subscription-with-lookout.md) tematu

## <a name="troubleshoot-device-status-issues"></a>Rozwiązać problemy dotyczące stanu urządzenia

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Urządzenie nie pojawia się na liście urządzeń konsoli Lookout MTP

Może się tak zdarzyć w jednym z następujących scenariuszy:
* Gdy użytkownik, który jest właścicielem tego urządzenia nie ma w **grupy rejestracji** określony w **Lookout MTP konsoli**.  Z **systemu** modułu, przejdź do **łącznika Intune** karcie i przyjrzyj się **zarządzania rejestracji** ustawienia.  Powinny pojawić się jeden lub więcej grup usługi Azure AD skonfigurowane dla rejestracji.  Sprawdź, czy użytkownik, który jest właścicielem urządzenia brak jest częścią jednego określonego grup usługi Azure AD.  Po dodaniu nowego użytkownika do grupy rejestracji będzie zajmować do skonfigurowanego interwału sondowania (wartość domyślna to 5 minut) aby wyświetlić urządzenia wyświetlani w **urządzeń** modułu Lookout MTP konsoli.

* Jeśli urządzenie jest nieobsługiwany przez usługę Lookout MTP.  Urządzenia, które są nieobsługiwane będą wyświetlane w **urządzenia zarządzane za pośrednictwem** ustawień connector w konsoli Lookout MTP.

### <a name="device-continues-to-be-reported-as-pending"></a>Urządzenie w dalszym ciągu były zgłaszane jako **oczekujące**

Urządzenia, który jest wyświetlany **oczekujące** oznacza, że użytkownik końcowy nie ma otworzyć aplikację Lookout for work aplikacji i dotknięciu **Aktywuj** przycisku. Aby uzyskać więcej informacji na urządzeniu aktywacji za pomocą Lookout pracy aplikacji, przeczytaj temat następujące:

[Zostanie wyświetlony monit o zainstalowanie aplikacji Lookout for Work na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>W konsoli Lookout MTP urządzenie jest wyświetlany jako aktywny, ale nie ma identyfikatora urządzenia.
Oznacza to, że nie jest podana w konsoli Lookout MTP Grupa rejestracji użytkownika będącego właścicielem tego urządzenia.   Urządzenie można uzyskać do tego stanu użytkownika, który jest właścicielem urządzenia został usunięty z grupy rejestracji lub ma grupy rejestracji, do której należy użytkownik został usunięty.

Z **systemu** modułu w konsoli Lookout MTP, przejdź do **łącznika Intune** , a następnie przejrzyj **rejestracji** ustawienia.  Powinny pojawić się jeden lub więcej grup usługi Azure AD skonfigurowane dla rejestracji.  Sprawdź, czy użytkownik, który jest właścicielem urządzenia jest częścią jednej z określonych grup usługi Azure AD.

Gdy urządzenie jest w tym stanie, Lookout będą w dalszym ciągu powiadamia użytkownika o wszelkich zagrożeń wykrył, ale nie będzie wysyłać żadnych informacji o zagrożeniach do usługi Intune.

### <a name="device-shows-disconnected-state"></a>Urządzenie pokazuje stanie rozłączenia

Odłączony oznacza, że Lookout MTP ma niektórzy z urządzenia dla przedziałach czasu wstępnie skonfigurowane (domyślny to 30 dni i co najmniej 7 dni). Oznacza to, czy w aplikacji Portal firmy lub zaczekaj na pracę aplikacji nie jest zainstalowany na urządzeniu lub został odinstalowany. Ponowna instalacja aplikacji powinno rozwiązać ten problem. Gdy użytkownik otwiera aplikację Lookout for Work i aktywuje aplikację resyncs urządzenia z Lookout MTP i Intune.

### <a name="forcing-a-resync-on-the-device"></a>Wymuszanie ponownej synchronizacji na urządzeniu
Z **urządzeń** modułu Lookout MTP konsoli administratora programu można wybrać urządzenie i wybierz go usunąć.   Przy następnym właściciel urządzenia otwiera Zaczekaj na pracę aplikacji i funkcji podsłuchu **Aktywuj**, stan urządzenia spowoduje wykonanie pełnej ponownej synchronizacji.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>Właścicielem urządzenia nie używa już tego urządzenia
Należy wyczyścić urządzenie i poproś nowego użytkownika, aby zarejestrować zgodnie z opisem w [w tym temacie](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe).


Można także przejść do **urządzeń** modułu Lookout MTP konsoli i wybierz polecenie **usunąć**.

Tak długo, jak nowy użytkownik to w jednej z grup rejestracji określone w konsoli Lookout MTP, urządzenie będzie pojawiał się jednokrotnie usługi Azure AD kojarzy urządzenia do nowego użytkownika.

## <a name="compliance-remediation-workflows"></a>Przepływy pracy korygowania zgodności
[Zostanie wyświetlony monit o zainstalowanie aplikacji Lookout for Work na urządzeniu z systemem Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Musisz rozwiązać zagrożenie znaleziono aplikację Lookout for Work na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
