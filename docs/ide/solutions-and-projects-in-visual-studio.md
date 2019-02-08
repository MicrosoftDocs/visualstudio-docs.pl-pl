---
title: Rozwiązania i projekty
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8302c517f28e32c154f688bd9f282070013f812
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957827"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Rozwiązania i projekty w programie Visual Studio

W tym artykule opisano pojęcia *projektu* i *rozwiązania* w programie Visual Studio. Również krótko opisano sposób tworzenia nowego projektu i **Eksploratora rozwiązań** okna narzędzi.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [projektów i rozwiązań w programie Visual Studio dla komputerów Mac](/visualstudio/mac/projects-and-solutions).

## <a name="projects"></a>Projekty

Podczas tworzenia aplikacji witryny sieci Web dodatku typu plug-in, etc. w programie Visual Studio, możesz zaczynać *projektu*. W sensie logicznym projekt zawiera wszystkie pliki kodu źródłowego, ikony, obrazy, pliki danych, itp., które są kompilowane do pliku wykonywalnego, biblioteki lub witryny sieci Web. Projekt zawiera także ustawienia kompilatora i inne pliki konfiguracyjne, które mogą być wymagane przez różnych dostawców usług ani składników, które komunikuje się program.

> [!NOTE]
> Nie masz na potrzeby rozwiązań lub projektów w programie Visual Studio Edytuj, twórz i Debuguj kod. Możesz po prostu otwórz folder, który zawiera plików źródłowych w programie Visual Studio i rozpocząć edycję. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

Projekt został zdefiniowany w pliku XML z rozszerzeniem, takich jak *.vbproj*, *.csproj*, lub *.vcxproj*. Ten plik zawiera folder wirtualny hierarchii i ścieżki do wszystkich elementów w projekcie. Zawiera ona także ustawienia kompilacji.

> [!TIP]
> Aby wyświetlić zawartość pliku projektu w programie Visual Studio, najpierw Zwolnij projekt, wybierając nazwę projektu w **Eksploratora rozwiązań** i wybierając pozycję **Zwolnij projekt** z menu kontekstowego lub kliknij prawym przyciskiem myszy. Następnie ponownie otwórz menu kontekstowe i wybierz **Edytuj \<projectname\>**.

W programie Visual Studio, plik projektu jest używany przez **Eksploratora rozwiązań** do wyświetlania zawartości projektu i ustawień. Podczas kompilowania projektu aparat MSBuild używa pliku projektu, aby utworzyć plik wykonywalny. Można również dostosować projekty do tworzenia innych rodzajów danych wyjściowych.

## <a name="solutions"></a>Rozwiązania

Projekt jest zawarty w *rozwiązania*. Pomimo swojej nazwy rozwiązania nie jest "" (odpowiedź). Jest po prostu kontener dla jednego lub kilku powiązanych projektów, oraz informacje o kompilacji, ustawienia okna programu Visual Studio i różne pliki, które nie są skojarzone z określonym projektem. To rozwiązanie jest opisany przez plik tekstowy (rozszerzenie *.sln*) swój własny unikatowy format; go ma nie powinny być edytowane ręcznie.

Program Visual Studio używa dwóch typów plików (*.sln* i *.suo*) do przechowywania ustawień rozwiązania:

|Wewnętrzny|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Visual Studio Solution|Organizuje projekty, elementy projektu i rozwiązania elementów w rozwiązaniu.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje ustawienia na poziomie użytkownika i dostosowania, takie jak punkty przerwania.|

## <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem utworzenia nowego projektu jest Rozpocznij od szablonu projektu dla danego typu aplikacji lub witryny sieci Web. Szablon projektu składa się z podstawowego zestawu wstępnie wygenerowanego kodu pliki, pliki konfiguracji, zasobów i ustawień. Te szablony są, zostanie wyświetlony w **nowy projekt** okno dialogowe, w przypadku wybrania **pliku** > **New** > **projektu**. Aby uzyskać więcej informacji, zobacz [tworzenia rozwiązań i projektów](../ide/creating-solutions-and-projects.md).

Można również utworzyć niestandardowe szablony projektów i elementów. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="manage-projects-in-solution-explorer"></a>Zarządzaj projektami w Eksploratorze rozwiązań

Po utworzeniu nowego projektu, można użyć **Eksploratora rozwiązań** do przeglądania i zarządzania projektu i rozwiązania i ich skojarzonych elementów. Poniższa ilustracja przedstawia **Eksploratora rozwiązań** z C# rozwiązanie, które zawiera dwa projekty:

![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/projects-and-solutions)
- [Dodawanie i usuwanie elementów projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/add-and-remove-project-items)