---
title: Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi)
titleSuffix: Configuration Manager
description: Dowiedz się, jak zmienić urząd zarządzania urządzeniami Przenośnymi z hybrydowego zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune dla niektórych użytkowników.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: 6f0201d7-5714-4ba0-b2bf-d1acd0203e9a
ms.openlocfilehash: 46fb1333c58f3010acde4d064044a124050d211a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="change-the-mdm-authority-for-specific-users-mixed-mdm-authority"></a>Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi) 

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Mieszane urzędu zarządzania urządzeniami Przenośnymi można skonfigurować w ramach tej samej dzierżawy, wybierając w przypadku niektórych użytkowników, które mają być zarządzane w usłudze Intune i innych użytkowników można zarządzać za pomocą hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager). Ten artykuł zawiera informacje o uruchamianiu przenoszenie użytkowników do autonomicznej usługi Intune i przyjęto założenie, że zostały wykonane następujące kroki:
- Używane narzędzie importowania danych do [importowania obiektów programu Configuration Manager z usługą Intune](migrate-import-data.md) (opcjonalnie).
- [Przygotowywania migracji użytkownika usługi Intune](migrate-prepare-intune.md) zapewnienie użytkownikom i ich urządzenia będą nadal zarządzane po ich migracji.

> [!Note]    
> Jeśli zdecydujesz, że chcesz wykonać pełne Resetowanie dzierżawie, co spowoduje usunięcie wszystkich zasad, aplikacji i rejestracji urządzeń, z działem pomocy technicznej Aby uzyskać pomoc.

Migrowanych użytkowników i urządzeń, które są zarządzane w usłudze Intune i inne urządzenia będą nadal zarządzane w programie Configuration Manager. Rozpoczyna małych testowej grupy użytkowników, aby sprawdzić, czy wszystko działa zgodnie z oczekiwaniami. Następnie stopniowo migracji dodatkowe grupy użytkowników, dopóki wszystko będzie gotowe zmienić urząd zarządzania urządzeniami Przenośnymi poziomie dzierżawy z programu Configuration Manager do autonomicznej usługi Intune. 

## <a name="things-to-know-before-you-migrate-users"></a>Co należy wiedzieć przed przeprowadzeniem migracji użytkowników
- Podczas migracji stopniowej wszelkie istniejące zasady zarządzania urządzeniami Przenośnymi lub aplikacji w programie Configuration Manager nadal stosuje się do urządzeń MDM hybrydowego.
- Urządzenia dla użytkowników w kolekcji skojarzone z subskrypcją usługi Intune można zarejestrować hybrydowego zarządzania urządzeniami przenośnymi. Wszystkie urządzenia skojarzone z użytkownikami w kolekcji nie są zarządzane w usłudze Intune, tak długo, jak długo użytkownik ma licencję usługi Intune/EMS. 
- W przypadku migracji użytkownika do usługi Intune, użytkownika i urządzenia są wyświetlane w usłudze Intune w portalu Azure po około 15 minut.  
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
  > Nadal edytować zasady poziomie dzierżawy przy użyciu konsoli programu Configuration Manager. Po [zmienić urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy](change-mdm-authority.md) do usługi Intune, następnie można zarządzać tymi zasadami w usłudze Intune na platformie Azure. 
