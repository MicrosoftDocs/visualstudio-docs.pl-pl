---
title: Konstrukcje warunkowe MSBuild | Microsoft Docs
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
ms.openlocfilehash: b7b22f63d5d3d6e0b1f7789561029bbfbfb4cdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143767"
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zapewnia mechanizm do przetwarzania za pomocą elementów [Choose](../msbuild/choose-element-msbuild.md), [when](../msbuild/when-element-msbuild.md)i [Otherwise](../msbuild/otherwise-element-msbuild.md) .  
  
## <a name="using-the-choose-element"></a>Korzystanie z elementu wybierz  
 `Choose`Element zawiera serię `When` elementów z `Condition` atrybutami, które są testowane w kolejności od góry do dołu do momentu, w którym ma zostać obliczona wartość `true` . Jeśli więcej niż jeden `When` element ma wartość `true` , zostanie użyta tylko pierwsza z nich. `Otherwise`Element, jeśli jest obecny, będzie oceniany, jeśli nie ma żadnego warunku dla `When` elementu `true` .  
  
 `Choose` elementy mogą być używane jako elementy podrzędne elementów `Project` `When` i `Otherwise` . `When``Otherwise`elementami i mogą być `ItemGroup` `PropertyGroup` `Choose` elementy podrzędne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Choose` `When` elementów i dla obu/lub do przetwarzania. Właściwości i elementy projektu są ustawiane w zależności od wartości `Configuration` właściwości.  
  
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
 [Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When, element (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise — element (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
