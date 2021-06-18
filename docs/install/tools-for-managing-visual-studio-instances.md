---
title: Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi
titleSuffix: ''
description: Dowiedz się więcej o narzędziach, których można używać do wykrywania instalacji Visual Studio na maszynach klienckich i zarządzania nimi.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306894"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania Visual Studio instalacji na komputerach klienckich i zarządzania instalacjami.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejących Visual Studio wystąpień

Następujące narzędzia i narzędzia ułatwiają wykrywanie zainstalowanych wystąpień Visual Studio na maszynach klienckich i zarządzanie nimi:

* [**vswhere:**](https://github.com/microsoft/vswhere)plik wykonywalny wbudowany w Visual Studio dostępny dla oddzielnej dystrybucji, który pomaga znaleźć lokalizację wszystkich wystąpień Visual Studio na określonej maszynie.
* [**VSSetup.PowerShell:**](https://github.com/microsoft/vssetup.powershell)skrypty programu PowerShell, które używają interfejsu API konfiguracji instalatora do identyfikowania zainstalowanych wystąpień Visual Studio.
* [**VS-Setup-Samples:**](https://github.com/microsoft/vs-setup-samples)przykłady w językach C# i C++, które pokazują, jak używać interfejsu API konfiguracji instalatora do wykonywania zapytań dotyczących istniejącej instalacji.
* [**Instrumentacja zarządzania Windows (WMI):**](/windows/win32/wmisdk/wmi-start-page)Visual Studio informacji o wystąpieniu można wyszukiwać za pośrednictwem Visual Studio klasy MSFT_VSInstance.
* Interfejs [**API konfiguracji instalacji**](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć własne narzędzia do Visual Studio wystąpień.
* [**Microsoft Endpoint Configuration Manager spisu oprogramowania:**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory)może służyć do zbierania informacji o Visual Studio wystąpieniach programu na urządzeniach klienckich.

## <a name="using-vswhereexe"></a>Korzystanie z vswhere.exe

`vswhere.exe`program jest automatycznie uwzględniany Visual Studio 2017 r. i nowszych wersjach lub można pobrać go ze strony wydań programu [vswhere.](https://github.com/Microsoft/vswhere/releases) Użyj `vswhere -?` narzędzia , aby uzyskać informacje o narzędziu. Na przykład to polecenie wyświetla wszystkie wersje Visual Studio, w tym wcześniejsze wersje produktu i wersje wstępne, oraz wyświetla wyniki w formacie JSON:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Korzystanie Instrumentacja zarządzania Windows (WMI)

Jeśli na Visual Studio jest zainstalowane narzędzie do wykrywania klienta, można wysyłać zapytania o informacje Visual Studio wystąpienia przy użyciu usługi WMI. Narzędzie Visual Studio Client Detector jest instalowane domyślnie co Visual Studio 2017, Visual Studio 2019 i aktualizacji do wersji Visual Studio 2022, która została wydana 12 maja 2020 r. lub później. Jest on również dostępny w [katalogu Microsoft Update,](https://catalog.update.microsoft.com/) jeśli chcesz zainstalować go niezależnie.  Aby uzyskać przykład sposobu używania narzędzia do zwracania informacji o wystąpieniu Visual Studio, otwórz program PowerShell jako administrator na komputerze klienckim i wpisz następujące polecenie:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Korzystanie z Microsoft Endpoint Configuration Manager

[Microsoft Endpoint Configuration Manager spisu oprogramowania](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) mogą służyć do wykonywania zapytań i zbierania informacji Visual Studio o wystąpieniach na urządzeniach klienckich. Na przykład następujące zapytanie zwróci nazwę wyświetlaną, wersję i nazwę urządzenia, na Visual Studio jest zainstalowany dla wszystkich zainstalowanych wystąpień programu Visual Studio 2017 i 2019:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
```

::: moniker range="vs-2017"

> [!TIP]
> Aby uzyskać więcej informacji na Visual Studio 2017, zobacz [Visual Studio Archiwa instalatora](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edytowanie rejestru dla Visual Studio rejestru

W Visual Studio ustawienia rejestru są przechowywane w lokalizacji prywatnej, co umożliwia wiele wystąpień równocześnie tej samej wersji usługi Visual Studio na tym samym komputerze.

Ponieważ te wpisy nie są przechowywane w rejestrze globalnym, istnieją specjalne instrukcje dotyczące używania Edytora rejestru w celu zmiany ustawień rejestru:

1. Jeśli masz otwarte wystąpienie klasy Visual Studio, zamknij je.

1. Uruchom `regedit.exe` .

1. Wybierz `HKEY_LOCAL_MACHINE` węzeł.

1. Z menu głównego regedit wybierz pozycję **File** Load Hive... (Załaduj plik Hive...), a następnie wybierz plik rejestru prywatnego, który jest przechowywany w  >   folderze **AppData\Local.** Na przykład:

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpowiada wystąpieniu Visual Studio, które chcesz przeglądać.

Zostanie wyświetlony monit o podanie nazwy gałęzi, która staje się nazwą izolowanej gałęzi. Po tej stronie powinno być możliwe przeglądanie rejestru w ramach utworzonego izolowanego gałęzi.

> [!IMPORTANT]
> Przed rozpoczęciem Visual Studio należy zwolnić utworzony odizolowany gałąź. W tym celu wybierz pozycję **Plik**  >  **Zwolnij gałąź Hive** z menu głównego regedit. (Jeśli tego nie zrobisz, plik pozostanie zablokowany i Visual Studio nie będzie można uruchomić).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
