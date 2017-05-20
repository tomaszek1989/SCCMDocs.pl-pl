---
title: "Możliwości w Technical Preview 1603 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1603."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: dee2b4ce042bb4a434bb019e17a6b16e2807945c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1603-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1603 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1603. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Alternatywnie korzystając z systemu Center Technical Preview 5, tej wersji instaluje w linii bazowej wersji programu System Center Configuration Manager Technical Preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 **Znane problemy dotyczące tej Technical Preview:**  

-   Ta wersja zawiera aktualizacje dla funkcji wydanych, ale nie wprowadzają nowych funkcji. W związku z tym na stronie funkcje kreatora aktualizacji będzie pusta, jeśli został wcześniej uaktualniony do 1602 i wszystkie funkcje programu 1602 włączone.  

-   Po aktualizacji serwera lokacji do 1603 Technical Preview, klienci są w stanie używać żadnych funkcji zdalnego sterowania, aż do ich również aktualizacja do wersji 1603.  

 **Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="BKMK_SC1603"></a>Ulepszenia programu Software Center  

### <a name="new-tiled-view-for-apps"></a>Nowy widok ułożonymi sąsiadująco dla aplikacji  
 Użytkownicy końcowi można wybrać między listę aplikacji lub widok ułożonymi sąsiadująco aplikacje w **aplikacji** kartę Centrum oprogramowania.  

### <a name="select-multiple-updates-in-software-center"></a>Wybrać wiele aktualizacji w Centrum oprogramowania  
 W **aktualizacje** kartę w programie Software Center, możesz teraz wybrać wiele aktualizacji, lub wybrać **Aktualizuj wszystkie** rozpoczęcie instalacji wielu aktualizacji jednocześnie.  

##  <a name="BKMK_RC1603"></a>Ulepszenia zdalnego sterowania  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>Ograniczenia dostępu Schowek udostępniony w sesji zdalnego sterowania  
 Obecnie można włączyć nowe ustawienie klienta narzędzi zdalnych **Monituj użytkownika o uprawnienia transferu pliku Schowek udostępniony** do ograniczania dostępu do udostępnionych Schowka w sesji zdalnego sterowania.  

 Po włączeniu użytkownika końcowego, który udostępnia sesję zdalnego należy przyznać uprawnienia do przeglądarki z tej sesji, aby przeglądarka może transferu plików z sesji do ich komputera lokalnego przez Schowek udostępniony.  

 Dodaje warstwę ochrony dla użytkownika końcowego, jak wcześniej, jeśli Podgląd uzyskał pełną kontrolę nad komputerem użytkownika końcowego, byłyby mógł użyć udostępnionych Schowka do transferu plików z sesji na ich komputerach lokalnych w taki sposób, że został całkowicie niewidoczne dla użytkownika końcowego.  

##  <a name="BKMK_RamDiskTFTP"></a> Dostosowywanie rozmiaru okna i bloku RamDisk TFTP w punktach dystrybucji z obsługą środowiska PXE  
 W 1603 Technical Preview można dostosować rozmiar bloku RamDisk TFTP i rozmiaru okna dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli skonfigurowano sieć, może to powodować niepowodzenie pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ rozmiar bloku lub okna jest zbyt duży. Dostosowanie rozmiaru bloku i rozmiaru okna RamDisk TFTP umożliwia zoptymalizowanie ruchu TFTP w środowisku PXE w celu spełnienia określonych wymagań sieciowych.   
Aby określić najbardziej wydajne rozwiązanie, należy przetestować dostosowane ustawienia w swoim środowisku.  

-   **Rozmiar bloku TFTP**: Rozmiar bloku jest rozmiar pakietów danych, które są wysyłane przez serwer do klienta, który pobiera plik (zgodnie z opisem w dokumencie RFC 2347). Większy rozmiar bloku zezwala serwerowi na wysyłanie mniejszej liczby pakietów, co przekłada się na zmniejszenie obustronnych opóźnień między serwerem a klientem. Niemniej jednak duże rozmiary bloków powodują fragmentowanie pakietów. Większość wdrożeń klienckich środowiska PXE nie obsługuje pakietów po fragmentacji.  

-   **Rozmiar okna TFTP**: TFTP wymaga pakietu potwierdzenie (ACK) dla każdego bloku danych, które są wysyłane. Serwer nie wyśle kolejnego bloku, dopóki nie odbierze pakietu ACK dla poprzedniego bloku. Dostosowywanie okien TFTP jest funkcją Usług wdrażania systemu Windows, która umożliwia określenie liczby bloków danych potrzebnych do wypełnienia okna. Serwer wysyła bloki danych symetrycznie, dopóki okno nie zostanie wypełnione, a następnie klient wysyła pakiet ACK. Zwiększenie rozmiaru okna redukuje liczbę obustronnych opóźnień między klientem a serwerem i zmniejsza całkowity czas wymagany do pobrania obrazu rozruchowego.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie powiadomienie nas o tym, jak pracy za pomocą informacji opinii w górnej części tego tematu:  

-   Można dostosować rozmiar okna RamDisk TFTP w punkcie dystrybucji z włączoną obsługą środowiska PXE.  

-   Można dostosować rozmiar bloku RamDisk TFTP w punkcie dystrybucji z włączoną obsługą środowiska PXE.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>Aby zmienić rozmiar okna RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPWindowSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosować rozmiar okna\>  

 Wartość domyślna to 1 (1 blok danych będzie wypełniać okno).  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>Aby zmienić rozmiar bloku RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPBlockSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosować rozmiar bloku\>  

 Wartość domyślna to 4096 (4k).  

