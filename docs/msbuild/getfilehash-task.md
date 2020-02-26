---
title: GetFileHash — zadanie | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578653"
---
# <a name="getfilehash-task"></a>GetFileHash, zadanie

Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

To zadanie zostało dodane w 15,8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia z wersjami MSBuild poniżej 16,0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry zadania `GetFileHash`.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Pliki do przetworzenia skrótów.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br />`Files` dane wejściowe z dodatkowymi metadanymi ustawionymi na wartość skrótu pliku.|
|`Hash`|`String` parametr wyjściowy.<br /><br />Skrót pliku. Te dane wyjściowe są ustawiane tylko wtedy, gdy przekazano dokładnie jeden element.|
|`Algorithm`|Opcjonalny parametr `String`.<br /><br />Algorytm. Dozwolone wartości: `SHA256`, `SHA384`, `SHA512`. Wartość domyślna = `SHA256`.|
|`MetadataName`|Opcjonalny parametr `String`.<br /><br />Nazwa metadanych, w której skrót jest przechowywany w każdym elemencie. Wartość domyślna to `FileHash`.|
|`HashEncoding`|Opcjonalny parametr `String`.<br /><br />Kodowanie, które ma być używane dla wygenerowanych skrótów. Wartość domyślna to `hex`. Dozwolone wartości = `hex`, `base64`.|

## <a name="example"></a>Przykład

Poniższy przykład używa zadania `GetFileHash`, aby określić i wydrukować sumę kontrolną elementów `FilesToHash`.

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)