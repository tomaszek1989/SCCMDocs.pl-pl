---
title: Tworzenie roli systemu lokacji punktu programu Endpoint Protection
titleSuffix: Configuration Manager
description: "Dowiedz się, jak skonfigurować program Endpoint Protection do zarządzania zabezpieczeniami i złośliwego oprogramowania na komputerach klienckich programu Configuration Manager."
defintion: 
definition: 
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: a52f01ad365ca637b2bfda51657d0294e1bf268f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Tworzenie roli systemu lokacji punktu programu Endpoint Protection

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Rola systemu lokacji punktu ochrony punktu końcowego musi być zainstalowana, aby można było używać programu Endpoint Protection. Ta rola musi być zainstalowana tylko na serwerze systemu lokacji oraz na najwyższym poziomie w hierarchii centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.

 Użyj jednej z poniższych procedur w zależności od tego, czy chcesz zainstalować nowy serwer systemu lokacji dla programu Endpoint Protection lub użyć istniejącego serwera systemu lokacji:
 - [Zainstaluj na nowy serwer systemu lokacji](#new-site-system-server)
 - [Zainstaluj na istniejącym serwerze systemu lokacji](#existing-site-system-server)

> [!IMPORTANT]
>  Po zainstalowaniu punktu programu Endpoint Protection, klient Endpoint Protection jest zainstalowany na serwerze hostującym punkt programu Endpoint Protection. Usługi i możliwości skanowania są wyłączane na tym kliencie, aby umożliwić współistnienie z każdym istniejącym rozwiązaniem chroniącym przed złośliwym kodem, które zostało zainstalowane na serwerze. Jeśli później włączyć tego serwera na potrzeby zarządzania przez program Endpoint Protection i wybierz opcję usuwania wszelkich rozwiązań innych firm chroniące przed złośliwym kodem, produkt innej firmy nie zostaną usunięte. Trzeba będzie odinstalować go ręcznie.

## <a name="new-site-system-server"></a>Nowy serwer systemu lokacji

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Serwery i role systemu lokacji**.

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz serwer systemu lokacji**.

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Wybór roli systemu** wybierz na liście dostępnych ról element **Punkt programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

6.  Na stronie **Endpoint Protection** zaznacz pole wyboru **Akceptuję postanowienia licencyjne programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

    > [!IMPORTANT]
    >  Nie możesz użyć programu Endpoint Protection w programie Configuration Manager, jeśli nie akceptujesz postanowień licencyjnych.

7.  Na **usługi w chmurze ochrony** wybierz poziom informacji, które chcesz wysyłać do firmy Microsoft, aby pomóc w tworzeniu nowych definicji, a następnie kliknij przycisk **dalej**.

    > [!NOTE]
    >  Ta opcja powoduje skonfigurowanie ustawienia usługi ochrony chmury (wcześniej znane jako Microsoft Active Protection Service lub mapy), które domyślnie są używane. Następnie możesz skonfigurować niestandardowe ustawienia dla każdej utworzonej zasady ochrony przed złośliwym kodem. Dołącz do usługi ochrony chmury, aby pomóc chronić komputery poprzez dostarczanie Microsoft przykłady złośliwego oprogramowania, które mogą pomóc firmie Microsoft na aktualizowanie definicji ochrony przed złośliwym oprogramowaniem. Ponadto po dołączeniu do usługi w chmurze ochrony klienta programu Endpoint Protection można użyć usługi podpisu dynamicznego do pobierania nowych definicji przed ich opublikowaniem w witrynie Windows Update. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Ukończ pracę kreatora.


## <a name="existing-site-system-server"></a>Istniejący serwer systemu lokacji

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, kliknij przycisk **serwery i role systemu lokacji**, a następnie wybierz serwer, który ma być używany dla programu Endpoint Protection.

3.  Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**.

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Wybór roli systemu** wybierz na liście dostępnych ról element **Punkt programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

6.  Na stronie **Endpoint Protection** zaznacz pole wyboru **Akceptuję postanowienia licencyjne programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

    > [!IMPORTANT]
    >  Nie możesz użyć programu Endpoint Protection w programie Configuration Manager, jeśli nie akceptujesz postanowień licencyjnych.

7.  Na **usługi w chmurze ochrony** wybierz poziom informacji, które chcesz wysyłać do firmy Microsoft, aby pomóc w tworzeniu nowych definicji, a następnie kliknij przycisk **dalej**.

    > [!NOTE]
    >  Ta opcja konfiguruje ustawienia ochrony usługa w chmurze (wcześniej znane jako mapy) używanych domyślnie. Następnie możesz skonfigurować niestandardowe ustawienia dla każdej skonfigurowanej zasady ochrony przed złośliwym kodem. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Ukończ pracę kreatora.
