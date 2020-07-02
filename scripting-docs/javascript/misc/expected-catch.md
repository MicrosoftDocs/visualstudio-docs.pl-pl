---
title: Oczekiwano instrukcji "Catch" | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816687"
---
# <a name="expected-catch"></a>Oczekiwano instrukcji „catch"
Użyto bloku **try** obsługi wyjątków, ale nie zapisał skojarzonej instrukcji **catch** . Mechanizm obsługi wyjątków wymaga, aby kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie powinien zostać wykonany w przypadku wystąpienia wyjątku, być opakowany wewnątrz bloku **try** . Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** z co najmniej jedną instrukcją **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj skojarzony blok **catch** .  
  
- Spróbuj użyć bloku **finally** zamiast bloku **catch** .  
  
## <a name="see-also"></a>Zobacz także  
 [Spróbuj... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error, obiekt](../../javascript/reference/error-object-javascript.md)