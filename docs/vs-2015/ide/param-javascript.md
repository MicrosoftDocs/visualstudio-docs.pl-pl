---
title: '&lt;param &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670358"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji dla parametru w funkcji lub metodzie.

## <a name="syntax"></a>Składnia

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parametry
 `name` Wymagane. Nazwa parametru.

 `type` Obowiązkowe. Typ danych parametru. Typ może być jednym z następujących:

- Typ języka ECMAScript w specyfikacji ECMAScript 5, taki jak `Number` i `Object` .

- Obiekt DOM, taki jak `HTMLElement` , `Window` , i `Document` .

- Funkcja konstruktora JavaScript.

  `integer` Obowiązkowe. Jeśli `type` jest `Number` , określa, czy parametr jest liczbą całkowitą. Ustaw na, aby `true` wskazać, że parametr jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` Obowiązkowe. Ten atrybut jest przestarzały; `type` atrybut ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy udokumentowany parametr jest elementem modelu DOM. Ustaw, aby `true` określić, że parametr jest elementem modelu dom; w przeciwnym razie ustaw wartość `false` . Jeśli `type` atrybut nie jest ustawiony i `domElement` jest ustawiony na `true` , IntelliSense traktuje udokumentowany parametr jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` Obowiązkowe. Określa, czy parametr udokumentowany może być ustawiony na wartość null. Ustaw na `true` , aby wskazać, że parametr może być ustawiony na wartość null; w przeciwnym razie ustaw wartość `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` Obowiązkowe. Jeśli `type` jest `Array` , ten atrybut określa typ elementów w tablicy.

  `elementInteger` Obowiązkowe. Jeśli `type` jest `Array` i `elementType` ma `Number` , ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na, aby `true` wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` Obowiązkowe. Ten atrybut jest przestarzały; `elementType` atrybut ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array` , ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw, aby `true` określić, że elementy są elementami modelu dom; w przeciwnym razie ustaw wartość `false` . Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` jest ustawiony na `true` , IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` Obowiązkowe. Jeśli `type` jest `Array` , określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true` , aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `locid` Obowiązkowe. Identyfikator informacji o lokalizacji dla parametru. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc>](../ide/loc-javascript.md) elemencie.

  `parameterArray` Obowiązkowe. Określa, czy opisany parametr może być powtórzony w wywołaniu funkcji, podobnie jak powtarzające się parametry obsługiwane w `String.format` funkcji. Ustaw na `true` , aby wskazać, że parametr może być powtórzony; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `optional` Obowiązkowe. Określa, czy udokumentowany parametr jest opcjonalny w funkcji wywołującej. Ustaw na `true` , aby wskazać, że parametr jest opcjonalny; w przeciwnym razie ustaw wartość `false` .

  `value` Obowiązkowe. Określa kod, który powinien być oceniany do użycia przez IntelliSense zamiast samego kodu funkcji. Ten atrybut służy do dostarczania informacji o typie, gdy typ parametru jest niezdefiniowany. Na przykład można użyć `value=’1’` do traktowania typu parametru jako liczby.

  `description` Obowiązkowe. Opis parametru.

## <a name="remarks"></a>Uwagi
 Jedynym wymaganym atrybutem jest `name` . Wszystkie inne atrybuty są opcjonalne.

 Elementy służące do dodawania adnotacji do funkcji, takich jak [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) i [\<returns>](../ide/returns-javascript.md) , muszą być umieszczone w treści funkcji przed dowolnymi instrukcjami.

 Jeśli istnieje wiele `<param>` elementów, które mają taką samą nazwę, jeden z `<param>` elementów jest używany i nadmiarowe elementy są ignorowane. Zachowanie określające, który element jest używany, nie jest zdefiniowane. Jeśli `name` odwołuje się do nieistniejącego parametru, element jest ignorowany.

## <a name="example"></a>Przykład
 Poniższy kod ilustruje przykład użycia elementu `<param>`.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
