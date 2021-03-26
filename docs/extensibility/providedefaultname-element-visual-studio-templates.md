---
title: ProvideDefaultName —, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie ProvideDefaultName — i sposobie jego określania, czy program Visual Studio będzie generował domyślną nazwę programu Visual Studio w oknie dialogowym Dodaj nowy element lub nowy projekt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d29ca3075ee6e5ef031bb360ecfd10d6cb341c26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068650"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName —, element (szablony Visual Studio)
Określa, czy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] system projektu będzie generował nazwę domyślną dla szablonu w oknie dialogowym **Dodaj nowy element** lub **Nowy projekt** .

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Składnia

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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

 Tekst musi mieć wartość `true` lub `false` , wskazujący, czy generować nazwę domyślną szablonu w oknie dialogowym **Dodaj nowy element** lub **Nowy projekt** .

## <a name="remarks"></a>Uwagi
 `ProvideDefaultName` jest elementem opcjonalnym. Wartość domyślna to `true`.

 Jeśli `ProvideDefaultName` element to `false` , pola **nazwy** okna dialogowego **Dodaj nowy element** i **Nowy projekt** zawierają wartość `<Enter_name>` .

 Użyj elementu [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) , aby określić nazwę domyślną projektu lub elementu w oknach dialogowych **Dodaj nowy element** i **Nowy projekt** . Gdy wartość `ProvideDefaultName` elementu jest `true` , pominięcie `DefaultName` elementu dla projektów powoduje wypełnienie okna dialogowego nazwą szablonu, czyli wartością z elementu [Nazwa](../extensibility/name-element-visual-studio-templates.md) ...

## <a name="example"></a>Przykład
 Poniższy przykład kodu ustawia `ProvideDefaultName` element na `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
