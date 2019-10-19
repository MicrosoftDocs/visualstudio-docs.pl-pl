---
title: Oczekiwano wartości logicznej | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576055"
---
# <a name="boolean-expected"></a>Oczekiwano obiektu logicznego
Podjęto próbę wywołania metody **Boolean. prototype. ToString** lub **Boolean. prototype. valueOf** na obiekcie typu innego niż `Boolean`. Obiekt tego typu wywołania musi być typu `Boolean`. Na przykład:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Wywołaj metody **Boolean. prototype. ToString** lub **Boolean. prototype. valueOf** dla obiektów typu **Boolean.**

## <a name="see-also"></a>Zobacz także

- [Boolean, obiekt](../../javascript/reference/boolean-object-javascript.md)
- [Typy danych](../../javascript/data-types-javascript.md)
- [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopiowanie, przekazywanie i porównywanie danych](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)