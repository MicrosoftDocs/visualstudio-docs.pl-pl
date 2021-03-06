---
title: ZipDirectory — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania ZipDirectory, aby utworzyć archiwum zip z zawartości katalogu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6b897a33dacdbd52beaabdd9289a010df92a85c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847885"
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

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
