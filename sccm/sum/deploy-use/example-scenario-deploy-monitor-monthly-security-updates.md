---
title: "Przykładowy scenariusz wdrażania i monitorowania aktualizacji oprogramowania zabezpieczającego | Dokumentacja firmy Microsoft"
description: "Użyj ten przykładowy scenariusz sposobu korzystania z aktualizacji oprogramowania w programie Configuration Manager do wdrażania i monitorowania aktualizacji oprogramowania zabezpieczającego w wersjach miesięczne firmy Microsoft."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.service: 
ms.assetid: c32f757a-02da-43f2-b055-5cfd097d8c43
ms.openlocfilehash: 0e6e2b3a9455bb6eda437eb1325aaaadb3d83420
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="example-scenario-for-using-system-center-configuration-manager-to-deploy-and-monitor-the-security-software-updates-released-monthly-by-microsoft"></a>Przykładowy scenariusz użycia programu System Center Configuration Manager do wdrażania i monitorowania aktualizacji oprogramowania zabezpieczającego, wydawanych co miesiąc przez firmę Microsoft

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera przykładowy scenariusz sposobu użycia aktualizacji oprogramowania w programie System Center Configuration Manager do wdrażania i monitorowania aktualizacji oprogramowania zabezpieczającego, które firma Microsoft udostępnia co miesiąc.  

 W tym scenariuszu Jan jest administratorem programu Configuration Manager w banku Woodgrove Bank. Jan musi utworzyć strategię wdrażania aktualizacji oprogramowania z uwzględnieniem następujących warunków i wymogów:  

-   Aktywne wdrożenie aktualizacji oprogramowania odbywa się jeden tydzień po tym, jak firma Microsoft wydaje aktualizację oprogramowania zabezpieczającego w drugi wtorek każdego miesiąca. To zdarzenie jest zwykle nazywane „wtorkiem poprawek”.  

-   Aktualizacje oprogramowania są pobierane na punkty dystrybucji i przygotowywane na nich. Następnie, zanim Jan w pełni wdroży aktualizacje oprogramowania w środowisku produkcyjnym, wdrożenie jest testowane na podzestawie klientów.  

-   Jan musi mieć możliwość monitorowania zgodności aktualizacji oprogramowania według miesięcy lub lat.  

 W tym scenariuszu przyjęto założenie, że infrastruktura punktu aktualizacji oprogramowania jest już zaimplementowana. Planowanie i konfigurowanie aktualizacji oprogramowania w programie Configuration Manager, skorzystaj z poniższych informacji.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Sprawdź kluczowe założenia aktualizacji oprogramowania.|[Wprowadzenie do aktualizacji oprogramowania](../understand/software-updates-introduction.md)|  
|Zaplanuj aktualizacje oprogramowania. Te informacje ułatwiają planowanie kwestii związanych z pojemnością, ustaleniem infrastruktury punktu aktualizacji oprogramowania, instalacją punktu aktualizacji oprogramowania, ustawieniami synchronizacji oraz ustawieniami klienta dotyczącymi aktualizacji oprogramowania.|[Planowanie aktualizacji oprogramowania](../plan-design/plan-for-software-updates.md)|  
|Skonfiguruj aktualizacje oprogramowania. Te informacje ułatwiają instalowanie i konfigurowanie punktów aktualizacji oprogramowania w hierarchii oraz pomagają konfigurować i synchronizować aktualizacje oprogramowania.<br /><br /> W tym scenariuszu Jan konfiguruje harmonogram synchronizacji aktualizacji oprogramowania występuje w drugą środę każdego miesiąca, aby upewnić się, że zostaną pobrane najnowsze aktualizacje oprogramowania zabezpieczającego firmy Microsoft.|[Synchronizowanie aktualizacji oprogramowania](../get-started/synchronize-software-updates.md)|  

 Następujące sekcje w tym temacie przedstawiono przykładowe kroki ułatwiające wdrażanie i monitorowanie aktualizacji oprogramowania zabezpieczającego programu Configuration Manager w organizacji.

