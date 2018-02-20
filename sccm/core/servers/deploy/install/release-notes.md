---
title: 'Informacje o wersji '
titleSuffix: Configuration Manager
description: "Te informacje można uzyskać pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie lub omówione w artykule bazy wiedzy Microsoft Knowledge Base."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 53685ef2647cfd87c2fcb603097186360f1c96a5
ms.sourcegitcommit: fbd4a9d2fa8ed4ddd3a0fecc4a2ec4fc0ccc3d0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Informacje o wersji dla programu System Center Configuration Manager

Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programu Configuration Manager informacje o wersji produktu są ograniczone do pilnych problemów. Te problemy nie zostały jeszcze rozwiązane w produkcie, lub szczegółowo opisane w artykule bazy wiedzy Microsoft Knowledge Base.  

Dokumentacja właściwych dla funkcji zawiera informacje o znanych problemach, które mają wpływ na podstawowe scenariusze.  

> [!TIP]  
>  Ten temat zawiera informacje o wersji dla bieżącej gałęzi programu Configuration Manager. Informacje dotyczące gałęzi wersji zapoznawczej technical preview, sekcji [Technical Preview programu System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Aby uzyskać informacje o nowych funkcjach wprowadzona z różnymi wersjami zobacz następujące artykuły:
- [Co nowego w wersji 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [Co nowego w wersji 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [Co nowego w wersji 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)



## <a name="setup-and-upgrade"></a>Instalowanie i uaktualnianie  


### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Podczas instalowania lokacji oddziału usługi długoterminowe przy użyciu wersji 1606, Current Branch lokacji jest zainstalowany
<!-- Consider move to core content  -->
Użycie nośnika linii bazowej 1606 wersji z października 2016 wersji aby zainstalować lokację długoterminowe Servicing Branch (LTSB), instalacja lokacji bieżącej gałęzi zamiast tego. Dzieje się tak, ponieważ nie wybrano opcję zainstalowania punktu połączenia usługi w ramach instalacji lokacji.

 - Punkt połączenia usługi nie jest wymagany, musi ona zostać wybrana do zainstalowania podczas instalacji, aby zainstalować lokację LTSB.

Po zakończeniu instalacji można odinstalować punkt połączenia usługi. Jednak musi mieć połączenie usługi punktu w trybie offline lub online do przesyłania danych telemetrycznych i Pobierz aktualizacje zabezpieczeń dla bieżącej gałęzi i LTSB witryny.

Jeśli witryny zainstalowany w lokacji bieżącej gałęzi, ale trzeba zainstalować LTSB, należy odinstalować lokację i zainstaluj go ponownie. Alternatywnie możesz wywołać [Microsoft Help i pomocy technicznej](http://go.microsoft.com/fwlink/?LinkId=243064) Aby uzyskać pomoc.  

Aby upewnić się, która gałąź zainstalowane, w konsoli pod adresem **administracji** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Opcja skonwertuje wówczas lokację do lokacji bieżącej gałęzi jest dostępna tylko w przypadku, gdy w lokacji działa LTSB.  

**Obejście problemu:** Brak.   


### <a name="an-update-persists-in-downloading-state-in-the-updates-and-servicing-node-of-the-console"></a>Aktualizacja utrzymuje się pobieranie stanu w węźle aktualizacje i obsługa konsoli programu  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
Podczas automatycznego pobierania aktualizacji przez punkt połączenia usługi online aktualizacja może zostać wstrzymana ze stanem pobieranie. W przypadku wstrzymania aktualizacji podczas pobierania we wskazanych plikach dziennika wyświetlane są pozycje podobne do poniższych:  

Dziennik DMPdownloader:  
`ERROR: Failed to download redist for 037cd17e-4d7b-40e1-802b-14bb682364c7 with command  /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 /RedistVersion 112015 /NoUI  "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"`  

ConfigMgrSetup.log:  
`Error: failed to verify 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi' authenticode signature.`  
`Error: file signature check failed for 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi`  

**Obejście**: Na serwerze lokacji zmodyfikuj następujący klucz rejestru, aby pasowała do następujących wartości:  

-   **Klucz do edycji**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software publikowania  

-   **Wartość stanu**: Ustaw **146944** dziesiętną lub **0x00023e00** szesnastkowe  

Następnie należy uruchomić ponownie usługę SMS_Executive lub poczekaj maksymalnie 24 godziny na następny cykl pobierania automatycznego.

### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>Korzystając z pliki redystrybucyjne z dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu błędu weryfikacji manifestu
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

W przypadku uruchamiania Instalatora z dysku CD. Najnowszy folder utworzona dla wersji 1606 i użyj pakietu redystrybucyjnego plików uwzględnionych w tym dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu następujących błędów w dzienniku instalacji programu Configuration Manager:

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

**Obejście problemu:** Użyj jednej z następujących opcji:
 - Podczas instalacji należy wybrać pobrać najnowsze pliki redystrybucyjne firmy Microsoft. Użyj najnowszych plików pakietu redystrybucyjnego zamiast plików znajdujących się na dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Instalacja klienta kończy się niepowodzeniem z kodem błędu 0x8007064c
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*Następujący problem dotyczy wszystkie aktywne wersje programu Configuration Manager.*  

Podczas wdrażania klienta na komputerach z systemem Windows, instalacja nie powiedzie się. Plik ccmsetup.log zawiera następujące wpisy: 

`File 'C:\WINDOWS\ccmsetup\Silverlight.exe' returned failure exit code 1612. Fail the installation`  
`InstallFromManifest failed 0x8007064c`

**Obejście**: Uszkodzony, zainstalowanych wcześniej wersji Silverlight powoduje, że ten problem. Aby rozwiązać ten problem, należy uruchomić następujące narzędzia na danym komputerze: [Naprawianie problemów, które blokować programom jest instalowana lub usuwana](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed).

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>Plany obsługi tworzą wiele powielonych grup aktualizacji oprogramowania i wdrożeń domyślnie  
Domyślnie kreator tworzenia planów obsługi jest uruchamiany obecnie po każdej synchronizacji aktualizacji oprogramowania. Przy każdym uruchomieniu tworzy on nową grupę aktualizacji oprogramowania i wdrożenia. Jeśli masz harmonogramu synchronizacji aktualizacji oprogramowania uruchamia się wiele razy dziennie, Kreator tworzenia planów obsługi tworzy wiele grup aktualizacji oprogramowania i wdrożeń każdego dnia.  

**Obejście**: po utworzeniu planu obsługi otwórz właściwości planu, przejdź do karty **Harmonogram szacowania**, wybierz pozycję **Uruchom tę regułę według harmonogramu**, kliknij pozycję **Dostosuj** i utwórz harmonogram niestandardowy. Można na przykład określić uruchamianie planu obsługi co 60 dni.  



## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Importowanie ustawień klienta usługi Office 365 z pliku konfiguracji nie powiedzie się, gdy zawiera nieobsługiwanych językach
<!-- 489258  Fixed in 1706  -->
*Następujący problem dotyczy wersji 1702 i wcześniejszych.*   

Podczas importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML, a plik zawiera języki, które nie są obsługiwane przez klienta usługi Office 365 ProPlus, występuje błąd. Aby uzyskać więcej informacji, zobacz: [Wdrażanie aplikacji usługi Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Obejście**: Użyj tylko [języki obsługiwane przez klienta usługi Office 365 ProPlus](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) w pliku konfiguracji XML.  



## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="beginning-with-version-1710-you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10------503274--should-be-fixed-by-1802-if-not-sooner---"></a>Począwszy od wersji 1710, możesz nie można wdrażać profile sieci VPN programu Windows Phone 8.1 do systemu Windows 10   <!-- 503274  Should be fixed by 1802, if not sooner -->
W 1710 go nie jest już możliwe utworzyć profil sieci VPN za pomocą przepływu pracy systemu Windows Phone 8.1, który jest również dotyczy urządzeń z systemem Windows 10. Dla tych profilów strony obsługiwane platformy już jest wyświetlana w kreatorze tworzenia. Windows Phone 8.1 jest automatycznie wybierany na zaplecza. Obsługiwane platformy jest dostępna w oknie właściwości profilu, ale nie są wyświetlane opcje systemu Windows 10.

**Obejście**: Użyj przepływu pracy profilu sieci VPN systemu Windows 10 dla urządzeń z systemem Windows 10. Jeśli ta opcja nie jest możliwe w danym środowisku, należy się z pomocą techniczną. Obsługa ułatwia dodawanie przeznaczonych dla systemu Windows 10.


### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-of-memory"></a>Pełne czyszczenie powoduje wyłączenie urządzeń systemu Windows 10 z mniej niż 4 GB pamięci
Wykonywanie pełnego czyszczenia danych na urządzeniach z systemem Windows 10, wersji 1507, z mniej niż 4 GB pamięci RAM można pozostawić urządzenia korzystanie z niej. Po próbie wyczyść urządzenie, nie można uruchomić i nie odpowiada.

**Obejście**: Upewnij się, że urządzenia z systemem Windows 10 mieć co najmniej 4 GB pamięci, aby wykonać pełne czyszczenie danych. Aby wyświetlić numer wersji systemu Windows 10 urządzenia, w wierszu polecenia wprowadź „winver”. Jeśli zostać już wyczyszczone urządzenia, a nie jest już reakcji, należy użyć dysku rozruchowego systemu Windows 10 USB do odzyskania urządzenia.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-to-which-you-deploy-a-terms-and-conditions-policy-the-user-sees-multiple-sets-of-the-same-terms"></a>Jeśli użytkownik należy do dwóch lub więcej kolekcji użytkowników, na których można wdrożyć zasady warunków i postanowień, użytkownik zobaczy wiele zestawów tych samych warunków  
<!-- 454394    -->
Jeśli wdrożenia zestawu warunków w wielu kolekcjach użytkowników, a użytkownik jest członkiem więcej niż jednej z nich, użytkownik zobaczy wiele kopii identycznych warunków w portalu firmy. Na przykład:
- Użytkownik o nazwie "To dla użytkownika Użytkownikprzykładowy" jest elementem członkowskim dwóch różnych kolekcji użytkowników, "Pracownicyfirmyfte" i "Kolekcji Pracownicyfirmyna"
- Wdróż "W nazwie Warunkifirmy" warunki i postanowienia do kolekcji Pracownicyfirmyfte i w kolekcji Pracownicyfirmyna
- To dla użytkownika Użytkownikprzykładowy widział dwa identyczne zestawy warunków o nazwie Warunkifirmy na stronie akceptacji warunków w portalu firmy. 

Użytkownicy mogą tylko zaakceptować wszystkie lub odrzucić wszystkie warunki. W związku z tym istnieje niebezpieczeństwo stanu niejednoznacznej akceptacji. (Taki stan niejednoznaczne jest której użytkownik akceptuje i odrzuca tych samych warunków). Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków dla poszczególnych użytkowników, więc nie ma żadnych błędów w raporcie. Jedynym wynikiem jest to, że użytkownik będzie widział dwa zestawy warunków na stronie akceptacji.  

**Obejście**: Upewnij się, że każdy użytkownik znajduje się tylko do jednej kolekcji, do której są wdrożone warunki.  


<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
