---
title: Wybierz element (MSBuild) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634477"
---
# <a name="choose-element-msbuild"></a>Wybierz element (MSBuild)

Ocenia elementy podrzędne, aby `ItemGroup` wybrać jeden `PropertyGroup` zestaw elementów i/lub elementów do oceny.

 \<> projektu \<wybierz \<>, kiedy> \<wybierz> ... \<W przeciwnym razie \<> Wybierz> ...

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
|[Inaczej](../msbuild/otherwise-element-msbuild.md)|Element opcjonalny.<br /><br /> Określa `PropertyGroup` blok kodu i `ItemGroup` elementy do oceny, `When` czy warunki `false`wszystkich elementów są obliczane na . Może być zero `Otherwise` lub jeden `Choose` element w elemencie i musi być ostatnim elementem.|
|[Kiedy](../msbuild/when-element-msbuild.md)|Element wymagany.<br /><br /> Określa możliwy blok kodu dla `Choose` elementu do wybrania. Może istnieć jeden `When` lub `Choose` więcej elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Inaczej](../msbuild/otherwise-element-msbuild.md) | Określa blok kodu do wykonania, jeśli `When` warunki wszystkich `false`elementów są obliczane na . |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Kiedy](../msbuild/when-element-msbuild.md) | Określa możliwy blok kodu dla `Choose` elementu do wybrania. |

## <a name="remarks"></a>Uwagi

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
