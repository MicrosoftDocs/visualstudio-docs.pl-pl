---
title: Polecenia konsoli JavaScript | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 07/17/2017
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
- cordova
ms.openlocfilehash: bf9f339283af27f450950d9a79079ea35c97e3b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941468"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Polecenia konsoli JavaScript w programie Visual Studio
  
 Polecenia umożliwiają wysyłanie komunikatów oraz wykonywania innych zadań w oknie konsoli JavaScript programu Visual Studio. Przykłady pokazujące, jak używać tego okna, zobacz [Szybki Start: Debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md). Informacje przedstawione w tym temacie mają zastosowanie do aplikacji platformy uniwersalnej systemu Windows i aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova. Aby uzyskać informacje na temat obsługiwanych konsoli poleceń w aplikacji Cordova, zobacz [Debug Your App](https://taco.visualstudio.com/en-us/docs/debug-using-visual-studio/). Aby uzyskać informacje na temat korzystania z konsoli w programie Internet Explorer F12 tools, zobacz [w tym temacie](/previous-versions/windows/internet-explorer/ie-developer/samples/dn255006(v=vs.85)).  
  
 Jeśli nastąpi zamknięcie okna konsoli języka JavaScript, możesz go otworzyć podczas debugowania w programie Visual Studio, wybierając **debugowania** > **Windows** > **języka JavaScript Konsola**.  
  
> [!NOTE]
>  Jeśli okno nie jest dostępne podczas sesji debugowania, upewnij się, że typ debugera jest ustawiona na **skryptu** właściwości debugowania projektu.  
  
## <a name="console-object-commands"></a>Konsola obiektu polecenia  
 W poniższej tabeli przedstawiono składnię `console` obiekt polecenia, można użyć w oknie konsoli języka JavaScript lub służącego do wysyłania komunikatów do konsoli w kodzie. Ten obiekt udostępnia wiele form tak, aby rozróżnić komunikaty informacyjne i komunikaty o błędach, jeśli chcesz.  
  
 Można użyć dłużej formy polecenia `window.console.[command]` Jeśli potrzebujesz uniknąć możliwa pomyłka z lokalnych obiektów o nazwie konsoli.  
  
> [!TIP]
>  Starsze wersje programu Visual Studio nie obsługują kompletny zestaw poleceń. Użyj funkcji IntelliSense w obiekcie konsoli, aby pobrać skróconych informacji o obsługiwanych poleceniach.  
  
|Polecenie|Opis|Przykład|  
|-------------|-----------------|-------------|  
|`assert(expression, message)`|Wysyła komunikat, jeżeli `expression` daje w wyniku **false**.|`console.assert((x == 1), "assert message: x != 1");`|  
|`clear()`|Usuwa wiadomości z okna konsoli, w tym komunikaty o błędach skryptów, a także czyści skryptu, który pojawia się w oknie konsoli. Czyści skrypt, który wprowadzono w wierszu polecenia konsoli danych wejściowych.|`console.clear();`|  
|`count(title)`|Wysyła liczbę prób wywołano polecenie liczba w oknie konsoli. Każde wywołanie do zliczenia jest unikatowo identyfikowana przez opcjonalny `title`.<br /><br /> Istniejący wpis w oknie konsoli jest identyfikowane za pomocą `title` parametru (jeśli istnieje) i aktualizowane przez polecenie count. Nie zostanie utworzony nowy wpis.|`console.count();`<br /><br /> `console.count("inner loop");`|  
|`debug(message)`|Wysyła `message` w oknie konsoli.<br /><br /> To polecenie jest taka sama jak dziennika console.log.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.debug("logging message");`|  
|`dir(object)`|Wysyła określony obiekt do okna konsoli i wyświetla go w wizualizatorze obiektu. Korzystanie z wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`console.dir(obj);`|  
|`dirxml(object)`|Wysyła Podany węzeł XML `object` w oknie konsoli i wyświetla je jako węzeł drzewa XML.|`console.dirxaml(xmlNode);`|  
|`error(message)`|Wysyła `message` w oknie konsoli. Tekst komunikatu jest czerwonego i poprzedzone symbolem błędu.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.error("error message");`|  
|`group(title)`|Rozpoczyna się grupowanie komunikatów, które są wysyłane do okna konsoli, a następnie wysyła opcjonalnego `title` jako etykieta grupy. Grupy mogą być zagnieżdżane i są wyświetlane w widoku drzewa w oknie konsoli.<br /><br /> Polecenia grupy * może ułatwić wyświetlanie danych wyjściowych okna konsoli w niektórych scenariuszach, na przykład gdy model składników jest używana.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|  
|`groupCollapsed(title)`|Rozpoczyna się grupowanie komunikatów, które są wysyłane do okna konsoli, a następnie wysyła opcjonalnego `title` jako etykieta grupy. Grupy, które są wysyłane przy użyciu `groupCollapsed` domyślnie wyświetlana w widoku zwiniętym. Grupy mogą być zagnieżdżane i są wyświetlane w widoku drzewa w oknie konsoli.|Użycie jest taka sama jak `group` polecenia.<br /><br /> Zobacz przykład `group` polecenia.|  
|`groupEnd()`|Kończy bieżącą grupę.<br /><br /> Wymagania:<br /><br /> Visual Studio 2013|Zobacz przykład `group` polecenia.|  
|`info(message)`|Wysyła `message` w oknie konsoli. Komunikat jest poprzedzone symbolem informacji.|`console.info("info message");`<br /><br /> Aby uzyskać więcej przykładów, zobacz [formatowanie danych wyjściowych dziennika console.log](#ConsoleLog) w dalszej części tego tematu.|  
|`log(message)`|Wysyła `message` w oknie konsoli.<br /><br /> W przypadku przekazania obiektu to polecenie wysyła tego obiektu w oknie konsoli i wyświetla go w wizualizatorze obiektu. Korzystanie z wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`console.log("logging message");`|  
|`msIsIndependentlyComposed(element)`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`profile(reportName)`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`profileEnd()`|Używane w aplikacji sieci web. Nie są obsługiwane w aplikacjach platformy UWP przy użyciu języka JavaScript.|Nieobsługiwane.|  
|`select(element)`|Wybiera określony kod HTML `element` w [narzędzia DOM Explorer](../debugger/quickstart-debug-html-and-css.md).|console.select(element);|  
|`time (name)`|Uruchamia czasomierz, co jest identyfikowane za pomocą opcjonalnego `name` parametru. Gdy jest używane z `console.timeEnd`, oblicza czas, jaki upływa między `time` i `timeEnd`i wysyła wynik (mierzoną w ms) za pomocą konsoli `name` ciągu jako prefiksu. Używane w celu włączenia Instrumentacji kodu aplikacji do pomiaru wydajności.|`console.time("app start");  app.start();  console.timeEnd("app start");`|  
|`timeEnd(name)`|Zatrzymuje timer, która jest identyfikowane za pomocą opcjonalnego `name` parametru. Zobacz `time` polecenie konsoli.|`console.time("app start"); app.start(); console.timeEnd("app start");`|  
|`trace()`|Wysyła ślad stosu, w oknie konsoli. Śledzenie obejmuje pełny stos wywołań i zawiera informacje, takie jak nazwa pliku, numer wiersza i numer kolumny.|`console.trace();`|  
|`warn(message)`|Wysyła `message` w oknie konsoli poprzedzone symbolem ostrzeżenia.<br /><br /> Obiekty, które są przekazywane za pomocą polecenia są konwertowane na wartość ciągu.|`console.warn("warning message");`|  
  
## <a name="miscellaneous-commands"></a>Inne polecenia  
 Te polecenia są dostępne również w oknie konsoli języka JavaScript (nie są one dostępne z kodu).  
  
|Polecenie|Opis|Przykład|  
|-------------|-----------------|-------------|  
|`$0`, `$1`, `$2`, `$3`, `$4`|Zwraca określony element w oknie konsoli. `$0` Zwraca element aktualnie wybrane w Eksploratorze DOM `$1` zwraca element, który został wcześniej wybrane w Eksploratorze DOM i tak dalej, aż czwarty poprzednio wybranego elementu.|$3|  
|`$(id)`|Zwraca element według identyfikatora. To polecenie skrótu dla `document.getElementById(id)`, gdzie `id` jest ciągiem, który reprezentuje identyfikator elementu.|`$("contenthost")`|  
|`$$(selector)`|Zwraca tablicę elementy, które odpowiadają określony selektor za pomocą składni selektora CSS. To polecenie skrótu dla `document.querySelectorAll()`.|`$$(".itemlist")`|  
|`cd()`<br /><br /> `cd(window)`|Umożliwia zmianę kontekstu do obliczenia wyrażenia w oknie najwyższego poziomu domyślnej strony do okna ramki o określonym. Wywoływanie `cd()` bez parametrów zwraca kontekst do okna najwyższego poziomu.|`cd();`<br /><br /> `cd(myframe);`|  
|`select(element)`|Wybiera określony element w [narzędzia DOM Explorer](../debugger/quickstart-debug-html-and-css.md).|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|  
|`dir(object)`|Zwraca Wizualizator dla określonego obiektu. Korzystanie z wizualizatora, aby sprawdzić właściwości w oknie konsoli.|`dir(obj);`|  
  
## <a name="checking-whether-a-console-command-exists"></a>Sprawdzanie, czy istnieje polecenia konsoli  
 Możesz sprawdzić, czy określone polecenie istnieje przed podjęciem próby wykonania z niego korzystać. W tym przykładzie, sprawdza istnienie `console.log` polecenia. Jeśli `console.log` istnieje, kod wywołuje on.  
  
```javascript  
if (console && console.log) {  
    console.log("msg");  
}  
  
```  
  
## <a name="examining-objects-in-the-javascript-console-window"></a>Badanie obiektów w oknie konsoli języka JavaScript  
 Możesz porozmawiać z dowolnego obiektu, który znajduje się w zakresie, korzystając z okna konsoli JavaScript. Aby przeprowadzić inspekcję obiekt poza zakresem w oknie konsoli, należy użyć `console.log` , `console.dir`, lub innych poleceń w kodzie. Alternatywnie możesz porozmawiać z obiektu z okna konsoli jest w zakresie przez ustawienie punktu przerwania w kodzie (**punktu przerwania** > **Wstaw punkt przerwania**).  
  
##  <a name="ConsoleLog"></a> Formatowanie danych wyjściowych dziennika console.log  
 W przypadku przekazania wiele argumentów `console.log`, konsolę będzie traktować argumenty jako tablica i połącz dane wyjściowe.  
  
```javascript  
var user = new Object();  
user.first = "Fred";  
user.last = "Smith";  
  
console.log(user.first, user.last);  
// Output:  
// Fred Smith  
  
```  
  
 `console.log` obsługuje również wzorców podstawienia "printf", aby sformatować dane wyjściowe. Jeśli używasz wzorców podstawienia w pierwszym argumencie dodatkowe argumenty będzie służyć do zastąpienia określonego wzorce w kolejności, w której są one używane.  
  
 Obsługiwane są następujące wzorce podstawienia:  
  
- %s - ciąg  
   %i - liczba całkowita  
   %d - Liczba całkowita  
   %f - float  
   %o — obiekt  
   %b - binarne  
   %x - szesnastkowe  
   %e - wykładnika  
  
  Poniżej przedstawiono kilka przykładów użycia wzorce podstawienia w `console.log`:  
  
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
 [Szybki start: Debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)   
 [Szybki start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)