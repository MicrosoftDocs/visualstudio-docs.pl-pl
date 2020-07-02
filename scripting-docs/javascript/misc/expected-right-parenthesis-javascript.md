---
title: Oczekiwano znaku ")" (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2fb72012-0f83-40fa-b747-167940d90bdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d109f91e447bc96612dae82d0141d717eaa1f20c
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817583"
---
# <a name="expected--javascript"></a>Oczekiwano „)" (JavaScript)
Próbowano umieścić wyrażenie w zestawie nawiasów, ale nie zawiera nawiasu zamykającego. Niektóre wyrażenia muszą być ujęte w zestaw otwierających i zamykających nawiasów. Zwróć uwagę na użycie nawiasów w poniższym przykładzie.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj prawy nawias do wyrażenia oceny.