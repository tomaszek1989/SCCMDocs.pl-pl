---
title: Certyfikaty i zabezpieczenia
titleSuffix: Configuration Manager
description: "Zarządzaj certyfikatami i zabezpieczeń dla programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7f91e63-4750-402e-9970-dd14be7f76a3
caps.latest.revision: "1"
author: mestew
ms.author: mstewart
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 9d8812da3588b60f388288cef6f9a093731d873f
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="manage-certificates-and-security-for-updates-publisher"></a>Zarządzaj certyfikatami i zabezpieczeń dla programu Updates Publisher

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniższe procedury ułatwiają konfigurowanie magazynu certyfikatów na serwerze aktualizacji, skonfigurować własny podpisywania certyfikatu na komputerze klienckim, i skonfigurować zasady grupy, aby umożliwić usługi Windows Update Agent na komputerach w celu skanowania w poszukiwaniu opublikować aktualizacje.

## <a name="configure-the-certificate-store-on-the-update-server"></a>Konfigurowanie magazynu certyfikatów na serwerze aktualizacji
 Aktualizacje Wydawca używa certyfikatu cyfrowego do podpisania aktualizacji w wykazach, który publikuje go. Katalog można było opublikować na serwerze aktualizacji, tego certyfikatu musi być w magazynie certyfikatów na serwerze aktualizacji i w magazynie certyfikatów komputera Updates Publisher, jeśli komputer jest zdalnie z serwera aktualizacji.

Poniższa procedura jest jednym z kilku dostępnych metod, aby dodać certyfikat do magazynu certyfikatów na serwerze aktualizacji.

### <a name="to-configure-the-certificate-store"></a>Aby skonfigurować Magazyn certyfikatów
1.  Na komputerze, który ma dostęp do zarówno komputera Updates Publisher, jak i serwer aktualizacji, kliknij przycisk **Start**, kliknij przycisk **Uruchom**, typ **MMC** w polu tekstowym, a następnie kliknij przycisk **OK** można otworzyć programu Microsoft Management Console (MMC).

2.  Kliknij przycisk **pliku**, kliknij przycisk **Dodaj/Usuń przystawkę**, kliknij przycisk **Dodaj**, kliknij przycisk **certyfikaty**, kliknij przycisk **Dodaj**, wybierz pozycję **konto komputera**, a następnie kliknij przycisk **dalej**.

3.  Wybierz **inny komputer**, wpisz nazwę serwera aktualizacji, lub kliknij przycisk **Przeglądaj** Aby odnaleźć komputer serwera aktualizacji, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

4.  Rozwiń węzeł  **certyfikatów (*nazwy serwera aktualizacji*) **, rozwiń węzeł **WSUS**, a następnie kliknij przycisk **certyfikaty**.

5.  W okienku wyników kliknij prawym przyciskiem myszy żądany certyfikat, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **wyeksportować**.

6.  W Kreatorze eksportu certyfikatów należy użyć wartości domyślnych do utworzenia pliku eksportu z nazwy i lokalizacji określonej w kreatorze. Ten plik musi być dostępny na serwerze aktualizacji przed przejściem do następnego kroku.

7.  Kliknij prawym przyciskiem myszy **zaufanych wydawców**, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **importu**. Ukończ pracę Kreatora importu certyfikatów za pomocą wyeksportowanego pliku z kroku 6.

8.  Jeśli certyfikat z podpisem własnym jest używany, takich jak **WSUS Publishers Self-signed**, kliknij prawym przyciskiem myszy **zaufane główne urzędy certyfikacji**, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **importu**. Ukończ pracę Kreatora importu certyfikatów za pomocą wyeksportowanego pliku z kroku 6.

9.  Kliknij prawym przyciskiem myszy  **certyfikatów (*nazwy serwera aktualizacji*) **, kliknij przycisk **Podłącz do innego komputera**, wpisz nazwę komputera dla komputera Updates Publisher i kliknij przycisk **OK**.

10. Jeśli Updates Publisher znajduje się zdalnie z serwera aktualizacji, powtórz kroki od 7 do 9, aby zaimportować certyfikat do magazynu certyfikatów na komputerze Updates Publisher.



## <a name="configure-a-self-signing-certificate-on-client-computers"></a>Konfigurowanie własnym podpisywania certyfikatu na komputerach klienckich
Na komputerach klienckich systemu Windows Update Agent (WUA) skanuje aktualizacje z wykazu. Ten proces zakończy się niepowodzeniem zainstalować aktualizacje, gdy agent nie może zlokalizować certyfikatu cyfrowego w magazynie zaufanych wydawców na komputerze lokalnym. Jeśli użyto certyfikatu z podpisem własnym do publikowania aktualizacji katalogu, takie jak **WSUS Publishers Self-signed**, certyfikat musi być również w magazynie certyfikatów zaufanych głównych urzędów certyfikacji na komputerze lokalnym, aby agenta można sprawdzić poprawności certyfikatu.

Można użyć jednej z kilku metod konfigurowania certyfikatów na komputerach klienckich, takich jak za pomocą zasad grupy i **Kreatora importu certyfikatów** lub przy użyciu narzędzia Certutil narzędzia i dystrybucji oprogramowania.

