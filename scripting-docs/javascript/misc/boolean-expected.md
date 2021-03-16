---
description: Podjęto próbę wywołania metody Boolean. prototype. toString lub Boolean. prototype. valueOf na obiekcie typu innego niż wartość logiczna.
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
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571444"
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

- [Boolean, obiekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Typy danych](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Sterowanie przepływem programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Kopiowanie, przekazywanie i porównywanie danych](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
