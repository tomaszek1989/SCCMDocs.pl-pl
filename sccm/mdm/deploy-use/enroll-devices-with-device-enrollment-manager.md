---
title: "Rejestrować urządzenia za pomocą Menedżera rejestracji urządzeń — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Rejestrowanie firmowych urządzeń przy użyciu konta Menedżera rejestracji urządzeń z System Center Configuration Manager."
ms.custom: na
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: "8"
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: dcc35fb6ebe385d07a3b60e8968e06dec8ad60af
ms.sourcegitcommit: 40f2a4e3cc546e6bfd10f195a8e87af2b0780928
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Rejestrować urządzenia za pomocą Menedżera rejestracji urządzeń z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Organizacje mogą zarządzać dużą liczbą urządzeń przenośnych za pomocą jednego konta użytkownika przy użyciu usługi Intune. *Menedżera rejestracji urządzeń* konto (urządzeń DEM) to specjalne konto użytkownika użyte do rejestracji urządzeń. Możesz dodać istniejących użytkowników do konta Menedżera rejestracji urządzeń, aby nadać im funkcje specjalne Menedżera rejestracji urządzeń. Każdy zarejestrowane urządzenie korzysta z pojedynczej licencji. Zaleca się, że używasz urządzenia zarejestrowane za pomocą tego konta jako udostępnionych urządzeń bez koligacji użytkownika, a nie urządzenia osobiste, dedykowane.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>Rejestrowanie urządzeń należących do firmy przy użyciu Menedżera rejestracji urządzeń  
 Można przypisać Menedżer magazynu lub przełożonego, na przykład Menedżera rejestracji urządzeń konta użytkownika, aby umożliwić jej wykonanie następujących czynności:  

-   Rejestrowanie maksymalnie 1000 urządzeń do zarządzania  
-   Za pomocą aplikacji Portal firmy, aby zainstalować aplikacje firmowe  
-   Konfigurowanie dostępu do danych firmowych  

Na urządzeniach zarządzanych za pomocą konta Menedżera rejestracji urządzeń obowiązują następujące ograniczenia:

- Menedżer magazynu nie można zresetować urządzenia z portalu firmy.  
- Urządzenia nie może być dołączone do obszaru roboczego lub przyłączonych do usługi Azure Active Directory. Zapobiega to przy użyciu dostępu warunkowego tych urządzeń.
-  Aby wdrożyć aplikacje firmowe do urządzeń zarządzanych za pomocą Menedżera rejestracji urządzeń, Wdróż aplikację Portal firmy jako **wymagana instalacja** do konta użytkownika Menedżera rejestracji urządzeń. Menedżer rejestracji urządzeń można następnie uruchom aplikację Portal firmy, aby zainstalować dodatkowe aplikacje.
- Aby zwiększyć wydajność, aplikacja Portal firmy wyświetlane są tylko urządzenie lokalne. Zdalne zarządzanie innymi urządzeniami Menedżera rejestracji urządzeń jest możliwe tylko z konsoli programu Configuration Manager i administratora
- Witryny sieci Web Portal firmy nie jest dostępny dla konta Menedżera rejestracji urządzeń. Użyj aplikacji Portal firmy.
- Jeśli używasz Menedżera rejestracji urządzeń do zarejestrowania urządzenia z systemem iOS do rejestracji urządzeń nie można użyć narzędzia Apple Configurator lub Apple Device Enrollment Program (DEP). (dotyczy tylko urządzeń z systemem iOS) 

 **Przykłady scenariusza Menedżera rejestracji urządzeń:**   
Restauracja potrzebuje tabletów do punktów sprzedaży dla swoich kelnerów oraz monitorów zamówień dla personelu w kuchni. Pracownicy nigdy nie potrzebują dostępu do danych firmowych lub zaloguj się jako użytkownik. Administrator usługi Intune tworzy konto menedżera rejestracji urządzeń i rejestruje urządzenia należące do firmy za pomocą tego konta. Alternatywnie administrator może zapewnić rejestracji urządzeń poświadczenia Menedżera do Menedżera restauracji, zbliża się do zarejestrowania i zarządzania urządzeniami.  

 Administrator lub Menedżer można wdrażać aplikacje specjalne urządzeniom restauracji. Administrator można wybrać urządzenie w konsoli i wycofać je z zarządzania urządzeniami przenośnymi.  

#### <a name="add-a-device-enrollment-manager"></a>Dodawanie menedżera rejestracji urządzeń  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Wybierz subskrypcję Microsoft Intune, do którego można będzie dodać Menedżera rejestracji urządzeń, a następnie kliknij **właściwości**.  

3.  W oknie dialogowym właściwości subskrypcji usługi Microsoft Intune kliknij **Menedżera rejestracji urządzeń** kartę.  

4.  Kliknij przycisk **dodawania i usuwania**.  

5.  W **Menedżera rejestracji urządzeń** okna dialogowego, wpisz nazwę użytkownika, aby dodać jako menedżera rejestracji urządzeń, a następnie kliknij przycisk **wyszukiwania**. Wybierz użytkownika, które chcesz dodać jako menedżera rejestracji urządzeń, a następnie kliknij przycisk **Dodaj**.  

6.  Upewnij się, konto użytkownika, który ma być Menedżera rejestracji urządzeń, a następnie kliknij przycisk **Dodaj lub usuń**.  Dla każdego użytkownika uzyskującego dostęp do usługi wymagana jest licencja subskrypcji i *Menedżera rejestracji urządzeń* nie może być administratorem usługi Intune. Ustal, czy potrzebujesz dodać więcej licencji, przed użyciem tej funkcji.  

7.  Menedżer rejestracji urządzeń mogą od teraz rejestrować urządzenia przenośne przy użyciu tej samej procedury, które użytkownik końcowy używa do scenariusza (BYOD) bring-your własne urządzenie w portalu firmy.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Usuwanie Menedżera rejestracji urządzeń z usługi Intune  
Usunięcie Menedżera rejestracji urządzeń nie ma wpływu na zarejestrowanych urządzeniach. Po usunięciu Menedżera rejestracji urządzeń:  
- Brak zarejestrowanych urządzeń jest anulowana  
- Zarejestrowane urządzenia będą nadal pełni zarządzane  
- Poświadczenia konta Menedżera rejestracji urządzeń usunięto ważność zalogować się do portalu firmy na dostęp do aplikacji  
- Poświadczenia konta Menedżera rejestracji urządzeń usunięto nadal nie można wyczyścić lub wycofać urządzeń  
- Konta Menedżera rejestracji urządzeń usuniętych relacji do zarejestrowane urządzenia pozostaną, ale żadne dodatkowe urządzenia mogą być rejestrowane.

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  
2.  W obszarze roboczym **Administracja** rozwiń węzeł **Usługi w chmurze**, a następnie kliknij pozycję **Subskrypcje usługi Microsoft Intune**. Wybierz subskrypcję Microsoft Intune, do którego można będzie dodać Menedżera rejestracji urządzeń, a następnie kliknij **właściwości**.  
3.  W oknie dialogowym właściwości subskrypcji usługi Microsoft Intune kliknij **Menedżera rejestracji urządzeń** kartę.  
4.  **Wyszukiwanie** dla Menedżera rejestracji urządzeń, które chcesz usunąć, a następnie kliknij przycisk **Usuń**, następnie **OK**.  
