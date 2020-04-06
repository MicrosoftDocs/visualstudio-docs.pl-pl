---
title: Tworzenie niestandardowych szablonów projektów i elementów | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739451"
---
# <a name="create-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i elementów

Zestaw SDK programu Visual Studio zawiera szablony projektów, które tworzą niestandardowy szablon projektu i niestandardowy szablon elementu. Szablony te zawierają niektóre typowe podstawienia parametrów i kompilacji jako pliki zip. Nie są one automatycznie wdrażane i nie są dostępne w wystąpieniu eksperymentalnym. Wygenerowany plik zip należy skopiować do katalogu szablonu użytkownika.

Szablony tworzenia szablonów umożliwiają dołączanie szablonów w większych rozszerzeniach. Dzięki temu można zaimplementować kontrolę wersji na plikach źródłowych i utworzyć grupę projektów szablonów w jeden pakiet VSIX.

Można również skonfigurować szablon do instalowania pakietów NuGet. Aby uzyskać więcej informacji, zobacz [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

W przypadku scenariuszy tworzenia szablonów podstawowych należy użyć **Kreatora eksportu szablonu,** który wyprowadza skompresowany plik. Aby uzyskać więcej informacji na temat tworzenia szablonów podstawowych, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Począwszy od programu Visual Studio 2017 skanowanie w poszukiwaniu szablonów niestandardowych projektów i elementów nie będzie już wykonywane. Zamiast tego rozszerzenie musi zawierać pliki manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. Jeśli rozmieszczenia rozszerzenia przy użyciu MSI, należy wygenerować pliki manifestu szablonu ręcznie. Aby uzyskać więcej informacji, zobacz [Uaktualnianie szablonów niestandardowych projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [odwołaniu do schematu manifestu szablonu programu Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Tworzenie szablonu projektu

1. Tworzenie projektu szablonu projektu. Szablon projektu można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "szablon projektu" i wybierając wersję języka C# lub Visual Basic.

     Szablon generuje plik klasy, ikonę, plik *vstemplate,* edytowalny plik projektu o nazwie *ProjectTemplate.vbproj* lub *ProjectTemplate.csproj*oraz niektóre pliki, które są zwykle generowane przez inne typy projektów, taki plik *resources.resx,* plik *AssemblyInfo* i plik *.settings.* Każdy plik kodu zawiera typowe podstawienia parametrów, w stosownych przypadkach.

![wybór projektu szablonu projektu](media/project-template-selection.png)

2. Dodawanie i usuwanie elementów z projektu zgodnie z wymaganiami dla projektu. Nie należy usuwać edytowalny plik projektu, plik *AssemblyInfo* lub pliku *vstemplate.*

3. Zaktualizuj plik *vstemplate,* aby odzwierciedlić wszelkie dodatki i usunięcia. [Project](../extensibility/project-element-visual-studio-templates.md) Element musi zawierać [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) element dla każdego pliku, które mają być zawarte w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość skierowaną do użytkownika i dodaj odpowiednie podstawienia parametrów.

5. W razie potrzeby zmodyfikuj wygenerowaną zawartość.

6. Skompiluj projekt.

     Program Visual Studio tworzy plik *zip* zawierający szablon. Nie jest wdrożony i nie jest dostępny w wystąpieniu eksperymentalnym.

## <a name="create-an-item-template"></a>Tworzenie szablonu elementu

1. Utwórz projekt szablonu elementu.

     Szablon generuje plik klasy, ikonę, plik *vstemplate* i plik *AssemblyInfo.* Plik klasy zawiera typowe podstawienia parametrów.

2. Dodawanie i usuwanie elementów z projektu zgodnie z wymaganiami dla projektu.

3. Zaktualizuj plik *vstemplate,* aby odzwierciedlić wszelkie dodatki i usunięcia. [Project](../extensibility/project-element-visual-studio-templates.md) Element musi zawierać [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) element dla każdego pliku, które mają być zawarte w szablonie.

4. Zmodyfikuj pliki kodu i inną zawartość skierowaną do użytkownika i dodaj odpowiednie podstawienia parametrów.

5. Modyfikuj wygenerowaną zawartość zgodnie z wymaganiami.

6. Skompiluj projekt.

     Program Visual Studio tworzy skompresowany plik zawierający szablon. Nie jest wdrożony i nie jest dostępny w wystąpieniu eksperymentalnym.

## <a name="deployment"></a>Wdrożenie

### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu

1. Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

2. Ustaw projekt VSIX jako projekt startowy. W **Eksploratorze rozwiązań**wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw jako projekt uruchamiania**.

3. Ustaw projekt szablonu projektu jako zasób projektu VSIX. Otwórz plik *vsixmanifest.* Przejdź do karty **Zasoby** i kliknij pozycję **Nowy**.

    1. Ustaw pole **Typ** na **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.

    2. Dla źródła wybierz opcję **A projekt w bieżącym rozwiązaniu,** a następnie wybierz projekt zawierający szablon.

4. Zbuduj rozwiązanie i naciśnij **klawisz F5**. Pojawi się eksperymentalne wystąpienie.

5. W przypadku projektu szablonu projektu powinien zostać wyświetlony szablon projektu wymieniony w oknie dialogowym **Nowy projekt** **(Plik** > **nowego** > **projektu)** w węźle Visual C# lub Visual Basic. W przypadku projektu szablonu elementu powinien zostać wyświetlony szablon elementu wymieniony w oknie dialogowym **Dodawanie nowego elementu.** Aby wyświetlić okno dialogowe **Dodawanie nowego elementu,** w **Eksploratorze rozwiązań**wybierz węzeł projektu i kliknij pozycję **Dodaj** > **nowy element**).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do szablonu programu Visual Studio](../ide/creating-project-and-item-templates.md)
- [Pakiety NuGet w szablonach programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
