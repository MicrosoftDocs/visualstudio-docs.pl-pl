---
title: 'Jak: Ucieczka znaków specjalnych w MSBuild | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: f9958ae93e2605ad3c89decb4ac9fabc18102148
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633879"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Jak: Ucieczka znaków specjalnych w MSBuild

Niektóre znaki mają specjalne znaczenie w plikach projektu MSBuild. Przykłady znaków obejmują średniki`;`( ) i gwiazdki (`*`). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [MSBuild znaki specjalne](../msbuild/msbuild-special-characters.md).

Aby użyć tych znaków specjalnych jako literałów w pliku projektu, muszą być `%<xx>`określone `<xx>` przy użyciu składni , gdzie reprezentuje ascii szesnastkowej wartości znaku.

## <a name="msbuild-special-characters"></a>Znaki specjalne MSBuild

Jednym z przykładów, gdzie znaki `Include` specjalne są używane jest w atrybucie list towarów. Na przykład na poniższej liście elementów zadeklarowane są dwa elementy: *MyFile.cs* i *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Jeśli chcesz zadeklarować element, który zawiera średnik w nazwie, `%<xx>` należy użyć składni, aby uniknąć średnika i zapobiec MSBuild z deklarowania dwóch oddzielnych elementów. Na przykład następujący element wycofuje średnik i `MyFile.cs;MyClass.cs`deklaruje jeden element o nazwie .

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Można również użyć [funkcji właściwości,](../msbuild/property-functions.md) aby uniknąć ciągów. Na przykład jest to równoważne z powyższym przykładem.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć znaku specjalnego MSBuild jako znaku dosłownego

Użyj notacji `%<xx>` zamiast znaku specjalnego, `<xx>` gdzie reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (`*`) jako znaku `%2A`literału, użyj wartości .

## <a name="see-also"></a>Zobacz też
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Items](../msbuild/msbuild-items.md)
