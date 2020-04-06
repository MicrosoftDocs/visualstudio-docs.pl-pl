---
title: Element RequiredFrameworkVersion (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701509"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Element RequiredFrameworkVersion (szablony programu Visual Studio)

Określa minimalną wersję programu .NET Framework, która jest wymagana przez szablon. Powoduje to, że **wersja docelowa wersja** rozwijana mają być wyświetlane w oknie dialogowym **Nowy projekt.** Element `RequiredFrameworkVersion` określa również najniższą wartość dostępną w rozwijanej.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2017 w wersji 15.6, **docelowa wersja frameworka rozwijana** nie jest już filtrem dla wyświetlanych szablonów w sekcji **Szablony** okna dialogowego **Nowy projekt.** Zamiast tego rozwijane funkcje jako selektor struktury dla wybranego szablonu.

 \<> \<szablonu> \<>> RequiredFrameworkVersion

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób jego wyświetlania w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być minimalny numer wersji programu .NET Framework, który jest wymagany dla szablonu.

## <a name="remarks"></a>Uwagi

`RequiredFrameworkVersion`jest elementem opcjonalnym. Tego elementu należy używać tylko wtedy, gdy szablon obsługuje określoną wersję minimalną (i nowszą wersję, jeśli istnieje) programu .NET Framework. Jeśli określisz `RequiredFrameworkVersion` element i szablon nie obsługuje określonej minimalnej wersji programu .NET Framework, listy rozwijanej **Wersja docelowa frameworka** jest wyświetlana, gdy nie ma zastosowania.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje metadane szablonu klasy standardowej. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

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

W tym przykładzie minimalna wersja programu .NET Framework, która jest `RequiredFrameworkVersion`wymagana przez szablon, reprezentowana przez , jest 3.0. Projekt utworzony za pomocą tego szablonu może dotyczyć wersji programu .NET Framework od wersji 3.0.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md)
