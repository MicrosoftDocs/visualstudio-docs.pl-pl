---
title: Projectitem — Element (szablony elementów Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fe6613288cac93034dd32a3203f1bb73004f83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747952"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem Element (szablony elementów Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa plik, który znajduje się w szablonie elementu.  
  
> [!NOTE]
>  `ProjectItem` Akceptuje różnych atrybutów w zależności od tego, czy szablon projektu lub elementu. W tym temacie opisano `ProjectItem` elementu dla elementu. Aby uzyskać informacje o `ProjectItem` element dla szablonów projektu, zobacz [ProjectItem, Element (szablony projektu Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`SubType`|Atrybut opcjonalny.<br /><br /> Określa podtyp elementu w szablonie elementów wielu plików. Ta wartość służy do określania edytora, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] będzie używać, aby otworzyć element.|  
|`CustomTool`|Atrybut opcjonalny.<br /><br /> Ustawia CustomTool dla elementu w pliku projektu.|  
|`ItemType`|Atrybut opcjonalny.<br /><br /> Ustawia ItemType dla elementu w pliku projektu.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać przesłonięte, gdy projekt jest tworzony na podstawie tego szablonu. Wartość domyślna to `false`.|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę elementu, który jest tworzone na podstawie szablonu. Ten atrybut jest przydatne w przypadku za pomocą zastąpienia parametrów do utworzenia nazwy elementu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 A `string` reprezentujący nazwę pliku w pliku zip szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectItem` jest podrzędnym opcjonalne `TemplateContent`.  
  
 `TargetFileName` Atrybut może służyć do zmiany nazwy plików z parametrami. Na przykład jeśli plik `MyFile.vb` istnieje w katalogu głównym pliku zip szablonu, ale chcesz plik miała nazwę oparty na nazwę pliku, dostarczone przez użytkownika w **Dodaj nowy element** okno dialogowe, należy użyć następujący kod XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Po utworzeniu elementu za pomocą tego szablonu, nazwa pliku będzie zależeć od nazwy użytkownik wprowadzi w **Dodaj nowy element** okno dialogowe. Jest to przydatne podczas tworzenia szablonów elementów wielu plików. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md) i [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych dla szablonu elementu standardowego dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)

