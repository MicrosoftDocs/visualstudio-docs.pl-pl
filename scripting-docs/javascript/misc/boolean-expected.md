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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862651"
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