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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114647"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio

Program Visual Studio można zainstalować na komputerze, na który jest już zainstalowana wcześniejsza lub nowsza wersja programu Visual Studio.

::: moniker range="vs-2017"

Przed zainstalowaniem wersji obok siebie należy zapoznać się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2017, aby otworzyć rozwiązanie, które zostało utworzone w programie Visual Studio 2015, można później otworzyć i zmodyfikować rozwiązanie ponownie we wcześniejszej wersji, o ile nie zaimplementowano żadnych funkcji, które są specyficzne dla programu Visual Studio 2017.

* Jeśli spróbujesz użyć programu Visual Studio 2017, aby otworzyć rozwiązanie, które zostało utworzone w programie Visual Studio 2015 lub wcześniejszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2017. Aby uzyskać więcej informacji, zobacz [port, migracji i uaktualnienia projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) strony.

::: moniker-end

::: moniker range=">= vs-2019"

Przed zainstalowaniem wersji obok siebie należy zapoznać się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2019, aby otworzyć rozwiązanie, które zostało utworzone w programie Visual Studio 2017, można później otworzyć i zmodyfikować rozwiązanie ponownie we wcześniejszej wersji, o ile nie zaimplementowano żadnych funkcji, które są specyficzne dla programu Visual Studio 2019.

* Jeśli spróbujesz użyć programu Visual Studio 2019, aby otworzyć rozwiązanie, które zostało utworzone w programie Visual Studio 2017 lub wcześniejszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2019. Aby uzyskać więcej informacji, zobacz [port, migracji i uaktualnienia projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md) strony.

::: moniker-end

* Jeśli odinstalujesz wersję programu Visual Studio na komputerze, na który jest zainstalowana więcej niż jedna wersja, skojarzenia plików dla programu Visual Studio zostaną usunięte dla wszystkich wersji.

* Visual Studio nie uaktualnia automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub wydawcy oprogramowania.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje programu .NET Framework i instalacje obok siebie

Visual Basic, Visual C# i Visual F# projekty używają docelowej **ramki** opcji w **Projektancie projektu,** aby określić, która wersja programu .NET Framework, który używa projektu. W przypadku projektu języka C++ można ręcznie zmienić platformę docelową, modyfikując plik .vcxproj. Aby uzyskać więcej informacji, zobacz zgodność wersji na stronie [.NET Framework.](/dotnet/framework/migration-guide/version-compatibility)

Podczas tworzenia projektu można określić, która wersja programu .NET Framework jest przeznaczona dla projektu na liście **.NET Framework** w oknie dialogowym **Nowy projekt.**

Aby uzyskać informacje dotyczące języka, zobacz odpowiedni temat w poniższej tabeli.

::: moniker range="vs-2017"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Tworzenie za pomocą języka Visual F# w programie Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Jak: Modyfikowanie zestawu narzędzi struktury docelowej i platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md?view=vs-2017)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Tworzenie izolowanych aplikacji C/C++ i zespołów side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Tworzenie za pomocą języka Visual F# w programie Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Jak: Modyfikowanie zestawu narzędzi struktury docelowej i platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Tworzenie izolowanych aplikacji C/C++ i zespołów side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
