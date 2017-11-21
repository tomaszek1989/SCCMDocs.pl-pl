---
title: "Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender"
titleSuffix: Configuration Manager
description: "Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender."
ms.custom: na
ms.date: 11/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 
caps.latest.revision: "5"
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.openlocfilehash: db2508e5bbd1435fce432b6ef98d7968e68ea5ab
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="create-and-deploy-windows-defender-application-guard-policy----1351960---"></a>Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender<!-- 1351960 -->

Można tworzyć i wdrażać [Windows Defender aplikacji Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) zasady przy użyciu Menedżera konfiguracji programu endpoint protection. Te zasady chronią użytkowników, otwierając niezaufanych witryn sieci web w bezpiecznego kontenera izolowanym, który nie jest dostępny za pomocą innymi składnikami systemu operacyjnego.

## <a name="prerequisites"></a>Wymagania wstępne

Aby utworzyć i wdrożyć zasady zabezpieczenia programu Windows Defender aplikacji, należy użyć twórca spadek 10 Windows Update. Ponadto urządzenia systemu Windows 10, na których można wdrożyć zasady musi mieć zasady izolacji sieci. Aby uzyskać więcej informacji, zobacz [Omówienie programu Windows Defender aplikacji Guard](https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview). Ta funkcja działa tylko dla bieżącej kompilacji systemu Windows 10 wewnętrznych. Aby ją przetestować, musi być uruchomiona klientów ostatnie systemu Windows 10 niejawnego kompilacji.


## <a name="create-a-policy-and-to-browse-the-available-settings"></a>Tworzenie zasad oraz do przeglądania dostępnych ustawień:

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.
2. W **zasoby i zgodność** obszaru roboczego wybierz **omówienie** > **programu Endpoint Protection** > **Windows Defender aplikacji Guard**.
3. W **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji Guard zasady usługi Windows Defender**.
4. Przy użyciu [wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97) jako odwołanie, można wybrać i skonfigurować dostępne ustawienia.
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

6. Gdy skończysz, Zakończ pracę kreatora i wdróż zasady w co najmniej jedno urządzenie z systemem Windows 10.

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej o ochronie aplikacji systemu Windows Defender, zobacz [ten wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Ponadto, aby dowiedzieć się więcej o trybie autonomiczny Guard aplikacji dla systemu Windows Defender, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).
