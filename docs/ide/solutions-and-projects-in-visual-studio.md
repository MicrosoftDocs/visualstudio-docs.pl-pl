---
title: Rozwiązania i projekty
description: Dowiedz się więcej o projektach i rozwiązaniach programu Visual Studio, sposobach tworzenia nowych projektów na podstawie szablonu oraz sposobie wyświetlania & zarządzania projektami w programie Eksplorator rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 12/15/2020
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
ms.openlocfilehash: ebe6e5c7479ce4e3cda435c51a883c4d5db8cc45
ms.sourcegitcommit: 6f37100d4b8c15a21d3858335ded3c26ab275b93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/16/2020
ms.locfileid: "97599502"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio

Ta strona zawiera opis koncepcji *projektu* i *rozwiązania* w programie Visual Studio. Zawarto również krótko omówiono okno narzędzia Eksplorator rozwiązań i sposób tworzenia nowego projektu.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [projekty i rozwiązania w Visual Studio dla komputerów Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Podczas tworzenia aplikacji lub witryny sieci Web w programie Visual Studio rozpoczyna się od *projektu*. W sensie logicznym projekt zawiera wszystkie pliki, które są kompilowane do pliku wykonywalnego, biblioteki lub witryny sieci Web. Pliki te mogą obejmować kod źródłowy, ikony, obrazy, pliki danych itd. Projekt zawiera również ustawienia kompilatora i inne pliki konfiguracji, które mogą być konieczne przez różne usługi lub składniki, z którymi program komunikuje się.

### <a name="project-file"></a>Plik projektu

Program Visual Studio używa programu [MSBuild](../msbuild/msbuild.md) do kompilowania każdego projektu w rozwiązaniu, a każdy projekt zawiera plik projektu MSBuild. Rozszerzenie pliku odzwierciedla typ projektu, na przykład projekt C# (. csproj), projekt Visual Basic (. vbproj) lub projekt bazy danych (. DBPROJ). Plik projektu to dokument XML, który zawiera wszystkie informacje i instrukcje wymagane przez MSBuild w celu skompilowania projektu, w tym zawartość, wymagania dotyczące platformy, informacje o wersji, ustawienia serwera sieci Web lub serwera bazy danych oraz zadania do wykonania.

Pliki projektu są oparte na [schemacie XML programu MSBuild](../msbuild/msbuild-project-file-schema-reference.md). Aby sprawdzić zawartość nowszych [plików projektu w stylu zestawu SDK](../msbuild/how-to-use-project-sdk.md) w programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Edytuj \<projectname\>**. Aby przyjrzeć się zawartości .NET Framework i innych projektów tego stylu, najpierw Zwolnij projekt (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Zwolnij projekt**). Następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Edytuj \<projectname\>**.

> [!NOTE]
> Nie musisz używać rozwiązań ani projektów w programie Visual Studio do edytowania, kompilowania i debugowania kodu. Możesz po prostu otworzyć folder zawierający pliki źródłowe w programie Visual Studio i rozpocząć edycję. Aby uzyskać więcej informacji, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Rozwiązania

Projekt jest zawarty w *rozwiązaniu*. Pomimo nazwy, rozwiązanie nie jest "odpowiedzią". Jest to po prostu kontener dla co najmniej jednego powiązanego projektu, a także informacje o kompilacji, ustawienia okna programu Visual Studio oraz inne pliki, które nie są skojarzone z określonym projektem. Rozwiązanie jest opisane przez plik tekstowy (rozszerzenie *. sln*) z własnym unikatowym formatem; nie jest przeznaczona do edycji.

### <a name="solution-file"></a>Plik rozwiązania

Program Visual Studio używa dwóch typów plików (*. sln* i *. suo*) do przechowywania ustawień rozwiązań:

|Wewnętrzny|Nazwa|Opis|
|---------------|----------|-----------------|
|. sln|Rozwiązanie programu Visual Studio|Organizuje projekty, elementy projektu i elementy rozwiązania w rozwiązaniu.|
|. suo|Opcje użytkownika rozwiązania|Przechowuje ustawienia i dostosowania na poziomie użytkownika, takie jak punkty przerwania.|

### <a name="solution-folder"></a>Folder rozwiązania

"Folder rozwiązania" to folder wirtualny, który jest tylko w **Eksplorator rozwiązań**, w którym można go użyć do grupowania projektów w rozwiązaniu. Jeśli chcesz zlokalizować plik rozwiązania na komputerze, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  >  . Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje: projekty i rozwiązania > lokalizacje](./reference/projects-solutions-locations-options.md).

## <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem tworzenia nowego projektu jest rozpoczęcie od szablonu projektu dla określonego typu aplikacji lub witryny sieci Web. Szablon projektu składa się z podstawowego zestawu wstępnie wygenerowanych plików kodu, plików konfiguracji, zasobów i ustawień. Te szablony są dostępne w oknie dialogowym, w którym tworzysz nowy projekt (**plik**  >  **Nowy**  >  **projekt**). Aby uzyskać więcej informacji, zobacz [Tworzenie nowego projektu](create-new-project.md) i [opracowywanie rozwiązań i projektów](../ide/creating-solutions-and-projects.md).

Jeśli często dostosowujesz projekty w określony sposób, możesz utworzyć niestandardowy szablon projektu, za pomocą którego można tworzyć nowe projekty z programu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

Podczas tworzenia nowego projektu jest on domyślnie zapisywany w *%USERPROFILE%\source\repos*. Tę lokalizację można zmienić w ustawieniu **Lokalizacja projektów** w obszarze **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  >  . Aby uzyskać więcej informacji na temat tego i innych ustawień projektów i rozwiązań, zobacz [Strona projekty i rozwiązania, opcje okna dialogowego](./reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Eksplorator rozwiązań

Po utworzeniu nowego projektu można użyć **Eksplorator rozwiązań** , aby wyświetlić projekt i rozwiązanie oraz ich skojarzone elementy i zarządzać nimi. Na poniższej ilustracji przedstawiono **Eksplorator rozwiązań** z rozwiązaniem w języku C# zawierającym dwa projekty:

![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png)

Wiele poleceń menu jest dostępnych w menu po kliknięciu prawym przyciskiem myszy na różnych elementach w **Eksplorator rozwiązań**. Te polecenia obejmują Kompilowanie projektu, zarządzanie pakietami NuGet, Dodawanie odwołania, zmiana nazwy pliku i uruchamianie testów, po prostu do nazwy a. Pasek narzędzi w górnej części **Eksplorator rozwiązań** zawiera przyciski do przełączenia z widoku rozwiązania do widoku folderu, wyświetlania ukrytych plików, zwijania wszystkich węzłów i innych.

> [!TIP]
> Jeśli zamknięto Eksplorator rozwiązań i chcesz go otworzyć ponownie, wybierz pozycję **okno**  >  **Ustawienia układ okna** z paska menu.

W przypadku projektów ASP.NET Core można dostosować sposób zagnieżdżania plików w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zagnieżdżania plików w Eksplorator rozwiązań](file-nesting-solution-explorer.md).

Aby wyświetlić listę niektórych ikon, które pojawiają się w Eksplorator rozwiązań, zobacz [ikony widok klasy i Przeglądarka obiektów](class-view-and-object-browser-icons.md).

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/projects-and-solutions)
- [Dodawanie i usuwanie elementów projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/add-and-remove-project-items)
