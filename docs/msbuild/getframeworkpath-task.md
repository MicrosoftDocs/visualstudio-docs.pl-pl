---
title: GetFrameworkPath — — zadanie | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b907194c4818ff6b867e9d15b795506ef3b77476
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634009"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — zadanie

Pobiera ścieżkę do zestawów .NET Framework.
Pobiera ścieżkę do zestawów .NET Framework.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry zadania `GetFrameworkPath`.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 1,1, jeśli istnieją. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion20Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 2,0, jeśli istnieją. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion30Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,0, jeśli istnieją. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion35Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 3,5, jeśli istnieją. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion40Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów programu Framework w wersji 4,0, jeśli istnieją. W przeciwnym razie zwraca `null`.|
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszych zestawów struktury, jeśli są dostępne. W przeciwnym razie zwraca `null`.|

## <a name="remarks"></a>Uwagi

Jeśli zainstalowano kilka wersji .NET Framework, to zadanie zwróci wersję, na której ma być uruchamiany program MSBuild.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa zadania `GetFrameworkPath` do przechowywania ścieżki do .NET Framework we właściwości `FrameworkPath`.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
