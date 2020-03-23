---
title: Zadanie GetReferenceAssemblyPaths | Dokumenty firmy Microsoft
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
ms.openlocfilehash: d2ca532e37fa2f70800416539a7de2ff5e9978e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633983"
---
# <a name="getreferenceassemblypaths-task"></a>Zadanie GetReferenceAssemblyPaths

Zwraca ścieżki zestawu odwołań różnych struktur.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `GetReferenceAssemblyPaths` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Opcjonalny parametr wyjściowy. `String[]`<br /><br /> Zwraca ścieżkę na `TargetFrameworkMoniker` podstawie parametru. Jeśli `TargetFrameworkMoniker` jest null lub puste, `String.Empty`ta ścieżka będzie .|
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalny parametr wyjściowy. `String[]`<br /><br /> Zwraca ścieżkę na `TargetFrameworkMoniker` podstawie parametru, bez uwzględnienia części profilu monikera. Jeśli `TargetFrameworkMoniker` jest null lub puste, `String.Empty`ta ścieżka będzie .|
|`TargetFrameworkMoniker`|Parametr `String` opcjonalny.<br /><br /> Określa moniker struktury docelowej, który jest skojarzony ze ścieżkami zestawu odwołań.|
|`RootPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę główną używaną do generowania ścieżki zestawu odniesienia.|
|`BypassFrameworkInstallChecks`|Parametr <xref:System.Boolean> opcjonalny.<br /><br /> Jeśli `true`, pomija podstawowe `GetReferenceAssemblyPaths` kontrole, które wykonuje domyślnie, aby upewnić się, że niektóre struktury środowiska wykonawczego są zainstalowane, w zależności od struktury docelowej.|
|`TargetFrameworkMonikerDisplayName`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa nazwę wyświetlaną monikera struktury docelowej.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)