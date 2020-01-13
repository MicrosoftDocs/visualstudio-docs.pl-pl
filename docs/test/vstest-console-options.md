---
title: Opcje wiersza poleceń narzędzia VSTest.Console.exe
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: affad69f6821addb50686d4f41d0bdb3bd816e8e
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919022"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opcje wiersza poleceń narzędzia VSTest.Console.exe

*VSTest. Console. exe* to narzędzie wiersza polecenia do uruchamiania testów. W wierszu polecenia można określić kilka opcji w dowolnej kolejności. Te opcje są wymienione w [ogólnych opcjach wiersza polecenia](#general-command-line-options).

> [!NOTE]
> Adapter MSTest w programie Visual Studio działa również we starszej wersji (równoważnej uruchamianiu testów z *MSTest. exe*) w celu zapewnienia zgodności. W trybie starszym nie można korzystać z funkcji TestCaseFilter. Karta może przełączać się do trybu starszego, gdy jest określony plik *testsettings* , **forcelegacymode** jest ustawiona na **wartość true** w pliku *runsettings* lub przy użyciu atrybutów takich jak **HostType**.
>
> Aby uruchomić testy automatyczne na komputerze opartym na architekturze ARM, należy użyć *VSTest. Console. exe*.

Otwórz [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) , aby użyć narzędzia wiersza polecenia, lub narzędzie można znaleźć w *pliku% Program Files (x86)% \ Microsoft Visual Studio\\< wersji\>\\< edition\>\Common7\ide\CommonExtensions\\< platformę | Microsoft >* .

## <a name="general-command-line-options"></a>Ogólne opcje wiersza polecenia

W poniższej tabeli wymieniono wszystkie opcje *VSTest. Console. exe* i krótkie opisy. Podobne Podsumowanie można zobaczyć, wpisując `VSTest.Console/?` w wierszu polecenia.

| Opcja | Opis |
|---|---|
|**[*nazwy plików testowych*]**|Uruchom testy z określonych plików. Oddziel wiele nazw plików testowych spacjami.<br />Przykłady: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings: [*Nazwa pliku*]**|Uruchom testy z dodatkowymi ustawieniami, takimi jak moduły zbierające dane.<br />Przykład: `/Settings:Local.RunSettings`|
|**/Tests: [*nazwa testu*]**|Uruchom testy z nazwami, które zawierają podane wartości. Aby podać wiele wartości, rozdziel je przecinkami.<br />Przykład: `/Tests:TestMethod1,testMethod2`<br />Opcji wiersza polecenia **/Tests** nie można używać z opcją wiersza polecenia **/TestCaseFilter** .|
|**/Parallel**|Określa, że testy są wykonywane równolegle. Domyślnie można użyć maksymalnie wszystkich dostępnych rdzeni na komputerze. Można skonfigurować liczbę rdzeni do użycia w pliku ustawień.|
|**/Enablecodecoverage**|Włącza adapter diagnostyki danych CodeCoverage w przebiegu testu.<br />Ustawienia domyślne są używane, jeśli nie zostaną określone przy użyciu pliku ustawień.|
|**/Inisolation.**|Uruchamia testy w procesie izolowanym.<br />Ta izolacja sprawia, że proces *VSTest. Console. exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.|
|**/UseVsixExtensions**|Ta opcja powoduje, że proces *VSTest. Console. exe* używa lub pomija zainstalowane rozszerzenia VSIX (jeśli istnieją) w przebiegu testu.<br />Ta opcja jest przestarzały. Począwszy od następnej wersji głównej programu Visual Studio, ta opcja może zostać usunięta. Przenieś do pakietu, który jest używany jako pakiet NuGet.<br />Przykład: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*path*]**|Wymusza, aby proces *VSTest. Console. exe* używał niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieje) w przebiegu testu.<br />Przykład: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform: [*Typ platformy*]**|Docelowa architektura platformy, która ma być używana na potrzeby wykonywania testów.<br />Prawidłowe wartości to x86, x64 i ARM.|
|**/Framework: [*wersja platformy*]**|Docelowa wersja platformy .NET, która ma zostać użyta do wykonania testu.<br />Przykładowe wartości to `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10`, `.NETCoreApp,Version=v1.1`.<br />Jeśli struktura docelowa jest określona jako **Framework35**, testy są uruchamiane w trybie compatibly CLR 4,0.<br />Przykład: `/Framework:framework40`|
|**/TestCaseFilter:[*expression*]**|Uruchom testy zgodne z podanym wyrażeniem.<br />\> wyrażenia < ma format < Właściwość\>= < wartość\>[\|< wyrażenie\>].<br />Przykład: `/TestCaseFilter:"Priority=1"`<br />Przykład: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Opcji wiersza polecenia **/TestCaseFilter** nie można używać z opcją wiersza polecenia **/Tests** . <br />Aby uzyskać informacje na temat tworzenia i używania wyrażeń, zobacz [Filtr przypadku testowego](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Wyświetla informacje o użyciu.|
|**/Logger: [*URI/FriendlyName*]**|Określ Rejestrator dla wyników testu.<br />Przykład: Aby rejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj<br />**/Logger: TRX**<br />**[; Plik_dziennikaname =\<domyślna nazwa pliku >]**<br />Przykład: Aby opublikować wyniki testów do Team Foundation Server, użyj TfsPublisher:<br />**/logger:TfsPublisher;**<br />**Kolekcja = < URL projektu\>;**<br />**Kompilacjaname = < nazwa kompilacji\>;**<br />**TeamProject = < nazwa projektu\>;**<br />**[; Wartość platform =\<domyślna to "dowolny procesor CPU" >]**<br />**[; Wersja =\<domyślna to "debug" >]**<br />**[;RunTitle=<title\>]**<br />Uwaga: rejestrator TfsPublisher jest przestarzały w programie Visual Studio 2017 i nie jest obsługiwany w nowszych wersjach programu Visual Studio. W tych scenariuszach należy zamiast tego użyć rejestratora niestandardowego. Ten rejestrator przełącza Rejestrator do trybu starszej wersji.|
|**/ListTests: [*Nazwa pliku*]**|Wyświetla listę odnalezionych testów z danego kontenera testowego.|
|**/ListDiscoverers**|Wyświetla listę zainstalowanych odnajdywania testów.|
|**/ListExecutors**|Wyświetla listę zainstalowanych programów wykonujących testy.|
|**/ListLoggers**|Wyświetla listę zainstalowanych rejestratorów testów.|
|**/ListSettingsProviders**|Wyświetla listę zainstalowanych dostawców ustawień testu.|
|**/Blame**|Śledzi testy w trakcie ich wykonywania, a jeśli proces hosta testowego ulega awarii, emituje nazwy testów w sekwencji wykonywania do i włącznie z konkretnym testem, który był uruchomiony w chwili awarii. Te dane wyjściowe ułatwiają odizolowanie badanego testu i dalsze zdiagnozowanie. [Więcej informacji](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag: [*Nazwa pliku*]**|Zapisuje dzienniki śledzenia diagnostycznego do określonego pliku.|
|**/ResultsDirectory: [*ścieżka*]**|Katalog wyników testu zostanie utworzony w określonej ścieżce, jeśli nie istnieje.<br />Przykład: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.|
|**/Port:[*port*]**|Port połączenia gniazda i otrzymywania komunikatów o zdarzeniach.|
|**/Collect: [*friendlyer datacollect*]**|Włącza moduł zbierający dane dla przebiegu testu. [Więcej informacji](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> W opcjach i wartościach nie jest rozróżniana wielkość liter.

## <a name="examples"></a>Przykłady

Składnia do uruchamiania *VSTest. Console. exe* to:

`Vstest.console.exe [TestFileNames] [Options]`

Następujące polecenie uruchamia *VSTest. Console. exe* dla biblioteki testowej **myTestProject. dll**:

```cmd
vstest.console.exe myTestProject.dll
```

Następujące polecenie uruchamia *VSTest. Console. exe* z wieloma plikami testowymi. Oddziel nazwy plików testowych spacjami:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Następujące polecenie uruchamia *VSTest. Console. exe* z kilkoma opcjami. Uruchamia testy w pliku *myTestFile. dll* w procesie izolowanym i używa ustawień określonych w pliku *Local. runsettings* . Ponadto uruchamia tylko testy oznaczone "Priority = 1" i rejestruje wyniki w pliku *. TRX* .

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
