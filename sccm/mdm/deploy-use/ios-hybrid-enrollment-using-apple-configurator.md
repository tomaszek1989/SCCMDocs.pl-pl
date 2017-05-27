---
title: "Rejestrowanie urządzeń iOS Apple Configurator — Configuration Manager | Dokumentacja firmy Microsoft"
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
caps.latest.revision: 5
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f8242b4b454622388f45c34ba71c4148c87c27b7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>iOS hybrydowe rejestracji przy użyciu programu Apple Configurator z programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Kup urządzeń z systemem iOS do użycia przez pracowników firmy może zarządzać nimi za pomocą programu Microsoft Intune. W celu przygotowania urządzeń firmowych iOS do rejestracji, skonfiguruj profil rejestracji w konsoli programu Configuration Manager, a następnie wyeksportowania adres URL profilu do użycia przez narzędzia Apple Configurator. Przygotuj się do rejestracji na urządzeniu przez połączenie go na komputer Mac za pomocą kabla USB i je skonfigurować przy użyciu programu Apple Configurator. Fabryka Apple Configurator resetuje urządzenia i dodaje profil rejestracji, tak aby można było zarejestrować urządzenie, gdy użytkownik najpierw uprawnienia go się i przechodzi przez proces Asystenta.

Poniższa procedura jest zalecana dla dedykowanych iOS urządzeń z pojedynczego użytkownika, który uzyskuje dostęp do firmowej poczty e-mail i zasobów firmy, takich jak aplikacje i daty urządzenia.  

## <a name="prerequisites"></a>Wymagania wstępne  

-   Fizyczny dostęp do urządzeń z systemem iOS  

