---
title: Tworzenie szablonów internetowych
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 245b20dd9cad465129d6c79c38e53b6379c2c09c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591011"
---
# <a name="how-to-manually-create-web-templates"></a>Jak: Ręczne tworzenie szablonów stron internetowych

Tworzenie szablonu sieci Web różni się od tworzenia innych rodzajów szablonów. Ponieważ szablony projektów sieci Web są wyświetlane w oknie dialogowym **Dodawanie nowej witryny sieci Web,** a elementy projektu sieci Web są podzielone według języka programowania, plik *vstemplate* musi określać szablon jako szablon sieci Web i identyfikować język programowania.

> [!NOTE]
> Szablony sieci Web muszą zawierać pusty plik *.webproj* i musi się odwoływać `File` w pliku `Project` *vstemplate* w atrybucie elementu. Mimo że projekty sieci Web nie wymagają pliku projektu *proj,* konieczne jest utworzenie tego pliku skrótowego, aby szablon sieci web działał poprawnie.

## <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web

1. Tworzenie projektu sieci Web.

2. Modyfikowanie lub usuwanie plików w projekcie lub dodawanie nowych plików do projektu.

3. Utwórz plik XML i zapisz go z rozszerzeniem nazwy pliku *vstemplate* w tym samym katalogu co projekt. Nie należy dodawać go do projektu w programie Visual Studio.

4. Edytuj plik XML *vstemplate,* aby zapewnić metadane szablonu projektu. Aby uzyskać więcej informacji, zobacz [poniższy przykład](#example).

5. Zlokalizuj `ProjectType` element w pliku *vstemplate* `Web`i ustaw wartość tekstową na .

6. Po `ProjectType` elemencie `ProjectSubType` dodaj element i ustaw wartość tekstową do języka programowania szablonu. Język programowania może być jedną z następujących wartości:

   - Csharp
   - Visualbasic

     Przykład:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Zaznacz pliki w szablonie (obejmuje to plik *vstemplate),* kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wyślij do** > **skompresowanego (spakowane) folderu**. Pliki są kompresowane do pliku *zip.*

8. Umieść plik szablonu *zip* w katalogu szablonów projektu programu Visual Studio. Domyślnie ten katalog to *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono podstawowy plik *vstemplate* dla szablonu projektu sieci web:

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

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)
