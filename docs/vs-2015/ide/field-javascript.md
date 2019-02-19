---
title: '&lt;pole&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54766559"
---
# <a name="ltfieldgt-javascript"></a>&lt;pole&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa informacje w dokumentacji, w tym opis, pola lub elementu członkowskiego, który jest zdefiniowany w obiekcie.  
  
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
 `name`  
 Nazwa pola lub elementu członkowskiego. Gdy `<field>` element jest używany w funkcji konstruktora `name` jest wymagana, a następnie definiuje składową, do której stosują się tag. Gdy `<field>` element bezpośrednio jest dodawanie adnotacji do pola, ten atrybut jest ignorowany i nazwę używaną przez program Visual Studio jest nazwa rzeczywistej pola w kodzie źródłowym.  
  
 `static`  
 Opcjonalna. Określa, czy pole jest elementem członkowskim funkcji konstruktora członka obiektu zwrócona przez funkcję konstruktora. Ustaw `true` traktowanie pola jako członek funkcji konstruktora. Ustaw `false` traktowanie pola jako członka obiektu zwróconego przez funkcję konstruktora.  
  
 `type`  
 Opcjonalna. Typ danych pola. Typ może być jednym z następujących czynności:  
  
- Wpisz w specyfikacji ECMAScript 5, takie jak z językiem ECMAScript `Number` i `Object`.  
  
- Obiekt modelu DOM, takich jak `HTMLElement`, `Window`, i `Document`.  
  
- Funkcja konstruktora języka JavaScript.  
  
  `integer`  
  Opcjonalna. Jeśli `type` jest `Number`, określa, czy pole jest liczbą całkowitą. Ustaw `true` do wskazania, że pole jest liczba całkowita; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `domElement`  
  Opcjonalna. Ten atrybut jest przestarzała; `type` atrybut mają pierwszeństwo przed tego atrybutu. Ten atrybut określa, czy pole udokumentowanego jest DOM element. Ustaw `true` do określenia, że pole jest element DOM w LICZBIE; w przeciwnym wypadku ustaw `false`. Jeśli `type` atrybut nie jest ustawiony i `domElement` ustawiono `true`, IntelliSense traktuje udokumentowanego pola jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `mayBeNull`  
  Opcjonalna. Określa, czy udokumentowanego pole można ustawić na wartość null. Ustaw `true` aby wskazać, że pole można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementType`  
  Opcjonalna. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.  
  
  `elementInteger`  
  Opcjonalna. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw `true` do wskazania elementów w tablicy są liczbami całkowitymi; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `elementDomElement`  
  Opcjonalna. Ten atrybut jest przestarzała; `elementType` atrybut mają pierwszeństwo przed tego atrybutu. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy elementów DOM w LICZBIE. Ustaw `true` określić elementy są elementów DOM; w przeciwnym wypadku ustaw `false`. Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` ustawiono `true`, IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.  
  
  `elementMayBeNull`  
  Opcjonalna. Jeśli `type` jest `Array`, określa, czy elementy w tablicy może być ustawiona na wartość null. Ustaw `true` aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
  `helpKeyword`  
  Opcjonalna. Słowo kluczowe dla pomocy F1.  
  
  `locid`  
  Opcjonalna. Identyfikator informacji o lokalizacji na temat pola. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Identyfikator typu zależy od formatu określonego w [ \<lokalizacja >](../ide/loc-javascript.md) tagu.  
  
  `value`  
  Opcjonalna. Określa kod, który ma zostać obliczona dla użycia przez funkcję IntelliSense zamiast sam kod funkcji. Aby uzyskać `<field>`, ten atrybut jest obsługiwana w przypadku funkcji konstruktora, ale nie jest obsługiwana dla literałów obiektu. Możesz użyć tego atrybutu jest zapewnienie informacji o typie, gdy zdefiniowano typ pola. Na przykład, można użyć `value=’1’` traktowanie typ pola jako liczby.  
  
  `description`  
  Opcjonalna. Opis pola.  
  
## <a name="remarks"></a>Uwagi  
 `name` Atrybut jest wymagany, gdy masz dokumentowanie pola w funkcji konstruktora. W innych sytuacjach, wszystkie atrybuty dla `<field>` elementu są opcjonalne.  
  
 Gdy jesteś dokumentowanie funkcję konstruktora `<field>` element musi znajdować się bezpośrednio przed deklarację pola. `name` Atrybut musi pasować do nazwy pola, która jest używana w kodzie źródłowym. W przypadku członków obiektu `name` atrybut można pominąć, jeśli `<field>` element pojawia się bezpośrednio przed deklaracja elementu członkowskiego obiektu.  
  
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
 Poniższy przykład pokazuje, jak używać `<field>` element z `static` ustawioną wartość atrybutu `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<field>` element z `static` ustawioną wartość atrybutu `false`.  
  
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
 Poniższy przykład pokazuje, jak używać `<field>` element z `value` atrybutu.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
