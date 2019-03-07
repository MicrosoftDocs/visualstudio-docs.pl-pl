---
title: Instalowanie obok siebie różnych wersji programu Visual Studio
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-isntallation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 22c4f24c8e97d98bb0bbe88fb998deb5929c6b7b
ms.sourcegitcommit: b7f25ae08e45fcaa84a84276b588cf6799cc7620
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57567128"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio

Visual Studio można zainstalować na komputerze, który ma już zainstalowanego programu Visual Studio w wersji starszej lub nowszej.

::: moniker range="vs-2017"

Przed zainstalowaniem wersji obok siebie, przejrzyj następujące warunki:

* Jeśli używasz programu Visual Studio 2017 do otwarcia rozwiązania, który został utworzony w programie Visual Studio 2015 możesz później otwierać i modyfikować rozwiązanie ponownie w starszej wersji, tak długo, jak jeszcze nie zaimplementowano żadnych funkcji, które są specyficzne dla programu Visual Studio 2017.

* Jeśli spróbujesz otworzyć rozwiązanie utworzone w programie Visual Studio 2015 lub starsza wersja za pomocą programu Visual Studio 2017, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2017. Aby uzyskać więcej informacji, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) strony.

::: moniker-end

::: moniker range=">= vs-2019"

Przed zainstalowaniem wersji obok siebie, przejrzyj następujące warunki:

* Jeśli używasz programu Visual Studio 2019 r. Aby otworzyć rozwiązanie utworzone w programie Visual Studio 2017, możesz później otworzyć i modyfikować rozwiązanie ponownie w starszej wersji, tak długo, jak nie zaimplementowano żadnych funkcji, które są specyficzne dla programu Visual Studio 2019 r.

* Jeśli spróbujesz otworzyć rozwiązanie utworzone w programie Visual Studio 2017 lub starszej wersji za pomocą programu Visual Studio 2019 r, może być konieczne zmodyfikowanie projektów i plików, aby był zgodny z programu Visual Studio 2019 r. Aby uzyskać więcej informacji, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md) strony.

::: moniker-end

* Jeśli odinstalujesz daną wersję programu Visual Studio na komputerze, na którym została zainstalowana więcej niż jedna wersja, skojarzenia plików dla programu Visual Studio są usuwane dla wszystkich wersji.

* Program Visual Studio nie aktualizuje automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) lub od wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje programu .NET framework i instalacje side-by-side

Visual Basic, Visual C#i Visual F# projektów użyj **platformę docelową** opcji **projektanta projektu** do określenia którą wersję programu .NET Framework, która używa projektu. Dla projektu w języku C++ można ręcznie zmienić platformę docelową, modyfikując plik vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji w programie .NET Framework](/dotnet/framework/migration-guide/version-compatibility) strony.

Podczas tworzenia projektu można określić, która wersja programu .NET Framework jest przeznaczony projekt **.NET Framework** listy w **nowy projekt** okno dialogowe.

Aby uzyskać informacje specyficzne dla języka zobacz odpowiedni temat w poniższej tabeli.

::: moniker range="vs-2017"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Programowanie za pomocą wizualizacji F# w programie Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Instrukcje: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md?view=vs-2017)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Tworzenie języka C/C++ izolowanymi oraz aplikacjami wykonywanymi side-by-side](/cpp/build/building-c-cpp-isolated-applications-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2019) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2019) |
| Visual F# | [Programowanie za pomocą wizualizacji F# w programie Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2019) |
| C++ | [Instrukcje: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md?view=vs-2019)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md)
* [Tworzenie języka C/C++ izolowanymi oraz aplikacjami wykonywanymi side-by-side](/cpp/build/building-c-cpp-isolated-applications-side-by-side-assemblies/)

::: moniker-end