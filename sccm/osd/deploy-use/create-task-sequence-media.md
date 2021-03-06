---
title: Tworzenie nośnika sekwencji zadań
titleSuffix: Configuration Manager
description: Utwórz nośnik sekwencji zadań, takich jak dysk CD, aby wdrożyć system operacyjny na komputerze docelowym w środowisku programu Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 69c2f3620ed618711534366121aa1267efe6a8a5
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-task-sequence-media-with-system-center-configuration-manager"></a>Tworzenie nośnika sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Nośnika można użyć, aby przechwycić obraz systemu operacyjnego z komputera odniesienia lub do wdrożenia systemu operacyjnego na komputerze docelowym w środowisku programu System Center Configuration Manager. Tworzonym nośnikiem może być zestaw dysków CD lub DVD albo dysk flash USB.  

 Nośniki są używane przede wszystkim do wdrażania systemów operacyjnych na komputerach docelowych, które nie dysponują połączeniem sieciowym lub których połączenia o niskiej przepustowości do lokacji programu Configuration Manager. Jednak nośniki wdrażania są także używane do uruchamiania wdrożenia systemu operacyjnego spoza istniejącego systemu operacyjnego Windows. To drugie zastosowanie nośnika wdrażania przydaje się zwłaszcza wtedy, gdy na komputerze docelowym nie ma systemu operacyjnego, system operacyjny nie nadaje się do użytku albo użytkownik administracyjny chce ponownie podzielić dysk komputera docelowego na partycje.  

 Nośnikami wdrażania mogą być nośniki rozruchowe, nośniki samodzielne i nośniki wstępnie przygotowane. Zawartość nośników wdrażania różni się w zależności od typu nośnika. Na przykład nośnik samodzielny zawiera sekwencję zadań, która wdraża system operacyjny, natomiast nośniki innych typów pobierają sekwencję zadań z punktu zarządzania.  

> [!IMPORTANT]  
>  Aby utworzyć nośnik sekwencji zadań, musi być kontem administratora na komputerze z poziomu konsoli programu Configuration Manager. Jeśli użytkownik nie jest administratorem, zostanie poproszony o poświadczenia administratora po uruchomieniu Kreatora tworzenia nośnika sekwencji zadań.  

##  <a name="BKMK_PlanCaptureMedia"></a> Nośniki dla obrazów systemu operacyjnego przechwytywania  
 Nośniki przechwytywania pozwalają przechwytywać obraz systemu operacyjnego z komputera odniesienia. Nośnik przechwytywania zawiera obraz rozruchowy, który uruchamia komputer odniesienia, oraz sekwencję zadań, która przechwytuje obraz systemu operacyjnego. Aby uzyskać informacje na temat sposobu tworzenia nośnika przechwytywania, zobacz [Tworzenie nośnika przechwytywania w programie System Center Configuration Manager](create-capture-media.md).  

##  <a name="BKMK_PlanBootableMedia"></a> Wdrożenia z nośników rozruchowych systemu operacyjnego  
 Nośnik rozruchowy zawiera tylko obraz rozruchowy, opcjonalne [polecenia przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md) i wymaganymi przez nie plikami oraz pliki binarne programu Configuration Manager. W chwili uruchomienia komputer docelowy łączy się z siecią i pobiera z niej sekwencję zadań, obraz systemu operacyjnego oraz inną wymaganą zawartość. Ponieważ sekwencja zadań nie znajduje się na nośniku, sekwencję zadań oraz zawartość można zmienić bez konieczności ponownego tworzenia nośnika.  

> [!IMPORTANT]  
>  Pakiety na nośniku rozruchowym nie są szyfrowane. Użytkownik administracyjny musi podjąć odpowiednie środki bezpieczeństwa, takie jak dodanie hasła do nośnika, oraz upewnić się, że zawartość pakietu jest chroniona przed nieautoryzowanymi użytkownikami.  

 Aby uzyskać informacje o sposobie tworzenia nośnika rozruchowego [tworzenia nośnika rozruchowego](create-bootable-media.md).  

