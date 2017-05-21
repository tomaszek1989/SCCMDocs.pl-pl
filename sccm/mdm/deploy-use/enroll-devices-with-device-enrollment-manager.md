---
title: "Rejestrowanie urządzeń przy użyciu Menedżera rejestracji urządzeń - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Rejestrowanie firmowych urządzeń za pomocą konta Menedżera rejestracji urządzeń z System Center Configuration Manager."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: 8
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7573590763c68a4c97d388be1e64054c318da9cc
ms.openlocfilehash: 8c491636925670732e6af67d8c1c741e4793ef96
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Rejestrowanie urządzeń przy użyciu Menedżera rejestracji urządzeń z programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Organizacje mogą używać usługi Intune do zarządzania dużą liczbą urządzeń przenośnych za pomocą jednego konta użytkownika. *Menedżera rejestracji urządzeń* konto (DEM) to specjalne konto użytkownika, które mogą rejestrować urządzenia do 1000. Istniejący użytkownicy są dodawane konto DEM im przekazać specjalne możliwości DEM. Każdy zarejestrowane urządzenie używa jednej licencji. Zalecane jest użycie urządzenia zarejestrowane za pomocą tego konta jako udostępnionego urządzenia z Brak koligacji użytkownika, a nie urządzeń osobistych, dedykowanego.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>Rejestrowanie firmowych urządzeń za pomocą Menedżera rejestracji urządzeń  
 Użytkownik może przypisać menedżera lub kierownika magazynu, na przykład Menedżera rejestracji urządzeń konta użytkownika, aby umożliwić wykonywanie następujących czynności:  

-   Rejestrowanie do 1000 urządzeń do zarządzania  
-   Instalowanie aplikacji firmowych przy użyciu aplikacji Portal firmy  
-   Konfigurowanie dostępu do danych firmowych  

Na urządzeniach zarządzanych przy użyciu konta Menedżera rejestracji urządzeń mają zastosowanie następujące ograniczenia:

- Menedżer magazynu nie można zresetować urządzenia z portalu firmy.  
- Urządzenia nie mogą zostać dołączone do obszaru roboczego lub przyłączona do usługi Azure Active Directory. Zapobiega to korzystania z dostępu warunkowego tych urządzeń.
-  Do wdrażania aplikacji firmowych na urządzeniach zarządzanych za pomocą Menedżera rejestracji urządzeń, należy wdrożyć aplikację Portal firmy jako **wymagana instalacja** kontu użytkownika Menedżera rejestracji urządzeń. Następnie uruchomić aplikacji Portal firmy, aby zainstalować dodatkowe aplikacje Menedżera rejestracji urządzeń.
- W celu poprawy wydajności aplikacji Portal firmy wyświetlane są tylko urządzenia lokalnego. Zdalne zarządzanie innymi urządzeniami DEM może być przeprowadzone wyłącznie z konsoli programu Configuration Manager i administratora
- Witryna sieci Web portalu firmy nie jest dostępny dla konta Menedżera rejestracji urządzeń. Korzystać z aplikacji Portal firmy.
- (tylko iOS) Jeśli używasz DEM, aby zarejestrować urządzenia iOS, nie można użyć programu Apple Configurator lub Apple Device Enrollment Program (DEP) do rejestrowania urządzeń.

 **Przykład scenariusza Menedżera rejestracji urządzeń:**   
Restauracja potrzebuje tabletów do punktów sprzedaży dla personelu oczekiwania i kolejność monitory dla personelu kuchni. Pracownicy nigdy nie potrzebujesz dostępu do danych firmy lub zaloguj się jako użytkownik. Administrator usługi Intune tworzy konto menedżera rejestracji urządzeń i rejestruje urządzenia należące do firmy za pomocą tego konta. Alternatywnie administrator może również przyznać rejestracji urządzeń Menedżer poświadczeń menedżerowi restauracji, umożliwiając mu tym samym rejestrowanie urządzeń i zarządzanie nimi.  

 Administrator lub Menedżer może wdrożyć aplikacje specyficzne dla ról na urządzeniach w restauracji. Administrator może również wybrać urządzenie w konsoli i wycofać je z zarządzania urządzeniami przenośnymi.  

#### <a name="add-a-device-enrollment-manager"></a>Dodawanie menedżera rejestracji urządzeń  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Wybierz subskrypcję Microsoft Intune, do którego można będzie dodać Menedżera rejestracji urządzeń, a następnie kliknij **właściwości**.  

3.  W oknie dialogowym właściwości subskrypcji usługi Microsoft Intune, kliknij przycisk **Menedżera rejestracji urządzeń** kartę.  

4.  Kliknij przycisk **Dodaj lub usuń**.  

5.  W **Menedżera rejestracji urządzeń** okno dialogowe, wpisz nazwę użytkownika, o których chcesz dodać jako menedżera rejestracji urządzeń, a następnie kliknij przycisk **wyszukiwania**. Wybierz użytkownika, o której chcesz dodać jako menedżera rejestracji urządzeń, a następnie kliknij przycisk **Dodaj**.  

6.  Konto użytkownika, który będzie menedżerem rejestracji urządzeń i kliknij przycisk Potwierdź **Dodaj lub usuń**.  Dla każdego użytkownika uzyskującego dostęp do usługi wymagana jest licencja subskrypcji i *Menedżera rejestracji urządzeń* nie może być administratorem usługi Intune. Ustal, czy potrzebujesz dodać więcej licencji, przed użyciem tej funkcji.  

7.  Menedżer rejestracji urządzeń może teraz rejestrować urządzenia przenośne za pomocą tej samej procedury, której używa użytkownik końcowy w ramach scenariusza (BYOD) Przełącz your właścicielem — urządzenia w portalu firmy.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Usuwanie Menedżera rejestracji urządzeń z usługi Intune  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Wybierz subskrypcję Microsoft Intune, do którego można będzie dodać Menedżera rejestracji urządzeń, a następnie kliknij **właściwości**.  

3.  W oknie dialogowym właściwości subskrypcji usługi Microsoft Intune, kliknij przycisk **Menedżera rejestracji urządzeń** kartę.  

4.  **Wyszukiwanie** dla Menedżera rejestracji urządzeń, które chcesz usunąć, a następnie kliknij przycisk **Usuń**, następnie **OK**.  

 Usunięcie Menedżera rejestracji urządzeń nie ma wpływu na zarejestrowane urządzenia. Gdy Menedżer rejestracji urządzeń zostanie usunięty:  

-   Problem dotyczy nie zarejestrowane urządzenia  

-   Zarejestrowane urządzenia będą nadal w pełni zarządzane  

-   Poświadczenia konta Menedżera rejestracji urządzeń, nadal obowiązują zalogować się do portalu firmy w celu uzyskiwania dostępu do aplikacji  

-   Poświadczenia konta Menedżera rejestracji urządzeń nadal nie można wyczyścić lub wycofania urządzenia  

-   Relacja konta Menedżera rejestracji urządzeń z zarejestrowanymi urządzeniami zostaną zachowane, ale nie można zarejestrować żadnych dodatkowych urządzeń

