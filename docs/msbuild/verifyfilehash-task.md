---
title: Zadanie VerifyFileHash | Dokumentacja firmy Microsoft
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf7738019680085020b9650094931d5860bc29b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618383"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash task

Sprawdza, czy plik odpowiada oczekiwanej wyznaczania wartości skrótu.

To zadanie, który został dodany w 15.8, ale wymaga [obejście](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia dla wersji programu MSBuild poniżej 16.0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `VerifyFileHash` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br />Pliki do skrótu i zweryfikowane.|
|`Hash`|Wymagane `String` parametru.<br /><br />Oczekiwano skrótu pliku.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` Parametr wyjściowy.<br /><br />`Files` Danych wejściowych za pomocą dodatkowych metadanych, ustaw wartość skrótu pliku.|
|`Algorithm`|Opcjonalnie `String` parametru.<br /><br />Algorytm. Dozwolone wartości: `SHA256`, `SHA384`, `SHA512`. Domyślne = `SHA256`.|
|`HashEncoding`|Opcjonalnie `String` parametru.<br /><br />Kodowanie do użycia dla wygenerowane skróty. Wartość domyślna to `hex`. Dozwolone wartości = `hex`, `base64`.|

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `VerifyFileHash` zadania, aby zweryfikować swój własny sumy kontrolnej.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)