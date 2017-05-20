---
title: "Podstawy zabezpieczeń | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o warstwy zabezpieczeń dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d56c8a76e4770336d4a2ab519e776e48fec8ebcd
ms.openlocfilehash: df3198885259b1db4a1aadee0db6512a1a2d4911
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>Podstawowe informacje na temat zabezpieczeń programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zabezpieczenia programu System Center Configuration Manager składa się z kilku warstw. Pierwsza warstwa jest świadczona przez funkcji zabezpieczeń systemu Windows dla systemu operacyjnego i sieci i obejmuje:  

-   Udostępnianie plików do transferu plików między składnikami programu Configuration Manager.  

-   Listy kontroli dostępu (ACL) ułatwiające zabezpieczanie plików oraz kluczy rejestru.  

-   Zabezpieczenia protokołu internetowego (IPsec) bezpieczną komunikację.  

-   Zasady grupy do ustawiania zasad zabezpieczeń.  

-   Rozproszone uprawnień modelu DCOM (Component Object) dla aplikacji rozproszonych, takich jak konsola programu Configuration Manager.  

-   Usług domenowych Active Directory do przechowywania podmiotów zabezpieczeń.  

-   Zabezpieczenia konta Windows, w tym niektórych grup utworzonych podczas instalacji programu Configuration Manager.  

Kolejne dodatkowe składniki zabezpieczeń, takich jak zapory i funkcje wykrywania nieautoryzowanego dostępu, zapewniają obrony w całym środowisku. Certyfikaty wydane przez branży pomoc implementacje standardowych infrastruktury kluczy publicznych (PKI) zapewniają uwierzytelnianie, podpisywanie i szyfrowanie.  

Dodatkowa zabezpieczeń systemu Windows server i infrastruktury sieci Menedżer konfiguracji kontroluje dostęp do konsoli programu Configuration Manager i jej zasobów na kilka sposobów. Domyślnie tylko lokalni administratorzy mają dostęp do plików i kluczy rejestru, które są wymagane do uruchamiania konsoli programu Configuration Manager na komputerach, w którym jest zainstalowany.  

Kolejna warstwa zabezpieczeń bazuje na dostępie przy użyciu Instrumentacji zarządzania Windows (WMI), konkretnie na dostawcy programu SMS. Dostawca programu SMS jest składnika programu Configuration Manager, która udziela użytkownikowi dostępu do informacji w bazie danych lokacji. Domyślnie dostęp do dostawcy jest ograniczony do członków lokalnej grupy administratorów programu SMS. Ta grupa w najpierw zawiera tylko użytkownik, który zainstalował program Configuration Manager. Aby przydzielić innym kontom uprawnienie do repozytorium modelu wspólnych informacji (CIM) i dostawcy programu SMS, należy dodać te konta do grupy administratorów programu SMS.  

Ostatnia warstwa zabezpieczeń bazuje na uprawnieniach do obiektów w bazie danych lokacji. Domyślnie lokalne konto systemowe i konto użytkownika używane do zainstalowania programu Configuration Manager umożliwia administrowanie wszystkimi obiektami w bazie danych lokacji. Można przydzielić lub odebrać uprawnienia użytkownikom administracyjnym dodatkowe w konsoli programu Configuration Manager za pomocą administracji opartej na rolach.  



## <a name="role-based-administration"></a>Administracja oparta na rolach  
 Program Configuration Manager używa administracji opartej na rolach, aby zabezpieczać takie obiekty jak kolekcje, wdrożenia i lokacje. Ten model administrowania definiuje w sposób centralny ustawienia bezpiecznego dostępu w całej hierarchii do wszystkich witryn i ustawień lokacji oraz pozwala nimi zarządzać. Role zabezpieczeń są przypisywane do użytkowników administracyjnych i uprawnienia grupy. Uprawnienia są podłączone do różnych typów obiektów programu Configuration Manager, takie jak uprawnienia, które są używane do tworzenia lub zmiany ustawień klienta. Zakresy zabezpieczeń pozwalają grupować konkretne wystąpienia obiektów, które użytkownik administracyjny jest odpowiedzialny do zarządzania, takich jak aplikacja, która instaluje program Microsoft Office. Połączenie ról zabezpieczeń, zakresy zabezpieczeń i kolekcji definiuje obiekty, które użytkownik administracyjny można wyświetlać i zarządzać nimi. Program Configuration Manager instaluje pewne domyślne role zabezpieczeń dotyczące typowych zadań zarządzania. Można jednak tworzyć własne role zabezpieczeń stosownie do konkretnych potrzeb biznesowych.  

 Aby uzyskać więcej informacji, zobacz [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="securing-client-endpoints"></a>Zabezpieczanie punktów końcowych klienta  
 Komunikacja klienta z rolami systemu lokacji jest zabezpieczana za pomocą certyfikatów z podpisem własnym lub za pomocą certyfikatów PKI. Należy użyć certyfikatu PKI dla komputerów klienckich, które Configuration Manager wykryje się w Internecie, a dla klientów urządzeń przenośnych. Certyfikatu PKI używa protokołu HTTPS w celu zabezpieczenia punktów końcowych klienta. Role systemu lokacji, z którymi łączą się klienci, można skonfigurować do komunikacji HTTPS lub HTTP. Komputery klienckie zawsze komunikują się za pomocą najbardziej bezpiecznej metody, która jest dostępna. Komputery klienckie tylko wrócić do korzystania na mniej bezpieczną metodę komunikacji HTTP w intranecie Jeśli rola systemu lokacji zezwala na komunikację HTTP.  

 Aby uzyskać więcej informacji, zobacz [szyfrowania formanty techniczne dla programu System Center Configuration Manager](../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

## <a name="configuration-manager-accounts-and-groups"></a>Konta i grupy programu Configuration Manager  
 Program Configuration Manager używa konta systemu lokalnego dla większości operacji lokacji. Niektóre zadania zarządzania mogą wymagać do tworzenia i utrzymywania dodatkowych kont. Podczas instalacji są tworzone różne domyślne grupy i role programu SQL Server. Może być konieczne ręczne dodanie konta użytkownika lub komputera do domyślnych grup i ról programu SQL Server.  

 Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md).  

## <a name="privacy"></a>Ochrona prywatności  
 Mimo że produkty przeznaczone do zarządzania przedsiębiorstwem oferują wiele zalet, ponieważ umożliwiają wydajne zarządzanie wieloma klientami, należy wziąć pod uwagę ich wpływ na prywatność użytkowników w organizacji. System Center Configuration Manager udostępnia wiele narzędzi do gromadzenia danych i monitorowania urządzeń. Niektóre narzędzia mogą budzić zastrzeżenia co do zachowania poufności informacji.  

 Na przykład po zainstalowaniu klienta programu Configuration Manager wiele ustawień zarządzania są domyślnie włączone. To sprawia, że oprogramowanie klienta do wysyłania informacji do lokacji programu Configuration Manager. Informacje o kliencie są przechowywane w bazie danych programu Configuration Manager, a informacje nie są wysyłane do firmy Microsoft. Przed zaimplementowaniem programu System Center Configuration Manager, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

