---
title: '&lt;wartość &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656398"
---
# <a name="ltvaluegt-javascript"></a>&lt;wartość &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji `get` dotyczące `set` funkcji i dla właściwości języka ECMAScript 3.

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
 `type` Obowiązkowe. Typ danych właściwości. Typ może być jednym z następujących:

- Typ języka ECMAScript, który znajduje się w specyfikacji ECMAScript 5, np `Number` . i `Object` .

- Obiekt DOM, taki jak `HTMLElement` , `Window` , i `Document` .

- Funkcja konstruktora JavaScript.

  `integer` Obowiązkowe. Jeśli `type` jest `Number` , określa, czy właściwość jest liczbą całkowitą. Ustaw na, aby `true` wskazać, że właściwość jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` Obowiązkowe. Ten atrybut jest przestarzały; `type` atrybut ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy opisana właściwość jest elementem modelu DOM. Ustaw, aby `true` określić, że właściwość jest elementem modelu dom; w przeciwnym razie ustaw wartość `false` . Jeśli `type` atrybut nie jest ustawiony i `domElement` jest ustawiony na `true` , IntelliSense traktuje udokumentowaną właściwość jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` Obowiązkowe. Określa, czy właściwość udokumentowana może być ustawiona na wartość null. Ustaw na `true` , aby wskazać, że właściwość może mieć wartość null; w przeciwnym razie ustaw wartość `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` Obowiązkowe. Jeśli `type` jest `Array` , ten atrybut określa typ elementów w tablicy.

  `elementInteger` Obowiązkowe. Jeśli `type` jest `Array` i `elementType` ma `Number` , ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na, aby `true` wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false` . Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` Obowiązkowe. Ten atrybut jest przestarzały; `elementType` atrybut ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array` , ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw, aby `true` określić, że elementy są elementami modelu dom; w przeciwnym razie ustaw wartość `false` . Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` jest ustawiony na `true` , IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` Obowiązkowe. Jeśli `type` jest `Array` , określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true` , aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false` . Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `locid` Obowiązkowe. Identyfikator informacji o lokalizacji dla właściwości. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc>](../ide/loc-javascript.md) elemencie.

  `description` Obowiązkowe. Opis właściwości.

## <a name="remarks"></a>Uwagi
 Właściwości ECMAScript 5 używają [\<summary>](../ide/summary-javascript.md) elementu.

 Użyj `<value>` elementu bezpośrednio przed `get` `set` funkcją or.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak używać `<value>` elementu w `get` funkcji.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
