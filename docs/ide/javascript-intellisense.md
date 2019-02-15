---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91ea140ffef8d564cc1380d2fe3fd30a252fef14
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318460"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Program Visual Studio 2017 zawiera zaawansowane środowisko gotową do edytowania plików JavaScript. Usługa języka TypeScript, na podstawie, Visual Studio zapewnia ulepszoną funkcję IntelliSense, obsługę nowoczesnych funkcji JavaScript, oraz funkcji zwiększania wydajności, takie jak Przejdź do definicji, Refaktoryzacja i nie tylko.

> [!NOTE]
> Usługa języka JavaScript w programie Visual Studio 2017 używa nowego aparatu usługi języka (o nazwie "Salsa"). Szczegółowe informacje znajdują się w tym temacie, a możesz również przeczytać ten tekst [wpis w blogu](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Nowe środowisko edytowania dotyczy również przede wszystkim od programu Visual Studio Code. Zobacz [dokumentacja programu VS Code](https://code.visualstudio.com/docs/languages/javascript) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji na temat ogólnych funkcji IntelliSense programu Visual Studio, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>What's new in usługa języka JavaScript w programie Visual Studio 2017

Począwszy od programu Visual Studio 2017 JavaScript IntelliSense wyświetla informacje o wiele więcej list parametrów i elementów członkowskich.
To nowe informacje są udostępniane przez usługę języka TypeScript, która używa analiza statyczna w tle, aby lepiej zrozumieć swój kod.
TypeScript korzysta z wielu źródeł do utworzenia tych informacji:

- [Funkcja IntelliSense, oparte na wnioskowanie o typie](#TypeInference)
- [Funkcja IntelliSense, oparte na danych JSDoc](#JsDoc)
- [Funkcja IntelliSense, na podstawie plików deklaracji TypeScript](#TsDeclFiles)
- [Automatyczne nabycia definicje typów](#Auto)

<a name="TypeInference"></a>
### <a name="intellisense-based-on-type-inference"></a>Funkcja IntelliSense, oparte na wnioskowanie o typie

W języku JavaScript w większości przypadków nie ma żadnych jawnego typu informacji dostępna. Na szczęście zazwyczaj przyczyną jest dość proste ustalenie typu, biorąc pod uwagę otaczającego kontekst kodu.
Ten proces jest nazywany wnioskowanie o typie.

Dla zmiennej lub właściwości Typ jest zazwyczaj typ wartości używane do zainicjowania jego lub najnowszych przypisanie wartości.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Dla funkcji można wywnioskować zwracanego typu na podstawie instrukcji return.

Dla parametrów funkcji nie ma żadnych wnioskowania, ale istnieją sposoby obejścia tego problemu za pomocą JSDoc lub TypeScript *. d.ts* plików (zobacz w kolejnych sekcjach).

Ponadto ma specjalne wnioskowania dla następujących elementów:

- Klasy "ES3-style" określony za pomocą funkcji konstruktora i przypisania do właściwości prototypu.
- Wzorce modułu CommonJS stylu, określony jako przypisania właściwości na `exports` obiektu lub przypisania do `module.exports` właściwości.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>
### <a name="intellisense-based-on-jsdoc"></a>Funkcja IntelliSense, oparte na danych JSDoc

Gdzie wnioskowanie o typie nie dostarcza informacji żądanego typu (lub do obsługi dokumentacji), informacje o typie może zostać jawnie dostarczone za pośrednictwem adnotacji JSDoc.  Na przykład, aby dać częściowo deklarowanego obiektu określonego typu, można użyć `@type` tag, jak pokazano poniżej:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak wspomniano wcześniej, parametry funkcji nigdy nie są wnioskowane. Jednak przy użyciu JSDoc `@param` tagu, można dodać typy do parametrów funkcji, jak również.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Zobacz [Obsługa formatu JSDoc w języku JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) dla adnotacji JsDoc obecnie obsługiwane.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>Funkcja IntelliSense, na podstawie plików deklaracji TypeScript

Ponieważ JavaScript i TypeScript, teraz są oparte na tej samej usługi w języka, będą mogli wchodzić w interakcje w sposób bardziej zaawansowane. Na przykład można podać JavaScript IntelliSense dla wartości zadeklarowanych w *. d.ts* pliku (zobacz [dokumentacji TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), i typów, takich jak interfejsy i klasy zadeklarowanej w TypeScript dostępne do użycia jako typów w komentarzy JsDoc.

Poniżej przedstawiono prosty przykład pliku definicji TypeScript, podając takie informacje o typie (za pośrednictwem interfejsu) do pliku JavaScript, w tym samym projekcie (przy użyciu `JsDoc` tagu).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640" alt="TypeScript definition file" />

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatyczne nabycia definicje typów

W świecie TypeScript najbardziej popularne biblioteki JavaScript mają swoje interfejsy API opisanego przez *. d.ts* plików i najbardziej typowe repozytorium takie definicje znajduje się na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Domyślnie usługa języka Salsa podejmie próbę wykrycia biblioteki JavaScript, które są w użyciu i automatycznie, pobieranie i odpowiednie odwołania *. d.ts* pliku, który opisuje biblioteki w celu zapewnienia bardziej zaawansowane Funkcja IntelliSense. Pliki są pobierane do pamięci podręcznej znajduje się w folderze użytkownika na *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Ta funkcja jest **wyłączone** domyślnie, jeśli za pomocą *tsconfig.json* konfiguracji pliku, ale mogą zostać ustawione w pozycji włączone jako dalsze schemat poniżej.

Automatyczne wykrywanie działa obecnie zależności pobrany z poziomu narzędzia npm (, zapoznając się *package.json* pliku), Bower (, zapoznając się *bower.json* pliku) oraz luźne pliki w projekcie, które odpowiadają liście z grubsza pierwszych 400 najbardziej popularne biblioteki JavaScript. Na przykład, jeśli masz *jquery 1.10.min.js* w projekcie, plik *jquery.d.ts* zostaną pobrane i załadowane w celu zapewnienia lepszej edytowania. To *. d.ts* pliku nie będzie mieć wpływu na projekt.

Jeśli nie chcesz używać automatycznego pozyskiwania, należy ją wyłączyć, dodając plik konfiguracji, tak jak pokazano poniżej. Możesz nadal umieścić pliki definicji do użycia bezpośrednio w obrębie projektu ręcznie.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Obsługa języka JavaScript (Visual Studio dla komputerów Mac)](/visualstudio/mac/javascript)