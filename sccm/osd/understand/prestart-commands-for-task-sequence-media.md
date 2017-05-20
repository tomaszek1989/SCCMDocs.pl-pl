---
title: "Polecenia dla nośnika sekwencji zadań przeduruchomieniowe | Dokumentacja firmy Microsoft"
description: "Tworzenie skryptu w celu użycia dla polecenia przeduruchomieniowego, dystrybucję zawartości powiązanej z poleceniem przeduruchomieniowym oraz konfigurowanie polecenia przeduruchomieniowego na nośniku."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccc9f652-2953-4c38-8a90-c799484105ca
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 1c396534425179c6828d48acc578295167c566be
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prestart-commands-for-task-sequence-media-in-system-center-configuration-manager"></a>Polecenia przeduruchomieniowe dla nośnika sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Polecenia przeduruchomieniowego można utworzyć w programie System Center Configuration Manager do użycia z nośnika rozruchowego, nośniki samodzielne i nośniki. Polecenie przeduruchomieniowe to skrypt lub plik wykonywalny, który jest wykonywany przed wybraniem sekwencji zadań i może wchodzić w interakcję z użytkownikiem w systemie Windows PE. Polecenie przeduruchomieniowe może monitować użytkownika o informacje i zapisywać je w środowisku sekwencji zadań lub wykonywać kwerendę zmiennej sekwencji zadań w celu uzyskania informacji. Po uruchomieniu komputera docelowego wiersz polecenia jest uruchamiany przed pobraniem zasad z punktu zarządzania. Poniższe procedury umożliwiają tworzenie skryptu w celu użycia dla polecenia przeduruchomieniowego, dystrybucję zawartości powiązanej z poleceniem przeduruchomieniowym oraz konfigurowanie polecenia przeduruchomieniowego na nośniku.  

## <a name="create-a-script-file-to-use-for-the-prestart-command"></a>Tworzenie pliku skryptu w celu użycia dla polecenia przeduruchomieniowego  
 Zmienne sekwencji zadań można odczytywać i zapisywać podczas działania sekwencji zadań za pośrednictwem obiektu COM Microsoft.SMS.TSEnvironment. Poniższy przykład przedstawia plik skryptu w języku Visual Basic, który odpytuje zmienną sekwencji zadań _SMSTSLogPath, aby uzyskać bieżącą lokalizację dziennika. Skrypt ustawia ponadto zmienną niestandardową.  

```  
dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")  
dim logPath  
' You can query the environment to get an existing variable.  
logPath = env("_SMSTSLogPath")  
' You can also set a variable in the OSD environment.  
env("MyCustomVariable") = "varname"  
```  

## <a name="create-a-package-for-the-script-file-and-distribute-the-content"></a>Tworzenie pakietu dla pliku skryptu i dystrybucja zawartości  
 Po utworzeniu skryptu lub pliku wykonywalnego dla polecenia przeduruchomieniowego należy utworzyć źródło pakietu, które będzie zawierać pliki dla tego skryptu lub pliku wykonywalnego, utworzyć pakiet dla plików (nie jest wymagany żaden program), a następnie dokonać dystrybucji zawartości do punktu dystrybucji.  

 Aby uzyskać więcej informacji o tworzeniu pakietów, zobacz [pakietów i programów](../../apps/deploy-use/packages-and-programs.md).  

 Aby uzyskać więcej informacji o dystrybucji zawartości, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

## <a name="configure-the-prestart-command-in-media"></a>Konfigurowanie polecenia przeduruchomieniowego na nośniku  
 Polecenie przeduruchomieniowe można skonfigurować w Kreatorze tworzenia nośnika sekwencji zadań dla nośnika rozruchowego, nośnika samodzielnego lub nośnika wstępnie przygotowanego. Aby uzyskać więcej informacji o typach nośników, zobacz [Utwórz nośnik sekwencji zadań](../deploy-use/create-task-sequence-media.md). Aby utworzyć polecenie przeduruchomieniowe na nośniku, należy czynności opisane w poniższej procedurze.  

#### <a name="to-create-a-prestart-command-in-media"></a>Aby utworzyć polecenie przeduruchomieniowe na nośniku  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybierz typ nośnika** wybierz opcję **Nośnik samodzielny**, **Nośnik rozruchowy**lub **Nośnik wstępny**, a następnie kliknij przycisk **Dalej**.  

5.  Przejdź w kreatorze do strony **Dostosowywanie** . Aby uzyskać więcej informacji o konfigurowaniu innych stron w kreatorze, zobacz [Utwórz nośnik sekwencji zadań](../deploy-use/create-task-sequence-media.md).  

6.  Na stronie **Dostosowywanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz opcję **Włącz polecenie przeduruchomieniowe**.  

    -   W polu tekstowym **Wiersz polecenia** wprowadź skrypt lub plik wykonywalny, który został utworzony dla polecenia przeduruchomieniowego.  

        > [!IMPORTANT]  
        >  Użyj **cmd /C < polecenie przeduruchomieniowe\>**  , aby określić polecenie przeduruchomieniowe. Jeśli na przykład użyto nazwy TSScript.vbs dla skryptu polecenia przeduruchomieniowego, wpisz polecenie **cmd /C TSScript.vbs** w wierszu polecenia. Polecenie **cmd /C** powoduje otwarcie nowego okna interpretera poleceń systemu Windows i użycie zmiennej środowiskowej ścieżki w celu znalezienia skryptu lub pliku wykonywalnego polecenia przeduruchomieniowego. Można także określić pełną ścieżkę do polecenia przeduruchomieniowego, ale litera dysku może się różnić na komputerach z innymi konfiguracjami dysków.  

    -   Wybierz opcję **Dołącz pliki dla polecenia przeduruchomieniowego**.  

    -   Kliknij przycisk **Ustaw** , aby wybrać pakiet powiązany z plikami polecenia przeduruchomieniowego.  

    -   Kliknij przycisk **Przeglądaj** , aby wybrać punkt dystrybucji z zawartością dla polecenia przeduruchomieniowego.  

7.  Ukończ pracę kreatora.  

