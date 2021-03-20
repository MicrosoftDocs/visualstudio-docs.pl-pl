---
title: Testowanie jednostkowe JavaScript i TypeScript
description: Program Visual Studio zapewnia obsługę testów jednostkowych w języku JavaScript i kodzie TypeScript przy użyciu narzędzi Node.js Tools for Visual Studio
ms.date: 03/18/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dc44e39223fd252ae8c4130a1b358aa6af981119
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671511"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testowanie jednostkowe JavaScript i TypeScript w programie Visual Studio

Możesz pisać i uruchamiać testy jednostkowe w programie Visual Studio przy użyciu niektórych popularnych platform języka JavaScript bez konieczności przełączania się do wiersza polecenia. Obsługiwane są zarówno projekty Node.js, jak i ASP.NET Core.

Obsługiwane są następujące platformy:
* Środowiska Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.IO](https://jasmine.github.io/))
* Taśma ([GitHub.com/Substack/Tape](https://github.com/substack/tape))
* On ([jestjs.IO](https://jestjs.io/))
* Eksportuj moduł uruchamiający (Platforma ta jest specyficzna dla Node.js narzędzi dla programu Visual Studio)

Aby uzyskać ASP.NET Core i JavaScript lub TypeScript, zobacz [pisanie testów jednostkowych dla ASP.NET Core ](#write-unit-tests-for-aspnet-core).

Jeśli Twoja ulubiona platforma nie jest obsługiwana, zobacz [Dodawanie obsługi dla struktury testów jednostkowych](#addingFramework) , aby uzyskać informacje na temat dodawania obsługi.

## <a name="write-unit-tests-in-a-nodejs-project"></a>Zapisz testy jednostkowe w projekcie Node.js

Przed dodaniem testów jednostkowych do projektu upewnij się, że struktura, którą planujesz użyć, jest zainstalowana lokalnie w projekcie. Można to łatwo zrobić przy użyciu [okna instalacji pakietu npm](npm-package-management.md#npmInstallWindow).

Preferowanym sposobem dodawania testów jednostkowych do projektu jest utworzenie folderu *Tests* w projekcie i ustawienie tego jako elementu głównego testu we właściwościach projektu. Należy również wybrać platformę testową, która ma być używana.

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

![Platforma testowa](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Opcje testów jednostkowych będą mieć preferencję dotyczącą ustawień poszczególnych plików.

Po otwarciu Eksploratora testów (wybierz **test**  >    >  **Eksplorator testów** systemu Windows) program Visual Studio odnajduje i wyświetla testy. Jeśli testy nie są początkowo wyświetlane, ponownie skompiluj projekt, aby odświeżyć listę.

![Eksplorator testów](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> W przypadku języka TypeScript nie używaj `outdir` opcji or `outfile` w *tsconfig.json*, ponieważ Eksplorator testów nie będzie w stanie znaleźć testów jednostkowych.

## <a name="run-tests-nodejs"></a>Uruchom testy (Node.js)

Testy można uruchamiać w programie Visual Studio lub w wierszu polecenia.

### <a name="run-tests-in-visual-studio"></a>Uruchamianie testów w programie Visual Studio

::: moniker range=">=vs-2019"
Testy można uruchomić, klikając link **Uruchom wszystkie** w Eksploratorze testów. Lub można uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając polecenie **Uruchom** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i wyświetla wyniki. Ponadto można debugować wybrane testy, klikając je prawym przyciskiem myszy i wybierając polecenie **Debuguj**.
::: moniker-end
::: moniker range="vs-2017"
Testy można uruchomić, klikając link **Uruchom wszystkie** w Eksploratorze testów. Lub można uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając polecenie **Uruchom wybrane testy** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i wyświetla wyniki. Ponadto można debugować wybrane testy, wybierając **Debuguj wybrane testy**.
::: moniker-end

W przypadku języka TypeScript testy jednostkowe są uruchamiane względem wygenerowanego kodu JavaScript.

> [!NOTE]
> W większości scenariuszy języka TypeScript można debugować test jednostkowy przez ustawienie punktu przerwania w kodzie TypeScript, kliknięcie prawym przyciskiem myszy w Eksploratorze testów i wybranie polecenia **Debuguj**. W bardziej złożonych scenariuszach, takich jak niektóre scenariusze korzystające z map źródła, może wystąpić problem, który sprawia, że punkty przerwania w kodzie TypeScript. Aby obejść ten sposób, spróbuj użyć `debugger` słowa kluczowego.

> [!NOTE]
> Obecnie nie obsługujemy testów profilowania ani pokrycia kodu.

### <a name="run-tests-from-the-command-line"></a>Uruchamianie testów z poziomu wiersza polecenia

Testy z [wiersz polecenia dla deweloperów dla programu Visual Studio](../ide/reference/command-prompt-powershell.md) można uruchomić przy użyciu następującego polecenia:

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
> Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że nie można odnaleźć *vstest.console.exe* , upewnij się, że otwarto wiersz polecenia dla deweloperów, a nie zwykły wiersz polecenia.

## <a name="write-unit-tests-for-aspnet-core"></a>Zapisz testy jednostkowe dla ASP.NET Core

1. Utwórz projekt ASP.NET Core i Dodaj obsługę języka TypeScript.

   Przykładowy projekt można znaleźć w temacie [Tworzenie aplikacji ASP.NET Core przy użyciu języka TypeScript](../javascript/tutorial-aspnet-with-typescript.md). W przypadku obsługi testowania jednostkowego zalecamy rozpoczęcie od standardowego szablonu projektu ASP.NET Core.

   Użyj pakietu NuGet, aby dodać obsługę języka TypeScript zamiast pakietu npm TypeScript.

1. Zainstaluj pakiet NuGet [Microsoft. JavaScript. testu jednostkowego](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zwolnij projekt**.

   Plik *. csproj* powinien zostać otwarty w programie Visual Studio.

1. Dodaj następujące elementy do pliku *. csproj* w `PropertyGroup` elemencie.

   Ten przykład określa środowiska Mocha jako platformę testową. Zamiast tego można określić za ich Jasmine.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot`Element określa, że testy jednostkowe będą znajdować się w folderze *Tests* katalogu głównego projektu.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Załaduj ponownie projekt**.

1. Dodaj obsługę npm, jak opisano w artykule Zarządzanie pakietami npm w obszarze [projekty ASP.NET Core](../javascript/npm-package-management.md#aspnet-core-projects).

   Wymaga to zainstalowania środowiska uruchomieniowego Node.js dla obsługi npm i dodania *package.jsw elemencie* głównym projektu.

1. W *package.jsna*, Dodaj pakiet npm, który ma być objęty zależnościami.

   Na przykład dla środowiska Mocha można użyć następujących:

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Niektóre struktury testów jednostkowych, takie jak npm, wymagają dodatkowych pakietów. W przypadku programu należy użyć następującego kodu JSON:

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > W niektórych scenariuszach Eksplorator rozwiązań nie może wyświetlić węzła npm z powodu znanego problemu opisanego [tutaj](https://github.com/aspnet/Tooling/issues/479). Jeśli musisz zobaczyć węzeł npm, możesz zwolnić projekt (kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**), a następnie ponownie Załaduj projekt, aby ponownie wyświetlić węzeł npm.

1. Dodaj kod do testu.

   Jeśli używasz przykładu opisanego w temacie [Create a ASP.NET Core app with TypeScript](tutorial-aspnet-with-typescript.md), Dodaj następujący kod na końcu pliku *Library. TS* , który znajduje się w folderze *scripts* .

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   W przypadku języka TypeScript testy jednostkowe są uruchamiane względem wygenerowanego kodu JavaScript.

1. Dodaj testy jednostkowe do folderu *Tests* w katalogu głównym projektu.

   Na przykład można użyć poniższego kodu, wybierając poprawną kartę dokumentacji, która pasuje do struktury testowej, w tym przykładzie środowiska Mocha lub. Ten kod testuje funkcję o nazwie `getData` .

   # <a name="mocha"></a>[Środowiska Mocha](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[Rejestr](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. Otwórz Eksploratora testów (wybierz **test**  >    >  **Eksplorator testów** systemu Windows), a program Visual Studio odnajduje i wyświetla testy. Jeśli testy nie są początkowo wyświetlane, ponownie skompiluj projekt, aby odświeżyć listę.

   ![Odnajdywanie testów w Eksploratorze testów](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > W przypadku języka TypeScript nie należy używać `outfile` opcji w *tsconfig.json*, ponieważ Eksplorator testów nie będzie w stanie znaleźć testów jednostkowych. Możesz użyć `outdir` opcji, ale upewnij się, że pliki konfiguracji, takie jak `package.json` i `tsconfig.json` znajdują się w katalogu głównym projektu.

## <a name="run-tests-aspnet-core"></a>Uruchom testy (ASP.NET Core)

::: moniker range=">=vs-2019"
Testy można uruchomić, klikając link **Uruchom wszystkie** w Eksploratorze testów. Lub można uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając polecenie **Uruchom** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i wyświetla wyniki. Ponadto można debugować wybrane testy, klikając je prawym przyciskiem myszy i wybierając polecenie **Debuguj**.
::: moniker-end
::: moniker range="vs-2017"
Testy można uruchomić, klikając link **Uruchom wszystkie** w Eksploratorze testów. Lub można uruchomić testy, wybierając jeden lub więcej testów lub grup, klikając prawym przyciskiem myszy i wybierając polecenie **Uruchom wybrane testy** z menu skrótów. Testy są uruchamiane w tle, a Eksplorator testów automatycznie aktualizuje i wyświetla wyniki. Ponadto można debugować wybrane testy, wybierając **Debuguj wybrane testy**.
::: moniker-end

W przypadku języka TypeScript testy jednostkowe są uruchamiane względem wygenerowanego kodu JavaScript.

![Wyniki Eksploratora testów](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> W większości scenariuszy języka TypeScript można debugować test jednostkowy przez ustawienie punktu przerwania w kodzie TypeScript, kliknięcie prawym przyciskiem myszy w Eksploratorze testów i wybranie polecenia **Debuguj**. W bardziej złożonych scenariuszach, takich jak niektóre scenariusze korzystające z map źródła, może wystąpić problem, który sprawia, że punkty przerwania w kodzie TypeScript. Aby obejść ten sposób, spróbuj użyć `debugger` słowa kluczowego.

> [!NOTE]
> Obecnie nie obsługujemy testów profilowania ani pokrycia kodu.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Dodawanie obsługi dla struktury testów jednostkowych

Można dodać obsługę dodatkowych platform testowych przez implementację logiki odnajdywania i wykonywania przy użyciu języka JavaScript. Można to zrobić przez dodanie folderu o nazwie struktury testowej w:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Ten folder musi zawierać plik JavaScript o tej samej nazwie, który eksportuje następujące dwie funkcje:

* `find_tests`
* `run_tests`

Aby zapoznać się z dobrymi przykładami `find_tests` i `run_tests` implementacjami, zobacz implementację struktury testów jednostkowych środowiska Mocha w:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Odnajdywanie dostępnych platform testowych odbywa się po rozpoczęciu programu Visual Studio. Jeśli po uruchomieniu programu Visual Studio zostanie dodana struktura, uruchom ponownie program Visual Studio, aby wykryć strukturę. Nie trzeba jednak ponownie uruchamiać w przypadku wprowadzania zmian w implementacji.

## <a name="unit-tests-in-net-framework"></a>Testy jednostkowe w .NET Framework

Nie możesz pisać testów jednostkowych tylko w Node.js i ASP.NET Core projektach. Po dodaniu właściwości TestFramework i TestRoot do dowolnego projektu C# lub Visual Basic testy te zostaną wyliczone i można uruchomić je przy użyciu okna Eksplorator testów.

Aby włączyć tę funkcję, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań, wybierz polecenie **Zwolnij projekt**, a następnie wybierz polecenie **Edytuj projekt**. Następnie w pliku projektu Dodaj następujące dwa elementy do grupy właściwości.

> [!IMPORTANT]
> Upewnij się, że grupa właściwości, do której dodawane są elementy, nie ma określonego warunku.
> Może to spowodować nieoczekiwane zachowanie.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Następnie Dodaj testy do podanego głównego folderu testowego i będą one dostępne do uruchomienia w oknie Eksplorator testów. Jeśli nie pojawią się na początku, może być konieczne ponowne skompilowanie projektu.

## <a name="unit-test-net-core-and-net-standard"></a>Test jednostkowy .NET Core i .NET Standard

Oprócz powyższych właściwości należy również zainstalować pakiet NuGet [Microsoft. JavaScript. testu jednostkowego](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) i ustawić właściwość:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Niektóre środowiska testowe mogą wymagać dodatkowych pakietów npm na potrzeby wykrywania testów. Na przykład jest to program, który wymaga npm pakietu. W razie potrzeby zapoznaj się z dokumentacją dla konkretnej struktury.
