---
title: Funkcje w wersji zapoznawczej Technical Preview 1603 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersji 1603."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: dee2b4ce042bb4a434bb019e17a6b16e2807945c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1603-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1603 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersji 1603. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Alternatywnie użycie oprogramowania System Center Technical Preview 5, ta wersja jest instalowany jako wersji bazowej programu System Center Configuration Manager Technical Preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 **Znane problemy dotyczące tej wersji Technical Preview:**  

-   Ta wersja zawiera aktualizacje wcześniej wydanych funkcji, ale nie wprowadza nowych funkcji. W związku z tym strona funkcje w Kreatorze aktualizacji będzie pusta, jeśli został wcześniej uaktualniony do wersji 1602 i włączył wszystkie funkcje dołączone do wersji 1602.  

-   Po aktualizacji serwera lokacji do wersji Technical Preview 1603, klienci będą mogli używać żadnych funkcji zdalnego sterowania, dopóki nie przeprowadzą aktualizacji do wersji 1603.  

 **Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="BKMK_SC1603"></a>Ulepszenia Centrum oprogramowania  

### <a name="new-tiled-view-for-apps"></a>Nowy widok sąsiadującym dla aplikacji  
 Użytkownicy końcowi mogą teraz wybierać między listę aplikacji lub aplikacji w widoku sąsiadującym **aplikacji** Centrum oprogramowania.  

### <a name="select-multiple-updates-in-software-center"></a>Wybieranie wielu aktualizacji w programie Software Center  
 W **aktualizacje** kartę Centrum oprogramowania, można teraz wybrać wiele aktualizacji, lub wybrać **Aktualizuj wszystkie** aby rozpocząć jednoczesne instalowanie wielu aktualizacji.  

##  <a name="BKMK_RC1603"></a>Ulepszenia zdalnego sterowania  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>Ogranicz dostęp do udostępnionego Schowka podczas sesji zdalnego sterowania  
 Można teraz włączyć nowe ustawienie klienta narzędzi zdalnych **Monituj użytkownika o zezwolenie na transfer pliku udostępnionego w schowku** Aby ograniczyć dostęp do udostępnionego Schowka podczas sesji zdalnego sterowania.  

 Po włączeniu użytkownik końcowy udostępniający sesję zdalną musi udzielić uprawnień do Podgląd sesji, zanim Podgląd można przesyłać pliki z sesji do komputera lokalnego za pośrednictwem udostępnionego Schowka.  

 Dodaje warstwę ochrony dla użytkownika końcowego, jak wcześniej, jeśli przeglądarka uzyskał pełną kontrolę nad komputerem użytkownika końcowego, one będą mogli używać udostępnionego Schowka do przesyłania plików z sesji do komputera lokalnego w sposób całkowicie niewidoczny dla użytkownika końcowego.  

##  <a name="BKMK_RamDiskTFTP"></a> Dostosowywanie rozmiaru okna i bloku RamDisk TFTP w punktach dystrybucji z obsługą środowiska PXE  
 W Technical Preview 1603 można dostosować rozmiar bloku RamDisk TFTP i rozmiaru okna dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli skonfigurowano sieć, może to powodować niepowodzenie pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ rozmiar bloku lub okna jest zbyt duży. Dostosowanie rozmiaru bloku i rozmiaru okna RamDisk TFTP umożliwia zoptymalizowanie ruchu TFTP w środowisku PXE w celu spełnienia określonych wymagań sieciowych.   
Aby określić najbardziej wydajne rozwiązanie, należy przetestować dostosowane ustawienia w swoim środowisku.  

-   **Rozmiar bloku TFTP**: Rozmiar bloku jest rozmiarem pakietów danych, które są wysyłane przez serwer do klienta pobierającego plik (zgodnie z opisem w dokumencie RFC 2347). Większy rozmiar bloku zezwala serwerowi na wysyłanie mniejszej liczby pakietów, co przekłada się na zmniejszenie obustronnych opóźnień między serwerem a klientem. Niemniej jednak duże rozmiary bloków powodują fragmentowanie pakietów. Większość wdrożeń klienckich środowiska PXE nie obsługuje pakietów po fragmentacji.  

-   **Rozmiar okna TFTP**: TFTP wymaga pakietu z potwierdzeniem (ACK) dla każdego bloku danych, które są wysyłane. Serwer nie wyśle kolejnego bloku, dopóki nie odbierze pakietu ACK dla poprzedniego bloku. Dostosowywanie okien TFTP jest funkcją Usług wdrażania systemu Windows, która umożliwia określenie liczby bloków danych potrzebnych do wypełnienia okna. Serwer wysyła bloki danych symetrycznie, dopóki okno nie zostanie wypełnione, a następnie klient wysyła pakiet ACK. Zwiększenie rozmiaru okna redukuje liczbę obustronnych opóźnień między klientem a serwerem i zmniejsza całkowity czas wymagany do pobrania obrazu rozruchowego.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać następujące zadania, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

-   Mogę dostosować rozmiar okna RamDisk TFTP w punkcie dystrybucji z włączoną obsługą środowiska PXE.  

-   Mogę dostosować rozmiar bloku RamDisk TFTP w punkcie dystrybucji z włączoną obsługą środowiska PXE.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>Aby zmienić rozmiar okna RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPWindowSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosowany rozmiar okna\>  

 Wartość domyślna to 1 (1 blok danych będzie wypełniać okno).  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>Aby zmienić rozmiar bloku RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPBlockSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosowany rozmiar bloku\>  

 Wartość domyślna to 4096 (4k).  
