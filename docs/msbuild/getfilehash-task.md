---
title: Zadanie GetFileHash | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ebd50b42408dc7bd2642c257dece686245870f
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484887"
---
# <a name="getfilehash-task"></a>GetFileHash task

Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

To zadanie, który został dodany w 15.8, ale wymaga [obejście](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia dla wersji programu MSBuild poniżej 16.0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `GetFileHash` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Pliki, aby zostać obliczona wartość skrótu.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` Parametr wyjściowy.<br /><br />`Files` Danych wejściowych za pomocą dodatkowych metadanych, ustaw wartość skrótu pliku.|
|`Hash`|`String` Parametr wyjściowy.<br /><br />Skrót pliku. Te dane wyjściowe jest ustawiona tylko wtedy, jeśli została dokładnie jeden element przekazanej.|
|`Algorithm`|Opcjonalnie `String` parametru.<br /><br />Algorytm. Dozwolone wartości: `SHA256`, `SHA384`, `SHA512`. Domyślne = `SHA256`.|
|`MetadataName`|Opcjonalnie `String` parametru.<br /><br />Nazwa metadanych, gdzie skrótu jest przechowywana w każdym elemencie. Wartość domyślna to `FileHash`.|
|`HashEncoding`|Opcjonalnie `String` parametru.<br /><br />Kodowanie do użycia dla wygenerowane skróty. Wartość domyślna to `hex`. Dozwolone wartości = `hex`, `base64`.|

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `GetFileHash` zadanie, aby określić i Drukuj suma kontrolna `FilesToHash` elementów.

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

## <a name="see-also"></a>Zobacz także

[Zadania](../msbuild/msbuild-tasks.md)

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)