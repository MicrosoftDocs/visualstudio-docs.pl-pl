---
title: MaxFrameworkVersion, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573fcbce3b395f7f351d57208998b0b63b175559
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907230"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion, element (szablony Visual Studio)

Określa maksymalną wersję programu .NET Framework, która jest wymagana przez szablon. Określa wartość najwyższy dostępny w **wersji platformy docelowej** lista rozwijana z **nowy projekt** okna dialogowego. Aby użytkownicy mogli wybrać wersję framework, należy także określić [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimalnej wersji systemu .NET Framework dla szablonu.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2017 w wersji 15.6, **wersji platformy docelowej** listy rozwijanej nie jest już filtr dla szablonów wyświetlanych w **szablony** części **nowy projekt** okna dialogowego. Zamiast tego **wersji platformy docelowej** listy rozwijanej działa jako selektora framework, dla wybranego szablonu.

 \<VSTemplate> \<TemplateData> \<MaxFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być najwyższy numer wersji systemu .NET Framework, który jest dozwolony przez szablon.

## <a name="remarks"></a>Uwagi

`MaxFrameworkVersion` element jest opcjonalny. `MaxFrameworkVersion` Element należy pominąć, chyba że jest to wymagane, w celu przypadkowo ograniczenie wersji obsługiwanych zakres dla programu .NET Framework dla szablonu. Należy również pominąć, jeśli .NET Framework nie ma zastosowania do szablonu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metadanych dla standardowego [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.

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

W tym przykładzie maksymalna wersja systemu .NET Framework, która jest wymagana przez szablon, reprezentowane przez `MaxFrameworkVersion`, jest 4.7.1. Projekt, który został utworzony za pomocą tego szablonu można wskazać wersje programu .NET Framework do 4.7.1.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
