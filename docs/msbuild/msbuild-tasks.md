---
title: Zadania programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: 3a6bc01ee1f692a4da0cf1921de757236651a177
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593811"
---
# <a name="msbuild-tasks"></a>zadania programu MSBuild
Platforma kompilacji musi mieć możliwość wykonywania dowolnej liczby akcji w procesie kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa *zadań* do wykonania tych działań. Zadanie jest jednostką kodu wykonywalnego używaną przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania niepodzielnych operacji kompilacji.

## <a name="task-logic"></a>Logika zadań
 Format pliku projektu XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie może w pełni wykonywać operacji kompilacji, więc logika zadań musi być implementowana poza plikiem projektu.

 Logika wykonywania zadania jest implementowana jako Klasa platformy .NET implementująca interfejs <xref:Microsoft.Build.Framework.ITask>, który jest zdefiniowany w przestrzeni nazw <xref:Microsoft.Build.Framework>.

 Klasa Task definiuje również parametry wejściowe i wyjściowe dostępne dla zadania w pliku projektu. Wszystkie publiczne, niestatyczne właściwości nieabstrakcyjne uwidocznione przez klasę zadania mogą być dostępne w pliku projektu przez umieszczenie odpowiedniego atrybutu o tej samej nazwie w elemencie [Task](../msbuild/task-element-msbuild.md) .

 Można napisać własne zadanie, tworząc zarządzaną klasę, która implementuje interfejs <xref:Microsoft.Build.Framework.ITask>. Aby uzyskać więcej informacji, zobacz [Zapisywanie zadań](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Wykonywanie zadania z pliku projektu
 Przed wykonaniem zadania w pliku projektu należy najpierw zmapować typ w zestawie, który implementuje zadanie do nazwy zadania z elementem [UsingTask](../msbuild/usingtask-element-msbuild.md) . Pozwala to [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wiedzieć, gdzie szukać logiki wykonywania zadania po jego znalezieniu w pliku projektu.

 Aby wykonać zadanie w pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], Utwórz element o nazwie zadania jako element podrzędny elementu `Target`. Jeśli zadanie przyjmuje parametry, są one przenoszone jako atrybuty elementu.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] listy elementów i właściwości mogą być używane jako parametry. Na przykład poniższy kod wywołuje zadanie `MakeDir` i ustawia wartość właściwości `Directories` obiektu `MakeDir` równą wartości właściwości `BuildDir` zadeklarowanej w poprzednim przykładzie.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Zadania mogą także zwracać informacje do pliku projektu, które mogą być przechowywane w elementach lub właściwościach w celu późniejszego użycia. Na przykład poniższy kod wywołuje zadanie `Copy` i zapisuje informacje z właściwości dane wyjściowe `CopiedFiles` na liście `SuccessfullyCopiedFiles` elementów.

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
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest dostarczany z wieloma zadaniami, takimi jak [kopia](../msbuild/copy-task.md), która kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), tworzące katalogi i [Csc](../msbuild/csc-task.md), które kompilują [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki kodu źródłowego. Aby uzyskać pełną listę dostępnych zadań i informacji o użyciu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Zastąpione zadania
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] szuka zadań w kilku lokalizacjach. Pierwsza lokalizacja znajduje się w plikach z rozszerzeniem *. OverrideTasks* przechowywanych w katalogach .NET Framework. Zadania w tych plikach zastępują wszystkie inne zadania o tych samych nazwach, w tym zadania w pliku projektu. Druga lokalizacja znajduje się w plikach z rozszerzeniem *. Zadania* w katalogach .NET Framework. Jeśli zadanie nie zostanie odnalezione w żadnej z tych lokalizacji, zostanie użyte zadanie w pliku projektu.

## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Pisanie zadania](../msbuild/task-writing.md)
- [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
