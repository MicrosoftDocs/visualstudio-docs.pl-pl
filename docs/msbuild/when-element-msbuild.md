---
title: When — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcb9404b8c68171f0695b33c285582f5e4c5b4ec
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630928"
---
# <a name="when-element-msbuild"></a>When, element (MSBuild)

Określa możliwy blok kodu dla elementu `Choose` do wybrania.

 \<> projektu \<wybierz > \<, gdy > \<wybierz >... \<w przeciwnym razie > \<wybierz >...

## <a name="syntax"></a>Składnia

```xml
<When Condition="'StringA'=='StringB'">
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</When>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Atrybut wymagany.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Następnie](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania. Element `When` może mieć co najmniej zero elementów `Choose`.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw [elementów zdefiniowanych przez](../msbuild/item-element-msbuild.md) użytkownika. Element `When` może mieć co najmniej zero elementów `ItemGroup`.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [Właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Element `When` może mieć co najmniej zero elementów `PropertyGroup`.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Choose — element (MSBuild)](../msbuild/choose-element-msbuild.md)|Oblicza elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania.|

## <a name="remarks"></a>Uwagi

 Jeśli atrybut `Condition` ma wartość true, są wykonywane elementy podrzędne `ItemGroup` i `PropertyGroup` elementu `When`, a wszystkie kolejne elementy `When` są pomijane.

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

## <a name="see-also"></a>Zobacz też

- [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
