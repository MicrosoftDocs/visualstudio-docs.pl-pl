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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75b2a336cf9a229b4834b68e0f7bed5d6b1174f4
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233072"
---
# <a name="javascript-in-visual-studio-2017"></a>Język JavaScript w programie Visual Studio 2017

JavaScript to pierwszorzędny język w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). Można napisać kod JavaScript dla wielu typów aplikacji i usług.

> [!NOTE]
> Połączyliśmy się z ogólnospołecznymi wysiłkami, aby [dokumenty internetowe MDN](https://developer.mozilla.org/en-US/) stały się kompleksowym, premierowym zasobem deweloperskim w sieci Web, przekierowując wszystkie (ponad 500 stron) odwołania do interfejsu API JavaScript firmy Microsoft z docs.microsoft.com do ich odpowiedników MDN. Aby uzyskać szczegółowe informacje, zobacz to [ogłoszenie](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a>Obsługa ecmascript 2015 (ES6) i nie tylko

Program Visual Studio obsługuje teraz składnię aktualizacji języka ECMAScript, takich jak ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co to jest ECMAScript 2015?

JavaScript wciąż ewoluuje jako język programowania, a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) jest komisją odpowiedzialną za wprowadzanie aktualizacji.
ECMAScript 2015 to aktualizacja języka JavaScript, która wprowadza nową, pomocną składnię i funkcjonalność. Aby zapoznać się z funkcjami ES6, zapoznaj się z [tą](http://es6-features.org/#Constants) witryną referencyjną.

Oprócz obsługi języka ECMAScript 2015 program Visual Studio obsługuje również program ECMAScript 2016 i będzie miał obsługę przyszłych wersji programu ECMAScript w miarę ich wydań. Aby nadążyć za TC39 i najnowszymi zmianami w ECMAScript, postępuj zgodnie z ich pracami nad [github](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpile JavaScript

Częstym problemem z javascript jest to, że chcesz korzystać z najnowszych funkcji języka ES6 +, ponieważ pomagają one być bardziej wydajne, ale środowiska wykonawcze (często przeglądarki) nie obsługują jeszcze tych nowych funkcji. Oznacza to, że albo trzeba śledzić, które przeglądarki obsługują jakie funkcje (co może być uciążliwe), lub potrzebujesz sposobu, aby przekonwertować kod ES6 + do wersji, którą rozumieją docelowe środowiska wykonawcze (zwykle ES5). Konwersja kodu do wersji, która rozumie środowiska wykonawczego jest powszechnie określane jako "transpiling".

Jedną z kluczowych funkcji Języka TypeScript jest możliwość transpile ES6 + kod do ES5 lub ES3, dzięki czemu można napisać kod, który sprawia, że najbardziej produktywne, ale nadal uruchomić kod na dowolnej platformie. Ponieważ JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] w użyciu tej samej usługi języka jako TypeScript, to też może korzystać z ES6 + do ES5 transpilacji.

Przed konfiguracją transpilacji wymagane jest zrozumienie opcji konfiguracji.
TypeScript jest konfigurowany za pomocą `tsconfig.json` pliku.
W przypadku braku takiego pliku używane są niektóre wartości domyślne.
Ze względu na zgodność te wartości domyślne różnią się w kontekście, w którym znajdują się tylko pliki JavaScript (i opcjonalnie `.d.ts` pliki).
Aby skompilować pliki `tsconfig.json` JavaScript, należy dodać plik, a niektóre z tych opcji muszą być ustawione jawnie.

Wymagane ustawienia dla pliku tsconfig są następujące:

- `allowJs`: Ta wartość musi `true` być ustawiona na rozpoznawanie plików JavaScript. Wartością domyślną jest `false`, ponieważ TypeScript kompiluje się do JavaScript, a kompilator nie powinien zawierać plików, które właśnie skompilował.
- `outDir`: Wartość ta powinna być ustawiona na lokalizację nieuwzględnianą w projekcie, aby nie zostały `exclude`wykryte, a następnie uwzględnione w projekcie (patrz ).
- `module`: W przypadku korzystania z modułów, to ustawienie informuje kompilatora, który format modułu emitowany kod powinien być używany (na przykład `commonjs` dla node lub bundlers, takich jak Browserify).
- `exclude`: To ustawienie określa, które foldery nie mają być uwzględniane w projekcie.
Do tego ustawienia należy dodać lokalizację wyjściową, a także foldery inne niż te, takie jak `node_modules` lub `temp`, które.
- `enableAutoDiscovery`: To ustawienie umożliwia automatyczne wykrywanie i pobieranie plików definicji zgodnie z wcześniejszym opisem.
- `compileOnSave`: To ustawienie informuje kompilator, czy należy ponownie skompilować za każdym razem, gdy plik źródłowy jest zapisywany w programie Visual Studio.
- `typeAcquisition`: Ten zestaw ustawień kontroluje zachowanie automatycznego pozyskiwania typu (dalsze wyjaśnienie w [tej sekcji)](/visualstudio/ide/javascript-intellisense#Auto)

Aby przekonwertować pliki JavaScript na moduły CommonJS i umieścić je w folderze, `./out` można użyć następującego `tsconfig.json` pliku:

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

Z ustawieniami w miejscu, jeśli`./app.js`plik źródłowy ( ) istniał i zawierał kilka funkcji języka ECMAScript 2015 w następujący sposób:

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

Następnie plik zostanie wyemitowany `./out/app.js` do kierowania ECMAScript 5 (domyślnie), który wygląda mniej więcej tak:

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

## <a name="better-intellisense"></a>Lepszy IntelliSense

JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] w będzie teraz wyświetlać dużo więcej informacji na temat parametrów i list członków. Te nowe informacje są dostarczane przez usługę języka TypeScript, która używa analizy statycznej za kulisami, aby lepiej zrozumieć kod. Możesz przeczytać więcej o nowym doświadczeniu IntelliSense i jak to działa [tutaj](/visualstudio/ide/javascript-intellisense/).

## <a name="jsx-syntax-support"></a><a name="JSX"></a>Obsługa składni JSX

JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] w ma bogatą obsługę składni JSX. JSX to zestaw składni, który umożliwia tagi HTML w plikach JavaScript.

