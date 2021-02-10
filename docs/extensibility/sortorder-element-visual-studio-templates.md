---
title: SortOrder — Element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu SortOrder i sposobu określania wartości, która jest używana do rozmieszczenia szablonu w postaci wyświetlanej w oknie dialogowym Nowy projekt lub Dodaj nowy element.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a086f2ae678541ce28e9ede874c4198e349f438
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942922"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder — Element (szablony Visual Studio)
Określa wartość, która jest używana do rozmieszczenia szablonu, między innymi szablonami w tej samej kategorii, jak pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 `integer`Reprezentuje wartość kolejności sortowania.

## <a name="remarks"></a>Uwagi
 `SortOrder` jest elementem opcjonalnym. Wartość domyślna to 100, a wszystkie wartości muszą być wielokrotnościami 10.

 `SortOrder`Element jest ignorowany dla szablonów utworzonych przez użytkownika. Wszystkie szablony utworzone przez użytkownika są sortowane alfabetycznie.

 Szablony, które mają niskie wartości kolejności sortowania, są wyświetlane w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** przed szablonami, które mają wysokie wartości kolejności sortowania.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla standardowego [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.

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

 W tym przykładzie `SortOrder` element jest stosunkowo wysoki. Prawdopodobnie inne [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Szablony elementów będą mieć `SortOrder` wartość niższą niż `290` i pojawią się przed tym szablonem w oknie dialogowym **nowy element** .

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
