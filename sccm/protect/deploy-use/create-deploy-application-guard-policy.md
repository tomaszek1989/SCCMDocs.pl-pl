---
title: Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender
titleSuffix: System Center Configuration Manager
description: Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ''
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: faa1a50b29fe4ba966812441243b81ee2d31b024
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender 
*Dotyczy: Program System Center Configuration Manager (Current Branch)*
<!-- 1351960 -->
Można tworzyć i wdrażać [Windows Defender aplikacji Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) zasady przy użyciu Menedżera konfiguracji programu endpoint protection. Te zasady chronią użytkowników, otwierając niezaufanych witryn sieci web w bezpiecznego kontenera izolowanym, który nie jest dostępny za pomocą innymi składnikami systemu operacyjnego.

## <a name="prerequisites"></a>Wymagania wstępne

Aby utworzyć i wdrożyć zasady zabezpieczenia programu Windows Defender aplikacji, należy użyć twórca spadek 10 Windows Update (1709). Ponadto urządzenia systemu Windows 10, na których można wdrożyć zasady musi mieć zasady izolacji sieci. Aby uzyskać więcej informacji, zobacz [Omówienie programu Windows Defender aplikacji Guard](https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview). 


## <a name="create-a-policy-and-to-browse-the-available-settings"></a>Tworzenie zasad oraz do przeglądania dostępnych ustawień:

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.
2. W **zasoby i zgodność** obszaru roboczego wybierz **omówienie** > **programu Endpoint Protection** > **Windows Defender aplikacji Guard**.
3. W **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji Guard zasady usługi Windows Defender**.
4. Przy użyciu [artykułu](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard) jako odwołanie, można wybrać i skonfigurować dostępne ustawienia. Menedżer konfiguracji umożliwia ustawienie niektórych ustawień zasad, zobacz [interakcji ustawienia hosta](#BKMK_HIS) i [zachowanie aplikacji](#BKMK_AppB).
5. Na **definicji sieci** Określ tożsamością firmową, a Definiowanie sieci granic sieci firmowej.

    > [!NOTE]
    > Komputery z systemem Windows 10 przechowywać tylko jedną listę izolacji sieci na komputerze klienckim. Można utworzyć dwa różne rodzaje list izolacji sieci i wdrożyć je do klienta:
    >
    >  - z systemu Windows Information Protection
    >  - z programu Windows Defender aplikacji Guard
    >
    > Jeśli obie zasady są wdrażane, te listy izolacji sieci muszą być zgodne. Jeśli wdrożono list, które nie pasują do tego samego klienta, wdrożenie zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [dokumentacji systemu Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).
    > 
    > 

6. Gdy skończysz, Zakończ pracę kreatora i wdrożyć zasady dla urządzeń z systemem Windows 10 1709 co najmniej jeden.

### <a name="bkmk_HIS"></a> Ustawienia interakcji hosta
Konfiguruje interakcje między urządzeniami hosta i kontener ochrona aplikacji. Przed 1802 wersji programu Configuration Manager, zarówno interakcji zachowanie i hosta aplikacji podlegały **ustawienia** kartę.

- **Schowek** — w obszarze Ustawienia przed 1802 Menedżera konfiguracji
    - Dozwolony typ zawartości
        - Tekst
        - Obrazy
- **Drukowanie:**
    - Włącz drukowania na XPS
    - Włączanie drukowania na PDF.
    - Włączanie drukowania do drukarek lokalnych
    - Włączanie drukowania do drukarek sieciowych
- **Grafika:** (począwszy od programu Configuration Manager w wersji 1802)
    - Dostęp do procesora wirtualnego grafiki
- **Pliki:** (począwszy od programu Configuration Manager w wersji 1802)
    - Zapisz pobranych plików na potrzeby hostowania

### <a name="bkmk_ABS"></a> Ustawienia zachowania aplikacji
Określa zachowanie aplikacji wewnątrz sesji ochrona aplikacji. Przed 1802 wersji programu Configuration Manager, zarówno interakcji zachowanie i hosta aplikacji podlegały **ustawienia** kartę.

- **Zawartość:**
   - Lokacje przedsiębiorstwa mogą ładować zawartości innych niż przedsiębiorstwa, takich jak plug-in innych firm.
- **Inne:**
    - Zachowaj dane przeglądarki użytkownika wygenerowany
    - Zdarzenia inspekcji zabezpieczeń w sesji guard izolowanych aplikacji



## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o Guard aplikacji programu Windows Defender: [Omówienie zabezpieczenia systemu Windows Defender aplikacji](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview).
[Windows Defender aplikacji Guard — często zadawane pytania](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/faq-wd-app-guard).
