---
title: JavaScript
description: Dowiedz się, że podczas pisania kodu JavaScript w Visual Studio IDE można używać większości lub wszystkich standardowych pomocy w edytowaniu (fragmentów kodu, funkcji IntelliSense itp.).
ms.custom: SEO-VS-2020
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 79c7c13ea80e32e80d32c04052269cb814072aeb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232911"
---
# <a name="javascript-in-visual-studio-2017"></a>Język JavaScript w programie Visual Studio 2017

JavaScript to język najwyższej klasy w Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). Kod JavaScript można napisać dla wielu typów aplikacji i usług.

> [!NOTE]
> Dołączyliśmy do całej społeczności, aby dokumenty internetowe [MDN](https://developer.mozilla.org/en-US/) były jednym z najbardziej premierowych zasobów deweloperskich, przekierowujejąc wszystkie (ponad 500 stron) odwołania do interfejsu API języka JavaScript firmy Microsoft z usługi docs.microsoft.com do ich odpowiedników MDN. Aby uzyskać szczegółowe informacje, zobacz to [zawiadomienie.](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> Obsługa języka ECMAScript 2015 (ES6) i innych

Visual Studio obsługuje teraz składnię aktualizacji języka ECMAScript, takich jak ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Co to jest ECMAScript 2015?

Język JavaScript nadal ewoluuje jako język programowania, a [TC39](https://www.ecma-international.org/memento/tc39-m.htm) jest komitetem odpowiedzialnym za tworzenie aktualizacji.
EcMAScript 2015 to aktualizacja języka JavaScript, która zapewnia pomocną nową składnię i funkcjonalność. Aby uzyskać więcej informacji na temat funkcji ES6, zapoznaj się z [tą witryną](http://es6-features.org/#Constants) referencyjną.

Oprócz obsługi języka ECMAScript 2015, program Visual Studio obsługuje również język ECMAScript 2016 i będzie obsługiwać przyszłe wersje języka ECMAScript, gdy zostaną wydane. Aby być na bieżąco ze standardem TC39 i najnowszymi zmianami w języku ECMAScript, postępuj zgodnie z ich zmianami w [GitHub](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpile JavaScript

Powszechnym problemem w języku JavaScript jest to, że chcesz korzystać z najnowszych funkcji języka ES6+, ponieważ pomagają one wydajniej pracować, ale środowiska uruchomieniowe (często przeglądarki) nie obsługują jeszcze tych nowych funkcji. Oznacza to, że musisz śledzić, które przeglądarki obsługują jakie funkcje (co może być pracochłonne) lub potrzebujesz sposobu na przekonwertowanie kodu ES6+ na wersję zrozumiałą dla docelowych środowisk uruchomieniowych (zazwyczaj ES5). Konwertowanie kodu na wersję zrozumiałą dla środowiska uruchomieniowego jest często określane jako "transpiling".

Jedną z kluczowych funkcji języka TypeScript jest możliwość transpilowania kodu ES6+ na ES5 lub ES3, dzięki czemu można napisać kod, który zapewnia najbardziej wydajną pracę, ale nadal uruchamiać kod na dowolnej platformie. Ponieważ język JavaScript w programie korzysta z tej samej usługi językowej co język TypeScript, może również korzystać z [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] transpilacji ES6+ do ES5.

Przed skonfigurowaniem transpilacji wymagane jest pewne zrozumienie opcji konfiguracji.
Język TypeScript jest konfigurowany za pośrednictwem `tsconfig.json` pliku .
W przypadku braku takiego pliku są używane niektóre wartości domyślne.
Ze względu na zgodność te wartości domyślne różnią się w kontekście, w którym znajdują się tylko pliki JavaScript (i opcjonalnie `.d.ts` pliki).
Aby skompilować pliki JavaScript, należy dodać plik, a niektóre `tsconfig.json` z tych opcji należy ustawić jawnie.

Wymagane ustawienia dla pliku tsconfig są następujące:

- `allowJs`: ta wartość musi być ustawiona na `true` , aby pliki JavaScript zostały rozpoznane. Wartość domyślna to , ponieważ typeScript kompiluje się do języka JavaScript, a kompilator nie powinien `false` zawierać właśnie skompilowanych plików.
- `outDir`: Tę wartość należy ustawić na lokalizację, która nie jest uwzględniona w projekcie, aby emitowane pliki JavaScript nie zostały wykryte, a następnie uwzględnione w projekcie (zobacz `exclude` ).
- `module`: Jeśli używasz modułów, to ustawienie informuje kompilator, którego formatu modułu powinien używać emitowany kod (na przykład w przypadku języka Node lub `commonjs` pakietów, takich jak Browserify).
- `exclude`: to ustawienie określa foldery, które nie mają być dołączane do projektu.
Do tego ustawienia należy dodać lokalizację wyjściową, a także foldery spoza projektu, takie jak `node_modules` `temp` lub .
- `enableAutoDiscovery`: to ustawienie umożliwia automatyczne wykrywanie i pobieranie plików definicji, jak opisano wcześniej.
- `compileOnSave`: to ustawienie informuje kompilator, czy powinien zostać ponownie skompilowany za każdym razem, gdy plik źródłowy zostanie zapisany w Visual Studio.
- `typeAcquisition`: ten zestaw ustawień steruje zachowaniem automatycznego pozyskiwania typu (dalsze objaśnianie [w tej sekcji)](../ide/javascript-intellisense.md#Auto)

Aby przekonwertować pliki JavaScript na moduły CommonJS i umieścić je w `./out` folderze, można użyć następującego `tsconfig.json` pliku:

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

Jeśli plik źródłowy () istniał i zawierał kilka funkcji języka ECMAScript 2015 w następujący sposób, po wymuś te `./app.js` ustawienia:

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

Następnie plik będzie emitowany do określania wartości `./out/app.js` docelowej ECMAScript 5 (ustawienie domyślne), który wygląda podobnie do następującego:

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

## <a name="better-intellisense"></a>Lepsza funkcja IntelliSense

Funkcja IntelliSense języka JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] w programie będzie teraz wyświetlać o wiele więcej informacji na temat parametrów i list członków. Te nowe informacje są dostarczane przez usługę językową TypeScript, która używa analizy statycznej w tle, aby lepiej zrozumieć kod. Więcej informacji na temat nowego działania funkcji IntelliSense i sposobu jej działania można znaleźć [tutaj.](../ide/javascript-intellisense.md)

## <a name="jsx-syntax-support"></a><a name="JSX"></a> Obsługa składni języka JSX

Język JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] w programie obsługuje bogatą obsługę składni JSX. JSX to zestaw składni, który umożliwia korzystanie z tagów HTML w plikach JavaScript.

Na poniższej ilustracji przedstawiono składnik języka React zdefiniowany w pliku TypeScript, a następnie ten składnik jest używany z pliku , wraz z intelliSense do uzupełniania i dokumentacji w wyrażeniach `comps.tsx` `app.jsx` JSX.
Nie potrzebujesz tutaj języka TypeScript. Ten konkretny przykład po prostu zawiera kod Języka TypeScript.

![Składnia języka JSX](../javascript/media/js-react.png)

> [!NOTE]
> Aby przekonwertować składnię JSX na React wywołania, należy dodać ustawienie do pliku `"jsx": "react"` `compilerOptions` w pliku `tsconfig.json` .

Plik JavaScript utworzony w pliku "./out/app.js" podczas kompilacji będzie zawierać kod:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurowanie projektu JavaScript

Usługa językowa jest napędzana przez analizę statyczną, co oznacza, że analizuje kod źródłowy bez wykonywania go w celu zwrócenia wyników funkcji IntelliSense i zapewnienia innych funkcji edycji.
W związku z tym im większa jest ilość i rozmiar plików uwzględnionych w kontekście projektu, tym więcej pamięci i procesora CPU zostanie użytych podczas analizy.
W związku z tym istnieje kilka domyślnych założeń dotyczących kształtu projektu:

- `package.json` i wyświetlić listę zależności używanych przez projekt i domyślnie są `bower.json` uwzględniane w automatycznym pozyskiwaniu typu (ATA)
- Folder najwyższego poziomu zawiera kod źródłowy biblioteki, a jego zawartość jest domyślnie `node_modules` wykluczona z kontekstu projektu
- Każdy inny plik , , i jest prawdopodobnie jednym z Twoich własnych plików źródłowych i `.js` musi `.jsx` być `.ts` `.tsx` uwzględniony w kontekście projektu 

W większości przypadków będzie można po prostu otworzyć projekt i dobrze korzystać z domyślnej konfiguracji projektu. Jednak w projektach, które są duże lub mają różne struktury folderów, może być wskazane dalsze skonfigurowanie usługi językowej, aby lepiej skupić się tylko na własnych plikach źródłowych.

### <a name="override-defaults"></a>Przesłanianie wartości domyślnych

Konfigurację domyślną można przesłonić, `tsconfig.json` dodając plik do katalogu głównego projektu.
Obiekt `tsconfig.json` ma kilka różnych opcji, które mogą manipulować kontekstem projektu.
Poniżej wymieniono kilka z nich, ale aby uzyskać pełny zestaw wszystkich dostępnych opcji, [zobacz magazyn schematów](http://json.schemastore.org/tsconfig).

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

- pliki źródłowe projektu znajdują się w `wwwroot/js`
- pliki lib projektu znajdują się w `wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation` , i są wymienione `jquery-validation-unobtrusive` w `bower.json`
- `kendo-ui` został ręcznie dodany do folderu lib

![Struktura folderów](../javascript/media/js-folderstructure.png)

Możesz użyć poniższej funkcji, aby upewnić się, że usługa językowa analizuje tylko pliki źródłowe w folderze, ale nadal pobiera i używa plików dla bibliotek w `tsconfig.json` `js` `.d.ts` `lib` folderze.

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
Po otwarciu projektu w języku JavaScript, który ma bardzo dużą ilość zawartości, może zostać wyświetlony komunikat "Usługa języka JavaScript została wyłączona dla następujących projektów". Najczęstszą przyczyną posiadania bardzo dużej ilości źródła języka JavaScript jest to, że biblioteki z kodem źródłowym przekraczają limit projektów 20 MB.

Prostym sposobem optymalizacji projektu jest dodanie pliku w katalogu głównym projektu, aby usługa językowa wiedziała, które pliki można bezpiecznie `tsconfig.json` ignorować. Użyj poniższego przykładu, aby wykluczyć najbardziej typowe katalogi, w których są przechowywane biblioteki:

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

Dodaj więcej katalogów zgodnie z potrzebami. Niektóre inne przykłady obejmują katalogi "vendor" lub "wwwroot/lib".

> [!NOTE]
> Właściwość kompilatora może również służyć do `disableSizeLimit` wyłączania limitu sprawdzania 20 MB. Podczas korzystania z tej właściwości należy zachować specjalne środki ostrożności, ponieważ wyłączenie limitu może spowodować awarię usługi językowej.

## <a name="notable-changes-from-visual-studio-2015"></a>Zmiany notable changes from Visual Studio 2015

Ponieważ [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkcja obejmuje całkowicie nową usługę językową, istnieje kilka zachowań, które będą inne lub nieobecne w poprzednich doświadczeniach.
Najbardziejymi zmianami są zastąpienie narzędzia VSDoc plikiem JSDoc, usunięcie niestandardowych rozszerzeń i ograniczenie funkcji IntelliSense dla `.intellisense.js` określonych wzorców kodu.

### <a name="no-more-references-or-_referencesjs"></a>Nie więcej `///<references/>` lub `_references.js`

Wcześniej zrozumienie, które pliki należy do zakresu funkcji IntelliSense, było w danym momencie dość skomplikowane. Czasami pożądane było, aby wszystkie pliki były w zakresie, a czasami nie, co prowadziło do złożonych konfiguracji obejmujących ręczne zarządzanie odwołaniami. W przyszłości nie trzeba już myśleć o zarządzaniu odwołaniami, a więc nie potrzebujesz trzykrotnego ukośnika odwołań do komentarzy ani `_references.js` plików.

Aby uzyskać więcej informacji na temat działania funkcji IntelliSense, zobacz stronę [JavaScript IntelliSense.](../ide/javascript-intellisense.md)

### <a name="vsdoc"></a>VSDoc

Komentarze dokumentacji XML, czasami określane jako VSDocs, mogły być wcześniej używane do dekorowania kodu źródłowego dodatkowymi danymi, które byłyby używane do poprawiania wyników funkcji IntelliSense.
VsDoc nie jest już obsługiwany na rzecz [JSDoc,](https://jsdoc.app/about-getting-started.html) który jest łatwiejszy do napisania i zaakceptowany standard dla języka JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Rozszerzenia

Wcześniej można było tworzyć [rozszerzenia IntelliSense, które](/previous-versions/visualstudio/visual-studio-2015/ide/extending-javascript-intellisense) umożliwiają dodawanie niestandardowych wyników uzupełniania dla bibliotek innych firm.
Te rozszerzenia były dość trudne do napisania i zainstalowania, a odwoływanie się do nich było kłopotliwe, więc w przyszłości nowa usługa językowa nie będzie obsługiwać tych plików.
Jako łatwiejszą alternatywę możesz napisać plik definicji języka TypeScript, aby zapewnić te same korzyści funkcji IntelliSense co `.intellisense.js` stare rozszerzenia.
Więcej informacji na temat tworzenia pliku deklaracji ( `.d.ts` ) można znaleźć [tutaj.](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)

### <a name="unsupported-patterns"></a>Nieobsługiwane wzorce

Ponieważ nowa usługa językowa jest napędzana przez analizę statyczną, a nie aparat wykonywania (przeczytaj ten problem, aby uzyskać informacje o różnicach), istnieje kilka wzorców języka JavaScript, których nie można już wykryć. [](https://github.com/Microsoft/TypeScript/issues/4789)
Najbardziej powszechnym wzorcem jest wzorzec "expando".
Obecnie usługa językowa nie może zapewnić funkcji IntelliSense w obiektach, które mają właściwości naklejone po deklaracji.
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
