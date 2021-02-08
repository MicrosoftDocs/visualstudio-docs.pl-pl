---
title: RequiredFrameworkVersion — Element (szablony Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 211393ea65f7ca31f80134c48863b0092478b3f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836985"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion, element (szablony Visual Studio)

Określa minimalną wersję .NET Framework wymaganą przez szablon. Powoduje, że lista rozwijana **wersji platformy docelowej** zostanie wyświetlona w oknie dialogowym **Nowy projekt** . `RequiredFrameworkVersion`Element określa również najniższą wartość dostępną na liście rozwijanej.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2017 w wersji 15,6, lista rozwijana **wersji platformy docelowej** nie jest już filtrem dla wyświetlanych szablonów w sekcji **Szablony** okna dialogowego **Nowy projekt** . Zamiast tego element DropDown działa jako selektor struktury dla wybranego szablonu.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Składnia

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Tekst musi być minimalnym numerem wersji .NET Framework, który jest wymagany dla szablonu.

## <a name="remarks"></a>Uwagi

`RequiredFrameworkVersion` jest elementem opcjonalnym. Tego elementu należy używać tylko wtedy, gdy szablon obsługuje określoną minimalną wersję (i nowsze wersje, jeśli istnieją) .NET Framework. Jeśli określisz `RequiredFrameworkVersion` element, a szablon nie obsługuje określonej minimalnej wersji .NET Framework, lista rozwijana **wersji platformy docelowej** zostanie wyświetlona, gdy nie ma zastosowania.

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

W tym przykładzie minimalna wersja .NET Framework, która jest wymagana przez szablon, reprezentowana przez `RequiredFrameworkVersion` , to 3,0. Projekt utworzony przy użyciu tego szablonu może być celem .NET Framework wersji, począwszy od 3,0.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Omówienie określania celu platformy](../ide/visual-studio-multi-targeting-overview.md)
