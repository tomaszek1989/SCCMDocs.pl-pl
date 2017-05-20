---
title: "Schemat usługi Active Directory i publikowanie | Dokumentacja firmy Microsoft"
description: "Rozszerz schemat usługi Active Directory programu System Center Configuration Manager w celu uproszczenia procesu wdrażania i konfigurowania klientów."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 88649111ea3a38c027efb4952211546afd0bf27e
ms.openlocfilehash: 58beef440db8e019a06ce7c4c8eaabc8e85ce954
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-active-directory-for-site-publishing"></a>Przygotowanie usługi Active Directory do publikowania witryny

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W przypadku rozszerzania schematu usługi Active Directory dla programu System Center Configuration Manager wprowadzania nowych struktur do usługi Active Directory są używane przez lokacji programu Configuration Manager, aby opublikować informacje o kluczu w bezpiecznej lokalizacji, w której klienci łatwo do niego dostęp.  

Jest warto używać programu Configuration Manager za pomocą rozszerzonych schemat usługi Active Directory podczas zarządzania klientami lokalnie. Rozszerzone schematu można uprościć proces wdrażania i konfigurowanie klientów. Rozszerzone schematu umożliwia również klientom szybkie lokalizowanie zasobów, takich jak serwery zawartości i dodatkowych usług, które zapewniają różne role systemu lokacji programu Configuration Manager.  

-   Jeśli nie jesteś zaznajomiony z jakiego rozszerzonym schemacie zapewnia wdrażania programu Configuration Manager, można uzyskać więcej informacji o [rozszerzenia schematu dla programu System Center Configuration Manager](../../../core/plan-design/network/schema-extensions.md) ułatwiające dokonanie takiego wyboru.  

-   Gdy nie jest używany schemat jest rozszerzony, można skonfigurować innych metod, takich jak serwery DNS i WINS w celu lokalizowania usług i serwerów systemu lokacji. Te metody lokalizacji usług wymagają dodatkowej konfiguracji i nie są preferowaną metodą lokalizacji usług przez klientów. Aby dowiedzieć się więcej, przeczytaj [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md),  

-   Jeżeli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager 2007 lub System Center 2012 Configuration Manager, nie potrzebujesz zrobić więcej. Rozszerzenia schematu nie uległy zmianie i będzie się już w miejscu.  

Rozszerzanie schematu jest akcja jednorazowa dla dowolnego lasu. Aby rozszerzyć, a następnie użyć rozszerzony schemat usługi Active Directory, wykonaj następujące kroki:  

## <a name="step-1-extend-the-schema"></a>Krok 1. Rozszerzenie schematu  
Aby rozszerzyć schemat programu Configuration Manager:  

-   Użyj konta, które jest członkiem grupy zabezpieczeń Administratorzy schematu.  

-   Zalogować się w głównym kontrolerze domeny schematu.  

-   Uruchom **Extadsch.exe** narzędzia lub użyj narzędzia wiersza polecenia LDIFDE z **ConfigMgr_ad_schema.ldf** pliku. Narzędzie jest zarówno i plików w **SMSSETUP\BIN\X64** folderze na nośniku instalacyjnym programu Configuration Manager.  

#### <a name="option-a-use-extadschexe"></a>Opcja o: Użyj Extadsch.exe  

1.  Uruchom program **extadsch.exe**, aby dodać nowe klasy i atrybuty do schematu usługi Active Directory.  

    > [!TIP]  
    >  Uruchom to narzędzie z wiersza polecenia, aby wyświetlać informacje podczas jego pracy.  

2.  Sprawdź, czy rozszerzenie schematu powiodło się, przeglądając zawartość extadsch.log w folderze głównym dysku systemowego.  

#### <a name="option-b-use-the-ldif-file"></a>Opcja B: Użyj plików LDIF  

1.  Edytuj **ConfigMgr_ad_schema.ldf** plik, aby określić domenę główną usługi Active Directory, który ma zostać rozszerzony:  

    -   Zamień wszystkie wystąpienia tekstu, **DC = x**, w pliku z pełną nazwę domeny do rozszerzenia.  

    -   Na przykład, jeśli pełną nazwę domeny do rozszerzenia to widgets.microsoft.com, Zmień wszystkie wystąpienia DC = x w pliku **DC = widgets, DC = microsoft, DC = com**.  

