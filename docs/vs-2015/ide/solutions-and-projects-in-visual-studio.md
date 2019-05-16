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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 340fe819086d3cc18cb9c2dd6a4ca14129c6d8ad
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679878"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia aplikacji, aplikacji, witryny sieci Web, aplikacji sieci Web skrypt wtyczki itp w programie Visual Studio, możesz zaczynać *projektu*. W sensie logicznym projekt zawiera wszystkich plikach kodu źródłowego, ikony, obrazy, pliki danych i dowolne inne zostanie skompilowany w program wykonywalny lub witryny sieci web; w przeciwnym razie jest wymagane w celu wykonywania kompilacji.  Projekt zawiera również wszystkie ustawienia kompilatora i inne pliki konfiguracyjne, które mogą być wymagane przez różnych dostawców usług ani składników, które program będzie komunikować się z.

 W tym sensie literału projektu to plik XML (*.vbproj, \*.csproj, \*.vcxproj) definiujący hierarchii folder wirtualny, wraz ze ścieżkami do wszystkich elementów "zawiera" i wszystkich ustawień kompilacji. W programie Visual Studio plik projektu jest używany przez Eksploratora rozwiązań do wyświetlania zawartości projektu i ustawień. Podczas kompilowania projektu aparat MSBuild używa pliku projektu, aby utworzyć plik wykonywalny. Można również dostosować projekty do produktu inne rodzaje danych wyjściowych.

 Projekt znajduje się, w sensie logicznym i w systemie plików w ramach *rozwiązania*, które mogą zawierać jeden lub więcej projektów, oraz informacje o kompilacji, ustawienia okna programu Visual Studio i różne pliki, które nie są skojarzone z jakimkolwiek projektem. W tym sensie literału rozwiązania jest plikiem tekstowym swój własny unikatowy format; Ogólnie nie zamierza się być edytowane ręcznie.

 To rozwiązanie ma plik *.suo skojarzone, który przechowuje ustawienia i preferencje i informacje o konfiguracji dla każdego użytkownika, który pracuje nad projektem.

 Na poniższym diagramie przedstawiono relację między projektami i rozwiązaniami i elementy, które zawierają logicznie.

 ![Visual Studio projekty i rozwiązania](../ide/media/vs2015-project-diagram.png "vs2015_project_diagram")

 Można również utworzyć niestandardowe szablony projektów i elementów. Aby uzyskać więcej informacji, zobacz [tworzenie projektów i szablonów elementów](../ide/creating-project-and-item-templates.md).

## <a name="creating-new-projects"></a>Tworzenie nowych projektów
 Najprostszym sposobem utworzenia nowego projektu jest uruchomienie przy użyciu szablonu projektu wstępnie zdefiniowane, co składa się z podstawowego zestawu wstępnie wygenerowanego kodu pliki, pliki konfiguracji, zasobów, i ustawienia, które ułatwiają pracę, tworzenia określonego typu aplikacji lub witryny sieci Web w języków programowania. Te szablony są, zostanie wyświetlony w **okna dialogowego Nowy projekt** po wybraniu **pliku &#124; New &#124; projektu** lub **pliku &#124; New &#124; witryny sieci Web** z menu głównego, a następnie przejdź. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md) i [NIB tworzenie projektów z szablonów](https://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Zarządzanie projektami w Eksploratorze rozwiązań
 Po utworzeniu nowego projektu, należy użyć **Eksploratora rozwiązań** do przeglądania i zarządzania projektów i rozwiązań i ich skojarzonych elementów. Poniższa ilustracja przedstawia Eksploratora serwera za pomocą rozwiązań języka C#, która zawiera dwa projekty.

 ![Eksplorator rozwiązań](../ide/media/vs2015-solution-explorer.png "vs2015_solution_explorer")

## <a name="in-this-section"></a>W tej sekcji

- [Tworzenie rozwiązań i projektów](../ide/creating-solutions-and-projects.md)

- [Dodawanie i usuwanie elementów projektu](../ide/adding-and-removing-project-items.md)

- [Zarządzanie właściwościami projektu i rozwiązania](../ide/managing-project-and-solution-properties.md)

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)

- [Właściwości aplikacji](../ide/application-properties.md)

- [Zarządzanie podpisywaniem zestawu i manifestu](../ide/managing-assembly-and-manifest-signing.md)

- [Instrukcje: Określanie ikony aplikacji (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

- [Określanie konkretnej wersji programu .NET Framework jako docelowej](../ide/targeting-a-specific-dotnet-framework-version.md)

- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>Zobacz też
 [Visual Studio IDE](../ide/visual-studio-ide.md)
