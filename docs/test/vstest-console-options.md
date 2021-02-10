---
title: Opcje wiersza poleceń narzędzia VSTest.Console.exe
description: Dowiedz się więcej na temat narzędzia wiersza polecenia VSTest.Console.exe, które uruchamia testy. Ten artykuł zawiera ogólne opcje wiersza polecenia.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6256343efbc9b81c14b03753fab2fa478df1e4f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946192"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opcje wiersza poleceń narzędzia VSTest.Console.exe

*VSTest.Console.exe* jest narzędziem wiersza polecenia do uruchamiania testów. W wierszu polecenia można określić kilka opcji w dowolnej kolejności. Te opcje są wymienione w [ogólnych opcjach wiersza polecenia](#general-command-line-options).

> [!NOTE]
> Adapter MSTest w programie Visual Studio działa również w trybie starszej wersji (równoważne uruchamianiu testów z *mstest.exe*) w celu zapewnienia zgodności. W trybie starszym nie można korzystać z funkcji TestCaseFilter. Karta może przełączać się do trybu starszego, gdy jest określony plik *testsettings* , **forcelegacymode** jest ustawiona na **wartość true** w pliku *runsettings* lub przy użyciu atrybutów takich jak **HostType**.
>
> Aby uruchomić testy automatyczne na komputerze opartym na architekturze ARM, należy użyć *VSTest.Console.exe*.

Otwórz [wiersz polecenia dla deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs) , aby użyć narzędzia wiersza polecenia, lub narzędzie można znaleźć w *pliku% Program Files (x86)% \ Microsoft Visual Studio \\<wersja \> \\<Edition \> \common7\ide\CommonExtensions \\<platformę | Microsoft>*.

## <a name="general-command-line-options"></a>Ogólne opcje wiersza polecenia

W poniższej tabeli wymieniono wszystkie opcje *VSTest.Console.exe* i krótkie opisy. Podobne Podsumowanie można zobaczyć, wpisując `VSTest.Console/?` w wierszu polecenia.

| Opcja | Opis |
|---|---|
|**[*nazwy plików testowych*]**|Uruchom testy z określonych plików. Oddziel wiele nazw plików testowych spacjami.<br />Przykłady: `mytestproject.dll` , `mytestproject.dll myothertestproject.exe`|
|**/Settings: [*Nazwa pliku*]**|Uruchom testy z dodatkowymi ustawieniami, takimi jak moduły zbierające dane. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Przykład: `/Settings:local.runsettings`|
|**/Tests: [*nazwa testu*]**|Uruchom testy z nazwami, które zawierają podane wartości. Aby podać wiele wartości, rozdziel je przecinkami.<br />Przykład: `/Tests:TestMethod1,testMethod2`<br />Opcji wiersza polecenia **/Tests** nie można używać z opcją wiersza polecenia **/TestCaseFilter** .|
|**/Parallel**|Określa, że testy są wykonywane równolegle. Domyślnie można użyć maksymalnie wszystkich dostępnych rdzeni na komputerze. Można skonfigurować liczbę rdzeni do użycia w pliku ustawień.|
|**/Enablecodecoverage**|Włącza adapter diagnostyki danych CodeCoverage w przebiegu testu.<br />Ustawienia domyślne są używane, jeśli nie zostaną określone przy użyciu pliku ustawień.|
|**/Inisolation.**|Uruchamia testy w procesie izolowanym.<br />Ta izolacja sprawia, że proces *vstest.console.exe* jest mniej prawdopodobnie zatrzymany w przypadku błędu w testach, ale testy mogą działać wolniej.|
|**/UseVsixExtensions**|Ta opcja powoduje, że proces *vstest.console.exe* używa lub pomija zainstalowane rozszerzenia VSIX (jeśli istnieją) w przebiegu testu.<br />Ta opcja jest przestarzały. Począwszy od następnej wersji głównej programu Visual Studio, ta opcja może zostać usunięta. Przenieś do pakietu, który jest używany jako pakiet NuGet.<br />Przykład: `/UseVsixExtensions:true`|
|**/TestAdapterPath: [*ścieżka*]**|Wymusza, aby proces *vstest.console.exe* używać niestandardowych adapterów testowych z określonej ścieżki (jeśli istnieje) w przebiegu testu.<br />Przykład: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform: [*Typ platformy*]**|Wymusza użycie danej platformy zamiast platformy ustalonej na podstawie bieżącego środowiska uruchomieniowego. Ta opcja umożliwia wymuszenie tylko platform x86 i x64 w systemie Windows. Opcja ARM jest uszkodzona i spowoduje to architekturę x64 w większości systemów.<br />NIE określaj tej opcji do uruchamiania w przypadku środowisk uruchomieniowych, które nie znajdują się na liście prawidłowych wartości, takich jak ARM64.<br />Prawidłowe wartości to x86, x64 i ARM.<br /> 
|**/Framework: [*wersja platformy*]**|Docelowa wersja platformy .NET, która ma zostać użyta do wykonania testu.<br />Przykładowe wartości to `Framework35` , `Framework40` , `Framework45` , `FrameworkUap10` , `.NETCoreApp,Version=v1.1` .<br />TargetFrameworkAttribute jest używany do automatycznego wykrywania tej opcji z zestawu i domyślnie, `Framework40` gdy atrybut nie jest obecny. Tę opcję należy określić jawnie po usunięciu [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) z zestawów .NET Core.<br />Jeśli struktura docelowa jest określona jako **Framework35**, testy są uruchamiane w trybie zgodności środowiska CLR 4,0.<br />Przykład: `/Framework:framework40`|
|**/TestCaseFilter: [*wyrażenie*]**|Uruchom testy zgodne z podanym wyrażeniem.<br />Wyrażenie <\> ma format <Property \> =<Value \> [ \| wyrażenie<\> ].<br />Przykład: `/TestCaseFilter:"Priority=1"`<br />Przykład: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Opcji wiersza polecenia **/TestCaseFilter** nie można używać z opcją wiersza polecenia **/Tests** . <br />Aby uzyskać informacje na temat tworzenia i używania wyrażeń, zobacz [Filtr przypadku testowego](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Wyświetla informacje o użyciu.|
|**/Logger: [*URI/FriendlyName*]**|Określ Rejestrator dla wyników testu. Określ parametr wiele razy, aby włączyć obsługę wielu rejestratorów.<br />Przykład: Aby rejestrować wyniki do pliku Wyniki testów programu Visual Studio (TRX), użyj<br />**/Logger: TRX**<br />**[; Plik_dziennikaname = \<Defaults to unique file name> ]**|
|**/ListTests: [*Nazwa pliku*]**|Wyświetla listę odnalezionych testów z danego kontenera testowego.|
|**/ListDiscoverers**|Wyświetla listę zainstalowanych odnajdywania testów.|
|**/ListExecutors**|Wyświetla listę zainstalowanych programów wykonujących testy.|
|**/ListLoggers**|Wyświetla listę zainstalowanych rejestratorów testów.|
|**/ListSettingsProviders**|Wyświetla listę zainstalowanych dostawców ustawień testu.|
|**/Blame**|Uruchamia testy w trybie polecenia Blame. Ta opcja jest przydatna do izolowania problematycznych testów, które powodują awarię hosta testowego. Gdy zostanie wykryta awaria, tworzy plik sekwencji w programie `TestResults/<Guid>/<Guid>_Sequence.xml` , który przechwytuje kolejność testów, które zostały uruchomione przed awarią. Aby uzyskać więcej informacji, zobacz [polecenia Blame Data Collector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag: [*Nazwa pliku*]**|Zapisuje dzienniki śledzenia diagnostycznego do określonego pliku.|
|**/ResultsDirectory: [*ścieżka*]**|Katalog wyników testu zostanie utworzony w określonej ścieżce, jeśli nie istnieje.<br />Przykład: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId: [*ParentProcessId*]**|Identyfikator procesu nadrzędnego odpowiedzialny za uruchamianie bieżącego procesu.|
|**/Port: [*port*]**|Port połączenia gniazda i otrzymywania komunikatów o zdarzeniach.|
|**/Collect: [*friendlyer datacollect*]**|Włącza moduł zbierający dane dla przebiegu testu. [Więcej informacji](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> W opcjach i wartościach nie jest rozróżniana wielkość liter.

## <a name="examples"></a>Przykłady

Składnia *vstest.console.exe* jest następująca:

`vstest.console.exe [TestFileNames] [Options]`

Następujące polecenie działa *vstest.console.exe* dla biblioteki testów *myTestProject.dll*:

```cmd
vstest.console.exe myTestProject.dll
```

Następujące polecenie działa *vstest.console.exe* z wieloma plikami testowymi. Oddziel nazwy plików testowych spacjami:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Następujące polecenie działa *vstest.console.exe* z kilkoma opcjami. Uruchamia testy w pliku *myTestFile.dll* w procesie izolowanym i używa ustawień określonych w *lokalnym pliku. runsettings* . Ponadto uruchamia tylko testy oznaczone "Priority = 1" i rejestruje wyniki w pliku *. TRX* .

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Następujące polecenie działa *vstest.console.exe* z `/blame` opcją dla biblioteki testów *myTestProject.dll*:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Jeśli wystąpi awaria hosta testowego, zostanie wygenerowany plik *sequence.xml* . Plik zawiera w pełni kwalifikowane nazwy testów w sekwencji wykonywania do i włącznie z konkretnym testem, który był uruchomiony w chwili awarii.

Jeśli nie wystąpi awaria hosta testowego, plik *sequence.xml* nie zostanie wygenerowany.

Przykład wygenerowanego pliku *sequence.xml* : 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
