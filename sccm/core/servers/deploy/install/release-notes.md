---
title: Informacje o wersji
titleSuffix: Configuration Manager
description: Więcej informacji na temat pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie lub omówione w artykule bazy wiedzy Microsoft Knowledge Base.
ms.date: 04/18/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4aeacdbc73e21c3bae18111e22c8407eba865a87
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Informacje o wersji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programu Configuration Manager informacje o wersji produktu są ograniczone do pilnych problemów. Te problemy nie są jeszcze rozwiązane w produkcie lub szczegółowo opisane w artykule bazy wiedzy Microsoft Knowledge Base.  

Dokumentacja właściwych dla funkcji zawiera informacje o znanych problemach, które mają wpływ na podstawowe scenariusze.  

> [!TIP]  
>  Ten temat zawiera informacje o wersji dla bieżącej gałęzi programu Configuration Manager. Informacje dotyczące gałęzi wersji zapoznawczej technical preview, sekcji [Technical Preview programu System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Aby uzyskać informacje o nowych funkcjach wprowadzona z różnymi wersjami zobacz następujące artykuły:
- [Co nowego w wersji 1802](/sccm/core/plan-design/changes/whats-new-in-version-1802)
- [Co nowego w wersji 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [Co nowego w wersji 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  



## <a name="setup-and-upgrade"></a>Instalowanie i uaktualnianie  


### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>Korzystając z pliki redystrybucyjne z dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu błędu weryfikacji manifestu
<!-- 510080, 490569  -->

W przypadku uruchamiania Instalatora z dysku CD. Najnowszy folder utworzona dla wersji 1606 i użyj pakietu redystrybucyjnego plików uwzględnionych w tym dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu następujących błędów w dzienniku instalacji programu Configuration Manager:

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

#### <a name="workaround"></a>Obejście
Użyj jednej z następujących opcji:
 - Podczas instalacji należy wybrać pobrać najnowsze pliki redystrybucyjne firmy Microsoft. Użyj najnowszych plików pakietu redystrybucyjnego zamiast plików znajdujących się na dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.


### <a name="setup-command-line-option-joinceip-must-be-specified"></a>Ustawienia opcji wiersza polecenia musi być określona JoinCEIP
<!--510806-->
*Dotyczy: 1802 wersji programu Configuration Manager*

Począwszy od programu Configuration Manager w wersji 1802 funkcji programu poprawy jakości obsługi klienta (CEIP) zostaną usunięte z produktu. Gdy [automatyzacji instalacji](/sccm/core/servers/deploy/install/command-line-options-for-setup) ze skryptu wiersza polecenia lub instalacji nienadzorowanej nowej lokacji, Instalator zwraca błąd brakuje wymaganego parametru. 

#### <a name="workaround"></a>Obejście
Gdy go nie ma wpływu na wyniki procesu instalacji, obejmują **JoinCEIP** parametru w wierszu polecenia Instalatora.

 > [!Note]  
 > Parametr EnableSQM [instalacji konsoli](/sccm/core/servers/deploy/install/install-consoles) nie jest wymagana.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów

### <a name="azure-ad-enabled-clients-cant-communicate-with-management-point"></a>Klienci z obsługą usługi AD platformy Azure nie może komunikować się z punktem zarządzania
<!--501089-->
*Dotyczy: 1706 wersji programu Configuration Manager*
<!--also fixed in 1710 HFRU-->
W tym scenariuszu do [zainstalować i przypisać przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure), komunikacji z klientem zakończy się niepowodzeniem, kiedy punkt zarządzania z włączonym protokołem HTTPS korzysta z poświadczenia alternatywne wartości bazy danych. 

#### <a name="workaround"></a>Obejście
Zminimalizować ten problem z jedną z następujących czynności:
- Aktualizacja lokacji do najnowszej wersji i Zastosuj najnowsze poprawki
- Zmiana poświadczeń używanych przez punkt zarządzania.


<!-- ## Operating system deployment  -->



## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>Plany obsługi tworzą wiele powielonych grup aktualizacji oprogramowania i wdrożeń domyślnie  
<!-- 474326 -->
Domyślnie kreator tworzenia planów obsługi jest uruchamiany obecnie po każdej synchronizacji aktualizacji oprogramowania. Przy każdym uruchomieniu tworzy on nową grupę aktualizacji oprogramowania i wdrożenia. Jeśli masz harmonogramu synchronizacji aktualizacji oprogramowania, który uruchamia kilka razy dziennie, Kreator tworzenia planów obsługi tworzy wiele grup aktualizacji oprogramowania i wdrożeń każdego dnia.  

#### <a name="workaround"></a>Obejście
 po utworzeniu planu obsługi otwórz właściwości planu, przejdź do karty **Harmonogram szacowania**, wybierz pozycję **Uruchom tę regułę według harmonogramu**, kliknij pozycję **Dostosuj** i utwórz harmonogram niestandardowy. Można na przykład określić uruchamianie planu obsługi co 60 dni.  


### <a name="changing-office-365-client-setting-doesnt-apply"></a>Zmiana usługi Office 365 ustawienie klienta nie ma zastosowania 
<!--511551-->
*Dotyczy: 1802 wersji programu Configuration Manager*  

Wdrażanie [ustawienia klienta](/sccm/core/clients/deploy/about-client-settings#enable-management-of-the-office-365-client-agent) z **Włącz zarządzanie agenta klienta Office 365** skonfigurowany tak, aby `Yes`. Następnie zmienić to ustawienie, aby `No` lub `Not Configured`. Po zaktualizowaniu zasad na docelowych komputerach klienckich, aktualizacji usługi Office 365 są nadal zarządzane przez program Configuration Manager. 

#### <a name="workaround"></a>Obejście
Zmień poniższej wartości rejestru w celu `0` i uruchom ponownie **usługi kliknij program Microsoft Office** (ClickToRunSvc):

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\office\16.0\Common\officeupdate]
"OfficeMgmtCOM"=dword:00000000
```



## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10"></a>Nie można wdrażać profile sieci VPN programu Windows Phone 8.1 do systemu Windows 10
<!-- 503274  -->
*Dotyczy: 1710 wersji programu Configuration Manager*

Nie można utworzyć profil sieci VPN za pomocą przepływu pracy systemu Windows Phone 8.1, która jest również dotyczy urządzeń z systemem Windows 10. Dla tych profilów Kreator tworzenia nie jest już wyświetlana na stronie obsługiwane platformy. Windows Phone 8.1 jest automatycznie wybierany na zaplecza. Na stronie obsługiwane platformy są dostępne we właściwościach profilu, ale nie wyświetla opcje systemu Windows 10.

#### <a name="workaround"></a>Obejście
 Użyj przepływu pracy profilu sieci VPN systemu Windows 10 dla urządzeń z systemem Windows 10. Jeśli ta opcja nie jest możliwe w danym środowisku, należy się z pomocą techniczną. Obsługa ułatwia dodawanie przeznaczonych dla systemu Windows 10.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
