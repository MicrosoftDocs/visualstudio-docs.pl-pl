---
title: VerifyFileHash Zadanie | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579525"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash zadanie

Sprawdza, czy plik pasuje do oczekiwanego skrótu pliku. Jeśli skrót nie jest zgodny, zadanie kończy się niepowodzeniem.

To zadanie zostało dodane w wersji 15.8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) problemu w wersjach MSBuild poniżej 16.0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `VerifyFileHash` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany parametr interfejsu `String`.<br /><br />Plik, który ma być haszem i zweryfikowany.|
|`Hash`|Wymagany parametr interfejsu `String`.<br /><br />Oczekiwany skrót pliku.|
|`Algorithm`|Parametr `String` opcjonalny.<br /><br />Algorytm. Dozwolone wartości: `SHA256` `SHA384`, `SHA512`, . Domyślnie `SHA256`= .|
|`HashEncoding`|Parametr `String` opcjonalny.<br /><br />Kodowanie do użycia dla wygenerowanych skrótów. Wartość domyślna to `hex`. Dozwolone wartości `hex`= `base64`, .|

## <a name="example"></a>Przykład

W poniższym przykładzie `VerifyFileHash` użyto zadania do zweryfikowania własnej sumy kontrolnej.

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

Na MSBuild 16.5 i nowsze, jeśli nie chcesz kompilacji zakończyć się niepowodzeniem, gdy skrót nie jest zgodny, na przykład jeśli używasz porównania mieszania jako warunek przepływu sterowania, można obniżyć ostrzeżenie do komunikatu przy użyciu następującego kodu:

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
