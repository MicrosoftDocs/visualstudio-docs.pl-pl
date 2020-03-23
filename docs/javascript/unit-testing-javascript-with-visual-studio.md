---
title: Testowanie jednostek JavaScript i TypeScript
description: Program Visual Studio zapewnia jednostkę pomocy technicznej testującą kod JavaScript i TypeScript przy użyciu narzędzia Node.js dla programu Visual Studio
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
ms.openlocfilehash: 792c74a3b5da5ed6528fa3919a0c60625d1a38ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77071950"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testowanie jednostek JavaScript i TypeScript w programie Visual Studio

Node.js Tools for Visual Studio umożliwiają pisanie i uruchamianie testów jednostkowych przy użyciu niektórych bardziej popularnych struktur JavaScript bez konieczności przełączania się do wiersza polecenia.

Obsługiwane ramy to:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jaśmin ([Jasmine.github.io](https://jasmine.github.io/))
* Taśma[(github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Moduł eksportu (ta struktura jest specyficzna dla node.js Tools for Visual Studio)

> [!WARNING]
> Problem w taśmie obecnie uniemożliwia testy taśmy z systemem. Jeśli [#361 PR](https://github.com/substack/tape/pull/361) zostanie scalona, problem powinien zostać rozwiązany.

Jeśli twoja ulubiona struktura nie jest obsługiwana, zobacz [Dodawanie pomocy technicznej dla struktury testów jednostkowych, aby](#addingFramework) uzyskać informacje na temat dodawania pomocy technicznej.

## <a name="write-unit-tests"></a>Zapis testów jednostkowych

Przed dodaniem testów jednostkowych do projektu upewnij się, że struktura, której zamierzasz użyć, jest zainstalowana lokalnie w projekcie. Jest to łatwe do zrobienia za pomocą [okna instalacji pakietu npm](npm-package-management.md#npmInstallWindow).

Preferowanym sposobem dodawania testów jednostkowych do projektu jest utworzenie folderu *testów* w projekcie i ustawienie go jako głównego testu we właściwościach projektu. Należy również wybrać strukturę testów, które chcesz użyć.

![Ustawianie katalogu głównego i struktury testowej](../javascript/media/unit-test-project-properties.png)

Za pomocą okna dialogowego **Dodawanie nowego elementu** można dodawać proste puste testy. Zarówno JavaScript, jak i TypeScript są obsługiwane w tym samym projekcie.

![Dodaj nowy test jednostkowy](../javascript/media/unit-test-add-new-item.png)

W przypadku testu jednostkowego Mocha użyj następującego kodu:

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

Jeśli nie ustawiono opcji testu jednostkowego we właściwościach projektu, należy upewnić się, że właściwość **Test Framework** w oknie **Właściwości** jest ustawiona na poprawną strukturę testów dla plików testów jednostkowych. Odbywa się to automatycznie przez szablony plików testowych jednostki.

![Struktura testów](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Opcje testu jednostkowego będą miały pierwszeństwo przed ustawieniami dla poszczególnych plików.

Po otwarciu Eksploratora testów (wybierz > **Eksploratora** **Test** > testów**systemu**Windows) program Visual Studio odnajduje i wyświetla testy. Jeśli testy nie są wyświetlane początkowo, a następnie odbudować projekt, aby odświeżyć listę.

![Eksplorator testów](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Nie należy `outdir` używać `outfile` opcji lub opcji w *pliku tsconfig.json,* ponieważ Eksplorator testów nie będzie mógł znaleźć testów jednostkowych w plikach TypeScript.

## <a name="run-tests"></a>Uruchom testy

Testy można uruchamiać w programie Visual Studio 2017 lub z wiersza polecenia.

### <a name="run-tests-in-visual-studio-2017"></a>Uruchamianie testów w programie Visual Studio 2017

Testy można uruchomić, klikając łącze **Uruchom wszystko** w Eksploratorze testów. Można też uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając **polecenie Uruchom wybrane testy** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i pokazuje wyniki. Ponadto można również debugować wybrane testy, wybierając **opcję Debugowanie wybranych testów**.

> [!Warning]
> Debugowanie testów jednostkowych przy użyciu węzła 8+ obecnie działa tylko dla plików testowych JavaScript, pliki testowe TypeScript nie trafią w punkty przerwania. Aby obejść ten `debugger` problem, użyj słowa kluczowego.

> [!NOTE]
> Obecnie nie obsługujemy testów profilowania ani pokrycia kodu.

### <a name="run-tests-from-the-command-line"></a>Uruchamianie testów z poziomu wiersza polecenia

Testy można uruchomić w [wierszu polecenia dewelopera](/dotnet/framework/tools/developer-command-prompt-for-vs) dla programu Visual Studio 2017 za pomocą następującego polecenia:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

To polecenie pokazuje dane wyjściowe podobne do następujących:

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
> Jeśli pojawi się błąd wskazujący, że nie można odnaleźć *pliku vstest.console.exe,* upewnij się, że otwarto wiersz polecenia dewelopera, a nie zwykły wiersz polecenia.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Dodawanie obsługi struktury testów jednostkowych

Można dodać obsługę dodatkowych struktur testowych, implementując logikę odnajdywania i wykonywania przy użyciu języka JavaScript. Można to zrobić, dodając folder o nazwie struktury testowej w obszarze:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Ten folder musi zawierać plik JavaScript o tej samej nazwie, który eksportuje następujące dwie funkcje:

* `find_tests`
* `run_tests`

Na dobre przykład `find_tests` i `run_tests` implementacje, zobacz implementacji dla struktury testowania jednostek Mocha w:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Odnajdowanie dostępnych struktur testowych odbywa się w programie Visual Studio start. Jeśli struktura zostanie dodana, gdy program Visual Studio jest uruchomiony, uruchom ponownie program Visual Studio, aby wykryć strukturę. Jednak nie trzeba ponownie uruchomić podczas wprowadzania zmian w implementacji.

## <a name="unit-tests-in-other-project-types"></a>Testy jednostkowe w innych typach projektów
Nie są ograniczone do pisania testów jednostkowych tylko w projektach Node.js. Po dodaniu TestFramework i TestRoot właściwości do dowolnego projektu C# lub Visual Basic, te testy zostaną wyliczone i można je uruchomić za pomocą okna Eksploratora testów.

Aby to włączyć, kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań, wybierz pozycję **Zwolnij projekt**, a następnie wybierz polecenie **Edytuj projekt**. Następnie w pliku projektu dodaj następujące dwa elementy do grupy właściwości.

> [!NOTE]
> Upewnij się, że grupa właściwości, do której dodajesz elementy, nie ma określonego warunku.
> Może to spowodować nieoczekiwane zachowanie.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Następnie dodaj testy do określonego folderu głównego testu, a będą one dostępne do uruchomienia w oknie Eksploratora testów. Jeśli początkowo się nie pojawiają, może być konieczne odbudowanie projektu.

### <a name="unit-test-net-core-and-net-standard"></a>Test jednostkowy .NET Core i .NET Standard
Oprócz powyższych właściwości należy również zainstalować pakiet NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) i ustawić właściwość:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Niektóre struktury testowe mogą wymagać dodatkowych pakietów npm do wykrywania testów. Na przykład jest wymaga pakietu npm jest-editor-support. W razie potrzeby sprawdź dokumentację dla określonych ram.
