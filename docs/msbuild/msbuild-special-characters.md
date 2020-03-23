---
title: Znaki specjalne MSBuild | Dokumenty firmy Microsoft
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
ms.openlocfilehash: fdc9024db06fe27fab5dfdf9589300a6eb671368
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633216"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne MSBuild

MSBuild zastrzega niektóre znaki do specjalnego użycia w określonych kontekstach. Musisz uciec od takich znaków tylko wtedy, gdy chcesz ich używać dosłownie w kontekście, w którym są zarezerwowane. Na przykład gwiazdka ma specjalne znaczenie `Include` tylko `Exclude` w i atrybuty definicji `CreateItem`elementu i wywołania . Jeśli gwiazdka ma być wyświetlana jako gwiazdka w jednym z tych kontekstów, należy jej uniknąć. W każdym innym kontekście po prostu wpisz gwiazdkę, w której ma się pojawić.

 Aby uniknąć znaku specjalnego, należy użyć\<składni % xx \<>, gdzie xx> reprezentuje ascii szesnastkową wartość znaku. Aby uzyskać więcej informacji, zobacz [Jak: Ucieczka znaków specjalnych w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Znaki specjalne

 W poniższej tabeli wymieniono znaki specjalne MSBuild:

|**Znak**|**Ascii**|**Zarezerwowane użycie**|
|-------------------|---------------|------------------------|
|%|%25|Odwoływanie się do metadanych|
|$|%24|Odwoływanie się do właściwości|
|@|%40|Odwoływanie się do list elementów|
|'|%27|Warunki i inne wyrażenia|
|;|%3B|Separator listy|
|?|%3F|Symbol wieloznaczny dla `Include` `Exclude` nazw plików i atrybutów|
|*|%2A|Symbol wieloznaczny do użycia `Include` `Exclude` w nazwach plików i atrybutach|

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
- [Items](../msbuild/msbuild-items.md)
