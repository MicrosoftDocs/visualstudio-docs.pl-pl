---
title: MaxFrameworkVersion, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie MaxFrameworkVersion i sposobie określania maksymalnej wersji .NET Framework wymaganej przez szablon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44345b712f448bd7eedf288d7c58cb4193e1b020
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672428"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion, element (szablony Visual Studio)

Określa maksymalną wersję .NET Framework wymaganą przez szablon. Określa największą wartość dostępną na liście rozwijanej **wersji platformy docelowej** okna dialogowego **Nowy projekt** . Aby użytkownicy mogli wybrać wersję platformy, należy również określić [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimalną wersję .NET Framework szablonu.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2017 w wersji 15,6, lista rozwijana **wersji platformy docelowej** nie jest już filtrem dla wyświetlanych szablonów w sekcji **Szablony** okna dialogowego **Nowy projekt** . Zamiast tego lista rozwijana **wersji platformy docelowej** działa jako selektor struktury dla wybranego szablonu.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Składnia

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób jego wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być najwyższym numerem wersji .NET Framework, który jest dozwolony przez szablon.

## <a name="remarks"></a>Uwagi

`MaxFrameworkVersion` jest elementem opcjonalnym. `MaxFrameworkVersion`Element powinien być pominięty, chyba że jest wymagany, dlatego nie można przypadkowo ograniczyć obsługiwanego zakresu .NET Framework wersji szablonu. Należy również pominąć, jeśli .NET Framework nie ma zastosowania do szablonu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje metadane dla standardowego [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

W tym przykładzie Maksymalna wersja .NET Framework, która jest wymagana przez szablon, reprezentowana przez `MaxFrameworkVersion` , to 4.7.1. Projekt utworzony za pomocą tego szablonu może wskazywać .NET Framework wersje do 4.7.1.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
