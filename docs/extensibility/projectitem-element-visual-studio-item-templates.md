---
title: ProjectItem, element (szablony elementów Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu ProjectItem dla szablonów elementów i sposobu akceptowania przez niego różnych atrybutów w zależności od tego, czy szablon dotyczy projektu czy elementu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 431f1d5f81827b47b57a53dbe411a2a7e8a57941
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672336"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem, element (szablony elementów Visual Studio)
Określa plik, który jest zawarty w szablonie elementu.

> [!NOTE]
> `ProjectItem`Element akceptuje różne atrybuty w zależności od tego, czy szablon dotyczy projektu lub elementu. W tym temacie objaśniono `ProjectItem` element dla elementu. Aby uzyskać wyjaśnienie `ProjectItem` elementu szablonów projektu, zobacz [ProjectItem element (szablony projektów Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

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
| `SubType` | Atrybut opcjonalny.<br /><br /> Określa podtyp elementu w szablonie elementu wieloplikowego. Ta wartość służy do określenia edytora, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie używany do otwierania elementu. |
| `CustomTool` | Atrybut opcjonalny.<br /><br /> Ustawia CustomTool dla elementu w pliku projektu. |
| `ItemType` | Atrybut opcjonalny.<br /><br /> Ustawia ItemType dla elementu w pliku projektu. |
| `ReplaceParameters` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element zawiera wartości parametrów, które muszą zostać zastąpione, gdy projekt jest tworzony na podstawie szablonu. Wartość domyślna to `false`. |
| `TargetFileName` | Atrybut opcjonalny.<br /><br /> Określa nazwę elementu, który jest tworzony na podstawie szablonu. Ten atrybut jest przydatny do tworzenia nazwy elementu przy użyciu zastąpienia parametrów. |

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 `string`Reprezentuje nazwę pliku w pliku template *. zip* .

## <a name="remarks"></a>Uwagi
 `ProjectItem` jest opcjonalnym elementem podrzędnym `TemplateContent` .

 Ten `TargetFileName` atrybut może służyć do zmiany nazwy plików z parametrami. Na przykład jeśli plik *. vb* istnieje w katalogu głównym pliku template *. zip* , ale plik ma być nazwany na podstawie nazwy pliku dostarczonej przez użytkownika w oknie dialogowym **Dodaj nowy element** , należy użyć następującego kodu XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Gdy element jest tworzony na podstawie tego szablonu, nazwa pliku będzie oparta na nazwie wprowadzonej przez użytkownika w oknie dialogowym **Dodaj nowy element** . Jest to przydatne podczas tworzenia szablonów elementów wieloplikowych. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md) i [parametrów szablonu](../ide/template-parameters.md).

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla szablonu elementu standardowego dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.

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
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów elementów wieloplikowych](../ide/how-to-create-multi-file-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
