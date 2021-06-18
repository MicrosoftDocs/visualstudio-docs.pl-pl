---
title: Instalowanie obok siebie różnych wersji programu Visual Studio
description: Dowiedz się, jak Visual Studio na komputerze, który ma już zainstalowaną wcześniejszą lub nowszą Visual Studio programu .
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.openlocfilehash: c8d1da5f8cb5c237fe02a41197825d5086fc6471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307024"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalowanie obok siebie różnych wersji programu Visual Studio

Program można Visual Studio na komputerze z wcześniejszą lub nowszą wersją programu Visual Studio już zainstalowaną.

::: moniker range="vs-2017"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2017 do otwierania rozwiązania utworzonego w programie Visual Studio 2015, możesz później otworzyć i zmodyfikować rozwiązanie ponownie we wcześniejszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2017.

* Jeśli próbujesz użyć programu Visual Studio 2017 do otwarcia rozwiązania utworzonego w programie Visual Studio 2015 lub starszej wersji, może być konieczne zmodyfikowanie projektów i plików tak, aby były zgodne z programem Visual Studio 2017. Aby uzyskać więcej informacji, zobacz [stronę Przenoszenie, migrowanie i uaktualnianie Visual Studio Projektów.](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)

::: moniker-end

::: moniker range="vs-2019"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2019 do otwierania rozwiązania utworzonego w programie Visual Studio 2017, możesz później otworzyć i zmodyfikować rozwiązanie ponownie we wcześniejszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2019.

