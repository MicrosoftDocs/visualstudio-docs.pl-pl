---
title: Zadanie requiresFramework35SP1asześcijanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632774"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly — zadanie

Określa, czy aplikacja wymaga dodatku SP1 .NET Framework 3.5.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `RequiresFramework35SP1Assembly` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy, do których odwołuje się aplikacja.|
|`CreateDesktopShortcut`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program , utworzy ikonę skrótu na pulpicie podczas instalacji.|
|`DeploymentManifestEntryPoint`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa nazwę pliku manifestu dla aplikacji.|
|`EntryPoint`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa zestaw, który powinien być wykonywany po uruchomieniu aplikacji.|
|`ErrorReportUrl`|Parametr `String` opcjonalny.<br /><br /> Określa witrynę sieci Web wyświetlaną w oknach dialogowych napotkanych podczas instalacji ClickOnce.|
|`Files`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa listę plików, które zostaną wdrożone po opublikowaniu aplikacji.|
|`ReferencedAssemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy, do których odwołuje się projekt.|
|`RequiresMinimumFramework35SP1`|Opcjonalny parametr wyjściowy. `Boolean`<br /><br /> Jeśli `true`aplikacja wymaga dodatku SP1 .NET Framework 3.5.|
|`SigningManifests`|Opcjonalny parametr wyjściowy. `Boolean`<br /><br /> Jeśli `true`, ClickOnce manifesty są podpisane.|
|`SuiteName`|Parametr `String` opcjonalny.<br /><br /> Określa nazwę folderu w menu **Start,** w którym zostanie zainstalowana aplikacja.|
|`TargetFrameworkVersion`|Parametr `String` opcjonalny.<br /><br /> Określa wersję programu .NET Framework przeznaczoną dla tej aplikacji.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)