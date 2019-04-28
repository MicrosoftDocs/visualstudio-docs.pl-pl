---
title: Oczekiwano instrukcji "catch" | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935402"
---
# <a name="expected-catch"></a>Oczekiwano instrukcji „catch"
Została użyta Obsługa wyjątków **spróbuj** blokują, ale nie zapisano skojarzonego **catch** instrukcji. Mechanizm obsługi wyjątków wymaga zawinięta kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie powinien zostać wykonany, jeżeli wystąpi wyjątek, wewnątrz **spróbuj** bloku. Wyjątki są zgłaszane z poziomu **spróbuj** zablokowane, używając **throw** instrukcji, a przechwycony poza **spróbuj** blok z co najmniej jeden **catch**instrukcji.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj powiązane **catch** bloku.  
  
- Spróbuj użyć **na koniec** block zamiast **catch** bloku.  
  
## <a name="see-also"></a>Zobacz też  
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error, obiekt](../../javascript/reference/error-object-javascript.md)