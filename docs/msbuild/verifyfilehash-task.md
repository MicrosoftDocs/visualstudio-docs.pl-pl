---
title: VerifyFileHash — zadanie | Microsoft Docs
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
ms.openlocfilehash: 2e7330e750d0f636979f52eacf398ca7d496c523
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342411"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash, zadanie

Sprawdza, czy plik jest zgodny z oczekiwanym skrótem pliku.

To zadanie zostało dodane w 15,8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia z wersjami MSBuild poniżej 16,0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `VerifyFileHash` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br />Pliki do wyznaczania wartości skrótu i weryfikacji.|
|`Hash`|Wymagany `String` parametr.<br /><br />Oczekiwany skrót pliku.|
|`Algorithm`|Opcjonalny `String` parametr.<br /><br />Algorytm. Dozwolone wartości: `SHA256`, `SHA384`, `SHA512`. Wartość domyślna = `SHA256`.|
|`HashEncoding`|Opcjonalny `String` parametr.<br /><br />Kodowanie, które ma być używane dla wygenerowanych skrótów. Wartość domyślna to `hex`. Dozwolone wartości = `hex`, `base64`.|

## <a name="example"></a>Przykład

W poniższym przykładzie za pomocą zadania `VerifyFileHash` można sprawdzić własną sumę kontrolną.

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