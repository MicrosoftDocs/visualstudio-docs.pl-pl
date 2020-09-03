---
title: Oczekiwano wartości logicznej | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817674"
---
# <a name="boolean-expected"></a>Oczekiwano obiektu logicznego
Podjęto próbę wywołania metody **Boolean. prototype. ToString** lub **Boolean. prototype. valueOf** na obiekcie typu innego niż `Boolean` . Obiekt tego typu wywołania musi być typu `Boolean` . Na przykład:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Wywołaj metody **Boolean. prototype. ToString** lub **Boolean. prototype. valueOf** dla obiektów typu **Boolean.**

## <a name="see-also"></a>Zobacz też

- [Boolean, obiekt](../../javascript/reference/boolean-object-javascript.md)
- [Typy danych](../../javascript/data-types-javascript.md)
- [Sterowanie przepływem programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopiowanie, przekazywanie i porównywanie danych](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)