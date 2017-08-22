---
title: Ustawienia zapory i portu klienta systemu Windows | Dokumentacja firmy Microsoft
description: "Wybierz zapory systemu Windows i ustawienia portu dla klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dce4b640-c92f-401a-9873-ce9aa9262014
caps.latest.revision: "8"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 79686514efcba344c4babc3d3be03b48adca7132
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="windows-firewall-and-port-settings-for-clients-in-system-center-configuration-manager"></a>Ustawienia zapory systemu Windows i portu dla klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Komputery klienckie w programie System Center Configuration Manager, w których działa Zapora systemu Windows często wymagają konfigurowania wyjątków, aby umożliwić komunikację z ich lokacją. Wyjątki, które trzeba skonfigurować, zależą od funkcji zarządzania używanych z klientem programu Configuration Manager.  

 Poniższe sekcje umożliwiają identyfikację tych funkcji zarządzania oraz zawierają dodatkowe informacje o sposobie konfigurowania tych wyjątków dla Zapory systemu Windows.  

##  <a name="BKMK_ModifyingWindowsFirewall"></a> Modyfikowanie portów i programów dozwolonych przez Zaporę systemu Windows  
 Poniższa procedura umożliwia zmodyfikowanie portów i programów w Zaporze systemu Windows dla klienta programu Configuration Manager.  

#### <a name="to-modify-the-ports-and-programs-permitted-by-windows-firewall"></a>Aby zmienić porty i programy dozwolone przez Zaporę w systemu Windows  

1.  Na komputerze, na którym działa Zapora systemu Windows, otwórz okno Panel sterowania.  

2.  Kliknij prawym przyciskiem myszy aplet **Zapora systemu Windows**, a następnie kliknij polecenie **Otwórz**.  

3.  Skonfiguruj wymagane wyjątki oraz niestandardowe programy i porty.  

## <a name="programs-and-ports-that-configuration-manager-requires"></a>Programy i porty wymagane przez program Configuration Manager  
 Następujące funkcje programu Configuration Manager wymagają ustawienia wyjątków w Zaporze systemu Windows:  

### <a name="queries"></a>Kwerendy  
 Po uruchomieniu konsoli programu Configuration Manager na komputerze, na którym działa Zapora systemu Windows są uruchamiane po raz pierwszy zapytania kończyć się niepowodzeniem i system operacyjny wyświetli okno dialogowe z pytaniem, czy chcesz odblokowanie pliku statview.exe. Odblokowanie pliku statview.exe spowoduje, że zapytania będą w przyszłości uruchamiane bez błędów. Przed uruchomieniem kwerendy można dodać plik Statview.exe do listy programów i usług na karcie **Wyjątki** Zapory systemu Windows.  

### <a name="client-push-installation"></a>Wypychana instalacja klienta  
 Aby wypychania klienta do zainstalowania klienta programu Configuration Manager, należy dodać następujące porty jako wyjątki do zapory systemu Windows:  

-   Wychodzące i przychodzące: **Udostępnianie plików i drukarek**  

-   Przychodzące: **Instrumentacja zarządzania Windows (WMI)**  

### <a name="client-installation-by-using-group-policy"></a>Instalacja klienta za pomocą zasad grupy  
 Aby użyć zasad grupy, aby zainstalować klienta programu Configuration Manager, należy dodać **udostępnianie plików i drukarek** jako wyjątek do zapory systemu Windows.  

### <a name="client-requests"></a>Żądania klienta  
 Dla komputerów klienckich do komunikacji z systemami lokacji programu Configuration Manager należy dodać następujące porty jako wyjątki do zapory systemu Windows:  

 Wychodzące: TCP Port **80** (dla komunikacji HTTP)  

 Wychodzące: TCP Port **443** (dla komunikacji HTTPS)  

> [!IMPORTANT]  
>  Są to domyślne numery portów, które można zmienić w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz temat jak [jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md). Jeżeli domyślne wartości dla tych portów zostały zmienione, należy także skonfigurować odpowiednie wyjątki w Zaporze systemu Windows.  

