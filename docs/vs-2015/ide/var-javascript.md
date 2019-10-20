---
title: '&lt;var &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663058"
---
# <a name="ltvargt-javascript"></a>&gt; &lt;var (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji dla zmiennej.

## <a name="syntax"></a>Składnia

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parametry
 `type` opcjonalny. Typ danych zmiennej. Typ może być jednym z następujących:

- Typ języka ECMAScript, który znajduje się w specyfikacji ECMAScript 5, np. `Number` i `Object`.

- Obiekt DOM, taki jak `HTMLElement`, `Window` i `Document`.

- Funkcja konstruktora JavaScript.

  `integer` opcjonalny. Jeśli `type` jest `Number`, określa, czy zmienna jest liczbą całkowitą. Ustaw na `true`, aby wskazać, że zmienna jest liczbą całkowitą; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `domElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `type` ma pierwszeństwo przed tym atrybutem. Ten atrybut określa, czy udokumentowana zmienna jest elementem modelu DOM. Ustaw na `true`, aby określić, że zmienna jest elementem modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `type` nie jest ustawiony i `domElement` jest ustawiony na `true`, IntelliSense traktuje udokumentowaną zmienną jako `HTMLElement` podczas wykonywania instrukcji.

  `mayBeNull` opcjonalny. Określa, czy dla udokumentowanej zmiennej można ustawić wartość null. Ustaw na `true`, aby wskazać, że zmienna może być ustawiona na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementType` opcjonalny. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.

  `elementInteger` opcjonalny. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw na `true`, aby wskazać, że elementy w tablicy są liczbami całkowitymi; w przeciwnym razie ustaw wartość `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `elementDomElement` opcjonalny. Ten atrybut jest przestarzały; atrybut `elementType` ma pierwszeństwo przed tym atrybutem. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy są elementami modelu DOM. Ustaw na `true`, aby określić, że elementy są elementami modelu DOM; w przeciwnym razie ustaw wartość `false`. Jeśli atrybut `elementType` nie jest ustawiony i `elementDomElement` jest ustawiona na `true`, funkcja IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.

  `elementMayBeNull` opcjonalny. Jeśli `type` jest `Array`, określa, czy elementy w tablicy można ustawić na wartość null. Ustaw na `true`, aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie ustaw wartość `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio do udostępniania informacji IntelliSense.

  `helpKeyword` opcjonalny. Słowo kluczowe dla pomocy F1.

  `locid` opcjonalny. Identyfikator informacji o lokalizacji dla zmiennej. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w tagu [\<loc >](../ide/loc-javascript.md) .

  `description` opcjonalny. Opis zmiennej.

## <a name="example"></a>Przykład
 Poniższy kod ilustruje przykład użycia elementu `<var>`.

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
