---
title: MSBuild Znane metadane elementu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633099"
---
# <a name="msbuild-well-known-item-metadata"></a>MsBuild dobrze znane metadane elementu

W poniższej tabeli opisano metadane przypisane do każdego elementu podczas tworzenia. W każdym przykładzie następująca deklaracja elementu została użyta do uwzględnienia pliku *C:\MyProject\Source\Program.cs* w projekcie.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadane elementu|Opis|
|-------------------|-----------------|
|%(FullPath)|Zawiera pełną ścieżkę elementu. Przykład:<br /><br /> *C:\MyProject\Źródło\Program.cs*|
|%(RootDir)|Zawiera katalog główny elementu. Przykład:<br /><br /> *C:\\*|
|%(Nazwa pliku)|Zawiera nazwę pliku elementu bez rozszerzenia. Przykład:<br /><br /> *Program*|
|%(Rozszerzenie)|Zawiera rozszerzenie nazwy pliku elementu. Przykład:<br /><br /> *.cs*|
|%(RelativeDir)|Zawiera ścieżkę określoną `Include` w atrybucie, aż\\do ostatecznego ukośnika odwrotnego ( ). Przykład:<br /><br /> *Źródła\\*<br /><br /> Jeśli `Include` atrybut jest pełną ścieżką, `%(RelativeDir)` zaczyna się `%(RootDir)`od katalogu głównego .  Przykład: <br /><br /> *C:\MyProject\Źródło\\*|
|%(Katalog)|Zawiera katalog elementu bez katalogu głównego. Przykład:<br /><br /> *Źródło MyProject\\\\*|
|%(RekurencyjnyDir)|Jeśli `Include` atrybut zawiera symbol \* \*wieloznaczny, metadane określają część ścieżki, która zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [Jak: Wybieranie plików do utworzenia](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source\\ * zawiera plik *Program.cs*, a plik projektu zawiera ten element:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> wtedy wartość `%(MyItem.RecursiveDir)` będzie *MySolution\MyProject\Source\\*.|
|%(Tożsamość)|Element określony w `Include` atrybucie. Przykład:<br /><br /> *Źródło\Program.cs*|
|%(ModifiedTime)|Zawiera sygnaturę czasowa z ostatniej modyfikacji elementu. Przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Zawiera sygnaturę czasowa z momentu utworzenia elementu. Przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Zawiera sygnaturę czasowa z ostatniego dostępu do elementu.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Zobacz też

- [Items](../msbuild/msbuild-items.md)
- [Tworzenie partii](../msbuild/msbuild-batching.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
