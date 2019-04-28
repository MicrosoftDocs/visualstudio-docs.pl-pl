---
title: Konstrukcje warunkowe MSBuild | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 045a7366546e85ad2e9588ce2a14077f8b18a331
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842563"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] udostępnia mechanizm dla dowolnego / lub przetwarzania za pomocą [wybierz](../msbuild/choose-element-msbuild.md), [podczas](../msbuild/when-element-msbuild.md), i [przeciwnym](../msbuild/otherwise-element-msbuild.md) elementów.

## <a name="use-the-choose-element"></a>Użyj elementu wybierz
 `Choose` Element zawiera szereg `When` elementów za pomocą `Condition` atrybuty, które są badane w kolejności od góry do dołu, aż jedną daje w wyniku `true`. Jeśli istnieje więcej niż jedna `When` daje w wyniku element `true`, tylko pierwszy z nich jest używany. `Otherwise` Elementu, jeśli jest obecny, zostaną ocenione Jeśli żadnego warunku na `When` daje w wyniku element `true`.

 `Choose` elementy mogą być używane jako elementy podrzędne `Project`, `When` i `Otherwise` elementów. `When` i `Otherwise` może mieć elementów `ItemGroup`, `PropertyGroup`, lub `Choose` elementów podrzędnych.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto `Choose` i `When` elementów dla dowolnego / lub przetwarzania. Właściwości i elementy projektu są ustawiane w zależności od wartości `Configuration` właściwości.

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
- [Gdy element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)