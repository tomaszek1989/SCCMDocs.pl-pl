---
title: "Planowanie wdrażania klientów na komputerach Mac | Dokumentacja firmy Microsoft"
description: "Planowanie wdrożenia klientów na komputerach Mac w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c3108813a04cf464bfc05961113bbdffb9a81419
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>Planowanie wdrożenia klientów na komputerach Mac w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Klient programu Configuration Manager można zainstalować na komputerach Mac z zainstalowanym systemem operacyjnym Mac OS X i korzystać z następujących funkcji zarządzania:  

-   **Spis sprzętu**  

     Można użyć spisu sprzętu programu Configuration Manager do zbierania informacji o sprzęcie i aplikacje zainstalowane na komputerach Mac. Te informacje można następnie wyświetlić w Eksploratorze zasobów w konsoli programu Configuration Manager i pozwala utworzyć kolekcje, kwerendy i raporty. Aby uzyskać więcej informacji, zobacz [jak używać Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

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

    -   Urządzenia USB  

    -   Stacja CD-ROM  

    -   Kontroler wideo  

    -   Monitor komputera stacjonarnego  

    -   Bateria przenośna  

    -   Pamięć fizyczna  

    -   Drukarki  

    > [!IMPORTANT]  
    >  Nie można rozszerzyć informacje o sprzęcie zbierane z komputerów Mac podczas tworzenia spisu sprzętu.  

-   **Ustawienia zgodności**  

     Aby wyświetlić zgodność i korygować ustawienia preferencji (.plist) systemu Mac OS X, można użyć ustawień zgodności programu Configuration Manager. Można na przykład wymusić ustawienia strony głównej w przeglądarce sieci web Safari lub upewnij się, że Zapora jest włączona firmy Apple. Aby monitorować i korygować ustawienia w systemie MAC OS X umożliwia także skryptów powłoki.  

-   **Zarządzanie aplikacjami**  

     Menedżer konfiguracji można wdrażać oprogramowanie na komputerach Mac. Na komputerach Mac można wdrażać oprogramowanie w następujących formatach:  

    -   Obraz dysku Apple (. DMG)  

    -   Plik meta pakietu (. MPKG)  

    -   Mac OS X Instalatora pakietu (. PKG)  

    -   Aplikacja systemu Mac OS X (. APLIKACJA)  

 Po zainstalowaniu klienta programu Configuration Manager na komputerach Mac, nie można użyć następujących funkcji zarządzania, które są obsługiwane przez klienta programu Configuration Manager na komputerach z systemem Windows:  

-   Wypychana instalacja klienta  

-   Wdrożenie systemu operacyjnego  

-   Aktualizacje oprogramowania  

    > [!NOTE]  
    >  Zarządzanie aplikacjami w programie Configuration Manager służy do wdrażania na komputerach Mac wymagane aktualizacje oprogramowania systemu Mac OS X. Ponadto można użyć ustawień zgodności, aby upewnić się, że komputery mają wymagane aktualizacje oprogramowania.  

-   Okna obsługi  

-   Zdalne sterowanie  

-   Zarządzanie energią  

-   Sprawdzanie i korygowanie stanu klienta przez klienta  

 Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania klienta programu Configuration Manager Mac, zobacz [jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md).
