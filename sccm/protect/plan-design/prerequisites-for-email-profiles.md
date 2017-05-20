---
title: "Wymagania wstępne dotyczące profili poczty e-mail | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o profili poczty e-mail w programie System Center Configuration Manager i ich zależności zewnętrzne i w obrębie produktu."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 451317db1d7aab888c03d1a099b9ce25311e06d0
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="email-profile-prerequisites"></a>Wymagania wstępne dotyczące profilu poczty e-mail

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Profile poczty e-mail w programie System Center Configuration Manager mają zarówno zależności zewnętrzne i w obrębie produktu.  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Do zarządzania profilami poczty e-mail są wymagane określone uprawnienia zabezpieczeń.|Do zarządzania ustawieniami dostępu do zasobów firmy, takich jak profile poczty e-mail, są wymagane następujące uprawnienia zabezpieczeń:<br /><br /> — Do wyświetlania i zarządzania nimi alerty i raporty dla profili poczty e-mail: **Tworzenie**, **usunąć**, **Modyfikuj**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** uprawnienia dla **alerty** obiektu.<br /><br /> — Aby utworzyć i zarządzać profilami certyfikatów: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu** i **Uruchom raport** uprawnienia dla **profilu certyfikatu** obiektu.<br /><br /> -Aby zarządzać wdrożeniami profili poczty e-mail: **Wdrażanie zasad konfiguracji**, **Modyfikuj Alert stanu klienta**, **odczytu**, i **Odczytaj zasób** uprawnienia dla **kolekcji** obiektu.<br /><br /> -Aby zarządzać wszystkimi zasadami konfiguracji: **Tworzenie**, **usunąć**, **Modyfikuj**, **odczytu** i **Ustawianie zakresu zabezpieczeń** uprawnienia dla **zasady konfiguracji** obiektu.<br /><br /> -Aby uruchamiać kwerendy dotyczące profili poczty e-mail: **Odczyt** uprawnienia dla **kwerendy** obiektu.<br /><br /> — Aby wyświetlić informacje o profilach poczty e-mail w konsoli programu System Center Configuration Manager: **Odczyt** uprawnienia dla **witryny** obiektu.<br /><br /> — Aby wyświetlić komunikaty o stanie dla profili poczty e-mail: **Odczyt** uprawnienia dla **komunikatów o stanie** obiektu.<br /><br /> — Aby utworzyć i zarządzać profilami poczty e-mail: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** uprawnienia dla **profil udostępniania komunikacji** obiektu.<br /><br /> **Menedżer dostępu do zasobów firmy** roli zabezpieczeń obejmuje uprawnienia wymagane do zarządzania profilami poczty e-mail w programie System Center Configuration Manager. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../core/plan-design/security/configure-security.md).|  
|Atrybut mail w usłudze Active Directory|Jeśli chcesz wygenerować adres e-mail użytkownika w profilu poczty e-mail przy użyciu podstawowego adresu SMTP użytkownika, odnajdywania użytkownika programu System Center Configuration Manager musi być skonfigurowana do wykrywania **korespondencji** atrybutu z usługi Active Directory (jest to konfiguracja domyślna).|  

## <a name="external-dependencies"></a>Zależności zewnętrzne  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Atrybut mail w usłudze Active Directory|Jeśli chcesz wygenerować adres e-mail użytkownika w profilu poczty e-mail przy użyciu podstawowego adresu SMTP użytkownika, adres ten musi istnieć w **poczty** w usłudze Active Directory.<br /><br /> Więcej informacji znajduje się w dokumentacji systemu Windows Server.|

