---
title: JavaScript
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: jillfra
monikerRange: vs-2017
ms.openlocfilehash: 653b2576b0076d02f2e18cedc6f9f9890fd98fe5
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888662"
---
# <a name="javascript-in-visual-studio-2017"></a>Język JavaScript w programie Visual Studio 2017

JavaScript to język pierwszej klasy w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). Można napisać kod JavaScript dla wielu typów i usług aplikacji.

> [!NOTE]
> Dodaliśmy do społeczności społeczność rzeczy, aby powiadomienia MDN w witrynie [sieci Web dokumenty](https://developer.mozilla.org/en-US/) z jednym zatrzymywaniem, bardzo różnorodnym zasobem programistycznym, przekierowując wszystkie (500 + strony) informacje o interfejsie API języka JavaScript firmy Microsoft z docs.Microsoft.com do ich odpowiedników powiadomienia MDN. Aby uzyskać szczegółowe informacje, zobacz ten [anons](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="ES6"></a>Obsługa języka ECMAScript 2015 (ES6) i poza nim

Program Visual Studio obsługuje teraz składnię aktualizacji języka ECMAScript, takich jak ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co to jest ECMAScript 2015?

Kod JavaScript ciągle się rozwija jako język programowania, a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) jest odpowiedzialny za Dokonywanie aktualizacji.
ECMAScript 2015 to Aktualizacja języka JavaScript, która umożliwia korzystanie z nowej składni i funkcji. Aby uzyskać głębokie szczegółowe na temat funkcji ES6, zapoznaj się z [tą](http://es6-features.org/#Constants) lokacją odniesienia.

Oprócz obsługi języka ECMAScript 2015, Visual Studio obsługuje również ECMAScript 2016 i będzie obsługiwał przyszłe wersje języka ECMAScript w miarę ich wydaniu. Aby zachować TC39 i najnowsze zmiany w języku ECMAScript, postępuj zgodnie z ich pracą w witrynie [GitHub](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transstertowanie kodu JavaScript

Typowym problemem związanym z JavaScript jest korzystanie z najnowszych funkcji języka ES6 +, ponieważ mogą one zwiększyć produktywność, ale środowiska uruchomieniowe (często przeglądarki) nie obsługują jeszcze tych nowych funkcji. Oznacza to, że trzeba będzie śledzić, które przeglądarki obsługują funkcje (które mogą być żmudnym), lub że konieczne jest przekonwertowanie kodu ES6 + na wersję, którą ma zrozumieć docelowy program obsługi (zwykle ES5). Konwersja kodu do wersji, którą rozpoznaje środowisko uruchomieniowe, jest często określana jako "transpiling".

Jedną z najważniejszych funkcji języka TypeScript jest możliwość transsterty ES6 + Code do ES5 lub ES3, dzięki czemu można napisać kod, który zapewnia największą produktywność, ale nadal uruchamia kod na dowolnej platformie. Ponieważ język JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] korzysta z tej samej usługi językowej co TypeScript, można skorzystać z zalet ES6 + ES5 transpilation.

Aby można było skonfigurować transpilation, jest wymagane pewne zrozumienie opcji konfiguracji.
Język TypeScript jest konfigurowany za pośrednictwem pliku `tsconfig.json`.
W przypadku braku takiego pliku są używane pewne wartości domyślne.
Ze względu na zgodność te wartości domyślne są inne w kontekście, w którym znajdują się tylko pliki JavaScript (i opcjonalnie `.d.ts` pliki).
Aby kompilować pliki JavaScript, należy dodać plik `tsconfig.json` i niektóre z tych opcji muszą zostać ustawione jawnie.

Wymagane ustawienia dla pliku tsconfig są następujące:

- `allowJs`: Ta wartość musi być ustawiona na `true`, aby można było rozpoznać pliki JavaScript. Wartość domyślna to `false`, ponieważ program TypeScript kompiluje się do języka JavaScript, a kompilator nie powinien zawierać plików, które właśnie skompilowano.
- `outDir`: Ta wartość powinna być ustawiona na lokalizację, która nie jest uwzględniona w projekcie, w kolejności, w jakiej emitowane pliki JavaScript nie są wykrywane, a następnie uwzględniane w projekcie (zobacz `exclude`).
- `module`: Jeśli używasz modułów, to ustawienie instruuje kompilator, który format modułu, który emituje kod powinien używać (na przykład `commonjs` dla węzła lub dla pakietów, takich jak Browserify).
- `exclude`: to ustawienie określa, które foldery nie mają być uwzględnione w projekcie.
Do tego ustawienia należy dodać lokalizację wyjściową, a także foldery spoza projektu, takie jak `node_modules` lub `temp`.
- `enableAutoDiscovery`: to ustawienie umożliwia automatyczne wykrywanie i pobieranie plików definicji zgodnie z wcześniejszym opisem.
- `compileOnSave`: to ustawienie instruuje kompilator, jeśli powinien ponownie kompilować plik źródłowy w programie Visual Studio.
- `typeAcquisition`: ten zestaw ustawień steruje zachowaniem automatycznego pozyskiwania typów (w dalszej [części tego](/visualstudio/ide/javascript-intellisense#Auto)tematu)

Aby przekonwertować pliki JavaScript na moduły CommonJS i umieścić je w folderze `./out`, można użyć następującego pliku `tsconfig.json`:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Jeśli plik źródłowy (`./app.js`) istniał i zawiera kilka funkcji języka ECMAScript 2015 w następujący sposób:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Następnie plik zostanie wyemitowany do `./out/app.js` docelowego języka ECMAScript 5 (domyślnie), który wygląda podobnie do poniższego:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Lepsza technologia IntelliSense

Funkcja IntelliSense języka JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] będzie teraz wyświetlała więcej informacji na temat parametrów i list elementów członkowskich. Nowe informacje są dostarczane przez usługę języka TypeScript, która używa analizy statycznej w tle, aby lepiej zrozumieć swój kod. Więcej informacji na temat nowego środowiska IntelliSense i sposobu jego działania można znaleźć w [tym miejscu](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a>Obsługa składni JSX

Język JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] ma rozbudowaną obsługę składni JSX. JSX to zestaw składni, który umożliwia Tagi HTML w plikach JavaScript.

Na poniższej ilustracji przedstawiono składnik reakcji zdefiniowany w pliku `comps.tsx` TypeScript, a następnie ten składnik jest używany z pliku `app.jsx`, uzupełniany przy użyciu funkcji IntelliSense do uzupełniania i dokumentacji w wyrażeniach JSX.
Nie potrzebujesz języka TypeScript w tym miejscu, tym konkretnym przykładem może być również kod języka TypeScript.

![Składnia JSX](../javascript/media/js-react.png)

> [!NOTE]
> Aby skonwertować składnię JSX na wywołania reakcji, należy dodać ustawienie `"jsx": "react"` do `compilerOptions` w pliku `tsconfig.json`.

Plik JavaScript utworzony w lokalizacji "./out/App.js" podczas kompilacji będzie zawierać kod:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurowanie projektu JavaScript

Usługa językowa jest oparta na analizie statycznej, co oznacza, że analizuje kod źródłowy bez jego rzeczywistego wykonywania w celu zwracania wyników IntelliSense i zapewnia inne funkcje edycji.
W związku z tym większa ilość i rozmiar plików, które znajdują się w danym kontekście projektu, użycie większej ilości pamięci i procesora CPU będzie możliwe podczas analizy.
W związku z tym istnieje kilka domyślnych założeń dotyczących kształtu projektu:

- zależności `package.json` i `bower.json`y używane przez projekt i domyślnie są uwzględniane w funkcji automatycznego pozyskiwania typów (ATA)
- Folder `node_modules` najwyższego poziomu zawiera kod źródłowy biblioteki, a jego zawartość jest domyślnie wykluczona z kontekstu projektu
- Każdy inny `.js`, `.jsx`, `.ts`i plik `.tsx` jest prawdopodobnie jednym z *własnych* plików źródłowych i musi być uwzględniony w kontekście projektu

W większości przypadków można po prostu otworzyć projekt i uzyskać doskonałe środowisko przy użyciu domyślnej konfiguracji projektu. Jednak w projektach, które są duże lub mają różne struktury folderów, może być pożądane dalsze skonfigurowanie usługi językowej w celu lepszego skoncentrowania się tylko na własnych plikach źródłowych.

### <a name="override-defaults"></a>Przesłoń wartości domyślne

Konfigurację domyślną można zastąpić, dodając plik `tsconfig.json` do katalogu głównego projektu.
`tsconfig.json` ma kilka różnych opcji, które mogą manipulować kontekstem projektu.
Poniżej wymieniono kilka z nich, ale pełny zestaw wszystkich dostępnych opcji [można znaleźć w artykule magazyn schematu](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Ważne opcje `tsconfig.json`

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Przykładowa konfiguracja projektu

Nadany projekt o następującej konfiguracji:

- pliki źródłowe projektu znajdują się w `wwwroot/js`
- Pliki lib projektu znajdują się w `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation`i `jquery-validation-unobtrusive` są wymienione w `bower.json`
- `kendo-ui` został ręcznie dodany do folderu lib

![Struktura folderów](../javascript/media/js-folderstructure.png)

Poniższe `tsconfig.json` można użyć, aby upewnić się, że usługa języka analizuje tylko pliki źródłowe w folderze `js`, ale nadal pobiera i używa plików `.d.ts` dla bibliotek w folderze `lib`.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Rozwiązywanie problemów z usługą języka JavaScript została wyłączona dla następujących projektów
Po otwarciu projektu JavaScript z bardzo dużą ilością zawartości może zostać wyświetlony komunikat "Usługa języka JavaScript została wyłączona dla następujących projektów" (). Najbardziej typową przyczyną wystąpienia bardzo dużej ilości źródła JavaScript jest dołączenie bibliotek z kodem źródłowym, które przekraczają limit projektu baza.

Prostym sposobem na optymalizację projektu jest dodanie `tsconfig.json` pliku w katalogu głównym projektu, aby poinformować usługę języka o tym, które pliki są bezpieczne do ignorowania. Użyj poniższego przykładu, aby wykluczyć najpopularniejsze katalogi, w których są przechowywane biblioteki:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Dodaj więcej katalogów w miarę potrzeb. Niektóre inne przykłady obejmują katalogi "Vendor" lub "wwwroot/lib".

> [!NOTE]
> Właściwości kompilatora `disableSizeLimit` można również użyć, aby wyłączyć limit sprawdzania baza. W przypadku korzystania z tej właściwości należy podjąć specjalne środki ostrożności, ponieważ wyłączenie limitu może spowodować awarię usługi językowej.

## <a name="notable-changes-from-visual-studio-2015"></a>Istotne zmiany w programie Visual Studio 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkcje zupełnie nowej usługi językowej, istnieje kilka zachowań, które będą się różnić lub nieobecne w poprzednim środowisku.
Najbardziej istotnymi zmianami są zastąpienie VSDoc z JSDoc, usuwanie niestandardowych rozszerzeń `.intellisense.js` i ograniczoną technologią IntelliSense dla określonych wzorców kodu.

### <a name="no-more-references-or-_referencesjs"></a>Nie ma więcej `///<references/>` lub `_references.js`

Wcześniej było to dość skomplikowane, aby zrozumieć w dowolnym momencie, które pliki znajdowały się w zakresie funkcji IntelliSense. Czasami było wskazane, aby wszystkie pliki były w określonym zakresie, a inne nie były, a to doprowadziło do złożonych konfiguracji obejmujących ręczne Zarządzanie odwołaniami. W przód nie trzeba już myśleć o zarządzaniu odwołaniami i dlatego nie potrzebujesz potrójnych odwołań do komentarzy ani plików `_references.js`.

Więcej informacji na temat działania technologii IntelliSense można znaleźć na stronie [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) .

### <a name="vsdoc"></a>VSDoc

Komentarze dokumentacji XML, czasami określane jako VSDocs, mogły być wcześniej używane do dekorować kodu źródłowego z dodatkowymi danymi, które będą używane do buff wyników IntelliSense.
VSDoc nie jest już obsługiwana na korzyść [JSDoc](https://jsdoc.app/about-getting-started.html) , która jest łatwiejsza do pisania i zaakceptowana Standard dla języka JavaScript.

### <a name="intellisensejs-extensions"></a>rozszerzenia `.intellisense.js`

Wcześniej można było tworzyć [rozszerzenia IntelliSense](https://msdn.microsoft.com/library/hh874692.aspx) , które umożliwiają dodawanie niestandardowych wyników uzupełniania dla bibliotek innych firm.
Te rozszerzenia były dość trudne do pisania i instalowania i odwoływania się do nich są trudne, więc przekazanie nowej usługi językowej nie będzie obsługiwać tych plików.
Dzięki łatwiejszej alternatywie można napisać plik definicji TypeScript, aby zapewnić te same korzyści funkcji IntelliSense, co w przypadku starych rozszerzeń `.intellisense.js`.
Więcej informacji na temat tworzenia pliku deklaracji (`.d.ts`) można znaleźć [tutaj](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nieobsługiwane wzorce

Ponieważ nowa usługa języka jest oparta na analizie statycznej, a nie w aparacie wykonywania (Przeczytaj [ten problem](https://github.com/Microsoft/TypeScript/issues/4789) , aby uzyskać informacje o różnicach), istnieje kilka wzorców języka JavaScript, które nie mogą już być wykrywane.
Najbardziej typowym wzorcem jest wzorzec "expando".
Obecnie usługa językowa nie może zapewnić funkcji IntelliSense dla obiektów, które mają właściwości, które są włączone po deklaracji.
Na przykład:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Można to zrobić, deklarując właściwości podczas tworzenia obiektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Możesz również dodać komentarz JSDoc w następujący sposób:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
