---
title: OnError — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2ddf970225d96291f76935838a743ba358eff0f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594880"
---
# <a name="onerror-element-msbuild"></a>OnError — element (MSBuild)
Powoduje, że co najmniej jeden obiekt docelowy jest wykonywany, jeśli atrybut `ContinueOnError` jest `false` dla zadania zakończonego niepowodzeniem.

 \<Project > \<Target > \<OnError >

## <a name="syntax"></a>Składnia

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Elementy docelowe do wykonania, jeśli zadanie zakończy się niepowodzeniem. Rozdziel wiele obiektów docelowych średnikami. Wiele obiektów docelowych jest wykonywanych w określonej kolejności.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Cel](../msbuild/target-element-msbuild.md) | Element kontenera dla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań. |

## <a name="remarks"></a>Uwagi
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykonuje `OnError` elementu, jeśli jeden z zadań elementu `Target` nie powiedzie się z atrybutem `ContinueOnError` ustawionym na `ErrorAndStop` (lub `false`). Gdy zadanie nie powiedzie się, obiekty docelowe określone w atrybucie `ExecuteTargets` są wykonywane. Jeśli obiekt docelowy zawiera więcej niż jeden element `OnError`, elementy `OnError` są wykonywane sekwencyjnie, gdy zadanie zakończy się niepowodzeniem.

 Aby uzyskać informacje o atrybucie `ContinueOnError`, zobacz [element Task (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o celach, zobacz [targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Przykład
 Poniższy kod wykonuje zadania `TaskOne` i `TaskTwo`. Jeśli `TaskOne` nie powiedzie się, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] oblicza element `OnError` i wykonuje obiekt docelowy `OtherTarget`.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Docelowe elementy](../msbuild/msbuild-targets.md)
