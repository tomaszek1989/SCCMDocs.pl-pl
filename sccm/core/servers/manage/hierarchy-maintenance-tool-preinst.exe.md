---
title: "Narzędzie Obsługa hierarchii"
titleSuffix: Configuration Manager
description: "Zrozumieć, co oznacza narzędzia Obsługa hierarchii, i do czego można go użyć. Zawiera dokumentacja opcji wiersza polecenia."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cead6825-6113-4ba5-a381-ac3598dfee86
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 02bd5bfe0fc4ccc976d95b944bd51e9f0a276db0
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="hierarchy-maintenance-tool-preinstexe-for-system-center-configuration-manager"></a>Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Narzędzie Obsługa hierarchii (Preinst.exe) przekazuje polecenia do programu System Center Configuration hierarchii Manager jest uruchomiona usługa Menedżer hierarchii. Narzędzie Obsługa hierarchii jest automatycznie zainstalowany podczas instalacji lokacji programu Configuration Manager. Można znaleźć Preinst.exe w \\ &lt; *Nazwa_serwera_lokacji*> \SMS_&lt;*Kod_lokacji*\bin\X64\00000409 folderu udostępnionego na serwerze lokacji.  

 Narzędzia Obsługa hierarchii można użyć w następujących scenariuszach:  

-   Gdy wymagana jest wymiana klucza zabezpieczeń, istnieją sytuacje, w których należy dokonać ręcznej początkowej wymiany klucza publicznego między lokacjami. Więcej informacji znajduje się w sekcji [Ręczna wymiana kluczy publicznych między lokacjami](#BKMK_ManuallyExchangeKeys) w tym temacie.  

-   Aby usunąć aktywne zadania przeznaczone dla lokacji docelowej, która nie jest już dostępna.  

-   Aby usunąć serwer lokacji z konsoli programu Configuration Manager, gdy nie można odinstalować lokacji za pomocą Instalatora. Na przykład jeśli fizycznie usunięto lokację programu Configuration Manager bez wcześniejszego uruchomienia Instalatora w celu odinstalowania lokacji, informacje o lokacji będą nadal istnieć w bazie danych lokacji nadrzędnej, a lokacja nadrzędna będzie podejmować próby nawiązania komunikacji z lokacją podrzędną. Aby rozwiązać ten problem, należy uruchomić narzędzie Obsługa hierarchii i ręcznie usunąć lokację podrzędną z bazy danych lokacji nadrzędnej.  

-   Aby zatrzymać wszystkie usługi programu Configuration Manager w lokacji bez konieczności zatrzymywania ich pojedynczo.  

-   W przypadku przywracania lokacji można użyć opcji CHILDKEYS, aby dystrybuować klucze publiczne z wielu lokacji podrzędnych do przywracanej lokacji.  

Aby uruchomić narzędzie Obsługa hierarchii, bieżący użytkownik musi mieć uprawnienia administratora na komputerze lokalnym. Ponadto użytkownik musi mieć jawne uprawnienia zabezpieczeń Lokacja — Administracja; nie wystarczy, aby użytkownik odziedziczył te uprawnienia, będąc członkiem grupy, która ma te uprawnienia.  

## <a name="hierarchy-maintenance-tool-command-line-options"></a>Opcje wiersza polecenia narzędzia Obsługa hierarchii  
Aby korzystać z narzędzia Obsługa hierarchii, należy uruchomić je lokalnie na serwerze centralnej lokacji administracyjnej, lokacji głównej lub lokacji dodatkowej.  

W celu uruchomienia narzędzia Obsługa hierarchii, należy użyć następującej składni: preinst.exe /&lt;opcji\>. Poniżej zamieszczono opcje wiersza polecenia.  

 **/ DELJOB &lt;* Kod_lokacji*> ** — Użycie tej opcji w lokacji do usunięcia wszystkich zadań lub poleceń z bieżącej lokacji do określonej lokacji docelowej.  

 **/ DELSITE &lt;* Kod_lokacji_podrzędnej_do_usunięcia*> ** — Użycie tej opcji w lokacji nadrzędnej umożliwia usunięcie danych lokacji podrzędnych z bazy danych lokacji w lokacji nadrzędnej. Tej opcji należy zwykle użyć, jeżeli komputer serwera lokacji jest likwidowany, przed odinstalowaniem z niego lokacji.  

> [!NOTE]  
>  Opcja /DELSITE nie powoduje odinstalowania lokacji na komputerze określonym przez parametr kod_lokacji_podrzędnej_do_usunięcia. Ta opcja umożliwia tylko usunięcie informacji o lokacji z bazy danych lokacji programu Configuration Manager.  

**/ DUMP &lt;* Kod_lokacji*> ** — Użycie tej opcji na lokalnym serwerze lokacji umożliwia zapisanie obrazów sterowania lokacji w folderze głównym dysku, na którym zainstalowano lokację. Można zapisać określony obraz sterowania lokacji w folderze lub zapisać wszystkie pliki sterowania lokacji w hierarchii.  

-   / DUMP &lt; *Kod_lokacji*> zapisanie obrazu sterowania tylko dla określonej lokacji.  

-   Parametr /DUMP umożliwia zapisanie plików sterowania dla wszystkich lokacji.  

Obraz to binarna reprezentacja pliku sterowania lokacji, który jest przechowywany w bazie danych lokacji programu Configuration Manager. Zrzut obrazu pliku sterowania lokacji to suma obrazu podstawowego i oczekujących obrazów różnicowych.  

Po wykonaniu zrzutu obrazu pliku sterowania lokacji za pomocą narzędzia Obsługa hierarchii, nazwa pliku jest format sitectrl_&lt;*Kod_lokacji*> .ct0.  

**/ STOPSITE** — użycie tej opcji na lokalnym serwerze lokacji umożliwia zainicjowanie cyklu zamykania usługi Menedżer składników lokacji programu Configuration Manager, co powoduje częściowe zresetowanie lokacji. Po uruchomieniu tego cyklu zamykania niektóre usługi programu Configuration Manager na serwerze lokacji i jego zdalnych systemach lokacji są zatrzymywane. Te usługi są oflagowywane do ponownej instalacji. W wyniku tego cyklu zamykania niektóre hasła są automatycznie zmieniane po ponownym zainstalowaniu usług.  

> [!NOTE]  
>  Aby zobaczyć rekord zamykania, ponownej instalacji i zmian haseł dla programu Menedżer składników lokacji, przed użyciem tej opcji wiersza polecenia należy włączyć rejestrowanie dla tego składnika.  

Po rozpoczęciu cykl zamykania jest wykonywany automatycznie z pominięciem wszystkich składników lub komputerów, które nie odpowiadają. Jeżeli jednak usługa Menedżer składników lokacji nie może uzyskać dostępu do zdalnego systemu lokacji podczas cyklu zamykania, składniki zainstalowane w zdalnym systemie lokacji są instalowane jeszcze raz po ponownym uruchomieniu usługi Menedżer składników lokacji. Gdy usługa Menedżer składników lokacji zostanie uruchomiona ponownie, podejmuje wielokrotne próby ponownego zainstalowania wszystkich usług oflagowanych do ponownej instalacji, aż proces ten zakończy się powodzeniem.  

Usługę Menedżer składników lokacji można uruchomić ponownie, używając programu Service Manager. Po jej ponownym uruchomieniu następuje odinstalowanie, ponowna instalacja i uruchomienie wszystkich odpowiednich usług. Po użyciu opcji /STOPSITE do zainicjowania cyklu zamykania nie można pominąć cykli ponownej instalacji po uruchomieniu usługi Menedżer składników lokacji.  

**/KEYFORPARENT** — tej opcji należy użyć w lokacji w celu dystrybucji klucza publicznego lokacji do lokacji nadrzędnej.  

Opcja/keyforparent umożliwia umieszczenie umieszczenie klucza publicznego lokacji w pliku &lt; *Kod_lokacji*>. Dysku zawierającego pliki CT4 w katalogu głównym programu. Po uruchomieniu programu preinst.exe z tą opcją należy ręcznie skopiować &lt; *Kod_lokacji*>. CT4 plik do folderu...\Inboxes\hman.box lokacji nadrzędnej (nie hman.box\pubkey).  

**/KEYFORCHILD** — tej opcji należy użyć w lokacji w celu dystrybucji klucza publicznego lokacji do lokacji podrzędnej.  

Opcja/keyforchild umożliwia umieszczenie umieszczenie klucza publicznego lokacji w pliku &lt; *Kod_lokacji*>. Dysku zawierającego pliki CT5 w katalogu głównym programu. Po uruchomieniu programu preinst.exe z tą opcją należy ręcznie skopiować &lt; *Kod_lokacji*>. CT5 plik do folderu...\Inboxes\hman.box lokacji podrzędnej (nie hman.box\pubkey).  

**/CHILDKEYS** — tej opcji można użyć w lokacjach podrzędnych przywracanej lokacji. Ta opcja umożliwia dystrybucję kluczy publicznych z kilku lokacji podrzędnych do przywracanej lokacji.  

Opcja/childkeys umożliwia umieszczenie klucza z lokacji, w której uruchomiono opcję, i wszystkich podrzędnych tej lokacji do pliku kluczy publicznych &lt; *Kod_lokacji*>. CT6.  

Po uruchomieniu programu preinst.exe z tą opcją należy ręcznie skopiować &lt; *Kod_lokacji*>. CT6 plik do folderu...\Inboxes\hman.box przywracanej lokacji (nie hman.box\pubkey).  

**/PARENTKEYS** — tej opcji można użyć w lokacji nadrzędnej względem przywracanej lokacji. Ta opcja umożliwia dystrybucję kluczy publicznych ze wszystkich lokacji nadrzędnych do przywracanej lokacji.  

Opcja/parentkeys umożliwia umieszczenie klucza z lokacji, w której uruchomiono opcję, i kluczy z każdej nadrzędnej lokacji nad tą lokacją w pliku &lt;Kod_lokacji\>. CT7.  

Po uruchomieniu programu preinst.exe z tą opcją należy ręcznie skopiować &lt; *Kod_lokacji*>. CT7 plik do folderu...\Inboxes\hman.box przywracanej lokacji (nie hman.box\pubkey).  

##  <a name="BKMK_ManuallyExchangeKeys"></a>Ręczna wymiana kluczy publicznych między lokacjami  
Domyślnie **Wymagaj wymiany klucza zabezpieczeń** opcja jest włączona dla lokacji programu Configuration Manager. Gdy wymagana jest wymiana klucza zabezpieczeń, istnieją dwie sytuacje, w których należy dokonać ręcznej początkowej wymiany klucza między lokacjami:  

-   Jeżeli schemat usługi Active Directory nie został rozszerzony dla programu Configuration Manager  

-   Lokacje programu Configuration Manager nie publikują danych lokacji w usłudze Active Directory  

Można użyć narzędzia Obsługa hierarchii w celu wyeksportowania kluczy publicznych. Po ich wyeksportowaniu należy ręcznie wymienić klucze między lokacjami.  

> [!NOTE]  
>  Po ręcznej wymianie kluczy publicznych można przejrzeć plik dziennika **hman.log**, w którym rejestrowane są zmiany w konfiguracji lokacji i publikowanie informacji o lokacji w usługach domenowych Active Directory na serwerze lokacji nadrzędnej w celu zapewnienia przetworzenia przez lokację główną nowego klucza publicznego.  

#### <a name="to-manually-transfer-the-child-site-public-key-to-the-parent-site"></a>Aby ręcznie przenieść klucz publiczny lokacji podrzędnej do lokacji nadrzędnej  

1.  Po zalogowaniu w lokacji podrzędnej otwórz wiersz polecenia i przejdź do lokalizacji pliku **Preinst.exe**.  

2.  Wpisz następujące polecenie, aby wyeksportować klucz publiczny lokacji podrzędnej: **Preinst/keyforparent**  

3.  Opcja/keyforparent umożliwia umieszczenie umieszczenie klucza publicznego lokacji podrzędnej w  **&lt;kod lokacji\>. CT4** znajdującym się w folderze głównym dysku systemowego.  

4.  Przenieś  **&lt;kod lokacji\>. CT4** pliku do lokacji nadrzędnej  **&lt;katalog instalacji\>\inboxes\hman.box** folderu.  

#### <a name="to-manually-transfer-the-parent-site-public-key-to-the-child-site"></a>Aby ręcznie przenieść klucz publiczny lokacji nadrzędnej do lokacji podrzędnej  

1.  Po zalogowaniu w lokacji nadrzędnej otwórz wiersz polecenia i przejdź do lokalizacji pliku **Preinst.exe**.  

2.  Wpisz następujące polecenie, aby wyeksportować klucz publiczny lokacji nadrzędnej: **Preinst/keyforchild**.  

3.  Opcja/keyforchild umożliwia umieszczenie umieszczenie klucza publicznego lokacji nadrzędnej w  **&lt;kod lokacji\>. CT5** znajdującym się w folderze głównym dysku systemowego.  

4.  Przenieś  **&lt;kod lokacji\>. CT5** pliku  **&lt;katalog instalacji\>\inboxes\hman.box** katalogu w lokacji podrzędnej.  
