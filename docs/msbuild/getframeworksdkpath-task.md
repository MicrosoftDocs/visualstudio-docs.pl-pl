---
title: GetFrameworkSdkPath — — zadanie | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021bdb485846749ea2c7e9dfe483e09738fda46
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633996"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — zadanie

Pobiera ścieżkę do zestawu Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry zadania `GetFrameworkSdkPath`.
W poniższej tabeli opisano parametry zadania `GetFrameworkSdkPath`.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 2,0, jeśli istnieje. W przeciwnym razie zwraca `String.Empty`.|
|`FrameworkSdkVersion35Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 3,5, jeśli istnieje. W przeciwnym razie zwraca `String.Empty`.|
|`FrameworkSdkVersion40Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 4,0, jeśli istnieje. W przeciwnym razie zwraca `String.Empty`.|
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszego zestawu SDK platformy .NET, jeśli obecna jest jakakolwiek wersja. W przeciwnym razie zwraca `String.Empty`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa zadania `GetFrameworkSdkPath` do przechowywania ścieżki do Windows SDK we właściwości `SdkPath`.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
