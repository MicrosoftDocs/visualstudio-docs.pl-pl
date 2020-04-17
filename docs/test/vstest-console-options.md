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
ms.openlocfilehash: 40f8bc4847201d1bd0298bc91432996ecce58d65
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615554"
---
# <a name="vstestconsoleexe-command-line-options"></a>Opcje wiersza poleceń narzędzia VSTest.Console.exe

*VSTest.Console.exe* jest narzędziem wiersza polecenia do uruchamiania testów. Można określić kilka opcji w dowolnej kolejności w wierszu polecenia. Te opcje są wymienione w [opcjach wiersza polecenia ogólne](#general-command-line-options).

> [!NOTE]
> Karta MSTest w programie Visual Studio działa również w trybie starszej wersji (odpowiednik uruchamiania testów z *mstest.exe)* dla zgodności. W trybie starszej wersji nie można skorzystać z funkcji TestCaseFilter. Karta może przełączyć się do trybu starszego, gdy plik *testsettings* jest określony, **forcelegacymode** jest ustawiona na **true** w pliku *runsettings* lub przy użyciu atrybutów, takich jak **HostType**.
>
> Aby uruchomić automatyczne testy na komputerze opartym na architekturze ARM, należy użyć *pliku VSTest.Console.exe*.

Otwórz [wiersz polecenia dewelopera](/dotnet/framework/tools/developer-command-prompt-for-vs) w celu użycia narzędzia wiersza polecenia lub narzędzie można znaleźć w *%Program Files(x86)%\Microsoft Visual\\ Studio<version\> \\<edition\>\common7\ide\CommonExtensions\\<Platform | Microsoft>*.

## <a name="general-command-line-options"></a>Opcje wiersza polecenia ogólnego

W poniższej tabeli wymieniono wszystkie opcje *programu VSTest.Console.exe* i ich krótkie opisy. Podobne podsumowanie można zobaczyć, `VSTest.Console/?` wpisując je w wierszu polecenia.

| Opcja | Opis |
|---|---|
|**[*nazwy plików testowych*]**|Uruchom testy z określonych plików. Oddziel wiele nazw plików testowych spacjami.<br />Przykłady: `mytestproject.dll`,`mytestproject.dll myothertestproject.exe`|
|**/Settings:[*nazwa pliku*]**|Uruchom testy z dodatkowymi ustawieniami, takimi jak moduły zbierające dane.<br />Przykład: `/Settings:Local.RunSettings`|
|**/Tests:[*nazwa testu*]**|Uruchom testy z nazwami, które zawierają podane wartości. Aby podać wiele wartości, oddziel je przecinkami.<br />Przykład: `/Tests:TestMethod1,testMethod2`<br />Opcji wiersza polecenia **/Tests** nie można używać z opcją wiersza polecenia **/TestCaseFilter.**|
|**/Równolegle**|Określa, że testy mają być wykonywane równolegle. Domyślnie można używać maksymalnie wszystkich dostępnych rdzeni na komputerze. Liczbę rdzeni do użycia można skonfigurować w pliku ustawień.|
|**/Enablecodecoverage**|Włącza kartę diagnostyczną danych CodeCoverage w przebiegu testowym.<br />Ustawienia domyślne są używane, jeśli nie są określone przy użyciu pliku ustawień.|
|**/Niesienie**|Uruchamia testy w procesie izolowanym.<br />Ta izolacja sprawia, że proces *vstest.console.exe* jest mniej prawdopodobne, aby zatrzymać się na błąd w testach, ale testy mogą działać wolniej.|
|**/UseVsixExtensions**|Ta opcja sprawia, że proces *vstest.console.exe* używać lub pominąć rozszerzenia VSIX zainstalowane (jeśli istnieją) w przebiegu testu.<br />Ta opcja jest przestarzały. Począwszy od następnej wersji głównej programu Visual Studio ta opcja może zostać usunięta. Przejdź do korzystania z rozszerzeń udostępnione jako pakiet NuGet.<br />Przykład: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*ścieżka*]**|Wymusza proces *vstest.console.exe* do używania niestandardowych kart testowych z określonej ścieżki (jeśli istnieje) w przebiegu testu.<br />Przykład: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*typ platformy*]**|Architektura platformy docelowej, która ma być używana do wykonywania testów.<br />Prawidłowe wartości to x86, x64 i ARM.|
|**/Framework: [*wersja ramowa*]**|Docelowa wersja .NET, która ma być używana do wykonywania testów.<br />Przykładowe `Framework35`wartości `Framework40` `Framework45`to `FrameworkUap10` `.NETCoreApp,Version=v1.1`, , , , .<br />TargetFrameworkAttribute służy do automatycznego wykrywania tej opcji z `Framework40` zestawu i domyślnie, gdy atrybut nie jest obecny. Należy określić tę opcję jawnie, jeśli usuniesz [TargetFrameworkAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.versioning.targetframeworkattribute) z zestawów .NET Core.<br />Jeśli struktura docelowa jest określona jako **Framework35**, testy są uruchamiane w programie CLR 4.0 "tryb zgodności".<br />Przykład: `/Framework:framework40`|
|**/TestCaseFilter:[*wyrażenie*]**|Uruchom testy, które pasują do danego wyrażenia.<br /><\> Wyrażenie ma format <właściwość\>=<wartość\>[\| wyrażenie<\>].<br />Przykład: `/TestCaseFilter:"Priority=1"`<br />Przykład: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Opcji wiersza polecenia **/TestCaseFilter** nie można używać z opcją wiersza polecenia **/Tests.** <br />Aby uzyskać informacje dotyczące tworzenia i używania wyrażeń, zobacz [Filtr Skrzynia testowa](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Wyświetla informacje o użytkowaniu.|
|**/Rejestrator:[*uri/friendlyname*]**|Określ rejestrator dla wyników testów.<br />Przykład: Aby rejestrować wyniki w pliku wyników testów programu Visual Studio (TRX), należy użyć<br />**/Rejestrator:trx**<br />**[; LogFileName=\<Domyślnie unikatowa nazwa pliku>]**|
|**/ListTests:[*nazwa pliku*]**|Wyświetla listę wykrytych testów z danego kontenera testowego.|
|**/ListaOdkryjce**|Wyświetla listę zainstalowanych odnajdowanych testów.|
|**/ListWykonacze**|Wyświetla listę zainstalowanych wykonawców testów.|
|**/ListLoggers**|Wyświetla listę zainstalowanych rejestratorów testowych.|
|**/ListSettingsProvidery**|Wyświetla listę zainstalowanych dostawców ustawień testowych.|
|**/Obwinianie**|Śledzi testy podczas ich wykonywania i, jeśli proces hosta testów ulegnie awarii, emituje nazwy testów w ich sekwencji wykonywania do określonego testu, który był uruchomiony w momencie awarii. To dane wyjściowe ułatwia izolowanie testu naruszającego i diagnozowania dalej. [Więcej informacji](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*nazwa pliku*]**|Zapisuje dzienniki śledzenia diagnostycznego do określonego pliku.|
|**/ResultsDirectory:[*ścieżka*]**|Katalog wyników testów zostanie utworzony w określonej ścieżce, jeśli nie istnieje.<br />Przykład: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Identyfikator procesu nadrzędnego odpowiedzialnego za uruchomienie bieżącego procesu.|
|**/Port:[*port*]**|Port do podłączenia gniazda i odbieranie komunikatów o zdarzeniu.|
|**/Collect:[*dataCollector friendlyName*]**|Włącza moduł zbierający dane dla przebiegu testowego. [Więcej informacji](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> W opcjach i wartościach nie rozróżnia się wielkość liter.

## <a name="examples"></a>Przykłady

Składnia uruchamiania *programu VSTest.Console.exe* jest:

`Vstest.console.exe [TestFileNames] [Options]`

Następujące polecenie uruchamia *program VSTest.Console.exe* dla biblioteki testowej **myTestProject.dll:**

```cmd
vstest.console.exe myTestProject.dll
```

Następujące polecenie uruchamia *program VSTest.Console.exe* z wieloma plikami testowymi. Oddzielne nazwy plików testowych ze spacjami:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Następujące polecenie uruchamia *program VSTest.Console.exe* z kilkoma opcjami. Uruchamia testy w pliku *myTestFile.dll* w izolowanym procesie i używa ustawień określonych w pliku *Local.RunSettings.* Ponadto uruchamia tylko testy oznaczone jako "Priority=1" i rejestruje wyniki w pliku *.trx.*

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
