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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888098"
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