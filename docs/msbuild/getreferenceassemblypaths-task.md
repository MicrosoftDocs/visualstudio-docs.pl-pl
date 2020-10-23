---
title: GetReferenceAssemblyPaths — zadanie | Microsoft Docs
description: Użyj zadania MSBuild GetReferenceAssemblyPaths, aby zwrócić ścieżki zestawu odwołań różnych platform.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bbe9366e9b4b2c795b21ba46bd8320599c9e572
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436794"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths, zadanie

Zwraca ścieżki zestawów referencyjnych różnych struktur.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `GetReferenceAssemblyPaths` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Opcjonalny `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę opartą na `TargetFrameworkMoniker` parametrze. Jeśli wartość `TargetFrameworkMoniker` jest równa null lub pusta, ta ścieżka będzie `String.Empty` .|
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalny `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie `TargetFrameworkMoniker` parametru, bez uwzględnienia części profilu monikera. Jeśli wartość `TargetFrameworkMoniker` jest równa null lub pusta, ta ścieżka będzie `String.Empty` .|
|`TargetFrameworkMoniker`|Opcjonalny `String` parametr.<br /><br /> Określa moniker platformy docelowej, który jest skojarzony ze ścieżkami zestawu odwołania.|
|`RootPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę katalogu głównego, która ma zostać użyta do wygenerowania ścieżki zestawu odwołania.|
|`BypassFrameworkInstallChecks`|Opcjonalny <xref:System.Boolean> parametr.<br /><br /> Jeśli `true` program ignoruje podstawowe testy, które `GetReferenceAssemblyPaths` są domyślnie wykonywane w celu upewnienia się, że niektóre platformy środowiska uruchomieniowego są zainstalowane, w zależności od platformy docelowej.|
|`TargetFrameworkMonikerDisplayName`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę wyświetlaną moniker struktury docelowej.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)