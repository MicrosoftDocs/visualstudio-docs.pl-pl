---
title: W przeciwnym razie element (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 384886ad4292661648f5cbfde1a583d8d75b1c03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633047"
---
# <a name="otherwise-element-msbuild"></a>W przeciwnym razie element (MSBuild)

Określa blok kodu do wykonania wtedy i tylko `When` wtedy, `false`gdy warunki wszystkich elementów oceniają .

 \<> projektu \<wybierz \<>, kiedy> \<wybierz> ... \<W przeciwnym razie \<> Wybierz> ...

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
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Ocenia elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania. Może istnieć zero `Choose` lub `Otherwise` więcej elementów w elemencie.|
|[Itemgroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [elementu](../msbuild/item-element-msbuild.md) zdefiniowanego przez użytkownika. Może istnieć zero `ItemGroup` lub `Otherwise` więcej elementów w elemencie.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Może istnieć zero `PropertyGroup` lub `Otherwise` więcej elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Ocenia elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania.|

## <a name="remarks"></a>Uwagi

 Może istnieć `Otherwise` tylko jeden `Choose` element w elemencie i musi być ostatnim elementem.

 `When` `Otherwise` , `Choose`i elementy są używane razem, aby zapewnić sposób, aby wybrać jedną sekcję kodu do wykonania z wielu możliwych alternatyw. Aby uzyskać więcej informacji, zobacz [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Przykład

 W poniższym `Choose` projekcie używa elementu, aby wybrać, `When` który zestaw wartości właściwości w elementach do ustawionego. Jeśli `Condition` atrybuty `When` obu elementów ocenić `false`do `Otherwise` , wartości właściwości w elemencie są ustawione.

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
