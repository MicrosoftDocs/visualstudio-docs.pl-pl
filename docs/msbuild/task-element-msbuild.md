---
title: Element Task elementu docelowego (MSBuild) | Microsoft Docs
description: Dowiedz się więcej o elemencie Task Target programu MSBuild, który tworzy i wykonuje wystąpienie zadania programu MSBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 58ac6b02424da40ba1130d8a1b549886c9efd718
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047964"
---
# <a name="task-element-of-target-msbuild"></a>Element Task elementu docelowego (MSBuild)

Tworzy i wykonuje wystąpienie zadania programu MSBuild. Nazwa elementu jest określana na podstawie nazwy tworzonego zadania.

 \<Project> \<Target>

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
|`Condition`|Atrybut opcjonalny. Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Atrybut opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true** . Gdy zadanie się nie powiedzie, kolejne zadania w elemencie [Target](../msbuild/target-element-msbuild.md) i Build są nadal wykonywane, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue** . Gdy zadanie nie powiedzie się, kolejne zadania w `Target` elemencie i kompilacja będą nadal wykonywane, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (wartość domyślna). Jeśli zadanie nie powiedzie się, pozostałe zadania w `Target` elemencie i kompilacja nie są wykonywane, a cały `Target` element i kompilacja są uważane za zakończone niepowodzeniem.<br /><br /> Wersje .NET Framework przed 4,5 obsługiwane tylko `true` `false` wartości i.<br /><br /> Aby uzyskać więcej informacji, zobacz [How to: ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Wymagane, jeśli Klasa zadania zawiera jedną lub więcej właściwości, które są oznaczone `[Required]` atrybutem.<br /><br /> Zdefiniowany przez użytkownika parametr zadania, który zawiera wartość parametru jako wartość. W elemencie może być dowolna liczba parametrów `Task` z każdym mapowaniem atrybutu na Właściwość platformy .NET w klasie zadań.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Dane wyjściowe](../msbuild/output-element-msbuild.md)|Przechowuje dane wyjściowe z zadania w pliku projektu. W zadaniu może istnieć zero lub więcej `Output` elementów.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Obiektów](../msbuild/target-element-msbuild.md) | Element kontenera zadań programu MSBuild. |

## <a name="remarks"></a>Uwagi

 `Task`Element w pliku projektu MSBuild tworzy wystąpienie zadania, ustawia jego właściwości i wykonuje je. `Output`Element przechowuje parametry wyjściowe we właściwościach lub elementach, które mają być używane w innym miejscu w pliku projektu.

 Jeśli w elemencie nadrzędnym zadania znajdują się jakiekolwiek elementy z [błędami](../msbuild/onerror-element-msbuild.md) `Target` , będą one nadal oceniane, jeśli zadanie zakończy się niepowodzeniem i `ContinueOnError` ma wartość `false` . Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu tworzy wystąpienie klasy [zadania CSC](../msbuild/csc-task.md) , ustawia sześć właściwości i wykonuje zadanie. Po wykonaniu wartość `OutputAssembly` właściwości obiektu jest umieszczana w liście elementów o nazwie `FinalAssemblyName` .

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
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
