---
title: Xmlwgląd — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59bc42bd438d80bbaf0ff45cd1c95447961cd437
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630630"
---
# <a name="xmlpeek-task"></a>XmlPeek — zadanie

Zwraca wartości określone przez zapytanie XPath z pliku XML.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `XmlPeek`.

|Parametr|Opis|
|---------------|-----------------|
|`Namespaces`|Opcjonalny parametr `String`.<br /><br /> Określa przestrzenie nazw dla prefiksów zapytania XPath.|
|`Query`|Opcjonalny parametr `String`.<br /><br /> Określa zapytanie XPath.|
|`Result`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera wyniki, które są zwracane przez to zadanie.|
|`XmlContent`|Opcjonalny parametr `String`.<br /><br /> Określa dane wejściowe w formacie XML jako ciąg.|
|`XmlInputPath`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa dane wejściowe w formacie XML jako ścieżkę pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
