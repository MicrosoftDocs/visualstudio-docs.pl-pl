---
title: SupportsLanguageDropDown Element (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1230b493fe746a272cf4ca4cffe9d197afd8ba1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699470"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown — Element (szablony Visual Studio)
Określa, czy szablon elementu sieci Web jest identyczny dla wielu języków i czy opcja **Język** jest włączona w oknie dialogowym **Dodawanie nowego elementu.**

 \<VSTemplate> \<TemplateData> \<SupportsLanguageDropDown>

## <a name="syntax"></a>Składnia

```
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`lub , wskazując, czy opcja **Język** jest dostępna w oknie dialogowym **Dodawanie nowego elementu.**

## <a name="remarks"></a>Uwagi
 `SupportsLanguageDropDown`jest elementem opcjonalnym. Wartością domyślną jest `false`.

 Element `SupportsLanguageDropDown` jest dostępny tylko dla szablonów elementów sieci Web.

 Jeśli wartość tego elementu jest `true`ustawiona na wartość , szablon elementu jest identyczny dla wszystkich języków programowania, a opcja **Język** jest włączona w oknie dialogowym **Dodawanie nowego elementu.** Ta opcja umożliwia wybranie języka programowania nowego elementu, który chcesz utworzyć na podstawie szablonu.

## <a name="example"></a>Przykład
 Poniższy przykład określa, aby wyświetlić opcję rozwijaną **Język.**

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
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
