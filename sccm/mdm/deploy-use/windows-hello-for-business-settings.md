---
title: "Windows Hello ustawień biznesowych | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak integrować Windows Hello dla firm z System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0593c07-5dd7-4d23-a0d8-d30165f49ef7
caps.latest.revision: 17
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8c7bf901caa49c8585a9ed3913d4a5a2aac57013
ms.openlocfilehash: 7ac2baeb3c10ce90eb643fa28a953186b571d037
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager-hybrid"></a>Windows Hello ustawień biznesowych w System Center Configuration Manager (hybrydowy)

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager umożliwia integrację z Windows Hello dla firm (dawniej Passport firmy Microsoft dla systemu Windows), który jest alternatywna metoda logowania dla urządzeń z systemem Windows 10. Funkcja Hello dla firm korzysta z usługi Active Directory lub konta usługi Azure Active Directory w celu zastąpienia hasła, karty inteligentnej lub wirtualnej karty inteligentnej.  

Funkcja Hello dla firm pozwala używać **gestu użytkownika** do logowania, zamiast hasła. Gestem użytkownika może być prosty numer PIN, uwierzytelnianie biometryczne lub urządzenie zewnętrzne, np. czytnik linii papilarnych.  

 Menedżer konfiguracji integruje się z systemu Windows Hello dla firm na dwa sposoby:  

-   Aby kontrolować, którzy użytkownicy gestów mogą i nie można używać do logowania, można użyć programu Configuration Manager.  

-   W dostawcy magazynu kluczy funkcji Windows Hello dla firm można przechowywać certyfikaty uwierzytelniania. Aby uzyskać więcej informacji, zobacz [profile certyfikatów](create-pfx-certificate-profiles.md).  

