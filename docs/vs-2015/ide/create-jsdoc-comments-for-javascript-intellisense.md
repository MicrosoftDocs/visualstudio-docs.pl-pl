---
title: Tworzenie komentarzy JSDoc dla funkcji IntelliSense języka JavaScript | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4d300651731b38b9b86421d36d9de169dc6464d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188792"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Tworzenie komentarzy JSDoc na potrzeby funkcji IntelliSense języka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja IntelliSense w programie Visual Studio Wyświetla informacje, które można dodać do skryptu, używając standardowych komentarzy JSDoc. Komentarze JSDoc służy do dostarczania informacji dotyczących elementów kodu, takich jak functions, pól i zmiennych.  

## <a name="jsdoc-comment-tags"></a>Tagi komentarza JSDoc  
 Następujących standardowych tagów komentarzy JSDoc są używane przez funkcję IntelliSense, aby wyświetlić informacje o swoim kodzie.  

|  JSDoc tag   |                       Składnia                        |                                                     Uwagi                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *Opis elementu*              |                                   Określa zaniechanej funkcji lub metody.                                   |
| @description |             @description *Opis elementu*              |                              Określa opis funkcji lub metody.                               |
|    @param    | @param {*typu*} *parameterName*<em>opis</em> | Określa informacje dla parametru w funkcji lub metody.<br /><br /> Obsługuje również TypeScript @paramTag. |
|  @property   |          @property {*typu*} *propertyName*          |   Określa informacje, w tym opis, pola lub elementu członkowskiego, który jest zdefiniowany w obiekcie.    |
|   @returns   |                  @returns {*typu*}                  |           Określa wartość zwracaną.<br /><br /> TypeScript, można użyć @returnType zamiast @returns.           |
|   @summary   |               @summary *Opis elementu*                |                   Określa opis funkcji lub metody (taka sama jak @description).                   |
|    @type     |                   @type {*typu*}                    |                                Określa typ stałą lub zmienną.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            Określa typ niestandardowy.                                            |

### <a name="examples"></a>Przykłady  
 Poniższy przykład pokazuje użycie @description, @param, i @return JSDoc tagów dla funkcji o nazwie `getArea`.  

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

 W poprzednim przykładzie, funkcja IntelliSense wyświetla opis parametru i informacje zwrotne po wpisaniu nawiasu otwierającego dla `getArea`.  

 ![Informacje o technologii IntelliSense dla funkcji](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 Poniższy przykład pokazuje, jak używać @typedef oznaczyć za pomocą @property tagu.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 Poniższy przykład pokazuje użycie @type JSDoc tagów. Jak pokazano w tym przykładzie, pojedyncza gwiazdka (*), które należy wykonać parę początkowej gwiazdki (\*\*) nie są wymagane.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 Poniższy przykład pokazuje, jak używać @deprecated JSDoc tag.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
