---
title: Element MaxFrameworkVersion (szablony programu Visual Studio) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702619"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Element MaxFrameworkVersion (szablony programu Visual Studio)

Określa maksymalną wersję programu .NET Framework, która jest wymagana przez szablon. Określa najwyższą wartość dostępną w **docelowej wersji frameworka** rozwijanego okna dialogowego **Nowy projekt.** Aby użytkownicy mogli wybrać wersję framework, należy również określić [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimalną wersję programu .NET Framework dla szablonu.

> [!IMPORTANT]
> Począwszy od programu Visual Studio 2017 w wersji 15.6, **docelowa wersja frameworka rozwijana** nie jest już filtrem dla wyświetlanych szablonów w sekcji **Szablony** okna dialogowego **Nowy projekt.** Zamiast tego funkcja **rozwijana wersji platformy docelowej** działa jako selektor struktury dla wybranego szablonu.

 \<>> \<TemplateData \<> MaxFrameworkVersion

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób jego wyświetlania w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być najwyższy numer wersji programu .NET Framework, który jest dozwolony przez szablon.

## <a name="remarks"></a>Uwagi

`MaxFrameworkVersion`jest elementem opcjonalnym. Element `MaxFrameworkVersion` należy pominąć, chyba że jest to wymagane, tak aby nie przypadkowo ograniczyć obsługiwany zakres wersji programu .NET Framework dla szablonu. Należy również pominąć, jeśli .NET Framework nie ma zastosowania do szablonu.

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

W tym przykładzie maksymalna wersja programu .NET Framework, która jest `MaxFrameworkVersion`wymagana przez szablon, reprezentowana przez , jest 4.7.1. Projekt utworzony za pomocą tego szablonu może dotyczyć wersji programu .NET Framework do wersji 4.7.1.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
