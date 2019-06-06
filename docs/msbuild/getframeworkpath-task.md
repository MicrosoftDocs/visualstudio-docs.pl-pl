---
title: Getframeworkpath — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7bf2432e37278c924d1604e735feec7b848b01
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747556"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — zadanie
Pobiera ścieżkę do zestawów .NET Framework.

## <a name="task-parameters"></a>Parametry zadania
W poniższej tabeli opisano parametry `GetFrameworkPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 1.1, jeśli jest obecny. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion20Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 2.0, jeśli jest obecny. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion30Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 3.0 lub nowszej, jeśli jest obecny. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion35Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów w wersji 3.5 framework, jeśli jest obecny. W przeciwnym razie zwraca `null`.|
|`FrameworkVersion40Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 4.0 lub nowszej, jeśli jest obecny. W przeciwnym razie zwraca `null`.|
|`Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszych zestawów framework, jeśli są dostępne. W przeciwnym razie zwraca `null`.|

## <a name="remarks"></a>Uwagi
Jeśli są zainstalowane różne wersje programu .NET Framework, to zadanie zwraca informacje o wersji, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest przeznaczony do działania.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
W poniższym przykładzie użyto `GetFrameworkPath` zadanie, aby zapisać ścieżki programu .NET Framework w `FrameworkPath` właściwości.

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
