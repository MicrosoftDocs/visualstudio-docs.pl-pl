---
title: Konstrukcje warunkowe MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26891fa67616b1796499722e03a764da2a8fd7d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589269"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zapewnia mechanizm do przetwarzania za pomocą elementów [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)i [Otherwise](../msbuild/otherwise-element-msbuild.md) .

## <a name="use-the-choose-element"></a>Użyj wybierz element
 Element `Choose` zawiera serię `When` elementów z atrybutami `Condition`, które są testowane w kolejności od góry do dołu do momentu, aż do `true`. Jeśli więcej niż jeden element `When` oblicza `true`, zostanie użyta tylko pierwsza z nich. Element `Otherwise`, jeśli jest obecny, będzie oceniany, jeśli nie ma żadnego warunku elementu `When` do `true`.

 elementy `Choose` mogą być używane jako elementy podrzędne `Project`, `When` i `Otherwise` elementów. elementy `When` i `Otherwise` mogą mieć elementy podrzędne `ItemGroup`, `PropertyGroup`lub `Choose`.

## <a name="example"></a>Przykład
 W poniższym przykładzie są użyte elementy `Choose` i `When` do przetwarzania. Właściwości i elementy projektu są ustawiane w zależności od wartości właściwości `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
    </Choose>
    <!-- Rest of Project -->
</Project>
```

## <a name="see-also"></a>Zobacz także
- [Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When, element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
