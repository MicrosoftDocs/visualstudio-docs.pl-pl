---
title: Znaki specjalne w programie MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a54f446cb82b3181ee057d4887b37940868a5920
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59650801"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rezerwuje niektórych znaków specjalnych w określonych kontekstach. Masz tylko takie znaki ucieczki, aby ich używać dosłownie w kontekście, w którym są one zarezerwowane. Na przykład znak gwiazdki ma specjalne znaczenie tylko w `Include` i `Exclude` atrybuty definicji elementu i w wywołaniach `CreateItem`. Jeśli chcesz, aby znak gwiazdki, aby pojawiało się jako znak gwiazdki w jednym z tych kontekstach, musisz wyjść z niego. W każdym kontekście wystarczy wpisać gwiazdkę, w której ma się pojawić.  
  
 Aby znak specjalny, należy użyć składni %*xx*, gdzie *xx* reprezentuje wartości szesnastkowej znaku ASCII. Aby uzyskać więcej informacji, zobacz [jak: Znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Znaki specjalne  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] znaki specjalne:  
  
|**Znak**|**ASCII**|**Użycie zarezerwowanych**|  
|-------------------|---------------|------------------------|  
|%|%25|Odwoływanie się do metadanych|  
|$|%24|Właściwości odwołania|  
|@|%40|Odwołujący się listy elementów|  
|'|%27|Warunki i inne wyrażenia|  
|;|%3B|Separator listy|  
|?|%3F|Znak symbolu wieloznacznego dla nazwy plików w `Include` i `Exclude` atrybutów|  
|*|%2A|Znak symbolu wieloznacznego do użytku w nazwach plików w `Include` i `Exclude` atrybutów|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)   
 [Elementy](../msbuild/msbuild-items.md)
