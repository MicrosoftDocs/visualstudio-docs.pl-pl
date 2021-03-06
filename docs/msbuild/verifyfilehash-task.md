---
title: VerifyFileHash — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania VerifyFileHash, aby sprawdzić, czy plik jest zgodny z oczekiwanym skrótem pliku, i czy nie jest zgodny.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfd6bb88a5bfbbffb7c99f7f43036cf9fee4d6ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908802"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash, zadanie

Sprawdza, czy plik jest zgodny z oczekiwanym skrótem pliku. Jeśli skrót nie jest zgodny, zadanie zakończy się niepowodzeniem.

To zadanie zostało dodane w 15,8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) do użycia z wersjami MSBuild poniżej 16,0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `VerifyFileHash` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany parametr interfejsu `String`.<br /><br />Plik do wyznaczania wartości skrótu i weryfikacji.|
|`Hash`|Wymagany parametr interfejsu `String`.<br /><br />Oczekiwany skrót pliku.|
|`Algorithm`|Opcjonalny `String` parametr.<br /><br />Algorytm. Dozwolone wartości: `SHA256` , `SHA384` , `SHA512` . Wartość domyślna = `SHA256` .|
|`HashEncoding`|Opcjonalny `String` parametr.<br /><br />Kodowanie, które ma być używane dla wygenerowanych skrótów. Wartość domyślna to `hex` . Dozwolone wartości = `hex` , `base64` .|

## <a name="example"></a>Przykład

Poniższy przykład używa zadania, `VerifyFileHash` Aby sprawdzić własną sumę kontrolną.

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

Jeśli nie chcesz, aby kompilacja była zakończona niepowodzeniem w programie MSBuild 16,5 i nowszych, na przykład jeśli używasz porównania skrótu jako warunku przepływu sterowania, możesz obniżyć ostrzeżenie do komunikatu przy użyciu następującego kodu:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
