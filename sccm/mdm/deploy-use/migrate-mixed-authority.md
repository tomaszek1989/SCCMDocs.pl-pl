---
title: "Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi)"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zmienić urząd zarządzania urządzeniami Przenośnymi z hybrydowego zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune dla niektórych użytkowników."
keywords: 
author: dougeby
manager: dougeby
ms.date: 09/14/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 6f0201d7-5714-4ba0-b2bf-d1acd0203e9a
ms.openlocfilehash: 31d1d84c225d041f644669f0d3279e6bcd3f75ba
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="change-the-mdm-authority-for-specific-users-mixed-mdm-authority"></a>Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi) 

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Mieszane urzędu zarządzania urządzeniami Przenośnymi można skonfigurować w ramach tej samej dzierżawy, wybierając w przypadku niektórych użytkowników, które mają być zarządzane w usłudze Intune i innych użytkowników można zarządzać za pomocą hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager). Ten temat zawiera informacje o uruchamianiu przenoszenie użytkowników do autonomicznej usługi Intune i przyjęto założenie, że zostały wykonane następujące kroki:
- Używane narzędzie importowania danych do [importowania obiektów programu Configuration Manager z usługą Intune](migrate-import-data.md) (opcjonalnie).
- [Przygotowywania migracji użytkownika usługi Intune](migrate-prepare-intune.md) zapewnienie użytkownikom i ich urządzenia będą nadal zarządzane po ich migracji.

> [!Note]    
> Jeśli zdecydujesz, że chcesz wykonać pełne Resetowanie dzierżawie, co spowoduje usunięcie wszystkich zasad, aplikacji i rejestracji urządzeń, z działem pomocy technicznej Aby uzyskać pomoc.

Migrowanych użytkowników i ich urządzenia będą zarządzane w usłudze Intune i inne urządzenia będą nadal mają być zarządzane w programie Configuration Manager. Użytkownik rozpoczyna się od małych testowej grupy użytkowników, aby sprawdzić, czy wszystko działa zgodnie z oczekiwaniami. Stopniowo zostanie następnie migracji dodatkowych grup użytkowników, dopóki wszystko będzie gotowe zmienić urząd zarządzania urządzeniami Przenośnymi poziomie dzierżawy z programu Configuration Manager do autonomicznej usługi Intune. 

## <a name="things-to-know-before-you-migrate-users"></a>Co należy wiedzieć przed przeprowadzeniem migracji użytkowników
- Podczas migracji stopniowej wszelkie istniejące zasady zarządzania urządzeniami Przenośnymi lub aplikacji w programie Configuration Manager nadal stosuje się do urządzeń MDM hybrydowego.
- Użytkownicy są dodawani do grupy usługi AAD wyznaczony jako grupy migracji. Wszystkie urządzenia skojarzone z użytkownikami w grupie migracji są zarządzane w usłudze Intune.
- Jeśli urządzenia zostaną dodane do grupy usługi AAD, są ignorowane, chyba że znajdują się na urządzeniu bez skojarzonego użytkownika.
- Użytkownicy nie w grupie AAD oznaczone do migracji automatycznie dziedziczą urząd zarządzania urządzeniami Przenośnymi poziomie dzierżawy (program Configuration Manager).
- W przypadku migracji użytkownika do usługi Intune, użytkownika i urządzenia będą wyświetlane w usłudze Intune w portalu Azure po około 15 minut.  
- Podczas migracji użytkowników do autonomicznej usługi Intune, nadal zarządzać następującymi ustawieniami z programu Configuration Manager dla zarówno Intune autonomiczne, jak i hybrydowego zarządzania urządzeniami Przenośnymi na urządzeniach:
    - [Certyfikat Apple Push Notification service (APNs)](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)
    - [Program Device Enrollment Program](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)
    - Profile rejestracji
    - [Licencji programu zakupów zbiorczych](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)
    - Identyfikatory firmy 
    - [Certyfikaty podpisywania kodu](/sccm/mdm/deploy-use/enroll-hybrid-windows)
    - [Kategorie urządzeń](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections)
    - [Menedżerowie rejestracji](/sccm/mdm/plan-design/device-enrollment-methods)
    - Warunki i postanowienia
    - SLKs systemu Windows
    - Firmy znakowania w portalu    
      
> [!Important]    
  > Nadal edytować zasady poziomie dzierżawy przy użyciu konsoli programu Configuration Manager. Po [zmienić urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy](change-mdm-authority.md) do usługi Intune, czym zarządza się tych zasad w usłudze Intune na platformie Azure. 
