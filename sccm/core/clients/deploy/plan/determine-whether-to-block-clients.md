---
title: "Blokowanie klientów | Dokumentacja firmy Microsoft"
description: "Zablokuj dostęp klienta do zabezpieczenia systemu za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3e323ab90ec4cc274581e19065fd7d81c0c11c35
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-block-clients-in-system-center-configuration-manager"></a>Określanie, czy blokować klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Jeśli komputer kliencki lub klienckie urządzenie przenośne nie jest już zaufany, można zablokować klienta w konsoli programu System Center 2012 Configuration Manager. Zablokowani klienci są odrzucani przez infrastrukturę programu Configuration Manager, tak aby nie mogli komunikować się z systemami lokacji w celu pobrania zasad, wysyłania danych zapasów lub wysyłać komunikaty o stanie.  

 Klienta należy blokować i odblokowywać z przypisanej do niego lokacji, a nie z lokacji dodatkowej lub centralnej lokacji administracyjnej.  

> [!IMPORTANT]  
>  Mimo że blokowanie w programie Configuration Manager może ułatwić zabezpieczenie lokacji programu Configuration Manager, nie należy polegać na tej funkcji do ochrony lokacji przed niezaufanymi komputerami lub urządzeniami przenośnymi, czy zezwolić klientom na komunikację z systemami lokacji przy użyciu protokołu HTTP, ponieważ zablokowany klient mógł ponownie dołączyć lokację z nowego samopodpisany certyfikat i identyfikatora sprzętu. Zamiast tego należy użyć funkcji blokowania w celu zablokowania utraconych nośników rozruchowych lub takich, w przypadku których doszło do naruszenia bezpieczeństwa, używanych do wdrożenia systemów operacyjnych, jeżeli systemy lokacji akceptują połączenia klienckie HTTPS.  

 Klientów, którzy uzyskują dostęp do lokacji, używając certyfikatu proxy niezależnego dostawcy oprogramowania nie można zablokować. Aby uzyskać więcej informacji o certyfikacie Proxy niezależnego dostawcy oprogramowania Zobacz System Center Configuration Manager Software Development Kit (SDK).  

 Jeżeli używane systemy lokacji akceptują połączenia klienckie HTTPS, a infrastruktura kluczy publicznych (PKI) obsługuje listę odwołania certyfikatów (CRL), odwołanie certyfikatów powinno być zawsze główną linią obrony przed certyfikatami, które mogą mieć złamane zabezpieczenia. Blokowanie klientów w programie Configuration Manager stanowi drugą linię obrony w celu ochrony hierarchii.  

##  <a name="BKMK_Block_vs_CRL"></a> Zagadnienia dotyczące blokowania klientów  

-   Ta opcja jest dostępna tylko dla połączeń klienckich HTTP i HTTPS, ale zapewnia ograniczone bezpieczeństwo, gdy klienci łączą się z systemami lokacji za pomocą protokołu HTTP.  

-   Użytkownicy z uprawnieniami administracyjnymi w programie Configuration Manager ma uprawnienia do blokowania klienta i akcja jest wykonywana w konsoli programu Configuration Manager.  

-   Komunikacja z klientem jest odrzucana tylko z hierarchii programu Configuration Manager.  

    > [!NOTE]  
    >  Tego samego klienta można zarejestrować z innej hierarchii programu Configuration Manager.  

-   Klient jest natychmiast blokowany z lokacji programu Configuration Manager.  

-   Ułatwia zabezpieczenie systemów lokacji przed komputerami i urządzeniami przenośnymi, które mogą mieć złamane zabezpieczenia.  

## <a name="considerations-for-using-certificate-revocation"></a>Zagadnienia dotyczące korzystania z odwołań certyfikatów  

-   Ta opcja jest dostępna dla połączeń klienckich HTTPS w systemie Windows, jeśli infrastruktura klucza publicznego obsługuje listę odwołania certyfikatów (CRL, certificate revocation list).  

     Klienci na komputery Mac zawsze wykonują sprawdzanie listy CRL i nie można wyłączyć tej funkcji.  

     Mimo że klienci urządzeń przenośnych nie używają list odwołania certyfikatów do sprawdzania certyfikatów systemów lokacji, ich certyfikaty można odwołane i sprawdzone przez program Configuration Manager.  

-   Administratorzy infrastruktury klucza publicznego mają uprawnienia do odwołania certyfikatu, a czynność tę wykonują spoza konsoli programu Configuration Manager.  

-   Komunikację z klientem można odrzucić z dowolnego komputera lub urządzenia przenośnego, które wymaga tego certyfikatu klienta.  

-   Istnieje prawdopodobieństwo wystąpienia opóźnienia między odwołaniem certyfikatu a pobraniem przez systemy lokacji zmodyfikowanej listy odwołania certyfikatów (CRL).  

-   W przypadku wielu wdrożeń infrastruktury PKI to opóźnienie może wynosić jeden dzień lub dłużej. Przykładowo w Usługach certyfikatów w usłudze Active Directory domyślny okres wygaśnięcia wynosi tydzień w przypadku pełnej listy CRL i jeden dzień w przypadku różnicowej listy CRL.  

-   Ułatwia zabezpieczenie systemów lokacji i klientów przed komputerami i urządzeniami przenośnymi, które mogą mieć złamane zabezpieczenia.  

    > [!NOTE]  
    >  Systemy lokacji z uruchomionymi usługami IIS można dodatkowo zabezpieczyć przed nieznanymi klientami, konfigurując listę zaufania certyfikatów (CTL) w usługach IIS.  

