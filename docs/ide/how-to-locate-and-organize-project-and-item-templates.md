---
title: Lokalizowanie szablonów
description: Dowiedz się, jak lokalizować i organizować szablony projektów i elementów.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: ba986fee3f5cf6098b72f3b7a52340a61d3449d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962863"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Instrukcje: Lokalizowanie i organizowanie szablonów projektów i elementów

Pliki szablonów muszą być umieszczone w znanej lokalizacji, aby były wyświetlane w oknach dialogowych nowy projekt i nowy element.

::: moniker range="vs-2017"

Możesz również utworzyć niestandardowe podkategorie w lokalizacji szablonu użytkownika, a kategorie są wyświetlane w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** .

::: moniker-end

## <a name="locate-templates"></a>Lokalizowanie szablonów

Zainstalowane szablony i szablony użytkownika są przechowywane w dwóch różnych lokalizacjach.

### <a name="installed-templates"></a>Zainstalowane szablony

Domyślnie szablony zainstalowane z programem Visual Studio znajdują się w temacie:

::: moniker range="vs-2017"

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<język \> \\<identyfikator ustawień regionalnych\>*

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \COMMON7\IDE\ITEMTEMPLATES \\<język \> \\<identyfikator ustawień regionalnych\>*

Na przykład następujący katalog ma Visual Basic szablonów elementów dla języka angielskiego (LCID 1033):

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2017 \\ Community \\ Common7 \\ IDE \\ elementów \\ VisualBasic \\ 1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<język \> \\<identyfikator ustawień regionalnych\>*

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \COMMON7\IDE\ITEMTEMPLATES \\<język \> \\<identyfikator ustawień regionalnych\>*

Na przykład następujący katalog ma Visual Basic szablonów elementów dla języka angielskiego (LCID 1033):

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2019 \\ Community \\ Common7 \\ IDE \\ elementów \\ VisualBasic \\ 1033*

::: moniker-end

### <a name="user-templates"></a>Szablony użytkowników

Jeśli dodasz plik skompresowany (*. zip*), który zawiera plik *. vstemplate* do katalogu szablonów użytkownika, szablon zostanie wyświetlony w oknach dialogowych nowy projekt i nowy element. Domyślnie szablony użytkowników znajdują się w:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektu użytkownika dla języka C#:

- *C:\Users\UserName\Documents\Visual Studio 2017 \ Templates\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektu użytkownika dla języka C#:

- *C:\Users\UserName\Documents\Visual Studio 2019 \ Templates\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> Można zmienić znaną lokalizację szablonów użytkowników w obszarze **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  >  .

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** odzwierciedlają struktury katalogów, które istnieją w zainstalowanych szablonach i lokalizacjach szablonów użytkownika. Szablony użytkowników można organizować w własne kategorie, dodając nowe foldery do katalogu szablonów użytkownika. W oknach dialogowych **Nowy projekt** i **Dodaj nowy element** są wyświetlane wszelkie zmiany wprowadzone w kategoriach szablonów użytkowników.

> [!NOTE]
> Nie można utworzyć nowej kategorii na poziomie języka programowania. Nowe kategorie można tworzyć tylko w obrębie każdego języka.

### <a name="create-new-user-project-template-categories"></a>Tworzenie nowych kategorii szablonów projektu użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonów projektu użytkownika. Na przykład aby określić kategorię **HelloWorld** dla szablonów projektu C#, Utwórz następujący katalog:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ProjectTemplates\Visual C# \HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. W menu **plik** wybierz pozycję **Nowy** > **projekt**.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Nowy projekt** w obszarze **zainstalowane** > **Visual C#**.

### <a name="create-new-user-item-template-categories"></a>Tworzenie nowych kategorii szablonów elementów użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonów elementu użytkownika. Na przykład aby określić kategorię **HelloWorld** dla szablonów elementów języka C#, należy utworzyć następujący katalog:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ItemTemplates\Visual C# \HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Utwórz projekt lub Otwórz istniejący projekt. Następnie w menu **projekt** wybierz polecenie **Dodaj nowy element**.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane** > **elementy Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategoriach nadrzędnych

Szablony w podkategoriach można włączyć do wyświetlania w ich kategoriach nadrzędnych za pomocą `NumberOfParentCategoriesToRollUp` elementu w pliku *. vstemplate* . Te kroki są takie same dla szablonów projektu i szablonów elementów.

1. Znajdź plik *zip* , który zawiera szablon.

1. Wyodrębnij plik *zip* .

1. Otwórz plik *. vstemplate* w programie Visual Studio.

1. W `TemplateData` elemencie Dodaj `NumberOfParentCategoriesToRollUp` element. Na przykład poniższy kod powoduje, że szablon jest widoczny w kategorii nadrzędnej, ale nie jest wyższy.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Zapisz i zamknij plik *. vstemplate* .

1. Wybierz pliki w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do** > **folderu skompresowanego (spakowanego)**.

   Pliki są kompresowane do pliku *zip* .

1. Usuń wyodrębnione pliki szablonów i stary plik template *. zip* .

1. Umieść nowy plik *zip* w katalogu, który miał usunięty plik. *zip* .

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
