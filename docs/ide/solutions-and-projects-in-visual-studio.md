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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42a8dbc2fd9a6fc89b0be62271b048f8275a82b2
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432202"
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
> Aby wyświetlić zawartość pliku projektu w programie Visual Studio, najpierw Zwolnij projekt, wybierając nazwę projektu w **Eksploratora rozwiązań** i wybierając pozycję **Zwolnij projekt** z menu kontekstowego lub kliknij prawym przyciskiem myszy. Następnie ponownie otwórz menu kontekstowe i wybierz **Edytuj \<projectname\>** .

W programie Visual Studio, plik projektu jest używany przez **Eksploratora rozwiązań** do wyświetlania zawartości projektu i ustawień. Podczas kompilowania projektu aparat MSBuild używa pliku projektu, aby utworzyć plik wykonywalny. Można również dostosować projekty do tworzenia innych rodzajów danych wyjściowych.

## <a name="solutions"></a>Rozwiązania

Projekt jest zawarty w *rozwiązania*. Pomimo swojej nazwy rozwiązania nie jest "" (odpowiedź). Jest po prostu kontener dla jednego lub kilku powiązanych projektów, oraz informacje o kompilacji, ustawienia okna programu Visual Studio i różne pliki, które nie są skojarzone z określonym projektem. To rozwiązanie jest opisany przez plik tekstowy (rozszerzenie *.sln*) swój własny unikatowy format; go ma nie powinny być edytowane ręcznie.

Program Visual Studio używa dwóch typów plików ( *.sln* i *.suo*) do przechowywania ustawień rozwiązania:

|Wewnętrzny|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Visual Studio Solution|Organizuje projekty, elementy projektu i rozwiązania elementów w rozwiązaniu.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje ustawienia na poziomie użytkownika i dostosowania, takie jak punkty przerwania.|

## <a name="create-new-projects"></a>Utwórz nowe projekty

Najprostszym sposobem utworzenia nowego projektu jest Rozpocznij od szablonu projektu dla danego typu aplikacji lub witryny sieci Web. Szablon projektu składa się z podstawowego zestawu wstępnie wygenerowanego kodu pliki, pliki konfiguracji, zasobów i ustawień. Te szablony są dostępne w oknie dialogowym, w której utworzono nowy projekt (**pliku** > **New** > **projektu**). Aby uzyskać więcej informacji, zobacz [Utwórz nowy projekt w programie Visual Studio](create-new-project.md) i [tworzenia rozwiązań i projektów](../ide/creating-solutions-and-projects.md).

W przypadku dostosowania często Twoje projekty w określony sposób, można utworzyć szablonu niestandardowego projektu, która następnie umożliwia tworzenie nowych projektów z. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

Podczas tworzenia nowego projektu jest zapisywane domyślnie w *%USERPROFILE%\source\repos*. Możesz zmienić tę lokalizację w **projektów lokalizacji** w obszarze **narzędzia** > **opcje** > **projekty i Rozwiązania** > **lokalizacje**. Aby uzyskać więcej informacji, zobacz [strony Projekty i rozwiązania, okno dialogowe Opcje](../ide/reference/projects-and-solutions-options-dialog-box.md).

## <a name="solution-explorer"></a>Eksplorator rozwiązań

Po utworzeniu nowego projektu, można użyć **Eksploratora rozwiązań** wyświetlanie oraz zarządzanie nimi i ich skojarzone elementy projektu i rozwiązania. Poniższa ilustracja przedstawia **Eksploratora rozwiązań** z C# rozwiązanie, które zawiera dwa projekty:

![Eksplorator rozwiązań](../ide/media/vs2015_solution_explorer.png)

Wiele poleceń menu są dostępne w menu kliknij prawym przyciskiem myszy na różne elementy w **Eksploratora rozwiązań**. Są to skompilowanie projektu, Zarządzanie pakietami NuGet, Dodawanie odwołania, zmiany nazwy pliku, i Uruchamianie testów, wystarczy kilka. Pasek narzędzi w górnej części **Eksploratora rozwiązań** ma przycisków, aby przełączyć się z widoku rozwiązania na widok folderu, Pokaż ukryte pliki, Zwiń wszystkie węzły i nie tylko.

Dla projektów ASP.NET Core, można dostosować sposób pliki są zagnieżdżone w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [dostosować zagnieżdżanie plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md).

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/projects-and-solutions)
- [Dodawanie i usuwanie elementów projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/add-and-remove-project-items)
