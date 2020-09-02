---
title: Tworzenie niestandardowych szablonów projektów i szablonów elementów
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197401"
---
# <a name="creating-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i szablonów elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw Visual Studio SDK zawiera szablony projektów, które tworzą niestandardowy szablon projektu i szablon elementu niestandardowego. Te szablony obejmują kilka typowych podstawiania parametrów i Kompiluj jako pliki zip. Nie są one wdrażane automatycznie i nie są dostępne w eksperymentalnym wystąpieniu. Skopiuj plik zip do lokalizacji, do której

Szablony tworzenia szablonów umożliwiają uwzględnianie szablonów w większych rozszerzeniach. Dołączenie szablonów w rozszerzeniach umożliwia zaimplementowanie kontroli wersji na plikach źródłowych i utworzenie grupy projektów szablonów w jednym pakiecie VSIX.

W przypadku scenariuszy tworzenia szablonu podstawowego należy użyć kreatora **eksportu szablonów** , który wyprowadza dane wyjściowe do skompresowanego pliku. Aby uzyskać więcej informacji na temat tworzenia szablonu podstawowego, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu niestandardowych szablonów projektów i elementów nie jest już wykonywane. Zamiast tego rozszerzenie musi dostarczyć pliki manifestu szablonu opisujące lokalizację instalacji tych szablonów. Aby zaktualizować rozszerzenia VSIX, można użyć instalacji w wersji zapoznawczej 2. W przypadku wdrożenia rozszerzenia przy użyciu pliku MSI musisz ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie szablony projektów i elementów dla programu Visual Studio niestandardowego 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Utwórz szablon projektu

1. Utwórz projekt szablonu projektu. Szablon projektu można znaleźć w oknie dialogowym **Nowy projekt** , w folderze **rozszerzenia** Visual Basic lub Visual C#.

     Szablon generuje plik klasy, ikonę, plik. vstemplate, edytowalny plik projektu o nazwie ProjectTemplate. vbproj lub ProjectTemplate. csproj i niektóre pliki, które są zwykle generowane przez inne typy projektów, takie jak plik zasobów. resx, plik AssemblyInfo i plik. Settings. Każdy plik kodu zawiera wspólne podstawienia parametrów, tam gdzie jest to konieczne.

2. Dodaj i Usuń elementy z projektu zgodnie z wymaganiami projektu. Nie usuwaj edytowalnego pliku projektu, pliku AssemblyInfo ani pliku. vstemplate.

3. Zaktualizuj plik. vstemplate, aby odzwierciedlał wszelkie dodatki i usunięcia. Element [projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) dla każdego pliku, który ma zostać uwzględniony w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość dodaną do użytkownika i Dodaj odpowiednie podstawiania parametrów.

5. W razie potrzeby zmodyfikuj wygenerowaną zawartość.

6. Skompiluj projekt.

     Program Visual Studio tworzy plik zip, który zawiera szablon. Nie jest ona wdrożona i nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="create-an-item-template"></a>Utwórz szablon elementu

1. Utwórz projekt szablonu elementu.

     Szablon generuje plik klasy, ikonę, plik. vstemplate i plik AssemblyInfo. Plik klasy zawiera kilka typowych podstawiania parametrów.

2. Dodaj i Usuń elementy z projektu zgodnie z wymaganiami projektu.

3. Zaktualizuj plik. vstemplate, aby odzwierciedlał wszelkie dodatki i usunięcia. Element [projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) dla każdego pliku, który ma zostać uwzględniony w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość dodaną do użytkownika i Dodaj odpowiednie podstawiania parametrów.

5. W razie potrzeby zmodyfikuj wygenerowaną zawartość.

6. Skompiluj projekt.

     Program Visual Studio tworzy skompresowany plik, który zawiera szablon. Nie jest ona wdrożona i nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="deploy-the-project-or-item-template"></a>Wdróż szablon projektu lub elementu

1. Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

2. Ustaw projekt VSIX jako projekt startowy. W **Eksplorator rozwiązań**wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

3. Ustaw projekt szablonu projektu jako element zawartości projektu VSIX. Otwórz plik. vsixmanifest. Przejdź do karty **składniki** i kliknij pozycję **Nowy**.

    1. Ustaw wartość pola **Typ** na **Microsoft. VisualStudio. ProjectTemplate** lub **Microsoft. VisualStudio. ItemTemplate**.

    2. W obszarze Źródło wybierz opcję **projekt w bieżącym rozwiązaniu** , a następnie wybierz projekt, który zawiera szablon.

4. Skompiluj rozwiązanie i naciśnij klawisz F5. Zostanie wyświetlone wystąpienie eksperymentalne.

5. W przypadku projektu szablonu projektu powinien zostać wyświetlony szablon projektu w oknie dialogowym **Nowy projekt** (**plik/nowy/projekt**) w węźle Visual C# lub Visual Basic. Dla projektu szablonu elementu powinien zostać wyświetlony szablon elementu na liście w oknie dialogowym Dodaj nowy element (w **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie kliknij przycisk **Dodaj/nowy element**).

## <a name="see-also"></a>Zobacz też

- [Informacje o szablonach programu Visual Studio](../ide/visual-studio-template-reference.md)