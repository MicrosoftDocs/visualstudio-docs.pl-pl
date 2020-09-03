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
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814827"
---
# <a name="expected-"></a>Oczekiwano znaku " \@ "
Podjęto próbę utworzenia zmiennej, która będzie używana z instrukcją kompilacji warunkowej przy użyciu `@set` instrukcji, ale nie umieścić znaku " **@** " przed nazwą zmiennej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj znak " **@** " bezpośrednio przed nazwą zmiennej. Na przykład:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [@set Merge](../../javascript/reference/at-set-statement-javascript.md)   
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)
