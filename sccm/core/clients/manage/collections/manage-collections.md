---
title: "Zarządzanie kolekcjami | Dokumentacja firmy Microsoft"
description: "Czy kolekcje typowych zadań zarządzania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 4/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e102fd1a-76df-4d8e-b1b0-10ee18318f67
caps.latest.revision: 8
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 4d44f98eb0755619cdd2101203a13725186b835b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-collections-in-system-center-configuration-manager"></a>Jak zarządzać kolekcje w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj informacje w tym temacie ułatwiają wykonywanie zadań zarządzania dla kolekcji w programie System Center Configuration Manager.  

> [!NOTE]  
>  Aby uzyskać informacje o sposobie tworzenia kolekcji programu Configuration Manager, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).  

## <a name="how-to-manage-device-collections"></a>Zarządzanie kolekcjami urządzeń  
 W obszarze roboczym **Zasoby i zgodność** wybierz pozycję **Kolekcje urządzeń**, wybierz kolekcję do zarządzania, a następnie wybierz zadanie zarządzania.  

 Więcej informacji o zadaniach zarządzania, które mogą przed wybraniem wymagać dodatkowego opisu, znajduje się w poniższej tabeli.  

|Zadanie zarządzania|Szczegóły|Więcej informacji|  
|---------------------|-------------|----------------------|  
|**Pokaż elementy członkowskie**|Wyświetla wszystkie zasoby należące do wybranej kolekcji w tymczasowym węźle w ramach węzła **Urządzenia** .|Brak dodatkowych informacji.|  
|**Dodaj wybrane elementy**|Udostępnia następujące opcje, które umożliwiają wykonanie jednej z następujących akcji:<br /><br /> - <br />                    **Dodaj wybrane elementy do istniejącej kolekcji urządzeń** -otwiera **Wybieranie kolekcji** okno dialogowe, w którym można wybrać kolekcję, do której chcesz dodać członków wybranej kolekcji. Wybrana kolekcja zostanie dołączona do tej kolekcji przy użyciu reguły członkostwa **Dołącz kolekcje** .<br /><br /> - **Dodaj wybrane elementy do nowej kolekcji urządzeń** -otwiera **kreatorze tworzenia kolekcji urządzeń** umożliwiający utworzenie nowej kolekcji. Wybrana kolekcja zostanie dołączona do tej kolekcji przy użyciu reguły członkostwa **Dołącz kolekcje** .|[Jak utworzyć kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md)|  
|**Zainstaluj klienta**|Otwiera **Kreatora instalacji klienta** która korzysta z instalacji wypychanej klienta do zainstalowania klienta programu Configuration Manager na wszystkich komputerach w wybranej kolekcji.|[Wdrażanie klientów na komputery z systemem Windows](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)|  
|**Zarządzaj żądaniami koligacji**|Otwiera okno dialogowe **Zarządzanie żądaniami koligacji urządzeń użytkownika** , w którym można zatwierdzić lub odrzucić oczekujące żądania określenia koligacji urządzeń użytkownika dla urządzeń w wybranej kolekcji.|[Łączenie użytkowników i urządzeń dzięki koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Usuń wymagane wdrożenia PXE**|Usuwa wszelkie wymagane wdrożenia rozruchu środowiska PXE ze wszystkich elementów członkowskich wybranej kolekcji.|[Wprowadzenie do wdrażania systemu operacyjnego](../../../../osd/understand/introduction-to-operating-system-deployment.md)|  
|**Zaktualizuj członkostwo**|Ocenia członkostwo dla wybranej kolekcji. W przypadku kolekcji z wieloma elementami członkowskimi aktualizowanie może zająć trochę czasu. Użyj akcji **Odśwież** , aby zaktualizować wyświetlane dane z uwzględnieniem nowych elementów członkowskich kolekcji po zakończeniu aktualizacji.|Brak dodatkowych informacji.|  
|**Dodaj zasoby**|Otwiera okno dialogowe **Dodawanie zasobów do kolekcji** , w którym można wyszukać nowe zasoby, aby dodać je do wybranej kolekcji.<br /><br /> Ikona dla wybranej kolekcji wyświetli klepsydry symboli w trakcie aktualizacji.|Brak dodatkowych informacji.|  
|**Powiadomienie klienta**|Powoduje, że wszyscy klienci w wybranej kolekcji urządzeń pobiorą zasady komputera lub użytkownika.|Brak dodatkowych informacji.|  
|**Program Program Endpoint Protection**|Wykonuje pełne lub szybkie skanowanie ochrony przed złośliwym kodem na komputerach w wybranej kolekcji lub pobiera na nie najnowsze definicje dla funkcji ochrony przed złośliwym kodem.|[Ochrona punktu końcowego programu System Center Configuration Manager](../../../../protect/deploy-use/endpoint-protection.md)|  
|**Eksportowanie**|Otwiera **Kreator eksportu kolekcji** pozwala eksportu tej kolekcji do Managed Object Format (MOF) plik, który można następnie zarchiwizowane lub używany w innej lokacji programu Configuration Manager.<br /><br /> Podczas eksportowania kolekcji kolekcje przywoływane przez nią za pomocą reguły **Dołącz** lub **Wyklucz** nie są eksportowane.|Brak dodatkowych informacji.|  
|**Kopiuj**|Tworzy kopię wybranej kolekcji. Nowa kolekcja używa wybranej kolekcji jako kolekcji ograniczającej.|Brak dodatkowych informacji.|  
|**Usuwanie**|Usuwa wybraną kolekcję. Możesz także usunąć wszystkie zasoby w kolekcji z bazy danych lokacji.<br /><br /> Nie można usunąć kolekcji, które są wbudowane w programie Configuration Manager.|Lista wbudowanych kolekcji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Symuluj wdrożenie**|Otwiera **Kreatora symulowania wdrożenia aplikacji** , który umożliwia testowanie wyników wdrożenia aplikacji bez instalowania ani odinstalowywania aplikacji.|[Symulowanie wdrożenia aplikacji z System Center Configuration Manager](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Wdrażanie**|Wyświetla następujące opcje:<br /><br /> - <br />                    **Aplikacja** -otwiera **Kreatora wdrażania oprogramowania** gdzie można wybrać i skonfigurować wdrożenie aplikacji w wybranej kolekcji.<br /><br /> - <br />                    **Program** — otwiera **Kreatora wdrażania oprogramowania** , w którym można wybrać i skonfigurować wdrożenie pakietu i programu do wybranej kolekcji.<br /><br /> - **Linia bazowa konfiguracji** -otwiera **wdrażać linie bazowe konfiguracji** okno dialogowe konfigurowania wdrażania jednego lub więcej linii bazowych konfiguracji do wybranej kolekcji.<br /><br /> - <br />                    **Sekwencja zadań** — otwiera **Kreatora wdrażania oprogramowania** , w którym można wybrać i skonfigurować wdrożenie sekwencji zadań do wybranej kolekcji.<br /><br /> - <br />                    **Aktualizacje oprogramowania** -otwiera **Kreatora wdrażania aktualizacji oprogramowania** konfigurowania wdrożenia aktualizacji oprogramowania do zasobów w wybranej kolekcji.|[Jak wdrażać aplikacje z System Center Configuration Manager](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Pakiety i programy w programie System Center Configuration Manager](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [Jak wdrażać linie bazowe konfiguracji w programie System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md)<br /><br /> [Zarządzanie sekwencjami zadań do automatyzacji zadań w programie System Center Configuration Manager](../../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md)<br /><br /> [Zarządzanie aktualizacjami oprogramowania System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction)|  

## <a name="how-to-manage-user-collections"></a>Zarządzanie kolekcjami użytkowników  
 W obszarze roboczym **Zasoby i zgodność** wybierz pozycję **Kolekcje użytkowników**, wybierz kolekcję do zarządzania, a następnie wybierz zadanie zarządzania.  

 Więcej informacji o zadaniach zarządzania, które mogą przed wybraniem wymagać dodatkowego opisu, znajduje się w poniższej tabeli.  

|Zadanie zarządzania|Szczegóły|Więcej informacji|  
|---------------------|-------------|----------------------|  
|**Pokaż elementy członkowskie**|Wyświetla wszystkie zasoby należące do wybranej kolekcji w tymczasowym węźle w ramach węzła **Użytkownicy** .|Brak dodatkowych informacji.|  
|**Dodaj wybrane elementy**|Ta opcja umożliwia wykonanie jednej z następujących akcji:<br /><br /> - <br />                    **Dodaj wybrane elementy do istniejącej kolekcji użytkowników** -otwiera **Wybieranie kolekcji** okno dialogowe, w którym można wybrać kolekcję, do której chcesz dodać członków wybranej kolekcji. Wybrana kolekcja zostanie dołączona do tej kolekcji przy użyciu reguły członkostwa **Dołącz kolekcje** .<br /><br /> - **Dodaj wybrane elementy do nowej kolekcji użytkowników** -otwiera **kreatorze tworzenia kolekcji użytkowników** umożliwiający utworzenie nowej kolekcji. Wybrana kolekcja zostanie dołączona do tej kolekcji przy użyciu reguły członkostwa **Dołącz kolekcje** .|[Jak utworzyć kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md)|  
|**Zarządzaj żądaniami koligacji**|Otwiera okno dialogowe **Zarządzanie żądaniami koligacji urządzeń użytkownika** , w którym można zatwierdzić lub odrzucić oczekujące żądania określenia koligacji urządzeń użytkownika dla użytkowników w wybranej kolekcji.|[Łączenie użytkowników i urządzeń dzięki koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Zaktualizuj członkostwo**|Ocenia członkostwo dla wybranej kolekcji. W przypadku kolekcji z wieloma elementami członkowskimi aktualizowanie może zająć trochę czasu. Użyj akcji **Odśwież** , aby zaktualizować wyświetlane dane z uwzględnieniem nowych elementów członkowskich kolekcji po zakończeniu aktualizacji.<br /><br /> Ikona dla wybranej kolekcji wyświetli klepsydry symboli w trakcie aktualizacji.|Brak dodatkowych informacji.|  
|**Dodaj zasoby**|Otwiera okno dialogowe **Dodawanie zasobów do kolekcji** , w którym można wyszukać nowe zasoby, aby dodać je do wybranej kolekcji.|Brak dodatkowych informacji.|  
|**Eksportowanie**|Otwiera **Kreator eksportu kolekcji** pomaga wyeksportować tę kolekcję do pliku Managed Object Format (MOF), który następnie może być archiwizowane lub używana w innej lokacji programu Configuration Manager.<br /><br /> Podczas eksportowania kolekcji kolekcje przywoływane przez nią za pomocą reguły **Dołącz** lub **Wyklucz** nie są eksportowane.|Brak dodatkowych informacji.|  
|**Kopiuj**|Tworzy kopię wybranej kolekcji. Nowa kolekcja używa wybranej kolekcji jako kolekcji ograniczającej.|Brak dodatkowych informacji.|  
|**Usuwanie**|Usuwa wybraną kolekcję. Możesz także usunąć wszystkie zasoby w kolekcji z bazy danych lokacji.<br /><br /> Nie można usunąć kolekcji, które są wbudowane w programie Configuration Manager.|Lista wbudowanych kolekcji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Symuluj wdrożenie**|Otwiera **Kreatora symulowania wdrożenia aplikacji** , który umożliwia testowanie wyników wdrożenia aplikacji bez instalowania ani odinstalowywania aplikacji.|[Symulowanie wdrożenia aplikacji z System Center Configuration Manager](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Wdrażanie**|Wyświetla następujące opcje:<br /><br /> - **Aplikacja** -otwiera **Kreatora wdrażania oprogramowania** gdzie można wybrać i skonfigurować wdrożenie aplikacji w wybranej kolekcji.<br /><br /> - <br />                    **Program** — otwiera **Kreatora wdrażania oprogramowania** , w którym można wybrać i skonfigurować wdrożenie pakietu i programu do wybranej kolekcji.<br /><br /> - **Linia bazowa konfiguracji** -otwiera **wdrażać linie bazowe konfiguracji** okno dialogowe konfigurowania wdrażania jednego lub więcej linii bazowych konfiguracji do wybranej kolekcji.|[Jak wdrażać aplikacje z System Center Configuration Manager](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Pakiety i programy w programie System Center Configuration Manager](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [Jak wdrażać linie bazowe konfiguracji w programie System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md)|  

##  <a name="BKMK_CollProp"></a> Właściwości kolekcji  
 Po otwarciu okna dialogowego **Właściwości** dla kolekcji możesz wyświetlić i skonfigurować następujące właściwości dla kolekcji.  

|Nazwa karty|Więcej informacji|  
|--------------|----------------------|  
|**Ogólne**|Umożliwia wyświetlenie i skonfigurowanie ogólnych informacji o wybranej kolekcji, w tym nazwy kolekcji i kolekcji ograniczającej.|  
|**Reguły członkostwa**|Umożliwia skonfigurowanie reguł członkostwa, które definiują członkostwo tej kolekcji. Aby uzyskać więcej informacji, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).|  
|**Zarządzanie energią**|Umożliwia skonfigurowanie planów zarządzania energią, które są przypisane do komputerów w wybranej kolekcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania energią](../../../../core/clients/manage/power/introduction-to-power-management.md).|  
|**Wdrożenia**|Wyświetla nazwy programów, które zostały wdrożone na elementach członkowskich wybranej kolekcji.|  
|**Okna obsługi**|Umożliwia wyświetlenie i skonfigurowanie okien obsługi, które są stosowane dla elementów członkowskich wybranej kolekcji. Aby uzyskać więcej informacji, zobacz [sposobu używania okien obsługi w programie System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).|  
|**Zmienne kolekcji**|Umożliwia skonfigurowanie zmiennych, które dotyczą kolekcji i których mogą używać sekwencje zadań. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](../../../../osd/understand/task-sequence-built-in-variables.md).|  
|**Grupy punktów dystrybucji**|Umożliwia przypisanie co najmniej jednej grupy punktów dystrybucji do elementów członkowskich wybranej kolekcji. Aby uzyskać więcej informacji, zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Zabezpieczenia**|Wyświetla użytkowników administracyjnych, którzy mają uprawnienia do wybranej kolekcji ze względu na skojarzone role i zakresy zabezpieczeń.|  
|**Monitor**|Umożliwia skonfigurowanie czasu generowania alertów stanu klienta i ochrony punktu końcowego. Aby uzyskać więcej informacji, zobacz [jak skonfigurować stan klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-status.md) i [jak monitorować program Endpoint Protection w programie System Center Configuration Manager](../../../../protect/deploy-use/monitor-endpoint-protection.md).|  

