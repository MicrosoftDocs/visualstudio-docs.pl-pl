---
title: FormatUrl — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fcd4ed0c60d615f0c213e1af5099c5e94a9b485
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634126"
---
# <a name="formaturl-task"></a>FormatUrl — zadanie

Konwertuje adres URL na prawidłowy format adresu URL.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `FormatUrl`.

|Parametr|Opis|
|---------------|-----------------|
|`InputUrl`|Opcjonalny parametr `String`.<br /><br /> Określa adres URL do sformatowania.|
|`OutputUrl`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa sformatowany adres URL.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)