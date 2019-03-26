---
title: Znajdź szablony
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db74d23cf42e371f00bf25c7edcd8c480f7649d4
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415463"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Instrukcje: Lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonu muszą być umieszczone w znanej lokalizacji w kolejności ich mają być wyświetlane w nowym projektem i okien dialogowych nowy element...

::: moniker range="vs-2017"

Można również utworzyć niestandardowe podkategorii w lokalizacji szablonu użytkownika i kategorie są wyświetlane w **nowy projekt** i **Dodaj nowy element** okien dialogowych.

::: moniker-end

## <a name="locate-templates"></a>Znajdź szablony

Zainstalowane szablony i użytkowników są przechowywane w dwóch różnych lokalizacjach.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane z programem Visual Studio znajdują się w:

::: moniker range="vs-2017"

- *% ProgramFiles(x86) %\\programu Microsoft Visual Studio\\2017\\\<edition >\\Common7\IDE\ProjectTemplates\\< język\>\\< Identyfikator ustawień regionalnych\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2017\\\<edition>\Common7\IDE\ItemTemplates\\<Language\>\\<Locale ID\>*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles(x86) %\\programu Microsoft Visual Studio\\2019\\\<edition >\\Common7\IDE\ProjectTemplates\\< język\>\\< Identyfikator ustawień regionalnych\>*

- *%ProgramFiles(x86)%\\Microsoft Visual Studio\\2019\\\<edition>\Common7\IDE\ItemTemplates\\<Language\>\\<Locale ID\>*

Na przykład następujący katalog zawiera szablony elementów Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Szablony użytkownika

Jeśli dodasz skompresowany (*zip*) plik, który zawiera *.vstemplate* plik do katalogu szablonu użytkowników szablon jest wyświetlany nowy projekt i okien dialogowych nowy element. Domyślnie szablony użytkownika znajdują się w:

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
> Można zmienić tej lokalizacji dla szablonów użytkownika w **narzędzia** > **opcje** > **projekty i rozwiązania**  >   **Lokalizacje**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w **nowy projekt** i **Dodaj nowy element** okna dialogowe odzwierciedlają struktur katalogów, które istnieją w zainstalowanych lokalizacje szablonów szablonu i użytkownika. Szablony użytkownika może można podzielić na ich własnych kategorii, dodając nowe foldery do katalogu szablonu użytkownika. **Nowy projekt** i **Dodaj nowy element** okna dialogowe pojawią się żadne zmiany wprowadzone do kategorii szablonu użytkownika.

> [!NOTE]
> Nie można utworzyć nową kategorię na poziomie języka programowania. Nowe kategorie można tworzyć tylko w ramach każdego z języków.

### <a name="create-new-user-project-template-categories"></a>Utwórz nowy projekt użytkownika kategorie szablonów

1. Utwórz folder w folderze języka programowania, w katalogu szablonu projektu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię C# szablony projektów, należy utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.

1. Na **pliku** menu, wybierz **New** > **projektu**.

   **HelloWorld** kategorii pojawia się w **nowy projekt** dialogowego **zainstalowane** > **Visual C#** .

### <a name="create-new-user-item-template-categories"></a>Utwórz nowy element użytkownika kategorie szablonów

1. Utwórz folder w folderze języka programowania, w katalogu szablonów elementu użytkownika. Na przykład, aby ustanowić **HelloWorld** kategorię C# szablonów, należy go utworzyć następującego katalogu:

    - *\%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Umieścić wszystkie szablony dla tej kategorii w nowym folderze.

1. Utwórz projekt lub Otwórz istniejący projekt. Następnie na **projektu** menu, wybierz **Dodaj nowy element**.

   **HelloWorld** kategorii pojawia się w **Dodaj nowy element** dialogowego **zainstalowane** > **Visual C# elementów**.

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

1. Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz **wysyłać** > **skompresowany folder (zip)**.

   Pliki są kompresowane do *zip* pliku.

1. Usuń pliki szablonów wyodrębniony i starego szablonu *zip* pliku.

1. Umieść nową *zip* pliku w katalogu, który miał usunięte *zip* pliku.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Instrukcje: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)