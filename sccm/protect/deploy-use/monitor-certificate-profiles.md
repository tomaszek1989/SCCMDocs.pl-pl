---
title: "Monitorowanie profili certyfikatów | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie monitorowania stanu zgodności profili certyfikatów programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
caps.latest.revision: 7
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 84e275fa5b17bc703da22fb686ef9050d17e557f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>Monitorowanie profili certyfikatów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Wyświetl wyniki zgodności w konsoli programu Configuration Manager  

Monitorowanie zgodności certyfikatów protokołu SCEP należy używać konsoli, raczej, użyj [raporty](#view-compliance-results-by-using-reports). 

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**>  **wdrożeń**.  

3.  Wybierz wdrożenie profilu certyfikatu zainteresowania.  

4.  Przejrzyj informacje o zgodności certyfikatów podsumowania na stronie głównej. Bardziej szczegółowe informacje, wybierz profil certyfikatu, a następnie na **Home** w karcie **wdrożenia** grupy, wybierz **Wyświetl stan** otworzyć **stan wdrożenia** strony.  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodny z**: Wyświetla zgodność profilu certyfikatu na podstawie liczby zasobów, których dotyczy problem. Możesz dwukrotnie kliknąć zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników zgodnych z profilem certyfikatu. W okienku **Szczegóły zasobu** także zostaną wyświetleni użytkownicy zgodni z danym profilem. Kliknij dwukrotnie użytkownika na liście, aby uzyskać więcej informacji.  

        > [!IMPORTANT]  
        >  Profil certyfikatu nie jest oceniany, jeśli nie dotyczy urządzenia klienckiego. Jego stan jest jednak zwracany jako zgodny.  

    -   **Błąd**: Wyświetla listę wszystkich błędów dla wybranego wdrożenia profilu certyfikatu na podstawie liczby zasobów, których dotyczy problem. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników, dla których wygenerowano błąd związany z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji.  

    -   **Niezgodny**: Wyświetla listę wszystkich niezgodnych zasad w profilu certyfikatu na podstawie liczby zasobów, których dotyczy problem. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników, którzy nie są zgodni z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji o danym problemie.  

    -   **Nieznany**: Wyświetla listę wszystkich użytkowników, którzy nie zgłosili zgodności dla wybranego wdrożenia profilu certyfikatu wraz z bieżącym stanem klienta urządzeń.  

5.  Na **stan wdrożenia** Przejrzyj szczegółowe informacje o zgodności wdrożonego profilu certyfikatu. W węźle **Wdrożenia** jest tworzony węzeł tymczasowy, który ułatwia szybkie znalezienie tych informacji ponownie.  

     Stan rejestracji certyfikatu jest wyświetlany jako numer. W poniższej tabeli przedstawiono znaczenie poszczególnych numerów:  

    |Stan rejestracji|Opis|  
    |-----------------------|-----------------|  
    |0x00000001|Rejestracja powiodła się, a certyfikat został wydany.|  
    |0x00000002|Żądanie zostało przesłane i trwa oczekiwanie na zarejestrowanie lub żądanie zostało wydane poza pasmem.|  
    |0x00000004|Rejestracja musi zostać odroczona.|  
    |0x00000010|Wystąpił błąd.|  
    |0x00000020|Nieznany stan rejestracji.|  
    |0x00000040|Informacje o stanie zostały pominięte. Taka sytuacja może wystąpić, jeśli urząd certyfikacji HYPERLINK „http://msdn.microsoft.com/en-us/windows/ms721572” \l „_security_certification_authority_gly” jest nieprawidłowy lub nie został wybrany do monitorowania.|  
    |0x00000100|Odmówiono rejestracji.|  

##  <a name="view-compliance-results-by-using-reports"></a>Wyświetl wyniki zgodności przy użyciu raportów

 Ustawienia zgodności w programie System Center Configuration Manager obejmują wbudowane raporty, których można użyć do monitorowania informacji o profilach certyfikatów. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów **Filtr urządzenia** i **Filtr użytkownika** w raportach ustawień zgodności należy użyć symbolu wieloznacznego (%).  

Monitorowanie zgodności certyfikatów protokołu SCEP używać tych raportów certyfikatu w węźle raport **dostęp do zasobów firmy**:  

 -   Historia wystawiania certyfikatów  
 -   Lista zasobów z certyfikatami, które wkrótce wygasną  
 -   Lista zasobów według stanu wystawiania certyfikatu  



 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie System Center Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

