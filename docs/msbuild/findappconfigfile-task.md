---
title: Zadanie FindAppConfigFile | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634178"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile — zadanie

Znajduje plik *app.config,* jeśli istnieje, na podanych listach.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `FindAppConfigFile` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AppConfigFile`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa pierwszy pasujący element znaleziony na liście, jeśli istnieje.|
|`PrimaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę podstawową do przeszukania.|
|`SecondaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę pomocniczą do przeszukania.|
|`TargetPath`|Wymagany parametr interfejsu `String`.<br /><br /> Określa wartość dodaną jako metadane.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
