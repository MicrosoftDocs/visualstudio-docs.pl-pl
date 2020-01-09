---
title: Otherwise — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 460a02b3e2115c7ccb91258ffe960668e64fb363
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594845"
---
# <a name="otherwise-element-msbuild"></a>Otherwise — element (MSBuild)
Określa blok kodu do wykonania, gdy i tylko wtedy, gdy warunki wszystkich `When` elementów są szacowane do `false`.

 \<> projektu \<wybierz > \<, gdy > \<wybierz >... \<w przeciwnym razie > \<wybierz >...

## <a name="syntax"></a>Składnia

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Następnie](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania. Element `Otherwise` może mieć co najmniej zero elementów `Choose`.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Element `Otherwise` może mieć co najmniej zero elementów `ItemGroup`.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [Właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Element `Otherwise` może mieć co najmniej zero elementów `PropertyGroup`.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Następnie](../msbuild/choose-element-msbuild.md)|Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania.|

## <a name="remarks"></a>Uwagi
 Może istnieć tylko jeden element `Otherwise` w elemencie `Choose` i musi być ostatnim elementem.

 Elementy `Choose`, `When`i `Otherwise` są używane razem, aby zapewnić możliwość wybrania jednej sekcji kodu do wykonania z wielu możliwych wariantów. Aby uzyskać więcej informacji, zobacz [konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Przykład
 Następujący projekt używa elementu `Choose`, aby wybrać zestaw wartości właściwości w elementach `When` do ustawienia. Jeśli `Condition` atrybuty obu elementów `When` oblicza do `false`, wartości właściwości w elemencie `Otherwise` są ustawiane.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
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
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
        </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Zobacz także
- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
