---
title: Oczekiwano obiektu logicznego | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
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
ms.openlocfilehash: 82123fe2a38b3de1d6e6c015f47bc5f7edd02791
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840527"
---
# <a name="boolean-expected"></a>Oczekiwano obiektu logicznego
Podjęto próbę wywołania **Boolean.prototype.toString** lub **Boolean.prototype.valueOf** metody na obiekt typu innego niż `Boolean`. Obiekt tego typu wywołania musi być typu `Boolean`. Na przykład:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Tylko wywołania **Boolean.prototype.toString** lub **Boolean.prototype.valueOf** metod obiektów typu **Boolean.**

## <a name="see-also"></a>Zobacz też

- [Boolean, obiekt](../../javascript/reference/boolean-object-javascript.md)
- [Typy danych](../../javascript/data-types-javascript.md)
- [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopiowanie, przekazywanie i porównywanie danych](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)