- Zaleca się, że nie dokonuj migracji kont użytkowników, które zostały dodane jako menedżerów rejestracji urządzeń w programie Configuration Manager. Później gdy zmieniasz urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy do usługi Intune, te konta użytkowników będą migrowane poprawnie. W przypadku migrowania konta użytkownika Menedżera rejestracji urządzeń przed zmianą urzędu zarządzania urządzeniami Przenośnymi poziomie dzierżawy, musisz ręcznie dodać użytkownika jako menedżera rejestracji urządzeń w usłudze Intune na platformie Azure. Jednak urządzenia zarejestrowane przy użyciu Menedżera rejestracji urządzeń nie są migrowane pomyślnie. Należy wywołać pomocy technicznej, aby przeprowadzić migrację tych urządzeń. Aby uzyskać więcej informacji, zobacz [dodać Menedżera rejestracji urządzeń](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll#add-a-device-enrollment-manager).
- Urządzenia zarejestrowane przy użyciu Menedżera rejestracji urządzeń i urządzeń, które nie mają skojarzonych użytkowników nie są migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. Dla tych urządzeń należy się z działem pomocy technicznej, aby ułatwić tych poszczególnych urządzeń. Nie jest obsługiwane uruchamianie resetowania urzędu zarządzania urządzeniami Przenośnymi lub go spowoduje wyczyszczenie danych w usłudze Intune. Należy [zmienić urzędu zarządzania urządzeniami Przenośnymi](migrate-change-mdm-authority.md) z konsoli programu Configuration Manager.

## <a name="migrate-users-to-intune"></a>Migracja użytkowników do usługi Intune
Aby sprawdzić, czy konfiguracje Intune działają zgodnie z oczekiwaniami, należy najpierw przeprowadzić migrację niewielki zestaw użytkowników i urządzeń. Następnie po upewnieniu się, że elementy działają zgodnie z oczekiwaniami, można rozpocząć Migrowanie więcej grup usługi AAD z większej liczby użytkowników i urządzeń.

## <a name="migrate-a-test-group-of-users-to-intune-standalone"></a>Migrowanie testowej grupy użytkowników do autonomicznej usługi Intune.
Urządzenia dla użytkowników w kolekcji skojarzone z subskrypcją usługi Intune można zarejestrować hybrydowego zarządzania urządzeniami przenośnymi. Po usunięciu użytkownika z kolekcji, zarejestrowanych urządzeniach są migrowane do autonomicznej usługi Intune, jeśli użytkownik ma przypisaną licencję usługi Intune. Jeśli nie zostały jeszcze przypisane licencje użytkownikom który zamierzasz migrować, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/licenses-assign). W kolekcji w subskrypcji usługi Intune można wykluczyć kolekcje użytkowników ze swojej kolekcji można migrować użytkowników w wykluczonej kolekcji. 

W poniższym przykładzie kolekcji użytkowników hybrydowego zawiera wszystkie elementy członkowskie z kolekcji wszystkich użytkowników. Umożliwia użytkownikowi rejestrowania urządzenia w systemie hybrydowego zarządzania urządzeniami przenośnymi. Aby migrować użytkowników do autonomicznej usługi Intune, wybierz Wyklucz kolekcje i dodać kolekcji użytkowników do migracji. Gdy wszystko będzie gotowe przeprowadzić migrację większej liczby użytkowników, możesz dodać dodatkowe wykluczone kolekcje zawierające użytkowników. 

![Wykluczone kolekcje](../media/migrate-excludecollections.png)

> [!Note] 
> Jeśli masz **wszyscy użytkownicy** kolekcji wybranej na subskrypcję usługi Intune, nie możesz dodać regułę, aby wykluczyć kolekcje. Utwórz nową kolekcję na podstawie **wszyscy użytkownicy** kolekcji, sprawdź, czy kolekcja zawiera użytkowników, że oczekiwane, a następnie edytuj subskrypcję usługi Intune do użycia nowej kolekcji. Kolekcje użytkowników można wykluczyć z nowej kolekcji, aby przeprowadzić migrację użytkowników. 

Aby przeprowadzić migrację testowej grupy użytkowników do usługi Intune, utworzyć kolekcję użytkowników, które zawierają użytkowników, aby przeprowadzić migrację, a następnie wykluczyć kolekcji użytkowników z kolekcji używana dla subskrypcji usługi Intune.   

Następujący diagram zawiera omówienie działania migracji użytkowników.

 ![Omówienie urzędu mieszanych](../media/migrate-mixedauthority.svg)

1. Sprawdź, czy użytkownik ma licencję usługi Intune/EMS. 
2. Utwórz kolekcję, aby wykluczyć z kolekcji z subskrypcji usługi Intune. W tym przykładzie **hybrydowego wszystkich użytkowników** kolekcja zawiera reguły, aby wykluczyć użytkowników w **pilotażu migracji** kolekcji. **Użytkownik1** jest elementem członkowskim **pilotażu migracji** kolekcji i jest on wykluczony z **hybrydowego wszystkich użytkowników** kolekcji. 
3. **Użytkownik1**przez urządzenia są teraz zarządzane z usługi Intune w portalu Azure. 
4. Wszystkie inne urządzenia będą nadal zarządzane w konsoli programu Configuration Manager. 

## <a name="verify-intune-standalone-functionality"></a>Sprawdź funkcje autonomicznej usługi Intune
Po przeprowadzeniu migracji niewielki zbiór użytkowników, sprawdź, czy na urządzeniach użytkownika są wyświetlane w usłudze Intune. Przejdź do **urządzeń** bloku, a następnie wybierz **wszystkie urządzenia**. 

Następnie sprawdź, czy zasady, profile, aplikacje, etc. działają zgodnie z oczekiwaniami na urządzeniach użytkowników.

## <a name="migrate-additional-users"></a>Migrowanie dodatkowych użytkowników
Po upewnieniu się, że autonomicznej usługi Intune działa zgodnie z oczekiwaniami, można rozpocząć migrację dodatkowych użytkowników. Tak samo, jak utworzono kolekcję z zestawu testowego użytkowników, należy utworzyć kolekcje zawierające użytkowników do migracji i wykluczanie tych kolekcji z kolekcji skojarzone z subskrypcją usługi Intune. Aby uzyskać więcej informacji, zobacz [kolekcji skojarzonych z Twoją subskrypcją usługi Intune](#collection-associated-with-your-intune-subscription).

## <a name="next-steps"></a>Następne kroki
Po migracji użytkowników i przetestować funkcje usługi Intune, należy rozważyć, czy wszystko jest gotowe do [zmienić urząd zarządzania urządzeniami Przenośnymi](migrate-change-mdm-authority.md) dzierżawy usługi Intune z programu Configuration Manager do usługi Intune. 