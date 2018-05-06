---
title: Rozwiązywanie problemów z SCAP
titleSuffix: Configuraton Manager
description: Importowanie ustawień zgodności SCAP jako linie bazowe konfiguracji i eksportowanie wyników
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 27261853-1641-4826-98c6-afbb73a1209d
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 05010d73916ac4c012c157a470ed98dce47fc747
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshoot-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>Rozwiązywanie problemów z rozszerzeń SCAP dla programu Microsoft System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

> [!Tip]  
> Ta funkcja została wprowadzona w wersji zapoznawczej Technical Preview 1803 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Ta wersja wstępna rozszerzeń SCAP można zainstalować w żadnej wersji obecnie obsługiwane w bieżącej gałęzi programu Configuration Manager i LTSB 1606. Plik instalacji znajduje się w cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi począwszy od wersji technical preview 1803. 

Rozszerzenia SCAP dla programu Microsoft System Center Configuration Manager zostały zaprojektowane do pracy ze strumieniami danych SCAP dla zweryfikowanego narzędzia SCAP z możliwością ACS, obsługującego linie USGCB. Zazwyczaj nie występują problemy z tych strumieni danych USGCB SCAP, które zostały pobrane z witryny internetowej NIST.

Można jednak zdiagnozować i rozwiązać problemy, że mogą zostać wyświetlone przy użyciu następujących metod:

- Upewnij się, że zainstalowano rozszerzenia SCAP składniki klienta (scmdcm.msi) na wszystkich komputerach docelowych.
- Przejrzyj dane wyjściowe pliku dziennika narzędzia Microsoft.Sces.ScapToDcm.exe.
- Przejrzyj typowe problemy i rozwiązania, korzystając z rozszerzeń SCAP.
- Kontakt z firmą Microsoft, aby przekazać pytania lub opinie na temat rozszerzeń SCAP.



## <a name="review-microsoftscesscaptodcmexe-tool-log"></a>Przejrzyj dziennik Microsoft.Sces.ScapToDcm.exe narzędzia

Narzędzie Microsoft.Sces.ScapToDcm.exe tworzy dostosowany, nazwany dziennika plików podczas — dziennik został określony parametr. Plik dziennika zawiera informacje na temat wyników pracy narzędzia Microsoft.Sces.ScapToDcm.exe. Na przykład plik dziennika zawiera liczbę elementów w pliku wejściowym XCCDF/DataStream, które zostały porzucone lub pominięte podczas pracy narzędzia Microsoft.Sces.ScapToDcm.exe.

W poniższej tabeli wymieniono niektóre informacje pojawiające się w pliku dziennika oraz opis poszczególnych typów informacji.

### <a name="description-of-information-found-in-microsoftscesscaptodcmexe-log-files"></a>Opis informacji zamieszczonych w plikach dziennika Microsoft.Sces.ScapToDcm.exe

| Informacje | Opis |
| --- | --- |
| Upuść | Element może zostać porzucony typu testu nie jest obsługiwanym typem testu. |
| Pomiń |Identyfikator definicji OVAL dotyczy nieprawidłowej platformy. </br> </br> Identyfikator definicji OVAL nie odwołuje się do pliku wejściowym XCCDF/DataStream.</br> </br> Identyfikator testu OVAL nie odwołuje się do pliku wejściowym XCCDF/DataStream. </br> </br> Identyfikator profilu XCCDF nie zawiera żadnych @select instrukcje równa 1. </br> </br> Identyfikator profilu XCCDF zawiera atrybut abstrakcyjny, który ma wartość true. </br> </br> Identyfikator profilu XCCDF nie zawiera reguły kwalifikacji.|

## <a name="common-problems-and-solutions"></a>Typowe problemy i rozwiązania

W poniższej tabeli wymieniono niektóre typowe problemy i rozwiązania, aby pomóc w rozwiązywaniu problemów.

1.6 tabeli typowe problemy i rozwiązania

| Problem | Możliwe rozwiązanie |
| --- | --- |
| Jeśli **błąd** lub **nieznany** stany linii bazowej, a program IE nie może pomyślnie wyświetlić raportu. IE mówi &quot;raport jest pusty lub nieprawidłowy&quot; | Wybierz linię bazową, a następnie kliknij przycisk **Evaluate** Aby ponownie uruchomić linię bazową, a następnie Monitoruj **stan zgodności**/**aktualizacji ostatnia ocena**. Po uaktualnieniu daty ostatnia ocena do bieżącej daty/godziny (co oznacza ukończenie oceny), wybierz linię bazową i Wyświetl raport ponownie. Jeśli w programie IE nadal nie można wyświetlić raportu, może to oznaczać, że linia bazowa jest zbyt duży. Wygeneruj ponownie zawartości przy użyciu mniejszego rozmiaru wsadu, aby utworzyć mniejsze podrzędne linie bazowe. Jeśli ten problem wystąpi w nadrzędnych linii bazowych, spróbuj zamiast niej wdrażanie podrzędne linie bazowe. |
| I zostały utworzone obiekty zasad grupy (GPO), które zawierają wymagane ustawienia USGCB i powiązany jednostek organizacyjnych (OU), które zawierają komputery z systemem Windows 7, jednak raporty zgodności wskazują, że niektóre ustawienia nie są skonfigurowane poprawnie. | Istnieje możliwość, że uprawnienia zasad grupy są niepoprawne lub że nie zostały one połączone z poprawną jednostką organizacyjną. Jednak jest bardziej prawdopodobne, że nowe ustawienia nie zostały uwzględnione jeszcze. Domyślnie zasady grupy na komputerach klienckich, które należą do domeny usługi Active Directory do sprawdzania aktualizacji zasad grupy co 90 minut. Może to być powodem, dlaczego ustawienia wydają się nie zostały zastosowane, nawet jeśli zasady zostały poprawnie skonfigurowane. Innym czynnikiem do zapamiętania jest, że wiele ustawień komputer wymaga ponownego uruchomienia przed wejściem w życie. Na przykład, ustawienie o nazwie ** Kryptografia systemu: Użyj zgodnych algorytmów FIPS dla celów szyfrowania, mieszania i podpisywania, wymagane jest ponowne uruchomienie komputera, zanim systemu Windows można użyć określonych algorytmów szyfrowania. Interwał odświeżania zasad grupy można pominąć, wprowadzając następujące polecenie w wierszu polecenia z uprawnieniami administratora: gpupdate/force po zasady grupy ukończeniu odświeżania, uruchom ponownie komputer, aby upewnić się, że wszystkie ustawienia zostały zastosowane. Aby uzyskać więcej informacji, zobacz: [Opis narzędzia aktualizacji zasad grupy](http://support.microsoft.com/kb/298444), artykuł 298444 w bazy wiedzy Knowledge Base. |
| Mam problemy, zapewniając połączenie z bazą danych z informacji o organizacji. | Procedurach informacji o sposobie konfigurowania informacje o połączeniu bazy danych, zobacz [zainstalować i skonfigurować SCAP](/sccm/compliance/plan-design/scap/install-configure-scap) artykułu. 

## <a name="next-step"></a>Następny krok
> [!div class="nextstepaction"]
> [Instalowanie i konfigurowanie rozszerzeń protokołu SCAP](/sccm/compliance/plan-design/scap/install-configure-scap)