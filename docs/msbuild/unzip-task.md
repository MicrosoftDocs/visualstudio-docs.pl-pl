---
title: Rozpakuj zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631513"
---
# <a name="unzip-task"></a>Rozpakuj zadanie

Rozpakowywać archiwum *.zip* do określonej lokalizacji.

>[!NOTE]
>Zadanie `Unzip` jest dostępne tylko w umi.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `Unzip` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFolder`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr<br /><br /> Określa folder docelowy, do który ma być rozpakować plik.|
|`OverwriteReadOnlyFiles`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, zastępuje pliki tylko do odczytu. Wartość domyślna to `false`.|
|`SkipUnchangedFiles`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, pomija rozpakowywanie plików, które pozostają niezmienione. Wartość domyślna to `true`. Zadanie `Unzip` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa jeden lub więcej plików do rozpakować. Podczas określania wielu plików są one rozpakowane w celu uzyskania tego samego folderu.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład rozpakowywanie archiwum i zastępowanie wszystkich plików tylko do odczytu.

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
