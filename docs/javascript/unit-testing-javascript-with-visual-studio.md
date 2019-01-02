---
title: Testowanie jednostek w środowisku Node.js
description: Program Visual Studio udostępnia obsługują kodu JavaScript przy użyciu narzędzia Node.js dla programu Visual Studio testy jednostkowe
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a65fc53f72e2e7a90b03f376ced55fffbe9ecbf8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952767"
---
# <a name="unit-testing-in-nodejs"></a>Testowanie jednostek w środowisku Node.js

Node.js Tools For Visual Studio umożliwiają pisanie i Uruchamianie testów jednostkowych przy użyciu niektórych bardziej popularnych platform JavaScript, bez potrzeby, aby przełączyć się do wiersza polecenia.

Obsługiwane platformy to:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Taśmy ([github.com/substack/tape](https://github.com/substack/tape))
* Eksportuj modułu uruchamiającego (Ta struktura jest specyficzne dla środowiska Node.js Tools for Visual Studio)

> [!WARNING]
> Problem w taśmy obecnie zapobiega testy taśmy uruchamianiu. Jeśli [361 # żądania Ściągnięcia](https://github.com/substack/tape/pull/361) scalone, powinien zostać rozwiązany.

Jeśli w swojej ulubionej platformy nie jest obsługiwana, zobacz [obsługę środowiska testów jednostkowych](#addingFramework) informacji dotyczących dodawania obsługi.

## <a name="write-unit-tests"></a>Pisanie testów jednostkowych

Przed dodaniem testy jednostkowe z projektem, upewnij się, że framework, której planujesz używać jest instalowana lokalnie w swoim projekcie. Jest to łatwo zrobić za pomocą [okna instalacji pakietu npm](npm-package-management.md#npmInstallWindow).

Preferowany sposób, aby dodać testy jednostkowe do projektu jest utworzenie *testy* folderu w projekcie i ustawienia, które co test główny we właściwościach projektu. Należy również wybrać ze środowiskiem testowym, którego chcesz użyć.

![Ustaw platformę testu głównego i testowania](../javascript/media/unit-test-project-properties.png)

Proste testy puste można dodać do swojego projektu za pomocą **Dodaj nowy element** okno dialogowe. Kod JavaScript i TypeScript są obsługiwane w tym samym projekcie.

![Dodaj nowy test jednostki](../javascript/media/unit-test-add-new-item.png)

Dla testu jednostkowego środowiska Mocha Użyj następującego kodu:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Jeśli nie został ustawiony jednostki opcji testowania we właściwościach projektu, upewnij się, **Test Framework** właściwości w **właściwości** okna ustawiono ze środowiskiem testowym poprawne dla pliki testów jednostkowych. Odbywa się to automatycznie przez Szablony plików testów jednostkowych.

![Struktury testowej](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Opcje testu jednostki przejmie preferencji ustawienia dla poszczególnych plików.

Po otwarciu Eksploratora testów (wybierz **testu** > **Windows** > **Eksplorator testów**), Visual Studio wykrywa i wyświetla testów. Jeśli testy nie są wyświetlane na początku, ponownie skompilować projekt, aby odświeżyć listę.

![Eksplorator testów](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Nie używaj `outdir` lub `outfile` opcji *tsconfig.json*, ponieważ Eksplorator testów nie będzie mógł odnaleźć testów jednostkowych w pliki TypeScript.

## <a name="run-tests"></a>Uruchom testy

W programie Visual Studio 2017 lub z wiersza polecenia, można uruchomić testy.

### <a name="run-tests-in-visual-studio-2017"></a>Uruchamianie testów w programie Visual Studio 2017

Testy można uruchomić, klikając **Uruchom wszystkie** link w Eksploratorze testów. Alternatywnie można uruchomić testy, wybierając jeden lub więcej testów lub grupy, kliknij prawym przyciskiem myszy i wybierając opcję **Uruchom wybrane testy** z menu skrótów. Testy są uruchamiane w tle, a następnie automatycznie aktualizuje Eksplorator testów, przedstawiono wyniki. Ponadto można również debugować wybranych testów, wybierając **Debuguj wybrane testy**.

> [!Warning]
> Debugowanie testów jednostkowych za pomocą środowiska Node 8 + działa obecnie tylko dla języka JavaScript pliki testów, nie będzie można identyfikować punkty przerwania testu plików TypeScript. Jako obejście należy użyć `debugger` — słowo kluczowe.

> [!NOTE]
> Obecnie nie obsługujemy testy profilowania lub pokrycia kodu.

### <a name="run-tests-from-the-command-line"></a>Uruchamianie testów z poziomu wiersza polecenia

Możesz uruchomić testy z [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) programu Visual Studio 2017 przy użyciu następującego polecenia:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

To polecenie wyświetla dane wyjściowe podobne do następujących:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Jeśli otrzymasz komunikat o błędzie informujący, że *vstest.console.exe* nie można znaleźć, upewnij się, został otwarty wiersz polecenia dla deweloperów i nie regularne wiersza polecenia.

## <a name="addingFramework"></a>Dodano obsługę środowiska testów jednostkowych

Możesz dodać obsługę środowisk testowych dodatkowe, implementując odkrywania i wykonywania logiki przy użyciu języka JavaScript. Możesz to zrobić, dodając folder o nazwie struktury testowej w obszarze:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Ten folder musi zawierać plik JavaScript o takiej samej nazwie, który eksportuje następujące dwie funkcje:

* `find_tests`
* `run_tests`

Na stałe, na przykład `find_tests` i `run_tests` implementacji, zobacz implementację dla testowania w jednostkowego środowiska Mocha:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Odnajdywanie struktur testowania występuje podczas uruchamiania programu Visual Studio. Jeśli struktura zostanie dodany po uruchomieniu programu Visual Studio, uruchom ponownie Visual Studio, aby wykryć platformę. Jednak nie trzeba ponownie uruchomić podczas wprowadzania zmian do wdrożenia.

## <a name="unit-tests-in-other-project-types"></a>Testy jednostkowe w innych typów projektów
Nie jest ograniczona do pisania testów jednostkowych w właśnie projektach środowiska Node.js. Po dodaniu właściwości TestFramework i TestRoot do dowolnego C# lub projekcie Visual Basic tych testów zostaną wyliczone i mogły być uruchamiane przy użyciu okna Eksploratora testów.

Aby je włączyć, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierz polecenie **Zwolnij projekt**, a następnie wybierz **edycji projektu**. Następnie w pliku projektu należy dodać następujące dwa elementy do grupy właściwości.

> [!NOTE]
> Upewnij się, że grupa właściwości, dodawanego elementy, aby nie jest określony warunek.
> Może to spowodować nieoczekiwane zachowanie.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Następnie dodaj testy do wskazanego folderu głównego testu i będą one dostępne do uruchamiania w oknie Eksploratora testów. Jeśli początkowo nie są wyświetlane, konieczne może być ponownie skompilować projekt.

> [!NOTE]
> To obecnie nie działa dla projektów .NET Standard i .NET Core.
