---
title: Lokalizowanie szablonów
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591050"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Jak: Lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonów muszą być umieszczone w znanej lokalizacji, aby były wyświetlane w oknie dialogowym nowego projektu i nowego elementu..

::: moniker range="vs-2017"

Można również utworzyć niestandardowe podkategorie w lokalizacji szablonu użytkownika, a kategorie są wyświetlane w oknach dialogowych **Nowy projekt** i Dodawanie **nowego elementu.**

::: moniker-end

## <a name="locate-templates"></a>Lokalizowanie szablonów

Zainstalowane szablony i szablony użytkowników są przechowywane w dwóch różnych lokalizacjach.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane w programie Visual Studio znajdują się w:

::: moniker range="vs-2017"

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2017 \\edition>Common7\IDE\ProjectTemplates\\<Language\> \\<Locale ID\>*

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2017 edition\\>\Common7\IDE\ItemTemplates\> \\<Language<Locale ID\>*

Na przykład w poniższym katalogu są szablony elementów języka Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Pliki\\programów (x86) Microsoft Visual Studio\\2017\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2019 \\edition>Common7\IDE\ProjectTemplates\\ \> \\<Language<Locale ID\>*

- *%ProgramFiles(x86)%\\Microsoft\\Visual Studio\\\<2019 edition\\>\Common7\IDE\ItemTemplates<\> \\ Language<Locale ID\>*

Na przykład w poniższym katalogu są szablony elementów języka Visual Basic dla języka angielskiego (LCID 1033):

*C:\\Pliki\\programów (x86) Microsoft Visual Studio\\2019\\Community\\Common7\\IDE\\ItemTemplates\\VisualBasic\\1033*

::: moniker-end

### <a name="user-templates"></a>Szablony użytkowników

Jeśli dodasz skompresowany *(zip)* plik zawierający plik *vstemplate* do katalogu szablonów użytkownika, szablon pojawi się w oknach dialogowych nowego projektu i nowego elementu. Domyślnie szablony użytkowników znajdują się w:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017\Szablony\ItemTemplates*

Na przykład następujący katalog ma szablony projektów użytkownika dla języka C#:

- *C:\Użytkownicy\Nazwa użytkownika\Dokumenty\Visual Studio 2017\Szablony\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019\Szablony\ItemTemplates*

Na przykład następujący katalog ma szablony projektów użytkownika dla języka C#:

- *C:\Użytkownicy\Nazwa użytkownika\Dokumenty\Visual Studio 2019\Szablony\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> Znaną lokalizację szablonów użytkowników można zmienić w obszarze**Opcje** >  **narzędzi** > Projekty i**Lokalizacje****rozwiązań** > .

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w oknach dialogowych **Nowy projekt** i **Dodawanie nowego elementu** odzwierciedlają struktury katalogów istniejące w zainstalowanych lokalizacjach szablonów i szablonów użytkowników. Szablony użytkowników można organizować w ich własne kategorie, dodając nowe foldery do katalogu szablonów użytkowników. Okna dialogowe **Nowy projekt** i Dodawanie **nowego elementu** pokazują wszelkie zmiany wprowadzone w kategoriach szablonów użytkowników.

> [!NOTE]
> Nie można utworzyć nowej kategorii na poziomie języka programowania. Nowe kategorie można tworzyć tylko w każdym języku.

### <a name="create-new-user-project-template-categories"></a>Tworzenie nowych kategorii szablonów projektu użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonów projektu użytkownika. Na przykład, aby ustanowić kategorię **HelloWorld** dla szablonów projektów języka C#, utwórz następujący katalog:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**.

   Kategoria **HelloWorld** pojawia się w oknie dialogowym **Nowy projekt** w obszarze **Zainstalowany** > **program Visual C#**.

### <a name="create-new-user-item-template-categories"></a>Tworzenie nowych kategorii szablonów elementów użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonu elementu użytkownika. Na przykład, aby ustanowić kategorię **HelloWorld** dla szablonów elementów języka C#, utwórz następujący katalog:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Utwórz projekt lub otwórz istniejący projekt. Następnie w menu **Projekt** wybierz polecenie **Dodaj nowy element**.

   Kategoria **HelloWorld** pojawia się w oknie dialogowym **Dodawanie nowego elementu** w obszarze **Zainstalowane** > **elementy programu Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategoriach nadrzędnych

Szablony w podkategoriach można włączyć w ich kategoriach `NumberOfParentCategoriesToRollUp` nadrzędnych przy użyciu elementu w pliku *vstemplate.* Te kroki są takie same dla szablonów projektów i szablonów elementów.

1. Znajdź plik *zip* zawierający szablon.

1. Wyodrębnij plik *.zip.*

1. Otwórz plik *vstemplate* w programie Visual Studio.

1. W `TemplateData` elemencie `NumberOfParentCategoriesToRollUp` dodaj element. Na przykład poniższy kod sprawia, że szablon jest widoczny w kategorii nadrzędnej, ale nie wyższy.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Zapisz i zamknij plik *vstemplate.*

1. Zaznacz pliki w szablonie, kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wyślij do** > **folderu Skompresowanego (spakowane).**

   Pliki są kompresowane do pliku *zip.*

1. Usuń wyodrębnione pliki szablonów i stary plik *.zip* szablonu.

1. Umieść nowy plik *zip* w katalogu, który miał usunięty plik *.zip.*

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (szablony programu Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
