---
title: Wydajne używanie pamięci podczas kompilowania dużych projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178300"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Efektywne używanie pamięci podczas kompilowania dużych projektów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Duże projekty często zawierają wiele projektów podrzędnych i innych zależności i mogą zużywać dużą ilość pamięci systemowej w czasie kompilacji. Po zmniejszeniu dostępnej pamięci systemowej może ulec również obniżenie wydajności systemu. Starsze wersje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów pozostawały w pamięci lub, w wersji 3,5, projekty zostały usunięte, ale wyniki kompilacji są przechowywane w pamięci podręcznej do późniejszego pobrania.  
  
 Wersja 4,0 obsługuje automatyczne zarządzanie pamięcią, dzięki czemu zapisywanie projektów nie będzie miało zastosowania właściwości takich jak  `UnloadProjectsOnCompletion` i `UseResultsCache` .  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
