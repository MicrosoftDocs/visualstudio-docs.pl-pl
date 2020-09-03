---
title: Tworzenie komentarzy dokumentacji XML dla języka JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619544"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Utwórz komentarze dokumentacji XML dla języka JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Komentarze dokumentacji XML* to Komentarze JavaScript dodawane do skryptu w celu dostarczenia informacji o elementach kodu, takich jak funkcje, pola i zmienne. W programie Visual Studio te opisy tekstowe są wyświetlane z technologią IntelliSense podczas odwoływania się do funkcji skryptu.

 Ten temat zawiera podstawowy samouczek dotyczący korzystania z komentarzy do dokumentacji XML. Aby uzyskać informacje dotyczące korzystania z innych elementów, takich jak [\<var>](../ide/var-javascript.md) i [\<value>](../ide/value-javascript.md) , i aby uzyskać dodatkowe przykłady kodu, zobacz [Komentarze w dokumentacji XML](../ide/xml-documentation-comments-javascript.md). Informacje o udostępnianiu informacji IntelliSense na potrzeby asynchronicznego wywołania zwrotnego, takiego jak `Promise` , można znaleźć w temacie [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> Komentarze dokumentacji XML są dostępne tylko z odnośnych plików, zestawów i usług.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Aby utworzyć komentarze dokumentacji XML dla funkcji języka JavaScript

- W funkcji, Dodaj [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) , i [\<returns>](../ide/returns-javascript.md) poprzedź każdy element z trzema ukośnikami (///).

    > [!NOTE]
    > Każdy element musi znajdować się w jednym wierszu.

     Poniższy przykład pokazuje funkcję JavaScript.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający funkcji, która jest oznaczona za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie:

    ```javascript
    var areaVal = getArea(
    ```

     Po wpisaniu nawiasu otwierającego funkcji, która zawiera komentarze dokumentacji XML, Edytor kodu używa technologii IntelliSense do wyświetlania informacji, które są zdefiniowane w komentarzach dokumentacji XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Aby utworzyć komentarze dokumentacji XML dla pola JavaScript

- W definicji funkcji lub obiektu konstruktora Dodaj [\<field>](../ide/field-javascript.md) element poprzedzony trzema ukośnikami (///).

     Poniższy przykład pokazuje użycie `<field>` elementu w funkcji konstruktora. Aby uzyskać więcej przykładów, zobacz [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Aby wyświetlić komentarze dokumentacji XML, Utwórz obiekt przy użyciu konstruktora funkcji, który jest oznaczony za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie.

    ```javascript
    var eng = new Engine();
    ```

- W następnym wierszu wpisz nazwę obiektu i kropkę, aby wyświetlić informacje o IntelliSense dla tego pola.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Aby utworzyć komentarze dokumentacji XML dla przeciążonej funkcji

1. W funkcji Dodaj [\<signature>](../ide/signature-javascript.md) element dla każdego przeciążenia. W tych elementach Dodaj inne elementy, takie jak `<summary>` , `<param>` i `<returns>` , poprzedzając każdy element z trzema ukośnikami (///).

     Poniższy przykład przedstawia przeciążoną funkcję języka JavaScript. W tym przykładzie przeciążania różnią się w zależności od typu parametru.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający funkcji, która jest oznaczona za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Aby utworzyć zlokalizowaną funkcję IntelliSense

1. Utwórz plik XML, który zawiera komentarze dokumentacji w formacie OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle jest zalecanym formatem. Ten format nie jest obsługiwany w programie Microsoft Ajax ani w plikach WinMD. Aby uzyskać informacje o korzystaniu z formatu alternatywnego `VSDoc` , zobacz [\<loc>](../ide/loc-javascript.md) .

     Poniższy przykład przedstawia zawartość pliku przyczepki, który zawiera zlokalizowane informacje IntelliSense. Jest to plik XML, który znajduje się w folderze specyficznym dla kultury, takim jak JA. Folder musi znajdować się w tej samej lokalizacji co plik. js, który zawiera `<loc>` element. Nazwa pliku XML musi być zgodna z `filename` parametrem określonym w `<loc>` elemencie.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. W pliku js Dodaj następujący kod. `<loc>`Element musi być zadeklarowany przed dowolnym skryptem i mieć te same reguły użycia co `<reference>` element. Aby uzyskać więcej informacji, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md) i [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. W pliku. js Dodaj elementy dokumentacji XML i domyślne opisy. Ustaw `locid` wartości atrybutów w taki sposób, aby odpowiadały `name` wartościom odpowiednich atrybutów z pliku przyczepki. Domyślne opisy zostaną zastąpione przez zlokalizowane informacje IntelliSense, jeśli są dostępne.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający funkcji, jak w poniższym przykładzie:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md) [IntelliSense języka JavaScript](../ide/javascript-intellisense.md) [NIB: przewodnik: JavaScript IntelliSense w ASP.NET](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
