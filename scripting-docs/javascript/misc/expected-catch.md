---
title: Oczekiwano instrukcji "catch" | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801986"
---
# <a name="expected-catch"></a>Oczekiwano instrukcji „catch"
Została użyta Obsługa wyjątków **spróbuj** blokują, ale nie zapisano skojarzonego **catch** instrukcji. Mechanizm obsługi wyjątków wymaga zawinięta kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie powinien zostać wykonany, jeżeli wystąpi wyjątek, wewnątrz **spróbuj** bloku. Wyjątki są zgłaszane z poziomu **spróbuj** zablokowane, używając **throw** instrukcji, a przechwycony poza **spróbuj** blok z co najmniej jeden **catch**instrukcji.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj powiązane **catch** bloku.  
  
-   Spróbuj użyć **na koniec** block zamiast **catch** bloku.  
  
## <a name="see-also"></a>Zobacz też  
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error, obiekt](../../javascript/reference/error-object-javascript.md)