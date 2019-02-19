---
title: '&lt;param&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54772384"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje o dokumentacji dla parametru w funkcji lub metody.  
  
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
 `name`  
 Wymagana. Nazwa parametru.  
  
 `type`  
 Opcjonalna. Typ danych parametru. Typ może być jednym z następujących czynności:  
  
- Wpisz w specyfikacji ECMAScript 5, takie jak z językiem ECMAScript `Number` i `Object`.  
  
- Obiekt modelu DOM, takich jak `HTMLElement`, `Window`, i `Document`.  
  
- Funkcja konstruktora języka JavaScript.  
  
  `integer`  
  Opcjonalna. Jeśli `type` jest `Number`, określa, czy parametr jest liczbą całkowitą. Ustaw `true` do wskazania, że parametr jest liczbą całkowitą; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `domElement`  
  Opcjonalna. Ten atrybut jest przestarzała; `type` atrybut mają pierwszeństwo przed tego atrybutu. Ten atrybut określa, czy parametr udokumentowanego jest DOM element. Ustaw `true` do określenia, czy parametr jest element DOM w LICZBIE; w przeciwnym wypadku ustaw `false`. Jeśli `type` atrybut nie jest ustawiony i `domElement` ustawiono `true`, IntelliSense traktuje udokumentowanego parametr jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `mayBeNull`  
  Opcjonalna. Określa, czy udokumentowanego parametr może być ustawiony na wartość null. Ustaw `true` aby wskazać, że parametr można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementType`  
  Opcjonalna. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.  
  
  `elementInteger`  
  Opcjonalna. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw `true` do wskazania elementów w tablicy są liczbami całkowitymi; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementDomElement`  
  Opcjonalna. Ten atrybut jest przestarzała; `elementType` atrybut mają pierwszeństwo przed tego atrybutu. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy elementów DOM w LICZBIE. Ustaw `true` określić elementy są elementów DOM; w przeciwnym wypadku ustaw `false`. Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` ustawiono `true`, IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `elementMayBeNull`  
  Opcjonalna. Jeśli `type` jest `Array`, określa, czy elementy w tablicy może być ustawiona na wartość null. Ustaw `true` aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `locid`  
  Opcjonalna. Identyfikator informacji o lokalizacji na temat parametru. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Identyfikator typu zależy od formatu określonego w [ \<lokalizacja >](../ide/loc-javascript.md) elementu.  
  
  `parameterArray`  
  Opcjonalna. Określa, czy udokumentowanego parametr można powtarzać w wywołaniu funkcji, podobnie jak powtarzające się parametry są obsługiwane w `String.format` funkcji. Ustaw `true` aby wskazać, że parametr może być powtarzane; w przeciwnym razie, należy ustawić na `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `optional`  
  Opcjonalna. Określa, czy udokumentowanego parametr jest opcjonalny w funkcji wywołującej. Ustaw `true` aby wskazać, że parametr jest opcjonalny; w przeciwnym razie, należy ustawić na `false`.  
  
  `value`  
  Opcjonalna. Określa kod, który ma zostać obliczona dla użycia przez funkcję IntelliSense zamiast sam kod funkcji. Możesz użyć tego atrybutu jest zapewnienie informacji o typie, gdy zdefiniowano typ parametru. Na przykład, można użyć `value=’1’` traktowanie typ parametru jako liczby.  
  
  `description`  
  Opcjonalna. Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 Jest to jedyny atrybut wymagane `name`. Wszystkie inne atrybuty są opcjonalne.  
  
 Elementy adnotować funkcje, takie jak [ \<podsumowania >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), i [ \<zwraca >](../ide/returns-javascript.md), muszą być umieszczone w treści funkcji przed wszystkimi instrukcjami.  
  
 Jeśli dostępnych jest wiele `<param>` elementy, które mają taką samą nazwę, jeden z `<param>` elementy są używane i zbędne elementy są ignorowane. Nie zdefiniowano zachowanie, które określa, który element jest używany. Jeśli `name` odwołuje się do nieistniejącego parametru jest ignorowana.  
  
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
