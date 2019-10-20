---
title: 'Instrukcje: Tworzenie szablonów wieloprojektowych | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de155b71e82bb7561030cae2e1d0d4d777c9586
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668059"
---
# <a name="how-to-create-multi-project-templates"></a>Porady: tworzenie szablonów wielu projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. Gdy projekt oparty na szablonie wieloprojektowym jest tworzony z okna dialogowego **Nowy projekt** , każdy projekt w szablonie zostanie dodany do rozwiązania.

 Szablon wieloprojektowy musi zawierać następujące elementy, które zostały skompresowane do pliku zip:

- Plik root. vstemplate dla całego szablonu wieloprojektowego. Ten plik root. vstemplate zawiera metadane, które są wyświetlane w oknie dialogowym **Nowy projekt** , i określa, gdzie znaleźć pliki. vstemplate dla projektów w tym szablonie. Ten plik musi znajdować się w katalogu głównym pliku zip.

- Co najmniej jeden folder zawierający pliki, które są wymagane dla kompletnego szablonu projektu. Obejmuje to wszystkie pliki kodu dla projektu, a także plik. vstemplate dla projektu.

  Na przykład plik Template. zip szablonu z dwoma projektami może mieć następujące pliki i katalogi:

  MultiProjectTemplate. vstemplate

  \Project1\Project1.vstemplate

  \Project1\Project1.vbproj

  \Project1\Class.vb

  \Project2\Project2.vstemplate

  \Project2\Project2.vbproj

  \Project2\Class.vb

  Plik root. vstemplate szablonu wieloprojektowego różni się od szablonu pojedynczego projektu w następujący sposób:

- Atrybut `Type` elementu `VSTemplate` zawiera `ProjectGroup` wartości. Na przykład:

  ```
  <VSTemplate Version="2.0.0" Type="ProjectGroup"
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
  ```

- Element `TemplateContent` zawiera `ProjectCollection` element, który ma co najmniej jeden `ProjectTemplateLink` elementów, które definiują ścieżki do plików. vstemplate dołączonych projektów. Na przykład:

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

  Szablony wielu projektów zachowują się również inaczej niż normalne szablony. Szablony wieloprojektowe mają następujące unikatowe cechy:

- Poszczególne projekty w szablonie wieloprojektowym nie mogą być przypisane do nazw za pomocą okna dialogowego **Nowy projekt** . Zamiast tego należy użyć atrybutu `ProjectName` w elemencie `ProjectTemplateLink`, aby określić nazwę dla każdego projektu. Aby uzyskać więcej informacji, zapoznaj się z pierwszym przykładem w następnej sekcji.

- Szablony wielu projektów mogą zawierać projekty, które są zapisywane w różnych językach, ale cały szablon można umieścić tylko w jednej kategorii za pomocą elementu `ProjectType`.

### <a name="to-create-a-multi-project-template"></a>Aby utworzyć szablon wieloprojektowy

1. Utwórz projekty do uwzględnienia w szablonie wieloprojektowym.

2. Utwórz pliki. vstemplate dla każdego projektu. Aby uzyskać więcej informacji, zobacz [How to: Create Project Templates](../ide/how-to-create-project-templates.md).

3. Utwórz plik root. vstemplate, który będzie zawierał metadane dla szablonu wieloprojektowego. Aby uzyskać więcej informacji, zapoznaj się z pierwszym przykładem w następnej sekcji.

4. Wybierz pliki i foldery do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij polecenie **Wyślij do**, a następnie kliknij **folder skompresowany (zip)** . Pliki i foldery są kompresowane do pliku zip.

5. Umieść plik. zip szablonu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] katalogu szablonów projektu. Domyślnie ten katalog to \Moje Documents\Visual Studio w *wersji*\Templates\ProjectTemplates \\.

## <a name="example"></a>Przykład
 Ten przykład pokazuje podstawowy plik vstemplate z wielojęzycznym projektem. W tym przykładzie szablon zawiera dwa projekty, `My Windows Application` i `My Class Library`. Atrybut `ProjectName` w elemencie `ProjectTemplateLink` ustawia nazwę [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aby przypisać ten projekt. Jeśli atrybut `ProjectName` nie istnieje, nazwa pliku. vstemplate jest używana jako nazwa projektu.

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
 Ten przykład używa elementu `SolutionFolder`, aby podzielić projekty na dwie grupy, `Math Classes` i `Graphics Classes`. Szablon zawiera cztery projekty, z których dwa są umieszczane w każdym folderze rozwiązania.

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
 [Tworzenie szablonów projektów i elementów —](../ide/creating-project-and-item-templates.md) [Informacje o schemacie szablonu programu Visual](../extensibility/visual-studio-template-schema-reference.md) Studio [: Tworzenie szablonów projektu](../ide/how-to-create-project-templates.md) [programu Visual Studio szablon odwołania](../extensibility/visual-studio-template-schema-reference.md) [SolutionFolder element (szablony Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md) [ ProjectTemplateLink, element (szablony Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
