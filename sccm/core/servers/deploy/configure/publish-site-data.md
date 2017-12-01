---
title: Publikowanie danych lokacji
titleSuffix: Configuration Manager
description: "Dowiedz się, jak publikować Lokacje programu Configuration Manager w usługach domenowych w usłudze Active Directory."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: "8"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 70f3d0d048d1a80e9f11cc111166dd3ade0325f5
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="publish-site-data-for-system-center-configuration-manager"></a>Publikowanie danych lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po rozszerzeniu schematu usługi Active Directory dla programu System Center Configuration Manager można publikować Lokacje programu Configuration Manager do usług domenowych w usłudze Active Directory (AD DS). Dzięki temu komputery usługi Active Directory, bezpieczne pobieranie informacji o lokacji z zaufanego źródła. Mimo że publikowanie informacji o lokacji w usługach AD DS nie jest wymagane dla podstawowych funkcji programu Configuration Manager, zmniejsza koszty administracyjne, aby to zrobić.  

-   **Jeśli witryna została skonfigurowana do publikowania w usługach AD DS**, klientów programu Configuration Manager mogą automatycznie znaleźć punkty zarządzania poprzez publikowanie w usłudze Active Directory. Używają zapytanie LDAP do serwera wykazu globalnego.  

-   **Jeśli lokacja nie publikuje informacji w usługach AD DS**, klienci muszą mieć alternatywny mechanizm lokalizowania ich domyślnego punktu zarządzania.  

Aby dowiedzieć się jak klienci znajdują się punkt zarządzania, zobacz [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="configure-sites-to-publish-to-ad-ds"></a>Konfigurowanie lokacji do publikowania informacji w usługach AD DS  
 Poniżej przedstawiono ogólną procedurę:  

-   Należy [rozszerzyć schemat usługi Active Directory dla programu System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md) w każdym lesie, w którym będą publikowane dane lokacji. Upewnij się również **System zarządzania** kontenera jest obecny.  

-   Należy przydzielić kontu komputera każdej lokacji głównej, która będzie publikować dane **Pełna kontrola** do **System zarządzania** kontenera i wszystkich jego obiektów podrzędnych.  

### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-active-directory-forest"></a>Aby umożliwić lokacji programu Configuration Manager publikowanie informacji o lokacji w lesie usługi Active Directory

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i kliknij przycisk **witryny**. Wybierz lokację, która ma być publikowania własnych danych lokacji. Następnie na **Home** karcie **właściwości** kliknij przycisk **właściwości**.  

3.  Na **publikowania** kartę właściwości lokacji wybierz lasy, do których ta lokacja ma publikować dane lokacji.  

4.  Kliknij przycisk **OK** , aby zapisać konfigurację.  

### <a name="to-set-up-active-directory-forests-for-publishing"></a>Aby skonfigurować lasy usługi Active Directory do publikowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** kliknij pozycję **Lasy usługi Active Directory**. Jeśli odnajdywanie lasu za pomocą usługi Active Directory było wcześniej uruchamiane, wszystkie odnalezione lasy zostaną wyświetlone w okienku wyników. Uruchomienie odnajdywania lasu za pomocą usługi Active Directory powoduje odnalezienie lasu lokalnego oraz wszystkich lasów zaufanych. Ręcznie należy dodać tylko lasy niezaufane.  

    -   Aby skonfigurować poprzednio odnalezionego lasu, wybierz go w okienku wyników. Następnie na **Home** karcie **właściwości** kliknij przycisk **właściwości** aby otworzyć właściwości lasu. Przejdź do kroku 3.  

    -   Do skonfigurowania nowego lasu, który nie ma na liście, na **Home** karcie **Utwórz** kliknij przycisk **Dodaj las** otworzyć **Dodawanie lasów** okno dialogowe. Przejdź do kroku 3.  

3.  Na **ogólne** karcie, Dokończ konfigurację lasu, który chcesz odnaleźć i określ **konto lasu usługi Active Directory**.  

    > [!NOTE]  
    >  Aby odnajdywać lasy niezaufane i w nich publikować, odnajdywanie lasu usługi Active Directory wymaga konta globalnego. Jeżeli nie używasz konta komputera serwera lokacji, możesz wybrać tylko konto globalne.  

4.  Jeśli planujesz zezwolić lokacjom na publikowanie danych lokacji w tym lesie, dokończ konfigurację publikowania w tym lesie na karcie **Publikowanie** .  

    > [!NOTE]  
    >  Jeśli zezwolisz lokacjom na publikowanie w lesie, musisz rozszerzyć schemat usługi Active Directory tego lasu dla programu Configuration Manager. Konto lasu usługi Active Directory musi mieć uprawnienia pełnej kontroli do kontenera systemu w tym lesie.  

5.  Po zakończeniu konfigurowania tego lasu do stosowania z odnajdywaniem lasu usługi Active Directory kliknij przycisk **OK** , aby zapisać konfigurację.  
