---
title: 'Instrukcje: Tworzenie szablonów wielu projektów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1059e4035e620d9feb0498bacf5516eed99b5ba3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755342"
---
# <a name="how-to-create-multi-project-templates"></a>Instrukcje: Tworzenie szablonów wielu projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Gdy projekt oparty na szablonie wieloprojektowym jest tworzona na podstawie **nowy projekt** okno dialogowe, każdy projekt w szablonie zostanie dodany do rozwiązania.  
  
 Szablonu wieloprojektowego musi zawierać następujące elementy, skompresowany do pliku zip:  
  
- Główny plik .vstemplate szablonu wieloprojektowego całego. Ten główny plik .vstemplate szablonu zawiera metadane, **nowy projekt** okno dialogowe wyświetla i określa, gdzie można znaleźć plików .vstemplate dla projektów w tym szablonie. Ten plik musi znajdować się w katalogu głównym pliku zip.  
  
- Jeden lub więcej folderów zawierających pliki, które są wymagane przez szablon kompletnego projektu. W tym wszystkie pliki kodu dla projektu i pliku .vstemplate dla projektu.  
  
  Na przykład plik zip szablonu wieloprojektowego, który ma dwa projekty mają następujące pliki i katalogi:  
  
  MultiProjectTemplate.vstemplate  
  
  \Project1\Project1.vstemplate  
  
  \Project1\Project1.vbproj  
  
  \Project1\Class.VB  
  
  \Project2\Project2.vstemplate  
  
  \Project2\Project2.vbproj  
  
  \Project2\Class.VB  
  
  Główny plik .vstemplate szablonu wieloprojektowego różni się od szablonu jednego projektu w następujący sposób:  
  
- `Type` Atrybutu `VSTemplate` element zawiera wartość `ProjectGroup`. Na przykład:  
  
  ```  
  <VSTemplate Version="2.0.0" Type="ProjectGroup"  
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
  ```  
  
- `TemplateContent` Element zawiera `ProjectCollection` element, który ma co najmniej jeden `ProjectTemplateLink` elementy, które definiują ścieżki do plików .vstemplate uwzględnione projektów. Na przykład:  
  
  ```  
  <TemplateContent>  
      <ProjectCollection>  
          <ProjectTemplateLink>  
              Project1\Project1.vstemplate  
          </ProjectTemplateLink>  
          <ProjectTemplateLink>  
              Project2\Project2.vstemplate  
          </ProjectTemplateLink>  
      </ProjectCollection>  
  </TemplateContent>  
  ```  
  
  Szablony wielu projektów również będą działały inaczej niż normalny szablonów. Szablony wielu projektów mają następujące cechy unikatowy:  
  
- Poszczególnych projektów w szablonie wieloprojektowym nie można przypisać nazwy **nowy projekt** okno dialogowe. Zamiast tego należy użyć `ProjectName` atrybutu na `ProjectTemplateLink` elementu, aby określić nazwę dla każdego projektu. Aby uzyskać więcej informacji Zobacz pierwszy przykład w poniższej sekcji.  
  
- Szablony wielu projektów może zawierać projekty napisane w różnych językach, ale cały samego szablonu tylko można umieścić w jednej kategorii, za pomocą `ProjectType` elementu.  
  
### <a name="to-create-a-multi-project-template"></a>Aby utworzyć szablon wielu projektów  
  
1.  Twórz projekty do uwzględnienia w szablonie wieloprojektowym.  
  
2.  Tworzenie plików .vstemplate dla każdego projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md).  
  
3.  Utwórz główny plik .vstemplate szablonu, który zawiera metadane szablonu wieloprojektowego. Aby uzyskać więcej informacji Zobacz pierwszy przykład w poniższej sekcji.  
  
4.  Wybierz pliki i foldery do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki i foldery są kompresowane w pliku zip.  
  
5.  Umieść plik zip szablonu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katalogu szablonu projektu. Domyślnie ten katalog jest \My Studio *wersji*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia plik .vstemplate podstawowe główny wielu projektów. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library`. `ProjectName` Atrybutu na `ProjectTemplateLink` element ustawia nazwę [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przypisze temu projektowi. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku vstemplate jest używana jako nazwa projektu.  
  
```  
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
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `SolutionFolder` elementu, aby podzielić projekty na dwie grupy `Math Classes` i `Graphics Classes`. Szablon zawiera cztery projektów, dwie z nich są umieszczane w każdym folderze rozwiązania.  
  
```  
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Instrukcje: Create Project Templates](../ide/how-to-create-project-templates.md)   
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Solutionfolder — Element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink, element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
