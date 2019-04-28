---
title: 'Instrukcje: Znaki specjalne ucieczki w MSBuild | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 983e10f26e6fd1d8b4b7ff18c73edd65cb4810f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968109"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Instrukcje: Znaki specjalne ucieczki w MSBuild

Niektóre znaki mają specjalne znaczenie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu. Przykłady znaków średnikami (`;`) i gwiazdki (`*`). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).

Aby można było używać tych znaków specjalnych jako literały w pliku projektu, muszą one być określone przy użyciu składni `%<xx>`, gdzie `<xx>` reprezentuje wartości szesnastkowej znaku ASCII.

## <a name="msbuild-special-characters"></a>Znaki specjalne w MSBuild

Co znajduje się przykład użycia znaków specjalnych w `Include` atrybutu elementu listy. Na przykład na poniższej liście elementu deklaruje dwa elementy: *MyFile.cs* i *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Jeśli chcesz zadeklarować elementu, który zawiera średnikami w nazwie, należy użyć `%<xx>` składni ucieczki średnika i zapobiec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] od zadeklarowania dwa oddzielne elementy. Na przykład, następujący element specjalne średnika i deklaruje jeden element o nazwie `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Można również użyć [funkcji właściwości](../msbuild/property-functions.md) jako znak ucieczki dla ciągów. Na przykład jest to równoważne w powyższym przykładzie.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć znaku specjalnego MSBuild jako znak literału

Notacja `%<xx>` zamiast znaki specjalne, gdzie `<xx>` reprezentuje wartości szesnastkowej znaku ASCII. Na przykład, aby użyć gwiazdki (`*`) jako znak literałowy, użyj wartości `%2A`.

## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Elementy](../msbuild/msbuild-items.md)
