---
title: Przenieś zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b9f83fa7c80769ea3c584e2885c8fb1db24176
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633463"
---
# <a name="move-task"></a>Move — Zadanie

Przenosi pliki do nowej lokalizacji.

## <a name="parameters"></a>Parametry

 W tabeli następujące kwestie opisano parametry `Move` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa listę plików, do których mają zostać przeniesione pliki źródłowe. Ta lista powinna być mapowaniem jeden-do-jednego do listy określonej w `SourceFiles` parametrze. Oznacza to, że pierwszy plik określony w programie `SourceFiles` zostanie przeniesiony do pierwszej lokalizacji określonej w `DestinationFiles` i tak dalej.|
|`DestinationFolder`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa katalog, do którego chcesz przenieść pliki.|
|`MovedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały pomyślnie przeniesione.|
|`OverwriteReadOnlyFiles`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zastępuje pliki, nawet jeśli są oznaczone jako pliki tylko do odczytu.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do przeniesienia.|

## <a name="remarks"></a>Uwagi

 `DestinationFolder` `DestinationFiles` Należy określić parametr lub parametr, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.

 `Move`Zadanie tworzy foldery wymagane dla żądanych plików docelowych.

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
