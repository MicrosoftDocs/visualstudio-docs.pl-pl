---
title: 'Instrukcje: Tworzenie szablonów elementów wielu plików | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6c6dde1880881bfb236909fde6ce6deb6bf596f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201843"
---
# <a name="how-to-create-multi-file-item-templates"></a>Instrukcje: Tworzenie szablonów elementów obejmujących wiele plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony elementów może określić tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu formularzy Windows w języku Visual Basic wymaga następujących trzech plików:  
  
- Plik .vb, który zawiera kod dla formularza.  
  
- Odp. plik designer.vb, który zawiera informacje o projektancie formularza.  
  
- Plik Resx zawierający zasoby osadzone w formularzu.  
  
  Szablony elementów wielu plików wymagają parametry w celu zapewnienia rozszerzeń nazw plików poprawne są używane, gdy element zostanie utworzony w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jeśli utworzysz szablon elementu za pomocą **Eksportuj szablon** kreatora, parametry te są generowane automatycznie i nie dalszej edycji jest wymagany. Poniższe kroki wyjaśniają jak używać parametrów aby upewnić się, że rozszerzeń nazw plików poprawne są tworzone.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonów elementów wielu plików  
  
1. Utwórz szablon elementu, jak należy utworzyć szablon elementu pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md).  
  
2. Dodaj `TargetFileName` atrybuty do każdego `ProjectItem` elementu. Ustaw wartości `TargetFileName` atrybuty $fileinputname $. *FileExtension*, gdzie *FileExtension* jest rozszerzeniem nazwy pliku w pliku, który jest uwzględniane w szablonie. Na przykład:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Gdy element pochodzące z tego szablonu zostanie dodany do projektu, nazwy plików będzie zależeć od nazwy, wpisany przez użytkownika w **Dodaj nowy element** okno dialogowe.  
  
3. Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)** . Wybrane pliki są kompresowane w pliku zip.  
  
4. Umieść plik zip w lokalizacji szablonów elementów użytkownika. Domyślnie katalog jest \My Studio *wersji*\Templates\ItemTemplates\\. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu Windows Forms. Gdy element zostanie utworzony na podstawie tego szablonu, nazwy trzy utworzone pliki będą zgodne nazwy wprowadzone w **Dodaj nowy element** okno dialogowe.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Instrukcje: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)
