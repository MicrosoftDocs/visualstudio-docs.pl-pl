---
title: GetFileHash Zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578653"
---
# <a name="getfilehash-task"></a>GetFileHash zadanie

Oblicza sumy kontrolne zawartości pliku lub zestawu plików.

To zadanie zostało dodane w wersji 15.8, ale wymaga [obejścia](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) problemu w wersjach MSBuild poniżej 16.0.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `GetFileHash` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Pliki, które mają być haszowane.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`parametru wyjściowego.<br /><br />Dane `Files` wejściowe z dodatkowymi metadanymi ustawionymi na skrót pliku.|
|`Hash`|`String`parametru wyjściowego.<br /><br />Skrót pliku. To dane wyjściowe jest ustawiona tylko wtedy, gdy było dokładnie jeden element przekazany w.|
|`Algorithm`|Parametr `String` opcjonalny.<br /><br />Algorytm. Dozwolone wartości: `SHA256` `SHA384`, `SHA512`, . Domyślnie `SHA256`= .|
|`MetadataName`|Parametr `String` opcjonalny.<br /><br />Nazwa metadanych, w której skrót jest przechowywany w każdym elemencie. Wartość domyślna to `FileHash`.|
|`HashEncoding`|Parametr `String` opcjonalny.<br /><br />Kodowanie do użycia dla wygenerowanych skrótów. Wartość domyślna to `hex`. Dozwolone wartości `hex`= `base64`, .|

## <a name="example"></a>Przykład

W poniższym przykładzie `GetFileHash` użyto zadania do określenia `FilesToHash` i wydrukowania sumy kontrolnej elementów.

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