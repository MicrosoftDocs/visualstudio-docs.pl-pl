---
title: Tworzenie szablonów internetowych
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9af528cf92d4909bbe5c7d4ac114aa830e96162c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938218"
---
# <a name="how-to-manually-create-web-templates"></a>Instrukcje: Ręczne tworzenie szablonów sieci web

Tworzenie szablonu sieci web jest inny niż tworzenie innych rodzajów szablonów. Ponieważ szablony projektów internetowych są wyświetlane w **Dodaj nową witrynę sieci Web** okno dialogowe, a projekt sieci web, które elementy są pogrupowane według języka programowania, *vstemplate* pliku należy określić szablon jako szablon sieci web i zidentyfikować języka programowania.

> [!NOTE]
> Szablony sieci Web mogą zawierać pustą *.webproj* pliku który musi odwoływać się do *vstemplate* w pliku `File` atrybutu `Project` elementu. Chociaż projekty sieci web nie wymagają *.proj* plik projektu jest niezbędne do utworzenia tego pliku klasy zastępczej dla szablonu sieci web, aby działać poprawnie.

## <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci web

1. Utwórz projekt sieci web.

2. Modyfikować lub usuwać pliki w projekcie lub dodać nowe pliki do projektu.

3. Utwórz plik XML i zapisz go z *vstemplate* plikiem, w tym samym katalogu co projekt. Nie należy dodawać go do projektu w programie Visual Studio.

4. Edytuj *vstemplate* plik XML do udostępnienia metadanych szablonu projektu. Aby uzyskać więcej informacji, zobacz [poniższym przykładzie](#example).

5. Znajdź `ProjectType` element *vstemplate* pliku i ustaw wartość tekstową na `Web`.

6. Następujące `ProjectType` elementu Dodawanie `ProjectSubType` element i ustaw wartość tekstowa do język programowania szablonu. Język programowania może być jednym z następujących wartości:

   - CSharp
   - Języka Visual Basic

     Na przykład:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Wybierz pliki do szablonu (w tym *vstemplate* pliku), kliknij prawym przyciskiem myszy zaznaczenie, a wybierz **wysyłać** > **skompresowany folder (zip)**. Pliki są kompresowane do *zip* pliku.

8. Umieść *zip* pliku szablonu w katalogu szablonu projektu programu Visual Studio. Domyślnie ten katalog jest *%USERPROFILE%\Documents\Visual Studio \<wersji\>\ProjectTemplates*.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia podstawowe *vstemplate* w pliku szablonu projektu sieci web:

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
- [Visual Studio odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
