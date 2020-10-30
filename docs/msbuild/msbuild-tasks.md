---
title: Zadania programu MSBuild | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadań lub jednostek kodu wykonywalnego, które wykonują niepodzielne operacje kompilacji podczas procesu kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76b359eebe0f4a22bef3ff6c6742a5134aa4520c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049048"
---
# <a name="msbuild-tasks"></a>zadania programu MSBuild

Platforma kompilacji musi mieć możliwość wykonywania dowolnej liczby akcji w procesie kompilacji. Program MSBuild używa *zadań* do wykonania tych działań. Zadanie jest jednostką kodu wykonywalnego używanego przez program MSBuild do wykonywania niepodzielnych operacji kompilacji.

## <a name="task-logic"></a>Logika zadań

 Format pliku projektu XML programu MSBuild nie może w pełni wykonywać operacji kompilacji, więc logika zadań musi być implementowana poza plikiem projektu.

 Logika wykonywania zadania jest implementowana jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w <xref:Microsoft.Build.Framework> przestrzeni nazw.

 Klasa Task definiuje również parametry wejściowe i wyjściowe dostępne dla zadania w pliku projektu. Wszystkie publiczne, niestatyczne właściwości nieabstrakcyjne udostępniane przez klasę zadania mogą mieć wartości w pliku projektu przez umieszczenie odpowiedniego atrybutu o tej samej nazwie w elemencie [Task](../msbuild/task-element-msbuild.md) i ustawienie jego wartości, jak pokazano w przykładach w dalszej części tego artykułu.

 Można napisać własne zadanie, tworząc zarządzaną klasę, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji, zobacz [Zapisywanie zadań](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Wykonywanie zadania z pliku projektu

 Przed wykonaniem zadania w pliku projektu należy najpierw zmapować typ w zestawie, który implementuje zadanie do nazwy zadania z elementem [UsingTask](../msbuild/usingtask-element-msbuild.md) . Dzięki temu program MSBuild wie, gdzie szukać logiki wykonywania zadania po znalezieniu go w pliku projektu.

 Aby wykonać zadanie w pliku projektu programu MSBuild, Utwórz element o nazwie zadania jako element podrzędny `Target` elementu. Jeśli zadanie przyjmuje parametry, są one przenoszone jako atrybuty elementu.

 Listy i właściwości elementów programu MSBuild mogą służyć jako parametry. Na przykład, poniższy kod wywołuje `MakeDir` zadanie i ustawia wartość `Directories` właściwości `MakeDir` obiektu równą wartości `BuildDir` Właściwości:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Zadania mogą także zwracać informacje do pliku projektu, które mogą być przechowywane w elementach lub właściwościach w celu późniejszego użycia. Na przykład poniższy kod wywołuje `Copy` zadanie i zapisuje informacje z `CopiedFiles` Właściwości Output na `SuccessfullyCopiedFiles` liście elementów.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Uwzględnione zadania

 Program MSBuild jest dostarczany z wieloma zadaniami, takimi jak [copy](../msbuild/copy-task.md), które kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), tworzące katalogi i [CSC](../msbuild/csc-task.md), które kompilują pliki kodu źródłowego C#. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Zastąpione zadania

 Program MSBuild szuka zadań w kilku lokalizacjach. Pierwsza lokalizacja znajduje się w plikach z rozszerzeniem *. OverrideTasks* przechowywanych w katalogach .NET Framework. Zadania w tych plikach zastępują wszystkie inne zadania o tych samych nazwach, w tym zadania w pliku projektu. Druga lokalizacja znajduje się w plikach z rozszerzeniem *. Zadania* w katalogach .NET Framework. Jeśli zadanie nie zostanie odnalezione w żadnej z tych lokalizacji, zostanie użyte zadanie w pliku projektu.

## <a name="see-also"></a>Zobacz też

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Pisanie zadań](../msbuild/task-writing.md)
- [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
