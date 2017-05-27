---
title: "Certyfikaty i zabezpieczeń | Dokumentacja firmy Microsoft"
description: "Zarządzanie certyfikatami i zabezpieczeń dla programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7f91e63-4750-402e-9970-dd14be7f76a3
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: c43af95a539a9284e4e49822b284783e02f9fa21
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-certificates-and-security-for-updates-publisher"></a>Zarządzanie certyfikatami i zabezpieczeń dla wydawcy aktualizacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Poniższe procedury ułatwiają konfigurowanie magazynu certyfikatów na serwerze aktualizacji, skonfigurować certyfikat z podpisem własnym na komputerze klienckim, a następnie skonfigurować zasady grupy, aby umożliwić usługi Windows Update Agent na komputerach do skanowania w poszukiwaniu opublikowanych aktualizacji.

## <a name="configure-the-certificate-store-on-the-update-server"></a>Konfigurowanie magazynu certyfikatów na serwerze aktualizacji
 Updates Publisher używa certyfikatu cyfrowego do podpisywania aktualizacji w wykazach, który ją publikuje. Katalog można było opublikować na serwerze aktualizacji, ten certyfikat musi być w magazynie certyfikatów na serwerze aktualizacji i w magazynie certyfikatów komputera wydawcy aktualizacji w przypadku komputera zdalnego z serwerem aktualizacji.

Poniższa procedura jest jednym z kilku metod, aby dodać certyfikat do magazynu certyfikatów na serwerze aktualizacji.

### <a name="to-configure-the-certificate-store"></a>Aby skonfigurować Magazyn certyfikatów
1.  Na komputerze, który ma dostęp zarówno komputera Updates Publisher, jak i serwera aktualizacji, kliknij przycisk **Start**, kliknij przycisk **Uruchom**, typ **MMC** w polu tekstowym, a następnie kliknij przycisk **OK** do otwarcia konsoli Microsoft Management Console (MMC).

2.  Kliknij przycisk **pliku**, kliknij przycisk **Dodaj/Usuń przystawkę**, kliknij przycisk **Dodaj**, kliknij przycisk **certyfikaty**, kliknij przycisk **Dodaj**, wybierz opcję **konto komputera**, a następnie kliknij przycisk **dalej**.

3.  Wybierz **inny komputer**, wpisz nazwę serwera aktualizacji, lub kliknij przycisk **Przeglądaj** Aby odnaleźć komputer serwera aktualizacji, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

4.  Rozwiń węzeł  **certyfikatów (*nazwę serwera aktualizacji*) **, rozwiń węzeł **WSUS**, a następnie kliknij przycisk **certyfikaty**.

5.  W okienku wyników kliknij prawym przyciskiem myszy żądany certyfikat, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **wyeksportować**.

6.  W Kreatorze eksportu certyfikatów należy użyć ustawień domyślnych do utworzenia pliku eksportu przy użyciu nazwy i lokalizacji określonej w kreatorze. Ten plik musi być dostępny dla serwera aktualizacji, przed przejściem do następnego kroku.

7.  Kliknij prawym przyciskiem myszy **zaufanych wydawców**, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **importowania**. Ukończ Kreatora importu certyfikatów przy użyciu pliku wyeksportowany w kroku 6.

8.  Jeśli certyfikat z podpisem własnym jest używany, takich jak **certyfikatu WSUS Publishers Self-signed**, kliknij prawym przyciskiem myszy **zaufanych głównych urzędów certyfikacji**, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **importowania**. Ukończ Kreatora importu certyfikatów przy użyciu pliku wyeksportowany w kroku 6.

9.  Kliknij prawym przyciskiem myszy  **certyfikatów (*nazwę serwera aktualizacji*) **, kliknij przycisk **Podłącz do innego komputera**, wprowadź nazwę wydawcy aktualizacji komputera i kliknij przycisk **OK**.

10. W przypadku zdalnie z serwera aktualizacji Updates Publisher, powtórz kroki od 7 do 9, aby zaimportować certyfikat do magazynu certyfikatów na komputerze wydawcy aktualizacji.



## <a name="configure-a-self-signing-certificate-on-client-computers"></a>Skonfiguruj certyfikat z podpisem własnym na komputerach klienckich
Na komputerach klienckich systemu Windows Update Agent (WUA) skanuje aktualizacje z wykazu. Ten proces nie będzie można instalować aktualizacje, gdy agent nie może zlokalizować certyfikatu cyfrowego w magazynie zaufanych wydawców na komputerze lokalnym. Jeśli użyto certyfikatu z podpisem własnym do publikowania aktualizacji katalogu, takich jak **certyfikatu WSUS Publishers Self-signed**, certyfikat musi być również w magazynie certyfikatów zaufanych głównych urzędów certyfikacji na komputerze lokalnym, aby sprawdzić poprawność certyfikatu agenta.

Można użyć jednej z kilku metod konfigurowania certyfikatów na komputerach klienckich, takich jak za pomocą zasad grupy i **Kreatora importu certyfikatów** lub za pomocą narzędzia Certutil dystrybucji narzędzi i oprogramowania.

Następujące jest dostarczany jako przykład sposobu konfigurowania certyfikatu podpisywania na komputerach klienckich.

