---
title: UpdateManifest — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 215092d7fbcee8ec30210dd8332bc6ae5b7ad412
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578279"
---
# <a name="updatemanifest-task"></a>UpdateManifest — zadanie
Aktualizuje wybrane właściwości w manifeście i podpisuje je.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `UpdateManifest`.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa manifest aplikacji.|
|`ApplicationPath`|Wymagany `String` parametr.<br /><br /> Określa ścieżkę manifestu aplikacji.|
|`InputManifest`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa manifest do zaktualizowania.|
|`OutputManifest`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa manifest, który zawiera zaktualizowane właściwości.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)