* Jeśli spróbujesz użyć programu Visual Studio 2019 do otwarcia rozwiązania utworzonego w wersji programu Visual Studio 2017 lub starszej, może być konieczne zmodyfikowanie projektów i plików tak, aby były zgodne z programem Visual Studio 2019. Aby uzyskać więcej informacji, zobacz [stronę Przenoszenie, migrowanie i uaktualnianie Visual Studio Projektów.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

::: moniker range=">=vs-2022"

Przed zainstalowaniem wersji obok siebie zapoznaj się z następującymi warunkami:

* Jeśli używasz programu Visual Studio 2022 do otwierania rozwiązania utworzonego w programie Visual Studio 2017 lub Visual Studio 2019, możesz później otworzyć i zmodyfikować rozwiązanie ponownie we wcześniejszej wersji, o ile nie zaimplementowano żadnych funkcji specyficznych dla programu Visual Studio 2022.

* Jeśli próbujesz użyć programu Visual Studio 2022 do otwarcia rozwiązania utworzonego w wersji programu Visual Studio 2019 lub starszej, może być konieczne zmodyfikowanie projektów i plików tak, aby były zgodne z programem Visual Studio 2022. Aby uzyskać więcej informacji, zobacz [stronę Przenoszenie, migrowanie i uaktualnianie Visual Studio Projektów.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

* Jeśli odinstalujesz wersję programu Visual Studio komputerze z zainstalowaną więcej niż jedną wersją, skojarzenia plików dla Visual Studio zostaną usunięte dla wszystkich wersji.

* Visual Studio nie uaktualnia automatycznie rozszerzeń, ponieważ nie wszystkie rozszerzenia są zgodne. Należy ponownie zainstalować rozszerzenia z Visual Studio Marketplace [lub](https://marketplace.visualstudio.com/) wydawcy oprogramowania.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Instalowanie Visual Studio instalowania obok siebie wersji

Podczas uaktualniania z jednej wersji pomocniczej programu Visual Studio do następnej instalator programu Visual Studio domyślnie zaktualizuje bieżącą instalację do najnowszej wersji w tym kanale. Załóżmy na przykład, że właśnie wydano 16.9.4. Instalator spróbuje zastąpić bieżącą instalację wersji 16.9.3 (lub starszej) 16.9.4, ponieważ obie wersje są częścią kanału wydań programu [Visual Studio 2019.](/visualstudio/productinfo/release-rhythm) Zastąpienie starszej wersji nowszą wydaniem podczas aktualizacji pomaga zapewnić, że starsze wersje Visual Studio nie zajmą miejsca na komputerze. Jednak w niektórych konkretnych przypadkach pomocne może być zainstalowanie obok siebie różnych wersji Visual Studio wersji pomocniczej. Na przykład możesz chcieć mieć zarówno 16.9.3, jak i 16.9.4 na tej samej maszynie.

::: moniker range="vs-2017"

1. Pobierz najnowszy program inicjujący dla programu Visual Studio 2017 w wersji 15.9 ze strony [poprzednich](https://visualstudio.microsoft.com/vs/older-downloads/) wersji programu Visual Studio dla wersji, która ma być instalowana obok istniejącej wersji programu Visual Studio.

1. Otwórz wiersz polecenia w trybie administratora. Aby to zrobić, otwórz okno menu Start Windows, wpisz "cmd", kliknij prawym przyciskiem myszy wynik wyszukiwania wiersza polecenia i wybierz polecenie **Uruchom jako administrator.** W wierszu polecenia zmień katalog na folder, w którym znajduje się Visual Studio inicjujący.

1. Uruchom następujące polecenie, określając nową ścieżkę folderu dla lokalizacji instalacji i zastępując nazwę pliku programu .exe odpowiednią nazwą programu inicjjącego dla Visual Studio instalacji programu . Nazwa .exe powinna być dopasowana lub podobna do jednego z następujących plików:

   * vs_enterprise.exe for Visual Studio Enterprise
   * vs_professional.exe dla Visual Studio Professional

1. Postępuj zgodnie z oknie dialogowym instalatora, aby wybrać składniki potrzebne do instalacji. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range="vs-2019"

1. Pobierz plik programu inicjjącego programu Visual Studio 2019 ze strony pobierania programu [Visual Studio](https://visualstudio.microsoft.com/downloads) lub ze strony wersji programu [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) dla wersji pomocniczej, która ma być instalowana obok istniejącej wersji programu Visual Studio.

1. Otwórz wiersz polecenia w trybie administratora. Aby to zrobić, otwórz okno menu Start Windows, wpisz "cmd", kliknij prawym przyciskiem myszy wynik wyszukiwania wiersza polecenia i wybierz polecenie **Uruchom jako administrator.** W wierszu polecenia zmień katalog na folder, w którym znajduje się Visual Studio inicjujący.

1. Uruchom następujące polecenie, określając nową ścieżkę folderu dla lokalizacji instalacji i zastępując nazwę pliku programu .exe odpowiednią nazwą programu inicjjącego dla Visual Studio instalacji programu . Nazwa .exe powinna być dopasowana lub podobna do jednego z następujących plików:

   * vs_enterprise.exe for Visual Studio Enterprise
   * vs_professional.exe dla Visual Studio Professional
   * vs_community.exe dla Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Postępuj zgodnie z oknie dialogowym instalatora, aby wybrać składniki potrzebne do instalacji. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range=">=vs-2022"

1. Pobierz plik programu inicjujący programu Visual Studio 2022 ze strony pobierania programu [Visual Studio](https://visualstudio.microsoft.com/downloads) lub strony wydań programu [Visual Studio 2022](/visualstudio/releases/2022/history) dla wersji pomocniczej, która ma być instalowana obok istniejącej wersji programu Visual Studio.

1. Otwórz wiersz polecenia w trybie administratora. Aby to zrobić, otwórz okno menu Start Windows, wpisz "cmd", kliknij prawym przyciskiem myszy wynik wyszukiwania wiersza polecenia i wybierz polecenie **Uruchom jako administrator.** W wierszu polecenia zmień katalog na folder, w którym znajduje się Visual Studio inicjujący.

1. Uruchom następujące polecenie, określając nową ścieżkę folderu dla lokalizacji instalacji i zastępując nazwę pliku programu .exe odpowiednią nazwą programu inicjjącego dla Visual Studio instalacji programu . Nazwa .exe powinna być dopasowana lub podobna do jednego z następujących plików:

   * vs_enterprise.exe for Visual Studio Enterprise
   * vs_professional.exe dla Visual Studio Professional
   * vs_community.exe dla Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Postępuj zgodnie z oknie dialogowym instalatora, aby wybrać składniki potrzebne do instalacji. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio](install-visual-studio.md#step-4---choose-workloads).
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework wersje i instalacje side-by-side

Visual Basic, Visual C# i Visual F# używają opcji **Target Framework** w  Projektancie projektu, aby określić, która wersja pakietu .NET Framework używana przez projekt. W przypadku projektu w języku C++ można ręcznie zmienić platformę docelową, modyfikując plik vcxproj. Aby uzyskać więcej informacji, zobacz [zgodność wersji na .NET Framework](/dotnet/framework/migration-guide/version-compatibility) stronie.

Podczas tworzenia projektu można określić, która wersja pliku .NET Framework docelowych  projektu na liście .NET Framework w **oknie dialogowym Nowy** projekt.

Informacje specyficzne dla języka można znaleźć w odpowiednim temacie w poniższej tabeli.

::: moniker range="vs-2017"

| Język     | Temat                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [Opracowywanie za pomocą Visual F# w Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
| C++          | [Instrukcje: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/)                         |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Przenoszenie, migrowanie i uaktualnianie Visual Studio projektów](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Kompilowanie aplikacji izolowanych C/C++ oraz zestawów wykonywanych równocześnie](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Język     | Temat                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [Opracowywanie za pomocą Visual F# w Visual Studio](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [Instrukcje: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Przenoszenie, migrowanie i uaktualnianie Visual Studio projektów](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Kompilowanie aplikacji izolowanych C/C++ oraz zestawów wykonywanych równocześnie](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
