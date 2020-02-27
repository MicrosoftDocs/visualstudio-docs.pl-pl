---
title: XslTransformation Task | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84bc83f60d133dcaf22c9fa690357fa2624adabd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630798"
---
# <a name="xsltransformation-task"></a>XslTransformation — zadanie

Przekształca dane wejściowe XML przy użyciu XSLT lub skompilowanego XSLT i wyjść do urządzenia wyjściowego lub pliku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `XslTransformation`.

|Parametr|Opis|
|---------------|-----------------|
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe transformacji XML.|
|`Parameters`|Opcjonalny parametr `String`.<br /><br /> Określa parametry dokumentu wejściowego XSLT.|
|`XmlContent`|Opcjonalny parametr `String`.<br /><br /> Określa dane wejściowe w formacie XML jako ciąg.|
|`XmlInputPaths`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa pliki wejściowe XML.|
|`XslCompiledDllPath`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa skompilowane XSLT.|
|`XslContent`|Opcjonalny parametr `String`.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|
|`XslInputPath`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik wejściowy XSLT.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
