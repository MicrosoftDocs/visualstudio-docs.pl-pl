---
title: Tworzenie szablonów internetowych
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d121d9b970d8012aaf177c0a232cd21f6fe85d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645826"
---
# <a name="how-to-manually-create-web-templates"></a>Instruktaż: Ręczne tworzenie szablonów sieci Web

Tworzenie szablonu sieci Web różni się od tworzenia innych rodzajów szablonów. Ponieważ szablony projektu sieci Web pojawiają się w oknie dialogowym **Dodaj nową witrynę sieci Web** , a elementy projektu sieci Web są klasyfikowane według języka programowania, plik *vstemplate* musi określać szablon jako szablon sieci Web i identyfikować język programowania.

> [!NOTE]
> Szablony sieci Web muszą zawierać pusty plik *. webproj* i musi być przywoływany w pliku *vstemplate* w atrybucie `File` elementu `Project`. Chociaż projekty sieci Web nie wymagają pliku projektu *. proj* , należy utworzyć ten plik szczątkowy, aby szablon sieci Web działał poprawnie.

## <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web

1. Utwórz projekt sieci Web.

2. Zmodyfikuj lub Usuń pliki w projekcie lub Dodaj nowe pliki do projektu.

3. Utwórz plik XML i Zapisz go z rozszerzeniem nazwy pliku *vstemplate* w tym samym katalogu, w którym znajduje się projekt. Nie należy dodawać go do projektu w programie Visual Studio.

4. Edytuj plik XML *vstemplate* , aby dostarczyć metadane szablonu projektu. Aby uzyskać więcej informacji, zobacz [Poniższy przykład](#example).

5. Znajdź `ProjectType` element w pliku *vstemplate* i ustaw wartość tekstową na `Web`.

6. Po elemencie `ProjectType` Dodaj element `ProjectSubType` i ustaw wartość tekstową na język programowania szablonu. Język programowania może być jedną z następujących wartości:

   - CSharp
   - VisualBasic

     Na przykład:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Wybierz pliki z szablonu (w tym plik *vstemplate* ), kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz polecenie **Wyślij do**  > **skompresowanego folderu (zip)** . Pliki są kompresowane do pliku *zip* .

8. Umieść plik *zip* Template w katalogu szablonów projektu programu Visual Studio. Domyślnie ten katalog to *%USERPROFILE%\Documents\Visual Studio \<Version \> \projecttemplates*.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia podstawowy plik *vstemplate* szablonu projektu sieci Web:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
