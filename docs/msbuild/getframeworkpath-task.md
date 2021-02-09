---
title: GetFrameworkPath — — zadanie | Microsoft Docs
description: Dowiedz się, jak pobrać ścieżkę do zestawów .NET Framework przy użyciu zadania MSBuild GetFrameworkPath —.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dea1b70335f7a1cc98bc1ee111ff58d69023c18a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914663"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — zadanie

Pobiera ścieżkę do zestawów .NET Framework.
Pobiera ścieżkę do zestawów .NET Framework.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `GetFrameworkPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 1,1, jeśli istnieją. W przeciwnym razie zwraca wartość `null`.|
|`FrameworkVersion20Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 2,0, jeśli istnieją. W przeciwnym razie zwraca wartość `null`.|
|`FrameworkVersion30Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,0, jeśli istnieją. W przeciwnym razie zwraca wartość `null`.|
|`FrameworkVersion35Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,5, jeśli istnieją. W przeciwnym razie zwraca wartość `null`.|
|`FrameworkVersion40Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 4,0, jeśli istnieją. W przeciwnym razie zwraca wartość `null`.|
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszych zestawów struktury, jeśli są dostępne. W przeciwnym razie zwraca wartość `null`.|

## <a name="remarks"></a>Uwagi

Jeśli zainstalowano kilka wersji .NET Framework, to zadanie zwróci wersję, na której ma być uruchamiany program MSBuild.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa `GetFrameworkPath` zadania do przechowywania ścieżki do .NET Framework we `FrameworkPath` właściwości.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
