---
title: Konstrukcje warunkowe MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d28819ddb7b6b5e860e885803f8037f104e9f645
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54769016"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] udostępnia mechanizm dla dowolnego / lub przetwarzania za pomocą [wybierz](../msbuild/choose-element-msbuild.md), [podczas](../msbuild/when-element-msbuild.md), i [przeciwnym](../msbuild/otherwise-element-msbuild.md) elementów.  
  
## <a name="using-the-choose-element"></a>Za pomocą Choose — Element  
 `Choose` Element zawiera szereg `When` elementów za pomocą `Condition` atrybuty, które są badane w kolejności od góry do dołu, aż jedną daje w wyniku `true`. Jeśli istnieje więcej niż jedna `When` daje w wyniku element `true`, tylko pierwszy z nich jest używany. `Otherwise` Elementu, jeśli jest obecny, zostaną ocenione Jeśli żadnego warunku na `When` daje w wyniku element `true`.  
  
 `Choose` elementy mogą być używane jako elementy podrzędne `Project`, `When` i `Otherwise` elementów. `When` i `Otherwise` może mieć elementów `ItemGroup`, `PropertyGroup`, lub `Choose` elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Choose` i `When` elementów dla dowolnego / lub przetwarzania. Właściwości i elementy projektu są ustawiane w zależności od wartości `Configuration` właściwości.  
  
```  
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
 [Choose — Element (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Gdy Element (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise — Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
