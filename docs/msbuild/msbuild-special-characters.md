---
title: Znaki specjalne MSBuild | Microsoft Docs
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f18339dbbddb09e44e8c5fa53ba517f3d60c025
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566062"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwuje kilka znaków do użytku specjalnego w określonych kontekstach. Musisz tylko wypróbować takie znaki, jeśli chcesz ich używać dosłownie w kontekście, w którym są zarezerwowane. Na przykład gwiazdka ma specjalne znaczenie tylko w atrybutach `Include` i `Exclude` definicji elementu, a w wywołaniach do `CreateItem`. Jeśli chcesz, aby gwiazdka była wyświetlana jako gwiazdka w jednym z tych kontekstów, musisz ją wypróbować. W każdym innym kontekście wystarczy wpisać gwiazdkę, w której ma się pojawić.

 Aby wprowadzić znak specjalny, użyj składni%\<XX >, gdzie \<XX > reprezentuje szesnastkową wartość ASCII znaku. Aby uzyskać więcej informacji, zobacz [jak: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Znaki specjalne
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] znaki specjalne:

|**Znak**|**ASCII**|**Użycie zarezerwowane**|
|-------------------|---------------|------------------------|
|%|%25|Odwołania do metadanych|
|$|%24|Właściwości odwołania|
|@|%40|Odwołania do list elementów|
|'|%27|Warunki i inne wyrażenia|
|;|%3B|Separator listy|
|?|%3F|Symbol wieloznaczny dla nazw plików w atrybutach `Include` i `Exclude`|
|*|%2A|Symbol wieloznaczny do użycia w nazwach plików w atrybutach `Include` i `Exclude`|

## <a name="see-also"></a>Zobacz także
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
- [Elementy](../msbuild/msbuild-items.md)
