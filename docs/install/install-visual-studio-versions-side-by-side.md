---
title: Instalowanie obok siebie różnych wersji programu Visual Studio
description: Dowiedz się, jak zainstalować program Visual Studio na komputerze, na którym jest już zainstalowana wcześniejsza lub nowsza wersja programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.openlocfilehash: f17759d186805dc72623f27c9f254c7a6c0d36e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941531"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio

Program Visual Studio można zainstalować na komputerze, na którym jest już zainstalowana wcześniejsza lub nowsza wersja programu Visual Studio.

::: moniker range="vs-2017"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2017 do otwierania rozwiązania utworzonego w programie Visual Studio 2015, możesz później otworzyć i zmodyfikować rozwiązanie ponownie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2017.

* Jeśli spróbujesz użyć programu Visual Studio 2017 do otwarcia rozwiązania, które zostało utworzone w programie Visual Studio 2015 lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2017. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true) .

::: moniker-end

::: moniker range=">= vs-2019"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2019 do otwierania rozwiązania utworzonego w programie Visual Studio 2017, możesz później otworzyć i zmodyfikować rozwiązanie ponownie w starszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2019.

* Jeśli spróbujesz użyć programu Visual Studio 2019 do otwarcia rozwiązania, które zostało utworzone w programie Visual Studio 2017 lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików, aby były zgodne z programem Visual Studio 2019. Aby uzyskać więcej informacji, zobacz stronę [port, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md) .

::: moniker-end

* W przypadku odinstalowania wersji programu Visual Studio na komputerze, na którym jest zainstalowana więcej niż jedna wersja, skojarzenia plików dla programu Visual Studio zostaną usunięte dla wszystkich wersji.

* Program Visual Studio nie uaktualnia automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub wydawcy oprogramowania.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Zainstaluj drobne wersje programu Visual Studio obok siebie

W przypadku uaktualniania z jednej pomocniczej wersji programu Visual Studio do następnej Instalator programu Visual Studio zaktualizuje bieżącą instalację do następnej wersji w tym kanale domyślnie. Na przykład podczas instalowania wersji zapoznawczej usługi 16.6.4 Instalator spróbuje zastąpić bieżącą instalację wersji zapoznawczej programu 16.6.3, ponieważ obie wersje znajdują się w kanale w wersji zapoznawczej 16,6. Pozwala to zagwarantować, że starsze wersje programu Visual Studio nie zajmują miejsca na maszynie. W niektórych określonych przypadkach może być przydatne zainstalowanie mniejszych wersji obok siebie. W naszym przykładzie będzie to oznaczało, że zarówno 16.6.3, jak i 16.6.4 na tym samym komputerze.

1. Pobierz [plik inicjujący programu Visual Studio](/visualstudio/releases/2019/history#installing-an-earlier-release) dla wersji pomocniczej, który chcesz zainstalować obok istniejących wersji programu Visual Studio.
2. Otwórz wiersz polecenia w trybie administratora. W tym celu otwórz menu Start systemu Windows, wpisz "cmd", kliknij prawym przyciskiem myszy wyniki wyszukiwania w wierszu polecenia, a następnie wybierz polecenie **Uruchom jako administrator**. W wierszu polecenia Zmień katalog na folder, w którym znajduje się plik programu inicjującego programu Visual Studio.
3. Uruchom następujące polecenie, określając nową ścieżkę folderu dla lokalizacji instalacji i zastępując nazwę pliku exe odpowiednią nazwą programu inicjującego dla instalowanej wersji programu Visual Studio. Nazwa pliku. exe powinna być taka sama lub podobna do jednego z następujących plików:
   * vs_community.exe dla programu Visual Studio Community
   * vs_professional.exe Visual Studio Professional
   * vs_enterprise.exe Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Postępuj zgodnie z okna dialogowe Instalatora, aby wybrać składniki potrzebne do instalacji. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>Wersje .NET Framework i instalacje równoczesne

Visual Basic, Visual C# i projekty Visual F# używają opcji **platformy docelowej** w **projektancie projektu** , aby określić, która wersja .NET Framework jest używana przez projekt. W przypadku projektu języka C++ można ręcznie zmienić platformę docelową, modyfikując plik. vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji na stronie .NET Framework](/dotnet/framework/migration-guide/version-compatibility) .

Podczas tworzenia projektu można określić, która wersja .NET Framework obiektów docelowych projektu na liście **.NET Framework** w oknie dialogowym **Nowy projekt** .

Aby uzyskać informacje dotyczące języka, zobacz odpowiedni temat w poniższej tabeli.

::: moniker range="vs-2017"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true) |
| Visual F# | [Programowanie przy użyciu Visual F# w programie Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true) |
|C++ | [Instrukcje: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Kompilowanie aplikacji izolowanych C/C++ oraz zestawów wykonywanych równocześnie](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Język | Temat |
|--------------|-----------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Programowanie przy użyciu Visual F# w programie Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Instrukcje: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Kompilowanie aplikacji izolowanych C/C++ oraz zestawów wykonywanych równocześnie](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
