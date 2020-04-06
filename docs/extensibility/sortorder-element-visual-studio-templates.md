---
title: Element SortOrder (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699957"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder — Element (szablony Visual Studio)
Określa wartość używaną do rozmieszczenia szablonu, między innymi szablonami w tej samej kategorii, która jest wyświetlana w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element.**

 \<> \< \<> TemplateData> SortOrder

## <a name="syntax"></a>Składnia

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

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

 Reprezentujący `integer` wartość kolejności sortowania.

## <a name="remarks"></a>Uwagi
 `SortOrder`jest elementem opcjonalnym. Wartość domyślna to 100, a wszystkie wartości muszą być wielokrotnościami 10.

 Element `SortOrder` jest ignorowany dla szablonów utworzonych przez użytkownika. Wszystkie szablony utworzone przez użytkownika są sortowane alfabetycznie.

 Szablony o niskich wartościach kolejności sortowania są wyświetlane w oknie dialogowym **Nowy projekt** lub Nowy **element dodaj** przed szablonami o wysokich wartościach kolejności sortowania.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane szablonu klasy standardowej. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 W tym przykładzie `SortOrder` element jest stosunkowo wysoki. Jest prawdopodobne, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] że inne szablony `SortOrder` elementów `290` będą miały wartość niższą niż i pojawią się przed tym szablonem w oknie dialogowym **Nowy element.**

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
