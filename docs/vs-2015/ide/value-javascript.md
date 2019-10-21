---
title: '&lt;value &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656398"
---
# <a name="ltvaluegt-javascript"></a>&gt; &lt;value (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji dotyczące `get` i `set` funkcji dla właściwości ECMAScript 3.

## <a name="syntax"></a>Składnia

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Parametry
 `type` opcjonalny. Typ danych właściwości. Typ może być jednym z następujących:

- Typ języka ECMAScript, który znajduje się w specyfikacji ECMAScript 5, np. `Number` i `Object`.

- Obiekt DOM, taki jak `HTMLElement`, `Window` i `Document`.

- Funkcja konstruktora JavaScript.

  `integer` opcjonalny. Jeśli `type` jest `Number`, określa, czy właściwość jest liczbą całkowitą. Ustaw na `true`, aby wskazać, że właściwość jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `type` ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy opisana właściwość jest elementem modelu DOM. Ustaw na `true`, aby określić, że właściwość jest elementem modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `type` nie jest ustawiony i `domElement` jest ustawiony na `true`, IntelliSense traktuje udokumentowaną właściwość jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` opcjonalny. Określa, czy właściwość udokumentowana może być ustawiona na wartość null. Ustaw na `true`, aby wskazać, że właściwość może być ustawiona na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` opcjonalny. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.

  `elementInteger` opcjonalny. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na `true`, aby wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `elementType` ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw na `true`, aby określić, że elementy są elementami modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `elementType` nie jest ustawiony i `elementDomElement` jest ustawiona na `true`, funkcja IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` opcjonalny. Jeśli `type` jest `Array`, określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true`, aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `locid` opcjonalny. Identyfikator informacji o lokalizacji dla właściwości. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc >](../ide/loc-javascript.md) elementu.

  `description` opcjonalny. Opis właściwości.

## <a name="remarks"></a>Uwagi
 Właściwości ECMAScript 5 używają elementu [> \<summary](../ide/summary-javascript.md) .

 Użyj `<value>` elementu bezpośrednio przed funkcją `get` lub `set`.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak używać elementu `<value>` w funkcji `get`.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
