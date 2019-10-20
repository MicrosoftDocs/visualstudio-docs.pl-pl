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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670358"
---
# <a name="ltparamgt-javascript"></a>&gt; &lt;param (JavaScript)
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
 Wymagane `name`. Nazwa parametru.

 `type` opcjonalny. Typ danych parametru. Typ może być jednym z następujących:

- Typ języka ECMAScript w specyfikacji ECMAScript 5, taki jak `Number` i `Object`.

- Obiekt DOM, taki jak `HTMLElement`, `Window` i `Document`.

- Funkcja konstruktora JavaScript.

  `integer` opcjonalny. Jeśli `type` jest `Number`, określa, czy parametr jest liczbą całkowitą. Ustaw na `true`, aby wskazać, że parametr jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `type` ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy udokumentowany parametr jest elementem modelu DOM. Ustaw na `true`, aby określić, że parametr jest elementem modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `type` nie jest ustawiony i `domElement` jest ustawiony na `true`, IntelliSense traktuje udokumentowany parametr jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` opcjonalny. Określa, czy parametr udokumentowany może być ustawiony na wartość null. Ustaw na `true`, aby wskazać, że parametr może być ustawiony na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` opcjonalny. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.

  `elementInteger` opcjonalny. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na `true`, aby wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `elementType` ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw na `true`, aby określić, że elementy są elementami modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `elementType` nie jest ustawiony i `elementDomElement` jest ustawiona na `true`, funkcja IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` opcjonalny. Jeśli `type` jest `Array`, określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true`, aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `locid` opcjonalny. Identyfikator informacji o lokalizacji dla parametru. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc >](../ide/loc-javascript.md) elementu.

  `parameterArray` opcjonalny. Określa, czy opisany parametr może być powtórzony w wywołaniu funkcji, podobnie jak parametry powtarzane obsługiwane w funkcji `String.format`. Ustaw na `true`, aby wskazać, że można powtórzyć parametr; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `optional` opcjonalny. Określa, czy udokumentowany parametr jest opcjonalny w funkcji wywołującej. Ustaw na `true`, aby wskazać, że parametr jest opcjonalny; w przeciwnym razie ustaw wartość `false`.

  `value` opcjonalny. Określa kod, który powinien być oceniany do użycia przez IntelliSense zamiast samego kodu funkcji. Ten atrybut służy do dostarczania informacji o typie, gdy typ parametru jest niezdefiniowany. Na przykład można użyć `value=’1’` do traktowania typu parametru jako liczby.

  `description` opcjonalny. Opis parametru.

## <a name="remarks"></a>Uwagi
 Jedynym wymaganym atrybutem jest `name`. Wszystkie inne atrybuty są opcjonalne.

 Elementy służące do dodawania adnotacji do funkcji, takich jak [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)i [\<returns](../ide/returns-javascript.md)>, muszą być umieszczone w treści funkcji przed dowolnymi instrukcjami.

 Jeśli istnieje wiele `<param>` elementów o tej samej nazwie, jeden z elementów `<param>` jest używany, a elementy nadmiarowe są ignorowane. Zachowanie określające, który element jest używany, nie jest zdefiniowane. Jeśli `name` odwołuje się do nieistniejącego parametru, element zostanie zignorowany.

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
