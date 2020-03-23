---
title: Zadanie ResolveManifestFiles | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2628f06ac4eafc7d57123460771793005597b039
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632696"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles — zadanie

Rozwiązuje następujące elementy w procesie kompilacji do plików do generowania manifestu: elementy utworzone, zależności, satelity, zawartość, symbole debugowania i dokumentacji.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `ResolveManifestFiles` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa nazwę manifestu wdrażania.|
|`EntryPoint`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa zestaw zarządzany lub ClickOnce odwołanie manifestu, który jest punktem wejścia do manifestu.|
|`ExtraFiles`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa dodatkowe pliki.|
|`ManagedAssemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy zarządzane.|
|`NativeAssemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa natywne zestawy.|
|`OutputAssemblies`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa wygenerowane zestawy.|
|`OutputDeploymentManifestEntryPoint`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa punkt wejścia manifestu wdrożenia wyjściowego.|
|`OutputEntryPoint`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa wyjściowy punkt wejścia.|
|`OutputFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa pliki wyjściowe.|
|`PublishFiles`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa pliki publikowania.|
|`SatelliteAssemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy satelitowane.|
|`SigningManifests`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`manifesty są podpisane.|
|`TargetCulture`|Parametr `String` opcjonalny.<br /><br /> Określa kulturę docelową dla zestawów satelickich.|
|`TargetFrameworkVersion`|Parametr `String` opcjonalny.<br /><br /> Określa docelową wersję programu .NET Framework.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
