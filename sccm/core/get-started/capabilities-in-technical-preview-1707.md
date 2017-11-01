---
title: Technical Preview 1707
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1707 programu System Center Configuration Manager."
ms.custom: na
ms.date: 08/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb405ba0-8792-4ab7-988b-2f835f3a9550
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: bde9ed30ca5e52910a47c35cdb3d5b2f4475b18f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1707-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1707 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1707. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**Znane problemy w tej wersji Technical Preview:**
-   **Aktualizacja do wersji 1707 podglądu zakończy się niepowodzeniem, jeśli masz serwer lokacji w trybie pasywnym**. Po uruchomieniu wersji zapoznawczej 1706 i mieć [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), aby może pomyślnie zaktualizować lokację preview do wersji 1707 należy najpierw odinstalować serwer lokacji w trybie pasywnym. Po lokalizacji uruchomiono wersję 1707 można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku, kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.



**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Klient równorzędnej pamięci podręcznej obsługę plików instalacji ekspresowej dla systemu Windows 10 i usługi Office 365
<!-- 1352486 -->
Począwszy od tej wersji, równorzędnej pamięci podręcznej obsługuje dystrybucji plików instalacji ekspresowej zawartości dla systemu Windows 10 i plików aktualizacji w usłudze Office 365. Żadne dodatkowe konfiguracje są wymagane.

## <a name="surface-device-dashboard"></a>Powierzchni urządzenia pulpitu nawigacyjnego
<!--1355788-->
Urządzenia Surface pulpit nawigacyjny zawiera informacje o powierzchni urządzenia w danym środowisku. W konsoli przejdź do **monitorowanie** > **urządzeń Surface**. Można wyświetlić następujące czynności:
- procent powierzchni.
- procent powierzchni modeli
- z góry pięć wersji systemu operacyjnego

Kliknij sekcję **modeli powierzchni** wykresu, aby uzyskać pełną listę urządzeń.  

## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender
<!-- 1351960 -->

[Ochrona programu Windows Defender aplikacji](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) jest nową funkcją systemu Windows, która pomaga chronić użytkowników przez otwarcie niezaufanych witryn sieci web w bezpiecznego kontenera izolowanym, który nie jest dostępny za pomocą innymi składnikami systemu operacyjnego. W tej wersji technical preview dodaliśmy pomocy technicznej, aby skonfigurować tę funkcję za pomocą ustawień zgodności programu Configuration Manager, które można skonfigurować, a następnie wdrożyć do kolekcji. Ta funkcja zostanie wydana w 64-bitowej wersji aktualizacji twórca spadek 10 systemu Windows w wersji zapoznawczej (nazwa kodowa: RS3). Do testowania tej funkcji teraz, możesz muszą używać wersji zapoznawczej tej aktualizacji.

### <a name="before-you-start"></a>Przed rozpoczęciem

Aby utworzyć i wdrożyć zasady Guard aplikacji programu Windows Defender, urządzenia systemu Windows 10, na których można wdrożyć zasady musi być skonfigurowany z zasadami izolacji sieci. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Ta funkcja działa tylko dla bieżącej kompilacji systemu Windows 10 wewnętrznych. Aby ją przetestować, musi być uruchomiona klientów ostatnie systemu Windows 10 niejawnego kompilacji.

### <a name="try-it-out"></a>Wypróbuj

#### <a name="to-create-a-policy-and-to-browse-the-available-settings"></a>Aby utworzyć zasady i przeglądanie dostępnych ustawień:

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.
2. W **zasoby i zgodność** obszaru roboczego wybierz **omówienie** > **programu Endpoint Protection** > **Windows Defender aplikacji Guard**.
3. W **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji Guard zasady usługi Windows Defender**.
4. Przy użyciu wpis w blogu jako odwołanie, można wybrać i skonfigurować dostępne ustawienia wypróbowanie funkcji.
5. W tej wersji dodano nowe **definicji sieci** strony kreatora. Na tej stronie Określ tożsamością firmową, a Definiowanie sieci granic sieci firmowej.<br>Komputery z systemem Windows 10 przechowywać tylko jedną listę izolacji sieci na komputerze klienckim. W tej wersji można utworzyć dwa różne rodzaje list izolacji sieci (z systemem Windows Information Protection i z systemu Windows Defender aplikacji Guard) i wdrażać je do klienta. Jeśli obie zasady są wdrażane, te listy izolacji sieci muszą być zgodne. Jeśli wdrożono list, które nie pasują do tego samego klienta, wdrożenie zakończy się niepowodzeniem.
Można znaleźć więcej informacji o sposobie określania definicje sieci w [dokumentacji systemu Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).
6. Gdy skończysz, Zakończ pracę kreatora i wdróż zasady w co najmniej jedno urządzenie z systemem Windows 10.

### <a name="further-reading"></a>Dalsze informacje
Aby dowiedzieć się więcej o ochronie aplikacji systemu Windows Defender, zobacz [ten wpis w blogu](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Ponadto, aby dowiedzieć się więcej o trybie autonomiczny Guard aplikacji dla systemu Windows Defender, zobacz [ten wpis w blogu](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).

## <a name="add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Dodawanie parametrów podczas wdrażania skryptów programu PowerShell z programu Configuration Manager

<!-- 1236459 --->

W ostatnim Technical Preview wprowadzono nową możliwość, która umożliwia [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console).
W tej wersji Technical Preview możemy zostały rozszerzone na tej możliwości. Configuration Manager teraz odczytuje skrypt programu PowerShell i wyświetla wszystkie parametry w kreatorze tworzenia skryptów. Możesz podać wartość parametru w kreatorze, który będzie używany, gdy skrypt jest uruchamiany. Alternatywnie można pozostawić parametr puste. Jeśli to zrobisz, należy podać wartość parametru podczas uruchamiania skryptu.
W tej wersji technical preview należy podać parametry, które wymaga skryptu. W przyszłym wydaniu planujemy upewnij się, podając opcjonalne parametry skryptu.

### <a name="try-it-out"></a>Wypróbuj

1. Postępuj zgodnie z instrukcjami, aby [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console).
2. Na nowym **Parametry skryptu** strony **Kreatora tworzenia skryptu**, wybierz parametr, a następnie kliknij przycisk **Edytuj**.
3. Podana wartość parametru zaznaczony parametr, a następnie kliknij przycisk **OK**.
4. Ukończ pracę kreatora.

Po uruchomieniu skryptu, będzie on używać żadnych wartości parametrów, które zostały skonfigurowane.
