---
title: "Publikowanie i schematu usługi Active Directory | Dokumentacja firmy Microsoft"
description: "Rozszerzenie schematu usługi Active Directory programu System Center Configuration Manager w celu uproszczenia procesu wdrażania i konfigurowania klientów."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: "17"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 58beef440db8e019a06ce7c4c8eaabc8e85ce954
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-active-directory-for-site-publishing"></a>Przygotowanie usługi Active Directory do publikowania lokacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po rozszerzeniu schematu usługi Active Directory dla programu System Center Configuration Manager do usługi Active Directory, które są używane przez lokacje programu Configuration Manager do publikowania kluczowych informacji w bezpiecznej lokalizacji, gdzie klienci mogą łatwo uzyskiwać dostęp go zostaną wprowadzone nowe struktury.  

Zaleca się za pomocą programu Configuration Manager rozszerzony schemat usługi Active Directory w przypadku zarządzania klientami lokalnymi. Rozszerzony schemat może uprościć proces wdrażania i konfigurowania klientów. Rozszerzony schemat także umożliwia klientom wydajne lokalizowanie zasobów, takich jak serwery zawartości i dodatkowe usługi, które zapewniają różne role systemu lokacji programu Configuration Manager.  

-   Jeśli nie masz doświadczenia w obsłudze zapewnia rozszerzony schemat wdrożenia programu Configuration Manager, zawiera temat [rozszerzenia schematu dla programu System Center Configuration Manager](../../../core/plan-design/network/schema-extensions.md) ułatwiające podjęcie tej decyzji.  

-   Jeśli nie używasz schematu rozszerzonego, można skonfigurować inne metody, takie jak DNS i WINS do lokalizowania usług i serwerów systemu lokacji. Te metody lokalizacji usług wymagają dodatkowej konfiguracji i nie są preferowaną metodą lokalizacji usług przez klientów. Aby dowiedzieć się więcej, przeczytaj [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md),  

-   Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager 2007 lub System Center 2012 Configuration Manager, nie muszą wykonać jeszcze więcej. Rozszerzenia schematu nie uległy zmianie i będą już na miejscu.  

Rozszerzenie schematu to działanie jednorazowe dla każdego lasu. Aby rozszerzyć, a następnie użyj rozszerzonym schemacie usługi Active Directory, wykonaj następujące kroki:  

## <a name="step-1-extend-the-schema"></a>Krok 1. Rozszerzenie schematu  
Aby rozszerzyć schemat dla programu Configuration Manager:  

-   Użyj konta, które jest członkiem grupy zabezpieczeń Administratorzy schematu.  

-   Podpisany kontrolerze domeny głównego schematu.  

-   Uruchom **Extadsch.exe** narzędzie, lub użyj narzędzia wiersza polecenia LDIFDE z **ConfigMgr_ad_schema.ldf** pliku. Narzędzie i plik znajdują się w **SMSSETUP\BIN\X64** folderze na nośniku instalacyjnym programu Configuration Manager.  

#### <a name="option-a-use-extadschexe"></a>Opcja A: Użyj Extadsch.exe  

1.  Uruchom program **extadsch.exe**, aby dodać nowe klasy i atrybuty do schematu usługi Active Directory.  

    > [!TIP]  
    >  Uruchom to narzędzie z wiersza polecenia, aby wyświetlać informacje podczas jego pracy.  

2.  Sprawdź, czy rozszerzenie schematu powiodło się, przeglądając extadsch.log w folderze głównym dysku systemowego.  

#### <a name="option-b-use-the-ldif-file"></a>Opcja B: Użycie pliku LDIF  

1.  Edytuj **ConfigMgr_ad_schema.ldf** plik, aby określić domenę główną usługi Active Directory, który chcesz rozszerzyć:  

    -   Zastąp wszystkie wystąpienia tekstu, **DC = x**, w pliku z pełną nazwę domeny do rozszerzenia.  

    -   Przykładowo jeśli pełną nazwę domeny do rozszerzenia to widgets.microsoft.com, należy zmienić wszystkie wystąpienia tekstu DC = x w pliku **DC = widgets, DC = microsoft, DC = com**.  

