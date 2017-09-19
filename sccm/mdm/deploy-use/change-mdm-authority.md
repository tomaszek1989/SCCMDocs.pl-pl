---
title: "Zmienić urzędu zarządzania urządzeniami Przenośnymi | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zmienić urząd zarządzania urządzeniami Przenośnymi z programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune lub na odwrót."
keywords: 
author: dougeby
manager: angrobe
ms.date: 09/14/2017
ms.topic: article
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.openlocfilehash: d24e6e736397a4612db7b47e997d8cb1f97c4de9
ms.sourcegitcommit: 948644072bd158b156f782a4376bcd50fac7c73a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="change-your-mdm-authority"></a>Zmienić urzędu zarządzania urządzeniami Przenośnymi
Począwszy od programu Configuration Manager 1610 wersji, można zmienić urzędu zarządzania urządzeniami Przenośnymi bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Ten temat zawiera kroki, aby zmienić dzierżawy usługi Microsoft Intune istniejące skonfigurowane z konsoli programu Configuration Manager (rozwiązanie hybrydowe) do autonomicznej usługi Intune.

> [!Important]    
> Ten temat dotyczy można zmienić urzędu zarządzania urządzeniami Przenośnymi, gdy użytkownicy nie zostały wcześniej migrowane. Aby zmienić urzędu zarządzania urządzeniami Przenośnymi, po [migracji podzbiór użytkowników](migrate-hybridmdm-to-intunesa.md), zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](migrate-change-mdm-authority.md).

## <a name="key-considerations"></a>Najważniejsze kwestie związane z
Po zmianie do nowego urzędu zarządzania urządzeniami Przenośnymi, będą prawdopodobnie być przejścia (maksymalnie osiem godzin) przed urządzenie sprawdza i synchronizuje się z usługą. Należy skonfigurować ustawienia nowego urzędu zarządzania urządzeniami Przenośnymi (autonomicznej usługi Intune), aby upewnić się, zarejestrowane urządzenia są nadal zarządzane i chronione po zmianie. Należy uwzględnić następujące kwestie:
- Urządzenia muszą połączyć z usługą po zmianie tak, aby ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi (autonomicznej usługi Intune) zastępuje istniejące ustawienia na urządzeniu.
- Po zmianie urząd zarządzania urządzeniami Przenośnymi, niektóre z podstawowych ustawień (takich jak profile) z poprzednich urząd zarządzania urządzeniami Przenośnymi (rozwiązanie hybrydowe) pozostają na urządzeniu przez maksymalnie 7 dni. Zalecane jest skonfigurowanie aplikacji i ustawień (zasady, profile, aplikacje itd.) nowego urzędu zarządzania urządzeniami Przenośnymi tak szybko, jak to możliwe. Ponadto należy wdrożyć ustawienia dla grupy użytkowników, które zawierają użytkowników, którzy mają istniejących zarejestrowanych urządzeń. Gdy urządzenie łączy się z usługą po zmianie urzędu zarządzania urządzeniami Przenośnymi, odbiera nowe ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi. Wszystkie nowo docelowych zasady spowoduje zastąpienie istniejących zasad na urządzeniu.
- Po zmianie nowego urzędu zarządzania urządzeniami Przenośnymi, dane zgodności w konsoli administracyjnej Microsoft Intune może potrwać do tygodnia do precyzyjnie. Jednak stanów zgodności w usłudze Azure Active Directory i na urządzeniu będą dokładne, urządzenia będą nadal chronione.
- Urządzenia, które nie mają skojarzonych użytkowników (zazwyczaj gdy masz iOS Device Enrollment Program lub scenariusze rejestracji zbiorczej) nie są migrowane do nowego urzędu zarządzania urządzeniami Przenośnymi. Dla tych urządzeń należy się z działem pomocy technicznej, aby uzyskać pomoc przenieść je do nowego urzędu zarządzania urządzeniami Przenośnymi.

