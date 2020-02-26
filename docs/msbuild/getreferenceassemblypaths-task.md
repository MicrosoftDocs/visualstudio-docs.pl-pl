---
title: GetReferenceAssemblyPaths — zadanie | Microsoft Docs
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
ms.openlocfilehash: 56e3526f130a8717dec2dafeef794375ceffc37c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579620"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths, zadanie
Zwraca ścieżki zestawów referencyjnych różnych struktur.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `GetReferenceAssemblyPaths`.

|Parametr|Opis|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Opcjonalny `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie parametru `TargetFrameworkMoniker`. Jeśli `TargetFrameworkMoniker` ma wartość null lub jest pusty, ta ścieżka zostanie `String.Empty`a.|
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalny `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie parametru `TargetFrameworkMoniker`, bez uwzględnienia części profilu monikera. Jeśli `TargetFrameworkMoniker` ma wartość null lub jest pusty, ta ścieżka zostanie `String.Empty`a.|
|`TargetFrameworkMoniker`|Opcjonalny parametr `String`.<br /><br /> Określa moniker platformy docelowej, który jest skojarzony ze ścieżkami zestawu odwołania.|
|`RootPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę katalogu głównego, która ma zostać użyta do wygenerowania ścieżki zestawu odwołania.|
|`BypassFrameworkInstallChecks`|Opcjonalny parametr <xref:System.Boolean>.<br /><br /> Jeśli `true`, program pomija testy podstawowe, które są domyślnie `GetReferenceAssemblyPaths` wykonywane, aby upewnić się, że są zainstalowane pewne struktury środowiska uruchomieniowego, w zależności od platformy docelowej.|
|`TargetFrameworkMonikerDisplayName`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę wyświetlaną moniker struktury docelowej.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)