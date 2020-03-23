---
title: Zadania MSBuild | Dokumenty firmy Microsoft
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
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633138"
---
# <a name="msbuild-tasks"></a>zadania programu MSBuild

Platforma kompilacji wymaga możliwości wykonywania dowolnej liczby akcji podczas procesu kompilacji. MSBuild używa *zadań* do wykonywania tych akcji. Zadanie jest jednostką kodu wykonywalnego używanego przez MSBuild do wykonywania operacji kompilacji niepodzielnej.

## <a name="task-logic"></a>Logika zadania

 Format pliku projektu MSBuild XML nie może w pełni wykonać operacji kompilacji na własną rękę, więc logika zadania musi być zaimplementowana poza plikiem projektu.

 Logika wykonywania zadania jest implementowana jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> <xref:Microsoft.Build.Framework> interfejs, który jest zdefiniowany w obszarze nazw.

 Klasa zadań definiuje również parametry wejściowe i wyjściowe dostępne dla zadania w pliku projektu. Wszystkie publiczne settable niestatyczne właściwości nieabstrakcyjne udostępniane przez klasę zadań można podać wartości w pliku projektu, umieszczając odpowiedni atrybut o tej samej nazwie na [Task](../msbuild/task-element-msbuild.md) element i ustawienie jego wartości, jak pokazano w przykładach w dalszej części tego artykułu.

 Można napisać własne zadanie, tworząc klasę zarządzaną, <xref:Microsoft.Build.Framework.ITask> która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [Pisanie zadań](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Wykonywanie zadania z pliku projektu

 Przed wykonaniem zadania w pliku projektu należy najpierw zamapować typ w zestawie, który implementuje zadanie do nazwy zadania z [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Dzięki temu MSBuild wiedzieć, gdzie szukać logiki wykonywania zadania, gdy znajdzie go w pliku projektu.

 Aby wykonać zadanie w pliku projektu MSBuild, należy utworzyć element o nazwie `Target` zadania jako element podrzędny elementu. Jeśli zadanie akceptuje parametry, są one przekazywane jako atrybuty elementu.

 Listy elementów MSBuild i właściwości mogą służyć jako parametry. Na przykład następujący kod `MakeDir` wywołuje zadanie i ustawia `Directories` wartość `MakeDir` właściwości obiektu równą `BuildDir` wartości właściwości:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Zadania mogą również zwracać informacje do pliku projektu, które mogą być przechowywane w elementach lub właściwościach do późniejszego użycia. Na przykład następujący kod `Copy` wywołuje zadanie i przechowuje informacje z właściwości wyjściowej `CopiedFiles` na `SuccessfullyCopiedFiles` liście towarów.

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

 MSBuild jest dostarczany z wieloma zadaniami, takimi jak [Kopiuj](../msbuild/copy-task.md), który kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), który tworzy katalogi, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego języka C#. Aby uzyskać pełną listę dostępnych zadań i informacji o użytkowaniu, zobacz [Odwołanie do zadania](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Zastępowane zadania

 MSBuild wyszukuje zadania w kilku lokalizacjach. Pierwsza lokalizacja znajduje się w plikach z rozszerzeniem *. OverrideTasks* przechowywane w katalogach .NET Framework. Zadania w tych plikach zastępują inne zadania o tych samych nazwach, w tym zadania w pliku projektu. Druga lokalizacja znajduje się w plikach z rozszerzeniem *. Zadania* w katalogach platformy .NET Framework. Jeśli zadanie nie zostanie znalezione w żadnej z tych lokalizacji, zadanie w pliku projektu jest używane.

## <a name="see-also"></a>Zobacz też

- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Pisanie zadań](../msbuild/task-writing.md)
- [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
