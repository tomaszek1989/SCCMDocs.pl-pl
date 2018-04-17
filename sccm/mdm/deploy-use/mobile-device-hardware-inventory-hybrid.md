---
title: Konfigurowanie spisu sprzętu dla urządzeń przenośnych
titleSuffix: Configuration Manager
description: Konfigurowanie spisu sprzętu dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune i programu System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 78a0aecc-f775-451e-aa05-56377ec91b1f
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c3dcb39b50293d5c221a1b8b13fcfbf8aa53ad83
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-hardware-inventory-for-mobile-devices-enrolled-by-microsoft-intune-and-system-center-configuration-manager"></a>Jak skonfigurować spis sprzętu dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune i programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie Configuration Manager można zebrać spis sprzętu w systemach iOS, Android i Windows urządzeń przy użyciu łącznika programu Microsoft Intune. Aby uzyskać informacje o sposobie konfigurowania spisu sprzętu, zobacz [jak rozszerzyć spis sprzętu w programie System Center Configuration Manager](../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 Aby uzyskać informacje o sposobie rejestrowania urządzeń w programie Microsoft Intune, zobacz [zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn646962.aspx).  

## <a name="hardware-inventory-for-mobile-devices"></a>Spis sprzętu dla urządzeń przenośnych  
 W poniższych tabelach przedstawiono klas sprzętu dostępnych dla spisu sprzętu w często używanych platform urządzeń przenośnych.  

 **iOS**  

|Klasa spisu sprzętu|iOS|  
|------------------------------|---------|  
|Nazwa|Device_ComputerSystem.DeviceName|  
|Unikatowy identyfikator urządzenia|Device_ComputerSystem.UDID|  
|Numer seryjny|Device_ComputerSystem.SerialNumber|  
|Adres e-mail|Device_Email.OwnerEmailAddress|  
|Typ systemu operacyjnego|Nie dotyczy|  
|Wersja systemu operacyjnego|Device_OSInformation.OSVersion|  
|Wersja kompilacji|Nie dotyczy|  
|Wersja główna dodatku Service Pack|Nie dotyczy|  
|Wersja podrzędna dodatku Service Pack|Nie dotyczy|  
|Język systemu operacyjnego|Nie dotyczy|  
|Całkowita ilość miejsca|Device_Memory.DeviceCapacity|  
|Ilość wolnego miejsca|Device_Memory.AvailableDeviceCapacity|  
|International Mobile Equipment Identity lub IMEI (IMEI)|Device_ComputerSystem.IMEI|  
|Identyfikator sprzętu przenośnego (MEID)|Device_ComputerSystem.MEID|  
|Producent|Nie dotyczy|  
|Model|ModelName|  
|Numer telefonu<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Nazwa operatora|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Technologia sieci komórkowej|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **Android**  

> [!NOTE]  
>  **UWAGA:** Klasy spisu dla systemu android są dostępne podczas korzystania z aplikacji Portal firmy dla systemu Android.  

|Klasa spisu sprzętu|Android|  
|------------------------------|-------------|  
|Nazwa|Nie dotyczy|  
|Unikatowy identyfikator urządzenia|Nie dotyczy|  
|Numer seryjny|Device_ComputerSystem.SerialNumber|  
|Adres e-mail|Nie dotyczy|  
|Typ systemu operacyjnego|Device_OSInformation.Platform|  
|Wersja systemu operacyjnego|Device_OSInformation.Version|  
|Wersja kompilacji|Nie dotyczy|  
|Wersja główna dodatku Service Pack|Nie dotyczy|  
|Wersja podrzędna dodatku Service Pack|Nie dotyczy|  
|Język systemu operacyjnego|Nie dotyczy|  
|Całkowita ilość miejsca|Device_Memory.StorageTotal|  
|Ilość wolnego miejsca|Device_Memory.StorageFree|  
|International Mobile Equipment Identity lub IMEI (IMEI)|Device_ComputerSystem.IMEI|  
|Identyfikator sprzętu przenośnego (MEID)|Nie dotyczy|  
|Producent|Device_Info.Manufacturer|  
|Model|Device_Info.Model|  
|Numer telefonu<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Nazwa operatora|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Technologia sieci komórkowej|Device_ComputerSystem.CellularTechnology|  
|Wi-Fi MAC|Device_WLAN.WiFiMAC|  

 **Windows Phone 8/8.1**  

