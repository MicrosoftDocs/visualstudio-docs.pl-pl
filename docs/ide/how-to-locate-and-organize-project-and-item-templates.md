---
title: Lokalizowanie szablonów
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f9035e63fd172727f3bfae44e18a0727599d4edc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645881"
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

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2017 \\ \<edition > \\Common7 \IDE\ProjectTemplates \\ < Language \> \\ < identyfikator ustawień regionalnych \>*

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2017 \\ \<edition > \Common7\IDE\ItemTemplates \\ < Language \> \\ < identyfikator ustawień regionalnych \>*

Na przykład następujący katalog ma Visual Basic szablonów elementów dla języka angielskiego (LCID 1033):

*C: \\Program Files (x86) \\Microsoft Visual Studio \\2017 \\Community \\Common7 \\IDE \\ItemTemplates \\VisualBasic \\1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2019 \\ \<edition > \\Common7 \IDE\ProjectTemplates \\ < Language \> \\ < identyfikator ustawień regionalnych \>*

- *% ProgramFiles (x86)% \\Microsoft Visual Studio \\2019 \\ \<edition > \Common7\IDE\ItemTemplates \\ < Language \> \\ < identyfikator ustawień regionalnych \>*

Na przykład następujący katalog ma Visual Basic szablonów elementów dla języka angielskiego (LCID 1033):

*C: \\Program Files (x86) \\Microsoft Visual Studio \\2019 \\Community \\Common7 \\IDE \\ItemTemplates \\VisualBasic \\1033*

::: moniker-end

### <a name="user-templates"></a>Szablony użytkowników

Jeśli dodasz plik skompresowany ( *. zip*), który zawiera plik *. vstemplate* do katalogu szablonów użytkownika, szablon zostanie wyświetlony w oknach dialogowych nowy projekt i nowy element. Domyślnie szablony użytkowników znajdują się w:

::: moniker range="vs-2017"

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2017 \ Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektu użytkownika dla C#:

- *C:\Users\UserName\Documents\Visual Studio 2017 \ Templates\ProjectTemplates\VisualC#*

::: moniker-end

::: moniker range=">=vs-2019"

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio 2019 \ Templates\ItemTemplates*

Na przykład następujący katalog zawiera szablony projektu użytkownika dla C#:

- *C:\Users\UserName\Documents\Visual Studio 2019 \ Templates\ProjectTemplates\VisualC#*

::: moniker-end

> [!TIP]
> Znaną lokalizację szablonów użytkowników można zmienić w obszarze **narzędzia**  > **Opcje**  > **projekty i rozwiązania**  > **lokalizacje**.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Organizowanie szablonów

Kategorie w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** odzwierciedlają struktury katalogów, które istnieją w zainstalowanych szablonach i lokalizacjach szablonów użytkownika. Szablony użytkowników można organizować w własne kategorie, dodając nowe foldery do katalogu szablonów użytkownika. W oknach dialogowych **Nowy projekt** i **Dodaj nowy element** są wyświetlane wszelkie zmiany wprowadzone w kategoriach szablonów użytkowników.

> [!NOTE]
> Nie można utworzyć nowej kategorii na poziomie języka programowania. Nowe kategorie można tworzyć tylko w obrębie każdego języka.

### <a name="create-new-user-project-template-categories"></a>Tworzenie nowych kategorii szablonów projektu użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonów projektu użytkownika. Na przykład aby określić kategorię **HelloWorld** dla C# szablonów projektu, Utwórz następujący katalog:

    - *\%USERPROFILE% \ Documents\Visual Studio \<Version \> \Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. W menu **plik** wybierz **Nowy** **projekt**>.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Nowy projekt** w obszarze **zainstalowane** > **C#Wizualizacja**.

### <a name="create-new-user-item-template-categories"></a>Tworzenie nowych kategorii szablonów elementów użytkownika

1. Utwórz folder w folderze języka programowania w katalogu szablonów elementu użytkownika. Na przykład aby określić kategorię **HelloWorld** dla C# szablonów elementów, należy utworzyć następujący katalog:

    - *\%USERPROFILE% \ Documents\Visual Studio \<Version \> \Templates\ItemTemplates\Visual C#\HelloWorld*

1. Umieść wszystkie szablony dla tej kategorii w nowym folderze.

1. Utwórz projekt lub Otwórz istniejący projekt. Następnie w menu **projekt** wybierz polecenie **Dodaj nowy element**.

   Kategoria **HelloWorld** zostanie wyświetlona w oknie dialogowym **Dodaj nowy element** w obszarze **zainstalowane** > **elementy wizualne C#** .

### <a name="display-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategoriach nadrzędnych

Szablony w podkategoriach można włączyć do wyświetlania w swoich kategoriach nadrzędnych za pomocą elementu `NumberOfParentCategoriesToRollUp` w pliku *vstemplate* . Te kroki są takie same dla szablonów projektu i szablonów elementów.

1. Znajdź plik *zip* , który zawiera szablon.

1. Wyodrębnij plik *zip* .

1. Otwórz plik *. vstemplate* w programie Visual Studio.

1. W `TemplateData` elementu Dodaj element `NumberOfParentCategoriesToRollUp`. Na przykład poniższy kod powoduje, że szablon jest widoczny w kategorii nadrzędnej, ale nie jest wyższy.

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

1. Wybierz pliki w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do** > **folderu skompresowanego (spakowanego)** .

   Pliki są kompresowane do pliku *zip* .

1. Usuń wyodrębnione pliki szablonów i stary plik template *. zip* .

1. Umieść nowy plik *zip* w katalogu, który miał usunięty plik. *zip* .

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)