### <a name="client-notification"></a>Powiadomienie klienta  
 Punkt zarządzania powiadomienie, że komputery klienckie o akcji, które należy wykonać, gdy użytkownik administracyjny wybierze akcję klienta w konsoli programu Configuration Manager, takich jak pobranie zasad komputera lub rozpoczęcie skanowania złośliwego oprogramowania dodać następujący port jako wyjątek do zapory systemu Windows:  

 Wychodzące: TCP Port **10123**  

 Jeśli ta komunikacja nie powiedzie się, programu Configuration Manager automatycznie powraca do przy użyciu istniejącego punktu zarządzania klientami komunikacji portu protokołu HTTP lub HTTPS:  

 Wychodzące: TCP Port **80** (dla komunikacji HTTP)  

 Wychodzące: TCP Port **443** (dla komunikacji HTTPS)  

> [!IMPORTANT]  
>  Są to domyślne numery portów, które można zmienić w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md). Jeżeli domyślne wartości dla tych portów zostały zmienione, należy także skonfigurować odpowiednie wyjątki w Zaporze systemu Windows.  

### <a name="remote-control"></a>Zdalne sterowanie  
 Aby używać zdalnego sterowania programu Configuration Manager, Zezwalaj na następujące porty:  

-   Przychodzące: TCP Port**2701**  

### <a name="remote-assistance-and-remote-desktop"></a>Pomoc zdalna i Pulpit zdalny  
 Aby uruchomić Pomoc zdalną z konsoli programu Configuration Manager, należy dodać program niestandardowy **Helpsvc.exe** i niestandardowy port wejściowy TCP **135** do listy dozwolonych programów i usług w Zaporze systemu Windows na komputerze klienckim. Należy także zezwolić na działanie funkcji **Pomoc zdalna** i **Pulpit zdalny**. Jeżeli funkcja Pomoc zdalna zostanie uruchomiona z komputera klienckiego, Zapora systemu Windows Firewall automatycznie skonfiguruje funkcje **Pomoc zdalna** i **Pulpit zdalny**oraz zezwoli na ich działanie.  

### <a name="wake-up-proxy"></a>Serwer proxy wznawiania  
 Jeżeli ustawienie serwera proxy wznawiania zostanie włączone na kliencie, nowa usługa o nazwie Serwer proxy wznawiania ConfigMgr będzie korzystała z protokołu równorzędnego, aby sprawdzić, czy inne komputery w podsieci są wznowione oraz wznowić je w razie potrzeby. Ta funkcja komunikacji wykorzystuje następujące porty:  

 Wychodzące: UDP Port **25536**  

 Wychodzące: UDP Port **9**  

 Są to domyślne numery portów, które można zmienić w programie Configuration Manager za pomocą **zarządzania energią** ustawienia klientów **numer portu serwera proxy wznawiania (UDP)** i **numer portu Wake On LAN (UDP)**. Jeśli określisz **zarządzania energią**: **Wyjątek zapory systemu Windows dla serwera proxy wznawiania** klienta ustawienie, te porty zostaną automatycznie skonfigurowane w Zaporze systemu Windows dla klientów. Jeżeli jednak na klientach działa inna zapora, należy ręczne skonfigurować wyjątki dla tych numerów portów.  

 Oprócz tych portów, serwer proxy wznawiania korzysta także z komunikatów żądania echa protokołu ICMP (Internet Control Message Protocol) przesyłanych między komputerami klienckimi. Ta komunikacja służy do potwierdzenia, czy drugi komputer kliencki w sieci został wybudzony. Protokół ICMP jest czasami określany jako polecenia TCP/IP Ping.  

 Aby uzyskać więcej informacji o serwerze proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

### <a name="windows-event-viewer-windows-performance-monitor-and-windows-diagnostics"></a>Podgląd zdarzeń systemu Windows, Monitor wydajności systemu Windows i Diagnostyka systemu Windows  
 Aby otworzyć Podgląd zdarzeń systemu Windows, Monitor wydajności systemu Windows i Diagnostyka systemu Windows z konsoli programu Configuration Manager, należy włączyć **udostępnianie plików i drukarek** jako wyjątek w Zaporze systemu Windows.  

