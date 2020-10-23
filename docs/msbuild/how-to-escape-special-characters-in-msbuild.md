---
title: 'Instrukcje: znaki specjalne ucieczki w MSBuild | Microsoft Docs'
description: Dowiedz się, jak wypróbować znaki specjalne, aby można było używać tych znaków jako literałów w plikach projektów programu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 923c517653c42dd0362b398c420c99454ccf4034
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436409"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Instrukcje: znaki specjalne ucieczki w MSBuild

Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykłady znaków obejmują średnika ( `;` ) i gwiazdki ( `*` ). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).

Aby można było używać tych znaków specjalnych jako literałów w pliku projektu, muszą one być określone przy użyciu składni `%<xx>` , gdzie `<xx>` reprezentuje wartość szesnastkową ASCII znaku.

## <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild

Przykładem miejsca, w którym są używane znaki specjalne, znajduje się w `Include` atrybucie list elementów. Na przykład następująca lista elementów deklaruje dwie elementy: *myfile.cs* i *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Jeśli chcesz zadeklarować element, który zawiera średnik w nazwie, należy użyć `%<xx>` składni w celu wyznaczenia średnika i uniemożliwić programowi MSBuild deklarowanie dwóch oddzielnych elementów. Na przykład poniższy element wyprowadza średnik i deklaruje jeden element o nazwie `MyFile.cs;MyClass.cs` .

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Do ciągów ucieczki można także użyć [funkcji właściwości](../msbuild/property-functions.md) . Na przykład jest to odpowiednik powyższego przykładu.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć znaku specjalnego MSBuild jako znaku literału

Użyj notacji `%<xx>` zamiast znaku specjalnego, gdzie `<xx>` reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki ( `*` ) jako znaku literału, użyj wartości `%2A` .

## <a name="see-also"></a>Zobacz też
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Elementy](../msbuild/msbuild-items.md)
