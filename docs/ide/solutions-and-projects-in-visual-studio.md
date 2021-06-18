---
title: Co to są Visual Studio &amp; rozwiązań?
description: Dowiedz się Visual Studio projektach i rozwiązaniach, jak tworzyć nowe projekty na podstawie szablonu oraz jak wyświetlać & projektów w Eksplorator rozwiązań.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 12/31/2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f632922078383708319e610d82a4c94a58619424
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306400"
---
# <a name="what-are-solutions-and-projects-in-visual-studio"></a>Co to są rozwiązania i projekty w Visual Studio?

W tym artykule dowiesz się, *co* to jest projekt i *rozwiązanie* w Visual Studio. Ponadto pokrótce opisano Eksplorator rozwiązań narzędzi i sposób tworzenia nowego projektu.

> [!NOTE]
> Ten temat dotyczy Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Projekty i rozwiązania w Visual Studio dla komputerów Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Podczas tworzenia aplikacji lub witryny internetowej w Visual Studio rozpoczynasz od *projektu*. W sensie logicznym projekt zawiera wszystkie pliki, które są kompilowane w pliku wykonywalnym, bibliotece lub witrynie internetowej. Te pliki mogą zawierać kod źródłowy, ikony, obrazy, pliki danych i tak dalej. Projekt zawiera również ustawienia kompilatora i inne pliki konfiguracji, które mogą być potrzebne przez różne usługi lub składniki, z których program komunikuje się.

### <a name="project-file"></a>Plik projektu

Visual Studio używa [programu MSBuild](../msbuild/msbuild.md) do kompilowania każdego projektu w rozwiązaniu, a każdy projekt zawiera plik projektu MSBuild. Rozszerzenie pliku odzwierciedla typ projektu, na przykład projekt języka C# (csproj), projekt Visual Basic (vbproj) lub projekt bazy danych (dbproj). Plik projektu jest dokumentem XML zawierającym wszystkie informacje i instrukcje, których program MSBuild potrzebuje do skompilowania projektu, w tym zawartość, wymagania dotyczące platformy, informacje o wersji, ustawienia serwera sieci Web lub serwera bazy danych oraz zadania do wykonania.