## <a name="ports-used-during-configuration-manager-client-deployment"></a>Porty używane podczas wdrażania klienta programu Configuration Manager  
 Poniższa tabela zawiera porty używane w procesie instalacji klienta.  

> [!IMPORTANT]  
>  Jeżeli między serwerami systemu lokacji a komputerem klienckim występuje zapora, należy sprawdzić, czy zezwala ona na ruch przez porty wymagane dla wybranej metody instalacji klienta. Przykładowo zapory często powodują niepowodzenie instalacji wypychanej klienta, ponieważ blokują Blok komunikatów serwera (SMB) i Zdalne wywołania procedur (RPC). W tym scenariuszu należy użyć innej metody instalacji klienta, na przykład instalacji ręcznej (uruchamiając plik CCMSetup.exe) lub instalacji klienta w oparciu o zasady grupy. Te alternatywne metody instalacji klienta nie wymagają korzystania z funkcji SMB ani RPC.  

 Informacje o sposobie konfigurowania Zapory systemu Windows na komputerze klienckim znajdują się w temacie [Modyfikowanie portów i programów dozwolonych przez Zaporę systemu Windows](#BKMK_ModifyingWindowsFirewall).  

### <a name="ports-that-are-used-for-all-installation-methods"></a>Porty używane we wszystkich metodach instalacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP (Hypertext Transfer Protocol) z komputera klienckiego do rezerwowy punkt stanu, gdy rezerwowy punkt stanu jest przypisany do klienta.|--|80 (zobacz uwaga 1, **Dostępny alternatywny port**)|  

### <a name="ports-that-are-used-with-client-push-installation"></a>Porty używane w instalacji wypychanej klienta  
 Oprócz portów wymienionych w poniższej tabeli, instalacja wypychana klienta używa także protokołu komunikatów żądania echa protokołu ICMP (Internet Control Message Protocol) z serwera lokacji do komputera klienckiego, aby sprawdzić, czy komputer kliencki jest dostępny w sieci. Protokół ICMP jest czasami określany jako polecenia TCP/IP Ping. Protokół ICMP nie ma numeru protokołu UDP ani TCP, dlatego nie został wymieniony w poniższej tabeli. Jednak, aby instalacja wypychana klienta powiodła się, wszystkie pośredniczące urządzenia sieciowe, takie jak zapory, muszą zezwalać na ruch ICMP.  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB) między serwerem lokacji a komputerem klienckim.|--|445|  
|Mapowanie punktów końcowych wywołań RPC między serwerem lokacji a komputerem klienckim.|135|135|  
|Porty dynamiczne wywołań RPC między serwerem lokacji a komputerem klienckim.|--|DYNAMICZNE|  
|Protokół HTTP (Hypertext Transfer Protocol) z komputera klienckiego do punktu zarządzania, jeżeli połączenie wykorzystuje protokół HTTP.|--|80 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Protokół HTTPS (Secure Hypertext Transfer Protocol) z komputera klienckiego do punktu zarządzania, jeżeli połączenie wykorzystuje protokół HTTPS.|--|443 (zobacz uwaga 1, **Dostępny alternatywny port**)|  

### <a name="ports-that-are-used-with-software-update-point-based-installation"></a>Porty używane z instalacją opartą na punkcie aktualizacji oprogramowania  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP (Hypertext Transfer Protocol) z komputera klienckiego do punktu aktualizacji oprogramowania.|--|80 lub 8530 (patrz adnotacja 2, **Usługi Windows Server Update Services**)|  
|Protokół HTTPS (Secure Hypertext Transfer Protocol) z komputera klienckiego do punktu aktualizacji oprogramowania.|--|443 lub 8531 (patrz adnotacja 2, **Usługi Windows Server Update Services**)|  
|Blok komunikatów serwera (SMB) między serwerem źródłowym i komputer kliencki w przypadku określenia właściwości wiersza polecenia CCMSetup **/source:&lt;ścieżki\>**.|--|445|  

