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
ms.openlocfilehash: 1092add6386ccc5bc1de78efcf7b623a617d920b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183070"
---
# <a name="zipdirectory-task"></a>ZipDirectory, zadanie

Tworzy archiwum *zip* z zawartości katalogu.

>[!NOTE]
>`ZipDirectory`Zadanie jest dostępne tylko w programie MSBuild 15,8 i jego nowszych wersjach.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `ZipDirectory` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Pełna ścieżka do pliku *. zip* , który ma zostać utworzony.|
|`Overwrite`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` plik docelowy zostanie nadpisany, jeśli istnieje. Wartość domyślna to `false` .|
|`SourceDirectory`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa katalog, z którego ma zostać utworzony Archiwum *zip* .|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład (jeśli jest używany jako zaimportowany plik *. targets* ) tworzy archiwum *zip* z katalogu wyjściowego po skompilowaniu projektu. `$(OutputPath)`Właściwość zwykle jest zdefiniowana w pliku projektu programu MSBuild, dlatego plik projektu, który importuje następujący plik, spowoduje utworzenie archiwum zip `output.zip` :

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