-   Numery seryjne - [jak uzyskać numeru seryjnego systemu iOS](https://support.apple.com/en-us/HT204308)  

-   Komputer Mac z [Apple Configurator 2.0](http://go.microsoft.com/fwlink/?LinkId=518017)  

-   Kable USB do podłączania urządzeń do komputera Mac  

## <a name="step-1-add-a-corporate-owned-device-enrollment-profile"></a>Krok 1: Dodaj profil rejestracji urządzeń firmowych

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **Przegląd** > **wszystkich urządzeń należących do** > **iOS** > **profile rejestracji**. Kliknij przycisk **Utwórz profil** aby otworzyć Kreatora tworzenia profilu. Skonfiguruj ustawienia na następujących stronach:  

2.  Na stronie **Ogólne** określ następujące informacje:  

    -   **Nazwa** (niewidoczny dla użytkowników)  

    -   **Opis** (niewidoczny dla użytkowników)  

    -   **Koligacja użytkownika** — określa sposób rejestracji urządzeń. W przypadku większości scenariuszy Asystenta, użyj **Monituj o koligację użytkownika**.  

        -   **Monituj o koligację użytkownika**: Urządzenia muszą być powiązane z użytkownika podczas instalacji początkowej oraz można zezwolić na dostęp do danych firmowych i poczty e-mail jako ten użytkownik.  

        -   **Brak koligacji użytkownika**: Urządzenie nie jest powiązany z użytkownikiem. Tego typu przynależności należy użyć w przypadku urządzeń wykonujących zadania bez uzyskiwania dostępu do danych użytkowników lokalnych. Aplikacje wymagające przynależności do użytkownika nie będą działać.

    Kliknij przycisk **Dalej**, aby kontynuować.  

3.  Na **Device Enrollment Program** zostaw **ustawienia konfigurowania programu rejestracji urządzeń dla tego profilu** pole wyboru nie jest zaznaczona i kliknij przycisk **dalej**.  

4.  Przejrzyj podsumowanie, a następnie kliknij przycisk **dalej** do utworzenia profilu rejestracji. Kliknij przycisk **Zamknij**, aby zakończyć pracę kreatora. Możesz teraz dodać IMEI lub numery seryjne dla urządzeń, które chcesz zarejestrować.  

## <a name="step-2-predeclare-devices-to-enroll-with-setup-assistant"></a>Krok 2: Predeclare urządzenia do zarejestrowania za pomocą Asystenta

W tym kroku urządzenia jako należące do predeclare się poprzez dostarczenie listy identyfikatorów sprzętu (IMEI lub numery seryjne).

Aby uzyskać więcej informacji, zobacz [Predeclare urządzeń o numerze seryjnym IMEI i iOS](predeclare-devices-with-hardware-id.md). Po zakończeniu tego zadania, wróć do tej strony, aby przejść do następnego kroku.

## <a name="step-3-export-the-profile-to-deploy-to-ios-devices"></a>Krok 3: Eksportuj profil do wdrożenia na urządzeniach z systemem iOS

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **Przegląd** > **wszystkich urządzeń należących do** > **iOS** > **profile rejestracji**.

2.  Wybierz profil rejestracji dla wdrożenia na urządzeniach przenośnych, a następnie kliknij przycisk **Eksportuj...** .

3.  Skopiuj i Zapisz **adres URL profilu** w pliku można edytować.   

4.  Należy edytować 2.0 adres URL profilu do wsparcia 2 konfiguratora firmy Apple. Zastąp następujące część adresu URL:  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     za pomocą  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  Zapisz zmodyfikowany profil adresu URL. Zostanie użyty, aby dodać adres URL profilu rejestracji w programie Apple Configurator w [następny rozdział](#step-4-prepare-the-device-with-apple-configurator).  

> [!NOTE]
> Adres URL profilu rejestracji jest ważny przez dwa tygodnie po wyeksportowaniu. Po dwóch tygodniach należy wyeksportować nowy adres URL, aby zarejestrować urządzenia iOS.

## <a name="step-4-prepare-the-device-with-apple-configurator"></a>Krok 4: Przygotuj urządzenie przy użyciu narzędzia Apple Configurator

Przygotowanie do rejestracji urządzeń z systemem iOS, nawiąż połączenie z komputerem Mac każdego urządzenia i przekaż mu profilu rejestracji.  

> [!WARNING]  
>  Apple Configurator przetwarzający Czyści i resetuje urządzeń do konfiguracji fabrycznych.  

1.  Na komputerze Mac Otwórz **Apple Configurator 2**.  

2.  Na pasku menu kliknij **Apple Configurator 2** > **preferencje**.  

2.  Wybierz w okienku preferencje **serwerów** i kliknij poniżej okienku po lewej stronie, aby uruchomić Kreatora serwera MDM symbol "+". Kliknij przycisk **Dalej**.  

3.  Wprowadź **nazwa** i **URL rejestracji** możesz zapisać [wcześniejszych](#step-3-export-the-profile-to-deploy-to-ios-devices). Kliknij przycisk **Dalej**.  

   > [!NOTE]
   > Jeśli pojawi się ostrzeżenie o wymaganiach dotyczących profilu zaufania telewizji firmy Apple, możesz bezpiecznie anulować **profilu zaufania** opcji przez kliknięcie przycisku "X" w kolorze szarym. Można również bezpiecznie zignorować ostrzeżenia dotyczące certyfikatu zakotwiczenia.

   Aby kontynuować, kliknij przycisk **dalej** do czasu ukończenia kreatora.  

4.  Na **serwerów** okienko, kliknij przycisk "Edytuj", obok profilu nowego serwera. Upewnij się, że adres URL rejestracji dokładnie odpowiada wcześniej wprowadzony adres URL. Wprowadź ponownie adres URL, jeśli jest inny, a następnie kliknij przycisk **zapisać**.  

5.  Za pomocą kabla USB do komputera Mac należy połączyć urządzenie z systemem iOS.  

  > [!WARNING]  
  >  Ten proces powoduje zresetowanie urządzenia do konfiguracji fabrycznych. Przed podłączeniem urządzenia, zresetowanie urządzenia i włącz go. Najlepszym rozwiązaniem urządzenia należy na ekranie Hello przed kontynuowaniem.  

6.  Kliknij przycisk **przygotować**. Na **przygotować iOS urządzenia** wybierz opcję **ręcznego**, a następnie kliknij przycisk **dalej**.  

7.  Na **rejestrowanie MDM Server** okienka, wybierz serwer nazwie zostanie utworzony, a następnie kliknij **dalej**.  

9. Na **tworzenie organizacji** okienku wybierz **organizacji** lub utworzyć nowej organizacji, a następnie kliknij przycisk **dalej**.  

10. Na **Konfigurowanie Asystenta ustawień systemu iOS** okienku wybierz czynności wyświetlane dla użytkownika, a następnie kliknij przycisk **Prepare**. Jeśli zostanie wyświetlony monit, uwierzytelnianie zaktualizować ustawień zaufania.  

11. Po zakończeniu w przypadku odłączenia kabla USB.  

Powtórz te kroki dla wszystkich urządzeń, które mają być przygotowanie do rejestracji.

## <a name="step-5-distribute-devices"></a>Krok 5. Dystrybuuj urządzenia

Urządzenia są teraz gotowe do rejestracji w firmie. Wyłącz urządzenia i przekaż je użytkownikom. Po włączeniu urządzenia Asystenta uruchomi i monit o ich konta firmowego lub szkolnego do rozpoczęcia rejestrowania.