### <a name="to-configure-a-self-signing-certificate-on-client-computers"></a>Aby skonfigurować certyfikat z podpisem własnym na komputerach klienckich
1.  Na komputerze z dostępem do serwera aktualizacji, kliknij przycisk **Start**, kliknij przycisk **Uruchom**, typ **MMC** w polu tekstowym, a następnie kliknij przycisk **OK** do otwarcia konsoli Microsoft Management Console (MMC).

2.  Kliknij przycisk **pliku**, kliknij przycisk **Dodaj/Usuń przystawkę**, kliknij przycisk **Dodaj**, kliknij przycisk **certyfikaty**, kliknij przycisk **Dodaj**, wybierz opcję **konto komputera**, a następnie kliknij przycisk **dalej**.

3.  Wybierz **inny komputer**, wpisz nazwę serwera aktualizacji, lub kliknij przycisk **Przeglądaj** Aby odnaleźć komputer serwera aktualizacji, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

4.  Rozwiń węzeł  **certyfikatów (*nazwę serwera aktualizacji*) **, rozwiń węzeł **WSUS**, a następnie kliknij przycisk **certyfikaty**.

5.  Kliknij prawym przyciskiem myszy certyfikat w okienku wyników, kliknij przycisk **wszystkie zadania**, a następnie kliknij przycisk **wyeksportować**. Ukończ **Kreatora eksportu certyfikatów** przy użyciu ustawień domyślnych do utworzenia certyfikatu wyeksportowanego pliku o nazwie i lokalizacji określonej w kreatorze.

6.  Użyj jednej z następujących metod do dodania certyfikatu używanego do podpisywania katalogu aktualizacji dla każdego komputera, którego będzie używać WUA do skanowania aktualizacji w katalogu. Dodaj certyfikat na komputerze klienckim w następujący sposób:

    -   Certyfikaty z podpisem własnym: Dodaj certyfikat do **zaufanych głównych urzędów certyfikacji** i **zaufanych wydawców** magazyny certyfikatów.

    -   Dla urzędu certyfikacji (CA) wydanych certyfikatów: Dodaj certyfikat do **zaufanych wydawców** magazynu certyfikatów.

    > [!NOTE]
    > Usługa WUA sprawdza również czy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft** włączono ustawienie zasad grupy na komputerze lokalnym. To ustawienie zasad musi być włączone, aby usługa WUA mogła skanować w poszukiwaniu aktualizacji utworzonych i opublikowanych za pomocą programu Updates Publisher. Aby uzyskać więcej informacji na temat włączania tego ustawienia zasad grupy, zobacz [jak skonfigurować zasady grupy na komputerach klienckich] (https://technet.microsoft.com/library/bb530967.aspx(d=robot).



## <a name="configuring-group-policy-to-allow-wua-on-computers-to-scan-for-published-updates"></a>Konfigurowanie zasad grupy, aby umożliwić WUA na komputerach w celu skanowania pod kątem opublikowanych aktualizacji
Zanim Windows Update Agent (WUA) na komputerach rozpocznie skanowanie aktualizacji utworzonych i opublikowanych za pomocą programu Updates Publisher, ustawienie zasad musi zostać włączony, aby umożliwić podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft. Gdy ustawienie zasady jest włączone, usługa WUA będzie akceptować aktualizacje odebranych za pośrednictwem lokalizacji intranetowej, jeśli będą one podpisane w **zaufanych wydawców** magazynu certyfikatów na komputerze lokalnym. Istnieje kilka metod do konfigurowania zasad grupy na komputerach w środowisku.

Dla komputerów, które nie znajdują się w domenie ustawienie klucza rejestru można skonfigurować umożliwiający podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi Microsoft Update.

W poniższych procedurach opisano podstawowe kroki, które można skonfigurować zasady grupy dla komputerów w domenie i wartości klucza rejestru na komputerach, które nie znajdują się w domenie.

### <a name="to-configure-group-policy-to-allow-wua-to-scan-for-published-updates"></a>Aby skonfigurować zasady grupy, aby umożliwić WUA mogła skanować w poszukiwaniu opublikowanych aktualizacji
1.  Otwórz przystawkę Microsoft Management Console (MMC) edytora obiektu zasad grupy z użytkownikiem, który ma odpowiednie uprawnienia zabezpieczeń do konfigurowania zasad grupy.

2.  Kliknij przycisk **Przeglądaj** i wybierz domenę, jednostki Organizacyjnej lub obiekty zasad grupy połączone z lokacji, gdzie skonfigurowane zasady grupy zostaną przeniesione na komputery klienckie żądaną. Kliknij przycisk **OK**, kliknij przycisk **Zakończ**, kliknij przycisk **Zamknij**, a następnie kliknij przycisk **OK**.

3.  Ustawienie wybranych zasad w drzewie konsoli rozwiń, rozwiń **konfiguracji komputera**, rozwiń węzeł **Szablony administracyjne**, rozwiń węzeł **składniki systemu Windows**, a następnie kliknij przycisk **usługi Windows Update**.

4.  W okienku wyników kliknij prawym przyciskiem myszy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft**, kliknij przycisk **właściwości**, kliknij przycisk **włączone**, a następnie kliknij przycisk **OK**.

