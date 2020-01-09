---
title: Instalowanie obok siebie różnych wersji programu Visual Studio
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62acf1c5e8cab960d4b670f7a05481644e9ffc1e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594087"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio

Program Visual Studio można zainstalować na komputerze, na którym jest już zainstalowana wcześniejsza lub nowsza wersja programu Visual Studio.

::: moniker range="vs-2017"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2017 do otwierania rozwiązania utworzonego w programie Visual Studio 2015, możesz później otworzyć i zmodyfikować rozwiązanie ponownie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2017.

* Jeśli spróbujesz użyć programu Visual Studio 2017 do otwarcia rozwiązania, które zostało utworzone w programie Visual Studio 2015 lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2017. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) .

::: moniker-end

::: moniker range=">= vs-2019"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2019 do otwierania rozwiązania utworzonego w programie Visual Studio 2017, możesz później otworzyć i zmodyfikować rozwiązanie ponownie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2019.

* Jeśli spróbujesz użyć programu Visual Studio 2019 do otwarcia rozwiązania, które zostało utworzone w programie Visual Studio 2017 lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2019. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md) .

::: moniker-end

* W przypadku odinstalowania wersji programu Visual Studio na komputerze, na którym jest zainstalowana więcej niż jedna wersja, skojarzenia plików dla programu Visual Studio zostaną usunięte dla wszystkich wersji.

* Program Visual Studio nie aktualizuje automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub od wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje .NET Framework i instalacje równoczesne

Projekty Visual Basic, C#wizualizacji i F# wizualizacji używają opcji **platformy docelowej** w **projektancie projektu** , aby określić, która wersja .NET Framework jest używana przez projekt. Dla projektu w języku C++ można ręcznie zmienić platformę docelową, modyfikując plik vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji na stronie .NET Framework](/dotnet/framework/migration-guide/version-compatibility) .

Podczas tworzenia projektu można określić, która wersja programu .NET Framework jest przeznaczony projekt **.NET Framework** listy w **nowy projekt** okno dialogowe.

Aby uzyskać informacje specyficzne dla języka zobacz odpowiedni temat w poniższej tabeli.

::: moniker range="vs-2017"

| Język | Temat |
|--------------|-----------|
| Język Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Programowanie za pomocą F# wizualizacji w Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md?view=vs-2017)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Kompilowanie aplikacjiC++ C/izolowanych i zestawów równoległych](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Język | Temat |
|--------------|-----------|
| Język Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Programowanie za pomocą F# wizualizacji w Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Kompilowanie aplikacjiC++ C/izolowanych i zestawów równoległych](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
