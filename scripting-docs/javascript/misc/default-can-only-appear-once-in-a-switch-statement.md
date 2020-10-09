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
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862781"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>Element „default” może wystąpić tylko raz w instrukcji „switch”.
Próbowano użyć instrukcji **default** więcej niż raz w instrukcji switch. Domyślna wielkość liter jest zawsze ostatnią instrukcją case w instrukcji switch (jest to przypadek przypadający).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń wszelkie dodatkowe **domyślne** instrukcje Case z `switch` instrukcji (Użyj co najwyżej jednej domyślnej instrukcji case w instrukcji switch).  
  
## <a name="see-also"></a>Zobacz też  
 [Switch, instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Sterowanie przepływem programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Słowa zastrzeżone JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)