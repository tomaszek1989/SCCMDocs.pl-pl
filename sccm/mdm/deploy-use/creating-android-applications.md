---
title: Tworzenie aplikacji systemu Android | Dokumentacja firmy Microsoft
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji na urządzeniach z systemem Android."
ms.custom: na
ms.date: 03/27/2017
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: d3b20a59a9147e09e58f04f83f97fd72ebfef5a1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji Android z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aplikacji programu System Center Configuration Manager ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje wymagane do wdrożenia oprogramowania na urządzeniu. Typu wdrożenia zawiera również zasady określające czas i sposób wdrożenia oprogramowania.  

 Możesz tworzyć aplikacje przy użyciu następujących metod:  

-   Automatyczne utworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  
-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  
-   Importowanie aplikacji z pliku.  

Zobacz [Uruchom Kreatora tworzenia aplikacji](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) kroki wymagane do tworzenia aplikacji programu Configuration Manager i typów wdrożeń. Ponadto należy uwzględnić następujące kwestie, podczas tworzenia i wdrażania aplikacji na urządzeniach z systemem Android.  

## <a name="general-considerations-for-android-apps"></a>Ogólne zagadnienia dotyczące aplikacji systemu Android

Program Configuration Manager obsługuje wdrażanie następujących typów aplikacji dla systemu Android:

|Typ urządzenia|Obsługiwane pliki|
|-|-|
|Android|apk|

Obsługiwane są następujące akcje wdrażania:

|Typ urządzenia|Obsługiwane akcje|
|-|-|
|Android|**Dostępne**, **wymagane**. Użytkownik musi wyrazić zgodę na instalacji i dezinstalacji.

## <a name="approve-and-deploy-android-for-work-apps"></a>Zatwierdzanie i wdrażanie Android dla aplikacji do pracy
Jako administrator programu Configuration Manager, można zatwierdzać i wdrażać aplikacje w [odtwarzanie dla witryny sieci Web pracy](https://play.google.com/work)i wdrażania tych aplikacji Android zarządzanych urządzeń w pracy.

Wykonaj te kroki, aby zatwierdzić aplikacje w grę dla sklepu pracy, synchronizować je do konsoli programu Configuration Manager i wdrażanie ich Android zarządzanych urządzeń w pracy. Aby wdrożyć aplikacje profilów użytkowników pracy, musisz zatwierdzić aplikacje Play pracy, a następnie synchronizacji aplikacji za pomocą konsoli programu Configuration Manager.

1. Otwórz przeglądarkę i przejdź do: https://play.google.com/work.
2. Zaloguj się przy użyciu konta administratora Google powiązanej z dzierżawą usługi Intune.
3. Przeglądaj w poszukiwaniu aplikacji, które chcesz wdrożyć w środowisku, a następnie wybierz **Zatwierdź** dla każdego z nich, aby udostępnić aplikację dla systemu Android do pracy.
4. W konsoli programu Configuration Manager, przejdź do **administratora** > **Przegląd** > **usług w chmurze** > **Android pracy** i wybierz polecenie **synchronizacji**.
5. Poczekaj 10 minut dla aplikacji do synchronizacji, a następnie przejdź do **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **informacji o licencji dla aplikacji do sklepu**.
6. Wybierz aplikację zsynchronizowane z Play pracy, a następnie wybierz **tworzenie aplikacji**.
7. Zakończ pracę kreatora i wybrać **Zamknij**.
8. Przejdź do **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **aplikacji**, wybierz Android pracę aplikacji i wdrażania w zwykły sposób.

Aby zsynchronizować Play dla aplikacji do pracy z programem Configuration Manager, należy musi zatwierdzić co najmniej jedną aplikację na Play pracy witryny sieci Web.

