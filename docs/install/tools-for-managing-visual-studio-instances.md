---
title: Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi
titleSuffix: ''
description: Dowiedz się więcej o narzędziach, których można używać do wykrywania instalacji programu Visual Studio i zarządzania nimi na komputerach klienckich.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115035"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania instalacji programu Visual Studio na komputerach klienckich i do zarządzania instalacjami.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejących wystąpień programu Visual Studio

Udostępniliśmy kilka narzędzi, które pomogą Ci wykrywać i zarządzać zainstalowanymi wystąpieniami programu Visual Studio na komputerach klienckich:

* [vswhere](https://github.com/microsoft/vswhere): plik wykonywalny wbudowany w programie Visual Studio lub dostępny dla oddzielnej dystrybucji, która pomaga znaleźć lokalizację wszystkich wystąpień programu Visual Studio na określonym komputerze.
* [VSSetup.PowerShell:](https://github.com/microsoft/vssetup.powershell)Skrypty programu PowerShell, które używają interfejsu API konfiguracji instalacji do identyfikowania zainstalowanych wystąpień programu Visual Studio.
* [Przykłady konfiguracji vs: przykłady](https://github.com/microsoft/vs-setup-samples)języka C# i C++, które pokazują, jak używać interfejsu API konfiguracji instalatora do wykonywania zapytań o istniejącą instalację.

Ponadto interfejs [API konfiguracji instalacji](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć własne narzędzia do przesłuchiwania wystąpień programu Visual Studio.

## <a name="using-vswhereexe"></a>Korzystanie z pliku vswhere.exe

`vswhere.exe`jest automatycznie uwzględniany w programie Visual Studio (począwszy od programu Visual Studio 2017 w wersji 15.2 i nowszych wersjach) lub można go pobrać ze [strony wersji vswhere](https://github.com/Microsoft/vswhere/releases). Służy `vswhere -?` do uzyskania informacji pomocy na temat narzędzia. Na przykład to polecenie pokazuje wszystkie wersje programu Visual Studio, w tym wcześniejsze wersje produktu i prereleases i wyprowadza wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Aby uzyskać więcej informacji na temat instalacji programu Visual Studio 2017, zobacz [Archiwa instalacji programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edytowanie rejestru dla wystąpienia programu Visual Studio

W programie Visual Studio ustawienia rejestru są przechowywane w lokalizacji prywatnej, która umożliwia wiele wystąpień obok siebie tej samej wersji programu Visual Studio na tym samym komputerze.

Ponieważ te wpisy nie są przechowywane w rejestrze globalnym, istnieją specjalne instrukcje dotyczące wprowadzania zmian w ustawieniach rejestru za pomocą Edytora rejestru:

1. Jeśli masz otwarte wystąpienie programu Visual Studio, zamknij je.

1. Start `regedit.exe`.

1. Wybierz `HKEY_LOCAL_MACHINE` węzeł.

1. Z menu głównego Regedit wybierz **pozycję File** > **Load Hive...** a następnie wybierz prywatny plik rejestru, który jest przechowywany w folderze **AppData\Local.** Przykład:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>`odpowiada wystąpieniu programu Visual Studio, które chcesz przeglądać.

Zostanie wyświetlony monit o podanie nazwy gałęzi, która staje się nazwą izolowanego ula. Po zrobienie tego, powinieneś być w stanie przeglądać rejestr w obszarze izolowanej gałęzi, który został utworzony.

> [!IMPORTANT]
> Przed ponownym uruchomieniem programu Visual Studio należy zwolnić utworzony izolowany gałąź. Aby to zrobić, wybierz opcję**Rozładuj** **plik** > hive z menu głównego Regedit. (Jeśli tego nie zrobisz, plik pozostanie zablokowany i program Visual Studio nie będzie mógł się uruchomić).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Przewodnik dla administratorów programu Visual Studio](visual-studio-administrator-guide.md)
