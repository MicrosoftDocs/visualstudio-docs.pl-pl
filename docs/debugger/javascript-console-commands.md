---
title: Polecenia konsoli języka JavaScript | Microsoft Docs
description: Użyj poleceń do wysyłania komunikatów i wykonywania innych zadań w oknie konsoli JavaScript. Ten artykuł ma zastosowanie do Node.js aplikacji, aplikacji platformy UWP i aplikacji Apache Cordova.
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- uwp
- cordova
ms.openlocfilehash: d874b2831d906a42856e71d42dac6df1a1fe8d6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906382"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Polecenia konsoli języka JavaScript w programie Visual Studio

Polecenia służą do wysyłania komunikatów i wykonywania innych zadań w oknie konsoli JavaScript programu Visual Studio. Aby zapoznać się z przykładami pokazującymi, jak korzystać z tego okna, zobacz [Szybki Start: debugowanie JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true). Informacje przedstawione w tym temacie dotyczą Node.js aplikacji, aplikacji platformy UWP i aplikacji utworzonych przy użyciu Visual Studio Tools dla Apache Cordova.

Jeśli okno konsoli JavaScript jest zamknięte, można je otworzyć podczas debugowania w programie Visual Studio, wybierając **Debuguj**  >    >  **konsolę JavaScript** systemu Windows.

> [!NOTE]
> Jeśli okno nie jest dostępne podczas sesji debugowania, upewnij się, że typ debugera jest ustawiony na **skrypt** we właściwościach debugowania dla projektu.

Aby uzyskać informacje na temat korzystania z konsoli programu w narzędziach deweloperskich Microsoft Edge, zobacz [ten temat](/microsoft-edge/devtools-guide).

## <a name="console-object-commands"></a>polecenia obiektu konsoli

W tej tabeli przedstawiono składnię `console` poleceń obiektów, których można użyć w oknie konsoli JavaScript, lub można użyć do wysyłania komunikatów do konsoli programu z kodu. Ten obiekt zawiera wiele formularzy umożliwiających rozróżnienie komunikatów informacyjnych i komunikatów o błędach, jeśli chcesz.

Możesz użyć dłuższego formularza polecenia, `window.console.[command]` Aby uniknąć ewentualnych pomyłek z obiektami lokalnymi o nazwie konsola.

> [!TIP]
> Starsze wersje programu Visual Studio nie obsługują pełnego zestawu poleceń. Użyj funkcji IntelliSense w obiekcie konsoli, aby uzyskać szybkie informacje o obsługiwanych poleceniach.

