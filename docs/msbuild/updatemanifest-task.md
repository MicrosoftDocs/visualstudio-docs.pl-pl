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
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631345"
---
# <a name="updatemanifest-task"></a>UpdateManifest — zadanie

Aktualizuje wybrane właściwości w manifeście i podpisuje je.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `UpdateManifest` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa manifest aplikacji.|
|`ApplicationPath`|Wymagany parametr interfejsu `String`.<br /><br /> Określa ścieżkę manifestu aplikacji.|
|`InputManifest`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa manifest do zaktualizowania.|
|`OutputManifest`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa manifest, który zawiera zaktualizowane właściwości.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)