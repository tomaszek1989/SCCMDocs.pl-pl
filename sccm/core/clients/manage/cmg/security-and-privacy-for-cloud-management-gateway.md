---
title: CMG zabezpieczenia i prywatność
description: Więcej informacji na temat wskazówki i zalecenia dotyczące zabezpieczeń i prywatności z bramą zarządzania w chmurze.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 7304730b-b517-4c76-aadd-4cbd157dc971
ms.openlocfilehash: d07c30d6a1e4fd1314b6e69ac157577ae0163696
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="security-and-privacy-for-the-cloud-management-gateway"></a>Bezpieczeństwo i prywatność zarządzania bramy chmury

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera bezpieczeństwa i informacje o ochronie prywatności dla bramy zarządzania chmury programu Configuration Manager (CMG). Aby uzyskać więcej informacji, zobacz [planowanie brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).

## <a name="cmg-security-details"></a>Szczegóły zabezpieczeń CMG
- CMG akceptuje i zarządza połączeniami z CMG punkty połączenia. Używa wzajemnego uwierzytelniania protokołu SSL za pomocą certyfikatów i identyfikatorów połączeń.
- CMG akceptuje i przekazuje żądania klientów przy użyciu następujących metod:
    - Wstępnie uwierzytelnia połączeń przy użyciu wzajemnego protokołu SSL z certyfikatu uwierzytelniania klienta PKI lub usługi Azure AD. 
      - IIS na wystąpień maszyn wirtualnych CMG sprawdza ścieżka certyfikatu oparte na certyfikaty zaufanych głównych przekazane do CMG.
      - Usługi IIS w wystąpieniu maszyny Wirtualnej sprawdza także odwołanie certyfikatu klienta, jeśli włączone. Aby uzyskać więcej informacji, zobacz [publikowanie listy odwołania certyfikatów](#bkmk_crl).
    - Lista zaufania certyfikatów sprawdza głównego certyfikatu uwierzytelniania klienta. Wykonuje także tego samego weryfikacji jako punkt zarządzania dla klienta. Aby uzyskać więcej informacji, zobacz [Sprawdź wpisy listy zaufania certyfikatów witryny](#bkmk_ctl).
    - Weryfikuje i filtry żądań klientów (URL), aby sprawdzić, czy dowolnego punktu połączenia CMG można zrealizować żądania.  
    - Sprawdza długość zawartości dla każdego punktu końcowego, publikowania.
    - Używa działania okrężnego do punktów połączenia CMG Równoważenie obciążenia w tej samej lokacji.
- Punkt połączenia CMG korzysta z następujących metod:
    - Tworzy spójne połączenia HTTPS/TCP CMG wszystkie wystąpienia maszyny Wirtualnej. Nią sprawdzany i przechowuje te połączenia co minutę.
    - Używa wzajemnego uwierzytelniania SSL z CMG za pomocą certyfikatów.
    - Przekazuje żądania klienta oparte na mapowania adresów URL.
    - Raport stanu połączenia, aby wyświetlić stan usługi kondycji w konsoli.
    - Raporty dotyczące ruchu na punkt końcowy co pięć minut.

### <a name="configuration-manager-client-facing-roles"></a>Role po stronie klienta programu Configuration Manager
Punkt zarządzania aktualizacji punktu i oprogramowania punktów końcowych hosta w usługach IIS do obsługi żądań klientów. CMG nie zapewnia wszystkich wewnętrznych punktów końcowych. Każdy punkt końcowy opublikowane CMG ma mapowanie adresu URL.
  - Zewnętrzny adres URL jest ten, który klient używa do komunikacji z CMG.
  - Wewnętrzny adres URL jest punkt połączenia CMG używany do przekazywania żądań do wewnętrznego serwera.

#### <a name="url-mapping-example"></a>Przykładowe mapowanie adresu URL
Po włączeniu CMG ruchu w punkcie zarządzania programu Configuration Manager tworzy wewnętrzny zbiór mapowania adresów URL dla każdego serwera punktu zarządzania. Na przykład: ccm_system, ccm_incoming i sms_mp. Zewnętrzny adres URL punktu końcowego ccm_system punkt zarządzania może wyglądać tak:  
`https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System`  
Adres URL jest unikatowy dla każdego punktu zarządzania. Klient programu Configuration Manager następnie umieszcza nazwę punktu zarządzania z włączonym CMG internet listy punktów zarządzania. Ta nazwa wygląda następująco:  
`<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>`  
Lokacji automatycznie przekazuje wszystkie opublikowane zewnętrzne adresy URL do CMG. Takie zachowanie umożliwia CMG celu filtrowanie adresów URL. Wszystkie mapowania adresów URL są replikowane do CMG punktu połączenia. Następnie przekazuje komunikat do serwerów wewnętrznych, zgodnie z zewnętrznego adresu URL z żądania klienta.



## <a name="security-guidance-for-cmg"></a>Wskazówki dotyczące zabezpieczeń dla CMG


<a name="bkmk_crl"></a>

### <a name="publish-the-certificate-revocation-list"></a>Publikowanie listy odwołania certyfikatów

Publikowanie listy odwołania certyfikatów infrastruktury kluczy publicznych (CRL) dla klientów internetowych do uzyskania dostępu. W przypadku wdrażania CMG, przy użyciu infrastruktury kluczy publicznych, należy skonfigurować usługę, aby **sprawdzania odwołania certyfikatu klienta** na karcie Ustawienia. To ustawienie umożliwia skonfigurowanie usługi do listy odwołania opublikowanych certyfikatów (CRL). Aby uzyskać więcej informacji, zobacz [planowanie odwoływania certyfikatów PKI](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForCRLs).



<a name="bkmk_ctl"></a>

### <a name="review-entries-in-the-sites-certificate-trust-list"></a>Przejrzyj wpisy listy zaufania certyfikatów dla lokacji
<!--503739-->
Każda lokacja programu Configuration Manager zawiera listę zaufanych głównych urzędów certyfikacji, listy zaufania certyfikatów (CTL). Wyświetlanie i modyfikowanie listy, przejdź do obszaru roboczego Administracja, rozwiń węzeł Konfiguracja lokacji i wybierz lokacje. Wybierz lokację, a następnie kliknij polecenie Właściwości na Wstążce. Przejdź do karty komunikacja komputerów klienckich, a następnie kliknij przycisk **ustawić** w obszarze Zaufane główne urzędy certyfikacji.
 
Bardziej restrykcyjne CTL używana dla lokacji wraz z CMG, przy użyciu uwierzytelniania klienta PKI. W przeciwnym razie klienci z certyfikatów uwierzytelniania klienta wystawiony przez zaufany główny, który już istnieje w punkcie zarządzania automatycznie uznane za zaakceptowane dla rejestracji klienta.

Ten podzestaw zapewnia administratorom większą kontrolę zabezpieczeń. Listy CTL ogranicza serwera, aby akceptował tylko certyfikaty klienta, które zostały wystawione przez urzędy certyfikacji na liście CTL. Na przykład system Windows jest dostarczany z liczbą certyfikatów urzędu certyfikacji dobrze znanego certyfikacji innych firm, takich jak VeriSign i Thawte. Domyślnie komputer z uruchomionym zaufania usług IIS certyfikaty tym łańcucha tych dobrze znanych urzędów certyfikacji. Bez konfigurowania usług IIS listę CTL, dowolnego komputera z certyfikatem klienta wystawionym przez te urzędy certyfikacji będzie akceptowane jako prawidłowy klient programu Configuration Manager. Jeśli można skonfigurować w usługach IIS listy CTL, która nie zawiera tych urzędów certyfikacji, odrzucenie połączeń klienta, jeśli certyfikat te urzędy certyfikacji powiązane łańcuchem zależności. 


<!--486209-->


<!-- ## Privacy information for CMG -->


## <a name="next-steps"></a>Następne kroki

- [Planowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [Konfigurowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Często zadawane pytania dotyczące zarządzania bramy chmury](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Certyfikaty bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
