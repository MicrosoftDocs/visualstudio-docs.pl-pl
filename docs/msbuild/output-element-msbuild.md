---
title: OUTPUT — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb8f7a02183fe34dcd882e23ee7bf8b90f9a2cc6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617304"
---
# <a name="output-element-msbuild"></a>OUTPUT — element (MSBuild)
Zadanie magazyny danych wyjściowych wartości elementów i właściwości.

 \<Project> \<Target> \<Task> \<Output>

## <a name="syntax"></a>Składnia

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`TaskParameter`|Atrybut wymagany.<br /><br /> Nazwa zadania przez parametr danych wyjściowych.|
|`PropertyName`|Albo `PropertyName` lub `ItemName` atrybut jest wymagany.<br /><br /> Właściwość, która odbiera zadanie danych wyjściowych wartość parametru. Projekt może się wtedy odwoływać slajdu $(\<PropertyName >) składni. Nazwa tej właściwości może być nowej nazwy właściwości lub nazwą, która jest już zdefiniowana w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `ItemName` jest również używany.|
|`ItemName`|Albo `PropertyName` lub `ItemName` atrybut jest wymagany.<br /><br /> Element, który odbiera zadanie danych wyjściowych wartość parametru. Projekt może się wtedy odwoływać elementu z @(\<nazwa elementu >) składni. Nazwa elementu może być nazwę nowego elementu lub nazwą, która jest już zdefiniowana w projekcie. Jeśli nazwa elementu jest istniejący element, wartości parametrów wyjściowych są dodawane do istniejącego elementu. <br /><br /> Nie można użyć tego atrybutu, jeśli `PropertyName` jest również używany.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Zadanie](../msbuild/task-element-msbuild.md) | Tworzy i uruchamia wystąpienie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. |

## <a name="example"></a>Przykład
 Poniższy kod przedstawia przykład `Csc` zadanie wykonywane wewnątrz `Target` elementu. Elementów i właściwości przekazywane do parametrów zadania są zadeklarowane poza zakresem tego przykładu. Wartość parametru wyjściowego `OutputAssembly` są przechowywane w `FinalAssemblyName` elementu, a wartość parametru wyjściowego `BuildSucceeded` są przechowywane w `BuildWorked` właściwości. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
