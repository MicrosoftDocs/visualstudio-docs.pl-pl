---
title: Tworzenie szablonów obejmujących wiele projektów
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ef0dc772422322d8cfa2f8c7ca88a7cf30eab31
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416256"
---
# <a name="how-to-create-multi-project-templates"></a>Porady: Tworzenie szablonów obejmujących wiele projektów

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Podczas tworzenia projektu, który jest oparty na szablonie wieloprojektowym każdego projektu w szablonie zostanie dodany do rozwiązania.

Szablonu wieloprojektowego zawiera dwa lub więcej szablonów projektów i szablonu katalogu głównego, typu **ProjectGroup**.

Szablony wielu projektów będą działały inaczej niż szablony pojedynczego projektu. Mają one unikatowe następujące cechy:

- Nie można przypisać poszczególnych projektów w szablonie wieloprojektowym nazw, gdy szablon jest używany do tworzenia nowego projektu. Zamiast tego należy użyć **ProjectName** atrybutu na **ProjectTemplateLink** element *vstemplate* plik, aby określić nazwę dla każdego projektu.

- Szablony wielu projektów może zawierać projekty w różnych językach, ale cały samego szablonu można umieścić tylko w jednej kategorii. Określ kategorie szablonów w **ProjectType** elementu *vstemplate* pliku.

Szablonu wieloprojektowego musi zawierać następujące elementy, skompresowane w *zip* pliku:

- Katalog główny *vstemplate* dla całego szablonu wieloprojektowego. Ten katalog główny *vstemplate* plik zawiera metadane, który jest wyświetlany w oknie dialogowym, w której utworzono nowy projekt. Ponadto określa, gdzie można znaleźć *vstemplate* plików dla projektów w szablonie. Ten plik musi znajdować się w katalogu głównym *zip* pliku.

- Dwa lub więcej folderów zawierających pliki, które są wymagane przez szablon kompletnego projektu. Foldery Dołącz wszystkie pliki kodu dla projektu, a także *vstemplate* plik projektu.

Na przykład szablonu wieloprojektowego *zip* plik, który ma dwa projekty mają następujące pliki i katalogi:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.VB*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.VB*

Katalog główny *vstemplate* plik szablonu wieloprojektowego różni się od szablonu jednego projektu w następujący sposób:

- **Typu** atrybutu **VSTemplate** element ma wartość **ProjectGroup** zamiast **projektu**. Na przykład:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** element zawiera **ProjectCollection** element, który ma co najmniej jeden **ProjectTemplateLink** elementy, które definiują ścieżki do *vstemplate* pliki dołączone projektów. Na przykład:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Tworzenie szablonów wielu projektów z istniejącego rozwiązania

1. Tworzenie rozwiązania i dodaj dwa lub więcej projektów.

2. Dostosowywanie projektów, aż będą gotowe do wyeksportowania do szablonu.

   > [!TIP]
   > Jeśli używasz [parametry szablonu](template-parameters.md) i chcesz odwoływać się do zmiennych z szablonu nadrzędnego, poprzedź nazwę parametru za pomocą `ext_`. Na przykład `$ext_safeprojectname$`.

3. Na **projektu** menu, wybierz **Eksportuj szablon**.

   **Kreatora eksportowania szablonu** zostanie otwarty.

4. Na **wybierz typ szablonu** wybierz opcję **szablonu projektu**. Wybierz jeden z projektów, które chcesz wyeksportować do szablonu, a następnie wybierz **dalej**. (Należy powtórzyć te kroki dla każdego projektu w rozwiązaniu.)

5. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikona i obrazu podglądu dla szablonu. Wybierz **Zakończ**.

   Projekt jest eksportowana do *zip* pliku i umieszczane w lokalizacji określonym produktem wyjściowym.

   > [!NOTE]
   > Każdy projekt musi być wyeksportowany do szablonu oddzielnie, dlatego Powtórz te czynności dla każdego projektu w rozwiązaniu.

6. Utwórz katalog dla szablonu, w podkatalogu dla każdego projektu.

7. Wyodrębnij zawartość każdego projektu *zip* pliku do odpowiedniego podkatalogu, który został utworzony.

8. W katalogu podstawowym, Utwórz plik XML z *.vstemplate* rozszerzenie pliku. Ten plik zawiera metadane szablonu wieloprojektowego. Zobacz przykład znajdujący się w strukturze pliku. Pamiętaj określić ścieżkę względną do każdego projektu *vstemplate* pliku.

9. Zaznacz wszystkie pliki w katalogu podstawowym i w menu kliknij prawym przyciskiem myszy lub kontekstu, wybierz polecenie **wysyłać** > **skompresowany folder (zip)**.

   Pliki i foldery, które są kompresowane do *zip* pliku.

10. Kopiuj *zip* plik do katalogu szablonu projektu użytkownika. Domyślnie ten katalog jest *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*.

11. W programie Visual Studio, wybierz **pliku** > **New** > **projektu** i sprawdź, czy szablon jest wyświetlany.

## <a name="two-project-example"></a>Przykład dwóch projektu

W tym przykładzie przedstawiono podstawowe główny wielu projektów *vstemplate* pliku. W tym przykładzie szablon zawiera dwa projekty **My Windows Application** i **My Class Library**. **ProjectName** atrybutu na **ProjectTemplateLink** element Określa nazwę, który znajduje się w projekcie.

> [!TIP]
> Jeśli **ProjectName** atrybut nie jest określony, nazwa *vstemplate* plik jest używany jako nazwa projektu.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Przykład: folderów rozwiązania

W tym przykładzie użyto **SolutionFolder** elementu, aby podzielić projekty na dwie grupy **klasy matematyczne** i **klas grafiki**. Szablon zawiera cztery projektów, dwie z nich są umieszczane w każdym folderze rozwiązania.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [Solutionfolder — element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Projecttemplatelink — element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)