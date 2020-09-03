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
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633086"
---
# <a name="onerror-element-msbuild"></a>OnError — element (MSBuild)

Powoduje, że co najmniej jeden obiekt docelowy jest wykonywany, jeśli `ContinueOnError` atrybut dotyczy `false` zadania zakończonego niepowodzeniem.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Składnia

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Elementy docelowe do wykonania, jeśli zadanie zakończy się niepowodzeniem. Rozdziel wiele obiektów docelowych średnikami. Wiele obiektów docelowych jest wykonywanych w określonej kolejności.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Obiektów](../msbuild/target-element-msbuild.md) | Element kontenera zadań programu MSBuild. |

## <a name="remarks"></a>Uwagi

 MSBuild wykonuje `OnError` element, jeśli jeden z `Target` zadań elementu nie powiedzie się z `ContinueOnError` atrybutem ustawionym na `ErrorAndStop` (lub `false` ). Gdy zadanie nie powiedzie się, obiekty docelowe określone w `ExecuteTargets` atrybucie są wykonywane. Jeśli obiekt docelowy zawiera więcej niż jeden `OnError` element, `OnError` elementy są wykonywane sekwencyjnie, gdy zadanie zakończy się niepowodzeniem.

 Aby uzyskać informacje na temat `ContinueOnError` atrybutu, zobacz [element Task (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o celach, zobacz [targets](../msbuild/msbuild-targets.md).

## <a name="example"></a>Przykład

 Poniższy kod wykonuje `TaskOne` `TaskTwo` zadania i. W przypadku `TaskOne` niepowodzenia program MSBuild ocenia `OnError` element i wykonuje element `OtherTarget` docelowy.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
