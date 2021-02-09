---
title: Metadane dobrze znanego elementu MSBuild | Microsoft Docs
description: Dowiedz się więcej na temat metadanych programu MSBuild przypisanych do każdego elementu podczas tworzenia i pewnych opcjonalnych metadanych programu MSBuild, które można zdefiniować, aby kontrolować zachowanie kompilacji.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9ca2249e6119e27574791a2cbd9e8b09a9bde63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878186"
---
# <a name="msbuild-well-known-item-metadata"></a>Dobrze znane metadane elementów programu MSBuild

Metadane elementu są wartościami dołączonymi do elementów. Niektóre z nich są przypisywane przez program MSBuild do elementów podczas tworzenia elementów, ale można także definiować wymagane metadane. Niektóre wartości metadanych zdefiniowane przez użytkownika mają znaczenie dla programu MSBuild, określonych zadań zadań lub zestawów SDK, takich jak zestaw SDK platformy .NET.

W pierwszej tabeli w tym artykule opisano metadane przypisane do każdego elementu podczas tworzenia. W następnej tabeli przedstawiono kilka opcjonalnych metadanych, które mają znaczenie dla programu MSBuild, który można zdefiniować w celu sterowania zachowaniem kompilacji. W każdym przykładzie następująca deklaracja elementu została użyta w celu uwzględnienia *C:\MyProject\Source\Program.cs* pliku w projekcie.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadane elementu|Opis|
|-------------------|-----------------|
|% (FullPath)|Zawiera pełną ścieżkę do elementu. Na przykład:<br /><br /> *C:\MyProject\Source\Program.cs*|
|% (RootDir)|Zawiera katalog główny elementu. Na przykład:<br /><br /> *S\\*|
|% (Filename)|Zawiera nazwę pliku elementu, bez rozszerzenia. Na przykład:<br /><br /> *Program*|
|% (Rozszerzenie)|Zawiera rozszerzenie nazwy pliku elementu. Na przykład:<br /><br /> *. cs*|
|%(RelativeDir)|Zawiera ścieżkę określoną w `Include` atrybucie, do końcowego ukośnika odwrotnego ( \\ ). Na przykład:<br /><br /> *Element źródłowy\\*<br /><br /> Jeśli `Include` atrybut jest pełną ścieżką, zaczyna się od `%(RelativeDir)` katalogu głównego `%(RootDir)` .  Na przykład: <br /><br /> *C:\MyProject\Source\\*|
|% (Katalog)|Zawiera katalog elementu, bez katalogu głównego. Na przykład:<br /><br /> *Źródło projektu \\\\*|
|%(RecursiveDir)|Jeśli `Include` atrybut zawiera symbol wieloznaczny \* \* , metadane określają część ścieżki, która zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [How to: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source \\* zawiera plik *program.cs*, a plik projektu zawiera ten element:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> następnie wartość `%(MyItem.RecursiveDir)` zostałaby *\\ MySolution\MyProject\Source*.|
|% (Tożsamość)|Element określony w `Include` atrybucie. Na przykład:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Zawiera sygnaturę czasową od ostatniej modyfikacji elementu. Na przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Zawiera sygnaturę czasową od momentu utworzenia elementu. Na przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Zawiera sygnaturę czasową od ostatniego dostępu do elementu.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Zobacz też

- [Wspólne metadane elementów programu MSBuild](common-msbuild-item-metadata.md)
- [Elementy](../msbuild/msbuild-items.md)
- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
