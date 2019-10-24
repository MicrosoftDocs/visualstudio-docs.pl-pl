---
title: SortOrder — Element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719922"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder — Element (szablony Visual Studio)
Określa wartość, która jest używana do rozmieszczenia szablonu, między innymi szablonami w tej samej kategorii, jak pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

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

 `integer`, który reprezentuje wartość kolejności sortowania.

## <a name="remarks"></a>Uwagi
 `SortOrder` jest elementem opcjonalnym. Wartość domyślna to 100, a wszystkie wartości muszą być wielokrotnościami 10.

 Element `SortOrder` jest ignorowany dla szablonów utworzonych przez użytkownika. Wszystkie szablony utworzone przez użytkownika są sortowane alfabetycznie.

 Szablony, które mają niskie wartości kolejności sortowania, są wyświetlane w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** przed szablonami, które mają wysokie wartości kolejności sortowania.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla standardowego szablonu klasy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

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

 W tym przykładzie element `SortOrder` jest stosunkowo wysoki. Prawdopodobnie inne szablony elementów [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] będą mieć `SortOrder` wartość niższą niż `290` i pojawią się przed tym szablonem w oknie dialogowym **nowy element** .

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)