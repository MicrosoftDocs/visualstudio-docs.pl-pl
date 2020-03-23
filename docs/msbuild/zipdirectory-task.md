---
title: Zadanie ZipDirectory | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 5ceb23d34fab92fe0056f9bd82b9d9c63967dc4c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094572"
---
# <a name="zipdirectory-task"></a>Zadanie ZipDirectory

Tworzy archiwum *zip* z zawartości katalogu.

>[!NOTE]
>Zadanie `ZipDirectory` jest dostępne tylko w umi.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `ZipDirectory` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Pełna ścieżka do pliku *zip* do utworzenia.|
|`Overwrite`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`plik docelowy zostanie zastąpiony, jeśli istnieje. Wartość domyślna to `false`.|
|`SourceDirectory`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa katalog, z wyjętego z archiwum *.zip.*|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład (jeśli jest używany jako importowany plik *.targets)* tworzy archiwum *zip* z katalogu wyjściowego po zbudowaniu projektu. Właściwość `$(OutputPath)` będzie normalnie zdefiniowane w pliku projektu MSBuild, więc plik projektu, który `output.zip`importuje następujący plik będzie produkować archiwum zip:

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
