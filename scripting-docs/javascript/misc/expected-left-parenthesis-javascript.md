---
title: Oczekiwano znaku "(" (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adcabbe0b1d7ca7d0298202b5242049b86f8229a
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817102"
---
# <a name="expected--javascript"></a>Oczekiwano znaku „(" (JavaScript)
Próbowano umieścić wyrażenie w zestawie nawiasów, ale nie zawiera nawiasu otwierającego. Niektóre wyrażenia muszą być ujęte w zestaw otwierających i zamykających nawiasów. Zwróć uwagę na użycie nawiasów w poniższym przykładzie.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj lewy nawias do wyrażenia szacowania.