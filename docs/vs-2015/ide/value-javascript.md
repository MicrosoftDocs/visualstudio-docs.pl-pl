---
title: '&lt;wartość&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179314"
---
# <a name="ltvaluegt-javascript"></a>&lt;wartość&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji dla `get` i `set` funkcje dla właściwości ECMAScript 3.  
  
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
 `type`  
 Opcjonalny. Typ danych właściwości. Typ może być jednym z następujących czynności:  
  
- Typ języka ECMAScript, który znajduje się w specyfikacji ECMAScript 5, takie jak `Number` i `Object`.  
  
- Obiekt modelu DOM, takich jak `HTMLElement`, `Window`, i `Document`.  
  
- Funkcja konstruktora języka JavaScript.  
  
  `integer`  
  Opcjonalny. Jeśli `type` jest `Number`, określa, czy właściwość jest liczbą całkowitą. Ustaw `true` do wskazania, że właściwość jest liczbą całkowitą; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `domElement`  
  Opcjonalna. Ten atrybut jest przestarzała; `type` atrybut mają pierwszeństwo przed tego atrybutu. Ten atrybut określa, czy właściwość udokumentowanego jest DOM element. Ustaw `true` do określenia, czy właściwość jest element DOM w LICZBIE; w przeciwnym wypadku ustaw `false`. Jeśli `type` atrybut nie jest ustawiony i `domElement` ustawiono `true`, IntelliSense traktuje udokumentowanego właściwości jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `mayBeNull`  
  Opcjonalny. Określa, czy udokumentowanego właściwość można ustawić na wartość null. Ustaw `true` aby wskazać, że właściwość można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementType`  
  Opcjonalny. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.  
  
  `elementInteger`  
  Opcjonalna. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw `true` do wskazania elementów w tablicy są liczbami całkowitymi; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementDomElement`  
  Opcjonalny. Ten atrybut jest przestarzała; `elementType` atrybut mają pierwszeństwo przed tego atrybutu. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy elementów DOM w LICZBIE. Ustaw `true` określić elementy są elementów DOM; w przeciwnym wypadku ustaw `false`. Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` ustawiono `true`, IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `elementMayBeNull`  
  Opcjonalny. Jeśli `type` jest `Array`, określa, czy elementy w tablicy może być ustawiona na wartość null. Ustaw `true` aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `locid`  
  Opcjonalna. Identyfikator informacji o lokalizacji na temat właściwości. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Identyfikator typu zależy od formatu określonego w [ \<lokalizacja >](../ide/loc-javascript.md) elementu.  
  
  `description`  
  Opcjonalny. Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Użyj właściwości ECMAScript 5 [ \<podsumowania >](../ide/summary-javascript.md) elementu.  
  
 Użyj `<value>` element bezpośrednio przed `get` lub `set` funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia `<value>` element na `get` funkcji.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
