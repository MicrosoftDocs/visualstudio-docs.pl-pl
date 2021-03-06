---
title: GetFileHash — zadanie | Microsoft Docs
description: Dowiedz się, jak używać zadania MSBuild GetFileHash do obliczania sum kontrolnych zawartości pliku lub zestawu plików.
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 163fbfd9c2bf0ca56b5b9b6bc11dc48420cfc270
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914699"
---
# <a name="getfilehash-task"></a>GetFileHash, zadanie

Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

To zadanie zostało dodane w 15,8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia z wersjami MSBuild poniżej 16,0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `GetFileHash` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Pliki do przetworzenia skrótów.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br />`Files`Dane wejściowe z dodatkowymi metadanymi ustawionymi na wartość skrótu pliku.|
|`Hash`|`String` parametr wyjściowy.<br /><br />Skrót pliku. Te dane wyjściowe są ustawiane tylko wtedy, gdy przekazano dokładnie jeden element.|
|`Algorithm`|Opcjonalny `String` parametr.<br /><br />Algorytm. Dozwolone wartości: `SHA256` , `SHA384` , `SHA512` . Wartość domyślna = `SHA256` .|
|`MetadataName`|Opcjonalny `String` parametr.<br /><br />Nazwa metadanych, w której skrót jest przechowywany w każdym elemencie. Wartość domyślna to `FileHash` .|
|`HashEncoding`|Opcjonalny `String` parametr.<br /><br />Kodowanie, które ma być używane dla wygenerowanych skrótów. Wartość domyślna to `hex` . Dozwolone wartości = `hex` , `base64` .|

## <a name="example"></a>Przykład

Poniższy przykład używa zadania, `GetFileHash` Aby określić i wydrukować sumę kontrolną `FilesToHash` elementów.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)