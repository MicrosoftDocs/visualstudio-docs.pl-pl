---
title: Element SupportsCodeSeparation (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699498"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation — Element (szablony Visual Studio)
Określa, czy pole wyboru **Umieść kod w oddzielnym pliku** jest włączone w oknie dialogowym Dodawanie nowego **elementu.**

 \<> \<> TemplateData> \<supportsCodeSeparation>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub **Nowy element.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`albo , wskazując, czy pole wyboru **Umieść kod w oddzielnym pliku** jest włączone w oknie dialogowym Dodawanie nowego **elementu.**

## <a name="remarks"></a>Uwagi
 `SupportsCodeSeparation`jest elementem opcjonalnym. Wartością domyślną jest `false`.

 Element `SupportsCodeSeparation` jest dostępny tylko dla szablonów elementów sieci Web.

 Separacja kodu lub model strony związanej z kodem, umożliwia zachowanie znaczników w jednym pliku i kod programowania w innym pliku. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]i inne języki platformy .NET używają tego modelu.

## <a name="example"></a>Przykład
 Poniższy przykład określa, aby wyświetlić **opcję Umieść kod w osobnym pliku.**

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

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
