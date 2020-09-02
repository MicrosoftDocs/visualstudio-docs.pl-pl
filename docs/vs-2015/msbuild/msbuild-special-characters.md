---
title: Znaki specjalne MSBuild | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150763"
---
# <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rezerwuje kilka znaków do użytku specjalnego w określonych kontekstach. Musisz tylko wypróbować takie znaki, jeśli chcesz ich używać dosłownie w kontekście, w którym są zarezerwowane. Na przykład gwiazdka ma specjalne znaczenie tylko w `Include` `Exclude` atrybutach i definicji elementu oraz w wywołaniach do `CreateItem` . Jeśli chcesz, aby gwiazdka była wyświetlana jako gwiazdka w jednym z tych kontekstów, musisz ją wypróbować. W każdym innym kontekście wystarczy wpisać gwiazdkę, w której ma się pojawić.  
  
 Aby wprowadzić znak specjalny, użyj składni%*XX*, gdzie *XX* reprezentuje wartość szesnastkową ASCII znaku. Aby uzyskać więcej informacji, zobacz [jak: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Znaki specjalne  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] znaki specjalne:  
  
|**Opis**|**ASCII**|**Użycie zarezerwowane**|  
|-------------------|---------------|------------------------|  
|%|%25|Odwołania do metadanych|  
|$|%24|Właściwości odwołania|  
|@|%40|Odwołania do list elementów|  
|'|%27|Warunki i inne wyrażenia|  
|;|% 3B|Separator listy|  
|?|% 3F|Symbol wieloznaczny dla nazw plików w `Include` `Exclude` atrybutach i|  
|*|%2A|Symbol wieloznaczny do użycia w nazwach plików w `Include` `Exclude` atrybutach i|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)   
 [Elementy](../msbuild/msbuild-items.md)
