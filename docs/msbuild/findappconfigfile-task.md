---
title: FindAppConfigFile — — zadanie | Microsoft Docs
description: Dowiedz się, jak użyć zadania FindAppConfigFile — programu MSBuild, aby znaleźć plik app.config, jeśli istnieje, na liście dostarczonych.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff26ee3505671d29df610278d701803b816d30f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877138"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile — zadanie

Znajduje plik *app.config* , jeśli istnieje, na określonych listach.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `FindAppConfigFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AppConfigFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa pierwszy pasujący element znajdujący się na liście, jeśli istnieje.|
|`PrimaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa główną listę do przeszukania.|
|`SecondaryList`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę pomocniczą do przeszukania.|
|`TargetPath`|Wymagany parametr interfejsu `String`.<br /><br /> Określa wartość, która ma zostać dodana jako metadane.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
