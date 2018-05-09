---
title: 'Rejestrowanie urządzeń z systemem iOS firmy Apple Configurator '
titleSuffix: Configuration Manager
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.date: 08/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4c3dea67cd16c8efe272038894aa4f958f4ef160
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>Rejestrowanie hybrydowego systemu iOS przy użyciu programu Apple Configurator z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kup urządzeń z systemem iOS, które mają być używane przez pracowników firmy może zarządzać nimi za pomocą programu Microsoft Intune. Aby przygotować urządzenia z systemem iOS należące do rejestracji, skonfiguruj profil rejestracji w konsoli programu Configuration Manager i następnie wyeksportować adres URL profilu do użycia przy użyciu narzędzia Apple Configurator. Urządzenia z systemem iOS do rejestracji jest przygotowanie podłączenia do komputera Mac za pomocą kabla USB i skonfigurować ją przy użyciu programu Apple Configurator. Fabryka programu Apple Configurator powoduje zresetowanie urządzenia i dodaje profilu rejestracji, tak aby można było zarejestrować urządzenie, gdy użytkownik najpierw uprawnień go w górę i przechodzi przez proces Asystenta ustawień.

Poniższa procedura jest zalecane dla systemu IOS dedykowanych, które mają jednego użytkownika, który korzysta urządzenia dostępu do firmowej poczty e-mail i zasobów firmy, takich jak aplikacje i Data.  

## <a name="prerequisites"></a>Wymagania wstępne  

-   Fizyczny dostęp do urządzeń z systemem iOS  

