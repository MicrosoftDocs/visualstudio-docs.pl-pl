---
title: Tworzenie niestandardowych szablonów projektów i elementów | Microsoft Docs
description: Dowiedz się, jak szablony tworzenia szablonów w zestawie SDK programu Visual Studio umożliwiają uwzględnianie szablonów w większych rozszerzeniach.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: overview
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: afddd162312ac686e97df84bec0f48dc0478c898
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055768"
---
# <a name="create-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i elementów

Zestaw Visual Studio SDK zawiera szablony projektów, które tworzą niestandardowy szablon projektu i szablon elementu niestandardowego. Te szablony obejmują kilka typowych podstawiania parametrów i Kompiluj jako pliki zip. Nie są one wdrażane automatycznie i nie są dostępne w eksperymentalnym wystąpieniu. Należy skopiować wygenerowany plik zip do katalogu szablonów użytkownika.

Szablony tworzenia szablonów umożliwiają uwzględnianie szablonów w większych rozszerzeniach. Dzięki temu można zaimplementować kontrolę wersji na plikach źródłowych i utworzyć grupę projektów szablonów w jednym pakiecie VSIX.

Możesz również skonfigurować szablon, aby zainstalować pakiety NuGet. Aby uzyskać więcej informacji, zobacz [pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

W przypadku scenariuszy tworzenia szablonu podstawowego należy użyć kreatora **eksportu szablonów** , który wyprowadza dane wyjściowe do skompresowanego pliku. Aby uzyskać więcej informacji na temat tworzenia szablonu podstawowego, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu niestandardowych szablonów projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi dostarczyć pliki manifestu szablonu opisujące lokalizację instalacji tych szablonów. Aby zaktualizować rozszerzenia VSIX, można użyć programu Visual Studio 2017. W przypadku wdrożenia rozszerzenia przy użyciu pliku MSI musisz ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Utwórz szablon projektu

1. Utwórz projekt szablonu projektu. Szablon projektu można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "szablon projektu" i wybierając wersję C# lub Visual Basic.

     Szablon generuje plik klasy, ikonę, plik *. vstemplate* , edytowalny plik projektu o nazwie *ProjectTemplate. vbproj* lub *ProjectTemplate. csproj* i niektóre pliki, które są zwykle generowane przez inne typy projektów, takie jak plik *zasobów. resx* , plik *AssemblyInfo* i plik *. Settings* . Każdy plik kodu zawiera wspólne podstawienia parametrów, tam gdzie jest to konieczne.

![wybór projektu szablonu projektu](media/project-template-selection.png)

2. Dodaj i Usuń elementy z projektu zgodnie z wymaganiami projektu. Nie usuwaj edytowalnego pliku projektu, pliku *AssemblyInfo* ani pliku *. vstemplate* .

3. Zaktualizuj plik *. vstemplate* , aby odzwierciedlał wszelkie dodatki i usunięcia. Element [projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) dla każdego pliku, który ma zostać uwzględniony w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość dodaną do użytkownika i Dodaj odpowiednie podstawiania parametrów.

5. W razie potrzeby zmodyfikuj wygenerowaną zawartość.

6. Skompiluj projekt.

     Program Visual Studio tworzy plik *zip* , który zawiera szablon. Nie jest ona wdrożona i nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="create-an-item-template"></a>Utwórz szablon elementu

1. Utwórz projekt szablonu elementu.

     Szablon generuje plik klasy, ikonę, plik *. vstemplate* i plik *AssemblyInfo* . Plik klasy zawiera kilka typowych podstawiania parametrów.

2. Dodaj i Usuń elementy z projektu zgodnie z wymaganiami projektu.

3. Zaktualizuj plik *. vstemplate* , aby odzwierciedlał wszelkie dodatki i usunięcia. Element [projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) dla każdego pliku, który ma zostać uwzględniony w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość dodaną do użytkownika i Dodaj odpowiednie podstawiania parametrów.

5. W razie potrzeby zmodyfikuj wygenerowaną zawartość.

6. Skompiluj projekt.

     Program Visual Studio tworzy skompresowany plik, który zawiera szablon. Nie jest ona wdrożona i nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="deployment"></a>Wdrożenie

### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu

1. Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

2. Ustaw projekt VSIX jako projekt startowy. W **Eksplorator rozwiązań** wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3. Ustaw projekt szablonu projektu jako element zawartości projektu VSIX. Otwórz plik *. vsixmanifest* . Przejdź do karty **składniki** i wybierz pozycję **Nowy**.

    1. Ustaw wartość pola **Typ** na **Microsoft. VisualStudio. ProjectTemplate** lub **Microsoft. VisualStudio. ItemTemplate**.

    2. W obszarze Źródło wybierz opcję **projekt w bieżącym rozwiązaniu** , a następnie wybierz projekt, który zawiera szablon.

4. Skompiluj rozwiązanie i naciśnij klawisz **F5**. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W przypadku projektu szablonu projektu powinien zostać wyświetlony szablon projektu w oknie dialogowym **Nowy projekt** (**plik**  >  **Nowy**  >  **projekt**) w węźle Visual C# lub Visual Basic. Dla projektu szablonu elementu powinien zostać wyświetlony szablon elementu na liście w oknie dialogowym **Dodaj nowy element** . Aby wyświetlić okno dialogowe **Dodawanie nowego elementu** , w **Eksplorator rozwiązań** wybierz węzeł projektu i wybierz pozycję **Dodaj**  >  **nowy element**).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do szablonu programu Visual Studio](../ide/creating-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
