---
title: GetFrameworkSdkPath — — zadanie | Microsoft Docs
description: Dowiedz się, jak pobrać ścieżkę do Windows SDK przy użyciu zadania MSBuild GetFrameworkSdkPath —.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0fe468f593d085c10f8d077246af6858d0571fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914638"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — zadanie

Pobiera ścieżkę do zestawu Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `GetFrameworkSdkPath` zadania.
W poniższej tabeli opisano parametry `GetFrameworkSdkPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 2,0, jeśli istnieje. W przeciwnym razie zwraca wartość `String.Empty`.|
|`FrameworkSdkVersion35Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 3,5, jeśli istnieje. W przeciwnym razie zwraca wartość `String.Empty`.|
|`FrameworkSdkVersion40Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 4,0, jeśli istnieje. W przeciwnym razie zwraca wartość `String.Empty`.|
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszego zestawu SDK platformy .NET, jeśli obecna jest jakakolwiek wersja. W przeciwnym razie zwraca wartość `String.Empty`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa `GetFrameworkSdkPath` zadania do przechowywania ścieżki do Windows SDK we `SdkPath` właściwości.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
