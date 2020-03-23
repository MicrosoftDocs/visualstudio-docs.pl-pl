---
title: Konstrukcje warunkowe MSBuild | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 0a06849c2aa0f4ec0203a7209ffc78be438dba9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633385"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild

MSBuild udostępnia mechanizm dla albo/lub przetwarzania z [Wybierz](../msbuild/choose-element-msbuild.md), [Kiedy](../msbuild/when-element-msbuild.md)i [W inny sposób](../msbuild/otherwise-element-msbuild.md) elementów.

## <a name="use-the-choose-element"></a>Użyj elementu Wybierz

 Element `Choose` zawiera serię `When` elementów `Condition` z atrybutami, które są testowane w `true`kolejności od góry do dołu, aż jeden ocenia . Jeśli więcej `When` niż jeden `true`element ocenia , używany jest tylko pierwszy. Element, `Otherwise` jeśli jest obecny, zostanie oceniony, jeśli żaden warunek `When` elementu nie zostanie obliczony na `true`.

 `Choose`elementy mogą być używane `Project`jako `When` `Otherwise` elementy podrzędne , i elementów. `When`i `Otherwise` elementy `ItemGroup`mogą `PropertyGroup`mieć `Choose` , lub elementy podrzędne.

## <a name="example"></a>Przykład

 W poniższym `Choose` przykładzie `When` użyto i elementy dla albo/lub przetwarzania. Właściwości i elementy projektu są ustawiane w zależności `Configuration` od wartości właściwości.

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

## <a name="see-also"></a>Zobacz też

- [Wybierz element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Gdy element (MSBuild)](../msbuild/when-element-msbuild.md)
- [W przeciwnym razie element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
