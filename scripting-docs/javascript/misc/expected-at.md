---
title: Oczekiwano znaku "@" | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576511"
---
# <a name="expected-"></a>Oczekiwano "\@"
Podjęto próbę utworzenia zmiennej, która będzie używana z instrukcją kompilacji warunkowej przy użyciu instrukcji `@set`, ale nie umieszczono znaku " **@** " przed nazwą zmiennej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj znak " **@** " bezpośrednio przed nazwą zmiennej. Na przykład:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Zobacz także  
   [instrukcji @set](../../javascript/reference/at-set-statement-javascript.md)  
 @No__t_1 [kompilacji warunkowej](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)
