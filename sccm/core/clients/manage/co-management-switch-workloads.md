---
title: "Przełącz obciążeń programu Configuration Manager do usługi Intune"
description: "Dowiedz się, jak przełącznik obciążeń obecnie zarządzany przez Menedżera konfiguracji w usłudze Microsoft Intune."
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: 
ms.assetid: 60e2022f-a4f9-40dd-af01-9ecb37b43878
ms.openlocfilehash: 60aff996ec598cff7572a0e88c631dc9c509e007
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="switch-configuration-manager-workloads-to-intune"></a>Przełącz obciążeń programu Configuration Manager do usługi Intune
W [urządzenia przygotowanie systemu Windows 10 do zarządzania wspólnej](co-management-prepare.md), przygotowywania urządzenia z systemem Windows 10 do zarządzania wspólnej. Te urządzenia są przyłączone do usługi AD i Azure AD i są zarejestrowane w usłudze Intune i zainstalować klienta Configuration Manager. Prawdopodobnie nadal masz urządzenia z systemem Windows 10, które dołączyły do usługi AD i klienta programu Configuration Manager, ale nie zostały dołączone do usługi Azure AD lub zarejestrowane w usłudze Intune. Poniższa procedura zawiera kroki, aby włączyć zarządzanie wspólnej przygotowanie pozostałe urządzenia z systemem Windows 10 (klientów programu Configuration Manager bez rejestracji w usłudze Intune) do wspólnego zarządzania i umożliwia rozpoczęcie przełączania określonego programu Configuration Manager obciążeń do usługi Intune.

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**.    
2. Na karcie Narzędzia główne w grupie zarządzania, wybierz **konfigurowania zarządzania wspólnej** aby otworzyć Kreatora konfiguracji zarządzania wspólnej.    
3. Na stronie subskrypcji kliknij **logowania** i zaloguj się do dzierżawy usługi Intune, a następnie kliknij przycisk **dalej**.   
4. Na stronie aktywacji wybierz **pilotażu** lub **wszystkie** Włączanie automatycznej rejestracji w usłudze Intune, a następnie kliknij przycisk **dalej**. Po wybraniu **pilotażu**, tylko klienci programu Configuration manager, które są elementami członkowskimi grupy pilotażu automatycznie zarejestrowane w usłudze Intune. Dzięki temu można włączyć zarządzanie wspólnej w podzestawie klientów do początkowego testowania wspólnego zarządzania i zarządzania wspólnej wdrożenia przy użyciu podejście etapowe. W wierszu polecenia może służyć do wdrażania klienta programu Configuration Manager jako aplikacja w usłudze Intune dla urządzenia już zarejestrowane w usłudze Intune. Aby uzyskać więcej informacji, zobacz [urządzeń z systemem Windows 10 zarejestrowanych w usłudze Intune](co-management-prepare.md#windows-10-devices-enrolled-in-intune).
5. Na stronie obciążeń wybierz, czy przełączyć obciążeń programu Configuration Manager ma być zarządzany przez projekt pilotażowy usługi Intune lub usługi Intune, a następnie kliknij przycisk **dalej**. **Intune pilotażu** ustawienie zmienia obciążenia skojarzone tylko dla urządzeń z grupy pilotażu. **Intune** skojarzone obciążenia dla wszystkich urządzeń z systemem Windows 10 zarządzane wspólnie zmienia ustawienia. 
        
   > [!Important]    
   > Przed przejściem dowolnych zadań upewnij się, odpowiednich obciążenia w usłudze Intune został poprawnie skonfigurowany i wdrożony. W ten sposób zapewnia, że obciążeń zawsze są zarządzane przez jeden z narzędzia do zarządzania urządzeniami.   
1. Na stronie przemieszczania, skonfiguruj następujące ustawienia, a następnie kliknij przycisk **dalej**:
    - **Projekt pilotażowy**: Grupy pilotażowej zawiera co najmniej jednej kolekcji, które można wybrać. Użyj tej grupy w ramach wdrożenia etapowego zarządzania wspólnej. Można rozpoczynać się od małej testowej kolekcji, a następnie dodaj więcej kolekcji, do grupy pilotażowe wdrożenie zarządzania wspólnej do większej liczby użytkowników i urządzeń. Kolekcje w grupie pilotażowego można zmienić w dowolnym momencie we właściwościach zarządzania wspólnej.
    - **Produkcji**: Skonfiguruj **grupie wykluczenia** z co najmniej jedną kolekcję. Urządzenia, które są członkami kolekcji w tej grupie są wykluczone z za pomocą zarządzania wspólnej. 
2. Aby włączyć zarządzanie wspólnej, Zakończ pracę kreatora.  

## <a name="modify-your-co-management-settings"></a>Modyfikowanie ustawień zarządzania wspólnej
Po włączeniu wspólnego zarządzania za pomocą kreatora, można zmodyfikować ustawienia we właściwościach zarządzania wspólnej.  
- W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**.  
Wybierz obiekt wspólnej zarządzania, a następnie na karcie Narzędzia główne, kliknij przycisk **właściwości**. 

## <a name="monitor-co-management"></a>Monitorowania zarządzania wspólnej
Po włączeniu wspólnego zarządzania można monitorować wspólnej zarządzania urządzeniami przy użyciu następujących metod:
- **SQL widoku i klasy WMI**: Można zbadać **v &#95; ClientCoManagementState** widoku SQL w bazie danych lokacji programu Configuration Manager lub **SMS &#95; &#95; klienta ComanagementState** klasy usługi WMI. Informacje w klasie usługi WMI można utworzyć kolekcji niestandardowych w programie Configuration Manager w celu określenia stanu wdrożenia zarządzania wspólnej. Aby uzyskać więcej informacji, zobacz [sposobach tworzenia kolekcji](/sccm/core/clients/manage/collections/create-collections). Następujące pola są dostępne w widoku SQL i klasy WMI: 
    - **MachineId**: Określa unikatowy identyfikator urządzenia dla klienta programu Configuration Manager.
    - **MDMEnrolled**: Określa, czy urządzenie jest zarejestrowane zarządzania urządzeniami Przenośnymi. 
    - **Urząd**: Określa urząd rejestrowania urządzenia.
    - **ComgmtPolicyPresent**: Określa, czy zasady zarządzania wspólnej programu Configuration Manager istnieją na komputerze klienckim. Jeśli **MDMEnrolled** wartość jest **0**, urządzenie nie jest umieszczone zarządzane niezależnie od tego, czy zasady zarządzania wspólnej istnieje na komputerze klienckim.

   > [!Note]    
   > Urządzenie jest zarządzane wspólnie, gdy **MDMEnrolled** pola i **ComgmtPolicyPresent** pola zarówno mają wartość **1**.

- **Zasady wdrażania**:  Istnieją dwie zasady są tworzone w **monitorowanie** > **wdrożeń**; jednej zasady dla grupy pilotażowej i jeden w środowisku produkcyjnym. Te zasady tylko raport z liczbą urządzeń, których programu Configuration Manager ma stosowane zasady. Nie traktuje ile urządzeń zarejestrowanych w usłudze Intune, który jest wymagany, zanim urządzenia mogą być zarządzane wspólnie.  

## <a name="check-compliance-for-co-managed-devices"></a>Sprawdź zgodność wspólnie zarządzanych urządzeń
Użytkownicy mogą korzystać z programu Software Center, aby sprawdzić zgodność ich wspólnie zarządzanych urządzeń z systemem Windows 10, niezależnie od tego, czy dostęp warunkowy jest zarządzany przez programu Configuration Manager lub usługi Intune. Użytkownicy mogą także sprawdzać zgodność przy użyciu aplikacji Portal firmy, gdy dostęp warunkowy jest zarządzane przez usługę Intune.

## <a name="next-steps"></a>Następne kroki
Użyj następujących zasobów w celu zarządzania obciążeń, które można przełączyć się do usługi Intune:
- [Zasady zgodności urządzeń](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Zasady dostępu do zasobów](https://docs.microsoft.com/intune/device-profiles)
- [Usługi Windows Update dla firm zasad](https://docs.microsoft.com/intune/windows-update-for-business-configure)
