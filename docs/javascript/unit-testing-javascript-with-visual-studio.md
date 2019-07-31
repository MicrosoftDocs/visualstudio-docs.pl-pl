---
title: Testowanie jednostkowe JavaScript i TypeScript
description: Program Visual Studio zapewnia obsługę testów jednostkowych w języku JavaScript i kodzie TypeScript przy użyciu narzędzi Node. js dla programu Visual Studio
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 263d2eb93c3ad78e14a066fe11486be9122cfd96
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681303"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testowanie jednostkowe JavaScript i TypeScript w programie Visual Studio

Narzędzia Node. js Tools for Visual Studio umożliwiają pisanie i uruchamianie testów jednostkowych przy użyciu niektórych popularnych platform języka JavaScript bez konieczności przełączania się do wiersza polecenia.

Obsługiwane są następujące platformy:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Taśmy ([github.com/substack/tape](https://github.com/substack/tape))
* On ([jestjs.IO](https://jestjs.io/))
* Eksportuj moduł uruchamiający (Platforma ta jest specyficzna dla narzędzi Node. js dla programu Visual Studio)

> [!WARNING]
> Problem na taśmie uniemożliwia uruchomienie testów taśmowych. W przypadku scalania [#361](https://github.com/substack/tape/pull/361) żądania ściągnięcia należy rozwiązać problem.

Jeśli Twoja ulubiona platforma nie jest obsługiwana, zobacz [Dodawanie obsługi dla struktury testów jednostkowych](#addingFramework) , aby uzyskać informacje na temat dodawania obsługi.

## <a name="write-unit-tests"></a>Zapisz testy jednostkowe

Przed dodaniem testów jednostkowych do projektu upewnij się, że struktura, którą planujesz użyć, jest zainstalowana lokalnie w projekcie. Można to łatwo zrobić przy użyciu [okna instalacji pakietu npm](npm-package-management.md#npmInstallWindow).

Preferowanym sposobem dodawania testów jednostkowych do projektu jest utworzenie folderu Tests w projekcie i ustawienie tego jako elementu głównego testu we właściwościach projektu. Należy również wybrać platformę testową, która ma być używana.

![Ustawianie testów głównych i testów](../javascript/media/unit-test-project-properties.png)

Można dodać proste puste testy do projektu przy użyciu okna dialogowego **Dodaj nowy element** . Kod JavaScript i TypeScript są obsługiwane w tym samym projekcie.

![Dodaj nowy test jednostkowy](../javascript/media/unit-test-add-new-item.png)

W przypadku testu jednostkowego środowiska Mocha należy użyć następującego kodu:

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

Jeśli nie ustawisz opcji testów jednostkowych we właściwościach projektu, musisz upewnić się, że właściwość **Framework testów** w oknie **Właściwości** jest ustawiona na poprawną strukturę testową dla plików testów jednostkowych. Jest to wykonywane automatycznie przez szablony plików testów jednostkowych.

![Struktury testowej](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Opcje testów jednostkowych będą mieć preferencję dotyczącą ustawień poszczególnych plików.

Po otwarciu Eksploratora testów (wybierz **testu** > **Windows** > **Eksplorator testów**), Visual Studio wykrywa i wyświetla testów. Jeśli testy nie są początkowo wyświetlane, ponownie skompiluj projekt, aby odświeżyć listę.

![Eksplorator testów](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Nie używaj `outdir` opcji or `outfile` w *tsconfig. JSON*, ponieważ Eksplorator testów nie będzie w stanie znaleźć testów jednostkowych w plikach TypeScript.

## <a name="run-tests"></a>Uruchom testy

Testy można uruchamiać w programie Visual Studio 2017 lub w wierszu polecenia.

### <a name="run-tests-in-visual-studio-2017"></a>Uruchamianie testów w programie Visual Studio 2017

Testy można uruchomić, klikając link **Uruchom wszystkie** w Eksploratorze testów. Lub można uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając polecenie **Uruchom wybrane testy** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i wyświetla wyniki. Ponadto można debugować wybrane testy, wybierając **Debuguj wybrane testy**.

> [!Warning]
> Debugowanie testów jednostkowych za pomocą węzła 8 + obecnie działa tylko w przypadku plików testowych języka JavaScript, pliki testowe TypeScript nie trafią na punkty przerwania. Aby obejść ten `debugger` element, użyj słowa kluczowego.

> [!NOTE]
> Obecnie nie obsługujemy testów profilowania ani pokrycia kodu.

### <a name="run-tests-from-the-command-line"></a>Uruchamianie testów z poziomu wiersza polecenia

Testy można uruchomić z [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) dla programu Visual Studio 2017 przy użyciu następującego polecenia:

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
> Jeśli zostanie wyświetlony komunikat o błędzie informujący o tym, że nie można znaleźć pliku *VSTest. Console. exe* , upewnij się, że otwarto wiersz polecenia dla deweloperów, a nie zwykły wiersz polecenia.

## <a name="addingFramework"></a>Dodawanie obsługi dla struktury testów jednostkowych

Można dodać obsługę dodatkowych platform testowych przez implementację logiki odnajdywania i wykonywania przy użyciu języka JavaScript. Można to zrobić przez dodanie folderu o nazwie struktury testowej w:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Ten folder musi zawierać plik JavaScript o tej samej nazwie, który eksportuje następujące dwie funkcje:

* `find_tests`
* `run_tests`

Aby zapoznać się z dobrymi `find_tests` przykładami `run_tests` i implementacjami, zobacz implementację struktury testów jednostkowych środowiska Mocha w:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Odnajdywanie dostępnych platform testowych odbywa się po rozpoczęciu programu Visual Studio. Jeśli po uruchomieniu programu Visual Studio zostanie dodana struktura, uruchom ponownie program Visual Studio, aby wykryć strukturę. Nie trzeba jednak ponownie uruchamiać w przypadku wprowadzania zmian w implementacji.

## <a name="unit-tests-in-other-project-types"></a>Testy jednostkowe w innych typach projektów
Nie można pisać testów jednostkowych tylko w projektach środowiska Node. js. Po dodaniu właściwości TestFramework i TestRoot do projektu dowolnego C# lub Visual Basic, te testy zostaną wyliczone i można uruchomić je przy użyciu okna Eksplorator testów.

Aby włączyć tę funkcję, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, wybierz polecenie **Zwolnij projekt**, a następnie wybierz polecenie **Edytuj projekt**. Następnie w pliku projektu Dodaj następujące dwa elementy do grupy właściwości.

> [!NOTE]
> Upewnij się, że grupa właściwości, do której dodawane są elementy, nie ma określonego warunku.
> Może to spowodować nieoczekiwane zachowanie.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Następnie Dodaj testy do podanego głównego folderu testowego i będą one dostępne do uruchomienia w oknie Eksplorator testów. Jeśli nie pojawią się na początku, może być konieczne ponowne skompilowanie projektu.

> [!NOTE]
> Obecnie nie działa to w przypadku projektów .NET Standard i .NET Core.
