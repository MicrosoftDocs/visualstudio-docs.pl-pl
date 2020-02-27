---
title: Wybierz element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4f699b4ffc9372af0c803d094390544932d652b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634477"
---
# <a name="choose-element-msbuild"></a>Choose — element (MSBuild)

Oblicza elementy podrzędne w celu wybrania jednego zestawu `ItemGroup` elementów i/lub `PropertyGroup` elementów do obliczenia.

 \<> projektu \<wybierz > \<, gdy > \<wybierz >... \<w przeciwnym razie > \<wybierz >...

## <a name="syntax"></a>Składnia

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

 Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Przypadku](../msbuild/otherwise-element-msbuild.md)|Element opcjonalny.<br /><br /> Określa blok kodu `PropertyGroup` i `ItemGroup` elementów, które mają być oceniane w przypadku, gdy warunki wszystkich `When`ych elementów są szacowane do `false`. Może istnieć zero lub jeden `Otherwise` elementów w elemencie `Choose` i musi być ostatnim elementem.|
|[Czasie](../msbuild/when-element-msbuild.md)|Element wymagany.<br /><br /> Określa możliwy blok kodu dla elementu `Choose` do wybrania. Element `Choose` może zawierać co najmniej jeden element `When`.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Przypadku](../msbuild/otherwise-element-msbuild.md) | Określa blok kodu do wykonania, jeśli warunki wszystkich `When` elementów mają być `false`ne. |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Czasie](../msbuild/when-element-msbuild.md) | Określa możliwy blok kodu dla elementu `Choose` do wybrania. |

## <a name="remarks"></a>Uwagi

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
