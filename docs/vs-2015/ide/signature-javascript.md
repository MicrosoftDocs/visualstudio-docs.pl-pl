---
title: '&lt;podpis &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671130"
---
# <a name="ltsignaturegt-javascript"></a>&lt;Signature &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grupowanie zestawu powiązanych elementów dla funkcji lub metody, aby udostępnić dokumentację dla przeciążonych funkcji.

## <a name="syntax"></a>Składnia

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parametry
 `externalid` Obowiązkowe. Jeśli `format` atrybut dla [\<loc>](../ide/loc-javascript.md) elementu ma wartość `vsdoc` , ten atrybut określa identyfikator elementu członkowskiego, który jest używany do lokalizowania kodu XML, który jest skojarzony z podpisem. W przeciwieństwie do atrybutu `locid`, ten atrybut określa, czy wszystkie elementy w elemencie członkowskim, które mają ten identyfikator powinny być ładowane. Wszystkie skojarzone informacje opisu występujące w kodzie XML również zostaną scalone z elementami określonymi w podpisie. Dzięki temu można określić dodatkowe elementy, takie jak `<capability>`, w pliku sidecar bez określania ich w pliku źródłowym. `externalid` jest opcjonalnym atrybutem.

 `externalFile` Obowiązkowe. Określa nazwę pliku, w którym ma znaleźć `externalid`. Atrybut ten jest ignorowany, jeśli nie występuje żaden `externalid`. Jest to atrybut opcjonalny. Wartością domyślną jest nazwa bieżącego pliku, ale z rozszerzeniem pliku .xml zamiast js. Domyślnie reguły wyszukiwania zarządzanego zasobu dla lokalizacji są używane do lokalizowania pliku.

 `helpKeyword` Obowiązkowe. Słowo kluczowe dla pomocy F1.

 `locid` Obowiązkowe. Identyfikator informacji o lokalizacji na temat pola. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc>](../ide/loc-javascript.md) tagu.

## <a name="remarks"></a>Uwagi
 Należy użyć jednego elementu `<signature>` dla każdego przeciążonego opisu funkcji w pliku .js, lub użyć jednego elementu `<signature>` dla każdego określonego zewnętrznego identyfikatora elementu członkowskiego.

 Element `<signature>` musi być umieszczony w ciele funkcji przed wszystkimi instrukcjami. W przypadku używania [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) , lub [\<returns>](../ide/returns-javascript.md) elementów z `<signature>` elementem, umieść pozostałe elementy wewnątrz `<signature>` bloku.

## <a name="example"></a>Przykład
 Poniższy kod ilustruje przykład użycia elementu `<signature>`.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
