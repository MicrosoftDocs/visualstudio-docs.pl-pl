---
title: '&lt;Podsumowanie &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646849"
---
# <a name="ltsummarygt-javascript"></a>&lt;Podsumowanie &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa opis funkcji lub metody.

## <a name="syntax"></a>Składnia

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parametry
 `locid` Obowiązkowe. Identyfikator informacji o lokalizacji dotyczącej funkcji lub metody. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Typ identyfikatora zależy od formatu określonego w [\<loc>](../ide/loc-javascript.md) elemencie.

 `description` Obowiązkowe. Opis funkcji lub metody.

## <a name="remarks"></a>Uwagi
 Elementy używane do dodawania adnotacji do funkcji, które obejmują [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) , i [\<returns>](../ide/returns-javascript.md) , muszą być umieszczone w treści funkcji przed dowolnymi instrukcjami.

## <a name="example"></a>Przykład
 Poniższy kod pokazuje, jak używać `<summary>` elementu.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
