---
title: Tworzenie aplikacji systemu Android | Dokumentacja firmy Microsoft
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Android."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 3a89abc81cd70f4e499bf4e3087fd53915377c44
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji systemu Android z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia. Typy wdrożeń zawiera pliki instalacyjne i informacje niezbędne do wdrożenia oprogramowania na urządzeniu. Typ wdrożenia ma również zasady określające, kiedy i jak oprogramowanie zostanie wdrożone.  

 Aplikacje można utworzyć przy użyciu następujących metod:  

-   Automatyczne tworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  
-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  
-   Zaimportowanie aplikacji z pliku.  

Zobacz [uruchomić Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) dla czynności wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy pamiętać przedstawione poniżej zagadnienia, podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Android.  

## <a name="general-considerations-for-android-apps"></a>Ogólne zagadnienia dotyczące aplikacji dla systemu Android

Program Configuration Manager obsługuje wdrażanie następujących typów aplikacji dla systemu Android:

|Typ urządzenia|Obsługiwane pliki|
|-|-|
|Android|apk|

Obsługiwane są następujące akcje wdrażania:

|Typ urządzenia|Obsługiwane akcje|
|-|-|
|Android|**Dostępne**, **wymagane** użytkownik musi wyrazić zgodę do instalacji i dezinstalacji.|
|Android for Work | **Wymagane** |

## <a name="approve-and-deploy-android-for-work-apps"></a>Zatwierdzanie i wdrażanie systemu Android dla aplikacji służbowych
Jako administrator programu Configuration Manager, należy również zatwierdzić aplikacji w [odtwarzania dla witryny sieci Web pracy](https://play.google.com/work)i wdrożyć aplikacje Android zarządzanych urządzeń w pracy.

Wykonaj poniższe kroki zatwierdzania aplikacji w Play pracy magazynu, zsynchronizować je z konsoli programu Configuration Manager i wdrażać je dla Android zarządzanych urządzeń w pracy. Wdrażanie aplikacji na profilach pracy użytkowników, musisz zatwierdzić aplikacji w Play do pracy, a następnie synchronizacji aplikacji za pomocą konsoli programu Configuration Manager.

1. Otwórz przeglądarkę i przejdź do: https://play.google.com/work.
2. Zaloguj się przy użyciu konta administratora usługi Google powiązanej z dzierżawy usługi Intune.
3. Przeglądaj w poszukiwaniu aplikacji, które chcesz wdrożyć w danym środowisku, a następnie wybierz pozycję **Zatwierdź** dla każdego z nich, aby udostępnić aplikację dla systemu Android for Work.
4. W konsoli programu Configuration Manager, przejdź do **administratora** > **omówienie** > **usługi w chmurze** > **Android for Work** i wybierz polecenie **synchronizacji**.
5. Poczekaj do 10 minut aplikacje do synchronizacji, a następnie przejdź do **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **informacji o licencji dla aplikacji ze sklepu**.
6. Wybierz aplikację synchronizowane z Play do pracy, a następnie wybierz pozycję **tworzenie aplikacji**.
7. Zakończ pracę kreatora i wybrać **Zamknij**.
8. Przejdź do **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **aplikacji**, wybierz systemu Android dla aplikacji do pracy i wdrażanie w zwykły sposób.

Aby zsynchronizować Play dla aplikacji do pracy z programem Configuration Manager, możesz musi zatwierdzić co najmniej jedną aplikację na Play pracy witryny sieci Web.

