---
title: Tworzenie szablonów obejmujących wiele projektów
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b71af98c7d72e0b3a510f3968f3d0770cd5401df
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284415"
---
# <a name="how-to-create-multi-project-templates"></a>Instrukcje: Tworzenie szablonów wieloprojektowych

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Podczas tworzenia projektu, który jest oparty na szablonie wieloprojektowym, każdy projekt w szablonie jest dodawany do rozwiązania.

Szablon z wieloma projektami ma dwa lub więcej szablonów projektu i szablon główny typu **Project**.

Szablony wielu projektów działają inaczej niż w przypadku pojedynczych szablonów projektu. Mają one następujące unikalne cechy:

- W przypadku tworzenia nowego projektu w szablonie wieloprojektowym nie można przypisać nazw poszczególnych projektów. Zamiast tego należy użyć atrybutu **ProjectName** w elemencie **ProjectTemplateLink** w pliku *vstemplate* , aby określić nazwę dla każdego projektu.

- Szablony wielu projektów mogą zawierać projekty dla różnych języków, ale cały szablon można umieścić tylko w jednej kategorii. Określ kategorię szablonu w elemencie **ProjectType** pliku *vstemplate* .

Szablon wieloprojektowy musi zawierać następujące elementy, które zostały skompresowane do pliku *zip* :

- Główny plik *vstemplate* dla całego szablonu wieloprojektowego. Ten główny plik *vstemplate* zawiera metadane, które są wyświetlane w oknie dialogowym, w którym można utworzyć nowy projekt. Określa również, gdzie znaleźć pliki *vstemplate* dla projektów w szablonie. Ten plik musi znajdować się w katalogu głównym pliku *zip* .

- Co najmniej dwa foldery zawierające pliki, które są wymagane do pełnego szablonu projektu. Foldery obejmują wszystkie pliki kodu dla projektu, a także plik *vstemplate* dla projektu.

Na przykład plik template *. zip* szablonu z dwoma projektami może mieć następujące pliki i katalogi:

- *MultiProjectTemplate. vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Główny plik *vstemplate* dla szablonu wieloprojektowego różni się od szablonu pojedynczego projektu w następujący sposób:

- Atrybut **Type** elementu **vstemplate** ma wartość **projectmanager** zamiast **Project**. Przykład:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- Element **TemplateContent** zawiera element **ProjectCollection** , który ma jeden lub więcej elementów **ProjectTemplateLink** , które definiują ścieżki do plików *vstemplate* dołączonych projektów. Przykład:

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
> Jeśli chcesz, aby szablon wieloprojektowy był wyświetlany w oknie dialogowym Nowy projekt, a nie w poszczególnych projektach, Oznacz szablony wewnętrzne jako [ukryte](../extensibility/hidden-element-visual-studio-templates.md). Przykład:
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

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>Tworzenie szablonu wieloprojektowego na podstawie istniejącego rozwiązania

1. Utwórz rozwiązanie i Dodaj dwa lub więcej projektów.

2. Dostosuj projekty do momentu, aż będą gotowe do eksportowania do szablonu.

   > [!TIP]
   > Jeśli używasz [parametrów szablonu](template-parameters.md) i chcesz odwołać się do zmiennych z szablonu nadrzędnego, poprzedź nazwę parametru parametrem `ext_` . Na przykład `$ext_safeprojectname$`. Ponadto ustaw atrybut **CopyParameters** elementu **ProjectTemplateLink** na **true**.
   >
   > ```xml
   > <ProjectTemplateLink ProjectName="MyProject" CopyParameters="true">...</ProjectTemplateLink>
   > ```

3. W menu **projekt** wybierz polecenie **Eksportuj szablon**.

   Zostanie otwarty **Kreator eksportu szablonu** .

4. Na stronie **Wybieranie typu szablonu** wybierz **szablon projektu**. Wybierz jeden z projektów, które chcesz wyeksportować do szablonu, a następnie wybierz przycisk **dalej**. (Powtórz te kroki dla każdego projektu w rozwiązaniu).

5. Na stronie **Wybieranie opcji szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Wybierz pozycję **Zakończ**.

   Projekt zostanie wyeksportowany do pliku *zip* i umieszczony w określonej lokalizacji wyjściowej.

   > [!NOTE]
   > Każdy projekt musi zostać wyeksportowany do szablonu oddzielnie, dlatego Powtórz powyższe kroki dla każdego projektu w rozwiązaniu.

6. Utwórz katalog dla szablonu za pomocą podkatalogu dla każdego projektu.

7. Wyodrębnij zawartość pliku *zip* każdego projektu do odpowiedniego podkatalogu, który został utworzony.

8. W katalogu podstawowym Utwórz plik XML z rozszerzeniem *vstemplate* . Ten plik zawiera metadane dla szablonu wieloprojektowego. Zobacz następujący przykład dotyczący struktury pliku. Pamiętaj, aby określić ścieżkę względną do pliku *vstemplate* każdego projektu.

9. Zaznacz wszystkie pliki w katalogu podstawowym, a następnie w menu kontekstowym lub prawym przyciskiem myszy wybierz opcję **Wyślij do**  >  **folderu skompresowanego (spakowanego)**.

   Pliki i foldery są kompresowane do pliku *zip* .

10. Skopiuj plik *zip* do katalogu szablonów projektu użytkownika. Domyślnie ten katalog to *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*.

11. W programie Visual Studio wybierz kolejno pozycje **plik**  >  **Nowy**  >  **projekt** i sprawdź, czy szablon jest wyświetlany.

## <a name="two-project-example"></a>Przykład dwuprojektowy

W tym przykładzie przedstawiono podstawowy plik *vstemplate* z wielojęzycznym projektem. W tym przykładzie szablon ma dwa projekty, **moją aplikację systemu Windows** i **moją bibliotekę klas**. Atrybut **ProjectName** w elemencie **ProjectTemplateLink** określa nazwę nadaną dla projektu.

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

W tym przykładzie używa elementu **SolutionFolder** , aby podzielić projekty na dwie grupy, **klasy matematyczne** i **klasy graficzne**. Szablon zawiera cztery projekty, z których dwa są umieszczane w każdym folderze rozwiązania.

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
- [Instrukcje: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
- [SolutionFolder, element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [ProjectTemplateLink, element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