|Polecenie|Opis|Przykład|
|-------------|-----------------|-------------|
|`assert(expression, message)`|Wysyła komunikat, jeśli `expression` ma wartość **false**.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|Czyści komunikaty z okna konsoli, w tym komunikaty o błędach skryptu, a także czyści skrypt wyświetlany w oknie konsoli. Nie czyści skryptu wprowadzonego w monicie wejściowym konsoli.|`console.clear();`|
|`count(title)`|Wysyła liczbę przypadków wywołania polecenia Count do okna konsoli. Każde wywołanie metody Count jest jednoznacznie identyfikowane przez opcjonalny `title` .<br /><br /> Istniejący wpis w oknie konsoli jest identyfikowany przez `title` parametr (jeśli istnieje) i aktualizowany przez polecenie Count. Nowy wpis nie został utworzony.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|Wysyła `message` do okna konsoli.<br /><br /> To polecenie jest identyczne z konsolą. log.<br /><br /> Obiekty, które są przesyłane za pomocą polecenia, są konwertowane na wartość typu String.|`console.debug("logging message");`|
|`dir(object)`|Wysyła określony obiekt do okna konsoli i wyświetla go w wizualizatorze obiektów. Możesz użyć wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`console.dir(obj);`|
|`dirxml(object)`|Wysyła określony węzeł XML `object` do okna konsoli i wyświetla go jako drzewo węzłów XML.|`console.dirxaml(xmlNode);`|
|`error(message)`|Wysyła `message` do okna konsoli. Tekst komunikatu jest czerwony i poprzedzony symbolem błędu.<br /><br /> Obiekty, które są przesyłane za pomocą polecenia, są konwertowane na wartość typu String.|`console.error("error message");`|
|`group(title)`|Uruchamia grupowanie komunikatów wysyłanych do okna konsoli i wysyła opcjonalną `title` etykietę jako grupę. Grupy mogą być zagnieżdżane i wyświetlane w widoku drzewa w oknie konsoli.<br /><br /> Polecenia Group * mogą ułatwić wyświetlanie danych wyjściowych okna konsoli w niektórych scenariuszach, na przykład gdy model składników jest używany.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|Uruchamia grupowanie komunikatów wysyłanych do okna konsoli i wysyła opcjonalną `title` etykietę jako grupę. Grupy, które są wysyłane przy użyciu, `groupCollapsed` są domyślnie wyświetlane w zwiniętym widoku. Grupy mogą być zagnieżdżane i wyświetlane w widoku drzewa w oknie konsoli.|Użycie jest takie samo jak `group` polecenie.<br /><br /> Zobacz przykład dla `group` polecenia.|
|`groupEnd()`|Zamyka bieżącą grupę.<br /><br /> Wymagania:<br /><br /> Visual Studio 2013|Zobacz przykład dla `group` polecenia.|
|`info(message)`|Wysyła `message` do okna konsoli. Komunikat jest poprzedzony symbolem informacyjnym.|`console.info("info message");`<br /><br /> Aby uzyskać więcej przykładów, zobacz [Formatowanie konsoli. log dane wyjściowe](#ConsoleLog) w dalszej części tego tematu.|
|`log(message)`|Wysyła `message` do okna konsoli.<br /><br /> W przypadku przekazania obiektu to polecenie wysyła ten obiekt do okna konsoli i wyświetla go w wizualizatorze obiektów. Możesz użyć wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|Używany w aplikacjach sieci Web. Nieobsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|
|`profile(reportName)`|Używany w aplikacjach sieci Web. Nieobsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|
|`profileEnd()`|Używany w aplikacjach sieci Web. Nieobsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|
|`select(element)`|Wybiera określony kod HTML `element` w [dom Explorer](../debugger/quickstart-debug-html-and-css.md).|Console. Select (element);|
|`time (name)`|Uruchamia czasomierz, który jest identyfikowany przez opcjonalny `name` parametr. Gdy jest używany z `console.timeEnd` , oblicza czas upływający między `time` i i `timeEnd` wysyła wynik (mierzoną w MS) do konsoli przy użyciu `name` ciągu jako prefiksu. Służy do włączania Instrumentacji kodu aplikacji na potrzeby mierzenia wydajności.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|Wyłącza czasomierz identyfikowany przez opcjonalny `name` parametr. Zobacz `time` polecenie konsoli.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|Wysyła ślad stosu do okna konsoli. Ślad zawiera kompletny stos wywołań i zawiera informacje, takie jak nazwa pliku, numer wiersza i numer kolumny.|`console.trace();`|
|`warn(message)`|Wysyła `message` do okna konsoli, poprzedzone symbolem ostrzegawczym.<br /><br /> Obiekty, które są przesyłane za pomocą polecenia, są konwertowane na wartość typu String.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>Różne polecenia
Te polecenia są również dostępne w oknie konsoli JavaScript (nie są dostępne w kodzie).

|Polecenie|Opis|Przykład|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|Zwraca określony element do okna konsoli. `$0` Zwraca element aktualnie wybrany w DOM Explorer, `$1` zwraca element poprzednio wybrany w Dom Explorer i tak dalej, do czwartego poprzednio zaznaczonego elementu.|$3|
|`$(id)`|Zwraca element o IDENTYFIKATORze. Jest to polecenie skrótu dla `document.getElementById(id)` , gdzie `id` to ciąg, który reprezentuje identyfikator elementu.|`$("contenthost")`|
|`$$(selector)`|Zwraca tablicę elementów, które pasują do określonego selektora przy użyciu składni selektora CSS. To jest polecenie skrótu dla `document.querySelectorAll()` .|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|Umożliwia zmianę kontekstu oceny wyrażenia z domyślnego okna najwyższego poziomu strony do okna określonej ramki. Wywołanie `cd()` bez parametrów zwraca kontekst do okna najwyższego poziomu.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|Wybiera określony element w [dom Explorer](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|Zwraca wizualizator dla określonego obiektu. Możesz użyć wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>Sprawdzanie, czy istnieje polecenie konsoli
Możesz sprawdzić, czy określone polecenie istnieje przed podjęciem próby jego użycia. Ten przykład sprawdza obecność `console.log` polecenia. Jeśli `console.log` istnieje, kod wywołuje go.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>Badanie obiektów w oknie konsoli JavaScript
Można korzystać z dowolnego obiektu, który znajduje się w zakresie w przypadku korzystania z okna konsoli JavaScript. Aby sprawdzić obiekt poza zakresem w oknie konsoli, użyj `console.log` , `console.dir` lub innych poleceń w kodzie. Alternatywnie można korzystać z obiektu z okna konsoli, gdy jest on w zakresie przez ustawienie punktu przerwania w kodzie (punkt przerwania  >  **wstawiania** punktu przerwania).

## <a name="formatting-consolelog-output"></a><a name="ConsoleLog"></a> Formatowanie danych wyjściowych konsoli. log
W przypadku przekazania wielu argumentów do `console.log` , konsola będzie traktować argumenty jako tablicę i połączyć dane wyjściowe.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log` obsługuje również wzorce podstawiania "printf" do formatowania danych wyjściowych. Jeśli używasz wzorców podstawiania w pierwszym argumencie, dodatkowe argumenty zostaną użyte do zastąpienia określonych wzorców w kolejności, w jakiej są używane.

 Obsługiwane są następujące wzorce podstawiania:

- % s-String% i-Integer% d-Integer% f-float% o-Object% b-Binary% x-szesnastkowo% e-wykładnik

  Poniżej przedstawiono kilka przykładów użycia wzorców podstawiania w programie `console.log` :

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";
user.age = 10.01;
console.log("Hi, %s %s!", user.first, user.last);
console.log("%s is %i years old!", user.first, user.age);
console.log("%s is %f years old!", user.first, user.age);

// Output:
// Hi, Fred Smith!
// Fred is 10 years old!
// Fred is 10.01 years old!
```

## <a name="see-also"></a>Zobacz też
- [Szybki start: debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017&preserve-view=true)
- [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md?view=vs-2017&preserve-view=true)
