---
title: Opcje wiersza poleceń narzędzia VSTest.Console.exe
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bf4cea6dcd87b8cf0d2113ac3a245163ba89080
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746918"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opcje wiersza poleceń narzędzia VSTest.Console.exe

*VSTest.Console.exe* to narzędzie wiersza polecenia do uruchomienia testów. Można określać wiele opcji w dowolnej kolejności, w wierszu polecenia. Te opcje są wymienione w [ogólne opcje wiersza polecenia](#general-command-line-options).

> [!NOTE]
> Adapter MSTest w programie Visual Studio działa także w starszym trybie (równoznaczna z uruchomieniem testów z *mstest.exe*) dla zgodności. W starszym trybie nie można korzystać z funkcji TestCaseFilter. Adapter może się przełączyć do starszej wersji trybu podczas *testsettings* określono pliku **atrybut forcelegacymode** jest ustawiona na **true** w *runsettings* plik lub za pomocą atrybuty takie jak **HostType**.
>
> Aby uruchomić testy automatyczne na komputerze z procesorem ARM, należy użyć *VSTest.Console.exe*.

## <a name="general-command-line-options"></a>Ogólne opcje wiersza polecenia

Poniższa tabela zawiera listę wszystkich opcji *VSTest.Console.exe* i krótkie opisy. Zobacz podobne podsumowanie, wpisując `VSTest.Console/?` w wierszu polecenia.

| Opcja | Opis |
|---|---|
|**[*nazwy pliku testów*]**|Uruchom testy z określonych plików. Oddziel wiele nazw plików testowych spacjami.<br />Przykłady: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/ Ustawienia: [*nazwy pliku*]**|Uruchom testy z użyciem ustawień dodatkowych, takich jak moduły zbierające dane.<br />Przykład: `/Settings:Local.RunSettings`|
|**/ Tests: [*nazwa testu*]**|Uruchom testy z nazwami, które zawierają podanych wartości. Aby wprowadzić wiele wartości, oddziel je przecinkami.<br />Przykład: `/Tests:TestMethod1,testMethod2`<br />**/Testy** opcji wiersza polecenia nie można używać z **/testcasefilter** opcji wiersza polecenia.|
|**/ Parallel**|Określa, że testy mają być wykonywane równolegle. Domyślnie wszystkie dostępne rdzenie na komputerze mogą być używane. Liczba rdzeni do użycia, można skonfigurować za pomocą pliku ustawień.|
|**/ Enablecodecoverage**|Umożliwia uruchamianie adaptera diagnostycznych CodeCoverage w teście danych.<br />Domyślne ustawienia są używane, jeśli nie określono pliku ustawień.|
|**/ InIsolation.**|Uruchamia testy w procesie izolowanym.<br />Sprawia, że ta izolacja *vstest.console.exe* procesu mniej prawdopodobne zatrzymane w przypadku błędu w testach, ale testy mogą działać wolniej.|
|**/UseVsixExtensions**|Ta opcja powoduje, że *vstest.console.exe* użycie procesu lub pomija rozszerzenia VSIX zainstalowane w uruchomionym teście (jeśli istnieje).<br />Ta opcja jest przestarzały. Uruchamianie z kolejnej głównej wersji programu Visual Studio, ta opcja może zostać usunięty. Przenieś do używania rozszerzenia dostępne jako pakiet NuGet.<br />Przykład: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*path*]**|Wymusza *vstest.console.exe* proces używa niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieją) w przebiegu testu.<br />Przykład: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/ Platform: [*typu platformy*]**|Docelowa platforma architektury ma być używany dla wykonywania testów.<br />Prawidłowe wartości to x86 x64 i ARM.|
|**/ Framework: [*framework w wersji*]**|Wersja platformy .NET docelowa ma być używany dla wykonywania testów.<br />Prawidłowe wartości to Framework35, Framework40 i Framework45 oraz FrameworkUap10.<br />Jeśli platforma docelowa jest określona jako **Framework35**, testy w CLR w wersji 4.0 "compatibly tryb".<br />Przykład: `/Framework:framework40`|
|**/TestCaseFilter:[*expression*]**|Uruchom testy, które odpowiadają danemu wyrażeniu.<br />< wyrażenie\> jest w formacie < właściwość\>= < wartość\>[\|< wyrażenie\>].<br />Przykład: `/TestCaseFilter:"Priority=1"`<br />Przykład: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/Testcasefilter** opcji wiersza polecenia nie można używać z **/testy** opcji wiersza polecenia. <br />Aby uzyskać informacje na temat tworzenia i używania wyrażeń, zobacz [filtr przypadków testowych](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Wyświetla informacje o użyciu.|
|**/ Logger: [*identyfikatora uri/friendlyname*]**|Określ Rejestrator dla wyników badań.<br />Przykład: Aby rejestrować wyniki w Visual Studio Test wyniki pliku (TRX), użyj **/Logger:trx**.<br />Przykład: Aby opublikować wyniki testu z Team Foundation Server, użyj wyrażenia TfsPublisher:<br />**/logger:TfsPublisher;**<br />**Kolekcja = < adres url projektu\>;**<br />**BuildName = < nazwa kompilacji\>;**<br />**TeamProject = < Nazwa projektu\>;**<br />**[; Platform = < wartość domyślna to "Dowolny procesor CPU" >]**<br />**[; Flavor = < wartość domyślna to "Debugowanie" >]**<br />**[;RunTitle=<title\>]**|
|**/ ListTests: [*nazwy pliku*]**|Wyświetla listy odkrytych testów z podanego kontenera testowego.|
|**/ ListDiscoverers**|Wyświetla listę zainstalowanych odkrywców testów.|
|**/ ListExecutors**|Wyświetla listę zainstalowanych wykonawców testów.|
|**/ ListLoggers**|Wyświetla listę zainstalowanych programów rejestrujących testy.|
|**/ListSettingsProviders**|Wyświetla listę zainstalowanych dostawców ustawień testu.|
|**/ Polecenia blame**|Śledzi testów, ponieważ są one wykonywane i, jeśli wystąpiła awaria procesu hosta testów, emituje nazwy testów, w kolejności ich wykonywania do i łącznie z określonego testu, która była uruchomiona w chwili pojawienia się awarii. Te dane wyjściowe ułatwia izolowania naruszającym testu i przeprowadzić dalszą diagnozę. [Więcej informacji na](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/ Diag: [*nazwy pliku*]**|Zapisuje diagnostyczne dzienniki śledzenia w określonym pliku.|
|**/ ResultsDirectory: [*ścieżki*]**|Katalog wyników testu zostaną utworzone w określonej ścieżce Jeśli nie istnieje.<br />Przykład: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Identyfikator procesu nadrzędnego odpowiedzialna za uruchamianie bieżącego procesu.|
|**/Port:[*port*]**|Port do połączenia z gniazdem i odbierania komunikatów zdarzeń.|
|**/ Zbieranie: [*dataCollector friendlyName*]**|Włącza moduł zbierający dane dla przebiegu testu. [Więcej informacji na](https://aka.ms/vstest-collect).|

> [!TIP]
> Opcje i wartości nie jest rozróżniana wielkość liter.

## <a name="examples"></a>Przykłady

Składnia służąca do uruchamiania *VSTest.Console.exe* jest:

`Vstest.console.exe [TestFileNames] [Options]`

Następujące polecenie uruchamia *VSTest.Console.exe* biblioteki testu **myTestProject.dll**:

```cmd
vstest.console.exe myTestProject.dll
```

Następujące polecenie uruchamia *VSTest.Console.exe* z wielu plików testowych. Rozdziel nazw plików testowych spacjami:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Następujące polecenie uruchamia *VSTest.Console.exe* kilka opcji. Uruchamia testy *myTestFile.dll* pliku w izolowanym ustawień procesu i używa, określonych w *Local.RunSettings* pliku. Ponadto tylko uruchamia testy oznaczone jako "priorytet = 1" i rejestruje wyniki do *.trx* pliku.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
