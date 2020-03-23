---
title: Rozwiązania i projekty
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffa561667ea31f215306c7cac4b9820d7b386b5c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303072"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio

Na tej stronie opisano koncepcję *projektu* i *rozwiązania* w programie Visual Studio. Obejmuje również pokrótce okno narzędzia Eksploratora rozwiązań i jak utworzyć nowy projekt.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Projekty i rozwiązania w programie Visual Studio dla komputerów Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Podczas tworzenia aplikacji lub witryny sieci Web w programie Visual Studio należy rozpocząć od *projektu*. W sensie logicznym projekt zawiera wszystkie pliki, które są kompilowane do pliku wykonywalnego, biblioteki lub witryny sieci Web. Pliki te mogą zawierać kod źródłowy, ikony, obrazy, pliki danych i tak dalej. Projekt zawiera również ustawienia kompilatora i inne pliki konfiguracyjne, które mogą być potrzebne przez różne usługi lub składniki, z którymi program się komunikuje.

### <a name="project-file"></a>Plik projektu

Visual Studio używa [MSBuild](../msbuild/msbuild.md) do tworzenia każdego projektu w rozwiązaniu, a każdy projekt zawiera plik projektu MSBuild. Rozszerzenie pliku odzwierciedla typ projektu, na przykład projekt C# (csproj), projekt języka Visual Basic (.vbproj) lub projekt bazy danych (.dbproj). Plik projektu jest dokumentem XML, który zawiera wszystkie informacje i instrukcje potrzebne msBuild do zbudowania projektu, w tym zawartość, wymagania platformy, informacje o wersji, ustawienia serwera www lub serwera bazy danych oraz zadania Wykonać.

Pliki projektu są oparte na [schemacie MSBuild XML](../msbuild/msbuild-project-file-schema-reference.md). Aby przyjrzeć się zawartości nowszych [plików projektu w stylu SDK](../msbuild/how-to-use-project-sdk.md) w programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz pozycję ** \<Edytuj nazwę\>projektu**. Aby przyjrzeć się zawartości programu .NET Framework i innych projektów tego stylu, najpierw zwolnij projekt (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz pozycję **Zwolnij projekt).** Następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Edytuj \<nazwę\>projektu**.

> [!NOTE]
> Nie trzeba używać rozwiązań lub projektów w programie Visual Studio do edycji, kompilacji i debugowania kodu. Po prostu można otworzyć folder zawierający pliki źródłowe w programie Visual Studio i rozpocząć edycję. Aby uzyskać więcej informacji, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions"></a>Rozwiązania

Projekt jest zawarty w *rozwiązaniu*. Pomimo swojej nazwy, rozwiązanie nie jest "odpowiedzią". Jest to po prostu kontener dla jednego lub więcej powiązanych projektów, wraz z informacjami o kompilacji, ustawieniami okna programu Visual Studio i wszelkimi różnymi plikami, które nie są skojarzone z określonym projektem. Rozwiązanie jest opisane przez plik tekstowy (rozszerzenie *.sln)* z własnym unikalnym formatem; nie jest przeznaczony do edycji ręcznie.

Visual Studio używa dwóch typów plików (*.sln* i *.suo*) do przechowywania ustawień rozwiązań:

|Wewnętrzny|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Rozwiązanie programu Visual Studio|Organizuje projekty, elementy projektu i elementy rozwiązania w rozwiązaniu.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje ustawienia na poziomie użytkownika i dostosowania, takie jak punkty przerwania.|

## <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem utworzenia nowego projektu jest rozpoczęcie od szablonu projektu dla określonego typu aplikacji lub witryny sieci Web. Szablon projektu składa się z podstawowego zestawu wstępnie wygenerowanych plików kodu, plików konfiguracyjnych, zasobów i ustawień. Szablony te są dostępne w oknie dialogowym, w którym utworzysz nowy projekt (**Plik** > **nowego** > **projektu**). Aby uzyskać więcej informacji, zobacz [Tworzenie nowego projektu w programie Visual Studio](create-new-project.md) i Tworzenie [rozwiązań i projektów.](../ide/creating-solutions-and-projects.md)

Jeśli często dostosowujesz projekty w określony sposób, można utworzyć niestandardowy szablon projektu, który można następnie użyć do tworzenia nowych projektów. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

Podczas tworzenia nowego projektu jest on domyślnie zapisywany w *%USERPROFILE%\source\repos*. Lokalizację tę można zmienić w ustawieniu **Lokalizacja Projekty** w obszarze**Opcje** >  **narzędzi** > Projekty i**Lokalizacje****rozwiązań** > . Aby uzyskać więcej informacji, zobacz [stronę Projekty i rozwiązania, Okno dialogowe Opcje](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Eksplorator rozwiązań

Po utworzeniu nowego projektu można użyć **Eksploratora rozwiązań** do wyświetlania projektu i rozwiązania oraz zarządzania nimi oraz skojarzonymi z nimi elementami. Na poniższej ilustracji przedstawiono **Eksploratora rozwiązań** z rozwiązaniem języka C#, który zawiera dwa projekty:

![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png)

Wiele poleceń menu jest dostępnych w menu prawym przyciskiem myszy dla różnych elementów w **Eksploratorze rozwiązań**. Polecenia te obejmują tworzenie projektu, zarządzanie pakietami NuGet, dodawanie odwołania, zmiana nazwy pliku i uruchamianie testów, aby wymienić tylko kilka. Pasek narzędzi w górnej części **Eksploratora rozwiązań** ma przyciski, aby przełączyć się z widoku rozwiązania do widoku folderu, wyświetlić ukryte pliki, zwinąć wszystkie węzły i inne.

W przypadku projektów ASP.NET Core można dostosować sposób zagnieżdżania plików w **Eksploratorze rozwiązań**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zagnieżdżania plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Zobacz też

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/projects-and-solutions)
- [Dodawanie i usuwanie elementów projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/add-and-remove-project-items)
