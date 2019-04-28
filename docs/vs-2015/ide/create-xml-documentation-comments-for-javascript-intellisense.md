---
title: Tworzenie komentarzy dokumentacji XML dla funkcji IntelliSense języka JavaScript | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90fb5b1c9a388d64e191915bbcbbe3de65f6aa99
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437625"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Tworzenie komentarzy dokumentacji XML dla JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Komentarze dokumentacji XML* są JavaScript komentarze, które dodajesz do skryptu w celu dostarczenia informacji o elementów kodu, takich jak functions, pól i zmiennych. W programie Visual Studio te opisy tekstowe są wyświetlane za pomocą funkcji IntelliSense, gdy odwołujesz się funkcji skryptu.  
  
 Ten temat zawiera podstawowe samouczek na temat korzystania z komentarze dokumentacji XML. Informacji o używaniu inne elementy, takie jak [ \<var >](../ide/var-javascript.md) i [ \<wartość >](../ide/value-javascript.md)i dla dodatkowych przykładów kodu, zobacz [komentarze dokumentacji XML ](../ide/xml-documentation-comments-javascript.md). Na temat informacji IntelliSense dla asynchroniczne wywołanie zwrotne takie jak informacji `Promise`, zobacz [ \<zwraca >](../ide/returns-javascript.md).  
  
> [!NOTE]
> Komentarze dokumentacji XML są dostępne tylko z odnośnych plików, zestawów i usług.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Aby utworzyć komentarze dokumentacji XML dla funkcji języka JavaScript  
  
- W funkcji, należy dodać [ \<podsumowania >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), i [ \<zwraca >](../ide/returns-javascript.md) elementów, a poprzedzać każdy element z trzema ukośnikami (/ / /).  
  
    > [!NOTE]
    > Każdy element musi być w jednym wierszu.  
  
     Funkcja języka JavaScript można znaleźć w poniższym przykładzie.  
  
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
  
- Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający, funkcji, która jest oznaczona za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Podczas wpisywania tekstu otwierającym nawiasem funkcji, która zawiera komentarze dokumentacji XML, Edytor kodu korzysta z technologii IntelliSense do wyświetlania informacji, która jest zdefiniowana w komentarze dokumentacji XML.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Aby utworzyć komentarzy dokumentacji XML dla pola JavaScript  
  
- W definicji funkcji lub obiektu konstruktora, należy dodać [ \<pole >](../ide/field-javascript.md) element poprzedzone trzema ukośnikami (/ / /).  
  
     Poniższy przykład pokazuje użycie `<field>` elementu w funkcji konstruktora. Aby uzyskać więcej przykładów, zobacz [ \<pole >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
- Aby wyświetlić komentarze dokumentacji XML, należy utworzyć obiekt za pomocą konstruktora funkcji, która jest oznaczona za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
- W następnym wierszu wpisz nazwę obiektu i okres, aby przedstawiały informacje funkcji IntelliSense dla pola.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Aby utworzyć komentarze dokumentacji XML dla przeciążonej funkcji  
  
1. W funkcji, należy dodać [ \<podpis >](../ide/signature-javascript.md) element dla poszczególnych przeciążeń. W tych elementów, Dodaj inne elementy, takie jak `<summary>`, `<param>`, i `<returns>`, poprzedza każdy element z trzema ukośnikami (/ / /).  
  
     Poniższy przykład pokazuje przeciążonej funkcji języka JavaScript. W tym przykładzie przeciążenia różnią się od typu parametru.  
  
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
  
2. Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający, funkcji, która jest oznaczona za pomocą komentarzy dokumentacji XML, jak w poniższym przykładzie:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Aby utworzyć zlokalizowane IntelliSense  
  
1. Utwórz plik XML, który zawiera komentarze dokumentacji w formacie OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    > MessageBundle jest zalecanym formatem. Ten format nie jest obsługiwany w Microsoft Ajax lub pliki .winmd. Dla informacji o korzystaniu z alternatywnym `VSDoc` formatowania, zobacz [ \<lokalizacja >](../ide/loc-javascript.md).  
  
     Poniższy przykład pokazuje zawartość w pliku sidecar, który zawiera zlokalizowane informacje funkcji IntelliSense. Jest to plik XML, który znajduje się w folderze specyficzne dla kultury, takie jak Japonia. Folder musi być w tej samej lokalizacji co plik .js, który zawiera `<loc>` elementu. Nazwa pliku w pliku XML musi być zgodna `filename` określony w parametrze `<loc>` elementu.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2. W pliku js Dodaj następujący kod. `<loc>` Element musi być zadeklarowany przed jakimkolwiek skryptem i te same reguły użycia jako `<reference>` elementu. Aby uzyskać więcej informacji, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md) i [ \<lokalizacja >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3. W pliku js Dodaj elementy dokumentacji XML i opisów domyślnej. Ustaw `locid` wartości do dopasowania, odpowiednich atrybutów `name` wartości atrybutów pliku sidecar. Opisy domyślne zostanie zastąpiona przez zlokalizowane informacje IntelliSense, jeśli jest ona dostępna.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4. Aby wyświetlić komentarze dokumentacji XML, wpisz nazwę i nawias otwierający, funkcji, jak w poniższym przykładzie:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Przewodnik: Funkcja IntelliSense języka JavaScript w programie ASP.NET:](http://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
