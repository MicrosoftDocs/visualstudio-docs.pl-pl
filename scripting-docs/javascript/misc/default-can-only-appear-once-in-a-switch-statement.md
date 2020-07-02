---
title: element "default" może wystąpić tylko raz w instrukcji "switch" | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fdce6a86665b942098e4542dc237bc1ef22ad8a
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815516"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>Element „default” może wystąpić tylko raz w instrukcji „switch”.
Próbowano użyć instrukcji **default** więcej niż raz w instrukcji switch. Domyślna wielkość liter jest zawsze ostatnią instrukcją case w instrukcji switch (jest to przypadek przypadający).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń wszelkie dodatkowe **domyślne** instrukcje Case z `switch` instrukcji (Użyj co najwyżej jednej domyślnej instrukcji case w instrukcji switch).  
  
## <a name="see-also"></a>Zobacz także  
 [Switch, instrukcja](../../javascript/reference/switch-statement-javascript.md)   
 [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)   
 [Słowa zastrzeżone JavaScript](../../javascript/reference/javascript-reserved-words.md)