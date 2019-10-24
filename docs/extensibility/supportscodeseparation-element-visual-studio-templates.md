---
title: SupportsCodeSeparation —, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e68516a798bcd4d1437ab504c09b4cc529eb889
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719429"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation — Element (szablony Visual Studio)
Określa, czy pole wyboru **Umieść kod w osobnym pliku** jest włączone w oknie dialogowym **Dodaj nowy element** .

 \<VSTemplate > \<TemplateData > \<SupportsCodeSeparation >

## <a name="syntax"></a>Składnia

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi mieć wartość `true` lub `false`, co wskazuje, czy pole wyboru **Umieść kod w osobnym pliku** jest włączone w oknie dialogowym **Dodaj nowy element** .

## <a name="remarks"></a>Uwagi
 `SupportsCodeSeparation` jest elementem opcjonalnym. Wartość domyślna to `false`.

 Element `SupportsCodeSeparation` jest dostępny tylko dla szablonów elementów sieci Web.

 Separacja kodu lub model strony związany z kodem pozwala zachować adiustację w jednym pliku i kodzie programowania w innym pliku. Ten model jest używany przez [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] i inne języki platformy .NET.

## <a name="example"></a>Przykład
 Poniższy przykład określa, aby wyświetlić opcję **Umieść kod w osobnym pliku** .

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)