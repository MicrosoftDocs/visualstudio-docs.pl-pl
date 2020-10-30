---
title: Konstrukcje warunkowe MSBuild | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild udostępnia mechanizm przetwarzania warunkowego za pomocą elementów Choose, when i Otherwise.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 614a59771ea63637ee7c0576f67bf4798cb90c1f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046416"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe programu MSBuild

Program MSBuild oferuje mechanizm do wykonywania operacji lub przetwarzania za pomocą elementów [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)i [Otherwise](../msbuild/otherwise-element-msbuild.md) .

## <a name="use-the-choose-element"></a>Użyj wybierz element

 `Choose`Element zawiera serię `When` elementów z `Condition` atrybutami, które są testowane w kolejności od góry do dołu do momentu, w którym ma zostać obliczona wartość `true` . Jeśli więcej niż jeden `When` element ma wartość `true` , zostanie użyta tylko pierwsza z nich. `Otherwise`Element, jeśli jest obecny, będzie oceniany, jeśli nie ma żadnego warunku dla `When` elementu `true` .

 `Choose` elementy mogą być używane jako elementy podrzędne elementów `Project` `When` i `Otherwise` . `When``Otherwise`elementami i mogą być `ItemGroup` `PropertyGroup` `Choose` elementy podrzędne.

## <a name="example"></a>Przykład

 Poniższy przykład używa `Choose` `When` elementów i dla obu/lub do przetwarzania. Właściwości i elementy projektu są ustawiane w zależności od wartości `Configuration` właściwości.

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

W tym przykładzie jest używany warunek dla stałej kompilatora `DEFINED_CONSTANT` . Są one uwzględnione we `DefinedConstants` właściwości. Wyrażenie regularne jest używane do dopasowania dokładnej stałej na liście rozdzielanej średnikami.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Zobacz też

- [Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When, element (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
