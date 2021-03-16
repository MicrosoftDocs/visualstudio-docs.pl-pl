---
description: Próbowano użyć słowa kluczowego break poza pętlą.
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570651"
---
# <a name="cant-have-break-outside-of-loop"></a>Instrukcja „break" nie może występować poza pętlą
Próbowano użyć słowa kluczowego **Break** poza pętlą. Słowo kluczowe **Break** służy do kończenia pętli lub `switch` instrukcji. Musi być osadzony w treści pętli lub `switch` instrukcji. Jednak **etykieta** może być zgodna ze słowem kluczowym Break.  
  
```js
break labelname;  
```  
  
 **W przypadku** korzystania z zagnieżdżonych pętli lub `switch` instrukcji i należy przerwać pętlę, która nie jest zagłębią.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że słowo kluczowe **Break** pojawia się wewnątrz otaczającej pętli lub instrukcji switch.  
  
## <a name="see-also"></a>Zobacz też  
 [Break, instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Sterowanie przepływem programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Rozwiązywanie problemów ze skryptami](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
