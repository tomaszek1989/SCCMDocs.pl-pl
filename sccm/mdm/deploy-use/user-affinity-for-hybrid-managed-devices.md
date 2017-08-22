---
title: "Koligacja użytkownika dla hybrydowych zarządzanych urządzeń w programie Configuration Manager | Dokumentacja firmy Microsoft"
description: "Konfiguruj koligację użytkownika dla zarządzanych urządzeń w programie Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5d520a7-e9e5-40ee-91f9-f2684214beb6
caps.latest.revision: "6"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: d039792a88b9e7704f37718a88f841dd9216d1b1
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="user-affinity-for-hybrid-managed-devices-in-configuration-manager"></a>Koligacja użytkownika dla hybrydowych zarządzanych urządzeń w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas konfigurowania profilów dla urządzeń należących do firmy, administrator może określić, czy urządzenia zarządzanego mogą mieć *koligacji użytkownika* identyfikujący określonego użytkownika z urządzeniem.  

##  <a name="BKMK_iOSCP"></a>Zarządzanych urządzeń z koligacją użytkownika  
 Na urządzeniach, na których skonfigurowano **user affinity** , można instalować i uruchamiać aplikację Portal firmy w celu pobierania aplikacji i zarządzania urządzeniami. Gdy użytkownicy otrzymają urządzenia, ich należy wykonać kilka dodatkowych czynności w celu ukończenia działania Asystenta ustawień i zainstalowania aplikacji Portal firmy.  

#### <a name="how-to-enroll-ios-devices-with-user-affinity"></a>Jak rejestrować urządzenia z systemem iOS z koligacją użytkownika  

1.  Gdy użytkownicy włączają najpierw nowe urządzenia, są monitowani o ukończenie działania Asystenta ustawień. Profil rejestracji można określić monit o podanie poświadczeń podczas instalacji. Użytkownicy muszą korzystać z poświadczeń (tj. unikatową nazwę osobistych lub nazwy UPN) skojarzonych z ich subskrypcją w usłudze Intune.  

2.  Podczas instalacji użytkownicy mogą również monit podanie identyfikatora Apple ID. Należy podać identyfikator Apple ID przed urządzenia mogą zainstalować aplikację Portal firmy. Użytkownicy mogą podać identyfikator Apple ID, po zakończeniu instalacji z systemu iOS **ustawienia** menu.  

3.  Po ukończeniu instalacji urządzenie iOS musi zainstalować aplikację Portal firmy ze sklepu z aplikacjami, na przykład [aplikacji Portal firmy](https://itunes.apple.com/us/app/id719171358).  

4.  Użytkownik może teraz zalogować się do portalu firmy nazwy UPN używanej podczas konfigurowania urządzenia.  

5.  Po zalogowaniu użytkownik jest monitowany o zarejestrowanie swoich urządzeń. Pierwszym krokiem jest **zidentyfikowanie urządzenia**. Aplikacja wyświetla listę urządzeń z systemem iOS, które są zarejestrowane przez firmę i przypisane do konta użytkownika końcowego w usłudze Intune. Wybierz odpowiednie urządzenie.  

     Jeśli to urządzenie nie jest już zarejestrowane przez firmę, wybierz pozycję "nowe urządzenie" Aby kontynuować standardową procedurę rejestracji.  

6.  Na następnym ekranie użytkownik musi potwierdzić numer seryjny nowego urządzenia. Użytkownik może nacisnąć link „potwierdź numer seryjny”, aby uruchomić aplikację Ustawienia w celu zweryfikowania numeru seryjnego. Użytkownik musi następnie wprowadzić 4 ostatnie znaki numeru seryjnego w aplikacji Portal firmy.  

     Ten krok umożliwia zweryfikowanie, że urządzenie zostało zarejestrowane przez firmę w usłudze Intune. Jeśli numer seryjny urządzenia nie jest zgodny, oznacza to, że wybrano niewłaściwe urządzenie. Wróć do poprzedniego ekranu i wybierz inne urządzenie.  

7.  Po zweryfikowaniu numeru seryjnego Aplikacja Portal firmy wykonuje przekierowanie do witryny sieci Web Portal firmy w celu sfinalizowania rejestracji, a następnie monituje użytkownika o powrót do aplikacji.  

8.  Rejestracja jest teraz ukończona. Możesz teraz używać tego urządzenia z pełnym zestawem funkcji.  

##  <a name="BKMK_noUA"></a>Zarządzanych urządzeń bez koligacji użytkownika  
 Na urządzeniach, na których skonfigurowano **no user affinity** nie obsługują Portalu firmy i nie należy na nich instalować aplikacji. Portal firmy jest przeznaczony dla użytkowników, którzy mają poświadczenia firmowe i wymagają dostępu do spersonalizowanych zasobów firmowych (np. poczta e-mail). Urządzenia zarejestrowane **bez koligacji użytkownika** nie powinny być dedykowane do logowania dla określonego użytkownika. Urządzenia zarejestrowane bez koligacji użytkownika są zazwyczaj stosowane w kioskach lub punktach sprzedaży (POS) albo jako narzędzia udostępnione. Jeśli koligacja użytkownika jest wymagana, upewnij się, że dla profilu rejestracji urządzenia wybrano opcję **Koligacja użytkownika** przed zarejestrowaniem urządzenia. Aby zmienić stan koligacji urządzenia, należy wycofać i ponownie zarejestrować urządzenie.
