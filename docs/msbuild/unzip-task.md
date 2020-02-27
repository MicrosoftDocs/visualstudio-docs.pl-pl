---
title: Rozpakuj zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631513"
---
# <a name="unzip-task"></a>Rozpakuj zadanie

Rozpakuje Archiwum *. zip* do określonej lokalizacji.

>[!NOTE]
>Zadanie `Unzip` jest dostępne tylko w programie MSBuild 15,8 i nowszych wersjach.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `Unzip`.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFolder`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Określa folder docelowy, do którego ma zostać rozpakować plik.|
|`OverwriteReadOnlyFiles`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zastępuje pliki tylko do odczytu. Wartość domyślna to `false`.|
|`SkipUnchangedFiles`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program pomija niezmienione pliki rozpakowywania. Wartość domyślna to `true`. Zadanie `Unzip` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa co najmniej jeden plik do rozpakowania. Podczas określania wielu plików, które są rozpakowane, w celu przeszukania tego samego folderu.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład rozpakuje archiwum i zastępuje wszystkie pliki tylko do odczytu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
