---
title: SupportsLanguageDropDown —, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9b5727bd9aa09b05fc95d8f9f9b7913a6046b81
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719415"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown — Element (szablony Visual Studio)
Określa, czy szablon elementu sieci Web jest identyczny dla wielu języków i czy opcja **Język** jest włączona w oknie dialogowym **Dodaj nowy element** .

 \<VSTemplate > \<TemplateData > \<SupportsLanguageDropDown >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi mieć wartość `true` lub `false`, wskazując, czy opcja **języka** jest dostępna w oknie dialogowym **Dodaj nowy element** .

## <a name="remarks"></a>Uwagi
 `SupportsLanguageDropDown` jest elementem opcjonalnym. Wartość domyślna to `false`.

 Element `SupportsLanguageDropDown` jest dostępny tylko dla szablonów elementów sieci Web.

 Jeśli wartość dla tego elementu jest ustawiona na `true`, szablon elementu jest identyczny dla wszystkich języków programowania, a opcja **Język** jest włączona w oknie dialogowym **Dodaj nowy element** . Ta opcja umożliwia wybranie języka programowania nowego elementu, który ma zostać utworzony na podstawie szablonu.

## <a name="example"></a>Przykład
 Poniższy przykład określa, aby wyświetlić opcję Lista rozwijana **języka** .

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)