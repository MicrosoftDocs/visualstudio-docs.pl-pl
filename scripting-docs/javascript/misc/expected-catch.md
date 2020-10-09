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
ms.openlocfilehash: 47411a6376cd843b3a12cf74ed1800775b98cd83
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861953"
---
# <a name="expected-catch"></a>Oczekiwano instrukcji „catch"
Użyto bloku **try** obsługi wyjątków, ale nie zapisał skojarzonej instrukcji **catch** . Mechanizm obsługi wyjątków wymaga, aby kod, który może zakończyć się niepowodzeniem, wraz z kodem, który nie powinien zostać wykonany w przypadku wystąpienia wyjątku, być opakowany wewnątrz bloku **try** . Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** z co najmniej jedną instrukcją **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Dodaj skojarzony blok **catch** .  
  
- Spróbuj użyć bloku **finally** zamiast bloku **catch** .  
  
## <a name="see-also"></a>Zobacz też  
 [Spróbuj... catch... finally — instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Error, obiekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)