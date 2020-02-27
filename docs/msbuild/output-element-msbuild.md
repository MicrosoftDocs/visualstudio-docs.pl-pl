---
title: Output — element (MSBuild) | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633034"
---
# <a name="output-element-msbuild"></a>Output — element (MSBuild)

Przechowuje wartości wyjściowe zadania w elementach i we właściwościach.

 \<Project > \<Target > \<zadanie > \<danych wyjściowych >

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
|`TaskParameter`|Atrybut wymagany.<br /><br /> Nazwa parametru wyjściowego zadania.|
|`PropertyName`|Wymagany jest atrybut `PropertyName` lub `ItemName`.<br /><br /> Właściwość, która otrzymuje wartość parametru wyjściowego zadania. Projekt może następnie odwołać się do właściwości przy użyciu składni $ (\<PropertyName >). Ta nazwa właściwości może być nową nazwą właściwości lub nazwą, która jest już zdefiniowana w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `ItemName` jest również używany.|
|`ItemName`|Wymagany jest atrybut `PropertyName` lub `ItemName`.<br /><br /> Element, który otrzymuje wartość parametru wyjściowego zadania. Projekt może odwoływać się do elementu za pomocą składni @ (\<itemName >). Nazwa elementu może być nazwą nowego elementu lub nazwą, która jest już zdefiniowana w projekcie. Gdy nazwa elementu jest istniejącym elementem, wartości parametrów wyjściowych są dodawane do istniejącego elementu. <br /><br /> Nie można użyć tego atrybutu, jeśli `PropertyName` jest również używany.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Zadanie podrzędne](../msbuild/task-element-msbuild.md) | Tworzy i wykonuje wystąpienie zadania programu MSBuild. |

## <a name="example"></a>Przykład

 Poniższy przykład kodu pokazuje zadanie `Csc` wykonywane wewnątrz elementu `Target`. Elementy i właściwości przesłane do parametrów zadania są zadeklarowane poza zakresem tego przykładu. Wartość z `OutputAssembly` parametru wyjściowego jest przechowywana w elemencie `FinalAssemblyName`, a wartość z parametru wyjściowego `BuildSucceeded` jest przechowywana we właściwości `BuildWorked`. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