- Można wdrożyć Windows Hello zasady biznesowe przyłączonych do domeny systemu Windows 10 urządzeń, które Uruchom klienta programu Configuration Manager. Ta konfiguracja jest opisany w [skonfigurować Windows Hello firmy na urządzeniach przyłączonych do domeny systemu Windows 10](../../protect/deploy-use/windows-hello-for-business-settings.md#configure-windows-hello-for-business-on-domain-joined-windows-10-devices). Używając programu Configuration Manager za pomocą usługi Intune (hybrydowy), te ustawienia można skonfigurować w Windows 10 i Windows 10 Mobile urządzeń, ale nie w urządzeń dołączonych do domeny, które Uruchom klienta programu Configuration Manager.   

Ogólne informacje o konfigurowaniu Windows Hello ustawień biznesowych, zobacz [Windows Hello ustawień biznesowych w programie System Center Configuration Manager](../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="configure-windows-hello-for-business-settings-hybrid"></a>Konfigurowanie systemu Windows Hello dla firm ustawienia (hybrydowy)  

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **usług w chmurze** > **subskrypcje usługi Microsoft Intune**.  

3.  Wybierz z listy swoją subskrypcję usługi Microsoft Intune, a następnie na karcie **Narzędzia główne** w grupie **Subskrypcja** kliknij opcję **Konfiguruj platformy** > **Windows (MDM)**.  

4.  Na karcie **Windows Hello dla firm** okna dialogowego **Właściwości subskrypcji usługi Microsoft Intune** wybierz spośród następujących wartości. Będą one miały wpływ na wszystkie zarejestrowane urządzenia z systemem Windows 10 i Windows 10 Mobile:  

    -   **Wyłącz usługę Windows Hello dla firm na zarejestrowanych urządzeniach** lub **Włącz usługę Windows Hello dla firm na zarejestrowanych urządzeniach** — włącza lub wyłącza używanie funkcji Windows Hello dla firm na wszystkich zarejestrowanych urządzeniach z systemem Windows 10 i Windows 10 Mobile.  

    -   **Używaj modułu TPM (Trusted Platform Module)** — moduł TPM (Trusted Platform Module) zapewnia dodatkową warstwę zabezpieczeń danych. Wybierz jedną z następujących opcji:  

        -   **Wymagane** (domyślnie) — tylko urządzenia z dostępnym modułem TPM mogą aprowizować funkcję Windows Hello dla firm.  

        -   **Preferowane** — urządzenia najpierw próbują użyć modułu TPM. Jeśli nie jest on dostępny, mogą używać szyfrowania programowego.  

    -   **Wymagaj minimalnej długości numeru PIN** — określ minimalną liczbę znaków wymaganą dla numeru PIN funkcji Windows Hello dla firm. Należy użyć co najmniej 4 znaków (wartość domyślna to 6 znaków).  

    -   **Wymagaj maksymalnej długości numeru PIN** — określ maksymalną liczbę znaków dozwoloną dla numeru PIN funkcji Windows Hello dla firm. Można użyć do 127 znaków.  

    -   **Wymagaj małych liter w numerze PIN** – określa, czy w numerze PIN funkcji Windows Hello dla firm należy używać małych liter. Wybierz spośród opcji:  

        -   **Dozwolone** — użytkownicy mogą używać małych liter w numerach PIN.  

        -   **Wymagane** — użytkownicy muszą zawrzeć co najmniej jedną małą literę w numerze PIN.  

        -   **Niedozwolone** (domyślnie) — użytkownicy nie mogą używać małych liter w numerach PIN.  

    -   **Wymagaj wielkich liter w numerze PIN** – określa, czy w numerze PIN funkcji Windows Hello dla firm należy używać wielkich liter. Wybierz spośród opcji:  

        -   **Dozwolone** — użytkownicy mogą używać wielkich liter w numerach PIN.  

        -   **Wymagane** — użytkownicy muszą zawrzeć co najmniej jedną wielką literę w numerze PIN.  

        -   **Niedozwolone** (domyślnie) — użytkownicy nie mogą używać wielkich liter w numerach PIN.  

    -   **Wymagaj znaków specjalnych** — określa użycie znaków specjalnych w numerach PIN. Wybierz spośród opcji:  

        -   **Dozwolone** — użytkownicy mogą używać znaków specjalnych w numerach PIN.  

        -   **Wymagane** — użytkownicy muszą zawrzeć co najmniej jeden znak specjalny w numerze PIN.  

        -   **Niedozwolone** (domyślnie) — użytkownicy nie mogą używać znaków specjalnych w numerach PIN (ta wartość jest stosowana także w przypadku, gdy parametr nie zostanie skonfigurowany).  

         Znaki specjalne obejmują: **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**.  

    -   **Wymagaj wygasania numeru PIN (dni)** — określa liczbę dni, po której należy zmienić numer PIN urządzenia. Wartość domyślna to 41 dni.  

    -   **Zapobiegaj ponownemu używaniu poprzednich numerów PIN** — użyj tego ustawienia, aby ograniczyć ponowne używanie stosowanych wcześniej numerów PIN. Domyślnie nie jest dozwolone ponowne użycie żadnego z 5 ostatnich numerów PIN.  

    -   **Włącz gesty biometryczne** — umożliwia użycie uwierzytelniania biometrycznego, takiego jak rozpoznawanie twarzy lub linii papilarnych, zamiast numeru PIN na potrzeby funkcji Windows Hello dla firm. Użytkownicy nadal muszą skonfigurować służbowy numer PIN na wypadek niepowodzenia uwierzytelniania biometrycznego.  

         W przypadku wybrania opcji **Włączone**funkcja Windows Hello dla firm umożliwia użycie uwierzytelniania biometrycznego.  W przypadku wybrania opcji **Wyłączone**funkcja Windows Hello dla firm nie pozwala na użycie uwierzytelniania biometrycznego (dotyczy wszystkich typów kont).  

    -   **Użyj rozszerzonej ochrony przed fałszowaniem, jeśli jest dostępna** — określa, czy na urządzeniach, które obsługują tę funkcję, ma być używana rozszerzona ochrona przed fałszowaniem.  

         W przypadku wybrania opcji **Włączone**system Windows wymaga od wszystkich użytkowników używania ochrony przed fałszowaniem na potrzeby rozpoznawania twarzy, jeśli jest obsługiwana.  

    -   **Użyj paszportu zdalnego** — w przypadku wybrania opcji **Włączone**użytkownicy mogą używać zdalnej funkcji Windows Hello dla firm jako przenośnego urządzenia towarzyszącego w celu uwierzytelniania komputerów stacjonarnych. Komputer stacjonarny musi być przyłączony do usługi Azure Active Directory, a urządzenie towarzyszące musi posiadać skonfigurowany numer PIN funkcji Windows Hello dla firm.  

5.  Po zakończeniu kliknij przycisk **OK**.  

### <a name="see-also"></a>Zobacz także  
 [Ochrona infrastruktury danych i witryny z System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)

 [Zarządzanie weryfikacji tożsamości za pomocą Windows Hello dla firm](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport).  

