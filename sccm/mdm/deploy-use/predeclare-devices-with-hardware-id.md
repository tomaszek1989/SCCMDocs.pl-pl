---
title: "Predeclare urządzeń o numerach seryjnych IMEI lub iOS | Dokumentacja firmy Microsoft"
description: "Predeclare firmowych urządzeń za pomocą numeru seryjnego IMEI lub iOS."
ms.custom: na
ms.date: 03/24/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: 3
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6833951db27b227a3ca22925e9d9f4c3fc443fc
ms.openlocfilehash: e8606b8a9268a0a0668b75070cf35894f4794123
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Predeclare urządzenia z IMEI lub iOS numerów seryjnych

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Importowanie ich liczby tożsamości (IMEI) urządzeń przenośnych stacji międzynarodowe lub numery seryjne iOS można zidentyfikować firmowych urządzeń. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia lub można ręcznie wprowadzić informacje o urządzeniu.  Ustawi zaimportowanych informacji **własności** urządzeń, które są rejestrowane jako **firma** listach urządzeń. Licencja Intune jest nadal wymagana dla każdego użytkownika uzyskującego dostęp do usługi.  

Podczas przekazywania numerów seryjnych urządzeń z systemem iOS należące do firmy muszą być skojarzone z profilem rejestracji w firmie. Następnie można zarejestrować urządzeń, przy użyciu programu device enrollment program (DEP) firmy Apple albo lub Apple Configurator do nich są wyświetlane jako należące do firmy.

## <a name="how-to-predeclare-corporate-owned-devices"></a>Jak predeclare firmowych urządzeń

1.    W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **Przegląd** > **wszystkich urządzeń należących do** > **Predeclared urządzeń**.

2.  Kliknij przycisk **utworzyć Predeclared urządzeń**. Otworzy się Kreator tworzenia urządzenia Predeclared.

3.    Wybierz, jak chcesz dodać informacje o urządzeniu:

     -    **Przekaż plik CSV zawierający IMEI lub numery seryjne i szczegóły**

        Dla tej opcji, kliknij przycisk **Przeglądaj** do określ plik .csv zawierający informacje do predeclare firmowych urządzeń. Plik CSV musi być poprawnie sformatowana. Aby uzyskać więcej informacji, zobacz [Format wysyłania plików CSV](#format-for-uploading-csv-files).

     -    **Ręcznie Dodaj IMEI lub numery seryjne i szczegóły**

        Aby ręcznie wprowadzić informacje, wpisz IMEI numer lub iOS numery seryjne i szczegóły dla urządzeń. Popraw jakiekolwiek błędy lub ostrzeżenia przed kontynuowaniem.

    Kliknij przycisk **Dalej**.

4. Jeśli przekazać plik CSV, przejrzyj wyniki importu pliku. Jeśli numer urządzenia wcześniej został zaimportowany, Menedżer konfiguracji wyświetla tych urządzeń oraz zastąpienia **szczegóły**. Wybierz urządzenia, którego szczegóły chcesz zastąpić. Szczegóły urządzenia mogą być modyfikowane tylko przez ponowne importowanie identyfikacji urządzenia lub numer seryjny.

  Jeśli wybrano opcję ręcznie wprowadź liczbę, wypełnij formularz dla urządzeń, które mają być predeclare.

  Kliknij przycisk **Dalej**, aby kontynuować.

4. Jeśli lista zawiera numery seryjne iOS, wybierz **profilu rejestracji do przypisania** z listy dostępnych profilów, a następnie kliknij przycisk **dalej**.

5. Kliknij przycisk **dalej** Przejrzyj szczegóły, a następnie kliknij przycisk **dalej** ponownie, aby przekazać dane.

6. Kliknij przycisk **Zamknij** na zakończenie.

## <a name="format-for-uploading-csv-files"></a>Format wysyłania plików CSV

Plik CSV, używaną do identyfikowania urządzeń IMEI lub numer seryjny musi mieć następujący format, z wyłączeniem górnym wierszu, który dostarczany tylko do celów informacyjnych. Każdy wiersz musi zawierać numer identyfikacyjny albo numeru seryjnego IMEI, jak numer lub iOS. Może zawierać jednocześnie. Kod IMEI liczb może służyć do Android, iOS i Windows. iOS numery seryjne są również obsługiwane.  Ta tabela zawiera przykładowe dane:

| KOD IMEI #  | iOS numer seryjny  | SYSTEM OPERACYJNY | Szczegóły |
|------------ |---------------|-----|-----|
| 123456789012345    |   | SYSTEMU WINDOWS | Należące do firmy urządzenie z systemem Windows|
|   | A1B2C3D4E5C6 | IOS |     Urządzenia iOS należące do firmy|
| 223456789012345 | E6D5C4B3A210 |   IOS |     Inne urządzenie systemu iOS|
| 323456789012345 |        |   IOS |     Trzeci urządzenia iOS|
| 123456789012346 |         |   ANDROID |     Należące do firmy urządzeń z systemem Android|

Nie ma wiersz nagłówka w pliku CSV. W poniższym przykładzie pokazano tych samych danych przykładowych w formacie CSV:

```
123456789012345,,WINDOWS,Company-owned Windows device
,A1B2C3D4E5C6,IOS,Company-owned iOS device
223456789012345,E6D5C4B3A210,IOS,Another iOS device
323456789012345,,IOS,A third iOS device
123456789012346,,ANDROID,Company-owned Android device
```

Kolumny w pliku CSV zaakceptować następujące wartości:

| Kolumna 1 | Kolumna 2 | Kolumny 3 | Kolumna 4 |
|---|---|---|---|
|Numer IMEI bez spacji | numer seryjny iOS | IOS, WINDOWS i ANDROID | Szczegóły urządzenia opcjonalne (limit 1024 znaków) |

