---
title: Oczekiwano obiektu logicznego | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 261cf0ad93208c0eac09e42dcd68853352318e88
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149159"
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