##  <a name="BKMK_PlanPrestagedMedia"></a> Wdrażanie systemu operacyjnego wstępnie przygotowanego nośnika  
 Nośniki wstępnie przygotowane pozwalają wstępnie przygotować nośnik rozruchowy oraz obraz systemu operacyjnego przed ich udostępnieniem. Nośnik wstępnie przygotowany to plik Windows Imaging Format (WIM), który można zainstalować na komputerze bez systemu operacyjnego przez producenta tego komputera lub w Centrum przygotowywania przedsiębiorstwa niepołączonym do środowiska programu Configuration Manager.  

 Nośnik wstępnie przygotowany zawiera obraz rozruchowy używany do uruchomienia komputera docelowego oraz obraz systemu operacyjnego stosowany względem tego komputera. Możesz także określić aplikacje, pakiety i pakiety sterowników, które mają zostać dołączone do wstępnie przygotowanego nośnika. Na nośniku nie znajduje się sekwencja zadań, która wdraża system operacyjny. W czasie wdrażania sekwencji zadań wykorzystującej wstępnie przygotowany nośnik klient najpierw sprawdza, czy w lokalnej pamięci podręcznej sekwencji zadań znajduje się prawidłowa zawartość. Jeśli zawartości nie można odnaleźć lub została zmieniona, klient pobiera zawartość z punktu dystrybucji.  

 Nośnik wstępnie przygotowany jest umieszczany na dysku twardym nowego komputera przed jego wysłaniem do użytkownika końcowego. Po uruchomieniu komputera po raz pierwszy po zastosowaniu wstępnie przygotowanego nośnika komputer uruchamia środowisko Windows PE i nawiązuje połączenie z punktem zarządzania w celu zlokalizowania sekwencji zadań, która kończy proces wdrożenia systemu operacyjnego.  

> [!IMPORTANT]  
>  Pakiety na nośniku wstępnie przygotowanym nie są szyfrowane. Użytkownik administracyjny musi podjąć odpowiednie środki bezpieczeństwa, takie jak dodanie hasła do nośnika, oraz upewnić się, że zawartość pakietu jest chroniona przed nieautoryzowanymi użytkownikami.  

 Aby uzyskać informacje o sposobie tworzenia wstępnie przygotowanego nośnika, zobacz [Tworzenie wstępnie przygotowanego nośnika](create-prestaged-media.md).  

##  <a name="BKMK_PlanStandaloneMedia"></a> Wdrożenia z nośników autonomicznych systemu operacyjnego  
 Nośniki samodzielne zawierają wszystkie elementy niezbędne do wdrożenia systemu operacyjnego. Obejmuje to sekwencję zadań oraz wszelką inną wymaganą zawartość. Ponieważ na nośniku samodzielnym są przechowywane wszystkie elementy wymagane do wdrożenia systemu operacyjnego, przestrzeń dyskowa wymagana przez taki nośnik jest znacznie mniejsza niż w przypadku nośników innych typów.  

 Aby uzyskać informacje o sposobie tworzenia nośnika autonomicznego, zobacz [tworzenia nośnika samodzielnego](create-stand-alone-media.md).  

## <a name="media-considerations-when-using-site-systems-configured-for-https"></a>Uwagi dotyczące nośników stosowanych z systemami lokacji skonfigurowanymi do używania protokołu HTTPS  
 Gdy punkt zarządzania i punkty dystrybucji są skonfigurowane do używania protokołu HTTPS, nośnik rozruchowy i nośnik wstępnie przygotowany należy utworzyć w lokacji głównej, a nie w centralnej lokacji administracyjnej. Aby ułatwić ustalenie, czy nośnik ma być skonfigurowany jako dynamiczny, czy oparty na lokacji, należy również rozważyć następujące kwestie:  

-   Aby skonfigurować nośnik jako dynamiczny, wszystkie lokacje główne muszą mieć główny urząd certyfikacji lokacji, z której jest tworzony nośnik. Główny urząd certyfikacji można zaimportować do wszystkich lokacji głównych w hierarchii.  

-   Gdy lokacje główne w hierarchii programu Configuration Manager używają różnych głównych urzędów certyfikacji, należy korzystać z nośników opartych na lokacji w każdej lokacji.  
