---
title: Tworzenie niestandardowych szablonów projektów i elementów | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fbe1a4decebd68b80e6cbe8728c5de84a44c641
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68377751"
---
# <a name="create-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i elementów

Zestaw Visual Studio SDK zawiera szablony projektów, które tworzą niestandardowy szablon projektu i szablon elementu niestandardowego. Te szablony obejmują kilka typowych podstawieniach parametrów i kompilacji jako pliki zip. Nie są automatycznie wdrażane, a nie są one dostępne w doświadczalnym wystąpieniu. Należy skopiować wygenerowany plik zip do katalogu szablonów użytkownika.

Szablony do tworzenia szablonu pozwalają obejmują szablony w rozszerzeniach większe. Dzięki temu można zaimplementować kontrolę wersji na plikach źródłowych i utworzyć grupę projektów szablonów w jednym pakiecie VSIX.

Możesz również skonfigurować szablon, aby zainstalować pakiety NuGet. Aby uzyskać więcej informacji, zobacz [pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

W przypadku scenariuszy tworzenia podstawowego szablonu należy używać **Eksportuj szablon** kreatora, której dane wyjściowe do skompresowanego pliku. Aby uzyskać więcej informacji na temat tworzenia szablonu podstawowego, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Począwszy od programu Visual Studio 2017, skanowanie w poszukiwaniu szablonów elementów i projektów niestandardowych zostanie już wykonane. Zamiast tego rozszerzenia, należy podać plik manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenia, musisz ręcznie wygenerować plik manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [dokumentacji schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Utwórz szablon projektu

1. Utwórz projekt szablonu projektu. Szablon projektu można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "szablon projektu" i wybierając wersję C# lub Visual Basic.

     Szablon generuje plik klasy, ikonę, plik *. vstemplate* , edytowalny plik projektu o nazwie *ProjectTemplate. vbproj* lub *ProjectTemplate. csproj*i niektóre pliki, które są zwykle generowane przez inne typy projektów, takie jak  *plik resources. resx* , plik *AssemblyInfo* i plik *. Settings* . Każdy plik kodu zawiera typowe podstawieniach parametrów, gdzie jest to odpowiednie.

![wybór projektu szablonu projektu](media/project-template-selection.png)


2. Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu. Nie usuwaj edytowalnego pliku projektu, pliku *AssemblyInfo* ani pliku *. vstemplate* .

3. Zaktualizuj plik *. vstemplate* , aby odzwierciedlał wszelkie dodatki i usunięcia. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.

4. Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.

5. Zmodyfikuj wygenerowane zawartość zgodnie z potrzebami.

6. Skompiluj projekt.

     Program Visual Studio tworzy plik *zip* , który zawiera szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="create-an-item-template"></a>Utwórz szablon elementu

1. Tworzenie szablonu elementu projektu.

     Szablon generuje plik klasy, ikonę, plik *. vstemplate* i plik *AssemblyInfo* . Plik klasy zawiera niektóre typowe podstawieniach parametrów.

2. Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu.

3. Zaktualizuj plik *. vstemplate* , aby odzwierciedlał wszelkie dodatki i usunięcia. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.

4. Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.

5. Zmodyfikuj zawartość jest generowana zgodnie z potrzebami.

6. Skompiluj projekt.

     Visual Studio tworzy skompresowany plik, który zawiera ten szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.

## <a name="deployment"></a>wdrażania

### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu

1. Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

2. Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.

3. Ustaw projekt szablonu projektu jako zasób usługi w projekcie VSIX. Otwórz plik *. vsixmanifest* . Przejdź do **zasoby** kartę, a następnie kliknij przycisk **New**.

    1. Ustaw **typu** pole **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.

    2. Dla źródła, wybierz **projekt w bieżącym rozwiązaniu** opcji, a następnie wybierz projekt, który zawiera ten szablon.

4. Skompiluj rozwiązanie i naciśnij klawisz **F5**. Zostanie wyświetlone wystąpienie eksperymentalne.

5. Dla projektu szablonu projektu powinien zostać wyświetlony szablon projektu w oknie dialogowym **Nowy projekt** (**plik** > **Nowy** > **projekt**) w węźle Wizualizacja C# lub Visual Basic. Dla projektu szablonu elementu powinien zostać wyświetlony szablon elementu na liście w oknie dialogowym **Dodaj nowy element** . Aby wyświetlić okno dialogowe **Dodawanie nowego elementu** , w **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie kliknij przycisk **Dodaj** > **nowy element**).

## <a name="see-also"></a>Zobacz także

- [Odwołanie do szablonu programu Visual Studio](../ide/creating-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
