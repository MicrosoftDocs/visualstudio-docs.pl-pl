---
title: Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi
titleSuffix: ''
description: Dowiedz się więcej o narzędziach, których można użyć do wykrywania i zarządzanie instalacjami programu Visual Studio na maszynach klienckich.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d6e46c95584cb3732d6339a02f6098976f2bab85
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115035"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania instalacji programu Visual Studio na komputerach klienckich oraz do zarządzania instalacji, za.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejącego wystąpienia programu Visual Studio

Wprowadziliśmy kilka narzędzi, które pomogą Ci wykrywania wystąpień i zarządzanie nimi zainstalowanego programu Visual Studio na maszynach klienckich:

* [vswhere](https://github.com/microsoft/vswhere): plik wykonywalny wbudowany w program Visual Studio lub dostępny w oddzielnym dystrybucji, który ułatwia znalezienie lokalizacji wszystkich wystąpień programu Visual Studio na konkretnym komputerze.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): skrypty programu PowerShell, które identyfikują zainstalowanych wystąpień programu Visual Studio za pomocą interfejsu API konfiguracji instalacji.
* [VS-Instalator-Samples](https://github.com/microsoft/vs-setup-samples): przykłady C# i C++, które pokazują, jak zapytania istniejącą instalację za pomocą interfejsu API konfiguracji instalacji.

Ponadto [interfejs API konfiguracji instalacji](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć swoje własne narzędzia do przeszukiwania wystąpieniami programu Visual Studio.

## <a name="using-vswhereexe"></a>Za pomocą vswhere.exe

`vswhere.exe` jest automatycznie dołączany do programu Visual Studio (począwszy od programu Visual Studio 2017 w wersji 15,2 lub nowszej) lub można go pobrać ze [strony wersji vswhere](https://github.com/Microsoft/vswhere/releases). Użyj `vswhere -?` Aby uzyskać informacje o tym narzędziu. Na przykład to polecenie wyświetla wszystkie wersje programu Visual Studio, w tym wcześniejsze wersje produktu i wersji wstępnej, i wyświetla wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Aby uzyskać więcej informacji na temat instalacji programu Visual Studio 2017, zobacz [archiwa Instalatora programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edytowanie rejestru dla wystąpienia programu Visual Studio

W programie Visual Studio ustawienia rejestru są przechowywane w lokalizacji prywatnej, co umożliwia używanie wielu wystąpień równoległych tej samej wersji programu Visual Studio na tym samym komputerze.

Ponieważ te wpisy nie są przechowywane w rejestrze globalnego, istnieją specjalne instrukcje dotyczące używania Edytora rejestru, aby wprowadzić zmiany do ustawień rejestru:

1. Jeśli masz otwarte wystąpienie programu Visual Studio, zamknij je.

1. Rozpocznij `regedit.exe`.

1. Wybierz `HKEY_LOCAL_MACHINE` węzła.

1. Z menu głównego programu regedit wybierz kolejno pozycje **plik** > **Załaduj gałąź rejestru...** , a następnie wybierz plik rejestru prywatnego, który jest przechowywany w folderze **AppData\Local** . Na przykład:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odnosi się do wystąpienia programu Visual Studio, które chcesz przeglądać.

Zostanie wyświetlony monit podaj nazwę gałęzi, która stanie się nazwą swojej gałęzi izolowanym. Po wykonaniu tej czynności powinno być możliwe do przeglądania w rejestrze w izolowanej hive, który został utworzony.

> [!IMPORTANT]
> Przed ponownym uruchomieniu programu Visual Studio musi zwolnić izolowane hive, który został utworzony. W tym celu wybierz pozycję **plik** > **Zwolnij gałąź** z menu głównego programu regedit. (Jeśli jest to, następnie plik jest zablokowany i Visual Studio nie będzie możliwe jej uruchomienie.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Przewodnik dla administratorów programu Visual Studio](visual-studio-administrator-guide.md)
