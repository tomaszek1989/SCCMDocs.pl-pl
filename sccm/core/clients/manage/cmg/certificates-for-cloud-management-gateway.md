---
title: Certyfikaty CMG
description: Więcej informacji na temat różnych certyfikatów cyfrowych do użycia z bramą zarządzania w chmurze.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 71eaa409-b955-45d6-8309-26bf3b3b0911
ms.openlocfilehash: 1c7adec8f8919736c61859791802a96766af31bb
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="certificates-for-the-cloud-management-gateway"></a>Certyfikaty dla bramy zarządzania w chmurze

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W zależności od scenariusza, który służy do zarządzania klientami przez internet z bramą zarządzania chmury (CMG), należy co najmniej jednego certyfikatu cyfrowego. Aby uzyskać więcej informacji o różnych scenariuszy, zobacz [plan brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).


## <a name="cmg-server-authentication-certificate"></a>Certyfikat uwierzytelniania serwera CMG

*Ten certyfikat jest wymagany we wszystkich scenariuszach.*

Ten certyfikat należy podać podczas tworzenia CMG w konsoli programu Configuration Manager.

CMG tworzy usługi protokołu HTTPS, do którego połączenia klientów internetowych. Serwer wymaga certyfikatu uwierzytelniania serwera do tworzenia bezpiecznego kanału. Zakupienie certyfikatu w tym celu przez publicznego dostawcę lub wystawić go z infrastruktury kluczy publicznych (PKI). Aby uzyskać więcej informacji, zobacz [CMG zaufany certyfikat główny do klientów](#cmg-trusted-root-certificate-to-clients).

 > [!TIP]
 > Tego certyfikatu wymaga globalnie unikatowej nazwy do identyfikowania usługi na platformie Azure. Przed wysłaniem żądania certyfikatu, upewnij się, że nazwa żądanej domeny platformy Azure jest unikatowa. Na przykład *GraniteFalls.CloudApp.Net*. Zaloguj się do [portalu Microsoft Azure](https://portal.azure.com). Kliknij przycisk **Utwórz zasób**, wybierz pozycję **obliczeniowe** kategorii, następnie kliknij przycisk **usługi w chmurze**. W **nazwy DNS** na przykład wpisz żądany prefiks *GraniteFalls*. Interfejs odzwierciedla czy nazwa domeny jest niedostępna lub jest już używany przez inną usługę. Tworzenie usługi w portalu, nie tylko ten proces służy do sprawdzania dostępności nazwy. 
  
 > [!NOTE]
 > Począwszy od wersji 1802 certyfikatu uwierzytelniania serwera CMG obsługuje symboli wieloznacznych. Niektórych urzędów certyfikacji wystawiać certyfikaty przy użyciu symbolu wieloznacznego w przypadku nazwy hosta. Na przykład  **\*. contoso.com**. Niektóre firmy używają certyfikatów z symbolami wieloznacznymi uprościć ich infrastruktury kluczy publicznych i obniżenie kosztów obsługi.
 <!--491233-->


### <a name="cmg-trusted-root-certificate-to-clients"></a>CMG zaufany certyfikat główny dla klientów

Klienci muszą ufać CMG certyfikatu uwierzytelniania serwera. Istnieją dwie metody w celu tego zaufania:
- Użyj certyfikatu z dostawcy publicznego i globalnie zaufanych certyfikatów. Na przykład, między innymi VeriSign i Thawte. Klienci systemu Windows obejmują zaufane główne urzędy certyfikacji (CA) z usług tych dostawców. Za pomocą certyfikatu uwierzytelniania serwera wydany przez jedną z tych dostawców, klienci automatycznie ufać go. 
- Użyć certyfikatu wydanego przez urząd certyfikacji przedsiębiorstwa z infrastruktury kluczy publicznych (PKI). Większości wdrożeń infrastruktury kluczy publicznych przedsiębiorstwa Dodaj zaufanych głównych urzędów certyfikacji do klientów systemu Windows. Na przykład za pomocą usług certyfikatów Active Directory przy użyciu zasad grupy. Jeśli wydawane serwera CMG uwierzytelniania certyfikatu z urzędu certyfikacji, który klient automatycznie niezaufane musisz dodać certyfikat zaufanego głównego urzędu certyfikacji do klientów internetowych.
    - Umożliwia także profili certyfikatów programu Configuration Manager, aby udostępnić certyfikaty na klientach. Aby uzyskać więcej informacji, zobacz [wprowadzenie do profilów certyfikatów](/sccm/protect/deploy-use/introduction-to-certificate-profiles).

### <a name="server-authentication-certificate-issued-by-public-provider"></a>Certyfikat uwierzytelniania serwera wydanego przez publiczny dostawca

Korzystając z tej metody, klienci automatycznie ufać certyfikatowi i nie trzeba samodzielnie utworzyć niestandardowego certyfikatu. Configuration Manager tworzy usługę w systemie Azure z domeną cloudapp.net. Dostawca certyfikatu publicznego nie mogą wystawiać do Ciebie certyfikat o takiej nazwie. Aby utworzyć DNS alias, należy wykonać poniższe czynności:

1. Utwórz rekord nazwę kanoniczną (CNAME) w publicznym systemie DNS w organizacji. Ten rekord tworzy alias dla CMG do przyjazną nazwę używaną w publicznych certyfikatów.
Na przykład Contoso nazwy ich CMG **GraniteFalls**, które stają się **GraniteFalls.CloudApp.Net** na platformie Azure. W firmy Contoso publicznego contoso.com obszar nazw DNS, administrator usługi DNS tworzy nowy rekord CNAME dla **GraniteFalls.Contoso.com** dla nazwy hosta rzeczywistych **GraniteFalls.CloudApp.net**.
2. Żądanie certyfikatu uwierzytelniania serwera z publicznego dostawcę przy użyciu nazwa pospolita (CN) aliasu CNAME.
Na przykład firma Contoso używa **GraniteFalls.Contoso.com** CN certyfikatu.
3. Utwórz CMG w konsoli programu Configuration Manager przy użyciu tego certyfikatu. Na **ustawienia** strony kreatora tworzenia bramy zarządzania chmury: 
    - Po dodaniu certyfikatu serwera dla tej usługi w chmurze (z **plik certyfikatu**), Kreator wyodrębnia nazwy hosta z certyfikatu CN nazwy usługi. 
    - Następnie dołącza tej nazwy hosta do **cloudapp.net**, lub **usgovcloudapp.net** chmury Azure instytucji rządowych Stanów Zjednoczonych, jak nazwa FQDN usługi można utworzyć usługi na platformie Azure.
    - Na przykład gdy Contoso tworzy CMG, programu Configuration Manager wyodrębnia nazwa hosta **GraniteFalls** z nazwa Pospolita certyfikatu. Platforma Azure tworzy rzeczywiste usługi jako **GraniteFalls.CloudApp.net**.

### <a name="server-authentication-certificate-issued-from-enterprise-pki"></a>Certyfikat uwierzytelniania serwera wydanego Enterprise PKI

Tworzenie niestandardowego certyfikatu SSL dla CMG takie same jak dla punktu dystrybucji chmury. Postępuj zgodnie z instrukcjami dotyczącymi [wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) , ale inaczej wykonaj następujące czynności:

- Podczas żądania certyfikatu serwera sieci web niestandardowe, należy podać nazwę FQDN dla nazwa pospolita certyfikatu. Dla przy użyciu CMG w chmurze publicznej systemu Azure, użyj nazwy, która kończy się **cloudapp.net**, lub **usgovcloudapp.net** chmury Azure instytucji rządowych Stanów Zjednoczonych.



## <a name="azure-management-certificate"></a>Certyfikat zarządzania platformy Azure

*Ten certyfikat jest wymagany w przypadku wdrożeń klasycznych usługi. Nie jest wymagana w przypadku wdrożeń usługi Azure Resource Manager.*

Ten certyfikat w portalu Azure, należy podać podczas tworzenia CMG w konsoli programu Configuration Manager.

Aby utworzyć CMG na platformie Azure, musi najpierw zostać uwierzytelnione subskrypcji platformy Azure punktu połączenia z usługą Configuration Manager. Korzystając z wdrożenia usługi klasycznego, używa certyfikatu zarządzania platformy Azure dla tego uwierzytelnienia. Administrator usługi Azure przekazuje ten certyfikat do subskrypcji. Podczas tworzenia CMG w konsoli programu Configuration Manager, należy podać ten certyfikat.

Aby uzyskać więcej informacji oraz instrukcje przekazać certyfikat zarządzania zobacz następujące artykuły w dokumentacji platformy Azure:

- [Usługi w chmurze i certyfikaty zarządzania.](/azure/cloud-services/cloud-services-certs-create#what-are-management-certificates)

- [Przekaż certyfikat zarządzania usługi Azure](/azure/azure-api-management-certs)

> [!IMPORTANT]
> Upewnij się skopiować identyfikator subskrypcji skojarzonych z certyfikatem zarządzania. Służy do tworzenia CMG w konsoli programu Configuration Manager.



## <a name="client-authentication-certificate"></a>Certyfikat uwierzytelniania klienta

*Ten certyfikat jest wymagany dla klientów internetowych systemem Windows 7, Windows 8.1 i urządzeń z systemem Windows 10 nie są przyłączone do usługi Azure Active Directory (Azure AD). Jest również wymagany w punkcie połączenia CMG. Nie jest wymagane dla klientów systemu Windows 10 dołączone do usługi Azure AD.*

Klienci używają tego certyfikatu do uwierzytelniania za pomocą CMG. Urządzenia systemu Windows 10 hybrydowej lub chmury przyłączonych do domeny, nie wymagają tego certyfikatu, ponieważ używają usługi Azure AD do uwierzytelniania.

Udostępnić ten certyfikat poza kontekstem programu Configuration Manager. Na przykład użyć usług certyfikatów Active Directory i zasad grupy do wystawiania certyfikatów uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [wdrażanie certyfikatu klienta dla komputerów z systemem Windows](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).


### <a name="client-trusted-root-certificate-to-cmg"></a>Klienta zaufanego certyfikatu głównego na CMG

*Ten certyfikat jest wymagany w przypadku korzystania z certyfikatów uwierzytelniania klienta. Gdy wszyscy klienci używają usługi Azure AD do uwierzytelniania, ten certyfikat nie jest wymagana.* 

Ten certyfikat należy podać podczas tworzenia CMG w konsoli programu Configuration Manager.

CMG muszą ufać certyfikatów uwierzytelniania klienta. Aby osiągnąć tego zaufania, podaj łańcucha certyfikatów zaufanych certyfikatów głównych. Możesz określić dwa zaufanych głównych urzędów certyfikacji i cztery pośrednie urzędy certyfikacji (podrzędnego). 


#### <a name="export-the-client-certificates-trusted-root"></a>Eksportowanie certyfikatu klienta zaufanego głównego

Po wystawieniu certyfikatu uwierzytelniania klienta, na komputerze, aby wyeksportować zaufanych głównych należy użyć tego procesu na tym komputerze.

1.  Otwieranie Start menu. Typu "Uruchom", aby otworzyć okno Uruchamianie. Otwórz **mmc**. 

2.  Z menu Plik wybierz **Dodaj/Usuń przystawkę...** .

3.  W oknie dialogowym Dodawanie lub usuwanie przystawek wybierz **certyfikaty**, następnie kliknij przycisk **Dodaj**. 
    a. W oknie dialogowym w przystawce Certyfikaty wybierz **konto komputera**, następnie kliknij przycisk **dalej**. 
    b. W oknie dialogowym Wybierz komputer, wybierz **komputera lokalnego**, następnie kliknij przycisk **Zakończ**. 
    c. W oknie dialogowym Dodawanie lub usuwanie przystawek kliknij **OK**.

4.  Rozwiń węzeł **certyfikaty**, rozwiń węzeł **osobistych**i wybierz **certyfikaty**.

5.  Wybierz certyfikat, którego zamierzony cel jest **uwierzytelnianie klienta**. 
    a. W menu Akcja wybierz **Otwórz**. 
    b. Przełącz się do **ścieżki certyfikacji** c kartę. Wybierz certyfikat dalej zapasowej łańcucha, a następnie kliknij przycisk **Wyświetl certyfikat**.

6.  Okno dialogowe ten nowy certyfikat przełącznika do **szczegóły** kartę. Kliknij przycisk **Kopiuj do pliku...** .

7.  Ukończenie Kreatora eksportu certyfikatów przy użyciu domyślnego formatu certyfikatu **certyfikat x.509 szyfrowany binarnie algorytmem DER (. CER)**. Upewnij się, zanotuj nazwę i lokalizację wyeksportowanego certyfikatu.

8. Wyeksportuj wszystkie certyfikaty do ścieżki certyfikacji oryginalnego certyfikatu uwierzytelniania klienta. Zanotuj wyeksportowanego certyfikatów, które są pośrednie urzędy certyfikacji, a te, które są zaufane główne urzędy certyfikacji.



## <a name="enable-management-point-for-https"></a>Włącz punkt zarządzania dla protokołu HTTPS

*Wymagania dotyczące certyfikatów*
- W wersjach 1706 lub 1710, podczas zarządzania klientami tradycyjnych z lokalnymi tożsamość za pomocą certyfikatu uwierzytelniania klienta, ten certyfikat jest zalecane, ale nie jest wymagane.
- W wersji 1710 podczas zarządzania klientami systemu Windows 10 przyłączonych do usługi Azure AD, ten certyfikat jest wymagany dla punktów zarządzania. 
- Począwszy od wersji 1802 ten certyfikat jest wymagany we wszystkich scenariuszach. 

Udostępnić ten certyfikat poza kontekstem programu Configuration Manager. Na przykład użyć usług certyfikatów Active Directory i zasad grupy do wystawiania certyfikatu serwera sieci web. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące certyfikatu PKI](/sccm/core/plan-design/network/pki-certificate-requirements) i [wdrażania certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).



## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Często zadawane pytania dotyczące zarządzania bramy chmury](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Bezpieczeństwo i prywatność brama zarządzania w chmurze](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
