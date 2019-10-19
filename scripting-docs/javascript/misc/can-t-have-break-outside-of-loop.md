---
title: Element "Break" nie może występować poza pętlą | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576021"
---
# <a name="cant-have-break-outside-of-loop"></a>Instrukcja „break" nie może występować poza pętlą
Próbowano użyć słowa kluczowego **Break** poza pętlą. Słowo kluczowe **Break** służy do kończenia pętli lub instrukcji `switch`. Musi być osadzony w treści pętli lub instrukcji `switch`. Jednak **etykieta** może być zgodna ze słowem kluczowym Break.  
  
```js
break labelname;  
```  
  
 W przypadku używania pętli zagnieżdżonych lub instrukcji `switch` jest wymagana tylko etykieta z etykietą **Break** , która musi zostać przerwana przez pętlę, która nie jest wewnętrzna.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że słowo kluczowe **Break** pojawia się wewnątrz otaczającej pętli lub instrukcji switch.  
  
## <a name="see-also"></a>Zobacz także  
 [instrukcja break](../../javascript/reference/break-statement-javascript.md)    
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)    
 [Rozwiązywanie problemów ze skryptami](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)