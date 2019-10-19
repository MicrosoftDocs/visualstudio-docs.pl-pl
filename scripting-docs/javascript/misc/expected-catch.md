---
title: Oczekiwano instrukcji "Catch" | Microsoft Docs
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573428"
---
# <a name="expected-catch"></a>Oczekiwano instrukcji „catch"
Użyto bloku **try** obsługi wyjątków, ale nie zapisał skojarzonej instrukcji **catch** . Mechanizm obsługi wyjątków wymaga, aby kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie powinien zostać wykonany w przypadku wystąpienia wyjątku, być opakowany wewnątrz bloku **try** . Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** z co najmniej jedną instrukcją **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj skojarzony blok **catch** .  
  
- Spróbuj użyć bloku **finally** zamiast bloku **catch** .  
  
## <a name="see-also"></a>Zobacz także  
 [spróbuj... catch... finally   instrukcji](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)  
 [Error, obiekt](../../javascript/reference/error-object-javascript.md)