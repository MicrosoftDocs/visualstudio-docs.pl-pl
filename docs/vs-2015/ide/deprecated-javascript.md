---
title: '&lt;deprecated &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665805"
---
# <a name="ltdeprecatedgt-javascript"></a>&gt; &lt;deprecated (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa przestarzałą funkcję lub metodę.

## <a name="syntax"></a>Składnia

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parametry
 `type` opcjonalny. Określa, czy funkcja lub metoda zostanie usunięta w przyszłych wydaniach, czy funkcja lub metoda została już usunięta i że jej użycie może spowodować wystąpienie błędu. Ustaw wartość `deprecate`, aby określić, że funkcja lub metoda zostanie usunięta w przyszłej wersji. Ustaw na `remove`, aby określić, że funkcja lub metoda została już usunięta.

 `locid` opcjonalny. Identyfikator informacji o lokalizacji dotyczącej funkcji lub metody. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc >](../ide/loc-javascript.md) elementu.

 `description` opcjonalny. Opis funkcji lub metody, która jest przestarzała.

## <a name="remarks"></a>Uwagi
 Elementy służące do dodawania adnotacji do funkcji, które zawierają `<deprecated>`, muszą być umieszczone w treści funkcji przed dowolnymi instrukcjami. Po oznaczeniu funkcji jako przestarzałej zaleca się zamienienie jej [\<summary >](../ide/summary-javascript.md) elementu z elementem `<deprecated>`.

## <a name="example"></a>Przykład
 Poniższy kod pokazuje, jak używać elementu `<deprecated>`.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
