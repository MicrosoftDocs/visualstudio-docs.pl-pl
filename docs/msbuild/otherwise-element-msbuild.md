---
title: Otherwise — element (MSBuild) | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa elementu Otherwise, aby określić blok kodu do wykonania, gdy i tylko wtedy, gdy spełnione są warunki All, gdy elementy mają wartość false.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 05cc8820f073ea8c620e4331c180ee1ddbfc2b65
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048937"
---
# <a name="otherwise-element-msbuild"></a>Otherwise — element (MSBuild)

Określa blok kodu do wykonania, gdy i tylko wtedy, gdy warunki wszystkich `When` elementów są oceniane do `false` .

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

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

### <a name="attributes"></a>Atrybuty

 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania. Element może zawierać zero lub więcej `Choose` elementów `Otherwise` .|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Element może zawierać zero lub więcej `ItemGroup` elementów `Otherwise` .|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [Właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Element może zawierać zero lub więcej `PropertyGroup` elementów `Otherwise` .|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania.|

## <a name="remarks"></a>Uwagi

 Element może zawierać tylko jeden `Otherwise` element `Choose` i musi być ostatnim elementem.

 `Choose`Elementy, `When` , i `Otherwise` są używane razem, aby zapewnić możliwość wyboru jednej sekcji kodu do wykonania z wielu możliwych wariantów. Aby uzyskać więcej informacji, zobacz [konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Przykład

 Następujący projekt używa elementu, `Choose` Aby wybrać zestaw wartości właściwości w elementach, które `When` mają zostać ustawione. Jeśli `Condition` atrybuty obu `When` elementów są oceniane do `false` , wartości właściwości w `Otherwise` elemencie są ustawiane.

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

## <a name="see-also"></a>Zobacz też

- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
