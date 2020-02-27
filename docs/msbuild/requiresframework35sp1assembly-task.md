---
title: Requiresframework35sp1assembly — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caefe0887ca23cd4cee60c3a4ba2a6133e9893df
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632774"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly — zadanie

Określa, czy aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `RequiresFramework35SP1Assembly`.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy, do których odwołuje się aplikacja.|
|`CreateDesktopShortcut`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program tworzy na pulpicie ikonę skrótu podczas instalacji.|
|`DeploymentManifestEntryPoint`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa nazwę pliku manifestu aplikacji.|
|`EntryPoint`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestaw, który ma zostać wykonany po uruchomieniu aplikacji.|
|`ErrorReportUrl`|Opcjonalny parametr `String`.<br /><br /> Określa witrynę sieci Web, która jest wyświetlana w oknach dialogowych, które są dostępne podczas instalacji ClickOnce.|
|`Files`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa listę plików, które zostaną wdrożone po opublikowaniu aplikacji.|
|`ReferencedAssemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy, do których odwołuje się projekt.|
|`RequiresMinimumFramework35SP1`|Opcjonalny `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true`, aplikacja wymaga .NET Framework 3,5 z dodatkiem SP1.|
|`SigningManifests`|Opcjonalny `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true`, manifesty ClickOnce są podpisane.|
|`SuiteName`|Opcjonalny parametr `String`.<br /><br /> Określa nazwę folderu w menu **Start** , w którym zostanie zainstalowana aplikacja.|
|`TargetFrameworkVersion`|Opcjonalny parametr `String`.<br /><br /> Określa wersję .NET Framework, do której odwołuje się ta aplikacja.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)