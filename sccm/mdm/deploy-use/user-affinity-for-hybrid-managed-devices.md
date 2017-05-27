---
title: "Koligacji użytkownika dla hybrydowego zarządzanych urządzeń w programie Configuration Manager | Dokumentacja firmy Microsoft"
description: "Konfiguruj koligację użytkownika dla zarządzanych urządzeń w programie Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5d520a7-e9e5-40ee-91f9-f2684214beb6
caps.latest.revision: 6
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: d039792a88b9e7704f37718a88f841dd9216d1b1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="user-affinity-for-hybrid-managed-devices-in-configuration-manager"></a>Koligacji użytkownika dla hybrydowego zarządzanych urządzeń w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podczas konfigurowania profilów dla firmowych urządzeń, administrator może określić, czy zarządzanych urządzeń może mieć *koligacji użytkownika* identyfikujący określonego użytkownika z urządzeniem.  

##  <a name="BKMK_iOSCP"></a>Zarządzane urządzenia z koligacji użytkownika  
 Na urządzeniach, na których skonfigurowano **user affinity** , można instalować i uruchamiać aplikację Portal firmy w celu pobierania aplikacji i zarządzania urządzeniami. Użytkownicy otrzymują raz swoje urządzenia, muszą one wykonać kilka dodatkowe kroki w celu ukończenia Asystenta ustawień i zainstalowanie aplikacji Portal firmy.  

#### <a name="how-to-enroll-ios-devices-with-user-affinity"></a>Jak zarejestrować urządzenia iOS dzięki koligacji użytkownika  

1.  Gdy użytkownicy najpierw włączyć ich nowych urządzeń, są monitowani o ukończenia Asystenta. Profil rejestracji można określić monit o podanie poświadczeń podczas instalacji. Użytkownicy muszą używać poświadczeń (tj. unikatową nazwę osobiste lub nazwy UPN) skojarzone z jego subskrypcją w usłudze Intune.  

2.  Podczas instalacji użytkownicy mogą również wyświetlony monit o podanie identyfikatora firmy Apple. Przed urządzenia można instalować aplikacji Portal firmy, należy podać identyfikator firmy Apple. Użytkownicy mogą podać identyfikator firmy Apple, po zakończeniu instalacji z iOS **ustawienia** menu.  

3.  Po zakończeniu instalacji na urządzeniu należy zainstalować aplikację Portal firmy ze sklepu z aplikacjami, na przykład [aplikacji Portal firmy](https://itunes.apple.com/us/app/id719171358).  

4.  Użytkownik może teraz logowanie do portalu firmy z główną nazwę użytkownika używane podczas konfigurowania urządzenia.  

5.  Po zalogowaniu, użytkownik jest monitowany o zarejestrować swoje urządzenie. Pierwszym krokiem jest **zidentyfikowanie urządzenia**. Aplikacja zawiera listę urządzeń z systemem iOS, które firmy zarejestrowane i przypisane do konta usługi Intune użytkownika końcowego. Wybierz odpowiednie urządzenie.  

     Jeśli to urządzenie nie jest już zarejestrowane firmy, wybierz opcję "nowe urządzenie" Aby kontynuować przepływ standardowa rejestracji.  

6.  Na następnym ekranie użytkownik musi potwierdzić seryjny nowego urządzenia. Użytkownik może nacisnąć link „potwierdź numer seryjny”, aby uruchomić aplikację Ustawienia w celu zweryfikowania numeru seryjnego. Użytkownik musi następnie wprowadzić 4 ostatnie znaki numeru seryjnego w aplikacji Portal firmy.  

     Ten krok umożliwia zweryfikowanie, że urządzenie zostało zarejestrowane przez firmę w usłudze Intune. Jeśli numer seryjny urządzenia nie jest zgodny, oznacza to, że wybrano niewłaściwe urządzenie. Wróć do poprzedniego ekranu i wybierz inne urządzenie.  

7.  Po zweryfikowaniu numer seryjny przekierowuje do witryny internetowej portalu firmy, aby zakończyć rejestrację aplikacji Portal firmy, a następnie monituje użytkownika, aby powrócić do aplikacji.  

8.  Rejestracja jest teraz ukończona. Możesz teraz używać tego urządzenia z pełnym zestawem funkcji.  

##  <a name="BKMK_noUA"></a>Zarządzanych urządzeń bez koligacji użytkownika  
 Na urządzeniach, na których skonfigurowano **no user affinity** nie obsługują Portalu firmy i nie należy na nich instalować aplikacji. Portal firmy jest przeznaczony dla użytkowników, którzy mają poświadczenia firmowe i wymagają dostępu do spersonalizowanych zasobów firmowych (np. poczta e-mail). Urządzenia zarejestrowane **bez koligacji użytkownika** nie powinny być dedykowane do logowania dla określonego użytkownika. Urządzenia zarejestrowane bez koligacji użytkownika są zazwyczaj stosowane w kioskach lub punktach sprzedaży (POS) albo jako narzędzia udostępnione. Jeśli koligacja użytkownika jest wymagana, upewnij się, że dla profilu rejestracji urządzenia wybrano opcję **Koligacja użytkownika** przed zarejestrowaniem urządzenia. Aby zmienić stan koligacji na urządzeniu, należy wycofać i ponowna rejestracja urządzenia.

