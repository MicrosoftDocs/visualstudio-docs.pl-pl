---
title: Wyjątek zgłoszony i nieprzechwycony | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1e34be9f8eab5171af0e2553d5777b0958bf3c2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840873"
---
# <a name="exception-thrown-and-not-caught"></a>Wyjątek zgłoszony i nieprzechwycony
Możesz się `throw` instrukcji w kodzie, ale nie znajdował się w obrębie **spróbuj** bloku, lub nie skojarzono nie **catch** bloku, aby można było wyłapać błąd. Wyjątki są zgłaszane z poziomu **spróbuj** zablokowane, używając **throw** instrukcji i przechwycony poza **spróbuj** blokowania z **catch** Instrukcja.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Należy wpisać kod, który może zgłosić wyjątek w **spróbuj** zablokować, a także upewnij się, jest odpowiedni **catch** bloku.  
  
-   Upewnij się, że instrukcji catch oczekuje formie poprawny wyjątek.  
  
-   Jeśli wyjątek jest zgłaszany ponownie, upewnij się, że istnieje inny odpowiedniej instrukcji catch.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)   
 [Throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally, instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)