Pliki projektu są oparte na [schemacie XML programu MSBuild.](../msbuild/msbuild-project-file-schema-reference.md) Aby sprawdzić zawartość nowszej zawartości plików projektu w stylu zestawu [SDK](../msbuild/how-to-use-project-sdk.md) w programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu w programie **Eksplorator rozwiązań** wybierz pozycję **Edytuj \<projectname\>**. Aby przyjrzeć się zawartości projektu .NET Framework innych projektów tego stylu, najpierw zwolnij projekt (kliknij prawym przyciskiem myszy węzeł projektu w programie Eksplorator rozwiązań i wybierz pozycję **Unload Project** **(Zwolnij** projekt). Następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Edytuj \<projectname\>**.

> [!NOTE]
> Nie trzeba używać rozwiązań ani projektów w programie Visual Studio do edytowania, kompilowania i debugowania kodu. Możesz po prostu otworzyć folder zawierający pliki źródłowe w programie Visual Studio rozpocząć edytowanie. Aby uzyskać więcej informacji, zobacz Develop code in Visual Studio without projects or solutions (Tworzenie kodu w Visual Studio [bez projektów i rozwiązań).](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

### <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem utworzenia nowego projektu jest użycie szablonu projektu dla typu projektu. Szablon projektu zawiera podstawowy zestaw wstępnie wygenerowanych plików kodu, plików konfiguracji, zasobów i ustawień. Użyj **opcji Nowy**  >  **projekt**  >  **pliku,** aby wybrać szablon projektu. Aby uzyskać więcej informacji, [zobacz Create a new project (Tworzenie nowego projektu).](create-new-project.md)

Można również utworzyć niestandardowy szablon projektu, z których można tworzyć nowe projekty. Aby uzyskać więcej informacji, zobacz [Create project and item templates (Tworzenie szablonów projektów i elementów).](../ide/creating-project-and-item-templates.md)

Podczas tworzenia nowego projektu program Visual Studio go w domyślnej lokalizacji, *%USERPROFILE%\source\repos.* Aby zmienić tę lokalizację, przejdź do **pozycji Narzędzia**  >  **Opcje**  >  **Projekty i**  >  **lokalizacje rozwiązań.** Aby uzyskać więcej informacji, zobacz [Opcje okno dialogowe: Projekty i rozwiązania > lokalizacji.](./reference/projects-solutions-locations-options.md)

## <a name="solutions"></a>Rozwiązania

Projekt znajduje się w *rozwiązaniu*. Pomimo swojej nazwy rozwiązanie nie jest "odpowiedzią". Jest to po prostu kontener dla co najmniej jednego powiązanego projektu wraz z informacjami o kompilacji, ustawieniami okna Visual Studio i innymi plikami, które nie są skojarzone z konkretnym projektem.

### <a name="solution-file"></a>Plik rozwiązania

Visual Studio używa dwóch typów plików *(sln* i *suo)* do przechowywania ustawień rozwiązań:

|Wewnętrzny|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Visual Studio rozwiązania|Organizuje projekty, elementy projektu i elementy rozwiązania w rozwiązaniu.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje ustawienia i dostosowania na poziomie użytkownika, takie jak punkty przerwania.|

> [!IMPORTANT]
> Rozwiązanie jest opisane przez plik tekstowy (rozszerzenie *.sln*) z własnym unikatowym formatem; Nie jest ona przeznaczona do ręcznego edytowania. Z drugiej strony *plik suo* jest ukrytym plikiem, który nie jest wyświetlany w obszarze domyślnych Eksplorator plików ustawień. Aby wyświetlić ukryte pliki, w menu **Widok** Eksplorator plików zaznacz pole **wyboru Ukryte** elementy.

### <a name="solution-folder"></a>Folder rozwiązania

"Folder rozwiązania" to folder wirtualny, który znajduje się tylko w Eksplorator rozwiązań **,** w którym można go używać do grupowania projektów w rozwiązaniu. Jeśli chcesz zlokalizować plik rozwiązania na komputerze, przejdź do pozycji Narzędzia   >  **Opcje**  >  **Projekty i**  >  **lokalizacje rozwiązań.** Aby uzyskać więcej informacji, zobacz [Opcje okno dialogowe: Projekty i rozwiązania > lokalizacji.](./reference/projects-solutions-locations-options.md)

> [!TIP]
> Aby uzyskać przykładowy projekt i rozwiązanie utworzone od podstaw wraz z instrukcjami krok po kroku i przykładowym kodem, zobacz [Introduction to projects and solutions (Wprowadzenie](../get-started/tutorial-projects-solutions.md)do projektów i rozwiązań).

## <a name="solution-explorer"></a>Eksplorator rozwiązań

Po utworzeniu nowego projektu możesz użyć programu Eksplorator rozwiązań do wyświetlania projektu i rozwiązania oraz skojarzonych z **nim** elementów oraz zarządzania nimi. Na poniższej **ilustracji Eksplorator rozwiązań** z rozwiązaniem w języku C#, które zawiera dwa projekty:

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dwoma projektami.](../ide/media/vs2015_solution_explorer.png)

Pasek narzędzi w górnej **części** Eksplorator rozwiązań przyciski służące do przełączania z widoku rozwiązania do widoku folderu, wyświetlania ukrytych plików, zwijania wszystkich węzłów i nie tylko.

::: moniker-end

::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający Eksplorator rozwiązań z dwoma projektami w Visual Studio.](../ide/media/solution-explorer.png)

Pasek narzędzi w górnej części witryny **Eksplorator rozwiązań** ma przyciski służące do przełączania z widoku rozwiązania do widoku [](managing-project-and-solution-properties.md) folderu, filtrowania oczekujących zmian, wyświetlania wszystkich plików, zwijania wszystkich węzłów, wyświetlania stron właściwości, wyświetlania kodu podglądu w edytorze kodu i nie tylko. [](writing-code-in-the-code-and-text-editor.md)

::: moniker-end

Wiele poleceń menu jest dostępnych z menu kontekstowego dostępnego po kliknięciu prawym przyciskiem myszy dla różnych elementów **Eksplorator rozwiązań**. Polecenia te obejmują tworzenie projektu, zarządzanie pakietami NuGet, dodawanie odwołania, zmienianie nazwy pliku i uruchamianie testów.

W ASP.NET Core można dostosować sposób zagnieżdżanie plików w Eksplorator rozwiązań **.** Aby uzyskać więcej informacji, zobacz [Dostosowywanie zagnieżdżania plików w Eksplorator rozwiązań](file-nesting-solution-explorer.md).

> [!TIP]
> Jeśli zamknięto okno Eksplorator rozwiązań otworzyć go ponownie, wybierz pozycję Wyświetl Eksplorator rozwiązań na pasku menu lub naciśnij  >   **klawisze Ctrl** + **Alt** + **L**. Jeśli karty boczne zostały zamknięte i chcesz przywrócić je do domyślnych lokalizacji, wybierz pozycję **Układ** okna  >  **resetowania okna** na pasku menu.

> [!NOTE]
> Aby wyświetlić obrazy aplikacji i ikony wyświetlane w Visual Studio, pobierz Visual Studio [**Image Library.**](https://www.microsoft.com/download/details.aspx?id=35825)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do projektów i rozwiązań](../get-started/tutorial-projects-solutions.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Odfiltrowane rozwiązania w Visual Studio](filtered-solutions.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Zasoby dotyczące rozwiązywania problemów Visual Studio IDE](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
- [Projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/projects-and-solutions)
