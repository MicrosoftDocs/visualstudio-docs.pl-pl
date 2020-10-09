---
title: Oczekiwano znaku "@" | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98a35421054e4d2236fe509224ed146063b61a79
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862300"
---
# <a name="expected-"></a>Oczekiwano znaku „\@”
Podjęto próbę utworzenia zmiennej, która będzie używana z instrukcją kompilacji warunkowej przy użyciu `@set` instrukcji, ale nie umieścić znaku " **@** " przed nazwą zmiennej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj znak " **@** " bezpośrednio przed nazwą zmiennej. Na przykład:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [@set Merge](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Kompilacja warunkowa](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Zmienne kompilacji warunkowej](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))