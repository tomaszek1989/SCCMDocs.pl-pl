---
title: "Zarządzanie plikami instalacji ekspresowej, aktualizacji systemu Windows 10 | Dokumentacja firmy Microsoft"
description: "Program Configuration Manager obsługuje pliki instalacji ekspresowej dla systemu Windows 10, która zapewnia mniejsze pliki do pobrania i instalacji szybsze na klientach."
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
ms.translationtype: MT
ms.sourcegitcommit: 1035dbbf944a3a467d637a4a948a75b0946eb711
ms.openlocfilehash: baffb5f026bd63c50f878214e71d2c9e9b8b51c2
ms.contentlocale: pl-pl
ms.lasthandoff: 07/11/2017

---

# Zarządzanie plikami instalacji ekspresowej aktualizacji systemu Windows 10
<a id="manage-express-installation-files-for-windows-10-updates" class="xliff"></a>
Począwszy od 1702 wersji programu Configuration Manager, Configuration Manager obsługuje pliki instalacji ekspresowej aktualizacji systemu Windows 10. Korzystając z obsługiwanej wersji systemu Windows 10, umożliwia ustawień programu Configuration Manager Pobierz tylko zmiany między bieżącego miesiąca systemu Windows 10 aktualizacji zbiorczej i aktualizacją poprzedniego miesiąca. Bez plików instalacji ekspresowej programu Configuration Manager pobiera pełnego systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z ostatnich miesięcy) każdego miesiąca. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i instalacji szybsze na klientach.

> [!IMPORTANT]
> Podczas ustawienia, aby obsługiwać użycie plików instalacji ekspresowej jest dostępna w 1702 wersji programu Configuration Manager, system operacyjny klienta obsługuje jest dostępna w systemie Windows 10 w wersji 1607 z aktualizacją usługi Windows Update Agent. Ta aktualizacja jest dostępna w przypadku aktualizacji wydanej w dniu 11 kwietnia 2017 (wtorek poprawek). Aby uzyskać więcej informacji na temat tych aktualizacji, zobacz [obsługuje artykułu 4015217](http://support.microsoft.com/kb/4015217). Przyszłe aktualizacje będzie korzystać z express dla mniejsze pliki do pobrania. Windows 10 w wersji 1607 bez aktualizacji i wcześniejsze wersje nie obsługują plików instalacji ekspresowej.


### Aby włączyć pobieranie plików instalacji ekspresowej aktualizacji systemu Windows 10
<a id="to-enable-the-download-of-express-installation-files-for-windows-10-updates" class="xliff"></a>
Aby rozpocząć, synchronizacja metadanych dla plików instalacji ekspresowej systemu Windows 10, należy włączyć ją we właściwościach punktu aktualizacji oprogramowania.
1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**.
2.  Wybierz centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
3.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**. Na **pliki aktualizacji** wybierz opcję **pobrać pełną pliki dla wszystkich aktualizacji zatwierdzonych i pliki instalacji ekspresowej dla systemu Windows 10**.

### Aby włączyć obsługę klientów pobrać i zainstalować pliki instalacji ekspresowej
<a id="to-enable-support-for-clients-to-download-and-install-express-installation-files" class="xliff"></a>
Aby włączyć obsługę plików instalacji ekspresowej na klientach, należy włączyć plików instalacji ekspresowej, w sekcji Ustawienia klienta aktualizacji oprogramowania. Spowoduje to utworzenie nowego odbiornik HTTP, która nasłuchuje żądań pobrać pliki instalacji ekspresowej na porcie, który określisz.

> [!NOTE]    
> Jest to port lokalny, którego klienci będą używać do nasłuchiwania żądań z optymalizacji dostarczania (WYKONAJ) lub usługi inteligentnego transferu w tle (BITS) można pobrać express zawartości z punktu dystrybucji. Nie trzeba otworzyć ten port na zaporach, ponieważ cały ruch na komputerze lokalnym.

Po wdrożeniu ustawień klienta, aby włączyć tę funkcję na komputerze klienckim, spróbuje pobrać różnica między bieżącego miesiąca systemu Windows 10 aktualizacji zbiorczej i poprzedniego miesiąca aktualizacji (klientów musi działać wersja systemu Windows 10 obsługuje pliki instalacji ekspresowej).
1.  Umożliwia obsługę plików instalacji ekspresowej we właściwościach składnika punktu aktualizacji oprogramowania (poprzedniej procedury).
2.  W konsoli programu Configuration Manager, przejdź do **administracji** > **ustawień klienta**.
3.  Wybierz ustawienia odpowiedniego klienta, a następnie na **Home** , kliknij pozycję **właściwości**.
4.  Wybierz **aktualizacji oprogramowania** skonfiguruj **tak** dla **Włącz instalację Express aktualizacji na klientach** ustawienia i skonfigurować port używany przez odbiornik HTTP na kliencie **Port używany na pobieranie zawartości dla aktualizacji Express** ustawienie.

