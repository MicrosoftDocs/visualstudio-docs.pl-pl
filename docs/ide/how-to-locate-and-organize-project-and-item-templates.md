---
title: Znajdź szablony
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 480f583bb997a19bc84fcfbe6824c12a3c638784
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591050"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Porady: lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonów muszą być umieszczone w znanej lokalizacji, aby były wyświetlane w oknach dialogowych nowy projekt i nowy element.

::: moniker range="vs-2017"

Można również utworzyć niestandardowe podkategorii w lokalizacji szablonu użytkownika i kategorie są wyświetlane w **nowy projekt** i **Dodaj nowy element** okien dialogowych.

::: moniker-end

## <a name="locate-templates"></a>Znajdź szablony

Zainstalowane szablony i użytkowników są przechowywane w dwóch różnych lokalizacjach.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane z programem Visual Studio znajdują się w:

::: moniker range="vs-2017"

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2017\\\<Edition >\\Common7\IDE\ProjectTemplates\\< Language\>\\< identyfikator ustawień regionalnych\>*

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2017\\\<Edition > \Common7\IDE\ItemTemplates\\< Language\>\\< identyfikator ustawień regionalnych\>*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\społeczność\\Common7\\IDE\\elementów\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2019\\\<Edition >\\Common7\IDE\ProjectTemplates\\< Language\>\\< identyfikator ustawień regionalnych\>*

- *% ProgramFiles (x86)%\\Microsoft Visual Studio\\2019\\\<Edition > \Common7\IDE\ItemTemplates\\< Language\>\\< identyfikator ustawień regionalnych\>*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\społeczność\\Common7\\IDE\\elementów\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Szablony użytkownika

Jeśli dodasz plik skompresowany ( *. zip*), który zawiera plik *. vstemplate* do katalogu szablonów użytkownika, szablon zostanie wyświetlony w oknach dialogowych nowy projekt i nowy element. Domyślnie szablony użytkownika znajdują się w:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektów użytkownika dla C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\VisualC#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektów użytkownika dla C#:

- *C:\Users\UserName\Documents\Visual Studio 2019\Templates\ProjectTemplates\Visual C#*

::: moniker-end

> [!TIP]
> Znaną lokalizację szablonów użytkowników można zmienić w obszarze **narzędzia** > **Opcje** > **projekty i rozwiązania** > **lokalizacje**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w **nowy projekt** i **Dodaj nowy element** okna dialogowe odzwierciedlają struktur katalogów, które istnieją w zainstalowanych lokalizacje szablonów szablonu i użytkownika. Szablony użytkownika może można podzielić na ich własnych kategorii, dodając nowe foldery do katalogu szablonu użytkownika. **Nowy projekt** i **Dodaj nowy element** okna dialogowe pojawią się żadne zmiany wprowadzone do kategorii szablonu użytkownika.

> [!NOTE]
> Nie można utworzyć nową kategorię na poziomie języka programowania. Nowe kategorie można tworzyć tylko w ramach każdego z języków.

### <a name="create-new-user-project-template-categories"></a>Tworzenie nowych kategorii szablonów projektu użytkownika

1. Utwórz folder w folderze języka programowania, w katalogu szablonu projektu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię C# szablony projektów, należy utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.

1. W menu **plik** wybierz **Nowy** **projekt**>.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Nowy projekt** w obszarze **zainstalowane** > **C#Wizualizacja**.

### <a name="create-new-user-item-template-categories"></a>Tworzenie nowych kategorii szablonów elementów użytkownika

1. Utwórz folder w folderze języka programowania, w katalogu szablonów elementu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię C# szablonów, należy go utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.

1. Utwórz projekt lub Otwórz istniejący projekt. Następnie na **projektu** menu, wybierz **Dodaj nowy element**.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane** > **elementy wizualne C#** .

### <a name="display-templates-in-parent-categories"></a>Wyświetl szablony w kategorii nadrzędnych

Możesz włączyć szablonów w podkategorii, które mają być wyświetlane w ich kategorii nadrzędnych przy użyciu `NumberOfParentCategoriesToRollUp` element *.vstemplate* pliku. Te kroki są takie same dla szablonów projektów i szablonów elementów.

1. Znajdź *zip* pliku, który zawiera szablon.

1. Wyodrębnij *zip* pliku.

1. Otwórz *.vstemplate* pliku w programie Visual Studio.

1. W `TemplateData` elementu Dodawanie `NumberOfParentCategoriesToRollUp` elementu. Na przykład poniższy kod powoduje, że szablon widoczne w kategorii nadrzędnej, ale nie jest wyższa.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Zapisz i Zamknij *.vstemplate* pliku.

1. Wybierz pliki w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do** > **folderu skompresowanego (spakowanego)** .

   Pliki są kompresowane do *zip* pliku.

1. Usuń pliki szablonów wyodrębniony i starego szablonu *zip* pliku.

1. Umieść nową *zip* pliku w katalogu, który miał usunięte *zip* pliku.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
