---
title: "Zarządzanie pliki instalacji ekspresowej aktualizacji systemu Windows 10 | Dokumentacja firmy Microsoft"
description: "Program Configuration Manager obsługuje pliki instalacji ekspresowej w systemie Windows 10, który zapewnia mniejsze pliki do pobrania i skrócenie czasu instalacji na komputerach klienckich."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: fcdcbcde61402b47871d51deba32d23867a78370
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

## <a name="manage-express-installation-files-for-windows-10-updates"></a>Zarządzanie pliki instalacji ekspresowej aktualizacji systemu Windows 10
Począwszy od 1702 wersji programu Configuration Manager, Configuration Manager obsługuje pliki instalacji ekspresowej aktualizacji systemu Windows 10. Korzystając z obsługiwanych wersji systemu Windows 10, umożliwia ustawień programu Configuration Manager Pobierz tylko zmiany między bieżącym miesiącu systemu Windows 10 zbiorczej aktualizacji i aktualizacji w poprzednim miesiącu. Bez pliki instalacji ekspresowej programu Configuration Manager pobiera pełnego systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z poprzednich miesięcy) każdego miesiąca. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i skrócenie czasu instalacji na komputerach klienckich.

> [!IMPORTANT]
> Podczas ustawienia do obsługi plików instalacji ekspresowej plików jest dostępna w 1702 wersji programu Configuration Manager, system operacyjny klienta obsługuje jest dostępna w systemie Windows 10 wersji 1607 z aktualizacją Windows Update Agent. Ta aktualizacja jest dostępna z aktualizacjami wydana 11 kwietnia 2017 (wtorek poprawek). Aby uzyskać więcej informacji na temat tych aktualizacji, zobacz [obsługuje artykułu 4015217](http://support.microsoft.com/kb/4015217). Przyszłe aktualizacje będą używały express dla mniejsze pliki do pobrania. System Windows 10 wersji 1607 bez aktualizacji i wcześniejsze wersje nie obsługują pliki instalacji ekspresowej.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Aby umożliwić pobieranie plików instalacji ekspresowej aktualizacji systemu Windows 10 na serwerze
Aby rozpocząć synchronizowanie metadanych dla systemu Windows 10 pliki instalacji ekspresowej, można włączyć je w oknie Właściwości punktu aktualizacji oprogramowania.
1.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**.
2.    Wybierz centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
3.    Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**. Na **pliki aktualizacji** zaznacz **pobierania plików pełnego wszystkie aktualizacje zatwierdzone i express pliki instalacyjne dla systemu Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Aby włączyć obsługę klientów pobrać i zainstalować pliki instalacji ekspresowej
Aby włączyć obsługę plików instalacji ekspresowej na klientach, należy włączyć pliki instalacji ekspresowej na komputerach klienckich w sekcji Ustawienia klienta aktualizacji oprogramowania. Spowoduje to utworzenie nowego odbiornik HTTP, który nasłuchuje żądań pobrać pliki instalacji ekspresowej na porcie, który określisz. Gdy wdrożyć ustawienia klienta, aby włączyć tę funkcję na komputerze klienckim, podejmuje próbę pobrania różnica między bieżącym miesiącu systemu Windows 10 zbiorczej aktualizacji i aktualizacji w poprzednim miesiącu (klienci muszą uruchomić wersji systemu Windows 10, że obsługuje express pliki instalacyjne).
1.    Włącz obsługę plików instalacji ekspresowej we właściwościach składnika punktu aktualizacji oprogramowania (poprzedniej procedury).
2.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **ustawień klienta**.
3.    Wybierz ustawienia odpowiedniego klienta, a następnie na **Home** , kliknij pozycję **właściwości**.
4.    Wybierz **aktualizacji oprogramowania** skonfiguruj **tak** dla **Włącz instalację Express aktualizacji na klientach** i konfiguracji port używany przez odbiornik HTTP na kliencie **Port używany do pobierania zawartości dla aktualizacji Express** ustawienie.

