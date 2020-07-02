---
title: Element "Break" nie może występować poza pętlą | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817661"
---
# <a name="cant-have-break-outside-of-loop"></a>Instrukcja „break" nie może występować poza pętlą
Próbowano użyć słowa kluczowego **Break** poza pętlą. Słowo kluczowe **Break** służy do kończenia pętli lub `switch` instrukcji. Musi być osadzony w treści pętli lub `switch` instrukcji. Jednak **etykieta** może być zgodna ze słowem kluczowym Break.  
  
```js
break labelname;  
```  
  
 **W przypadku** korzystania z zagnieżdżonych pętli lub `switch` instrukcji i należy przerwać pętlę, która nie jest zagłębią.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że słowo kluczowe **Break** pojawia się wewnątrz otaczającej pętli lub instrukcji switch.  
  
## <a name="see-also"></a>Zobacz także  
 [Break, instrukcja](../../javascript/reference/break-statement-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [Rozwiązywanie problemów ze skryptami](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)