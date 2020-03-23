---
title: Element zadania obiektu docelowego (MSBuild) | Dokumenty firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a4ec2203430045c083b46b2eea8d3e884a4b794
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263178"
---
# <a name="task-element-of-target-msbuild"></a>Element zadania obiektu docelowego (MSBuild)

Tworzy i wykonuje wystąpienie zadania MSBuild. Nazwa elementu jest określana przez nazwę tworzonego zadania.

 \<> \<docelowe> projektu

## <a name="syntax"></a>Składnia

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Condition`|Atrybut opcjonalny. Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Atrybut opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndKontynuuj** lub **prawda**. Gdy zadanie nie powiedzie się, kolejne zadania w [target](../msbuild/target-element-msbuild.md) element i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Gdy zadanie nie powiedzie `Target` się, kolejne zadania w elemencie i kompilacji nadal wykonywać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (domyślnie). Gdy zadanie zakończy się niepowodzeniem, pozostałe zadania w `Target` elemencie `Target` i kompilacji nie są wykonywane, a cały element i kompilacja jest uważany za nie powiodło się.<br /><br /> Wersje programu .NET Framework przed 4.5 `true` `false` obsługiwane tylko i wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [Jak: Ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Wymagane, jeśli klasa zadań zawiera jedną lub więcej `[Required]` właściwości oznaczonych atrybutem.<br /><br /> Zdefiniowany przez użytkownika parametr zadania, który zawiera wartość parametru jako jego wartość. Może istnieć dowolna `Task` liczba parametrów w elemencie, z każdego mapowania atrybutu do właściwości .NET w klasie zadań.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Wyjście](../msbuild/output-element-msbuild.md)|Przechowuje dane wyjściowe z zadania w pliku projektu. W zadaniu może `Output` być zero lub więcej elementów.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Obiekt docelowy](../msbuild/target-element-msbuild.md) | Element kontenera dla zadań MSBuild. |

## <a name="remarks"></a>Uwagi

 Element `Task` w pliku projektu MSBuild tworzy wystąpienie zadania, ustawia właściwości na nim i wykonuje je. Element `Output` przechowuje parametry wyjściowe we właściwościach lub elementach, które mają być używane w innym miejscu w pliku projektu.

 Jeśli w elemencie `Target` nadrzędnym zadania znajdują się elementy [OnError,](../msbuild/onerror-element-msbuild.md) będą one nadal `false`oceniane, jeśli zadanie zakończy się niepowodzeniem i `ContinueOnError` mają wartość . Aby uzyskać więcej informacji na temat zadań, zobacz [Zadania](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu tworzy wystąpienie klasy [zadań Csc,](../msbuild/csc-task.md) ustawia sześć właściwości i wykonuje zadanie. Po wykonaniu wartość `OutputAssembly` właściwości obiektu jest umieszczana na liście `FinalAssemblyName`elementów o nazwie .

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
