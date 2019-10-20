---
title: '&lt;field &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663858"
---
# <a name="ltfieldgt-javascript"></a>&gt; &lt;field (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji, w tym opis, dla pola lub elementu członkowskiego zdefiniowanego w obiekcie.

## <a name="syntax"></a>Składnia

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Parametry
 `name` nazwę pola lub elementu członkowskiego. Gdy element `<field>` jest używany w funkcji konstruktora, `name` jest wymagany i definiuje element członkowski, do którego ma zastosowanie tag. Gdy element `<field>` jest bezpośrednio adnotacją pola, ten atrybut jest ignorowany, a nazwa używana przez program Visual Studio jest nazwą rzeczywistego pola w kodzie źródłowym.

 `static` opcjonalny. Określa, czy pole jest składową funkcji konstruktora, czy składową obiektu zwróconego przez funkcję konstruktora. Ustaw na `true`, aby traktować pole jako element członkowski funkcji konstruktora. Ustaw na `false`, aby traktować pole jako element członkowski obiektu zwróconego przez funkcję konstruktora.

 `type` opcjonalny. Typ danych pola. Typ może być jednym z następujących:

- Typ języka ECMAScript w specyfikacji ECMAScript 5, taki jak `Number` i `Object`.

- Obiekt DOM, taki jak `HTMLElement`, `Window` i `Document`.

- Funkcja konstruktora JavaScript.

  `integer` opcjonalny. Jeśli `type` jest `Number`, określa, czy pole jest liczbą całkowitą. Ustaw na `true`, aby wskazać, że pole jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `type` ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy dokumentowane pole jest elementem modelu DOM. Ustaw na `true`, aby określić, że pole jest elementem modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `type` nie jest ustawiony i `domElement` jest ustawiony na `true`, IntelliSense traktuje to pole jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` opcjonalny. Określa, czy dla udokumentowanego pola można ustawić wartość null. Ustaw na `true`, aby wskazać, że pole może mieć wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` opcjonalny. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.

  `elementInteger` opcjonalny. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na `true`, aby wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `elementType` ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw na `true`, aby określić, że elementy są elementami modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `elementType` nie jest ustawiony i `elementDomElement` jest ustawiona na `true`, funkcja IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` opcjonalny. Jeśli `type` jest `Array`, określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true`, aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `helpKeyword` opcjonalny. Słowo kluczowe dla pomocy F1.

  `locid` opcjonalny. Identyfikator informacji o lokalizacji na temat pola. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w tagu [\<loc >](../ide/loc-javascript.md) .

  `value` opcjonalny. Określa kod, który powinien być oceniany do użycia przez IntelliSense zamiast samego kodu funkcji. W przypadku `<field>` ten atrybut jest obsługiwany dla funkcji konstruktora, ale nie jest obsługiwany w przypadku literałów obiektów. Ten atrybut służy do dostarczania informacji o typie, gdy typ pola jest niezdefiniowany. Na przykład można użyć `value=’1’` do traktowania typu pola jako liczby.

  `description` opcjonalny. Opis pola.

## <a name="remarks"></a>Uwagi
 Atrybut `name` jest wymagany w przypadku dokumentowania pola w funkcji konstruktora. We wszystkich innych scenariuszach wszystkie atrybuty elementu `<field>` są opcjonalne.

 Podczas dokumentowania funkcji konstruktora element `<field>` musi występować bezpośrednio przed deklaracją pola. Atrybut `name` musi być zgodny z nazwą pola używaną w kodzie źródłowym. W przypadku elementów członkowskich obiektu atrybut `name` można pominąć, jeśli element `<field>` pojawia się bezpośrednio przed deklaracją elementu członkowskiego obiektu.

## <a name="example"></a>Przykład
 Poniższy kod ilustruje przykład użycia elementu `<field>`.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać elementu `<field>` z atrybutem `static` ustawionym na `true`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać elementu `<field>` z atrybutem `static` ustawionym na `false`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać elementu `<field>` z atrybutem `value`.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
