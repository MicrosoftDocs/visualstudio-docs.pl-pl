---
title: Znaki specjalne w programie MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87013ff3a1911caa667f7ba431e408fc87a98f4
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2019
ms.locfileid: "59584483"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwuje niektórych znaków specjalnych w określonych kontekstach. Masz tylko takie znaki ucieczki, aby ich używać dosłownie w kontekście, w którym są one zarezerwowane. Na przykład znak gwiazdki ma specjalne znaczenie tylko w `Include` i `Exclude` atrybuty definicji elementu i w wywołaniach `CreateItem`. Jeśli chcesz, aby znak gwiazdki, aby pojawiało się jako znak gwiazdki w jednym z tych kontekstach, musisz wyjść z niego. W każdym kontekście wystarczy wpisać gwiazdkę, w której ma się pojawić.

 Aby znak specjalny, należy użyć składni %\<xx >, gdzie \<xx > reprezentuje wartości szesnastkowej znaku ASCII. Aby uzyskać więcej informacji, zobacz [jak: Znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Znaki specjalne
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] znaki specjalne:

|**Znak**|**ASCII**|**Użycie zarezerwowanych**|
|-------------------|---------------|------------------------|
|%|%25|Odwoływanie się do metadanych|
|$|%24|Właściwości odwołania|
|@|%40|Odwołujący się listy elementów|
|\'|%27|Warunki i inne wyrażenia|
|;|%3B|Separator listy|
|?|%3F|Znak symbolu wieloznacznego dla nazwy plików w `Include` i `Exclude` atrybutów|
|*|%2A|Znak symbolu wieloznacznego do użytku w nazwach plików w `Include` i `Exclude` atrybutów|

## <a name="see-also"></a>Zobacz także
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
- [Elementy](../msbuild/msbuild-items.md)