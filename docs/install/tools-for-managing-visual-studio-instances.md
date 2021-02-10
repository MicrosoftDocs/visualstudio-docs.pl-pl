---
title: Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi
titleSuffix: ''
description: Informacje o narzędziach, których można użyć do wykrywania instalacji programu Visual Studio i zarządzania nimi na komputerach klienckich.
ms.date: 08/14/2017
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
ms.openlocfilehash: efd4091407d228a15cc80971d759e5371bddd3ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959262"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania wystąpień programu Visual Studio i zarządzania nimi

Istnieje kilka narzędzi, których można użyć do wykrywania instalacji programu Visual Studio na komputerach klienckich i zarządzania nimi.

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejących wystąpień programu Visual Studio

Wprowadziliśmy kilka dostępnych narzędzi, które pomogą wykryć zainstalowane wystąpienia programu Visual Studio i zarządzać nimi na komputerach klienckich:

* [vswhere](https://github.com/microsoft/vswhere): plik wykonywalny wbudowany w program Visual Studio lub dostępny w oddzielnym dystrybucji, który ułatwia znalezienie lokalizacji wszystkich wystąpień programu Visual Studio na konkretnym komputerze.
* [VSSetup. PowerShell](https://github.com/microsoft/vssetup.powershell): skrypty programu PowerShell, które używają interfejsu API konfiguracji Instalatora do identyfikowania zainstalowanych wystąpień programu Visual Studio.
* [Vs-Setup-Samples](https://github.com/microsoft/vs-setup-samples): przykłady języków C# i C++, które pokazują, jak używać interfejsu API konfiguracji Instalatora do wysyłania zapytań do istniejącej instalacji.

Ponadto [interfejs API konfiguracji instalacji](<xref:Microsoft.VisualStudio.Setup.Configuration>) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć własne narzędzia do Interrogating wystąpień programu Visual Studio.

## <a name="using-vswhereexe"></a>Używanie vswhere.exe

`vswhere.exe` jest automatycznie dołączany do programu Visual Studio (począwszy od programu Visual Studio 2017 w wersji 15,2 lub nowszej) lub można go pobrać ze [strony wersji vswhere](https://github.com/Microsoft/vswhere/releases). Użyj, `vswhere -?` Aby uzyskać informacje pomocy dotyczące narzędzia. Na przykład to polecenie wyświetla wszystkie wersje programu Visual Studio, w tym wcześniejsze wersje produktu i wersji wstępnej, i wyświetla wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
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

* [Przewodnik po administratorach programu Visual Studio](visual-studio-administrator-guide.md)
