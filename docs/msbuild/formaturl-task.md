---
title: FormatUrl — — zadanie | Microsoft Docs
description: Dowiedz się, jak za pomocą zadania MSBuild FormatUrl — skonwertować wprowadzony adres URL do prawidłowego formatu wyjściowego adresu URL.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436890"
---
# <a name="formaturl-task"></a>FormatUrl — zadanie

Konwertuje adres URL na prawidłowy format adresu URL.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `FormatUrl` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`InputUrl`|Opcjonalny `String` parametr.<br /><br /> Określa adres URL do sformatowania.|
|`OutputUrl`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa sformatowany adres URL.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)