-   Jeśli używasz certyfikaty podpisywania kodu, zaleca się przeprowadzenie migracji użytkowników etapami kolejnym. Po przeprowadzeniu migracji urządzenia przenośnego, ułatwia żądanie certyfikatu urzędu nowego certyfikatu. Za pomocą podejście etapowe migrację użytkowników (i ich urządzeniami), ogranicza liczbę jednoczesnych certyfikatu urzędu żądań.
- Zaleca się, że nie dokonuj migracji kont użytkowników, które zostały dodane jako menedżerów rejestracji urządzeń w programie Configuration Manager. Później gdy zmieniasz urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy do usługi Intune, te konta użytkowników przeprowadzić migrację poprawnie. W przypadku migrowania konta użytkownika Menedżera rejestracji urządzeń przed zmianą urzędu zarządzania urządzeniami Przenośnymi poziomie dzierżawy, musisz ręcznie dodać użytkownika jako menedżera rejestracji urządzeń w usłudze Intune na platformie Azure. Jednak urządzenia zarejestrowane przy użyciu Menedżera rejestracji urządzeń nie są migrowane pomyślnie. Należy wywołać pomocy technicznej, aby przeprowadzić migrację tych urządzeń. Aby uzyskać więcej informacji, zobacz [dodać Menedżera rejestracji urządzeń](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll#add-a-device-enrollment-manager).
- Urządzenia zarejestrowane przy użyciu Menedżera rejestracji urządzeń i urządzeń bez [koligacji użytkownika](/sccm/mdm/deploy-use/user-affinity-for-hybrid-managed-devices) nie są automatycznie migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. Aby zmienić urząd zarządzania dla tych urządzeń do zarządzania urządzeniami Przenośnymi, zobacz [migracji urządzeń bez koligacji użytkownika](#migrate-devices-without-user-affinity).

## <a name="migrate-users-to-intune"></a>Migracja użytkowników do usługi Intune
Aby sprawdzić, czy konfiguracje Intune działają zgodnie z oczekiwaniami, należy najpierw przeprowadzić migrację niewielki zestaw użytkowników i urządzeń. Następnie po upewnieniu się, że elementy działają zgodnie z oczekiwaniami, można rozpocząć Migrowanie więcej grup usługi AAD z większej liczby użytkowników i urządzeń.

## <a name="migrate-a-test-group-of-users-to-intune-standalone"></a>Migrowanie testowej grupy użytkowników do autonomicznej usługi Intune.
Urządzenia dla użytkowników w kolekcji skojarzone z subskrypcją usługi Intune można zarejestrować hybrydowego zarządzania urządzeniami przenośnymi. Po usunięciu użytkownika z kolekcji, zarejestrowanych urządzeniach są migrowane do autonomicznej usługi Intune, jeśli użytkownik ma przypisaną licencję usługi Intune. Jeśli nie zostały jeszcze przypisane licencje użytkownikom który zamierzasz migrować, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/licenses-assign). W kolekcji w subskrypcji usługi Intune można wykluczyć kolekcje użytkowników ze swojej kolekcji można migrować użytkowników w wykluczonej kolekcji. 

W poniższym przykładzie kolekcji użytkowników hybrydowego zawiera wszystkie elementy członkowskie z kolekcji wszystkich użytkowników. Umożliwia użytkownikowi rejestrowania urządzenia w systemie hybrydowego zarządzania urządzeniami przenośnymi. Aby migrować użytkowników do autonomicznej usługi Intune, wybierz Wyklucz kolekcje i dodać kolekcji użytkowników do migracji. Gdy wszystko będzie gotowe przeprowadzić migrację większej liczby użytkowników, możesz dodać dodatkowe wykluczone kolekcje zawierające użytkowników. 

![Wykluczone kolekcje](../media/migrate-excludecollections.png)

> [!Note] 
> Jeśli masz **wszyscy użytkownicy** kolekcji wybranej na subskrypcję usługi Intune, nie możesz dodać regułę, aby wykluczyć kolekcje. Utwórz nową kolekcję na podstawie **wszyscy użytkownicy** kolekcji, sprawdź, czy kolekcja zawiera użytkowników, że oczekiwane, a następnie edytuj subskrypcję usługi Intune do użycia nowej kolekcji. Kolekcje użytkowników można wykluczyć z nowej kolekcji, aby przeprowadzić migrację użytkowników. 

Aby przeprowadzić migrację testowej grupy użytkowników do usługi Intune, utworzyć kolekcję użytkowników obejmującą tych użytkowników do migracji, a następnie wykluczyć kolekcji użytkowników z kolekcji używana dla subskrypcji usługi Intune.   

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

## <a name="migrate-devices-without-user-affinity"></a>Migrowanie urządzeń bez koligacji użytkownika
Urządzenia zarejestrowane przy użyciu Menedżera rejestracji urządzeń i urządzeń bez [koligacji użytkownika](/sccm/mdm/deploy-use/user-affinity-for-hybrid-managed-devices) nie są automatycznie migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. Można użyć *MdmDeviceAuthority przełącznika* polecenia cmdlet programu PowerShell w celu przełączania się między usługą Intune i program Configuration Manager urzędy zarządzania w następujących scenariuszach: 

-   Scenariusz 1. Użyj *MdmDeviceAuthority przełącznika* polecenia cmdlet migracji wybranych urządzeń, a następnie sprawdź, czy mogą być zarządzane przy użyciu usługi Intune na platformie Azure. Następnie, kiedy wszystko będzie gotowe, możesz [zmienić urząd zarządzania urządzeniami Przenośnymi do usługi Intune dla dzierżawy](migrate-change-mdm-authority.md) do przeprowadzenia migracji dla urządzeń. 
-   Scenariusz 2. Gdy wszystko będzie gotowe zmienić urząd zarządzania urządzeniami Przenośnymi dla dzierżawy usługi Intune, można wykonać następujące czynności w celu migracji urządzenia bez koligacji użytkownika:
    - Użyj polecenia cmdlet, aby zmienić urząd zarządzania urządzeniami Przenośnymi dla urządzeń bez koligacji użytkownika przed [zmienić urząd zarządzania urządzeniami Przenośnymi do usługi Intune dla dzierżawy](migrate-change-mdm-authority.md).    
    - Zadzwoń do pomocy technicznej, aby urządzenia bez koligacji użytkownika przełączono po zmianie urząd zarządzania urządzeniami Przenośnymi usługi Intune dla dzierżawcy.

Aby zmienić urząd zarządzania dla następujących urządzeń MDM, możesz użyć *MdmDeviceAuthority przełącznika* polecenia cmdlet w celu przełączania się między urzędy zarządzania usługi Intune i programu Configuration Manager. 

### <a name="cmdlet-switch-mdmdeviceauthority"></a>Polecenia cmdlet *MdmDeviceAuthority przełącznika*

#### <a name="synopsis"></a>SYNOPSIS
Polecenie cmdlet zmienia urząd zarządzania MDM urządzeń bez koligacji użytkownika (na przykład urządzeń rejestrowanych zbiorczo). Polecenie cmdlet zmienia między usługą Intune i programu Configuration Manager urzędów zarządzania dla określonego urządzenia na podstawie ich urzędy zarządzania Uruchom polecenie cmdlet.

### <a name="syntax"></a>SYNTAX
`Switch-MdmDeviceAuthority -DeviceIds <Guid[]> [-Credential <PSCredential>] [-Force] [-LogFilePath <string>] [-LoggingLevel {Off | Critical | Error | Warning | Information | Verbose | ActivityTracing | All}] [-Confirm] [-WhatIf] [<CommonParameters>]`


### <a name="parameters"></a>PARAMETRY
#### `-Credential <PSCredential>`
Obiekt poświadczeń PowerShell dla konta użytkownika usługi Azure AD, które jest używane podczas przełączania urzędy zarządzania urządzeniami. Użytkownik jest monitowany o poświadczenia, jeśli parametr nie jest określony. Rola katalog dla tego konta użytkownika powinna być **administratora globalnego** lub **administratorem ograniczonym** z rolą administratora **administratora usługi Intune**.

#### `-DeviceIds <Guid[]>`
Identyfikatory urządzeń MDM, które muszą mieć ich urząd zarządzania przełączaniem. Identyfikatory urządzeń są unikatowych identyfikatorów dla urządzeń wyświetlane w konsoli programu Configuration Manager.

#### `-Force [<SwitchParameter>]`
Określ parametr, aby wyłączyć wiersza powinno być kontynuowane.<br>
 
#### `-LogFilePath <string>`
Ścieżka do lokalizacji pliku dziennika.
 
#### `-LoggingLevel <SourceLevels>`
Dziennik poziom użytego w celu określenia typu dzienników konieczne są zapisywane w pliku dziennika.
 
Poniżej przedstawiono możliwe wartości LoggingLevel:

  - ActivityTracing
  - Wszystkie
  - Krytyczny
  - Błąd
  - Informacje
  - Wyłączanie
  - Pełny
  - Ostrzeżenie
 
#### `-Confirm [<SwitchParameter>]`
Monituje o potwierdzenie przed wykonaniem polecenia.
 
#### `-WhatIf [<SwitchParameter>]`
Opisuje rezultat wykonania polecenia bez jego rzeczywistego wykonania polecenia.
 
#### `<CommonParameters>`
To polecenie cmdlet obsługuje typowe parametry: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer, PipelineVariable i OutVariable. Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

### <a name="example-1"></a>Przykład 1

``` powershell
C:\PS>Switch-MdmDeviceAuthority -Credential $creds -DeviceIds $deviceIds
 
  DeviceId       : 62e6ea43-18f8-4278-bcd4-a4baed2c6d24
  Success        : True
  FailureReason  :
  NewAuthority   : Intune
  CompletionTime : 11/15/2017 8:00:11 PM
 
Description
 
-----------
 
Successfully switched the management authority of the device from Configuration Manager to Intune.
```

### <a name="remarks"></a>REMARKS
- Aby zapoznać się z przykładami, wpisz: `get-help Switch-MdmDeviceAuthority -examples`  
- Aby uzyskać więcej informacji wpisz: `get-help Switch-MdmDeviceAuthority -detailed`  
- Aby uzyskać informacje techniczne wpisz: `get-help Switch-MdmDeviceAuthority -full`  
- Aby uzyskać pomoc wpisz: `get-help Switch-MdmDeviceAuthority -online`   


## <a name="next-steps"></a>Następne kroki
Po migracji użytkowników i przetestować funkcje usługi Intune, należy rozważyć, czy wszystko jest gotowe do [zmienić urząd zarządzania urządzeniami Przenośnymi](migrate-change-mdm-authority.md) dzierżawy usługi Intune z programu Configuration Manager do usługi Intune. 