Na poniższej ilustracji przedstawiono `comps.tsx` składnik React zdefiniowany w pliku `app.jsx` TypeScript, a następnie ten składnik używany z pliku, wraz z IntelliSense dla uzupełnień i dokumentacji w wyrażeniach JSX.
Nie potrzebujesz typescript tutaj, ten konkretny przykład po prostu dzieje się zawierać jakiś kod TypeScript, jak również.

![Składnia JSX](../javascript/media/js-react.png)

> [!NOTE]
> Aby przekonwertować składnię JSX `"jsx": "react"` na wywołania `compilerOptions` React, `tsconfig.json` ustawienie musi zostać dodane do pliku.

Plik JavaScript utworzony w "./out/app.js" na kompilacji będzie zawierać kod:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurowanie projektu JavaScript

Usługa językowa jest obsługiwana przez analizę statyczną, co oznacza, że analizuje kod źródłowy bez faktycznie wykonywania go w celu zwrócenia wyników IntelliSense i zapewnienia innych funkcji edycji.
W związku z tym im większa ilość i rozmiar plików, które są zawarte w kontekście projektu, tym więcej pamięci i procesora CPU będą używane podczas analizy.
Z tego powodu istnieje kilka domyślnych założeń dotyczących kształtu projektu:

- `package.json`i `bower.json` zależności listy używane przez projekt i domyślnie są uwzględniane w automatycznym naliczania typów (ATA)
- Folder najwyższego poziomu `node_modules` zawiera kod źródłowy biblioteki, a jego zawartość jest domyślnie wykluczona z kontekstu projektu
- Co `.js`drugi `.jsx` `.ts`, `.tsx` , i plik jest prawdopodobnie jednym z *własnych* plików źródłowych i muszą być zawarte w kontekście projektu

W większości przypadków będzie można po prostu otworzyć projekt i mieć duże doświadczenie przy użyciu domyślnej konfiguracji projektu. Jednak w projektach, które są duże lub mają różne struktury folderów, może być pożądane dalsze skonfigurowanie usługi języka, aby lepiej skupić się tylko na własnych plikach źródłowych.

### <a name="override-defaults"></a>Zastępowanie wartości domyślnych

