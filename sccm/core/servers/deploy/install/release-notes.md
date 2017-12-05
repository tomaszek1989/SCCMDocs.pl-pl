---
title: 'Informacje o wersji '
titleSuffix: Configuration Manager
description: "Te informacje można uzyskać pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie lub omówione w artykule bazy wiedzy Microsoft Knowledge Base."
ms.custom: na
ms.date: 11/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: "41"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 8030ce7f98ebb34d9581ad036513b9b1c879c0ad
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Informacje o wersji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programem System Center Configuration Manager informacje o wersji produktu są ograniczone do pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie (udostępnione za pośrednictwem aktualizacji w konsoli), lub szczegółowo opisane w artykule bazy wiedzy Microsoft Knowledge Base.  

Informacje o znanych problemach, które mają wpływ na podstawowe scenariusze jest przekazywany w dokumentacji online produktu w bibliotece dokumentacji programu System Center Configuration Manager.  

> [!TIP]  
>  Ten temat zawiera informacje o wersji dla bieżącej gałęzi programu System Center Configuration Manager. Technical Preview programu System Center Configuration Manager, zobacz [Technical Preview programu System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Aby uzyskać informacje o nowych funkcjach wprowadzona z różnymi wersjami zobacz następujące tematy:
- [Co nowego w wersji 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [Co nowego w wersji 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)
- [Co nowego w wersji 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)



## <a name="setup-and-upgrade"></a>Instalowanie i uaktualnianie  


### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Podczas instalowania lokacji oddziału usługi długoterminowe przy użyciu wersji 1606, Current Branch lokacji jest zainstalowany
<!-- Consider move to core content  -->
Użycie nośnika linii bazowej 1606 wersji z października 2016 wersji aby zainstalować lokację długoterminowe Servicing Branch (LTSB), instalacja lokacji bieżącej gałęzi zamiast tego. Dzieje się tak, ponieważ nie wybrano opcję zainstalowania punktu połączenia usługi w ramach instalacji lokacji.

 - Punkt połączenia usługi nie jest wymagany, musi ona zostać wybrana do zainstalowania podczas instalacji, aby zainstalować lokację LTSB.

Po zakończeniu instalacji można odinstalować punkt połączenia usługi.  Jednak musi mieć połączenie usługi punktu w trybie offline lub online do przesyłania danych telemetrycznych i Pobierz aktualizacje zabezpieczeń dla bieżącej gałęzi i LTSB witryny.

Jeśli witryny zainstalowany w lokacji bieżącej gałęzi, ale trzeba zainstalować LTSB, należy odinstalować lokację i zainstaluj go ponownie. Alternatywnie możesz wywołać [Microsoft Help i pomocy technicznej](http://go.microsoft.com/fwlink/?LinkId=243064) Aby uzyskać pomoc.  

Aby upewnić się, która gałąź zainstalowane, w konsoli pod adresem **administracji** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Opcja skonwertuje wówczas lokację do lokacji bieżącej gałęzi jest dostępna tylko w przypadku, gdy w lokacji działa LTSB.  

**Obejście problemu:**  Brak.   


### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Aktualizacja jest wstrzymywana podczas pobierania w węźle Aktualizacje i obsługa konsoli programu Configuration Manager  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
Podczas automatycznego pobierania aktualizacji przez punkt połączenia usługi online, aktualizacja może zostać wstrzymana ze stanem Pobieranie. W przypadku wstrzymania aktualizacji podczas pobierania we wskazanych plikach dziennika wyświetlane są pozycje podobne do poniższych:  

Dziennik DMPdownloader:  

-   BŁĄD: Nie można pobrać pakietu redystrybucyjnego dla 037cd17e-4d7b-40e1-802b-14bb682364c7 za pomocą polecenia /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 lnmanifesturl http://go.microsoft.com/fwlink/?LinkID=724434 redistversion 112015 / noui "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Błąd: Nie można zweryfikować podpisu authenticode 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi'.  

-   Błąd: Sprawdzenie podpisu pliku nie powiodło się dla 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**Obejście**: Na serwerze lokacji zmodyfikuj następujący klucz rejestru zgodnie z poniższym wzorem, a następnie uruchom ponownie usługę SMS_Executive lub poczekaj maksymalnie 24 godziny na następny cykl pobierania automatycznego.  

-   **Klucz do edycji**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software publikowania  

-   **Wartość stanu**:  Ustaw **146944** dziesiętną lub **0x00023e00** szesnastkowe  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>Instalacja nie powiedzie się, używając plików redystrybucyjnych z dysku CD. Najnowsze folderu z powodu błędu weryfikacji manifestu
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

W przypadku uruchamiania Instalatora z dysku CD. Najnowszy folder utworzona dla wersji 1606 i używać plików redystrybucyjnych dołączone do tego dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu następujących błędów w dzienniku instalacji programu Configuration Manager:

  - BŁĄD: Sprawdzenie skrótu pliku defaultcategories.dll nie powiodło się
  - BŁĄD: Nie można zweryfikować manifestu. Nieprawidłowa wersja manifestu?

**Obejście problemu:**  Użyj jednej z następujących czynności:
 - Podczas instalacji wybierz do pobrania najnowszych plików redystrybucyjnych przez firmę Microsoft do użycia zamiast uwzględnionych w dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Instalacja klienta kończy się niepowodzeniem z kodem błędu 0x8007064c
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*Poniższe informacje dotyczą wszystkich wersji aktywnych programu Configuration Manager.*   
W wersjach wszystkie aktywne podczas wdrażania klienta na komputerach z systemem Windows Instalacja nie powiedzie się. Plik ccmsetup.log zawiera wpis "pliku"C:\WINDOWS\ccmsetup\Silverlight.exe"zwrócił kod zakończenia błędu 1612. Niepowodzenie instalacji"następuje"InstallFromManifest nie powiodło się 0x8007064c".

**Obejście** przyczyną jest uszkodzony, wcześniej zainstalowanej wersji programu Silverlight. Można spróbować uruchomić następujące narzędzia na danym komputerze, aby rozwiązać ten problem: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Plany obsługi tworzą domyślnie wiele powielonych grup aktualizacji oprogramowania i wdrożeń  
Domyślnie kreator tworzenia planów obsługi jest uruchamiany obecnie po każdej synchronizacji aktualizacji oprogramowania. Przy każdym uruchomieniu tworzy on nową grupę aktualizacji oprogramowania i wdrożenia. W przypadku harmonogramu synchronizacji aktualizacji oprogramowania uruchamianego kilka razy dzienne kreator tworzenia planów obsługi każdego dnia będzie tworzył wiele prawdopodobnie identycznych grup aktualizacji oprogramowania i wdrożeń.  

**Obejście**:    
po utworzeniu planu obsługi otwórz właściwości planu, przejdź do karty **Harmonogram szacowania**, wybierz pozycję **Uruchom tę regułę według harmonogramu**, kliknij pozycję **Dostosuj** i utwórz harmonogram niestandardowy. Można na przykład określić uruchamianie planu obsługi co 60 dni.  



## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Importowanie ustawień klienta usługi Office 365 z pliku konfiguracji nie powiedzie się, gdy zawiera nieobsługiwanych językach
<!-- 489258  Fixed in 1706  -->
*Poniższe informacje dotyczą wersji 1702 i wcześniejszych.*   
Podczas importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML, a plik zawiera języki, które nie są obsługiwane przez klienta usługi Office 365 ProPlus, wystąpi błąd. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji usługi Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Obejście**:    
Użyj tylko [języki obsługiwane przez klienta usługi Office 365 ProPlus](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) w pliku konfiguracji XML.  



## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="beginning-with-version-1710-you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10------503274--should-be-fixed-by-1802-if-not-sooner---"></a>Począwszy od wersji 1710, możesz nie można wdrażać profile sieci VPN programu Windows Phone 8.1 do systemu Windows 10<!-- 503274  Should be fixed by 1802, if not sooner -->
W 1710 go nie jest już możliwe utworzyć profil sieci VPN za pomocą przepływu pracy systemu Windows Phone 8.1, który jest również dotyczy urządzeń z systemem Windows 10. Dla tych profilów w kreatorze tworzenia nie jest wyświetlana strona obsługiwane platformy i Windows Phone 8.1 jest automatycznie wybierany w wewnętrznej; na stronach właściwości strona obsługiwane platformy jest dostępna, ale nie są wyświetlane opcje systemu Windows 10.

**Obejście**: Użyj przepływu pracy profilu sieci VPN systemu Windows 10 dla urządzeń z systemem Windows 10. Jeśli nie jest to możliwe w danym środowisku, należy się z pomocą techniczną. Można pomóc dział pomocy technicznej można dodać wartości docelowej systemu Windows 10, w razie potrzeby.


### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Całkowite wyczyszczenie powoduje wyłączenie urządzeń z systemem Windows 10 z pamięcią RAM mniejszą niż 4 GB
Przeprowadzenie całkowitego czyszczenia danych w urządzeniu z systemem Windows 10 RTM (wersje starsze niż 1511) z pamięcią RAM mniejszą niż 4 GB sprawi, że urządzenie nie będzie nadawać się do użytku. Po podjęciu próby wyczyszczenia danych urządzenie nie reaguje i nie można go uruchomić.

**Obejście**: Upewnij się, że RTM komputerów z systemem Windows 10 mają co najmniej 4 GB pamięci RAM dostępnej przed wykonaniem pełne czyszczenie danych na urządzeniu. Aby wyświetlić numer wersji systemu Windows 10 urządzenia, w wierszu polecenia wprowadź „winver”. Jeśli urządzenie już zostało wyczyszczone i nie odpowiada, możesz użyć rozruchowego dysku USB z systemem Windows 10 USB do uruchomienia urządzenia i przywrócenia dostępu do niego.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Jeśli użytkownik należy do co najmniej dwóch kolekcji użytkowników, w których są wdrożone zasady warunków i postanowień, użytkownikowi będzie wyświetlanych wiele zestawów tych samych warunków  
<!-- 454394    -->
Gdy administrator wdraża zestaw warunków w wielu kolekcjach użytkowników, a użytkownik należy do więcej niż jednej z nich, dla tego użytkownika zostanie wyświetlonych wiele kopii identycznych warunków podczas otwierania Portalu firmy.  Na przykład, jeśli użytkownik o nazwie "To dla użytkownika Użytkownikprzykładowy" jest elementem członkowskim dwóch różnych kolekcji użytkowników, jeden o nazwie "Pracownicyfirmyfte" i "Kolekcji Pracownicyfirmyna," "i warunki i postanowienia o nazwie"W nazwie Warunkifirmy"jest wdrożony w kolekcji Pracownicyfirmyfte i w kolekcji Pracownicyfirmyna, to dla użytkownika Użytkownikprzykładowy zostaną wyświetlone dwa identyczne zestawy w o nazwie Warunkifirmy na stronie akceptacji warunków. Ponieważ użytkownicy mogą tylko zaakceptować lub odrzucić wszystkie warunki, nie ma ryzyka wystąpienia niejednoznacznej akceptacji, oznaczającej zarówno zaakceptowanie, jak i odrzucenie warunków przez użytkownika. Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków i każdego użytkownika, więc nie ma błędów w tym raporcie. Jedynym wynikiem jest to, że użytkownik będzie widział dwa zestawy warunków na stronie akceptacji.  

**Obejście**: Upewnij się, że każdy użytkownik znajduje się tylko do jednej kolekcji, do której są wdrożone warunki.  


### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android pracy profilów poczty e-mail, które korzystają z certyfikatu uwierzytelniania nie są stosowane do urządzeń
<!--  487657      -->
Po utworzeniu systemu Android dla profilu poczty e-mail z pracy, dostępne są dwie opcje dla uwierzytelniania. Jeden z nich jest nazwa użytkownika i hasło, a drugi to certyfikaty. W tej chwili nie działa opcja certyfikatów. Jeśli profil jest tworzony przy użyciu metody uwierzytelniania ustawioną **certyfikaty**monitowany o ręczne wprowadzenie szczegóły konta poczty e-mail i profil nie ma zastosowania do urządzenia.

**OBEJŚCIE**: Brak. Administratorzy muszą użyj **nazwy użytkownika i hasła** opcji lub poczekaj, aż ten problem został rozwiązany.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
