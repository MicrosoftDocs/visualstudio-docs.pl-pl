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
ms.openlocfilehash: a96831650e09b1018c6cffc8149a9a0020edc90b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793103"
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