|Klasa spisu sprzętu|Windows Phone 8 i Windows Phone 8.1|  
|------------------------------|-------------------------------------------|  
|Nazwa|Device_ComputerSystem.DeviceName|  
|Unikatowy identyfikator urządzenia|Device_ComputerSystem.DeviceClientID|  
|Numer seryjny|Nie dotyczy|  
|Adres e-mail|Device_Email.OwnerEmailAddress|  
|Typ systemu operacyjnego|Device_OSInformation.Platform|  
|Wersja systemu operacyjnego|Device_ComputerSystem.SoftwareVersion|  
|Wersja kompilacji|Nie dotyczy|  
|Wersja główna dodatku Service Pack|Nie dotyczy|  
|Wersja podrzędna dodatku Service Pack|Nie dotyczy|  
|Język systemu operacyjnego|Device_OSInformation.Language|  
|Całkowita ilość miejsca|Nie dotyczy|  
|Ilość wolnego miejsca|Nie dotyczy|  
|International Mobile Equipment Identity lub IMEI (IMEI)|Nie dotyczy|  
|Identyfikator sprzętu przenośnego (MEID)|Nie dotyczy|  
|Producent|Device_ComputerSystem.DeviceManufacturer|  
|Model|Device_ComputerSystem.DeviceModel|  
|Numer telefonu<sup>1</sup>|Nie dotyczy|  
|Nazwa operatora|Nie dotyczy|  
|Technologia sieci komórkowej|Nie dotyczy|  
|Wi-Fi MAC|Nie dotyczy|  

 **Windows RT**  

|Klasa spisu sprzętu|Windows RT|  
|------------------------------|----------------|  
|Nazwa|Device_ComputerSystem.DeviceName|  
|Unikatowy identyfikator urządzenia|Device_ComputerSystem.DeviceName|  
|Numer seryjny|Nie dotyczy|  
|Adres e-mail|Device_Email.OwnerEmailAddress|  
|Typ systemu operacyjnego|CCM_OperatingSystem .SystemType|  
|Wersja systemu operacyjnego|Win32_OperatingSystem.Version|  
|Wersja kompilacji|Win32_OperatingSystem.BuildNumber|  
|Wersja główna dodatku Service Pack|Win32_OperatingSystem.ServicePackMajorVersion|  
|Wersja podrzędna dodatku Service Pack|Win32_OperatingSystem.ServicePackMinorVersion|  
|Język systemu operacyjnego|Nie dotyczy|  
|Całkowita ilość miejsca|Win32_PhysicalMemory.Capacity|  
|Ilość wolnego miejsca|Win32_OperatingSystem.FreePhysicalMemory|  
|International Mobile Equipment Identity lub IMEI (IMEI)|Nie dotyczy|  
|Identyfikator sprzętu przenośnego (MEID)|Nie dotyczy|  
|Producent|Win32_ComputerSystem.Manufacturer|  
|Model|Win32_ComputerSystem.Model|  
|Numer telefonu<sup>1</sup>|Nie dotyczy|  
|Nazwa operatora|Nie dotyczy|  
|Technologia sieci komórkowej|Nie dotyczy|  
|Wi-Fi MAC|Win32_NetworkAdapter.MACAddress|  

 <sup>1</sup> Cyfry numeru telefonu są wyświetlane jako znaki * z wyjątkiem ostatnich 4 cyfr.  

 Aby spis objął numer telefonu, w urządzeniu musi znajdować się karta SIM, a numer telefonu nadany przez operatora musi być powiązany z tą kartą SIM.  
