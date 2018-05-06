---
title: Wymagania wstępne dotyczące profilów poczty e-mail
titleSuffix: Configuration Manager
description: Więcej informacji na temat profilów poczty e-mail w programie System Center Configuration Manager oraz ich zależności zewnętrzne i w obrębie produktu.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 58e1f4b56c99cf29c112773b2a82c70695e58744
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="email-profile-prerequisites"></a>Wymagania wstępne dotyczące profilu poczty e-mail

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Profile poczty e-mail w programie System Center Configuration Manager mają zarówno zależności zewnętrzne i w obrębie produktu.  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Do zarządzania profilami poczty e-mail są wymagane określone uprawnienia zabezpieczeń.|Do zarządzania ustawieniami dostępu do zasobów firmy, takich jak profile poczty e-mail, są wymagane następujące uprawnienia zabezpieczeń:<br /><br /> — Do wyświetlania i zarządzania nimi, alerty i raporty dla profili poczty e-mail: **Utwórz**, **usunąć**, **zmodyfikować**, **Modyfikuj raport**, **odczytu**, i **Uruchom raport** uprawnienia dla **alerty** obiektu.<br /><br /> — Aby utworzyć i zarządzać profilami certyfikatów: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu** i **Uruchom raport** uprawnienia dla **profil certyfikatu** obiektu.<br /><br /> -Aby zarządzać wdrożeniami profili poczty e-mail: **Wdrażanie zasad konfiguracji**, **modyfikowanie alertu stanu klienta**, **odczytu**, i **Odczytaj zasób** uprawnienia **kolekcji** obiektu.<br /><br /> -Aby zarządzać wszystkimi zasadami konfiguracji: **Utwórz**, **usunąć**, **Modyfikuj**, **odczytu** i **Ustawianie zakresu zabezpieczeń** uprawnienia  **Zasady konfiguracji** obiektu.<br /><br /> -Aby uruchamiać kwerendy dotyczące profili poczty e-mail: **Odczyt** uprawnienie **zapytania** obiektu.<br /><br /> — Aby wyświetlić informacje o profilach poczty e-mail w konsoli programu System Center Configuration Manager: **Odczyt** uprawnienie **lokacji** obiektu.<br /><br /> — Aby wyświetlić komunikaty o stanie dla profili poczty e-mail: **Odczyt** uprawnienie **komunikaty o stanie** obiektu.<br /><br /> — Aby utworzyć i zarządzać profilami poczty e-mail: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** uprawnienia **profil udostępniania komunikacji**obiektu.<br /><br /> **Menedżer dostępu do zasobów firmy** te uprawnienia, które są wymagane do zarządzania profilami poczty e-mail w programie System Center Configuration Manager obejmuje rola zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../core/plan-design/security/configure-security.md).|  
|Atrybut mail w usłudze Active Directory|Jeśli chcesz wygenerować adres e-mail użytkownika w profilu poczty e-mail przy użyciu podstawowego adresu SMTP użytkownika, odnajdowanie użytkowników usługi System Center Configuration Manager musi być skonfigurowana do wykrywania **poczty** atrybutów z usługi Active Directory (jest to konfiguracja domyślna).|  

## <a name="external-dependencies"></a>Zależności zewnętrzne  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Atrybut mail w usłudze Active Directory|Jeśli chcesz wygenerować adres e-mail użytkownika w profilu poczty e-mail przy użyciu podstawowego adresu SMTP użytkownika, adres ten musi istnieć w **poczty** atrybutu w usłudze Active Directory.<br /><br /> Więcej informacji znajduje się w dokumentacji systemu Windows Server.|