## <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>Przygotowanie do zmienić urząd zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune
Przejrzyj następujące informacje w celu przygotowania do zmiany urząd zarządzania urządzeniami Przenośnymi:
- Musi mieć Configuration Manager w wersji 1610 lub wyższą, aby zmienić urząd zarządzania urządzeniami Przenośnymi, które mają być dostępne.
- Może potrwać maksymalnie osiem godzin dla urządzeń połączyć się z usługą po przejściu do nowego urzędu zarządzania urządzeniami Przenośnymi.
- Upewnij się, że wszyscy użytkownicy, którzy są obecnie zarządzane przez hybrydowego mają licencji usługi Intune/EMS do nich przypisane przed zmianą urzędu zarządzania urządzeniami Przenośnymi. Licencja gwarantuje, że użytkownik i ich urządzenia są zarządzane przez autonomicznej usługi Intune po zmianie urzędu zarządzania urządzeniami Przenośnymi. Aby uzyskać więcej informacji, zobacz [przypisywanie licencji usługi Intune do kont użytkowników](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Upewnij się, że konto użytkownika Administrator ma przypisanej licencji usługi Intune/EMS i Potwierdź, czy konto użytkownika Administrator zalogować się do usługi Intune przed zmianą do urząd zarządzania urządzeniami Przenośnymi. Urząd zarządzania urządzeniami Przenośnymi powinien być wyświetlany **ustawiony program Configuration Manager** (hybrydowego dzierżawcy) w konsoli administracyjnej Microsoft Intune, przed zmianą urzędu zarządzania urządzeniami Przenośnymi.
- W konsoli programu Configuration Manager usuń wszystkie role menedżera rejestracji urządzeń. Przejdź do **administracji** > **usługi w chmurze** > **subskrypcje usługi Microsoft Intune**, wybierz subskrypcję Microsoft Intune, kliknij przycisk **właściwości**, kliknij przycisk **Menedżera rejestracji urządzeń** i Usuń wszystkie role menedżera rejestracji urządzeń.
- W konsoli programu Configuration Manager należy usunąć istniejące kategorie urządzeń. Przejdź do **zasoby i zgodność** > **omówienie** > **kolekcje urządzeń**, wybierz **Zarządzanie kategorie urządzeń**i Usuń istniejące kategorie urządzeń.
- Powinien istnieć bez zauważalnego wpływu użytkownikom końcowym podczas zmiany urzędu zarządzania urządzeniami Przenośnymi. 
- Jeśli używasz programu Configuration Manager (hybrydowego dzierżawcy) do zarządzania urządzeniami z systemem iOS przed zmianą urzędu zarządzania urządzeniami Przenośnymi, należy się upewnić, że tego samego certyfikatu firmy Apple Push Notification service (APNs), który był wcześniej używany w programie Configuration Manager jest odnowiony i użyty do skonfigurowania dzierżawy ponownie w autonomicznej usługi Intune.

   > [!IMPORTANT]  
   > Jeśli inny certyfikat usługi APN jest używany w przypadku autonomicznej usługi Intune, a następnie wszystkie wcześniej zarejestrowane urządzenia z systemem iOS będzie anulowana i będzie musiał przejść przez proces, aby zarejestruj je ponownie. Przed wykonaniem urząd zarządzania urządzeniami Przenośnymi zmian, upewnij się, że znasz dokładnie APNs certyfikat, który został użyty do zarządzania urządzeniami z systemem iOS w programie Configuration Manager. Znajdź tego samego certyfikatu, które są wyświetlane w portalu Apple Push Certificates (https://identity.apple.com) i upewnij się, że użytkownik o identyfikatorze firmy Apple użyty do tworzenia oryginalnego certyfikatu usługi APN jest zidentyfikowane i dostępne, aby odnowić ten sam certyfikat APNs w ramach przejścia do nowego urzędu zarządzania urządzeniami Przenośnymi.  

## <a name="change-the-mdm-authority-to-intune-standalone"></a>Zmień autonomicznej usługi Intune urząd zarządzania urządzeniami Przenośnymi
Proces można zmienić urząd zarządzania urządzeniami Przenośnymi na autonomicznej usługi Intune obejmuje następujące ogólne kroki:  
- W konsoli programu Configuration Manager za pomocą **zmiany urzędu zarządzania urządzeniami Przenośnymi w usłudze Microsoft Intune** opcję, aby usunąć istniejącą subskrypcję Microsoft Intune.
- W konsoli administracyjnej Microsoft Intune, ustaw urząd zarządzania urządzeniami Przenośnymi nowe **Intune**.
- Konfigurowanie certyfikatu Apple APNs przy użyciu tego samego zostanie odnowiony certyfikat APNs.
- W konsoli administracyjnej Microsoft Intune Konfigurowanie i wdrażanie nowych ustawień i aplikacji z nowego urzędu zarządzania urządzeniami Przenośnymi (Intune).
- Dalej urządzeń czas połączyć się z usługą, zostanie synchronizacji i zastosować nowe ustawienia z nowego urzędu zarządzania urządzeniami Przenośnymi.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>Aby zmienić urząd zarządzania urządzeniami Przenośnymi autonomicznej usługi Intune.
1. W konsoli programu Configuration Manager, przejdź do **administracji** &gt; **omówienie** &gt; **usługi w chmurze** &gt; **subskrypcję usługi Microsoft Intune**i usuń istniejącą subskrypcję usługi Intune.
2. Wybierz **zmiany urzędu zarządzania urządzeniami Przenośnymi w usłudze Microsoft Intune**, a następnie kliknij przycisk **dalej**.
   ![Pobierz żądanie certyfikatu APNs](./media/mdm-change-delete-subscription.png)
3. Zaloguj się do dzierżawy usługi Intune, która pierwotnie używana po ustawieniu urzędu zarządzania urządzeniami Przenośnymi w programie Configuration Manager.
4. Kliknij przycisk **Dalej** i ukończ pracę kreatora.
5. Urząd zarządzania urządzeniami Przenośnymi została zresetowana. Subskrypcję usługi Intune powinien przestanie być wyświetlana w węźle subskrypcje usługi Microsoft Intune w konsoli programu Configuration Manager.
6. Zaloguj się do [konsoli administracyjnej Microsoft Intune](http://manage.microsoft.com) przy użyciu tej samej dzierżawy usługi Intune używany w starszych.
7. Upewnij się, że urząd zarządzania urządzeniami Przenośnymi została resetowania, a następnie ustaw urząd zarządzania urządzeniami Przenośnymi jako **Microsoft Intune**. Po zmianie urząd zarządzania urządzeniami Przenośnymi, powinien pojawić się on odzwierciedlone w konsoli. Aby uzyskać więcej informacji, zobacz [jak ustawić urząd zarządzania urządzeniami Przenośnymi](https://docs.microsoft.com/en-us/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).
<!-- [Azure portal](https://docs.microsoft.com/en-us/intune-azure/enroll-devices/set-mdm-authority) -->


## <a name="configure-the-apns-certificate"></a>Konfigurowanie certyfikatu APNs
Jeśli masz urządzenia z systemem iOS, należy skonfigurować certyfikat APNs w usłudze Intune.

#### <a name="to-configure-the-apns-certificate"></a>Aby skonfigurować certyfikat APNs
1. Pobierz żądanie certyfikatu APNs.
   <!--The process is different depending on how you connect to Intune:
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment** &gt; **Apple MDM Push Certificate**, and then select **Download your CSR** to download and save the .csr file locally.   
    <br/>
    **Microsoft Intune administration console**   -->
   W [konsoli administracyjnej Microsoft Intune](http://manage.microsoft.com), przejdź do **administracji** &gt; **zarządzanie urządzeniami przenośnymi** &gt; **z systemem iOS i Mac OS X** &gt; **Przekaż certyfikat APNs**, a następnie wybierz pozycję **Pobierz żądanie certyfikatu APNs**. Zapisz lokalnie plik żądania podpisania certyfikatu (CSR).
   > [!IMPORTANT]    
   > Pobierz żądanie podpisania certyfikatu nowe. Nie należy używać istniejącego pliku, lub zakończy się niepowodzeniem.

   ![Pobierz żądanie certyfikatu APNs](./media/mdm-change-download-apns-certificate.png)

2. Przejdź do [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844)i zaloguj się przy **tego samego** Apple ID, który został użyty do wcześniej tworzenia i odnawiania certyfikatu APNs, który został użyty w programie Configuration Manager (rozwiązanie hybrydowe).

   ![Stronę logowania w portalu Apple Push Certificates](./media/mdm-change-apns-portal.png)

3. Wybierz certyfikat APNs, który został użyty w programie Configuration Manager (rozwiązanie hybrydowe), a następnie kliknij przycisk **odnawiania**.   

    ![Odnów APNs — okno dialogowe](./media/mdm-change-renew-apns.png)

4. Wybierz APNs plik żądania podpisania certyfikatu (CSR) pobranego lokalnie, a następnie kliknij przycisk **przekazać**.

    ![Stronę logowania w portalu Apple Push Certificates](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-upload.png)
 
5. Wybierz tej samej usługi APNs, a następnie kliknij przycisk **Pobierz**. Pobierz certyfikat usługi APN (PEM) i Zapisz plik lokalnie.  

   ![Stronę logowania w portalu Apple Push Certificates](./media/mdm-change-renew-apns-download.png)

6. Przekazać odnowiony certyfikat APNs do dzierżawy usługi Intune przy użyciu tego samego Identyfikatora Apple jako przed.
<!--The process is different depending on how to connect to Intune:  
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment**  &gt; **Apple MDM Push Certificate**, enter your Apple ID in step 3, select the certificate (.pem) file in step 4, and then click **Upload**.     
    <br/>
    **Microsoft Intune administration console**    -->
    In the [Microsoft Intune administration console](http://manage.microsoft.com), go to **Administration** &gt; **Mobile Device Management** &gt; **iOS and Mac OS X** &gt; **Upload an APNs Certificate**, and then choose **Upload the APNs certificate**. Go to the certificate (.pem) file, choose **Open**, and then enter your **Apple ID**.   

   ![Przekaż certyfikat APNs](./media/mdm-change-upload-apns-certificate.png)

## <a name="next-steps"></a>Następne kroki
Po zakończeniu zmiany urzędu zarządzania urządzeniami Przenośnymi, przejrzyj poniższe kroki:
- Gdy usługi Intune wykryje, że urząd zarządzania urządzeniami Przenośnymi dzierżawy została zmieniona, wysyła powiadomienie do wszystkich zarejestrowanych urządzeń można sprawdzić i zsynchronizować z usługą (jest to poza zaplanowanego zaewidencjonowania). W związku z tym po urząd zarządzania urządzeniami Przenośnymi dla dzierżawy została zmieniona z hybrydowego do autonomicznej usługi Intune, wszystkie urządzenia, które są włączone i online będą łączyć się z usługą, odbierania nowego urzędu zarządzania urządzeniami Przenośnymi i zarządzany przez autonomiczną usługę Intune w przyszłości. Nie będzie żadnych przeszkód do zarządzania i ochrony tych urządzeń.
- Urządzenia, które są zasilane poza lub w trybie offline podczas (lub wkrótce po) Zmień urzędu zarządzania urządzeniami Przenośnymi nawiązać połączenie i synchronizacji z usługi w obszarze nowe urzędu zarządzania urządzeniami Przenośnymi, gdy są włączone i online.  

  urządzenia z systemem iOS wymaga dodatkowego czasu, aby odnowić i skonfiguruj certyfikat APN. W związku z tym urządzenia z systemem iOS nie będą otrzymywać początkowej wyboru w żądaniu. Nawet jeśli urządzenia z systemem iOS jest włączona i w trybie online podczas (lub wkrótce po) zmiany urzędu zarządzania urządzeniami Przenośnymi, nastąpi opóźnienie maksymalnie osiem godzin (w zależności od czasu następnego zaplanowanego sprawdzania regularne w) przed zarejestrowanych urządzeń z systemem iOS w usłudze nowego urzędu zarządzania urządzeniami Przenośnymi.    

  > [!IMPORTANT]
  > Czas, po zmianie zarządzania urządzeniami Przenośnymi między urzędu i po przekazaniu odnowionego certyfikatu APN do nowego urzędu, nowe rejestracje urządzenia i urządzenia Wyszukaj w zakończą się urządzeń z systemem iOS. Dlatego jest ważne, możesz sprawdzić i przekaż certyfikat APNs do nowego urzędu certyfikacji, jak najszybciej po zmianie urzędu zarządzania urządzeniami Przenośnymi.   

- Użytkowników można szybko zmienić nowego urzędu zarządzania urządzeniami Przenośnymi należy ręcznie uruchomić wyboru w z urządzenia do usługi. Użytkownicy można łatwo to zrobić przy użyciu aplikacji Portal firmy i Inicjowanie sprawdzenie zgodności urządzenia.
- Aby sprawdzić, czy elementy działają prawidłowo po urządzenia mają zaewidencjonowania i zsynchronizowane z usługą po zmianie urzędu zarządzania urządzeniami Przenośnymi, wyszukaj urządzenia [konsoli administracyjnej Microsoft Intune](http://manage.microsoft.com). Urządzenia, które wcześniej były zarządzane przez program Configuration Manager (rozwiązanie hybrydowe) zostaną wyświetlone jako zarządzanych urządzeń.    
- Brak okres przejściowy, gdy urządzenie jest w trybie offline podczas zmiany urzędu zarządzania urządzeniami Przenośnymi i zaewidencjonowaniu tego urządzenia do usługi. Aby upewnić się, że urządzenie pozostaje chroniony i funkcjonalności w tym okresie przejściowym, następujące pozostanie na urządzeniu przez siedem dni (lub dopóki urządzenie łączy się z nowego urzędu zarządzania urządzeniami Przenośnymi i odbiera nowe ustawienia, które zastąpią istniejące):
    - Profil poczty e-mail
    - Profil sieci VPN
    - Profil certyfikatu
    - Profil sieci Wi-Fi
    - Profilów konfiguracji
- Upewnij się, że nowe ustawienia, które mają na celu zastąpienie istniejących ustawień ma taką samą nazwę jak poprzednimi, aby upewnić się, że stare ustawienia zostaną zastąpione. W przeciwnym razie urządzenia mogą wystąpić nadmiarowe profile i zasady.    

  > [!TIP]   
  > Najlepszym rozwiązaniem należy utworzyć wszystkie ustawienia zarządzania i konfiguracji, a także wdrożeń później, po zakończeniu zmiany urząd zarządzania urządzeniami Przenośnymi. Dzięki temu, upewnij się, że urządzenia są chronione i aktywnie zarządzana w okresie przejściowym.   
-  Po zmianie urząd zarządzania urządzeniami Przenośnymi, wykonaj następujące kroki, aby sprawdzić poprawność pomyślnie zarejestrowane nowych urządzeń do nowego urzędu certyfikacji:   
    - Zarejestruj nowe urządzenie
    - Upewnij się, że nowo zarejestrowanym urządzeniu zostaną wyświetlone w konsoli administracyjnej usługi Intune.
    - Wykonaj akcję, takie jak zdalne blokowanie za pomocą konsoli administracyjnej na urządzeniu. Jeśli ten zakończy się powodzeniem, urządzenie jest zarządzany przez nowego urzędu zarządzania urządzeniami Przenośnymi.
- Jeśli masz problemy z określonymi urządzeniami, musisz wyrejestrować i Zarejestruj ponownie urządzenia do ich podłączenie do nowego urzędu certyfikacji i zarządzanie nimi tak szybko, jak to możliwe.

<!-- After the change in MDM authority and devices check in with the service, note the following:      - The updated compliance status of devices will only display in the Azure portal immediately.
- There will be a delay for compliance status of devices to display in the Intune administrative console.-->