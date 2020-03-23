---
title: Element wyjściowy (MSBuild) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633034"
---
# <a name="output-element-msbuild"></a>Element wyjściowy (MSBuild)

Przechowuje wartości wyjściowe zadania w elementach i właściwościach.

 \<>> \< \< \<> zadań> zadań>> projektu

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
|`PropertyName`|Wymagany jest `PropertyName` `ItemName` atrybut lub atrybut.<br /><br /> Właściwość, która odbiera wartość parametru wyjściowego zadania. Projekt może następnie odwoływać się\<do właściwości ze składnią $( PropertyName>). Ta nazwa właściwości może być nową nazwą właściwości lub nazwą, która jest już zdefiniowana w projekcie.<br /><br /> Ten atrybut nie może `ItemName` być używany, jeśli jest również używany.|
|`ItemName`|Wymagany jest `PropertyName` `ItemName` atrybut lub atrybut.<br /><br /> Element, który otrzymuje wartość parametru wyjściowego zadania. Projekt może następnie odwoływać się\<do elementu ze składnią @( ItemName>). Nazwa elementu może być nową nazwą elementu lub nazwą, która jest już zdefiniowana w projekcie. Gdy nazwa elementu jest istniejącym elementem, wartości parametrów wyjściowych są dodawane do istniejącego elementu. <br /><br /> Ten atrybut nie może `PropertyName` być używany, jeśli jest również używany.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Zadanie](../msbuild/task-element-msbuild.md) | Tworzy i wykonuje wystąpienie zadania MSBuild. |

## <a name="example"></a>Przykład

 Poniższy przykład kodu `Csc` pokazuje zadanie wykonywane `Target` wewnątrz elementu. Elementy i właściwości przekazywane do parametrów zadania są zadeklarowane poza zakresem tego przykładu. Wartość z parametru `OutputAssembly` output jest `FinalAssemblyName` przechowywana w elemencie, a wartość z parametru `BuildSucceeded` output jest przechowywana we `BuildWorked` właściwości. Aby uzyskać więcej informacji, zobacz [Zadania](../msbuild/msbuild-tasks.md).

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
