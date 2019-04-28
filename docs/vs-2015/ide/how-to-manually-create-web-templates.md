---
title: 'Instrukcje: Ręczne tworzenie szablonów sieci Web | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8a505fe3428a8e16c321eee4764f8a62fff65511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431106"
---
# <a name="how-to-manually-create-web-templates"></a>Instrukcje: Ręczne tworzenie szablonów sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzenie szablonu sieci Web jest inny niż tworzenie innych rodzajów szablonów. Ponieważ szablony projektów internetowych są wyświetlane w **Dodaj nową witrynę sieci Web** okno dialogowe, a elementy projektu sieci Web są pogrupowane według języka programowania, w pliku .vstemplate, należy określić szablon jako szablon sieci Web i zidentyfikować programowanie język.  
  
> [!NOTE]
> Szablony sieci Web musi zawierać plik .webproj pusty, który jest określony za pomocą `File` atrybutu `Project` elementu. Chociaż projekty sieci Web nie jest wymagane pliki projektu, ten plik jest wymagany, aby możliwe było poprawnie szablonu sieci Web.  
  
### <a name="to-manually-create-a-web-template"></a>Aby ręcznie utworzyć szablon sieci Web  
  
1. Utwórz projekt sieci Web.  
  
2. Modyfikować lub usuwać pliki w projekcie lub dodać nowe pliki do projektu.  
  
3. Utwórz plik XML i zapisz go przy użyciu rozszerzenia nazwy pliku .vstemplate, w tym samym katalogu co projekt. Nie należy dodawać go do projektu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Tworzenie pliku XML .vstemplate do udostępnienia metadanych szablonu projektu. Aby uzyskać więcej informacji zobacz przykład w poniższej sekcji.  
  
5. Znajdź `ProjectType` element w pliku .vstemplate i ustaw wartość tekstu `Web`.  
  
6. Następujące `ProjectType` elementu Dodawanie `ProjectSubType` element i ustaw wartość tekstowa do język programowania szablonu. Język programowania może być jednym z następujących wartości:  
  
   - CSharp  
  
   - Języka Visual Basic  
  
     Na przykład:  
  
   ```  
   <TemplateData>  
       ...  
       <ProjectType>Web</ProjectType>  
       <ProjectSubType>CSharp</ProjectSubType>  
       ...  
   </TemplateData>  
   ```  
  
7. Wybierz pliki do szablonu (w tym pliku .vstemplate), kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki są kompresowane w pliku zip.  
  
8. Umieść plik zip szablonu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katalogu szablonu projektu. Domyślnie ten katalog jest \My Studio *wersji*\My wyeksportowane szablony\\.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje plik .vstemplate podstawowe dla szablonu projektu sieci Web.  
  
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
