---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2459c9ab7b6dc6e49bbbe86729d25a2adb5bdb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593723"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Program Visual Studio zapewnia zaawansowane środowisko edycji języka JavaScript, które jest od razu dostępne. Obsługiwane przez usługę języka TypeScript, Visual Studio oferuje bogatszą funkcję IntelliSense, obsługę nowoczesnych funkcji języka JavaScript oraz udoskonalone funkcje produktywności, takie jak przejście do definicji, refaktoryzacja i inne.

> [!NOTE]
> Począwszy od programu Visual Studio 2017, usługa języka JavaScript używa nowego aparatu dla usługi językowej (o nazwie "Salsa"). Szczegółowe informacje znajdują się w tym artykule i można także przeczytać ten [wpis w blogu](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Nowe środowisko edycji ma również zastosowanie do Visual Studio Code. Więcej informacji można znaleźć w dokumentacji [vs Code](https://code.visualstudio.com/docs/languages/javascript) .

Aby uzyskać więcej informacji na temat ogólnej funkcji IntelliSense programu Visual Studio, zobacz [Używanie technologii IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Co nowego w usłudze języka JavaScript w programie Visual Studio 2017

Począwszy od programu Visual Studio 2017, język JavaScript IntelliSense wyświetla więcej informacji na temat list parametrów i elementów członkowskich. Nowe informacje są dostarczane przez usługę języka TypeScript, która używa analizy statycznej w tle, aby lepiej zrozumieć swój kod.

Program TypeScript używa kilku źródeł do tworzenia tych informacji:

- [Technologia IntelliSense oparta na wnioskach o typie](#TypeInference)
- [Technologia IntelliSense oparta na JSDoc](#JsDoc)
- [Technologia IntelliSense oparta na plikach deklaracji TypeScript](#TsDeclFiles)
- [Automatyczne pobieranie definicji typu](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>Technologia IntelliSense oparta na wnioskach o typie

W języku JavaScript większość niepełnych informacji o typie nie jest dostępna. Na szczęście, jest to zwykle dość łatwe do ustalenia typu z otaczającym kontekstem kodu.
Ten proces jest nazywany wnioskami o typie.

Dla zmiennej lub właściwości Typ jest zazwyczaj typem wartości użytej do zainicjowania go lub ostatniego przypisania wartości.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Dla funkcji zwracanego typu można wywnioskować na podstawie instrukcji return.

W przypadku parametrów funkcji nie ma obecnie żadnych wniosków, ale istnieją sposoby obejścia tego problemu przy użyciu plików JSDoc lub TypeScript *. d. TS* (zobacz sekcję w dalszej części).

Dodatkowo istnieją specjalne wnioskowanie dotyczące następujących:

- Klasy "ES3-Style", określone przy użyciu funkcji konstruktora i przypisań do właściwości prototypu.
- Wzorce modułu CommonJS, określone jako przypisania właściwości w obiekcie `exports` lub przypisania do właściwości `module.exports`.

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

### <a name="intellisense-based-on-jsdoc"></a>Technologia IntelliSense oparta na JSDoc

Gdzie wnioskowanie typu nie zapewnia informacji o żądanym typie (lub do obsługi dokumentacji), informacje o typie mogą być udostępniane jawnie za pośrednictwem adnotacji JSDoc.  Na przykład, aby nadać częściowo zadeklarowany obiekt określonego typu, można użyć tagu `@type`, jak pokazano poniżej:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak wspomniano, parametry funkcji nigdy nie są wywnioskowane. Jednak za pomocą tagu `@param` JSDoc można także dodawać typy do parametrów funkcji.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Zobacz [obsługę JSDoc w języku JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) dla obecnie obsługiwanych adnotacji JSDoc.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>Technologia IntelliSense oparta na plikach deklaracji TypeScript

Ponieważ skrypty JavaScript i TypeScript są teraz oparte na tej samej usłudze językowej, są w stanie korzystać z bogatszego sposobu działania. Na przykład można udostępnić kod JavaScript IntelliSense dla wartości zadeklarowanych w pliku *d. TS* (zobacz dokumentację języka [TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), a typy takie jak interfejsy i klasy zadeklarowane w języku TypeScript są dostępne do użycia jako typy w komentarzach JsDoc.

Poniżej przedstawiono prosty przykład pliku definicji TypeScript, który udostępnia takie informacje o typie (za pośrednictwem interfejsu) do pliku JavaScript w tym samym projekcie (przy użyciu tagu `JsDoc`).

![Plik definicji TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatyczne pobieranie definicji typu

W środowisku TypeScript, najpopularniejsze biblioteki JavaScript mają swoje interfejsy API opisane przez pliki *d. TS* , a najpopularniejsze repozytorium dla takich definicji znajduje się w [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Domyślnie usługa języka Salsa podejmie próbę wykrycia, które biblioteki JavaScript są używane, i automatycznie pobrać i odwołać się do odpowiedniego pliku *d. TS* , który opisuje bibliotekę w celu zapewnienia bogatszej technologii IntelliSense. Pliki są pobierane do pamięci podręcznej znajdującej się w folderze użytkownika pod adresem *%LocalAppData%\Microsoft\TypeScript*.

> [!NOTE]
> Ta funkcja jest domyślnie **wyłączona** , jeśli jest używany plik konfiguracji *tsconfig. JSON* , ale może być ustawiony na wartość włączone, jak opisano poniżej.

Obecnie Autowykrywanie działa w przypadku zależności pobranych z npm (przez odczytywanie pliku *Package. JSON* ), Bower (przez odczytanie pliku *Bower. JSON* ) oraz dla luźnych plików w projekcie, które pasują do listy najbardziej popularnych bibliotek JavaScript w najwyższej 400. Na przykład jeśli w projekcie jest *jQuery-1.10. min. js* , plik *jQuery. d. TS* zostanie pobrany i załadowany w celu zapewnienia lepszego środowiska edycji. Ten plik *. d. TS* nie będzie miał wpływu na Twój projekt.

Jeśli nie chcesz używać autopozyskiwania, wyłącz je, dodając plik konfiguracyjny opisany poniżej. Można nadal ręcznie umieszczać pliki definicji do użycia bezpośrednio w projekcie.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Obsługa języka JavaScript (Visual Studio dla komputerów Mac)](/visualstudio/mac/javascript)
