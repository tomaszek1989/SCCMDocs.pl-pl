---
title: "Konfigurowanie klasyfikacji i produktów do zsynchronizowania | Dokumentacja firmy Microsoft"
description: "Wykonaj następujące kroki, aby skonfigurować klasyfikacje i produkty do zsynchronizowania w konsoli programu Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 6add66e625c790b65edf64216c2262a5d082f820
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
#  <a name="configure-classifications-and-products-to-synchronize"></a>Konfigurowanie klasyfikacji i produktów do zsynchronizowania  

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


> [!NOTE]  
>  Procedura opisana w tej sekcji ma zastosowanie tylko do lokacji najwyższego poziomu.  

 Podczas procesu synchronizacji w programie Configuration Manager na podstawie ustawień określonych we właściwościach składnika punktu aktualizacji oprogramowania są pobierane metadane aktualizacji oprogramowania. Po zsynchronizowaniu aktualizacji oprogramowania po raz pierwszy lub po wydaniu nowych produktów i klasyfikacje należy przejść do właściwości, aby wybrać nowe elementy. Aby skonfigurować klasyfikacje i produkty do zsynchronizowania, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>Aby skonfigurować klasyfikacje i produkty do zsynchronizowania  

1.  W **programu Configuration Manager** konsoli, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**.

2. Wybierz centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

3.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**.

4.  Na karcie **Klasyfikacje** określ klasyfikacje, w ramach których mają zostać zsynchronizowane aktualizacje oprogramowania.  

    > [!NOTE]  
    >  Każdą aktualizację oprogramowania definiuje klasyfikacja aktualizacji, która pomaga organizować aktualizacje w różne typy. Podczas procesu synchronizacji są synchronizowane metadane aktualizacji oprogramowania dla określonych klasyfikacji. Menedżer konfiguracji umożliwia synchronizowanie aktualizacji oprogramowania o następujących klasyfikacjach aktualizacji:  
    >   
    > - **Aktualizacje krytyczne**: Określa szeroko rozpowszechnianej aktualizacji dotyczącej konkretnego problemu, którego dotyczy krytyczną usterkę niepowiązaną z zabezpieczeń.  
    > - **Aktualizacje definicji**: Określenie aktualizacji plików definicji wirusów lub innych plików definicji.  
    > - **Funkcja pakiety**: Określenie nowych funkcji produktów dystrybuowanych poza wydaniami oraz najczęściej uwzględnianych w następnym pełnym wydaniu produktu.  
    > - **Aktualizacje zabezpieczeń**: Określenie szeroko rozpowszechnianej aktualizacji dotyczącej problemu z konkretnym produktem, związane z zabezpieczeniami.  
    > - **Dodatki Service Pack**: Określenie zbiorczego zestawu poprawek stosujących się do aplikacji. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje oprogramowania i tak dalej.  
    > - **Narzędzia**: Określenie programu narzędziowego lub funkcji pomagających wykonać jedno lub więcej zadań.  
    > - **Pakiety zbiorcze aktualizacji**: Określenie zbiorczego zestawu poprawek zebranych w jednym pakiecie w celu łatwiejszego wdrażania. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje zwykłe i tak dalej. Pakiet zbiorczy aktualizacji na ogół dotyczy konkretnego obszaru, takiego jak zabezpieczenia czy składnik produktu.  
    > - **Aktualizacje**: Określenie aktualizacji aplikacji lub pliku, który jest obecnie zainstalowany.  
    > - **Uaktualnij**: Określa uaktualnienia dla systemu Windows 10 funkcji i funkcjonalności.  
    >   
    >      Twoje punkty aktualizacji oprogramowania i witryn musi być uruchomiony co najmniej 4.0 WSUS z [poprawkę 3095113](https://support.microsoft.com/kb/3095113) uzyskać **uaktualnienia** klasyfikacji.  

5.  Na karcie **Produkty** określ produkty, w ramach których mają zostać zsynchronizowane aktualizacje oprogramowania, a następnie kliknij przycisk **Zamknij**.  

    > [!NOTE]  
    >  Metadane każdej aktualizacji oprogramowania definiują produkty, których dotyczy dana aktualizacja. Produkt to konkretna wersja systemu operacyjnego lub aplikacji, na przykład Windows Server 2012. Rodzina produktów to podstawowy system operacyjny lub podstawowa aplikacja, od których pochodzą produkty indywidualne. Przykładem rodziny produktów jest Windows, do której należy system operacyjny Windows Server 2012. Można określać rodziny produktów lub należące do nich produkty indywidualne. Im więcej produktów zostanie wybranych, tym dłużej potrwa synchronizacja aktualizacji oprogramowania.  
    >   
    >  Gdy aktualizacje oprogramowania dotyczą wielu produktów, a co najmniej jeden z nich zostanie wybrany do synchronizacji, wszystkie produkty pojawi się w konsoli programu Configuration Manager, nawet jeśli nie wybrano niektórych produktów. Na przykład jeśli system Windows Server 2012 jest jedynym systemem operacyjnym wybranym i aktualizacja oprogramowania dotyczy systemu Windows 8 i Windows Server 2012, obydwa te produkty będą wyświetlane w konsoli programu Configuration Manager.  

    > [!IMPORTANT]  
    >  Program Configuration Manager przechowuje listę produktów i rodzin produktów, spośród których można dokonać wyboru podczas pierwszej instalacji oprogramowania punktu aktualizacji. Produktów i rodzin produktów, wydane po wydaniu programu Configuration Manager mogą nie być dostępne do wybrania, dopóki nie zostanie ukończona synchronizacja aktualizacji oprogramowania, której lista produktów i rodzin produktów, spośród których można dokonać wyboru.  


## <a name="next-steps"></a>Następne kroki
Uruchom synchronizację aktualizacji oprogramowania, aby pobrać aktualizacje oprogramowania na podstawie nowych kryteriów. Aby uzyskać szczegółowe informacje, zobacz [synchronizowanie aktualizacji oprogramowania](synchronize-software-updates.md).

