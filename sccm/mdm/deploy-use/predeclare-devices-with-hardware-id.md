---
title: Wstępna deklaracja urządzeń z numery IMEI lub iOS za
titleSuffix: Configuration Manager
description: Wstępna deklaracja urządzeń firmowych z ich numerami IMEI lub iOS za.
ms.date: 09/01/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 86ef14c871f476df39923e01e47874702271a08d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Wstępna deklaracja urządzeń z numery IMEI lub iOS za

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można zidentyfikować urządzenia należące do firmy przez zaimportowanie ich numerów identyfikujących (IMEI) urządzeń przenośnych międzynarodowe stacji lub numery seryjne systemu iOS. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI lub możesz ręcznie wprowadzić informacje o urządzeniu.  Zaimportowane informacje ustawią **własność** urządzeń rejestrowanych **Corporate** na listach urządzeń. Licencji usługi Intune są nadal wymagane dla każdego użytkownika uzyskującego dostęp do usługi.  

Podczas przekazywania numerów seryjnych urządzeń z systemem iOS należące do firmy, muszą być skojarzone z profilem rejestracji w firmie. Następnie można zarejestrować urządzeń, przy użyciu programu device enrollment program (DEP) albo firmy Apple lub narzędziu Apple Configurator, aby wyświetlać je jako należące do firmy.

>[!NOTE]
>Urządzenia z systemem android, z wyjątkiem urządzeń Samsung Knox Standard, musi mieć przypisany numer telefonu do nich predeclare i zarejestrować jako urządzenia należące do firmy z numerem IMEI.

## <a name="how-to-predeclare-corporate-owned-devices"></a>Jak wstępna deklaracja urządzeń należących do firmy za

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **omówienie** > **wszystkich firmowych urządzeń** > **wcześniej zadeklarowanej urządzeń**.

2.  Kliknij przycisk **utworzyć wcześniej zadeklarowanej urządzeń**. Zostanie otwarty Kreator tworzenia wcześniej zadeklarowanej urządzeń.

3.  Wybierz jak chcesz dodać informacje o urządzeniu:

     -  **Przekaż plik CSV zawierający IMEI lub numery seryjne i szczegóły**

        Dla tej opcji, kliknij przycisk **Przeglądaj** Aby określić plik CSV zawierający informacje do wstępna deklaracja urządzeń należących do firmy za. Plik CSV musi być poprawnie sformatowana. Aby uzyskać więcej informacji, zobacz [Format przekazywania CSV plików](#format-for-uploading-csv-files).

     -  **Ręcznie Dodaj IMEI lub numery seryjne i szczegóły**

        Aby ręcznie wprowadzić informacje, wpisz numer seryjny numer lub iOS IMEI i szczegóły dla urządzeń. Aby kontynuować, popraw jakiekolwiek błędy lub ostrzeżenia.

    Kliknij przycisk **Dalej**.

4. Jeśli został przekazany plik CSV, przejrzyj wyniki importowania z pliku. Jeśli wcześniej zaimportowano numer urządzenia, program Configuration Manager wyświetli te urządzenia i zastąpienia **szczegóły**. Wybierz urządzenia, którego szczegóły chcesz zastąpić. Szczegóły urządzenia mogą być modyfikowane tylko przez ponownie zaimportować identyfikacji urządzenia lub numer seryjny.

  Jeśli wybrano opcję ręcznie wprowadzić numer, wypełnij formularz dla urządzeń, które chcesz predeclare.

  Kliknij przycisk **Dalej** , aby kontynuować.

4. Jeśli lista zawiera numery seryjne systemu iOS, wybierz **profil rejestracji do przypisania** z listy dostępnych profilów, a następnie kliknij przycisk **dalej**.

5. Kliknij przycisk **dalej** Przejrzyj szczegóły, a następnie kliknij przycisk **dalej** ponownie, aby przekazać dane.

6. Kliknij przycisk **Zamknij** aby zakończyć.

## <a name="format-for-uploading-csv-files"></a>Format przekazywania plików CSV

Plik CSV, który umożliwia identyfikowanie urządzeń za pomocą numeru seryjnego IMEI lub iOS musi mieć następujący format, z wyłączeniem górnym wierszu, która jest dostępna tylko do celów informacyjnych. Każdy wiersz musi zawierać identyfikator, numer IMEI lub numer seryjny systemu iOS. Dla urządzeń z systemem iOS mogą obejmować jednocześnie. Numery IMEI może służyć do urządzeń z systemem Android, iOS i Windows. Ta tabela zawiera przykładowe dane:

| IMEI #  | numer seryjny systemu iOS  | SYSTEM OPERACYJNY | Szczegóły |
|------------ |---------------|-----|-----|
| 123456789012345    |   | SYSTEMU WINDOWS | Należące do firmy urządzenia z systemem Windows|
|   | A1B2C3D4E5C6 | IOS |  Urządzenia z systemem iOS należące do firmy|
| 223456789012345 | E6D5C4B3A210 |   IOS |  Inne urządzenie z systemem iOS|
| 323456789012345 |        |   IOS |    Trzeci urządzenia z systemem iOS|
| 123456789012346 |         |   ANDROID |   Należące do firmy urządzenia z systemem Android|

Nie dołączaj wiersz nagłówków w pliku CSV. W poniższym przykładzie przedstawiono te same dane przykładowe w formacie CSV:

```
123456789012345,,WINDOWS,Company-owned Windows device
,A1B2C3D4E5C6,IOS,Company-owned iOS device
223456789012345,E6D5C4B3A210,IOS,Another iOS device
323456789012345,,IOS,A third iOS device
123456789012346,,ANDROID,Company-owned Android device
```

Kolumn w pliku CSV akceptuje następujące wartości:

| Kolumna 1 | Kolumna 2 | Kolumna 3 | Kolumna 4 |
|---|---|---|---|
|Numer IMEI, bez spacji | numer seryjny systemu iOS | IOS, WINDOWS lub systemu ANDROID | Szczegóły urządzenia opcjonalne (limit to 1024 znaków) |
