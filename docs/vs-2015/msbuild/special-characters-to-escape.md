---
title: Znaki specjalne wyjścia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659686"
---
# <a name="special-characters-to-escape"></a>Znaki specjalne wyjścia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tylko wtedy, gdy mają one specjalnego znaczenia w kontekście, w którym są one używane, należy użyć znaków ucieczki znaków specjalnych. Na przykład znak gwiazdki (*) jest znakiem specjalnym, tylko w atrybutach "Include" i "Wyklucz" definicji elementu lub w wywołaniu <xref:Microsoft.Build.Tasks.CreateItem>. We wszystkich innych przypadkach gwiazdka jest traktowany jako literał gwiazdki. Gdy jest konieczne ucieczki gwiazdki wszędzie, gdzie w plikach projektu, to to samo dotyczy żadnych szkód.  
  
 Użyj % notacji*xx* zamiast znaki specjalne, gdzie *xx* reprezentuje wartości szesnastkowej znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znak literałowy, użyj wartości `%2A`.  
  
 Pełną listę znaki specjalne wyjścia są następujące:  
  
|Znak|Opis|  
|---------------|-----------------|  
|%|Używany znak procentu, aby odwoływać się do metadanych.|  
|$|Znak dolara, używany do odwoływać się do właściwości.|  
|@|Znak używany do odwoływać się do elementu listy.|  
|(|Nawiasem otwierającym używane na listach.|  
|)|Nawiasu zamykającego używane na listach.|  
|`| Apostrof (lub znacznika) używane w warunkach i inne wyrażenia.|  
|;|Średnik jest separatorem listy.|  
|?|Znak zapytania, symbolu wieloznacznego w opisie specyfikacji pliku, w sekcji uwzględniania/wykluczania elementów.|  
|*|Gwiazdka jest symbolem wieloznacznym podczas opisywania specyfikacji pliku, w sekcji uwzględniania/wykluczania elementów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
