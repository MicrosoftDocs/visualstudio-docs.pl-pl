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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 006a3fa3d41799a87449b8f9e111ca341a698bf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935415"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania instalacji programu Visual Studio na komputerach klienckich oraz do zarządzania instalacji, za.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejącego wystąpienia programu Visual Studio

Wprowadziliśmy kilka narzędzi, które pomogą Ci wykrywania wystąpień i zarządzanie nimi zainstalowanego programu Visual Studio na maszynach klienckich:

* [vswhere](https://github.com/microsoft/vswhere): plik wykonywalny, wbudowanego w program Visual Studio lub będą dostępne dla oddzielnych dystrybucji, która pomoże Ci znaleźć lokalizacji wszystkich wystąpień programu Visual Studio na danym komputerze.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): Skrypty programu PowerShell, które identyfikują zainstalowanych wystąpień programu Visual Studio za pomocą interfejsu API konfiguracji instalacji.
* [VS-Instalator Samples](https://github.com/microsoft/vs-setup-samples): C#i przykłady w języku C++, które pokazują, jak zapytania istniejącą instalację za pomocą interfejsu API konfiguracji instalacji.

Ponadto [interfejs API konfiguracji instalacji](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć swoje własne narzędzia do przeszukiwania wystąpieniami programu Visual Studio.

## <a name="using-vswhereexe"></a>Za pomocą vswhere.exe

`vswhere.exe` jest automatycznie uwzględnione w programie Visual Studio (począwszy od programu Visual Studio 2017 wersja 15.2 i nowsze wersje), lub możesz ją pobrać z [strony z wersjami vswhere](https://github.com/Microsoft/vswhere/releases). Użyj `vswhere -?` Aby uzyskać informacje o tym narzędziu. Na przykład to polecenie przedstawia wszystkie wersje programu Visual Studio, w tym wcześniejsze wersje produktu i wersje i zapisuje wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Aby uzyskać więcej informacji na temat instalacji programu Visual Studio 2017 zobacz [Visual Studio Instalator archiwa](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edytowanie rejestru dla wystąpienia programu Visual Studio

W programie Visual Studio ustawienia rejestru są przechowywane w lokalizacji prywatnej, co umożliwia wielu wystąpień side-by-side tę samą wersję programu Visual Studio na tym samym komputerze.

Ponieważ te wpisy nie są przechowywane w rejestrze globalnego, istnieją specjalne instrukcje dotyczące używania Edytora rejestru, aby wprowadzić zmiany do ustawień rejestru:

1. Jeśli masz otwarte wystąpienia programu Visual Studio, należy go zamknąć.

1. Rozpocznij `regedit.exe`.

1. Wybierz `HKEY_LOCAL_MACHINE` węzła.

1. Wybierz z menu głównego Regedit **pliku** > **Załaduj gałąź rejestru...**  a następnie wybierz plik rejestru prywatnego, który jest przechowywany w **AppData\Local** folderu. Na przykład:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odnosi się do wystąpienia programu Visual Studio, które chcesz przeglądać.

Zostanie wyświetlony monit podaj nazwę gałęzi, która stanie się nazwą swojej gałęzi izolowanym. Po wykonaniu tej czynności powinno być możliwe do przeglądania w rejestrze w izolowanej hive, który został utworzony.

> [!IMPORTANT]
> Przed ponownym uruchomieniu programu Visual Studio musi zwolnić izolowane hive, który został utworzony. Aby to zrobić, wybierz **pliku** > **Zwolnij gałąź rejestru** z menu głównego Regedit. (Jeśli jest to, następnie plik jest zablokowany i Visual Studio nie będzie możliwe jej uruchomienie.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Przewodnik dla administratorów programu Visual Studio](visual-studio-administrator-guide.md)
