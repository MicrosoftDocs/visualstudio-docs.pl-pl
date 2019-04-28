---
title: PROJECTTYPE — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84bdc9b7f0ff6d342abe15f4fb5679c642f54fb2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434756"
---
# <a name="projecttype-element-visual-studio-templates"></a>PROJECTTYPE — element (szablony Visual Studio)
Klasyfikuje szablon projektu, tak aby była wyświetlana w ramach określonej grupy w **nowy projekt** lub **Dodaj nowy element** okno dialogowe.

> [!WARNING]
> Szablony projektów są obsługiwane dla języka C++, począwszy od programu Visual Studio 2012. Nie są obsługiwane w języku C++ w Visual Studio 2010 i starszych wersji.

 \<VSTemplate> \<TemplateData> \<ProjectType>

## <a name="syntax"></a>Składnia

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ta wartość określa typ projektu szablonu zostanie utworzona i musi zawierać jeden z następujących wartości:

- `CSharp`: Określa, że ten szablon tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu lub elementu.

- `VisualBasic`: Określa, że ten szablon tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu lub elementu.

- `Web`: Określa, że ten szablon tworzy projekt sieci Web lub elementu. Jeśli `ProjectType` element zawiera tę wartość, język projektu lub elementu jest zdefiniowany w [projectsubtype — Element (szablony Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Uwagi
 `ProjectType` jest wymaganym elementem podrzędnym elementu `TemplateData`.

 Wartość `ProjectType` element określa, gdzie szablon znajduje się w **nowy projekt** lub **Dodaj nowy element** okno dialogowe. Na przykład szablon z `ProjectType` wartość `CSharp` pojawia się w obszarze **Visual C#** w węźle **nowy projekt** okno dialogowe.

 Podtyp szablonu można określić za pomocą [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) elementu.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Projectsubtype — element (szablony Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)