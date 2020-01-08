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
ms.openlocfilehash: 8fbe0dbda58a0c57cacd64c40b66cc640b779bca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593320"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — zadanie
Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].

## <a name="task-parameters"></a>Parametry zadania
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
Poniższy przykład używa zadania `GetFrameworkSdkPath` do przechowywania ścieżki do [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] we właściwości `SdkPath`.

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