Konfigurację domyślną można zastąpić, `tsconfig.json` dodając plik do katalogu głównego projektu.
A `tsconfig.json` ma kilka różnych opcji, które mogą manipulować kontekstu projektu.
Kilka z nich znajduje się poniżej, ale aby uzyskać pełny zestaw wszystkich dostępnych opcji, [zobacz magazyn schematów](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Ważne `tsconfig.json` opcje

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

Biorąc pod uwagę projekt z następującą konfiguracją:

- pliki źródłowe projektu znajdują się w`wwwroot/js`
- pliki lib projektu znajdują się w`wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation`, `jquery-validation-unobtrusive` i są wymienione w`bower.json`
- `kendo-ui`został ręcznie dodany do folderu lib

![Struktura folderów](../javascript/media/js-folderstructure.png)

`tsconfig.json` Aby upewnić się, że usługa językowa analizuje tylko `js` pliki źródłowe w folderze, `.d.ts` ale nadal pobiera `lib` i używa plików dla bibliotek w folderze.

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Rozwiązywanie problemów Usługa języka JavaScript została wyłączona dla następujących projektów
Po otwarciu projektu JavaScript, który ma bardzo dużą ilość zawartości, może pojawić się komunikat z napisem "Usługa języka JavaScript została wyłączona dla następujących projektów". Najczęstszą przyczyną posiadania bardzo dużej ilości źródła JavaScript jest włączenie bibliotek z kodem źródłowym, który przekracza limit projektu 20MB.

Prostym sposobem optymalizacji projektu jest dodanie `tsconfig.json` pliku w katalogu głównym projektu, aby usługa językowa wiedziała, które pliki są bezpieczne do zignorowania. Użyj poniższego przykładu, aby wykluczyć najpopularniejsze katalogi, w których przechowywane są biblioteki:

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

Dodaj więcej katalogów według własnego uznania. Inne przykłady obejmują katalogi "dostawca" lub "wwwroot/lib".

> [!NOTE]
> Właściwość `disableSizeLimit` kompilatora może również służyć do wyłączenia limitu czeku 20MB. Należy podjąć specjalne środki ostrożności podczas korzystania z tej właściwości, ponieważ wyłączenie limitu może ulec awarii usługi języka.

## <a name="notable-changes-from-visual-studio-2015"></a>Znaczące zmiany w programie Visual Studio 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkcje zupełnie nowej usługi językowej, istnieje kilka zachowań, które będą różne lub nieobecne w poprzednim doświadczeniu.
Najbardziej znaczące zmiany są zastąpienie VSDoc z JSDoc, `.intellisense.js` usunięcie niestandardowych rozszerzeń i ograniczone IntelliSense dla określonych wzorców kodu.

### <a name="no-more-references-or-_referencesjs"></a>Nie `///<references/>` więcej lub`_references.js`

Wcześniej było dość skomplikowane, aby zrozumieć w danym momencie, które pliki były w zakresie IntelliSense. Czasami pożądane było, aby wszystkie pliki w zakresie, a innym razem nie było, a to doprowadziło do złożonych konfiguracji obejmujących ręczne zarządzanie odwołaniami. Idąc dalej, nie musisz już myśleć o zarządzaniu odniesieniami, więc nie `_references.js` potrzebujesz komentarzy ani plików z potrójnym ukośnikiem.

Więcej informacji na temat działania programu IntelliSense można znaleźć na stronie [JavaScript IntelliSense.](/visualstudio/ide/javascript-intellisense/)

### <a name="vsdoc"></a>VSDoc ( vsdoc )

Komentarze dokumentacji XML, czasami określane jako VSDocs, może być wcześniej używany do dekoracji kodu źródłowego z dodatkowych danych, które będą używane do wzmocnienia wyników IntelliSense.
VSDoc nie jest już obsługiwany na rzecz [JSDoc,](https://jsdoc.app/about-getting-started.html) który jest łatwiejszy do napisania i przyjęty standard dla JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js`Rozszerzenia

Wcześniej można było tworzyć [rozszerzenia IntelliSense,](https://msdn.microsoft.com/library/hh874692.aspx) które umożliwiałyby dodawanie niestandardowych wyników uzupełniania bibliotek innych firm.
Rozszerzenia te były dość trudne do zapisania i zainstalowania i odwoływania się do nich było uciążliwe, więc w przyszłości nowa usługa językowa nie będzie obsługiwać tych plików.
Jako łatwiejszą alternatywę można napisać plik definicji TypeScript, aby zapewnić `.intellisense.js` takie same korzyści IntelliSense jak stare rozszerzenia.
Możesz dowiedzieć się`.d.ts`więcej o deklaracji ( ) tworzenie plików [tutaj](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nieobsługiwały się wzory

Ponieważ nowa usługa języka jest obsługiwana przez analizę statyczną, a nie aparat wykonywania (przeczytaj [ten problem,](https://github.com/Microsoft/TypeScript/issues/4789) aby uzyskać informacje o różnicach), istnieje kilka wzorców JavaScript, które nie mogą być już wykrywane.
Najczęstszym wzorcem jest wzór "expando".
Obecnie usługa języka nie może zapewnić IntelliSense na obiekty, które mają właściwości przypięte na po deklaracji.
Przykład:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Można obejść ten problem, deklarując właściwości podczas tworzenia obiektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Można również dodać komentarz JSDoc w następujący sposób:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
