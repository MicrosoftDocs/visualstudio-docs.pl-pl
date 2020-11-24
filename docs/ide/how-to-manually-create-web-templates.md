---
title: Tworzenie szablonów internetowych
description: Dowiedz się, jak ręcznie utworzyć szablon sieci Web i zidentyfikować język programowania, którego używa szablon.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 8546b1364248b5c419a32e8f8ed40abf0b69fb5a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597083"
---
# <a name="how-to-manually-create-web-templates"></a>Instrukcje: ręczne tworzenie szablonów sieci Web

Tworzenie szablonu sieci Web różni się od tworzenia innych rodzajów szablonów. Ponieważ szablony projektu sieci Web pojawiają się w oknie dialogowym **Dodaj nową witrynę sieci Web** , a elementy projektu sieci Web są klasyfikowane według języka programowania, plik *vstemplate* musi określać szablon jako szablon sieci Web i identyfikować język programowania.

> [!NOTE]
> Szablony sieci Web muszą zawierać pusty plik *. webproj* i musi być przywoływany w pliku *vstemplate* w `File` atrybucie `Project` elementu. Chociaż projekty sieci Web nie wymagają pliku projektu *. proj* , należy utworzyć ten plik szczątkowy, aby szablon sieci Web działał poprawnie.

## <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web

1. Utwórz projekt sieci Web.

2. Zmodyfikuj lub Usuń pliki w projekcie lub Dodaj nowe pliki do projektu.

3. Utwórz plik XML i Zapisz go z rozszerzeniem nazwy pliku *vstemplate* w tym samym katalogu, w którym znajduje się projekt. Nie należy dodawać go do projektu w programie Visual Studio.

4. Edytuj plik XML *vstemplate* , aby dostarczyć metadane szablonu projektu. Aby uzyskać więcej informacji, zobacz [Poniższy przykład](#example).

5. Znajdź `ProjectType` element w pliku *vstemplate* i ustaw wartość tekstową na `Web` .

6. Po `ProjectType` elemencie Dodaj `ProjectSubType` element i ustaw wartość tekstową na język programowania szablonu. Język programowania może być jedną z następujących wartości:

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

7. Wybierz pliki w szablonie (dotyczy to pliku *vstemplate* ), kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wyślij do**  >  **folderu skompresowanego (zip)**. Pliki są kompresowane do pliku *zip* .

8. Umieść plik *zip* Template w katalogu szablonów projektu programu Visual Studio. Domyślnie ten katalog to *%USERPROFILE%\Documents\Visual Studio \<Version\> \ProjectTemplates*.

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
