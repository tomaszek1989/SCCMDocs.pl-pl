---
title: Monitorowanie profili certyfikatów
titleSuffix: Configuration Manager
description: Informacje o sposobie monitorowania stanu zgodności profilów certyfikatów w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a3a9c27eed58bce1b6d2371c545621b48f4b4f54
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>Jak monitorować profile certyfikatów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Wyświetlanie wyników zgodności w konsoli programu Configuration Manager  

Do monitorowania certyfikatów protokołu SCEP należy używać konsoli, a nie, użyj [raporty](#view-compliance-results-by-using-reports). 

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**>  **wdrożeń**.  

3.  Wybierz wdrożenie profilu certyfikatu zainteresowań.  

4.  Przejrzyj informacje o zgodności certyfikatów podsumowania na stronie głównej. Bardziej szczegółowe informacje, wybierz profil certyfikatu, a następnie na **Home** karcie **wdrożenia** grupy, wybierz **Wyświetl stan** można otworzyć **stan wdrożenia** strony.  

     Na stronie **Stan wdrożenia** znajdują się następujące karty:  

    -   **Zgodne**: Zawiera informacje o zgodności profilu certyfikatu na podstawie liczby uwzględnionych zasobów. Możesz dwukrotnie kliknąć zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników zgodnych z profilem certyfikatu. W okienku **Szczegóły zasobu** także zostaną wyświetleni użytkownicy zgodni z danym profilem. Kliknij dwukrotnie użytkownika na liście, aby uzyskać więcej informacji.  

        > [!IMPORTANT]  
        >  Profil certyfikatu nie jest oceniany, jeśli nie dotyczy urządzenia klienckiego. Jego stan jest jednak zwracany jako zgodny.  

    -   **Błąd**: Wyświetla listę wszystkich błędów dla wybranego wdrożenia profilu certyfikatu na podstawie liczby uwzględnionych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników, dla których wygenerowano błąd związany z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji.  

    -   **Niezgodne**: Wyświetla listę wszystkich niezgodnych reguł w profilu certyfikatu na podstawie liczby uwzględnionych zasobów. Możesz kliknąć dwukrotnie zasadę, aby utworzyć tymczasowy węzeł w węźle **Użytkownicy** obszaru roboczego **Zasoby i zgodność** . Ten węzeł zawiera wszystkich użytkowników, którzy nie są zgodni z tym profilem. Po wybraniu użytkownika w okienku **Szczegóły zasobu** zostaną wyświetleni użytkownicy, których dotyczy wybrany problem. Kliknij dwukrotnie użytkownika na liście, aby wyświetlić więcej informacji o danym problemie.  

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
    |0x00000040|Informacje o stanie zostały pominięte. Taka sytuacja może wystąpić, jeśli hiperłącze "http://msdn.microsoft.com/windows/ms721572" urzędu certyfikacji "_security_certification_authority_gly" \l jest nieprawidłowy lub nie został wybrany do monitorowania.|  
    |0x00000100|Odmówiono rejestracji.|  

##  <a name="view-compliance-results-by-using-reports"></a>Wyświetlanie wyników zgodności przy użyciu raportów

 Ustawienia zgodności w programie System Center Configuration Manager obejmują wbudowane raporty, które umożliwiają monitorowanie informacji o profilach certyfikatów. Te raporty mają kategorię **Zarządzanie zgodnością i ustawieniami**.  

> [!IMPORTANT]  
>  W przypadku korzystania z parametrów **Filtr urządzenia** i **Filtr użytkownika** w raportach ustawień zgodności należy użyć symbolu wieloznacznego (%).  

Do monitorowania certyfikatów protokołu SCEP używać tych raportów certyfikatu w węźle raportu **dostęp do zasobów firmy**:  

 -   Historia wystawiania certyfikatów  
 -   Lista zasobów z certyfikatami, które wkrótce wygasną  
 -   Lista zasobów według stanu wystawiania certyfikatu  



 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie System Center Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  
