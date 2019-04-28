---
title: Efektywne używanie pamięci podczas kompilowania dużych projektów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab3be342f31e5df018c14f84d30febd38c31c401
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786209"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektywnie wykorzystać pamięci podczas kompilowania dużych projektów
Duże projekty często zawierają wiele podprojekty i inne zależności, które mogą wykorzystywać duże ilości pamięci systemowej w czasie kompilacji. Gdy jest zmniejszenie ilości dostępnej pamięci systemowej, wydajność systemu również można zmniejszyć. Starsze wersje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów pozostaje w pamięci. W wersji 3.5 usunięte starszej wersji projektów, ale przechowywane wyniki kompilacji w pamięci podręcznej pobierania nowsze.

 Wersja 4.0 obsługuje to zarządzanie pamięcią automatycznie, zapisywanie projektów z konieczności używania właściwości, takie jak `UnloadProjectsOnCompletion` i `UseResultsCache`.

### <a name="see-also"></a>Zobacz także
- [Tworzenie wielu projektów wykonywane równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)