---
title: Przenieś zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633463"
---
# <a name="move-task"></a>Move — Zadanie

Przenosi pliki w nową lokalizację.

## <a name="parameters"></a>Parametry

 W tabeli folowing opisano `Move` parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa listę plików, do które mają być przesuń pliki źródłowe. Oczekuje się, że ta lista będzie mapowaniem jeden do jednego `SourceFiles` do listy, która jest określona w parametrze. Oznacza to, że pierwszy `SourceFiles` plik określony w zostaną `DestinationFiles`przeniesione do pierwszej lokalizacji określonej w , i tak dalej.|
|`DestinationFolder`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa katalog, do którego mają zostać przeniesione pliki.|
|`MovedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera elementy, które zostały pomyślnie przeniesione.|
|`OverwriteReadOnlyFiles`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`pliki zostaną zastąpione, nawet jeśli są one oznaczone jako pliki tylko do odczytu.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do przeniesienia.|

## <a name="remarks"></a>Uwagi

 Należy określić `DestinationFolder` parametr `DestinationFiles` lub parametr, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.

 Zadanie `Move` tworzy foldery zgodnie z wymaganiami dla żądanych plików docelowych.

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
