---
title: '&lt;Returns &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669952"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Returns &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje dokumentacji dotyczące wyniku wywołania funkcji lub metody.

## <a name="syntax"></a>Składnia

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parametry
 `type` Obowiązkowe. Typ danych wartości zwracanej. Typ może być jednym z następujących:

- Typ języka ECMAScript w specyfikacji ECMAScript 5, taki jak `Number` i `Object` .

- Obiekt DOM, taki jak `HTMLElement` , `Window` , i `Document` .

- Funkcja konstruktora JavaScript.

  `integer` Obowiązkowe. Jeśli `type` jest `Number` , określa, czy wartość zwracana jest liczbą całkowitą. Ustaw na, aby `true` wskazać, że wartość zwracana jest liczbą całkowitą; w przeciwnym razie Ustaw jako `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` Obowiązkowe. Ten atrybut jest przestarzały; `type` atrybut ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy udokumentowana wartość zwracana jest elementem modelu DOM. Ustaw, aby `true` określić, że wartość zwracana jest elementem modelu dom; w przeciwnym razie Ustaw jako `false` . Jeśli `type` atrybut nie jest ustawiony i `domElement` jest ustawiony na `true` , IntelliSense traktuje udokumentowaną wartość zwracaną jako `HTMLElement` podczas uzupełniania instrukcji.

  `mayBeNull` Obowiązkowe. Określa, czy dla udokumentowanej wartości zwracanej można ustawić wartość null. Ustaw na `true` , aby wskazać, że wartość zwracana może być ustawiona na wartość null; w przeciwnym razie Ustaw jako `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` Obowiązkowe. Jeśli `type` jest `Array` , ten atrybut określa typ elementów w tablicy.

  `elementInteger` Obowiązkowe. Jeśli `type` jest `Array` i `elementType` ma `Number` , ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na, aby `true` wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` Obowiązkowe. Ten atrybut jest przestarzały; `elementType` atrybut ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array` , ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw, aby `true` określić, że elementy są elementami modelu dom; w przeciwnym razie ustaw wartość `false` . Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` jest ustawiony na `true` , IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` Obowiązkowe. Jeśli `type` jest `Array` , określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true` , aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `locid` Obowiązkowe. Identyfikator informacji o lokalizacji dla zwracanej wartości. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc>](../ide/loc-javascript.md) tagu.

  `value` Obowiązkowe. Określa kod, który powinien być oceniany do użycia przez IntelliSense zamiast samego kodu funkcji. Na przykład można użyć tego atrybutu, aby zapewnić funkcję IntelliSense dla asynchronicznych wywołań zwrotnych, takich jak `Promise` . Użycie `value` atrybutu z `<returns>` elementem może zwiększyć wydajność IntelliSense, pomijając długotrwałe wykonywanie kodu.

  `description` Obowiązkowe. Opis wartości zwracanej.

## <a name="remarks"></a>Uwagi
 Element `<returns>` musi być umieszczony w ciele funkcji przed wszystkimi instrukcjami.

## <a name="example"></a>Przykład
 Poniższy kod ilustruje przykład użycia elementu `<returns>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
