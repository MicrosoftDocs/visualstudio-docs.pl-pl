---
title: ResolveManifestFiles — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ebbc2a036700c26ccd6ca3bec7b235722432e9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595179"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles — zadanie
Rozwiązuje następujące elementy w procesie kompilacji do plików na potrzeby generowania manifestu: skompilowane elementy, zależności, satelity, zawartość, symbole debugowania i dokumentacja.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `ResolveManifestFiles`.

|Parametr|Opis|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa nazwę manifestu wdrożenia.|
|`EntryPoint`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zarządzany zestaw lub odwołanie do manifestu ClickOnce, które jest punktem wejścia do manifestu.|
|`ExtraFiles`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa dodatkowe pliki.|
|`ManagedAssemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy zarządzane.|
|`NativeAssemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy natywne.|
|`OutputAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa wygenerowane zestawy.|
|`OutputDeploymentManifestEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa punkt wejścia manifestu wdrożenia danych wyjściowych.|
|`OutputEntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa punkt wejścia danych wyjściowych.|
|`OutputFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa pliki wyjściowe.|
|`PublishFiles`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa pliki do opublikowania.|
|`SatelliteAssemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy satelickie.|
|`SigningManifests`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, manifesty są podpisane.|
|`TargetCulture`|Opcjonalny parametr `String`.<br /><br /> Określa kulturę docelową dla zestawów satelickich.|
|`TargetFrameworkVersion`|Opcjonalny parametr `String`.<br /><br /> Określa docelową wersję .NET Framework.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
