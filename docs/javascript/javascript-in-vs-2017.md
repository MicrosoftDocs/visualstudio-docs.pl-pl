---
title: Język JavaScript w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-nodejs
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: jillfra
ms.openlocfilehash: ee22803c7a479c6d22821a9a6b267cd72938792e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013005"
---
# <a name="javascript-in-visual-studio-2017"></a>Język JavaScript w programie Visual Studio 2017

JavaScript jest językiem pierwszej klasy w programie Visual Studio. Podczas pisania kodu w języku JavaScript w środowisku IDE programu Visual Studio można używać większości lub wszystkich standardowych ułatwień edycji (fragmenty kodu, technologia IntelliSense itd.). W przypadku wielu typów aplikacji i usług, można napisać kod JavaScript.

> [!NOTE]
> Przyłączył nakład pracy całej społeczności, aby [dokumentów sieci web powiadomienia MDN](https://developer.mozilla.org/en-US/) zasobu kompleksowy deweloperach projektowania sieci web, przekierowując wszystkich (ponad 500 stron) firmy Microsoft odwołanie interfejsu API języka JavaScript z witryny docs.microsoft.com do ich powiadomienia MDN odpowiedniki. Aby uzyskać więcej informacji, zobacz ten [ogłoszenie](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="ES6"></a> Obsługa dla ECMAScript 2015 (ES6) i nie tylko

Program Visual Studio obsługuje teraz składnię dla aktualizacji języka ECMAScript, takich jak ECMAScript 2015 sierpnia 2016 r.

### <a name="what-is-ecmascript-2015"></a>Co to jest ECMAScript 2015?

Nadal ewoluuje JavaScript jako języka programowania i [TC39](http://www.ecma-international.org/memento/TC39.htm) jest odpowiedzialny za wprowadzanie aktualizacji Komitet.
ECMAScript 2015 r. jest to aktualizacja dla języka JavaScript, którego oferuje przydatne nową składnię i funkcje. Aby uzyskać szczegółowe informacje na temat funkcji ES6, zapoznaj się z [to](http://es6-features.org) lokacji odniesienia.

Oprócz obsługi ECMAScript 2015 Visual Studio obsługuje ECMAScript 2016 i będą oferować obsługę dla przyszłych wersji ECMAScript, po ich wydaniu. Na bieżąco z TC39 i najnowsze zmiany w ECMAScript, postępuj zgodnie z ich pracy na [github](https://github.com/tc39).

### <a name="transpile-javascript"></a>Transpile JavaScript

Typowy problem za pomocą języka JavaScript jest chcesz używać najnowszych funkcji języków ES6 +, ponieważ pomagają mu bardziej wydajnej pracy, ale środowiska czasu wykonywania (często przeglądarki) nie obsługują te nowe funkcje. Oznacza to, że masz albo do śledzenia jakie przeglądarki obsługują funkcjach, (które może być uciążliwe) lub potrzebujesz możliwości wykonania konwersji kodu ES6 + do wersji, środowisk wykonawczych usługi docelowej zrozumieć (zazwyczaj ES5). Konwertowanie kodu na wersję obsługującą środowisko uruchomieniowe jest często określany jako "transpiling".

Jedną z kluczowych funkcji TypeScript jest możliwość transpiluj ES6 kod jest współdzielony ES5 lub ES3, aby napisać kod, który sprawia, że są możesz najwydajniejszej, ale nadal uruchamiać kod na dowolnej platformie. Ponieważ języka JavaScript w programie [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] używa tego samego języka usługi jako TypeScript, zbyt może korzystać ES6 + do ES5 transpilation.

Zanim transpilation można skonfigurować pod kątem, niektóre wiedzę na temat opcji konfiguracji jest wymagana.
TypeScript jest skonfigurowany za pośrednictwem `tsconfig.json` pliku.
W przypadku braku takiego pliku niektóre wartości domyślne są używane.
Ze względu na zgodność, te ustawienia domyślne różnią się w kontekście, w przypadku, gdy tylko pliki JavaScript (i opcjonalnie `.d.ts` plików) występują.
Aby skompilować pliki JavaScript `tsconfig.json` musi zostać dodany plik, a niektóre z tych opcji musi być ustawiony w sposób jawny.

Wymagane ustawienia dla pliku tsconfig są następujące:

 - `allowJs`: Ta wartość musi być równa `true` dla plików JavaScript uznać. Wartość domyślna to `false`, ponieważ TypeScript kompiluje w kodzie JavaScript, a kompilator nie może zawierać tylko skompilowanych plików.
 - `outDir`: Ta wartość powinna być równa lokalizacji nie są uwzględnione w projekcie, że emitowany plików JavaScript nie są wykrywane oraz dołączone do projektu (zobacz `exclude`).
 - `module`: Jeśli przy użyciu modułów, to ustawienie informuje kompilator, który format modułu należy używać emitowany kod (na przykład `commonjs` dla węzła lub narzędzia tworzące pakiety, takich jak Browserify).
 - `exclude`: To ustawienie stanów folderów nie do uwzględnienia w projekcie.
 Lokalizacja danych wyjściowych, foldery poza projektem, takie jak `node_modules` lub `temp`, powinny zostać dodane do tego ustawienia.
 - `enableAutoDiscovery`: To ustawienie umożliwia automatyczne wykrywanie i pobierania plików definicji, co zostało opisane wcześniej.
 - `compileOnSave`: To ustawienie informuje kompilator, jeśli należy ponownie skompilować każdym razem, gdy plik źródłowy jest zapisany w programie Visual Studio.
 - `typeAcquisition`: Ten zbiór ustawień kontrolowania zachowania przejęcia automatyczne typu (dokładniejszego wyjaśnienia w [w tej sekcji](/visualstudio/ide/javascript-intellisense#Auto))

Aby można było przekonwertować plików JavaScript z modułami CommonJS i umieść je w `./out` folderu, można użyć następującego `tsconfig.json` pliku:

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

Przy użyciu ustawień w miejscu, jeśli plik źródłowy (`./app.js`) istnieje i zawiera kilka funkcji języka ECMAScript 2015 w następujący sposób:

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

Wówczas plik będzie emitowany do `./out/app.js` przeznaczonych dla ECMAScript 5 (ustawienie domyślne), który wygląda podobnie do poniższego:

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

Funkcja IntelliSense języka JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] będą teraz wyświetlane znacznie więcej informacji na temat parametrów i listy elementów członkowskich. To nowe informacje są udostępniane przez usługę języka TypeScript, która używa analiza statyczna w tle, aby lepiej zrozumieć swój kod. Możesz przeczytać więcej na temat nowe środowisko IntelliSense, i jak działa [tutaj](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Obsługę składni JSX

Język JavaScript w [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] ma rozbudowaną obsługę składni JSX. JSX to zestaw składnię umożliwiającą tagów HTML w plikach JavaScript.

Na poniższej ilustracji przedstawiono składnik platformy React, zdefiniowane w `comps.tsx` plik TypeScript, a następnie ten składnik używany z `app.jsx` pliku ukończony z obsługą technologii IntelliSense dla uzupełnienia i dokumentach w obrębie wyrażenia JSX.
Nie ma potrzeby TypeScript w tym miejscu, w tym przykładzie określonych dzieją zawierać części kodu TypeScript.

![Składnia JSX](../javascript/media/js-react.png)

> [!NOTE]
> Aby przekonwertować składni JSX React wywołuje, ustawienie `"jsx": "react"` muszą zostać dodane do `compilerOptions` w `tsconfig.json` pliku.

Utworzono plik JavaScript ". / out/app.js podczas kompilacji zawierałoby kod:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurowanie projektu języka JavaScript

Usługa języka jest obsługiwana przez analizy statycznej, co oznacza, że analizuje ona kodu źródłowego bez jego faktycznego wykonania go w celu zwracania wyników funkcji IntelliSense i podaj inne funkcje edycji.
Dlatego im większa ilość i rozmiar plików, które są dołączone kontekst projektu, więcej pamięci i procesora CPU, które będą używane podczas analizy.
W związku z tym istnieje kilka założeń domyślne, które składają się o kształt projektu:

- `package.json` i `bower.json` listę zależności, używany w projekcie i domyślnie są uwzględnione w pozyskiwania typu automatyczne (ATA)
- Najwyższego poziomu `node_modules` folder zawiera kod źródłowy biblioteki i jego zawartość zostaną wykluczone z kontekstem projektu domyślnie
- Co drugi `.js`, `.jsx`, `.ts`, i `.tsx` pliku jest prawdopodobnie jednym z *własne* pliki źródłowe i muszą być zawarte w kontekście projektu

W większości przypadków można po prostu Otwórz swój projekt i spełni przy użyciu domyślnej konfiguracji projektu. Jednak w projektach, które mają duży lub ma inny folder struktury, może być pożądane, aby kontynuować konfigurowanie usługi języka, które mogą skoncentrować się tylko na plikach źródłowych.

### <a name="override-defaults"></a>Zastąp wartości domyślne

Można zastąpić domyślną konfigurację, dodając `tsconfig.json` plik do katalogu głównego projektu.
Element `tsconfig.json` ma kilka różnych opcji, które można manipulować kontekst projektu.
Niektóre z nich wymieniono poniżej, ale aby uzyskać pełny zestaw wszystkich dostępnych opcjach [wyświetlić schemat przechowywania](http://json.schemastore.org/tsconfig).

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

Podane projektu przy użyciu następujących ustawień:

- pliki źródłowe projektu znajdują się w `wwwroot/js`
- pliki biblioteki projektu znajdują się w `wwwroot/lib`
- `bootstrap`, `jquery`, `jquery-validation`, i `jquery-validation-unobtrusive` są wymienione w `bower.json`
- `kendo-ui` ręcznie został dodany do folderu biblioteki

![Struktura folderów](../javascript/media/js-folderstructure.png)

Można użyć następującego `tsconfig.json` aby upewnić się, że język usługi analizuje tylko plików źródłowych w `js` folder, ale pobiera i używa `.d.ts` plików do biblioteki w sieci `lib` folderu.

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Rozwiązywanie problemów z usługa języka JavaScript została wyłączona dla następujących projektów
Po otwarciu projektu w języku JavaScript, który ma bardzo dużą ilość zawartości, możesz otrzymać komunikat "Usługa języka JavaScript została wyłączona dla następujących projektów". Najbardziej typową przyczyną występowania bardzo dużą ilość źródłowy JavaScript wynika z tym bibliotek z kodem źródłowym, która przekracza limit projektu o rozmiarze 20 MB.

Prosty sposób na optymalizację projektu jest dodanie `tsconfig.json` pliku w katalogu głównym projektu aby umożliwić usługa językowa wiedzieć, które pliki są bezpiecznie zignorować. Użyj poniższego przykładu aby wykluczać katalogi najczęściej, gdzie są przechowywane biblioteki:

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

Dodaj więcej katalogi, zgodnie z potrzebami. Niektóre inne przykłady katalogi "dostawca" lub "wwwroot/lib".

> [!NOTE]
> Właściwość kompilatora `disableSizeLimit` można również wyłączyć limit wyboru o rozmiarze 20 MB. Należy zachować środki ostrożności, specjalne, gdy za pomocą tej właściwości, ponieważ wyłączenie limit może ulec awarii usługi języka.

## <a name="notable-changes-from-visual-studio-2015"></a>Znaczące zmiany z programu Visual Studio 2015

Jako [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] funkcji całkowicie nową usługę językową, istnieje kilka zachowań, które będą różnić się lub Brak z poprzednich doświadczeń.
Najbardziej znaczące zmiany są zastąpienia VSDoc z JSDoc, usunięcie niestandardowego `.intellisense.js` rozszerzenia i ograniczone IntelliSense pod kątem wzorców określonego kodu.

### <a name="no-more-references-or-referencesjs"></a>Nie ma więcej `///<references/>` lub `_references.js`

Wcześniej był dość skomplikowane zrozumieć, w danej chwili, które pliki zostały w zakresie Twoich obowiązków IntelliSense. Czasami zostało wskazane w zakresie oraz innych przypadków, gdy nie wszystkie pliki i doprowadziło to do złożonych konfiguracji obejmujących odwołanie do ręcznego zarządzania. Idąc dalej, nie trzeba myśleć o zarządzaniu odwołania, a więc nie trzeba Potrójna kreska ułamkowa odwołuje się komentarze lub `_references.js` plików.

Zobacz [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) strony, aby uzyskać więcej informacji o sposobie działania funkcji IntelliSense.

### <a name="vsdoc"></a>VSDoc

Komentarze dokumentacji XML, czasami nazywane VSDocs, wcześniej może służyć do dekorowania kodu źródłowego za dodatkowe dane, które będzie służyć do pasjonatem wyniki funkcji IntelliSense.
VSDoc nie jest już obsługiwana zastąpiona ceną [JSDoc](http://usejsdoc.org/about-getting-started.html) co jest łatwiejsze do zapisu i zaakceptowane standard dla języka JavaScript.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Rozszerzenia

Wcześniej, można utworzyć [rozszerzenia IntelliSense](https://msdn.microsoft.com/library/hh874692.aspx) pozwoliłoby można dodać niestandardowe uzupełniania wyniki dla bibliotek innych firm.
Te rozszerzenia są dość trudny do zapisu i instalowania i odwoływanie się do nich był obciążeniem, więc przyszłości Nowa usługa języka nie obsługuje tych plików.
Jako alternatywę łatwiej, można napisać pliku definicji TypeScript w celu udostępnienia tych samych korzyści IntelliSense, jak stary `.intellisense.js` rozszerzenia.
Dowiedz się więcej na temat deklaracji (`.d.ts`) opracowywania pliku [tutaj](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nieobsługiwana wzorców

Ponieważ nowa usługa języka jest obsługiwana przez analizy statycznej, a nie jako aparatu wykonywania (odczyt [ten problem](https://github.com/Microsoft/TypeScript/issues/4789) informacji o różnicach), istnieje kilka wzorców JavaScript, które już nie może zostać wykryte.
Najczęstszym wzorcem jest wzorzec "expando".
Obecnie usługa języka nie może dostarczyć IntelliSense dla obiektów, które mają właściwości kumulowany po deklaracji.
Na przykład:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Aby uzyskać obejścia tego problemu, należy deklarowanie właściwości podczas tworzenia obiektu:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Możesz również dodać komentarzy JSDoc w następujący sposób:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