2.  Użyj narzędzia wiersza polecenia LDIFDE w celu zaimportowania zawartości pliku **ConfigMgr_ad_schema.ldf** pliku w usługach domenowych w usłudze Active Directory:  

    -   Na przykład następujące polecenie w wierszu zaimportowanie rozszerzeń schematu do usług domenowych w usłudze Active Directory, włączenie pełnego rejestrowania i utworzenie pliku dziennika podczas procesu importowania: **ldifde -i -f ConfigMgr_ad_schema.ldf - v -j &lt;lokalizację do przechowywania plików dziennika\>**.  

3.  Aby sprawdzić, czy rozszerzenie schematu powiodło, przejrzyj plik dziennika utworzony przez wiersz polecenia użyty w poprzednim kroku.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>Krok 2.  Tworzenie kontenera zarządzania systemem i udzielenie lokacjom uprawnień do kontenera  
 Po rozszerzeniu schematu należy utworzyć kontener o nazwie **System zarządzania** w usługach domenowych w usłudze Active Directory (AD DS):  

-   Ten kontener należy utworzyć jeden raz w każdej domenie zawierającej podstawowej lub dodatkowej lokacji, która będzie publikować dane do usługi Active Directory.  

-   Dla każdego kontenera należy udzielić uprawnień do konta komputera każdego serwera lokacji głównej i dodatkowej, która będzie publikować dane do tej domeny. Każde konto wymaga **Pełna kontrola** do kontenera z uprawnieniem zaawansowanym **Zastosuj**, równa **ten obiekt i wszystkie obiekty zależne**.  

#### <a name="to-add-the-container"></a>Aby dodać kontener  

1.  Użyj konta, które ma uprawnienie **Tworzenie wszystkich obiektów podrzędnych** w kontenerze **System** w usługach domenowych Active Directory.  

2.  Uruchom **ADSI Edit** (adsiedit.msc) i połącz się z domeną serwera lokacji.  

3.  Utwórz kontener:  

    -   Rozwiń węzeł **domeny** &lt;w pełni kwalifikowana nazwa domeny komputera\>, rozwiń węzeł &lt;nazwy wyróżniającej\>, kliknij prawym przyciskiem myszy **CN = System**, wybierz **nowy**, a następnie wybierz pozycję **obiektu**.  

    -   W **Utwórz obiekt** oknie dialogowym wybierz **kontenera**, a następnie wybierz pozycję **dalej**.  

    -   W **wartość** wprowadź **System zarządzania**, a następnie wybierz pozycję **dalej**.  

4.  Przypisz uprawnienia:  

    > [!NOTE]  
    >  Jeśli wolisz, możesz użyć innych narzędzi, na przykład narzędzia administracyjnego Użytkownicy i komputery usługi Active Directory (dsa.msc), aby dodać uprawnienia do kontenera.  

    -   Kliknij prawym przyciskiem myszy **CN = Zarządzanie systemem**, a następnie wybierz pozycję **właściwości**.  

    -   Wybierz **zabezpieczeń** , wybierz pozycję **Dodaj**, a następnie dodaj konto komputera serwera lokacji z **Pełna kontrola** uprawnienia.  

    -   Wybierz **zaawansowane**, wybierz konto komputera serwera lokacji, a następnie wybierz **Edytuj**.  

    -   W **Zastosuj** wybierz **ten obiekt i wszystkie obiekty zależne**.  

5.  Wybierz **OK** aby zamknąć konsolę i zapisać konfigurację.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>Krok 3. Konfigurowanie lokacji do publikowania w usługach domenowych w usłudze Active Directory  
 Po skonfigurowaniu kontenera, zostały przyznane uprawnienia i zainstalowaniu lokacji głównej programu Configuration Manager, można skonfigurować tej lokacji do publikowania danych w usłudze Active Directory.  

 Aby uzyskać więcej informacji o publikowaniu, zobacz [publikowania danych lokacji programu System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md).  
