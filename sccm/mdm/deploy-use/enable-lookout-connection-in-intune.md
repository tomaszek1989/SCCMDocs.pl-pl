---
title: Włącz Lookout MTD w usłudze Intune
titleSuffix: Configuration Manager
description: Włącz Lookout przenośnych ochrona przed zagrożeniami (MTD) w portalu Microsoft Intune.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0de1859d97eed804eced58028d6459ab682f9b3f
ms.sourcegitcommit: 9cff0702c2cc0f214173b47ec241f7e5a40f84e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745439"
---
# <a name="enable-lookout-mtd-connection-in-the-intune-admin-console"></a>Włącz połączenie Lookout MTD w konsoli administracyjnej usługi Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule przedstawiono sposób włączania połączenia Lookout przenośnych zagrożeń obrony (MTD) w programie Microsoft Intune. Powinna już skonfigurowano łącznik usługi Intune w konsoli Lookout przed wykonaniem tego kroku. Jeśli nie zostało to jeszcze zrobione, wykonaj kroki opisane w [konfigurowania subskrypcji z przed zagrożeniami przenośnych Lookout](set-up-your-subscription-with-lookout.md).



## <a name="enable-the-lookout-mtd-connector"></a>Włącz łącznik Lookout od początku miesiąca

1. Przejdź do [portalu Azure](https://portal.azure.com)i zaloguj się przy użyciu poświadczeń usługi Intune. Po pomyślnie logowanie, zobacz **pulpitu nawigacyjnego Azure**.  

2. Na **pulpitu nawigacyjnego Azure**, wybierz **wszystkie usługi** z menu po lewej stronie, następnie wpisz **Intune** w filtrze pola tekstowego.  

3. Wybierz **Intune**; **nawigacyjnym usługi Intune** otwiera.  

4. Na **nawigacyjnym usługi Intune**, wybierz **zgodności urządzeń**, a następnie wybierz **przed zagrożeniami Mobile** w obszarze **Instalator** sekcji.  

5. Na **przed zagrożeniami Mobile** okienku wybierz **Dodaj**.  

6. Wybierz **Lookout** jako **przed zagrożeniami Mobile łącznik do instalacji** z listy rozwijanej.  

7. Włącz opcje Przełącz zgodnie z wymaganiami organizacji.  



## <a name="mtd-toggle-options"></a>Opcje Przełącz od początku miesiąca

Można określić, jakie opcje Przełącz MTD należy włączyć zgodnie z wymaganiami organizacji. Poniżej przedstawiono więcej informacji:

- **Połącz z systemem Android 4.1 + urządzeń do Lookout MTD pracy**: Po włączeniu tej opcji może mieć Android 4.1 + urządzenia podlegające zagrożenie dla bezpieczeństwa z powrotem do usługi Intune.  
    - **Oznacz jako niezgodne w przypadku nieodebrania żadnych danych**: Jeśli usługa Intune nie odbiera danych dotyczących urządzeń na tej platformie z Lookout, należy wziąć pod uwagę urządzenia niezgodne.  

- **Urządzenia z systemem iOS 8.0 i nowsze Połącz z usługą Lookout dla pracy MTD**: Po włączeniu tej opcji może mieć Android 4.1 + urządzenia podlegające zagrożenie dla bezpieczeństwa z powrotem do usługi Intune.
    - **Oznacz jako niezgodne w przypadku nieodebrania żadnych danych**: Jeśli usługa Intune nie odbiera danych dotyczących urządzeń na tej platformie z Lookout, należy wziąć pod uwagę urządzenia niezgodne.  

> [!TIP]  
> Widać **stan połączenia** i **ostatniej synchronizacji** czasu między usługą Intune a Lookout z okienka Mobile przed zagrożeniami.



## <a name="next-steps"></a>Następne kroki
Na tym kończy się Konfigurowanie integracji Lookout i Intune. Następnych kilku krokach implementacji tego rozwiązania dotyczą wdrażania [szukać aplikacji służbowych](configure-and-deploy-lookout-for-work-apps.md) i konfigurując [zgodności](enable-device-threat-protection-rule-compliance-policy.md) zasad.

>[!IMPORTANT]
> Możesz *musi* skonfigurować aplikację Lookout for Work aplikacji przed utworzeniem reguły zasad zgodności i skonfigurowaniem dostępu warunkowego. Dzięki temu, że dana aplikacja jest gotowa i dostępna dla użytkowników końcowych zainstalować, zanim uzyskają dostęp do poczty e-mail ani innych zasobów firmy.

[Skonfiguruj aplikację Lookout pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md)
