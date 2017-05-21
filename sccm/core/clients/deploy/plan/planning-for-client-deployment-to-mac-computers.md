---
title: "Planowanie wdrożenia klienta na komputerach Mac | Dokumentacja firmy Microsoft"
description: "Planowanie wdrożenia klienta na komputerach Mac w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 75bddb41d4d1cf209fa7595c52b5a6aa831ba3dd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>Planowanie wdrożenia klientów na komputerach Mac w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Klient programu Configuration Manager można zainstalować na komputerach Mac z systemem operacyjnym Mac OS X i korzystać z następujących funkcji zarządzania:  

-   **Spis sprzętu**  

     Można użyć spisu sprzętu programu Configuration Manager do zbierania informacji o sprzęcie i aplikacje zainstalowane na komputerach Mac. Informacje te można następnie wyświetlić w Eksploratorze zasobów w konsoli programu Configuration Manager i pozwala tworzyć kolekcje, kwerendy i raporty. Aby uzyskać więcej informacji, zobacz [sposobu używania Eksploratora zasobów do wyświetlenia spisu sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

     Menedżer konfiguracji zbiera następujące informacje o sprzęcie w komputerach Mac:  

    -   Procesor  

    -   System komputerowy  

    -   Stacja dysków  

    -   Partycja dysku  

    -   Karta sieciowa  

    -   System operacyjny  

    -   Usługi  

    -   Proces  

    -   Zainstalowane oprogramowanie  

    -   Systemowy produkt komputerowy  

    -   Kontroler USB  

    -   Urządzenie USB  

    -   Stacja CD-ROM  

    -   Kontroler wideo  

    -   Monitor komputera stacjonarnego  

    -   Bateria przenośna  

    -   Pamięć fizyczna  

    -   Drukarki  

    > [!IMPORTANT]  
    >  Nie można rozszerzyć informacje o sprzęcie zebranej z komputerów Mac w trakcie spisu sprzętu.  

-   **Ustawienia zgodności**  

     Aby wyświetlić zgodności i korygować ustawienia preferencji (.plist) systemu Mac OS X, można użyć ustawień zgodności programu Configuration Manager. Można na przykład wymusić ustawienia strony głównej w przeglądarce sieci web Safari lub upewnij się, że jest włączona Zapora sieciowa firmy Apple. Można również korzystać ze skryptów powłoki pozwala monitorować i korygować ustawienia w systemie MAC OS X.  

-   **Zarządzanie aplikacjami**  

     Oprogramowanie można wdrożyć na komputerach Mac programu Configuration Manager. Na komputerach Mac można wdrażać oprogramowanie w następujących formatach:  

    -   Obraz dysku Apple (. DMG)  

    -   Plik meta pakietu (. MPKG)  

    -   Mac OS X Instalator pakietu (. FULLY PACKAGED)  

    -   Aplikacja systemu Mac OS X (. APLIKACJA)  

 Po zainstalowaniu klienta programu Configuration Manager na komputerach Mac, nie można używać następujących funkcji zarządzania, które są obsługiwane przez klienta programu Configuration Manager na komputerach z systemem Windows:  

-   Wypychana instalacja klienta  

-   Wdrożenie systemu operacyjnego  

-   Aktualizacje oprogramowania  

    > [!NOTE]  
    >  Aby wdrażać wymagane aktualizacje oprogramowania systemu Mac OS X na komputerach Mac, można użyć zarządzania aplikacjami programu Configuration Manager. Ponadto można użyć ustawień zgodności, aby upewnić się, że komputery mają wymagane aktualizacje oprogramowania.  

-   Okna obsługi  

-   Zdalne sterowanie  

-   Zarządzanie energią  

-   Sprawdzanie i korygowanie stanu klienta przez klienta  

 Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania klienta programu Configuration Manager Mac, zobacz [sposobu wdrażania klientów w programie System Center Configuration Manager Mac](../../../../core/clients/deploy/deploy-clients-to-macs.md).

