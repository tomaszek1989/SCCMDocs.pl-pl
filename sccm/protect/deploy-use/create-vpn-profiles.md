---
title: Jak profile tworzenia sieci VPN w programie System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak tworzyć profile sieci VPN w programie System Center Configuration Manager."
ms.custom: 
ms.date: 4/19/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: 15
author: lleonard-msft
caps.handback.revision: 0
ms.author: alleonar
ms.manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7a6c89254d01f4074e5c170b20338686178ebdd3
ms.openlocfilehash: 359fcfd9754fb5c81763bc44cac45376ea3ab0b8
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>Jak tworzyć profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Dostępne dla platform urządzeń różnych typów połączeń są opisane w [profile sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

W przypadku połączeń sieci VPN innej firmy rozpowszechnić aplikację sieci VPN przed wdrożeniem profilu sieci VPN. Jeśli nie można wdrożyć aplikację, użytkowników będzie trzeba to zrobić podczas próby połączenia się z siecią VPN. Aby dowiedzieć się, jak wdrażać aplikacje, zobacz [wdrażania aplikacji z System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

### <a name="create-a-vpn-profile"></a>Tworzenie profilu sieci VPN   

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **ustawień zgodności** > **dostęp do zasobów firmy** > **profile sieci VPN**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **utworzyć profil sieci VPN**.  


1.  Ukończ **ogólne** strony. Należy pamiętać o następujących kwestiach:  

       - Nie używaj znaków \\/ :*?&lt; > &#124; lub znak spacji w nazwie profilu sieci VPN. Następujące znaki nie są obsługiwane przez profil sieci VPN systemu Windows Server.  

       -   Wybierz **Importuj istniejący element profilu VPN z pliku** zaimportować informacje o profilu sieci VPN, które zostały wyeksportowane do pliku XML (Windows 8.1 i Windows RT).  

1.  Na **połączenia** określ:  

    -   **Typ połączenia**: Wybierz typ połączenia sieci VPN. Można wybrać typy połączeń w poniższej tabeli.  

    -   **Lista serwerów**: Dodawanie nowego serwera na potrzeby połączenia VPN. W zależności od typu połączenia można dodać jeden lub więcej serwerów sieci VPN i określić domyślny serwer.  

        > [!NOTE]  
        >  Urządzenia z systemem iOS nie umożliwiają użycia wielu serwerów sieci VPN. Jeśli skonfigurowano wiele serwerów sieci VPN, a następnie wdrożono profil sieci VPN na urządzeniu z systemem iOS, możliwe będzie użycie tylko serwera domyślnego.  

     Ta tabela zawiera opcje typy połączeń. Zapoznaj się z dokumentacją serwera VPN, aby uzyskać więcej informacji.

| &nbsp;&nbsp;Opcja&nbsp;&nbsp; | Więcej informacji | &nbsp;&nbsp;Połączenie&nbsp;typu&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**Obszar**     |Obszar uwierzytelniania, która ma być używana. Obszar uwierzytelniania to grupa zasobów uwierzytelniania używana przez typ połączenia Pulse Secure.|Pulse Secure|    
|**Rola**        |Rola użytkownika, która ma dostęp do tego połączenia. |Pulse Secure|  
|**Grupa lub domena logowania** |Nazwa grupy lub domeny logowania, który chcesz nawiązać połączenie.|Dell SonicWALL Mobile Connect|  
|**Odcisk palca**  |Ciąg, na przykład "Contoso odcisk palca kod", który będzie używany do sprawdzenia, czy serwer sieci VPN jest zaufany.<br /><br /> Odcisk palca można:<br /><br /> — Wysłać do klienta, który będzie wówczas traktował każdy serwer przedstawiający ten sam odcisk palca podczas połączenia jako zaufany.<br /><br /> — Jeśli urządzenie nie otrzymało jeszcze odcisku palca, wyświetli monit użytkownika zaufania serwera sieci VPN, którym jest nawiązywane połączenie, zawierający odcisk palca (użytkownik samodzielnie weryfikuje odcisk palca i wybierze **zaufania** nawiązać).|Check Point Mobile VPN|  
|**Wyślij cały ruch sieciowy przez połączenie VPN** |Jeśli ta opcja nie została wybrana, można określić dodatkowe trasy dla połączenia (w przypadku typów połączeń **Microsoft SSL (SSTP)**, **Microsoft Automatic**, **IKEv2**, **PPTP** i **L2TP** ), czyli tzw. tunelowanie podzielone lub tunelowanie VPN.<br /><br /> Tylko połączenia z siecią firmową są przesyłane przez tunel VPN. Tunelowanie VPN nie jest używane w przypadku łączenia się z zasobami przez Internet. |Wszystkie|  
|**Sufiks DNS zależny od połączenia** |Sufiks systemu nazw domen (DNS) specyficzny dla połączenia.|— Microsoft SSL (SSTP)<br /><br /> — Tryb automatyczny firmy Microsoft<br /><br /> — IKEv2<br /><br /> — PPTP<br /><br /> — L2TP|  
|**Obejście sieci VPN po podłączeniu do firmowej sieci Wi-Fi**  |Połączenie sieci VPN nie będzie używany, gdy urządzenie jest połączone z firmową siecią Wi-Fi.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN<br /><br /> — Microsoft SSL (SSTP)<br /><br /> — Tryb automatyczny firmy Microsoft<br /><br /> — IKEv2<br /><br /> — L2TP|  
|**Obejdź sieć VPN w przypadku połączenia z domową siecią Wi-Fi**  |Połączenie sieci VPN nie będzie używany, gdy urządzenie jest połączone z domową siecią Wi-Fi.|Wszystkie|  
|**Dla sieci VPN aplikacji (system iOS 7 i nowsze, system Mac OS X 10.9 i nowsze)** |Powiązać to połączenie sieci VPN z aplikacją iOS tak, aby po uruchomieniu aplikacji będzie można otworzyć połączenia. Podczas wdrażania profilu sieci VPN możesz skojarzyć go z aplikacją.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN|  
|**Niestandardowy plik XML (opcja)** |Określenie niestandardowych poleceń XML do konfiguracji połączenia sieci VPN.<br /><br /> Przykłady:<br /><br /> **Pulse Secure**:<br /><br /> **&lt;Schemat Pulse ><br /> &nbsp; &lt;isSingleSignOnCredential > true&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema >**<br /><br /> **CheckPoint Mobile VPN**:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; port = "443" name = "CheckPointSelfhost" <br /> &nbsp; rejestracji jednokrotnej = "true" <br /> &nbsp; debug = "3"<br />/>**<br /><br /> **Dell SonicWALL Mobile Connect**:<br /><br /> **&lt;MobileConnect\> <br /> &nbsp; &nbsp; &lt;kompresji\>false&lt;iskrowy\> <br /> &nbsp; &nbsp; &lt;debugLogging\>True&lt;/debugLogging\> <br /> &nbsp; &nbsp; &lt;packetCapture\>False&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> **F5 Edge Client**:<br /><br /> **&lt;F5-vpn-conf >&lt;pojedynczego logowania na poświadczenia >&lt;/f5-vpn-conf >**<br /><br /> Więcej informacji na temat tworzenia niestandardowych poleceń XML zawiera dokumentacja sieci VPN dostarczana przez producentów.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN|  

> [!NOTE]  
>  Aby uzyskać informacje dotyczące tworzenia profilów sieci VPN dla urządzeń przenośnych, zobacz [tworzenie profili sieci VPN](../../mdm/deploy-use/create-vpn-profiles.md)  

Ukończ pracę kreatora. Nowy profil sieci VPN zostanie wyświetlony w węźle **Profile VPN** w obszarze roboczym **Zasoby i zgodność** .

### <a name="next-steps"></a>Następne kroki

- W przypadku połączeń sieci VPN innej firmy rozpowszechnić aplikację sieci VPN przed wdrożeniem profilu sieci VPN. Jeśli nie można wdrożyć aplikację, użytkowników będzie trzeba to zrobić podczas próby połączenia się z siecią VPN. Aby dowiedzieć się, jak wdrażać aplikacje, zobacz [wdrażania aplikacji z System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

- Wdrażanie profilu sieci VPN, zgodnie z opisem w [sposobu wdrażania profili w programie System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  

