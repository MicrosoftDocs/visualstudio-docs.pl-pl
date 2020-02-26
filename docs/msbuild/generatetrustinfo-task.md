---
title: GenerateTrustInfo — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b9c32681af56595f8b00feab4979a3ec45f1588
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578689"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — zadanie
Generuje zaufanie aplikacji z manifestu podstawowego oraz z parametrów `TargetZone` i `ExcludedPermissions`.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `GenerateTrustInfo`.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationDependencies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy zależne.|
|`BaseManifest`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa manifest podstawowy, z którego ma zostać wygenerowane zaufanie aplikacji.|
|`ExcludedPermissions`|Opcjonalny parametr `String`.<br /><br /> Określa jedną lub więcej wartości tożsamości uprawnień oddzielonych średnikami, które mają zostać wykluczone z domyślnego zestawu uprawnień strefy.|
|`TargetZone`|Opcjonalny parametr `String`.<br /><br /> Określa domyślny zestaw uprawnień strefy, który jest uzyskiwany z zasad komputera.|
|`TrustInfoFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który zawiera informacje o zaufaniu zabezpieczeń aplikacji.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)