---
title: "Rozwiązywanie problemów z integracją ewentualnym | System Center Configuration Manager"
description: "W tym temacie opisano rozwiązywanie problemów z najczęściej występujące z ewentualnym integracji."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4fd2d3b8aae6a2f42e7c6a87723d16368be30984
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Rozwiązywanie problemów z ewentualnym integracji z usługą Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

## <a name="troubleshoot-login-errors"></a>Rozwiązywanie problemów logowania
### <a name="403-errors"></a>403 błędy
Może być widoczny błąd 403 podczas logowania się [konsoli MTP ewentualnym](https://aad.lookout.com): **nie masz uprawnień do uzyskania dostępu do usługi** może się tak zdarzyć, jeśli podana nazwa użytkownika nie jest członkiem grupy Azure Active Directory (Azure AD), która jest skonfigurowana do dostępu do MTP szczególną.

Ewentualnym MTP skonfigurowano pozwalają grupować tylko użytkownicy z skonfigurowanej usługi Azure AD na dostęp. Jeśli nie wiesz, grupy, do której jest skonfigurowany z dostępem do MTP szczególną, skontaktuj się z obsługą szczególną.

Można się z pomocą techniczną ewentualnym za pomocą następujących metod:

* Adres e-mail:enterprisesupport@lookout.com
* Logowanie do [konsoli MTP](http://aad.lookout.com)i przejdź do **Obsługa** modułu.
* Przejdź do: https://enterprise.support.lookout.com/hc/en-us/requests i sprawdź żądania pomocy technicznej.

### <a name="unable-to-sign-in"></a>Nie można się zalogować
Podczas użytkownika administratora globalnego usługi Azure AD nie zaakceptował początkowej konfiguracji szczególną może się pojawić następujący błąd.

![Zrzut ekranu przedstawiający ekran logowania ewentualnym przedstawiający błąd logowania](media/lookout-consent-not-accepted-error.png)

Aby rozwiązać ten problem, administrator globalny musi logowanie do https://aad.lookout.com/les?action=consent i zaakceptować monit do inicjowania instalacji. Bardziej szczegółowe informacje można znaleźć w [skonfigurowaniu subskrypcji przy użyciu protokołu MTP ewentualnym](set-up-your-subscription-with-lookout.md) tematu

## <a name="troubleshoot-device-status-issues"></a>Rozwiązywanie problemów stanu urządzenia

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Urządzenie nie pojawia się na liście urządzeń MTP ewentualnym konsoli

Taka sytuacja może wystąpić w jednej z następujących scenariuszy:
* Kiedy użytkownik, który jest właścicielem tego urządzenia nie znajduje się w **grupy rejestracji** określone w **konsoli MTP ewentualnym**.  Z **systemu** modułu, przejdź do **łącznik usługi Intune** karcie i przyjrzyj się **zarządzania rejestracji** ustawienia.  Powinien zostać wyświetlony skonfigurowany dla rejestracji jedną lub więcej grup usługi Azure AD.  Sprawdź, czy użytkownik, który jest właścicielem urządzenia Brak część jednej z określonej grupy usługi Azure AD.  Po dodaniu nowego użytkownika do grupy rejestracji będzie zajmować do skonfigurowanego interwału sondowania (wartość domyślna to 5 minut) aby wyświetlić urządzenia są wyświetlane w **urządzeń** modułu ewentualnym MTP konsoli.

* Jeśli urządzenie nie jest obsługiwana przez ewentualnym MTP.  Urządzenia, które są nieobsługiwane będą wyświetlane w **urządzenia zarządzane** sekcji Ustawienia łącznika na konsoli MTP szczególną.

### <a name="device-continues-to-be-reported-as-pending"></a>Urządzenie będzie nadal raportowane jako **oczekujące**

Urządzenia, które jest wyświetlane **oczekujące** oznacza, że użytkownik końcowy nie otworzył szukać pracę aplikacji i obszar **uaktywnienia** przycisku. Aby uzyskać więcej informacji na urządzeniu aktywacji z ewentualnym pracy aplikacji, przeczytaj temat następujące:

[Zostanie wyświetlony monit o zainstalowanie szukać pracy na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>W konsoli MTP ewentualnym urządzenie jest wyświetlany jako aktywny, ale nie ma identyfikatora urządzenia.
Oznacza to, że nie jest w grupie rejestracji określone w konsoli MTP ewentualnym użytkownika będącego właścicielem tego urządzenia.   Urządzenia można uzyskać w ten stan jest ma grupy rejestracji, do której należy użytkownik lub użytkownika, który jest właścicielem urządzenia został usunięty z grupy rejestracji został usunięty.

Z **systemu** modułu na konsoli MTP ewentualnym przejdź do **łącznik usługi Intune** , a następnie przejrzyj **rejestracji** ustawienia.  Powinien zostać wyświetlony skonfigurowany dla rejestracji jedną lub więcej grup usługi Azure AD.  Sprawdź, czy użytkownik, który jest właścicielem urządzenia część jednej z określonych grup Azure AD.

Gdy urządzenie jest w tym stanie, będzie powiadamiać użytkownika o wszelkich zagrożeń wykryto szczególną, ale nie będą wysyłały żadnych informacji do usługi Intune.

### <a name="device-shows-disconnected-state"></a>Pokazuje urządzenie stanie rozłączenia

Odłączony oznacza, że MTP ewentualnym nie ma heard z urządzenia dla przedziałach czasu wstępnie skonfigurowane (wartość domyślna to 30 dni z co najmniej 7 dni). Oznacza to, że aplikacji Portal firmy lub szukać pracy aplikacji nie jest zainstalowany na urządzeniu lub został odinstalowany. Ponowne zainstalowanie aplikacji, należy rozwiązać ten problem. Gdy użytkownik otwiera szukać pracy i aktywuje aplikację, resyncs urządzenia przy użyciu protokołu MTP ewentualnym i Intune.

### <a name="forcing-a-resync-on-the-device"></a>Wymuszenie ponownej synchronizacji na urządzeniu
Z **urządzeń** modułu MTP ewentualnym konsoli administratora można wybrać urządzenie i wybierz go usunąć.   Przy następnym uruchomieniu właściciel urządzenia otwiera szukać pracę aplikacji i krany **uaktywnienia**, stan urządzenia spowoduje wykonanie pełnej ponownej synchronizacji.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>Użytkownik urządzenia nie używa już tego urządzenia
Należy czyścić urządzenie i poproś nowego użytkownika, aby zarejestrować zgodnie z opisem w [w tym temacie](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe).


Można także przejść do **urządzeń** modułu konsoli MTP ewentualnym i wybierz polecenie **usunąć**.

Tak długo, jak nowy użytkownik znajduje się w jednej z tych grup rejestracji określone w konsoli MTP szczególną, urządzenie pojawią się po Azure AD kojarzy urządzenia do nowego użytkownika.

## <a name="compliance-remediation-workflows"></a>Przepływy pracy korygowania zgodności
[Zostanie wyświetlony monit o zainstalowanie szukać pracy na urządzeniu z systemem Android]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Należy rozwiązać zagrożeniem szukać pracy znalezione na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

