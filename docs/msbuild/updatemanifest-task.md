---
title: UpdateManifest — — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania UpdateManifest —, aby zaktualizować wybrane właściwości w manifeście i zrezygnować.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8bb090b66a52e9c2931e8bf4afc878d87a0ae36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902502"
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