---
title: Wydajne używanie pamięci podczas kompilowania dużych projektów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631318"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Wydajne używanie pamięci podczas kompilowania dużych projektów

Duże projekty często zawierają wiele podprojektów i innych zależności, które mogą zużywać dużą ilość pamięci systemowej w czasie kompilacji. Po zmniejszeniu dostępnej pamięci systemowej może ulec również obniżenie wydajności systemu. Starsze wersje projektów programu MSBuild pozostawały w pamięci. W wersji 3,5 usunięto starsze wersje projektów, ale zachowane wyniki kompilacji są przechowywane w pamięci podręcznej na potrzeby późniejszego pobierania.

 Wersja 4,0 obsługuje automatyczne zarządzanie pamięcią, co pozwala na zapisywanie projektów przed użyciem takich właściwości jak `UnloadProjectsOnCompletion` i `UseResultsCache`.

### <a name="see-also"></a>Zobacz też

- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