##  <a name="BKMK_Step1"></a>Krok 1. Tworzenie grupy aktualizacji oprogramowania dla zgodności corocznej  
 Jan tworzy grupę aktualizacji oprogramowania, której można użyć w celu monitorowania zgodności wszystkich aktualizacji oprogramowania zabezpieczającego wydanych w 2016. Wykonuje kroki opisane w poniższej tabeli.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Z **wszystkie aktualizacje oprogramowania** węzeł w konsoli programu Configuration Manager, Jan dodaje kryteria do wyświetlenia tylko aktualizacji oprogramowania zabezpieczającego, które zostały wydane lub zmienione w roku 2015 i spełniają następujące kryteria:<br /><br /><ul><li>**Kryteria**: Data wydania lub zmian</li><li>**Warunek**: Jest większe lub równe konkretnej dacie<br />**Wartość**: 1/1/2015</li><li>**Kryteria**: Klasyfikacja aktualizacji<br />**Wartość**: Aktualizacje zabezpieczeń</li><li>**Kryteria**: Ważność <br />**Wartość**: Nie</li></ul>|Brak dodatkowych informacji|
|John dodaje wszystkie odfiltrowane aktualizacje oprogramowania do nowej grupy aktualizacji oprogramowania, nakładając poniższe warunki:<br /><br /><ul><li>**Nazwa**: Zgodność grupa — aktualizacje zabezpieczeń Microsoft 2015</li><li>**Opis elementu**: Aktualizacje oprogramowania|[Dodawanie aktualizacji oprogramowania do grupy aktualizacji](add-software-updates-to-an-update-group.md)|  

##  <a name="BKMK_Step2"></a>Krok 2. Utwórz regułę automatycznego wdrażania dla bieżącego miesiąca  
 Jan tworzy zasadę automatycznego wdrażania dotyczącą aktualizacji oprogramowania zabezpieczającego wydanego przez firmę Microsoft w bieżącym miesiącu. Wykonuje kroki opisane w poniższej tabeli.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jan tworzy zasadę automatycznego wdrażania z następującymi wymogami:<br /><br /><ol><li>Na karcie **Ogólne** Jan konfiguruje następujące opcje:<br /> <ul><li>Określa **comiesięcznych aktualizacji zabezpieczeń** dla nazwy.</li><li>Wybiera kolekcję testową z ograniczonymi klientami.</li><li>Wybiera **Utwórz nową grupę aktualizacji oprogramowania**.</li><li>Sprawdza, czy **Włącz wdrożenie po uruchomieniu tej reguły** nie jest zaznaczone.</li></ul></li><li>Na karcie **Ustawienie wdrażania** Jan wybiera ustawienia domyślne.</li><li>Na **aktualizacji oprogramowania** strony, Jacek konfiguruje następujące filtry właściwości i kryteria wyszukiwania:<br /><ul><li>Data wydania lub zmian **Ostatni miesiąc**.</li><li>Klasyfikacja aktualizacji **Aktualizacje zabezpieczeń**.</li></ul></li><li>Na **oceny** strony, Jan włącza zasadę uruchamiania zgodnie z harmonogramem **drugi czwartek** z każdym **miesiąca**. Jan sprawdza także, czy jego harmonogram synchronizacji jest skonfigurowany do uruchamiania na **drugą środę** z każdym **miesiąca**.</li><li>Jan używa ustawień domyślnych na stronach Harmonogram wdrażania, Czynności użytkownika, Alerty i Ustawienia pobierania.</li><li>Na **pakietu wdrożeniowego** strony, Jan Określa nowy pakiet wdrożeniowy.</li><li>Jan używa ustawień domyślnych na stronach Lokalizacja pobierania i Wybieranie języka.</li></ol>|[Automatyczne wdrażanie aktualizacji oprogramowania](automatically-deploy-software-updates.md)|  

