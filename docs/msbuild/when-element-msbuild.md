---
title: Gdy element (MSBuild) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630928"
---
# <a name="when-element-msbuild"></a>Gdy element (MSBuild)

Określa możliwy blok kodu dla `Choose` elementu do wybrania.

 \<> projektu \<wybierz \<>, kiedy> \<wybierz> ... \<W przeciwnym razie \<> Wybierz> ...

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
|Warunek|Atrybut wymagany.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Wybierz ikonę](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Ocenia elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania. Może istnieć zero `Choose` lub `When` więcej elementów w elemencie.|
|[Itemgroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [elementu](../msbuild/item-element-msbuild.md) zdefiniowanego przez użytkownika. Może istnieć zero `ItemGroup` lub `When` więcej elementów w elemencie.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw elementów [właściwości](../msbuild/property-element-msbuild.md) zdefiniowanych przez użytkownika. Może istnieć zero `PropertyGroup` lub `When` więcej elementów w elemencie.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Wybierz element (MSBuild)](../msbuild/choose-element-msbuild.md)|Ocenia elementy podrzędne, aby wybrać jedną sekcję kodu do wykonania.|

## <a name="remarks"></a>Uwagi

 Jeśli `Condition` atrybut ma wartość true, `ItemGroup` element `PropertyGroup` podrzędny `When` i elementy elementu `When` są wykonywane i wszystkie kolejne elementy są pomijane.

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
