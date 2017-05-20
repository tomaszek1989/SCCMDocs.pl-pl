---
title: "Utwórz rolę systemu lokacji punktu Endpoint Protection | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować program Endpoint Protection do zarządzania zabezpieczeniami i złośliwym oprogramowaniem na komputerach klienckich programu Configuration Manager."
defintion: 
definition: 
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: 6e717bcbe5ef8c3f2efa717d0cebb9e675e7c127
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Utwórz rolę systemu lokacji punktu ochrony punktu końcowego

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Rola systemu lokacji punktu ochrony punktu końcowego musi być zainstalowana, aby można było używać programu Endpoint Protection. Ta rola musi być zainstalowana tylko na serwerze systemu lokacji oraz na najwyższym poziomie w hierarchii centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.

 Użyj jednej z następujących procedur, w zależności od tego, czy chcesz zainstalować nowy serwer systemu lokacji programu Endpoint Protection lub użyj istniejącego serwera systemu lokacji:
 - [Zainstaluj na serwerze systemu lokacji](#new-site-system-server)
 - [Zainstaluj na istniejącym serwerze systemu lokacji](#existing-site-system-server)

> [!IMPORTANT]
>  Po zainstalowaniu ochrony punktu końcowego klienta Endpoint Protection jest zainstalowany na serwerze obsługującym ochrony punktu końcowego. Usługi i możliwości skanowania są wyłączane na tym kliencie, aby umożliwić współistnienie z każdym istniejącym rozwiązaniem chroniącym przed złośliwym kodem, które zostało zainstalowane na serwerze. Jeśli później włączyć tego serwera na potrzeby zarządzania przez program Endpoint Protection i wybierz opcję, aby usunąć wszelkie rozwiązania innych firm chroniące przed złośliwym kodem, produktu innej firmy nie zostaną usunięte. Trzeba będzie odinstalować go ręcznie.

## <a name="new-site-system-server"></a>Nowy serwer systemu lokacji

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Serwery i role systemu lokacji**.

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz serwer systemu lokacji**.

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Wybór roli systemu** wybierz na liście dostępnych ról element **Punkt programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

6.  Na stronie **Endpoint Protection** zaznacz pole wyboru **Akceptuję postanowienia licencyjne programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

    > [!IMPORTANT]
    >  Nie możesz użyć Endpoint Protection w programie Configuration Manager, jeśli nie akceptujesz postanowień licencyjnych.

7.  Na **usługi ochrony chmury** wybierz poziom danych, które chcesz wysłać do firmy Microsoft, aby tworzyć nowe definicje, a następnie kliknij przycisk **dalej**.

    > [!NOTE]
    >  Ta opcja konfiguruje ustawienia usługi ochrony chmury (wcześniej znane jako usługa Microsoft Active Protection lub MAPS), które domyślnie są używane. Następnie możesz skonfigurować niestandardowe ustawienia dla każdej utworzonej zasady ochrony przed złośliwym kodem. Dołącz do usługi ochrony chmury, aby chronić komputery poprzez dostarczanie przykłady złośliwego oprogramowania, które mogą pomóc firmie Microsoft do aktualizacji definicji ochrony przed złośliwym oprogramowaniem firmy Microsoft. Ponadto po dołączeniu usługi ochrony chmury klienta programu Endpoint Protection można użyć usługi podpisu dynamiczne pobrać nowe definicje przed ich opublikowaniem do usługi Windows Update. Aby uzyskać więcej informacji, zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Ukończ pracę kreatora.


## <a name="existing-site-system-server"></a>Istniejący serwer systemu lokacji

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, kliknij przycisk **serwery i role systemu lokacji**, a następnie wybierz serwer, którego chcesz używać do ochrony punktu końcowego.

3.  Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj role systemu lokacji**.

4.  Na stronie **Ogólne** określ ustawienia ogólne systemu lokacji, a następnie kliknij przycisk **Dalej**.

5.  Na stronie **Wybór roli systemu** wybierz na liście dostępnych ról element **Punkt programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

6.  Na stronie **Endpoint Protection** zaznacz pole wyboru **Akceptuję postanowienia licencyjne programu Endpoint Protection** , a następnie kliknij przycisk **Dalej**.

    > [!IMPORTANT]
    >  Nie możesz użyć Endpoint Protection w programie Configuration Manager, jeśli nie akceptujesz postanowień licencyjnych.

7.  Na **usługi ochrony chmury** wybierz poziom danych, które chcesz wysłać do firmy Microsoft, aby tworzyć nowe definicje, a następnie kliknij przycisk **dalej**.

    > [!NOTE]
    >  Ta opcja konfiguruje ustawienia ochrony usługa w chmurze (wcześniej znane jako mapy) używanych domyślnie. Następnie możesz skonfigurować niestandardowe ustawienia dla każdej skonfigurowanej zasady ochrony przed złośliwym kodem. Aby uzyskać więcej informacji, zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Ukończ pracę kreatora.