##  <a name="BKMK_Step3"></a>Krok 3. Sprawdź, czy aktualizacje oprogramowania są gotowe do wdrożenia  
 W drugi czwartek każdego miesiąca Jan sprawdza, czy aktualizacje oprogramowania są gotowe do wdrożenia. Wykonuje następny krok.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jan sprawdza, czy synchronizacja aktualizacji oprogramowania zakończyła się powodzeniem.|[Stan synchronizacji aktualizacji oprogramowania](monitor-software-updates.md#BKMK_SUSyncStatus)|  

##  <a name="BKMK_Step4"></a>Krok 4. Wdrożenie grupy aktualizacji oprogramowania  
 Po tym, jak Jan sprawdzi, czy aktualizacje oprogramowania są gotowe do wdrożenia, wdraża je. Wykonuje kroki opisane w poniższej tabeli.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jan tworzy dwa wdrożenia testowe dla nowej grupy aktualizacji oprogramowania. W przypadku każdego wdrożenia uwzględnia następujące środowiska:<br /><br /> **Testowe wdrożenie na stacji roboczej**: Jan rozważa następujące kwestie przypadku testowego wdrożenia na stacji roboczej:<br /><br /><ul><li>Określa kolekcję wdrożenia zawierającą podzestaw klienckich stacji roboczych do zweryfikowania wdrożenia.</li><li>Konfiguruje ustawienia wdrożenia, które są odpowiednie do klienckich stacji roboczej w środowisku.</li></ul><br />**Testowe wdrożenie na serwerze**: Jan rozważa następujące kwestie przypadku testowego wdrożenia na serwerze:<br /><br /><ul><li>Określa kolekcję wdrożenia zawierającą podzestaw serwerów klienckich do zweryfikowania wdrożenia.</li><li>Konfiguruje ustawienia wdrożenia, które są odpowiednie do klienckich serwera w środowisku.</li></ul>|[Wdrażanie aktualizacji oprogramowania](deploy-software-updates.md)|  
|Jan sprawdza, czy wdrożenia testowe zostały pomyślnie wdrożone.|[Stan wdrożenia aktualizacji oprogramowania](monitor-software-updates.md#BKMK_SUDeployStatus)|  
|Jan aktualizuje dwa wdrożenia za pomocą nowych kolekcji, które zawierają jego produkcyjne stacje robocze i serwery.|Brak dodatkowych informacji|  

##  <a name="BKMK_Step5"></a>Krok 5. Monitorowanie zgodności wdrożonych aktualizacji oprogramowania  
 Jan monitoruje zgodność zastosowanych wdrożeń aktualizacji oprogramowania. Wykonuje krok opisany w poniższej tabeli.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|John monitoruje stan wdrożenia aktualizacji oprogramowania w konsoli programu Configuration Manager i sprawdza raporty wdrożeń aktualizacji oprogramowania dostępne w konsoli.|[Monitorowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../sum/deploy-use/monitor-software-updates.md)|  

##  <a name="BKMK_Step6"></a>Krok 6. Dodanie comiesięcznych aktualizacji oprogramowania do grup aktualizacji corocznych  
 Jan dodaje aktualizacje oprogramowania z grupy comiesięcznych aktualizacji oprogramowania do grupy corocznych aktualizacji oprogramowania. Wykonuje krok opisany w poniższej tabeli.  

|Proces|Tematy pomocy|  
|-------------|---------------|  
|Jan wybiera aktualizacje oprogramowania z grupy comiesięcznych aktualizacji oprogramowania i dodaje je do grupy aktualizacji oprogramowania, którą utworzył na potrzeby zgodności corocznej. Śledzi zgodność aktualizacji oprogramowania i tworzy różne raporty dla zarządu.|[Dodawanie aktualizacji oprogramowania do wdrożonej grupy aktualizacji](add-software-updates-to-an-update-group.md)|  

Jan pomyślnie zrealizował comiesięczne wdrożenie aktualizacji oprogramowania zabezpieczającego. Kontynuuje monitorowanie i raportowanie zgodności aktualizacji oprogramowania, aby mieć pewność, że poziomy zgodności klientów w jego środowisku są akceptowalne.  

##  <a name="BKMK_MonthlyProcess"></a>Cykliczny comiesięczny proces wdrażania aktualizacji oprogramowania  
 Po pierwszym miesiącu, w którym Jan wdrożył aktualizacje oprogramowania, wykonuje on kroki od trzeciego do szóstego, aby wdrożyć kolejne comiesięczne aktualizacje oprogramowania zabezpieczającego wydane przez firmę Microsoft.  
