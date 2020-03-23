---
title: Efektywne korzystanie z pamięci podczas tworzenia dużych projektów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631318"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektywne korzystanie z pamięci podczas tworzenia dużych projektów

Duże projekty często zawierają wiele podprojektów i innych zależności, które mogą zużywać dużo pamięci systemowej w czasie kompilacji. Gdy ilość dostępnej pamięci systemowej zostanie zmniejszona, wydajność systemu również może zostać zmniejszona. Starsze wersje projektów MSBuild pozostały w pamięci. Wersja 3.5 usunęła starsze wersje projektów, ale zachowane wyniki kompilacji w pamięci podręcznej do późniejszego pobrania.

 Wersja 4.0 automatycznie obsługuje to zarządzanie pamięcią, oszczędzając projekty `UnloadProjectsOnCompletion` `UseResultsCache`przed koniecznością używania właściwości, takich jak i .

### <a name="see-also"></a>Zobacz też

- [Twórz wiele projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
