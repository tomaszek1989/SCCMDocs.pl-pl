---
title: 'Tworzenie profilów sieci VPN '
titleSuffix: Configuration Manager
description: Dowiedz się, jak utworzyć profile sieci VPN w programie System Center Configuration Manager.
ms.custom: ''
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: ''
author: lleonard-msft
caps.handback.revision: ''
ms.author: alleonar
ms.manager: angrobe
ms.openlocfilehash: 21fc286cdcc05244e1895ded5623d346e6cb8ebe
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2018
---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>Jak tworzyć profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Dostępne dla platform urządzeń różne typy połączeń są opisane w [profilów sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

Dla połączeń sieci VPN innych firm należy przeprowadzić dystrybucję aplikacji sieci VPN przed wdrożeniem profilu sieci VPN. Jeśli nie można wdrożyć aplikacji, użytkownicy otrzymują monit Aby to zrobić, podczas próby nawiązania połączenia z siecią VPN. Aby dowiedzieć się, jak wdrażać aplikacje, zobacz [wdrażania aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

### <a name="create-a-vpn-profile"></a>Tworzenie profilu sieci VPN   

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **ustawień zgodności** > **dostęp do zasobów firmy** > **profilów sieci VPN**.  

2.  Na **Home** karcie **Utwórz** grupy, wybierz **Tworzenie profilu sieci VPN**.  


3.  Zakończenie **ogólne** strony. . Weź pod uwagę następujące kwestie:  

    - Wybierz odpowiednie **platformy**.

       - W przypadku wybrania platformy Windows 8.1, masz możliwość wybrania **Importuj istniejący element profilu VPN z pliku** Aby zaimportować informacje o profilu sieci VPN, który został wyeksportowany do pliku XML.

    - Nie używaj znaków \\/ :*?&lt; >&#124;, lub spacja w nazwie profilu sieci VPN. Następujące znaki nie są obsługiwane przez profil sieci VPN w systemie Windows Server.  


4.  Na **połączenia** określ:  

    -   **Typ połączenia**: Wybierz typ połączenia VPN. Można wybrać typy połączeń w poniższej tabeli.  

    -   **Lista serwerów**: Dodaj nowy serwer do użycia na potrzeby połączenia sieci VPN. W zależności od typu połączenia można dodać jeden lub więcej serwerów sieci VPN i określić domyślny serwer.  

        > [!NOTE]  
        >  Urządzenia z systemem iOS nie umożliwiają użycia wielu serwerów sieci VPN. Jeśli skonfigurowano wiele serwerów sieci VPN, a następnie wdrożono profil sieci VPN na urządzeniu z systemem iOS, możliwe będzie użycie tylko serwera domyślnego.  

     Ta tabela zawiera opcje typy połączeń. Zapoznaj się z dokumentacją serwera VPN, aby uzyskać więcej informacji.

| &nbsp;&nbsp;Option&nbsp;&nbsp; | Więcej informacji | &nbsp;&nbsp;Połączenie&nbsp;typu&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**Obszar**     |Obszar uwierzytelniania, którego chcesz używać. Obszar uwierzytelniania to grupa zasobów uwierzytelniania używana przez typ połączenia Pulse Secure.|Pulse Secure|    
|**Rola**        |Rola użytkownika, który ma dostęp do tego połączenia. |Pulse Secure|  
|**Grupa lub domena logowania** |Nazwa logowania grupy lub domeny, który chcesz nawiązać połączenie.|Dell SonicWALL Mobile Connect|  
|**Odcisk palca**  |Ciąg, na przykład "Contoso kod odcisku palca", który będzie używany do sprawdzenia, czy serwer sieci VPN jest zaufany.<br /><br /> Odcisk palca można:<br /><br /> — Wysłać do klienta, który będzie wówczas traktował każdy serwer przedstawiający ten sam odcisk palca podczas połączenia jako zaufany.<br /><br /> — Jeśli urządzenie nie otrzymało jeszcze odcisku palca go będzie użytkownikowi monit dotyczący zaufania serwerowi sieci VPN jest nawiązywane połączenie, zawierający odcisk palca (użytkownik samodzielnie weryfikuje odcisk palca i wybiera **zaufania** nawiązać).|Check Point Mobile VPN|  
|**Wyślij cały ruch sieciowy przez połączenie VPN** |Jeśli ta opcja nie została wybrana, można określić dodatkowe trasy dla połączenia (w przypadku typów połączeń **Microsoft SSL (SSTP)**, **Microsoft Automatic**, **IKEv2**, **PPTP** i **L2TP** ), czyli tzw. tunelowanie podzielone lub tunelowanie VPN.<br /><br /> Tylko połączenia z siecią firmową są przesyłane przez tunel VPN. Tunelowanie VPN nie jest używane w przypadku łączenia się z zasobami przez Internet. |Wszystkie|  
|**Sufiks DNS zależny od połączenia** |Sufiks systemu nazw domen (DNS, Domain Name System) konkretnego połączenia dla połączenia.|— Microsoft SSL (SSTP)<br /><br /> — Tryb automatyczny firmy Microsoft<br /><br /> — IKEv2<br /><br /> — PPTP<br /><br /> — L2TP|  
|**Obejście sieci VPN po podłączeniu do firmowej sieci Wi-Fi**  |Połączenia sieci VPN nie będzie używany, gdy urządzenie jest połączone z firmową siecią Wi-Fi.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN<br /><br /> — Microsoft SSL (SSTP)<br /><br /> — Tryb automatyczny firmy Microsoft<br /><br /> — IKEv2<br /><br /> — L2TP|  
|**Obejdź sieć VPN w przypadku połączenia z domową siecią Wi-Fi**  |Połączenia sieci VPN nie będzie używany, gdy urządzenie jest połączone z domową siecią Wi-Fi.|Wszystkie|  
|**Dla sieci VPN aplikacji (system iOS 7 i nowsze, system Mac OS X 10.9 i nowsze)** |Powiązać to połączenie VPN z aplikacją dla systemu iOS, tak aby połączenie było otwierane w momencie uruchomienia aplikacji. Podczas wdrażania profilu sieci VPN możesz skojarzyć go z aplikacją.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN|  
|**Niestandardowy plik XML (opcja)** |Określenie niestandardowych poleceń XML konfiguracji połączenia sieci VPN.<br /><br /> Przykłady:<br /><br /> **Pulse Secure**:<br /><br /> **&lt;pulse-schema><br /> &nbsp; &lt;isSingleSignOnCredential>true&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema>**<br /><br /> **CheckPoint Mobile VPN**:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; port="443" name="CheckPointSelfhost" <br /> &nbsp; sso="true" <br /> &nbsp; debug="3"<br />/>**<br /><br /> **Dell SonicWALL Mobile Connect**:<br /><br /> **&lt;MobileConnect\><br />&nbsp; &nbsp; &lt;Compression\>false&lt;/Compression\><br />&nbsp; &nbsp; &lt;debugLogging\>True&lt;/debugLogging\><br />&nbsp; &nbsp; &lt;packetCapture\>False&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> **F5 Edge Client**:<br /><br /> **&lt;f5-vpn-conf>&lt;single-sign-on-credential>&lt;/f5-vpn-conf>**<br /><br /> Więcej informacji na temat tworzenia niestandardowych poleceń XML zawiera dokumentacja sieci VPN dostarczana przez producentów.|— Cisco AnyConnect<br /><br /> — Pulse Secure<br /><br /> — F5 Edge Client<br /><br /> — Dell SonicWALL Mobile Connect<br /><br /> — Check Point Mobile VPN|  

> [!NOTE]  
>  Aby uzyskać informacje dotyczące tworzenia profilów sieci VPN dla urządzeń przenośnych, zobacz [tworzenie profilów sieci VPN](../../mdm/deploy-use/create-vpn-profiles.md)  

Ukończ pracę kreatora. Nowy profil sieci VPN zostanie wyświetlony w węźle **Profile VPN** w obszarze roboczym **Zasoby i zgodność** .

### <a name="next-steps"></a>Następne kroki

- Dla połączeń sieci VPN innych firm należy przeprowadzić dystrybucję aplikacji sieci VPN przed wdrożeniem profilu sieci VPN. Jeśli nie można wdrożyć aplikacji, użytkownicy otrzymują monit Aby to zrobić, podczas próby nawiązania połączenia z siecią VPN. Aby dowiedzieć się, jak wdrażać aplikacje, zobacz [wdrażania aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

- Wdrażanie profilu sieci VPN, zgodnie z opisem w [sposobu wdrażania profili w programie System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  
