---
title: ResolveNonMSBuildProjectOutput — — Zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604ed91d32140c3b037e6ddef21e996f72ef8439
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632579"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput — zadanie

Określa pliki wyjściowe dla odwołań projektu innych niż MSBuild.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `ResolveNonMSBuildProjectOutput`.

|Parametr|Opis|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Opcjonalny parametr `String`.<br /><br /> Określa ciąg XML, który zawiera rozpoznane dane wyjściowe projektu.|
|`ProjectReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa odwołania do projektu.|
|`ResolvedOutputPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera listę rozwiązanych ścieżek odwołań (i zachowuje pierwotne atrybuty odwołania projektu).|
|`UnresolvedProjectReferences`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odwołań projektu, których nie można rozpoznać przy użyciu prewiązanej listy danych wyjściowych.<br /><br /> Ponieważ program Visual Studio rozpoznaje tylko wstępnie projekty programów innych niż MSBuild, oznacza to, że odwołania do projektu na tej liście są w formacie MSBuild.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)