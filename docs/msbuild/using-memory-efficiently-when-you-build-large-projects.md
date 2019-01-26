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
ms.openlocfilehash: 5d18f78a0ceec7b79388f53f83909e4dcbcf3b86
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923536"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektywnie wykorzystać pamięci podczas kompilowania dużych projektów
Duże projekty często zawierają wiele podprojekty i inne zależności, które mogą wykorzystywać duże ilości pamięci systemowej w czasie kompilacji. Gdy jest zmniejszenie ilości dostępnej pamięci systemowej, wydajność systemu również można zmniejszyć. Starsze wersje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów pozostaje w pamięci. W wersji 3.5 usunięte starszej wersji projektów, ale przechowywane wyniki kompilacji w pamięci podręcznej pobierania nowsze.  
  
 Wersja 4.0 obsługuje to zarządzanie pamięcią automatycznie, zapisywanie projektów z konieczności używania właściwości, takie jak `UnloadProjectsOnCompletion` i `UseResultsCache`.  
  
### <a name="see-also"></a>Zobacz także  
 [Tworzenie wielu projektów wykonywane równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)