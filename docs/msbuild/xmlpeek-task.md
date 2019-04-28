---
title: Xmlpeek — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19b8273617955092519bf16f0aa5b3fbea86218a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777824"
---
# <a name="xmlpeek-task"></a>XmlPeek — zadanie
Zwraca wartości określonych przez zapytanie XPath z pliku XML.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `XmlPeek` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalnie `String` parametru.<br /><br /> Określa obszary nazw w przypadku prefiksów kwerendy XPath.|
|`Query`|Opcjonalnie `String` parametru.<br /><br /> Określa zapytanie XPath.|
|`Result`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera wyniki, które są zwracane przez to zadanie.|
|`XmlContent`|Opcjonalnie `String` parametru.<br /><br /> Określa dane wejściowe XML jako ciąg.|
|`XmlInputPath`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę do pliku.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)