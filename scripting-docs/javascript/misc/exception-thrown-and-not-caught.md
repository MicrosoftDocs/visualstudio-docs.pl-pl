---
title: Wyjątek zgłoszony i nieprzechwycony | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349039"
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