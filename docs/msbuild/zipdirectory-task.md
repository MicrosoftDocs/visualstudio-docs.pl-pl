---
title: ZipDirectory — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4bf72509610e9d397e4b208294112fcc0975b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588333"
---
# <a name="zipdirectory-task"></a>ZipDirectory, zadanie
Tworzy archiwum *zip* z zawartości katalogu.

>[!NOTE]
>Zadanie `ZipDirectory` jest dostępne tylko w programie MSBuild 15,8 i nowszych wersjach.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `ZipDirectory`.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Pełna ścieżka do pliku *. zip* , który ma zostać utworzony.|
|`Overwrite`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, pomija plik docelowy zostanie nadpisany, jeśli istnieje. Wartość domyślna to `false`.|
|`SourceDirectory`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa katalog, z którego ma zostać utworzony Archiwum *zip* .|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 Poniższy przykład tworzy archiwum *zip* z katalogu wyjściowego po skompilowaniu projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
