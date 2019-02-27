---
title: Nie może być instrukcja "break" poza pętlą | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 36551a1a70973409768b7971545c783b3621ffb6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839896"
---
# <a name="cant-have-break-outside-of-loop"></a>Instrukcja „break" nie może występować poza pętlą
Podjęto próbę użycia **podziału** — słowo kluczowe poza pętlą. **Podziału** słowo kluczowe jest używane do zakończenia pętli lub `switch` instrukcji. Muszą być osadzone w treści pętli lub `switch` instrukcji. Jednak **etykiety** wykonać break — słowo kluczowe.  
  
```js
break labelname;  
```  
  
 Wystarczy etykietami formie **podziału** — słowo kluczowe podczas korzystania z zagnieżdżonej pętli lub `switch` instrukcji i potrzeb dotyczących zerwać pętlę, która nie jest to najbardziej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że **podziału** — słowo kluczowe pojawia się wewnątrz instrukcji otaczającej pętli lub przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [BREAK — instrukcja](../../javascript/reference/break-statement-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [Rozwiązywanie problemów ze skryptami](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)