2.  Użyj narzędzia wiersza polecenia LDIFDE w celu zaimportowania zawartości pliku **ConfigMgr_ad_schema.ldf** pliku w usługach domenowych w usłudze Active Directory:  

    -   Na przykład następujący wiersz polecenia importuje rozszerzeń schematu do usług domenowych w usłudze Active Directory, włączenie pełnego rejestrowania i tworzy plik dziennika podczas procesu importowania: **ldifde -i -f ConfigMgr_ad_schema.ldf - v -j &lt;lokalizację do zapisania pliku dziennika\>**.  

3.  Aby sprawdzić, czy rozszerzenie schematu powiodło się, sprawdź plik dziennika utworzony za pomocą wiersza polecenia używane w poprzednim kroku.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>Krok 2.  Tworzenie kontenera zarządzania systemem i udzielenie lokacjom uprawnień do kontenera  
 Po rozszerzeniu schematu, należy utworzyć kontener o nazwie **System zarządzania** w usługach domenowych w usłudze Active Directory (AD DS):  

-   Ten kontener można utworzyć jeden raz w każdej domenie, która ma lokacji głównej lub dodatkowej, która będzie publikować dane w usłudze Active Directory.  

-   Dla każdego kontenera można przyznać uprawnienia do konto komputera każdego serwera lokacji głównej i dodatkowej, która będzie publikować dane do tej domeny. Każde konto musi **Pełna kontrola** do kontenera zgodą zaawansowane **Zastosuj**, równa **ten obiekt i wszystkie obiekty zależne**.  

#### <a name="to-add-the-container"></a>Aby dodać kontener  

1.  Użyj konta, które ma uprawnienie **Tworzenie wszystkich obiektów podrzędnych** w kontenerze **System** w usługach domenowych Active Directory.  

2.  Uruchom **ADSI Edit** (adsiedit.msc) i połącz się z domeną serwera lokacji.  

3.  Utwórz kontener:  

    -   Rozwiń węzeł **domeny** &lt;w pełni kwalifikowana nazwa domeny komputera\>, rozwiń węzeł &lt;nazwa wyróżniająca\>, kliknij prawym przyciskiem myszy **CN = System**, wybierz **nowy**, a następnie wybierz **obiektu**.  

    -   W **Utwórz obiekt** okno dialogowe Wybierz **kontenera**, a następnie wybierz **dalej**.  

    -   W **wartość** wprowadź **System zarządzania**, a następnie wybierz **dalej**.  

4.  Przypisz uprawnienia:  

    > [!NOTE]  
    >  Jeśli wolisz, możesz użyć innych narzędzi, na przykład narzędzia administracyjnego Użytkownicy i komputery usługi Active Directory (dsa.msc), aby dodać uprawnienia do kontenera.  

    -   Kliknij prawym przyciskiem myszy **CN = Zarządzanie systemem**, a następnie wybierz **właściwości**.  

    -   Wybierz **zabezpieczeń** , wybierz **Dodaj**, a następnie dodaj konto komputera serwera lokacji z **Pełna kontrola** uprawnienia.  

    -   Wybierz **zaawansowane**, wybierz konto komputera serwera lokacji, a następnie wybierz **edytować**.  

    -   W **Zastosuj** wybierz **ten obiekt i wszystkie obiekty zależne**.  

5.  Wybierz **OK** Zamknij konsolę i zapisać konfigurację.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>Krok 3. Konfigurowanie lokacji do publikowania w usługach domenowych w usłudze Active Directory  
 Po ustawiono kontenera, czy przyznano uprawnienia i zainstalowanej lokacji głównej programu Configuration Manager, można skonfigurować tej lokacji do publikowania danych w usłudze Active Directory.  

 Aby uzyskać więcej informacji dotyczących publikowania, zobacz [publikowania danych lokacji programu System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md).  

