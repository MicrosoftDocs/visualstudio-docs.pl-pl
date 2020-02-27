---
title: FindAppConfigFile — — zadanie | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634178"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile — zadanie

Znajduje plik *App. config* (jeśli istnieje) na dostarczonych listach.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `FindAppConfigFile`.

|Parametr|Opis|
|---------------|-----------------|
|`AppConfigFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa pierwszy pasujący element znajdujący się na liście, jeśli istnieje.|
|`PrimaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa główną listę do przeszukania.|
|`SecondaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę pomocniczą do przeszukania.|
|`TargetPath`|Wymagany `String` parametr.<br /><br /> Określa wartość, która ma zostać dodana jako metadane.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
