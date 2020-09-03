---
title: Rozwiązania i projekty
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b1783adadd1bfab32bfbbdcfb5ae28df7c0aae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661193"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia aplikacji, aplikacji, witryny internetowej, aplikacji sieci Web, skryptu, wtyczki itp. w programie Visual Studio rozpoczyna się od *projektu*. W sensie logicznym projekt zawiera wszystkie pliki kodu źródłowego, ikony, obrazy, pliki danych i wszystkie inne, które zostaną skompilowane w programie wykonywalnym lub w witrynie sieci Web, lub w przeciwnym razie jest to konieczne, aby można było wykonać kompilację.  Projekt zawiera również wszystkie ustawienia kompilatora i inne pliki konfiguracji, które mogą być konieczne przez różne usługi lub składniki, z którymi program będzie się komunikować.

 W sensie literału projekt jest plikiem XML (*. vbproj, \* . csproj, \* . vcxproj), który definiuje hierarchię folderów wirtualnych wraz ze ścieżkami do wszystkich elementów, które zawiera, i wszystkich ustawień kompilacji. W programie Visual Studio plik projektu jest używany przez Eksplorator rozwiązań do wyświetlania zawartości i ustawień projektu. Podczas kompilowania projektu aparat MSBuild zużywa plik projektu w celu utworzenia pliku wykonywalnego. Możesz również dostosować projekty do innych typów danych wyjściowych produktu.

 Projekt jest zawarty w *rozwiązaniu*logicznym i w systemie plików w ramach rozwiązania, które może zawierać jeden lub więcej projektów, a także informacje o kompilacji, ustawienia okna programu Visual Studio i inne pliki, które nie są skojarzone z żadnym projektem. W sensie literalnym rozwiązanie jest plikiem tekstowym z własnym unikatowym formatem; zazwyczaj nie jest przeznaczona do edycji.

 Rozwiązanie ma skojarzony plik *. suo, który przechowuje ustawienia, preferencje i informacje o konfiguracji dla każdego użytkownika, który pracował nad projektem.

 Na poniższym diagramie przedstawiono relację między projektami i rozwiązaniami oraz elementy, które zawiera logicznie.

 ![Projekty i rozwiązania programu Visual Studio](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Można również tworzyć niestandardowe szablony projektów i elementów. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Tworzenie nowych projektów
 Najprostszym sposobem tworzenia nowego projektu jest rozpoczęcie ze wstępnie zdefiniowanym szablonem projektu, który składa się z podstawowego zestawu wstępnie wygenerowanych plików kodu, plików konfiguracji, zasobów i ustawień, które ułatwiają rozpoczęcie tworzenia określonego typu aplikacji lub witryny sieci Web w określonym języku programowania. Te szablony są wyświetlane w **oknie dialogowym Nowy projekt** , gdy wybierzesz opcję **plik &#124; nowy &#124; projekt** lub **plik &#124; &#124; nową witrynę sieci Web** z menu głównego, a następnie przejdź. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md) oraz  [NIB tworzenie projektów na podstawie szablonów](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Zarządzanie projektami w Eksplorator rozwiązań
 Po utworzeniu nowego projektu można używać **Eksplorator rozwiązań** do wyświetlania i zarządzania projektami i rozwiązaniami oraz związanymi z nimi elementami. Na poniższej ilustracji przedstawiono Eksplorator serwera z rozwiązaniem w języku C# zawierającym dwa projekty.

 ![Eksplorator rozwiązań](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>W tej sekcji

- [Tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md)

- [Dodawanie i usuwanie elementów projektu](../ide/adding-and-removing-project-items.md)

- [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)

- [Właściwości aplikacji](../ide/application-properties.md)

- [Zarządzanie zestawem i podpisywanie manifestu](../ide/managing-assembly-and-manifest-signing.md)

- [Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [Tworzenie zawartości dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Zobacz też
 [Visual Studio IDE](../ide/visual-studio-ide.md)
