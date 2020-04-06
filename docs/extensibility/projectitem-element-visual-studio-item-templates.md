---
title: Element ProjectItem (szablony elementów programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701873"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Element ProjectItem (szablony elementów programu Visual Studio)
Określa plik, który znajduje się w szablonie elementu.

> [!NOTE]
> Element `ProjectItem` akceptuje różne atrybuty w zależności od tego, czy szablon jest dla projektu lub elementu. W tym `ProjectItem` temacie wyjaśniono element dla elementu. Aby uzyskać wyjaśnienie `ProjectItem` elementu dla szablonów projektów, zobacz [Element ProjectItem (szablony projektu programu Visual Studio).](../extensibility/projectitem-element-visual-studio-project-templates.md)

 \<VsTemplate> \<TemplateContent> \<ProjectItem>

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
| `SubType` | Atrybut opcjonalny.<br /><br /> Określa podtyp elementu w szablonie elementu z wieloma plikami. Ta wartość jest używana do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] określenia edytora, który będzie używany do otwierania elementu. |
| `CustomTool` | Atrybut opcjonalny.<br /><br /> Ustawia CustomTool dla elementu w pliku projektu. |
| `ItemType` | Atrybut opcjonalny.<br /><br /> Ustawia itemtype dla elementu w pliku projektu. |
| `ReplaceParameters` | Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać zastąpione podczas tworzenia projektu na podstawie szablonu. Wartością `false`domyślną jest . |
| `TargetFileName` | Atrybut opcjonalny.<br /><br /> Określa nazwę elementu utworzonego na podstawie szablonu. Ten atrybut jest przydatny do tworzenia nazwy elementu przy użyciu zastępowania parametrów. |

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 A `string` reprezentujący nazwę pliku w pliku *zip* szablonu.

## <a name="remarks"></a>Uwagi
 `ProjectItem`jest opcjonalnym `TemplateContent`dzieckiem .

 Atrybut `TargetFileName` może służyć do zmiany nazwy plików z parametrami. Na przykład, jeśli plik *MyFile.vb* istnieje w katalogu głównym szablonu *.zip,* ale chcesz, aby plik został nazwany na podstawie nazwy pliku podanej przez użytkownika w oknie dialogowym **Dodawanie nowego elementu,** należy użyć następującego pliku XML:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Po utworzeniu elementu na podstawie tego szablonu nazwa pliku będzie oparta na nazwie wprowadzonej przez użytkownika w oknie dialogowym **Dodawanie nowego elementu.** Jest to przydatne podczas tworzenia szablonów elementów z wieloma plikami. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie szablonów elementów z wieloma plikami](../ide/how-to-create-multi-file-item-templates.md) i [parametrów szablonu](../ide/template-parameters.md).

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu elementu standardowego dla klasy.

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
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów elementów z wieloma plikami](../ide/how-to-create-multi-file-item-templates.md)
- [Parametry szablonu](../ide/template-parameters.md)
