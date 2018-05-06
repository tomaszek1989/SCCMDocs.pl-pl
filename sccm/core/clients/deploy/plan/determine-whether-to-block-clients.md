---
title: Blokowanie klientów
titleSuffix: Configuration Manager
description: Zablokuj dostęp klient systemu zabezpieczeń za pomocą programu System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4371e9ede643d794058520cf001f30f01b47fe94
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="determine-whether-to-block-clients-in-system-center-configuration-manager"></a>Określanie, czy blokować klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli komputer kliencki lub klienckie urządzenie przenośne nie jest już zaufane, można zablokować klienta w konsoli programu System Center 2012 Configuration Manager. Zablokowani klienci są odrzucani przez infrastrukturę programu Configuration Manager, tak aby nie mogli komunikować się z systemami lokacji w celu pobrania zasad, wysyłania danych zapasów lub wysłać lub komunikatów o stanie.  

 Klienta należy blokować i odblokowywać z przypisanej do niego lokacji, a nie z lokacji dodatkowej lub centralnej lokacji administracyjnej.  

> [!IMPORTANT]  
>  Mimo że blokowanie w programie Configuration Manager może pomóc zabezpieczyć lokacji programu Configuration Manager, nie należy polegać na tej funkcji do ochrony lokacji przed niezaufanymi komputerami lub urządzeniami przenośnymi, jeśli Zezwalaj klientom na komunikację z systemami lokacji przy użyciu protokołu HTTP, ponieważ zablokowany klient może ponownie połączyć się witryny o nowe samopodpisany certyfikat i identyfikatora sprzętu. Zamiast tego należy użyć funkcji blokowania w celu zablokowania utraconych nośników rozruchowych lub takich, w przypadku których doszło do naruszenia bezpieczeństwa, używanych do wdrożenia systemów operacyjnych, jeżeli systemy lokacji akceptują połączenia klienckie HTTPS.  

 Klientów, którzy uzyskują dostęp do lokacji, używając certyfikatu proxy niezależnego dostawcy oprogramowania nie można zablokować. Aby uzyskać więcej informacji o certyfikacie Proxy niezależnego dostawcy oprogramowania Zobacz System Center Configuration Manager Software Development Kit (SDK).  

 Jeżeli używane systemy lokacji akceptują połączenia klienckie HTTPS, a infrastruktura kluczy publicznych (PKI) obsługuje listę odwołania certyfikatów (CRL), odwołanie certyfikatów powinno być zawsze główną linią obrony przed certyfikatami, które mogą mieć złamane zabezpieczenia. Blokowanie klientów w programie Configuration Manager stanowi drugą linię obrony w celu ochrony hierarchii.  

##  <a name="BKMK_Block_vs_CRL"></a> Zagadnienia dotyczące blokowania klientów  

-   Ta opcja jest dostępna tylko dla połączeń klienckich HTTP i HTTPS, ale zapewnia ograniczone bezpieczeństwo, gdy klienci łączą się z systemami lokacji za pomocą protokołu HTTP.  

-   Użytkownicy administracyjni programu Configuration Manager mają uprawnienia do blokowania klienta, a czynność tę wykonują w konsoli programu Configuration Manager.  

-   Komunikacja z klientem jest odrzucana tylko z hierarchii programu Configuration Manager.  

    > [!NOTE]  
    >  Tego samego klienta można zarejestrować z innej hierarchii programu Configuration Manager.  

-   Klient jest natychmiast blokowany lokacji programu Configuration Manager.  

-   Ułatwia zabezpieczenie systemów lokacji przed komputerami i urządzeniami przenośnymi, które mogą mieć złamane zabezpieczenia.  

## <a name="considerations-for-using-certificate-revocation"></a>Zagadnienia dotyczące korzystania z odwołań certyfikatów  

-   Ta opcja jest dostępna dla połączeń klienckich HTTPS w systemie Windows, jeśli infrastruktura klucza publicznego obsługuje listę odwołania certyfikatów (CRL, certificate revocation list).  

     Klienci na komputery Mac zawsze wykonują sprawdzanie listy CRL i nie można wyłączyć tej funkcji.  

     Mimo że klienci urządzeń przenośnych nie używają list odwołania certyfikatów do sprawdzania certyfikatów systemów lokacji, ich certyfikaty można odwołane i sprawdzone przez program Configuration Manager.  

-   Administratorzy infrastruktury klucza publicznego mają uprawnienia do odwoływania certyfikatów, a czynność tę wykonują spoza konsoli programu Configuration Manager.  

-   Komunikację z klientem można odrzucić z dowolnego komputera lub urządzenia przenośnego, które wymaga tego certyfikatu klienta.  

-   Istnieje prawdopodobieństwo wystąpienia opóźnienia między odwołaniem certyfikatu a pobraniem przez systemy lokacji zmodyfikowanej listy odwołania certyfikatów (CRL).  

-   W przypadku wielu wdrożeń infrastruktury PKI to opóźnienie może wynosić jeden dzień lub dłużej. Przykładowo w Usługach certyfikatów w usłudze Active Directory domyślny okres wygaśnięcia wynosi tydzień w przypadku pełnej listy CRL i jeden dzień w przypadku różnicowej listy CRL.  

-   Ułatwia zabezpieczenie systemów lokacji i klientów przed komputerami i urządzeniami przenośnymi, które mogą mieć złamane zabezpieczenia.  

    > [!NOTE]  
    >  Systemy lokacji z uruchomionymi usługami IIS można dodatkowo zabezpieczyć przed nieznanymi klientami, konfigurując listę zaufania certyfikatów (CTL) w usługach IIS.  
