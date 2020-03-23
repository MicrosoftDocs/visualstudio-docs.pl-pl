---
title: Element OnError (MSBuild) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633086"
---
# <a name="onerror-element-msbuild"></a>Element OnError (MSBuild)

Powoduje, że jeden lub więcej `ContinueOnError` obiektów `false` docelowych do wykonania, jeśli atrybut jest dla zadania nie powiodło się.

 \<> \<docelowe>> projektu \<OnError

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
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Obiekty docelowe do wykonania w przypadku niepowodzenia zadania. Oddziel wiele celów średnikami. Wiele obiektów docelowych są wykonywane w określonej kolejności.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Obiekt docelowy](../msbuild/target-element-msbuild.md) | Element kontenera dla zadań MSBuild. |

## <a name="remarks"></a>Uwagi

 MSBuild wykonuje `OnError` element, jeśli `Target` jedno z zadań elementu `ContinueOnError` kończy się `ErrorAndStop` niepowodzeniem z atrybutem ustawionym na (lub `false`). Gdy zadanie zakończy się niepowodzeniem, obiekty docelowe określone w atrybucie `ExecuteTargets` są wykonywane. Jeśli istnieje więcej `OnError` niż jeden element `OnError` w docelowych, elementy są wykonywane sekwencyjnie, gdy zadanie nie powiedzie się.

 Aby uzyskać `ContinueOnError` informacje o tym atrybucie, zobacz [Task element (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o celach, zobacz [Cele](../msbuild/msbuild-targets.md).

## <a name="example"></a>Przykład

 Poniższy kod wykonuje `TaskOne` `TaskTwo` i zadania. Jeśli `TaskOne` nie powiedzie się, `OnError` MSBuild `OtherTarget` ocenia element i wykonuje obiekt docelowy.

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
- [Cele](../msbuild/msbuild-targets.md)
