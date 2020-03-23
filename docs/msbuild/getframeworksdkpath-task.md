---
title: Zadanie GetFrameworkSdkPath | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633996"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — zadanie

Pobiera ścieżkę do zestawu Windows Software Development Kit (SDK).
## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli `GetFrameworkSdkPath` opisano parametry zadania.
W poniższej tabeli `GetFrameworkSdkPath` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do .NET SDK w wersji 2.0, jeśli jest obecny. W `String.Empty`przeciwnym razie zwraca .|
|`FrameworkSdkVersion35Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do .NET SDK w wersji 3.5, jeśli jest obecny. W `String.Empty`przeciwnym razie zwraca .|
|`FrameworkSdkVersion40Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do .NET SDK w wersji 4.0, jeśli jest obecny. W `String.Empty`przeciwnym razie zwraca .|
|`Path`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera ścieżkę do najnowszego sdk .NET, jeśli istnieje dowolna wersja. W `String.Empty`przeciwnym razie zwraca .|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `GetFrameworkSdkPath` użyto zadania do przechowywania ścieżki `SdkPath` do sdk systemu Windows w właściwości.

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
