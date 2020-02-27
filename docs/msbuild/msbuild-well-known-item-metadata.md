---
title: Metadane dobrze znanego elementu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633099"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadane dobrze znanego elementu MSBuild

W poniższej tabeli opisano metadane przypisane do każdego elementu podczas tworzenia. W każdym przykładzie następująca deklaracja elementu została użyta w celu uwzględnienia *C:\MyProject\Source\Program.cs* pliku w projekcie.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadane elementu|Opis|
|-------------------|-----------------|
|%(FullPath)|Zawiera pełną ścieżkę do elementu. Na przykład:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Zawiera katalog główny elementu. Na przykład:<br /><br /> *C:\\*|
|% (Filename)|Zawiera nazwę pliku elementu, bez rozszerzenia. Na przykład:<br /><br /> *Program*|
|% (Rozszerzenie)|Zawiera rozszerzenie nazwy pliku elementu. Na przykład:<br /><br /> *. cs*|
|%(RelativeDir)|Zawiera ścieżkę określoną w atrybucie `Include`, do końcowego ukośnika odwrotnego (\\). Na przykład:<br /><br /> *\\ źródłowa*<br /><br /> Jeśli atrybut `Include` jest pełną ścieżką, `%(RelativeDir)` rozpoczyna się od katalogu głównego `%(RootDir)`.  Na przykład: <br /><br /> *C:\MyProject\Source\\*|
|% (Katalog)|Zawiera katalog elementu, bez katalogu głównego. Na przykład:<br /><br /> *\\ źródła\\projektu*|
|%(RecursiveDir)|Jeśli `Include` atrybut zawiera \*symbol wieloznaczny \*, to metadane określają część ścieżki, która zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [How to: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source\\* zawiera plik *program.cs*, a plik projektu zawiera ten element:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> następnie wartość `%(MyItem.RecursiveDir)` byłaby *MySolution\MyProject\Source\\* .|
|% (Tożsamość)|Element określony w atrybucie `Include`. Na przykład:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Zawiera sygnaturę czasową od ostatniej modyfikacji elementu. Na przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Zawiera sygnaturę czasową od momentu utworzenia elementu. Na przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Zawiera sygnaturę czasową od ostatniego dostępu do elementu.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Zobacz też

- [Elementy](../msbuild/msbuild-items.md)
- [Tworzenie partii](../msbuild/msbuild-batching.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
