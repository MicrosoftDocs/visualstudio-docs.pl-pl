---
title: Tworzenie komentarzy JSDoc dla języka JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619274"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Tworzenie komentarzy JSDoc na potrzeby funkcji IntelliSense języka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologia IntelliSense w programie Visual Studio Wyświetla informacje dodawane do skryptu przy użyciu standardowych komentarzy JSDoc. Komentarze JSDoc umożliwiają dostarczanie informacji o elementach kodu, takich jak funkcje, pola i zmienne.

## <a name="jsdoc-comment-tags"></a>Tagi komentarzy JSDoc
 Poniższe standardowe Tagi komentarzy JSDoc są używane przez funkcję IntelliSense do wyświetlania informacji o kodzie.

|  Tag JSDoc   |                       Składnia                        |                                                     Uwagi                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              *opis* @deprecated              |                                   Określa przestarzałą funkcję lub metodę.                                   |
| @description |             *opis* @description              |                              Określa opis funkcji lub metody.                               |
|    @param    | <em>opis</em> @param {*Type*} *ParameterName* | Określa informacje dla parametru w funkcji lub metodzie.<br /><br /> Język TypeScript obsługuje również @paramTag. |
|  @property   |          @property {*Type*} *PropertyName*          |   Określa informacje, łącznie z opisem, dla pola lub elementu członkowskiego zdefiniowanego w obiekcie.    |
|   @returns   |                  @returns {*Type*}                  |           Określa wartość zwracaną.<br /><br /> Dla języka TypeScript Użyj @returnType zamiast @returns.           |
|   @summary   |               *opis* @summary                |                   Określa opis funkcji lub metody (analogicznie jak @description).                   |
|    @type     |                   @type {*Type*}                    |                                Określa typ stałej lub zmiennej.                                |
|   @typedef   |         @typedef {*Type*} *customTypeName*          |                                            Określa typ niestandardowy.                                            |

### <a name="examples"></a>Przykłady
 W poniższym przykładzie pokazano użycie @description, @param i @return tagów JSDoc dla funkcji o nazwie `getArea`.

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 W poprzednim przykładzie technologia IntelliSense wyświetla opis, parametr i zwraca informacje po wpisaniu nawiasu otwierającego dla `getArea`.

 ![Informacje o technologii IntelliSense dla funkcji](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 Poniższy przykład pokazuje, jak używać tagu @typedef ze znacznikiem @property.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 W poniższym przykładzie pokazano użycie @type tagów JSDoc. Jak pokazano w tym przykładzie, pojedyncze gwiazdki (*), które występują po początkowej parze gwiazdki (\* \*) nie są wymagane.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 Poniższy przykład przedstawia sposób użycia znacznika @deprecated JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
