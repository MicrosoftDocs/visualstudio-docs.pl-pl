---
title: ConvertToAbsolutePath — — zadanie | Microsoft Docs
description: Za pomocą zadania MSBuild ConvertToAbsolutePath — można skonwertować ścieżkę względną lub odwołanie do ścieżki bezwzględnej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecf9695b36f341fa350abf53062e70095c03c374
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796163"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath — zadanie

Konwertuje ścieżkę względną lub odwołanie do ścieżki bezwzględnej.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `ConvertToAbsolutePath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista ścieżek względnych do przekonwertowania na ścieżki bezwzględne.|
|`AbsolutePaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Lista ścieżek bezwzględnych dla elementów, które zostały przesłane.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
