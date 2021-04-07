---
title: Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi
titleSuffix: ''
description: Informacje o narzędziach, których można użyć do wykrywania instalacji programu Visual Studio i zarządzania nimi na komputerach klienckich.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b6b641081c9b969cadd2c9517967adb8cc4cb1e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547443"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania instalacji programu Visual Studio na komputerach klienckich i zarządzania instalacjami.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejących wystąpień programu Visual Studio

Następujące narzędzia i programy narzędziowe ułatwią wykrywanie zainstalowanych wystąpień programu Visual Studio i zarządzanie nimi na komputerach klienckich:

* [**vswhere**](https://github.com/microsoft/vswhere): plik wykonywalny wbudowany w program Visual Studio lub dostępny w oddzielnym dystrybucji, który ułatwia znalezienie lokalizacji wszystkich wystąpień programu Visual Studio na konkretnym komputerze.
* [**VSSetup. PowerShell**](https://github.com/microsoft/vssetup.powershell): skrypty programu PowerShell, które używają interfejsu API konfiguracji Instalatora do identyfikowania zainstalowanych wystąpień programu Visual Studio.
* [**Vs-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): przykłady języków C# i C++, które pokazują, jak używać interfejsu API konfiguracji Instalatora do wysyłania zapytań do istniejącej instalacji.
* [**Instrumentacja zarządzania Windows (WMI)**](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page): informacje o wystąpieniu programu Visual Studio mogą być wysyłane za pomocą MSFT_VSInstance klasy Visual Studio. 
* [**Interfejs API konfiguracji Instalatora**](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć własne narzędzia do Interrogating wystąpień programu Visual Studio.
* [**Spis oprogramowania Microsoft Endpoint Configuration Manager**](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): służy do zbierania informacji o wystąpieniach programu Visual Studio na urządzeniach klienckich. 

## <a name="using-vswhereexe"></a>Używanie vswhere.exe

`vswhere.exe` jest automatycznie dołączany do programu Visual Studio 2017 lub nowszego lub można go pobrać ze [strony wydań vswhere](https://github.com/Microsoft/vswhere/releases). Użyj, `vswhere -?` Aby uzyskać informacje pomocy dotyczące narzędzia. Na przykład to polecenie przedstawia wszystkie wersje programu Visual Studio, w tym wcześniejsze wersje produktu i wersji wstępnej, i wyświetla wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Korzystanie z Instrumentacja zarządzania Windows (WMI)

Jeśli na komputerze zainstalowano narzędzie do wykrywania klienta programu Visual Studio, można wysłać zapytanie o informacje o wystąpieniu programu Visual Studio za pomocą usługi WMI. Narzędzie wykrywania klienta programu Visual Studio jest domyślnie instalowane z każdą aktualizacją programu Visual Studio 2017 i Visual Studio 2019 wydaną w dniu 12 maja 2020. Jest ona również dostępna w [katalogu Microsoft Update](https://catalog.update.microsoft.com/) , jeśli chcesz zainstalować go niezależnie.  Aby zapoznać się z przykładem użycia narzędzia do zwracania informacji o wystąpieniu programu Visual Studio, Otwórz program PowerShell jako administrator na komputerze klienckim i wpisz następujące polecenie:

```cmd
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Używanie Configuration Manager Endpoint firmy Microsoft 

Funkcje [spisu oprogramowania w programie Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) mogą służyć do wykonywania zapytań i zbierania informacji o wystąpieniach programu Visual Studio na urządzeniach klienckich. Na przykład następujące zapytanie zwróci nazwę wyświetlaną, wersję i nazwę urządzenia, na którym zainstalowano program Visual Studio dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 i 2019: 

```WQL 
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
``` 

::: moniker range="vs-2017"

> [!TIP]
> Aby uzyskać więcej informacji na temat instalacji programu Visual Studio 2017, zobacz [archiwa Instalatora programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edytowanie rejestru dla wystąpienia programu Visual Studio

W programie Visual Studio ustawienia rejestru są przechowywane w lokalizacji prywatnej, co umożliwia używanie wielu wystąpień równoległych tej samej wersji programu Visual Studio na tym samym komputerze.

Ponieważ te wpisy nie są przechowywane w rejestrze globalnym, istnieją specjalne instrukcje dotyczące używania Edytora rejestru do wprowadzania zmian w ustawieniach rejestru:

1. Jeśli masz otwarte wystąpienie programu Visual Studio, zamknij je.

1. Rozpocznij `regedit.exe` .

1. Wybierz `HKEY_LOCAL_MACHINE` węzeł.

1. Z menu głównego programu regedit wybierz pozycję **plik**  >  **Załaduj gałąź...** , a następnie wybierz plik rejestru prywatnego, który jest przechowywany w folderze **AppData\Local** . Na przykład:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpowiada wystąpieniu programu Visual Studio, które chcesz przeglądać.

Zostanie wyświetlony monit o podanie nazwy Hive, która jest nazwą oddzielonej gałęzi. Po wykonaniu tej czynności powinno być możliwe przeglądanie rejestru w ramach utworzonej gałęzi izolowanej.

> [!IMPORTANT]
> Przed ponownym uruchomieniem programu Visual Studio należy zwolnić utworzoną gałąź izolowaną. W tym celu wybierz pozycję **plik**  >  **Zwolnij gałąź** z głównego menu programu regedit. (Jeśli tego nie zrobisz, plik pozostaje zablokowany i nie będzie można uruchomić programu Visual Studio).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
