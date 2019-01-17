---
title: Nie może być instrukcja "break" poza pętlą | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345048"
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