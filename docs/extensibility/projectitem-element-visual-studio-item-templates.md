---
title: Projectitem — Element (szablony elementów Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a27c297dd9b33bbbe02b7addb827323505a7156d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956065"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Projectitem — element (szablony elementów Visual Studio)
Określa plik, który znajduje się w szablonie elementu.  
  
> [!NOTE]
>  `ProjectItem` Akceptuje różnych atrybutów w zależności od tego, czy szablon projektu lub elementu. W tym temacie opisano `ProjectItem` elementu dla elementu. Aby uzyskać informacje o `ProjectItem` element dla szablonów projektu, zobacz [ProjectItem, element (szablony projektu Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
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
  
| Atrybut | Opis |
|---------------------| - |
| `SubType` | Atrybut opcjonalny.<br /><br /> Określa podtyp elementu w szablonie elementów wielu plików. Ta wartość służy do określania edytora, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie używać, aby otworzyć element. |
| `CustomTool` | Atrybut opcjonalny.<br /><br /> Ustawia CustomTool dla elementu w pliku projektu. |
| `ItemType` | Atrybut opcjonalny.<br /><br /> Ustawia ItemType dla elementu w pliku projektu. |
| `ReplaceParameters` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać przesłonięte, gdy projekt jest tworzony na podstawie tego szablonu. Wartość domyślna to `false`. |
| `TargetFileName` | Atrybut opcjonalny.<br /><br /> Określa nazwę elementu, który jest tworzone na podstawie szablonu. Ten atrybut jest przydatne w przypadku za pomocą zastąpienia parametrów do utworzenia nazwy elementu. |
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 A `string` reprezentujący nazwę pliku w szablonie *zip* pliku.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectItem` jest podrzędnym opcjonalne `TemplateContent`.  
  
 `TargetFileName` Atrybut może służyć do zmiany nazwy plików z parametrami. Na przykład jeśli plik *MyFile.vb* istnieje w katalogu głównym szablonu *zip* pliku, ale ma pliku do się o nazwie na podstawie nazwy pliku, dostarczone przez użytkownika w **Dodaj nowy element**  okno dialogowe, należy użyć następujący kod XML:  
  
```xml  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Po utworzeniu elementu za pomocą tego szablonu, nazwa pliku będzie zależeć od nazwy użytkownik wprowadzi w **Dodaj nowy element** okno dialogowe. Jest to przydatne podczas tworzenia szablonów elementów wielu plików. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md) i [parametry szablonu](../ide/template-parameters.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych dla szablonu elementu standardowego dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)