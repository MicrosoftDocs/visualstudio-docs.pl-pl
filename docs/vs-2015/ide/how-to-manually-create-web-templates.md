---
title: 'Instrukcje: ręczne tworzenie szablonów sieci Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651804"
---
# <a name="how-to-manually-create-web-templates"></a>Porady: ręczne tworzenie szablonów sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzenie szablonu sieci Web różni się od tworzenia innych rodzajów szablonów. Ponieważ szablony projektu sieci Web pojawiają się w oknie dialogowym **Dodaj nową witrynę sieci Web** , a elementy projektu sieci Web są klasyfikowane według języka programowania, plik. vstemplate musi określać szablon jako szablon sieci Web i identyfikować język programowania.

> [!NOTE]
> Szablony sieci Web muszą zawierać pusty plik webproj, który jest określony przy użyciu `File` atrybutu `Project` elementu. Chociaż projekty sieci Web nie wymagają plików projektu, ten plik jest wymagany w celu poprawnego działania szablonu sieci Web.

### <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web

1. Utwórz projekt sieci Web.

2. Zmodyfikuj lub Usuń pliki w projekcie lub Dodaj nowe pliki do projektu.

3. Utwórz plik XML i Zapisz go przy użyciu rozszerzenia nazwy pliku. vstemplate w tym samym katalogu, w którym znajduje się projekt. Nie należy dodawać go do projektu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

4. Utwórz plik XML. vstemplate, aby dostarczyć metadane szablonu projektu. Aby uzyskać więcej informacji, zapoznaj się z przykładem w następnej sekcji.

5. Znajdź `ProjectType` element w pliku. vstemplate i ustaw wartość tekstową na `Web` .

6. Po `ProjectType` elemencie Dodaj `ProjectSubType` element i ustaw wartość tekstową na język programowania szablonu. Język programowania może być jedną z następujących wartości:

   - CSharp

   - VisualBasic

     Na przykład:

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. Wybierz pliki z szablonu (w tym plik. vstemplate), kliknij prawym przyciskiem myszy zaznaczenie, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)**. Pliki są kompresowane do pliku zip.

8. Umieść plik. zip szablonu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katalogu szablonów projektu. Domyślnie ten katalog to \Moje Documents\Visual Studio w *wersji*\Moje wyeksportowane szablony \\ .

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia podstawowy plik. vstemplate szablonu projektu sieci Web.

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md) — [odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
