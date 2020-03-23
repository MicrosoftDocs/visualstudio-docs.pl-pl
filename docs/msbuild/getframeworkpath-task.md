---
title: Zadanie GetFrameworkPath | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634009"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — zadanie

Pobiera ścieżkę do zestawów .NET Framework.
Pobiera ścieżkę do zestawów .NET Framework.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli `GetFrameworkPath` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkVersion11Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 1.1, jeśli jest obecny. W `null`przeciwnym razie zwraca .|
|`FrameworkVersion20Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 2.0, jeśli jest obecny. W `null`przeciwnym razie zwraca .|
|`FrameworkVersion30Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 3.0, jeśli jest obecny. W `null`przeciwnym razie zwraca .|
|`FrameworkVersion35Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do framework wersji 3.5 zestawów, jeśli jest obecny. W `null`przeciwnym razie zwraca .|
|`FrameworkVersion40Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do zestawów framework w wersji 4.0, jeśli jest obecny. W `null`przeciwnym razie zwraca .|
|`Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do najnowszych zestawów framework, jeśli są dostępne. W `null`przeciwnym razie zwraca .|

## <a name="remarks"></a>Uwagi

Jeśli zainstalowanych jest kilka wersji programu .NET Framework, to zadanie zwraca wersję, na której program MSBuild jest przeznaczony do uruchamiania.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `GetFrameworkPath` użyto zadania do przechowywania ścieżki `FrameworkPath` do programu .NET Framework we właściwości.

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
