---
title: Tworzenie szablonów elementów i projektów niestandardowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeb08af2edeea8650303b8e954bc7d3b42ef2641
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012251"
---
# <a name="create-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i elementów

Visual Studio SDK zawiera szablony projektów, które Tworzenie szablonu niestandardowego projektu i szablonu niestandardowego elementu. Te szablony obejmują kilka typowych podstawieniach parametrów i kompilacji jako pliki zip. Nie są automatycznie wdrażane, a nie są one dostępne w doświadczalnym wystąpieniu. Plik zip wygenerowanego należy skopiować do katalogu szablonu użytkownika.

Szablony do tworzenia szablonu pozwalają obejmują szablony w rozszerzeniach większe. Pozwala to na implementowanie kontroli wersji na pliki źródłowe i utworzyć grupę z projektów szablonu w jednym pakiecie VSIX.

Można również skonfigurować szablon, aby zainstalować pakiety NuGet. Aby uzyskać więcej informacji, zobacz [pakietów NuGet w programie Visual Studio szablonach](/nuget/visual-studio-extensibility/visual-studio-templates).

W przypadku scenariuszy tworzenia podstawowego szablonu należy używać **Eksportuj szablon** kreatora, której dane wyjściowe do skompresowanego pliku. Aby uzyskać więcej informacji na temat tworzenia podstawowego szablonu zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu szablonów elementów i projektów niestandardowych zostanie już wykonane. Zamiast tego rozszerzenia, należy podać plik manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenia, musisz ręcznie wygenerować plik manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schematu manifestu szablonu jest udokumentowany w [odwołanie do schematu manifestu szablonu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Tworzenie szablonu projektu

1.  Utwórz projekt szablonu projektu. Można znaleźć szablonu projektu w **nowy projekt** okna dialogowego, w języku Visual Basic lub Visual C# *rozszerzalności* folderu.

     Szablon generuje plik klasy ikony, *.vstemplate* pliku, plik można edytować projekt o nazwie *ProjectTemplate.vbproj* lub *ProjectTemplate.csproj*ale niektóre pliki, które zazwyczaj są generowane przez inne typy projektów takich *resources.resx* pliku *AssemblyInfo* pliku i *.settings* pliku. Każdy plik kodu zawiera typowe podstawieniach parametrów, gdzie jest to odpowiednie.

2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu. Nie usuwaj pliku projektu można edytować *AssemblyInfo* pliku, lub *.vstemplate* pliku.

3.  Aktualizacja *.vstemplate* pliku w celu uwzględnienia wszelkich dodanych i usuniętych. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.

4.  Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.

5.  Zmodyfikuj wygenerowane zawartość zgodnie z potrzebami.

6.  Skompiluj projekt.

     Program Visual Studio tworzy *zip* pliku, który zawiera ten szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="create-an-item-template"></a>Utworzyć szablon elementu

1.  Tworzenie szablonu elementu projektu.

     Szablon generuje plik klasy ikonę *.vstemplate* pliku, a *AssemblyInfo* pliku. Plik klasy zawiera niektóre typowe podstawieniach parametrów.

2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu.

3.  Aktualizacja *.vstemplate* pliku w celu uwzględnienia wszelkich dodanych i usuniętych. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.

4.  Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.

5.  Zmodyfikuj zawartość jest generowana zgodnie z potrzebami.

6.  Skompiluj projekt.

     Visual Studio tworzy skompresowany plik, który zawiera ten szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="deployment"></a>wdrażania

### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu

1.  Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

2.  Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.

3.  Ustaw projekt szablonu projektu jako zasób usługi w projekcie VSIX. Otwórz *.vsixmanifest* pliku. Przejdź do **zasoby** kartę, a następnie kliknij przycisk **New**.

    1.  Ustaw **typu** pole **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.

    2.  Dla źródła, wybierz **projekt w bieżącym rozwiązaniu** opcji, a następnie wybierz projekt, który zawiera ten szablon.

4.  Kompilacja rozwiązania, a następnie naciśnij klawisz **F5**. Zostanie wyświetlone wystąpienie eksperymentalne.

5.  Dla projektu szablonu projektu, powinien zostać wyświetlony na liście szablonu projektu **nowy projekt** okna dialogowego (**pliku** > **New**  >  **Projektu**), a w Visual C# lub Visual Basic węzła. Dla szablonu elementu projektu, powinien zostać wyświetlony szablon elementu na liście **Dodaj nowy element** okna dialogowego. Aby wyświetlić **Dodaj nowy element** okno dialogowe, z **Eksploratora rozwiązań**, wybierz węzeł projektu i kliknij **Dodaj** > **nowy element**).

## <a name="see-also"></a>Zobacz także

[Odwołanie do szablonu Visual Studio](../ide/creating-project-and-item-templates.md)
[pakietów NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