### <a name="ports-that-are-used-with-group-policy-based-installation"></a>Porty używane z instalacją opartą na zasadach grupy  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP (Hypertext Transfer Protocol) z komputera klienckiego do punktu zarządzania, jeżeli połączenie wykorzystuje protokół HTTP.|--|80 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Protokół HTTPS (Secure Hypertext Transfer Protocol) z komputera klienckiego do punktu zarządzania, jeżeli połączenie wykorzystuje protokół HTTPS.|--|443 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Blok komunikatów serwera (SMB) między serwerem źródłowym i komputer kliencki w przypadku określenia właściwości wiersza polecenia CCMSetup **/source:&lt;ścieżki\>**.|--|445|  

### <a name="ports-that-are-used-with-manual-installation-and-logon-script-based-installation"></a>Porty używane z instalacją ręczną i instalacją opartą na skrypcie logowania  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB) między komputerem klienckim a udziałem sieciowym, z którego uruchomiono program CCMSetup.exe.<br /><br /> Podczas instalowania programu Configuration Manager, pliki źródłowe instalacji klienta są kopiowane i automatycznie udostępniane z  *&lt;Ścieżka_instalacji\>*folderu \Client na punktach zarządzania. Można jednak skopiować te pliki i utworzyć nowy udział na komputerze w sieci. Można także wyeliminować ten ruch sieciowy, uruchamiając program CCMSetup.exe lokalnie, na przykład z nośnika wymiennego.|--|445|  
|Protokół HTTP (Hypertext Transfer) z komputera klienckiego do punktu zarządzania, jeżeli połączenie wykorzystuje protokół HTTP i nie należy określać właściwości wiersza polecenia CCMSetup **/source:&lt;ścieżki\>**.|--|80 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Secure Hypertext Transfer Protocol (HTTPS) z komputera klienckiego do punktu zarządzania, jeśli połączenie wykorzystuje protokół HTTPS i nie należy określać właściwości wiersza polecenia programu CCMSetup **/source:&lt;ścieżki\>**.|--|443 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Blok komunikatów serwera (SMB) między serwerem źródłowym i komputer kliencki w przypadku określenia właściwości wiersza polecenia CCMSetup **/source:&lt;ścieżki\>**.|--|445|  

### <a name="ports-that-are-used-with-software-distribution-based-installation"></a>Porty używane z instalacją opartą na dystrybucji oprogramowania  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB) między punktem dystrybucji a komputerem klienckim.|--|445|  
|Protokół HTTP (Hypertext Transfer Protocol) z komputera klienckiego do punktu dystrybucji, jeżeli połączenie wykorzystuje protokół HTTP.|--|80 (zobacz uwaga 1, **Dostępny alternatywny port**)|  
|Protokół HTTPS (Secure Hypertext Transfer Protocol) z komputera klienckiego do punktu dystrybucji, jeżeli połączenie wykorzystuje protokół HTTPS.|--|443 (zobacz uwaga 1, **Dostępny alternatywny port**)|  

## <a name="notes"></a>Uwagi  
 **1 dostępny alternatywny Port** w programie Configuration Manager można zdefiniować alternatywny port dla tej wartości. Jeżeli zdefiniowano port niestandardowy, należy go zastąpić podczas definiowania informacji o filtrze IP dla zasad IPsec lub w celu skonfigurowania zapory.  

 **2 Windows Server Update Services** Program Windows Server Update Service (WSUS) można zainstalować w domyślnej witrynie sieci Web (port 80) lub w niestandardowej witrynie sieci Web (port 8530).  

 Po przeprowadzeniu instalacji można zmienić port. Nie jest konieczne używanie tego samego numeru portu w całej hierarchii lokacji.  

 Jeżeli port protokołu HTTP to 80, port protokołu HTTPS musi mieć wartość 443.  

 Jeśli port protokołu HTTP jest inny, HTTPS port musi wynosić 1 wyższej. Na przykład 8530 i 8531.
