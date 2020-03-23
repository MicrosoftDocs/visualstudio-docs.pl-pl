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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593723"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio zapewnia zaawansowane środowisko edycji JavaScript od razu po wyjęciu z pudełka. Program Visual Studio, oparty na języku TypeScript, zapewnia bogatsze funkcje IntelliSense, obsługę nowoczesnych funkcji języka JavaScript oraz ulepszone funkcje zwiększające produktywność, takie jak Przejdź do definicji, refaktoryzowanie i inne.

> [!NOTE]
> Począwszy od programu Visual Studio 2017 usługa języka JavaScript używa nowego aparatu dla usługi językowej (o nazwie "Salsa"). Szczegóły są zawarte w tym artykule, a także można przeczytać ten [wpis w blogu](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Nowe środowisko edycji dotyczy również głównie visual studio code. Zobacz [dokumenty kodu PROGRAMU VS, aby](https://code.visualstudio.com/docs/languages/javascript) uzyskać więcej informacji.

Aby uzyskać więcej informacji na temat ogólnych funkcji intellisense programu Visual Studio, zobacz [Korzystanie z programu IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Co nowego w usłudze języka JavaScript w programie Visual Studio 2017

Począwszy od programu Visual Studio 2017, JavaScript IntelliSense wyświetla wiele więcej informacji na temat list parametrów i członków. Te nowe informacje są dostarczane przez usługę języka TypeScript, która używa analizy statycznej za kulisami, aby lepiej zrozumieć kod.

Do tworzenia tych informacji system TypeScript używa kilku źródeł:

- [IntelliSense na podstawie wnioskowania o typie](#TypeInference)
- [IntelliSense na podstawie JSDoc](#JsDoc)
- [IntelliSense na podstawie plików deklaracji TypeScript](#TsDeclFiles)
- [Automatyczne nabywanie definicji typów](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>IntelliSense na podstawie wnioskowania o typie

W języku JavaScript w większości przypadków nie ma żadnych jawnych informacji o typie. Na szczęście jest to zwykle dość łatwe do znalezienia typu, biorąc pod uwagę otaczający kontekst kodu.
Ten proces jest nazywany wnioskowaniem o typie.

Dla zmiennej lub właściwości typ jest zazwyczaj typem wartości używanej do jej zainicjowania lub najnowszym przypisaniem wartości.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Dla funkcji typu zwracanego można wywnioskować z instrukcji zwracanej.

W przypadku parametrów funkcji obecnie nie ma wnioskowania, ale istnieją sposoby obejść ten sposób za pomocą plików JSDoc lub TypeScript *.d.ts* (patrz dalsze sekcje).

Ponadto istnieje specjalne wnioskowanie dla następujących czynności:

- Klasy "ES3 stylu", określone przy użyciu funkcji konstruktora i przypisania do właściwości prototype.
- Wzorce modułów w stylu CommonJS, określone `exports` jako przypisania właściwości `module.exports` obiektu lub przypisania do właściwości.

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

### <a name="intellisense-based-on-jsdoc"></a>IntelliSense na podstawie JSDoc

W przypadku gdy wnioskowanie o typie nie zawiera żądanych informacji o typie (lub do obsługi dokumentacji), informacje o typie mogą być dostarczane jawnie za pośrednictwem adnotacji JSDoc.  Na przykład, aby nadać częściowo zadeklarowany obiekt określonej typowi, można użyć znacznika, `@type` jak pokazano poniżej:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Jak wspomniano, parametry funkcji nigdy nie są wywnioskowane. Jednak za pomocą tagu `@param` JSDoc można również dodawać typy do parametrów funkcji.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Zobacz [JSDoc pomocy technicznej w języku JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) dla adnotacji JsDoc obecnie obsługiwane.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense na podstawie plików deklaracji TypeScript

Ponieważ javascript i typescript są teraz oparte na tej samej usłudze językowej, mogą wchodzić w interakcje w bogatszy sposób. Na przykład technologia IntelliSense języka JavaScript może być dostarczana dla wartości zadeklarowanych w pliku *d.ts* (zobacz [dokumentacja TypeScript),](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)a typy, takie jak interfejsy i klasy zadeklarowane w języku TypeScript, są dostępne do użycia jako typy w komentarzach JsDoc.

Poniżej przedstawiamy prosty przykład pliku definicji TypeScript dostarczającego takich informacji o typie (za pośrednictwem `JsDoc` interfejsu) do pliku JavaScript w tym samym projekcie (przy użyciu znacznika).

![Plik definicji TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Automatyczne nabywanie definicji typów

W świecie TypeScript najpopularniejsze biblioteki JavaScript mają swoje interfejsy API opisane przez pliki *.d.ts,* a najczęstsze repozytorium dla takich definicji znajduje się na [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Domyślnie usługa języka Salsa będzie próbowała wykryć, które biblioteki JavaScript są używane i automatycznie pobrać i odwołać się do odpowiedniego pliku *.d.ts,* który opisuje bibliotekę w celu zapewnienia bogatszego IntelliSense. Pliki są pobierane do pamięci podręcznej znajdującej się w folderze użytkownika w *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Ta funkcja jest domyślnie **wyłączona,** jeśli używa pliku konfiguracyjnego *tsconfig.json,* ale może być ustawiona na włączoną, jak opisano poniżej.

Obecnie automatyczne wykrywanie działa dla zależności pobranych z npm (czytając plik *package.json),* Bower (czytając plik *bower.json),* a także dla luźnych plików w projekcie, które pasują do listy około 400 najpopularniejszych bibliotek JavaScript. Na przykład, jeśli masz *jquery-1.10.min.js* w projekcie, plik *jquery.d.ts* zostaną pobrane i załadowane w celu zapewnienia lepszego środowiska edycji. Ten plik *d.ts* nie będzie miał wpływu na projekt.

Jeśli nie chcesz używać automatycznego pozyskiwania, wyłącz go, dodając plik konfiguracyjny, jak opisano poniżej. Nadal można ręcznie umieszczać pliki definicji do użycia bezpośrednio w projekcie.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z IntelliSense](../ide/using-intellisense.md)
- [Obsługa języka JavaScript (Visual Studio dla komputerów Mac)](/visualstudio/mac/javascript)
