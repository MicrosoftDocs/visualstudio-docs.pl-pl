---
title: Tworzenie szablonów obejmujących wiele projektów
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6da7464f5e22e186edff7671744c2605bee3c9ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591089"
---
# <a name="how-to-create-multi-project-templates"></a>Jak: Tworzenie szablonów wielu projektów

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Podczas tworzenia projektu, który jest oparty na szablonie wielu projektów, każdy projekt w szablonie jest dodawany do rozwiązania.

Szablon wieloprojektowy ma co najmniej dwa szablony projektów i szablon główny typu **ProjectGroup**.

Szablony wielu projektów zachowują się inaczej niż szablony pojedynczego projektu. Mają one następujące unikalne cechy:

- Poszczególnych projektów w szablonie wielu projektów nie można przypisać nazw, gdy szablon jest używany do tworzenia nowego projektu. Zamiast tego użyj atrybutu **ProjectName** w **elemencie ProjectTemplateLink** w pliku *vstemplate,* aby określić nazwę dla każdego projektu.

- Szablony wielu projektów mogą zawierać projekty dla różnych języków, ale sam szablon można umieścić tylko w jednej kategorii. Określ kategorię szablonu w elemencie **ProjectType** pliku *vstemplate.*

Szablon wielu projektów musi zawierać następujące elementy skompresowane do pliku *zip:*

- Główny plik *vstemplate* dla całego szablonu wieloprojektowego. Ten główny plik *vstemplate* zawiera metadane wyświetlane w oknie dialogowym, w którym tworzysz nowy projekt. Określa również, gdzie można znaleźć pliki *vstemplate* dla projektów w szablonie. Ten plik musi znajdować się w katalogu głównym pliku *zip.*

- Dwa lub więcej folderów, które zawierają pliki, które są wymagane dla pełnego szablonu projektu. Foldery zawierają wszystkie pliki kodu dla projektu, a także plik *vstemplate* dla projektu.

Na przykład plik *zip* szablonu wielu projektów, który ma dwa projekty, może mieć następujące pliki i katalogi:

- *Płyta MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Główny plik *vstemplate* dla szablonu wielu projektów różni się od szablonu pojedynczego projektu w następujący sposób:

- Atrybut **Type** elementu **VSTemplate** ma wartość **ProjectGroup** zamiast **Project**. Przykład:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- **TemplateContent** Element zawiera **ProjectCollection** element, który ma jeden lub więcej **ProjectTemplateLink** elementów, które definiują ścieżki do plików *vstemplate* z dołączonych projektów. Przykład:

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

> [!TIP]
> Jeśli szablon wielu projektów ma być wyświetlany tylko w oknie dialogowym nowego projektu, a nie w poszczególnych projektach, które zawiera, oznacz szablony wewnętrzne jako [ukryte.](../extensibility/hidden-element-visual-studio-templates.md) Przykład:
>
> ```xml
> <VSTemplate Type="Project" ... >
>     <TemplateData>
>         ...
>         <Hidden>true</Hidden>
>     </TemplateData>
>     ...
> </VSTemplate>
> ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Tworzenie szablonu wieloprojektowego z istniejącego rozwiązania

1. Utwórz rozwiązanie i dodaj dwa lub więcej projektów.

2. Dostosuj projekty, dopóki nie będą gotowe do wyeksportowania do szablonu.

   > [!TIP]
   > Jeśli używasz [parametrów szablonu](template-parameters.md) i chcesz odwoływać się do zmiennych z szablonu nadrzędnego, przedrostek nazwę parametru z `ext_`. Na przykład `$ext_safeprojectname$`. Ponadto ustaw atrybut **CopyParameters** elementu **ProjectTemplateLink** na **true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. W menu **Projekt** wybierz polecenie **Eksportuj szablon**.

   Zostanie otwarty **Kreator szablonów eksportu.**

4. Na stronie **Wybierz typ szablonu** wybierz pozycję **Szablon projektu**. Wybierz jeden z projektów, które chcesz wyeksportować do szablonu, a następnie wybierz pozycję **Dalej**. (Powtórzysz te kroki dla każdego projektu w rozwiązaniu).

5. Na stronie **Wybierz opcje szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Wybierz **pozycję Zakończ**.

   Projekt jest eksportowany do pliku *zip* i umieszczany w określonej lokalizacji wyjściowej.

   > [!NOTE]
   > Każdy projekt musi być eksportowany do szablonu oddzielnie, więc powtórz poprzednie kroki dla każdego projektu w rozwiązaniu.

6. Utwórz katalog szablonu z podkatalogiem dla każdego projektu.

7. Wyodrębnij zawartość pliku *zip* każdego projektu do odpowiedniego podkatalogu, który został utworzony.

8. W katalogu podstawowym utwórz plik XML z rozszerzeniem pliku *vstemplate.* Ten plik zawiera metadane szablonu wieloprojektowego. Zobacz przykład, który następuje dla struktury pliku. Należy określić ścieżkę względną do pliku *vstemplate* każdego projektu.

9. Zaznacz wszystkie pliki w katalogu podstawowym, a następnie z menu kontekstowego lub kliknięcia prawym przyciskiem myszy wybierz polecenie **Wyślij do** > **folderu Skompresowanego (spakowanego).**

   Pliki i foldery są kompresowane do pliku *zip.*

10. Skopiuj plik *zip* do katalogu szablonów projektu użytkownika. Domyślnie ten katalog to *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

11. W programie Visual Studio wybierz pozycję **Plik** > **nowego** > **projektu** i sprawdź, czy szablon jest wyświetlany.

## <a name="two-project-example"></a>Przykład dwóch projektów

W tym przykładzie przedstawiono podstawowy plik *vstemplate* dla wielu projektów. W tym przykładzie szablon ma dwa projekty: **Moja aplikacja systemu Windows** i Moja **biblioteka klas**. **Atrybut ProjectName** w **elemencie ProjectTemplateLink** określa nazwę nadaną projektowi.

> [!TIP]
> Jeśli atrybut **ProjectName** nie jest określony, nazwa pliku *vstemplate* jest używana jako nazwa projektu.

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

## <a name="example-with-solution-folders"></a>Przykład z folderami rozwiązań

W tym przykładzie użyto **Elementu SolutionFolder** do dzielenia projektów na dwie grupy: **Klasy matematyczne** i **Klasy graficzne.** Szablon ma cztery projekty, z których dwa są umieszczane w każdym folderze rozwiązania.

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

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [Element Programu SolutionFolder (szablony programu Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Element ProjectTemplateLink (szablony programu Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