Poniżej podano jako przykład sposobu konfigurowania certyfikatów podpisywania na komputerach klienckich.

### <a name="to-configure-a-self-signing-certificate-on-client-computers"></a>Aby skonfigurować własny podpisywania certyfikatu na komputerach klienckich
1.  Na komputerze z dostępem do serwera aktualizacji, kliknij przycisk **Start**, kliknij przycisk **Uruchom**, typ **MMC** w polu tekstowym, a następnie kliknij przycisk **OK** można otworzyć programu Microsoft Management Console (MMC).

2.  Kliknij przycisk **pliku**, kliknij przycisk **Dodaj/Usuń przystawkę**, kliknij przycisk **Dodaj**, kliknij przycisk **certyfikaty**, kliknij przycisk **Dodaj**, wybierz pozycję **konto komputera**, a następnie kliknij przycisk **dalej**.

3.  Wybierz **inny komputer**, wpisz nazwę serwera aktualizacji, lub kliknij przycisk **Przeglądaj** Aby odnaleźć komputer serwera aktualizacji, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

4.  Rozwiń węzeł  **certyfikatów (*nazwy serwera aktualizacji*) **, rozwiń węzeł **WSUS**, a następnie kliknij przycisk **certyfikaty**.

5.  Kliknij prawym przyciskiem myszy certyfikat w okienku wyników, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **wyeksportować**. Zakończenie **Kreatora eksportu certyfikatów** przy użyciu ustawień domyślnych, aby utworzyć plik eksportu certyfikatu za pomocą nazwy i lokalizacji określonej w kreatorze.

6.  Użyj jednej z następujących metod można dodać certyfikatu używanego do podpisywania katalogu aktualizacji na każdym komputerze klienckim, który będzie używany do skanowania WUA aktualizacje w katalogu. Dodaj certyfikat na komputerze klienckim w następujący sposób:

    -   Dla certyfikatów z podpisem własnym: Dodaj certyfikat do **zaufane główne urzędy certyfikacji** i **zaufanych wydawców** magazyny certyfikatów.

    -   Dla urzędu certyfikacji (CA) wystawionych certyfikatów: Dodaj certyfikat do **zaufanych wydawców** magazynu certyfikatów.

    > [!NOTE]
    > Usługa WUA sprawdza również czy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft** ustawienie zasad grupy jest włączone na komputerze lokalnym. To ustawienie zasad musi być włączone, aby usługa WUA mogła skanować w poszukiwaniu aktualizacji utworzonych i opublikowanych za pomocą programu Updates Publisher. Aby uzyskać więcej informacji na temat włączania tego ustawienia zasad grupy, zobacz [jak skonfigurować zasady grupy na komputerach klienckich] (https://technet.microsoft.com/library/bb530967.aspx(d=robot).



## <a name="configuring-group-policy-to-allow-wua-on-computers-to-scan-for-published-updates"></a>Konfigurowanie zasad grupy, aby umożliwić WUA na komputerach w celu skanowania pod kątem opublikowanych aktualizacji
Zanim Windows zaktualizować Agent (WUA) na komputerach rozpocznie skanowanie aktualizacji utworzonych i opublikowanych przez program Updates Publisher, ustawienie zasad musi być włączony do Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft. Gdy ustawienie zasady jest włączone, usługa WUA będzie akceptować aktualizacje odebranych za pośrednictwem lokalizacji intranetowej, jeśli aktualizacje są podpisane **zaufanych wydawców** magazynu certyfikatów na komputerze lokalnym. Istnieje kilka metod konfigurowania zasad grupy na komputerach w środowisku.

Dla komputerów, które nie znajdują się w domenie ustawienie klucza rejestru można skonfigurować umożliwiający podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi Microsoft Update.

Poniższe procedury zawierają podstawowe kroki, które mogą służyć do konfigurowania zasad grupy dla komputerów w domenie i wartość klucza rejestru na komputerach, które nie znajdują się w domenie.

### <a name="to-configure-group-policy-to-allow-wua-to-scan-for-published-updates"></a>Aby skonfigurować zasady grupy, aby umożliwić WUA skanowania pod kątem opublikować aktualizacje
1.  Otwórz przystawkę Microsoft Management Console (MMC) edytora obiektu zasad grupy z użytkownika, który ma odpowiednie prawa zabezpieczeń do konfigurowania zasad grupy.

2.  Kliknij przycisk **Przeglądaj** i wybierz domenę, jednostki Organizacyjnej lub obiekty zasad grupy połączone z lokacji, w którym skonfigurowane zasady grupy zostaną przeniesione na komputery klienckie żądany. Kliknij przycisk **OK**, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

3.  Rozwiń ustawienie wybranych zasad w drzewie konsoli, rozwiń **Konfiguracja komputera**, rozwiń węzeł **Szablony administracyjne**, rozwiń węzeł **składniki systemu Windows**, a następnie kliknij przycisk **usługi Windows Update**.

4.  W okienku wyników kliknij prawym przyciskiem myszy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft**, kliknij przycisk **właściwości**, kliknij przycisk **włączone**, a następnie kliknij przycisk **OK**.
