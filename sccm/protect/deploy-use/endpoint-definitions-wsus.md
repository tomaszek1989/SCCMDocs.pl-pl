---
title: "Definicje złośliwego oprogramowania ochrony punktu końcowego programu WSUS | Dokumentacja firmy Microsoft"
definition: Learn how to configure Windows Server Updates Services to auto-approve definition updates.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a34d9401-83e4-471d-8e23-b8042fc11c90
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 0e606b25065fa25c782d1b5f3fbf164e60733353
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-windows-server-update-services-wsus-for-configuration-manager"></a>Włącz Endpoint Protection definicji złośliwego oprogramowania pobrać z systemu Windows Server Update Services (WSUS) dla programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Jeśli używasz programu WSUS do aktualizowania definicji oprogramowania chroniącego przed złośliwym kodem na bieżąco, możesz skonfigurować go do automatycznego zatwierdzania aktualizacji definicji. Korzystania z aktualizacji oprogramowania programu Configuration Manager jest to zalecana metoda aktualności definicje, można również skonfigurować WSUS jako metody umożliwiające użytkownikom ręcznie zainicjować aktualizacji definicji. Poniższe procedury służą do konfigurowania programu WSUS jako źródła aktualizacji definicji.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-configuration-manager-software-updates"></a>Aby zsynchronizować aktualizacji definicji programu Endpoint Protection w aktualizacji oprogramowania programu Configuration Manager

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.

3.  Wybierz lokację, która zawiera punkt aktualizacji oprogramowania. W grupie **Ustawienia** kliknij pozycję **Skonfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**.

4.  Na karcie **Klasyfikacje** okna dialogowego **Właściwości składnika punktu aktualizacji oprogramowania** zaznacz pole wyboru **Aktualizacje definicji** .

5.  Określ **produkty** aktualizowane przy użyciu programu WSUS:

    -   W systemie Windows 8.1 i starszych wersjach na karcie **Produkty** okna dialogowego **Właściwości składnika punktu aktualizacji oprogramowania** zaznacz pole wyboru **Forefront Endpoint Protection 2010** .

    -   W systemie Windows 10 i nowszych wersjach na karcie **Produkty** okna dialogowego **Właściwości składnika punktu aktualizacji oprogramowania** zaznacz pola wyboru **Windows Defender** oraz **Windows Technical Preview 2** .

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości składnika punktu aktualizacji oprogramowania** .

 Poniższa procedura umożliwia skonfigurowanie aktualizacji programu Endpoint Protection, gdy serwer programu WSUS nie jest zintegrowana w środowisku programu Configuration Manager.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus"></a>Aby zsynchronizować aktualizacje definicji dla programu Endpoint Protection w autonomicznym programie WSUS

1.  W konsoli administracyjnej programu WSUS rozwiń węzeł **Komputery**, kliknij pozycję **Opcje**, a następnie kliknij pozycję **Produkty i klasyfikacje**.

2.  Określ **produkty** aktualizowane przy użyciu programu WSUS:

    -   W systemie Windows 8.1 i starszych wersjach na karcie **Produkty** okna dialogowego **Właściwości składnika punktu aktualizacji oprogramowania** zaznacz pole wyboru **Forefront Endpoint Protection 2010** .

    -   W systemie Windows 10 i nowszych wersjach na karcie **Produkty** okna dialogowego **Właściwości składnika punktu aktualizacji oprogramowania** zaznacz pola wyboru **Windows Defender** oraz **Windows Technical Preview 2** .

3.  Na karcie **Klasyfikacje** okna dialogowego **Produkty i klasyfikacje** zaznacz pola wyboru **Aktualizacje definicji** i **Aktualizacje** .

## <a name="approving-definition-updates"></a>Zatwierdzanie aktualizacji definicji
 Aktualizacje definicji ochrony punktu końcowego musi być zatwierdzony i pobrane na serwer programu WSUS przed są oferowane klientów żądających listę dostępnych aktualizacji. Klienci nawiązują połączenie z serwerem programu WSUS w celu wyszukania dostępnych aktualizacji, a następnie żądają najnowszych zatwierdzonych aktualizacji definicji.

### <a name="to-approve-definitions-and-updates-in-wsus"></a>Aby zatwierdzić definicje i aktualizacje w programie WSUS

1.  W konsoli administracyjnej programu WSUS kliknij pozycję **Aktualizacje**, a następnie kliknij pozycję **Wszystkie aktualizacje** lub klasyfikację aktualizacji do zatwierdzenia.

2.  Na liście aktualizacji kliknij prawym przyciskiem myszy aktualizację lub aktualizacje do zatwierdzenia na potrzeby instalacji, a następnie kliknij pozycję **Zatwierdź**.

3.  W oknie dialogowym **Zatwierdzanie aktualizacji** wybierz grupę komputerów, dla której chcesz zatwierdzić aktualizacje, a następnie kliknij pozycję **Zatwierdzone do instalacji**.

 Oprócz ręcznego zatwierdzania można również ustawić regułę automatycznego zatwierdzania aktualizacji definicji i aktualizuje Endpoint Protection. Konfigurowania programu WSUS do automatycznego zatwierdzania aktualizacji definicji programu Endpoint Protection pobrane przez program WSUS.

### <a name="to-configure-an-automatic-approval-rule"></a>Aby skonfigurować regułę zatwierdzania automatycznego

1.  W konsoli administracyjnej programu WSUS kliknij pozycję **Opcje**, a następnie kliknij pozycję **Zatwierdzenia automatyczne**.

2.  Na karcie **Reguły aktualizacji** kliknij pozycję **Nowa reguła**.

3.  W **Dodaj regułę** okna dialogowego **krok 1: Wybierz właściwości**, wybierz opcję **gdy aktualizacja jest w określonej klasyfikacji** pole wyboru.

4.  W obszarze **krok 2: Edycja właściwości**, kliknij przycisk **klauzuli**.

5.  Usuń zaznaczenia wszystkich pól wyboru z wyjątkiem pola **Aktualizacje definicji**, a następnie kliknij przycisk **OK**.

6.  W **Dodaj regułę** okna dialogowego **krok 1: Wybierz właściwości**, wybierz opcję **gdy aktualizacja jest w określonym produktem** pole wyboru.

7.  W obszarze **krok 2: Edycja właściwości**, kliknij przycisk **dowolnego produktu**.

8.  Usuń zaznaczenia wszystkich pól wyboru z wyjątkiem **Forefront Endpoint Protection** w przypadku systemu Windows 8.1 i starszych wersji lub **Windows Defender** w przypadku systemu Windows 10 i nowszych wersji, a następnie kliknij przycisk **OK**.

9. W obszarze **krok 3: Określ nazwę**, wprowadź nazwę reguły, a następnie kliknij przycisk **OK**.

10. W oknie dialogowym **Zatwierdzenia automatyczne** zaznacz pole wyboru nowo utworzonej reguły, a następnie kliknij przycisk **Uruchom regułę**.

> [!NOTE]
>  Aby zmaksymalizować wydajność na komputerach klienckich i serwerach programu WSUS, odrzuć stare aktualizacje definicji. W tym celu możesz skonfigurować automatyczne zatwierdzanie poprawek i automatyczne odrzucanie wygasłych aktualizacji. Aby uzyskać więcej informacji, zobacz [artykuł 938947 w bazie wiedzy Microsoft Knowledge Base](http://go.microsoft.com/fwlink/p/?LinkId=204078).

> [!div class="button"]
[Następny krok >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Ponownie >](endpoint-configure-alerts.md)