-   Numery seryjne — [jak uzyskać numer seryjny systemu iOS](https://support.apple.com/en-us/HT204308)  

-   Komputer Mac z programem [Apple Configurator 2.0](http://go.microsoft.com/fwlink/?LinkId=518017)  

-   Kable USB do podłączania urządzeń do komputera Mac  

## <a name="add-a-corporate-owned-device-enrollment-profile"></a>Dodawanie profilu rejestracji urządzeń firmowych

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **omówienie** > **wszystkich firmowych urządzeń** > **iOS** > **profile rejestracji**. Kliknij przycisk **Utwórz profil** aby otworzyć Kreatora tworzenia profilu. Skonfiguruj ustawienia na następujących stronach:  

2.  Na stronie **Ogólne** określ następujące informacje:  

    -   **Nazwa** (nie są widoczne dla użytkowników)  

    -   **Opis elementu** (nie są widoczne dla użytkowników)  

    -   **Koligacja użytkownika** — określa sposób rejestracji urządzeń. W przypadku większości scenariuszy Asystenta ustawień użyj **Monituj o koligację użytkownika**.  

        -   **Monituj o koligację użytkownika**: Urządzenia muszą być powiązane z użytkownikiem podczas początkowej konfiguracji, a następnie opcjonalnie zezwolić na dostęp do danych firmowych i poczty e-mail jako ten użytkownik.  

        -   **Brak koligacji użytkownika**: Urządzenie nie jest powiązany z użytkownikiem. Tego typu przynależności należy użyć w przypadku urządzeń wykonujących zadania bez uzyskiwania dostępu do danych użytkowników lokalnych. Aplikacje wymagające przynależności do użytkownika nie będą działać.

    Kliknij przycisk **Dalej** , aby kontynuować.  

3.  Na **Device Enrollment Program** zostaw **ustawienia konfiguracji programu rejestracji urządzenia dla tego profilu** usunięciu zaznaczenia pola wyboru i kliknij przycisk **dalej**.  

4.  Przejrzyj podsumowanie, a następnie kliknij przycisk **dalej** Aby utworzyć profil rejestracji. Kliknij przycisk **Zamknij**, aby zakończyć pracę kreatora. Teraz możesz dodać numery IMEI lub numery seryjne dla urządzeń, które chcesz zarejestrować.  

## <a name="predeclare-devices-to-enroll-with-setup-assistant"></a>Wstępna deklaracja urządzeń do rejestracji przy użyciu Asystenta ustawień za

W tym kroku zostanie wstępna deklaracja urządzeń za jako firmowe podając listę identyfikatory sprzętu (IMEI lub numery seryjne).

Aby uzyskać więcej informacji, zobacz [wstępna deklaracja urządzeń z numerami IMEI i iOS za](predeclare-devices-with-hardware-id.md). Gdy wszystko będzie gotowe, wykonanie tego zadania, wróć do tej strony, aby kontynuować do następnego kroku.

## <a name="export-the-profile-to-deploy-to-ios-devices"></a>Eksportowanie profilu do wdrożenia na urządzeniach z systemem iOS

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **omówienie** > **wszystkich firmowych urządzeń** > **iOS** > **profile rejestracji**.

2.  Wybierz profil rejestracji ma być wdrażany na urządzeniach przenośnych, a następnie kliknij przycisk **Eksportuj...** .

3.  Skopiuj i Zapisz **adres URL profilu** w pliku można edytować.   

4.  Aby zapewnić obsługę programu Apple Configurator 2 należy edytować adres URL profilu 2.0. Zastąp następujące część adresu URL:  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     Z  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  Zapisz adres URL edycji profilu. Zostanie użyty, aby dodać adres URL profilu rejestracji w programie Apple Configurator w [następnej sekcji](#step-4-prepare-the-device-with-apple-configurator).  

> [!NOTE]
> Adres URL profilu rejestracji jest ważny przez dwa tygodnie po wyeksportowaniu. Po dwóch tygodniach należy wyeksportować nowy adres URL, aby zarejestrować urządzenia z systemem iOS.

## <a name="prepare-the-device-with-apple-configurator"></a>Przygotuj urządzenie przy użyciu narzędzia Apple Configurator

Aby przygotować urządzeń z systemem iOS do rejestracji, Połącz poszczególnych urządzeń do komputera Mac i Przekaż do niego profil rejestracji.  

> [!WARNING]  
>  Apple Configurator Czyści i powoduje zresetowanie urządzenia do konfiguracji fabrycznych.  

1.  Na komputerze Mac Otwórz **Apple Configurator 2**.  

2.  Na pasku menu kliknij **Apple Configurator 2** > **preferencje**.  

2.  W okienku preferencji wybierz **serwerów** i kliknij symbol "+" pod lewym okienkiem, aby uruchomić Kreatora serwera MDM. Kliknij przycisk **Dalej**.  

3.  Wprowadź **nazwa** i **adres URL rejestracji** oszczędzasz [wcześniejszych](#step-3-export-the-profile-to-deploy-to-ios-devices). Kliknij przycisk **Dalej**.  

   > [!NOTE]
   > Jeśli pojawi się ostrzeżenie o wymaganiach dotyczących profilu zaufanego dla Apple TV, możesz bezpiecznie anulować **zaufany profil** klikając szary symbol "X". Można również bezpiecznie zignorować ostrzeżenia dotyczące certyfikatu zakotwiczenia.

   Aby kontynuować, kliknij przycisk **dalej** do czasu ukończenia kreatora.  

4.  Na **serwerów** okienku, kliknij "Edytuj", obok profilu nowego serwera. Upewnij się, że adres URL rejestracji dokładnie odpowiada adresowi URL, wprowadzony wcześniej. Wprowadź ponownie adres URL, jeśli jest inny, a następnie kliknij przycisk **zapisać**.  

5.  Za pomocą kabla USB podłącz urządzenie z systemem iOS do komputera Mac.  

  > [!WARNING]  
  >  Ten proces powoduje zresetowanie urządzenia do konfiguracji fabrycznych. Przed podłączeniem urządzenia, zresetowania urządzenia i włączenie go. Najlepszym rozwiązaniem urządzenie powinno być na ekranie powitalnym przed kontynuowaniem.  

6.  Kliknij przycisk **przygotowanie**. Na **przygotowanie urządzenie iOS** okienku wybierz **ręcznego**, a następnie kliknij przycisk **dalej**.  

7.  Na **rejestrowanie na serwerze zarządzania urządzeniami Przenośnymi** okienku, wybierz nazwę utworzonego serwera, a następnie kliknij przycisk **dalej**.  

9. Na **Utwórz organizację** okienku wybierz **organizacji** lub Utwórz nową organizację, a następnie kliknij przycisk **dalej**.  

10. Na **Konfigurowanie Asystenta ustawień systemu iOS** okienku wybierz kroki, aby widoczne dla użytkownika, a następnie kliknij przycisk **Prepare**. Jeśli zostanie wyświetlony monit, Uwierzytelnij się do zaktualizowania ustawień zaufania.  

11. Po zakończeniu możesz odłączyć kabel USB.  

Powtórz te kroki dla wszystkich urządzeń, które chcesz przygotowanie do rejestracji.

## <a name="distribute-devices"></a>Dystrybuuj urządzenia

Urządzenia są teraz gotowe do rejestracji w firmie. Wyłącz urządzenia i przekaż je użytkownikom. Gdy urządzenie jest włączone, Asystent ustawień uruchomi i monituj użytkownika dla swojego konta firmowego lub szkolnego, aby rozpocząć rejestrowanie.
