---
title: Informacje w wierszu polecenia programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8cd04d16f35ae2cc1edaf43ae9f8803c3e424ba
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589256"
---
# <a name="msbuild-command-line-reference"></a>Dokumentacja wiersza polecenia programu MSBuild
Korzystając z programu *MSBuild. exe* do kompilowania pliku projektu lub rozwiązania, można dołączyć kilka przełączników, aby określić różne aspekty procesu.

Każdy przełącznik jest dostępny w dwóch formach:-Switch i/switch. Dokumentacja zawiera tylko formularz-przełącznik.

## <a name="syntax"></a>Składnia

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>Argumenty

|Argument|Opis|
|--------------|-----------------|
|`ProjectFile`|Kompiluje obiekty docelowe w pliku projektu, który określisz. Jeśli nie określisz pliku projektu, MSBuild przeszukuje bieżący katalog roboczy dla rozszerzenia nazwy pliku kończącego się w *proj* i używa tego pliku. Możesz również określić plik rozwiązania programu Visual Studio dla tego argumentu.|

## <a name="switches"></a>Przełączniki

|Przełącznik|Krótka forma|Opis|
|------------|----------------|-----------------|
|-help|/? lub-h|Wyświetla informacje o użyciu. Następujące polecenie jest przykładem:<br /><br /> `msbuild.exe -?`|
|-detailedsummary|-ds|Pokaż szczegółowe informacje na końcu dziennika kompilacji dotyczące konfiguracji, które zostały skompilowane i w jaki sposób zostały zaplanowane do węzłów.|
|-ignoreprojectextensions: `extensions`|-ignore: `extensions`|Ignoruj określone rozszerzenia podczas określania pliku projektu do skompilowania. Użyj średnika lub przecinka do oddzielenia wielu rozszerzeń, jak pokazano na poniższym przykładzie:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|-maxcpucount [:`number`]|-m[:`number`]|Określa maksymalną liczbę współbieżnych procesów, które mają być używane podczas kompilowania. Jeśli ten przełącznik nie zostanie uwzględniony, wartość domyślna to 1. Jeśli ten przełącznik zostanie uwzględniony bez określenia wartości, program MSBuild użyje do liczby procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> W poniższym przykładzie nakazuje programowi MSBuild Kompilowanie przy użyciu trzech procesów MSBuild, co umożliwia kompilowanie w tym samym czasie trzech projektów:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-noautoresponse|-noautorsp|Nie dołączaj żadnych plików *MSBuild. rsp* automatycznie.|
|-nodeReuse:`value`|-Nr:`value`|Włącza lub wyłącza ponowne korzystanie z węzłów programu MSBuild. Można określić następujące wartości:<br /><br /> -   **wartość true**. Węzły pozostają po zakończeniu kompilacji, tak aby kolejne kompilacje mogły ich używać (domyślnie).<br />-   **false**. Węzły nie pozostają po zakończeniu kompilacji.<br /><br /> Węzeł odpowiada projektowi, który jest wykonywany. Jeśli dołączysz przełącznik **-maxcpucount** , wiele węzłów może być wykonywanych współbieżnie.|
|-nologo||Nie wyświetlaj transparentu startowego ani komunikatu o prawach autorskich.|
|<a name="preprocess"></a>-preprocess [:`filepath`]|-PP [:`filepath`]|Utwórz pojedynczy, zagregowany plik projektu, określając wszystkie pliki, które zostaną zaimportowane podczas kompilacji, z oznaczeniem ich granic. Możesz użyć tego przełącznika, aby łatwiej określić, które pliki są importowane, skąd mają być importowane pliki, i które pliki współtworzą kompilację. Gdy używasz tego przełącznika, projekt nie jest skompilowany.<br /><br /> Jeśli określisz `filepath`, zagregowany plik projektu jest wyprowadzany do pliku. W przeciwnym razie dane wyjściowe pojawiają się w oknie konsoli.<br /><br /> Aby uzyskać informacje o sposobach używania elementu `Import` do wstawiania pliku projektu do innego pliku projektu, zobacz [Importowanie elementu (MSBuild)](../msbuild/import-element-msbuild.md) i [instrukcje: Użyj tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|
|-Property:`name`=`value`|-p:`name`=`value`|Ustaw lub Zastąp określone właściwości na poziomie projektu, gdzie `name` jest nazwą właściwości, a `value` jest wartością właściwości. Określ każdą właściwość osobno lub Użyj średnika lub przecinka do oddzielenia wielu właściwości, jak pokazano na poniższym przykładzie:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-Przywracanie|-r|Uruchamia `Restore` miejsce docelowe przed utworzeniem rzeczywistych elementów docelowych.|
|-target:`targets`|-t:`targets`|Kompiluj określone elementy docelowe w projekcie. Każdy element docelowy należy określić osobno lub użyć średnika lub przecinka do oddzielenia wielu elementów docelowych, jak pokazano na poniższym przykładzie:<br /><br /> `-target:PrepareResources;Compile`<br /><br /> W przypadku określenia dowolnych elementów docelowych przy użyciu tego przełącznika są one uruchamiane zamiast dowolnych obiektów docelowych w atrybucie `DefaultTargets` w pliku projektu. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md) i [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Obiekt docelowy jest grupą zadań. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md).|
|-ToolsVersion:`version`|-TV:`version`|Określa wersję zestawu narzędzi do użycia w celu skompilowania projektu, jak pokazano w poniższym przykładzie: `-toolsversion:3.5`<br /><br /> Za pomocą tego przełącznika można skompilować projekt i określić wersję, która różni się od wersji określonej w [elemencie projektu (MSBuild)](../msbuild/project-element-msbuild.md). Aby uzyskać więcej informacji, zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Dla programu MSBuild 4,5 można określić następujące wartości dla `version`: 2,0, 3,5 i 4,0. W przypadku określenia 4,0 Właściwość kompilacja `VisualStudioVersion` określa, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz sekcję podzestawy narzędzi zestawu [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Zestaw narzędzi składa się z zadań, obiektów docelowych i narzędzi, które są używane do kompilowania aplikacji. Narzędzia obejmują kompilatory, takie jak *CSC. exe* i *VBC. exe*. Więcej informacji o zestawach narzędzi można znaleźć w temacie zestaw narzędzi [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardowa i niestandardowa konfiguracja zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)i wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md). **Uwaga:**  Wersja zestawu narzędzi nie jest taka sama jak platforma docelowa, która jest wersją .NET Framework, w której projekt został skompilowany do uruchomienia. Aby uzyskać więcej informacji, zobacz [Target Framework i Target platform](../msbuild/msbuild-target-framework-and-target-platform.md).|
|-Validate: [`schema`]|-Val [`schema`]|Sprawdź poprawność pliku projektu i, jeśli Walidacja zakończyła się powodzeniem, Skompiluj projekt.<br /><br /> Jeśli nie określisz `schema`, projekt zostanie sprawdzony pod kątem domyślnego schematu.<br /><br /> Jeśli określisz `schema`, projekt zostanie sprawdzony pod kątem schematu, który określisz.<br /><br /> Następujące ustawienie jest przykładem: `-validate:MyExtendedBuildSchema.xsd`|
|-verbose:`level`|-v:`level`|Określa ilość informacji, które mają być wyświetlane w dzienniku kompilacji. Każdy Rejestrator wyświetla zdarzenia na podstawie poziomu szczegółowości ustawionych dla tego rejestratora.<br /><br /> Można określić następujące poziomy szczegółowości: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.<br /><br /> Następujące ustawienie jest przykładem: `-verbosity:quiet`|
|-Wersja|-ver|Wyświetlaj tylko informacje o wersji. Projekt nie został skompilowany.|
|@`file`||Wstaw przełączniki wiersza polecenia z pliku tekstowego. Jeśli masz wiele plików, należy je określić osobno. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi](../msbuild/msbuild-response-files.md).|

### <a name="switches-for-loggers"></a>Przełączniki dla rejestratorów

|Przełącznik|Krótka forma|Opis|
|------------|----------------|-----------------|
|-consoleloggerparameters:<br /><br /> `parameters`|-CLP:`parameters`|Przekaż parametry, które określisz, do rejestratora konsoli, który wyświetla informacje o kompilacji w oknie konsoli. Można określić następujące parametry:<br /><br /> -   **PerformanceSummary**. Pokazuje czas spędzony w zadaniach, obiektach docelowych i projektach.<br />**podsumowanie**-   . Pokaż na końcu podsumowanie błędu i ostrzeżenia.<br />-   **nosummary**. Nie pokazuj więcej informacji na temat błędu i ostrzeżenia na końcu.<br />-   **ErrorsOnly**. Pokaż tylko błędy.<br />-   **WarningsOnly**. Pokaż tylko ostrzeżenia.<br />-   **NoItemAndPropertyList**. Nie wyświetlaj listy elementów i właściwości, które pojawią się na początku każdej kompilacji projektu, jeśli poziom szczegółowości jest ustawiony na `diagnostic`.<br />-   **ShowCommandLine**. Pokaż `TaskCommandLineEvent` komunikatów.<br />-   **ShowTimestamp**. Pokaż sygnaturę czasową jako prefiks do dowolnej wiadomości.<br />-   **ShowEventId**. Pokaż identyfikator zdarzenia dla każdego zdarzenia uruchomionego, gotowego zdarzenia i komunikatu.<br />-   **ForceNoAlign**. Nie Wyrównaj tekstu do rozmiaru buforu konsoli.<br />-   **DisableConsoleColor**. Użyj domyślnych kolorów konsoli dla wszystkich komunikatów rejestrowania.<br />-   **DisableMPLogging**. Wyłącz styl rejestrowania wieloprocesorowego danych wyjściowych podczas uruchamiania w trybie non-procesorowym.<br />-   **EnableMPLogging**. Włącz styl rejestrowania wieloprocesorowego nawet w przypadku uruchamiania w trybie innym niż tryb wieloprocesorowy. Ten styl rejestrowania jest domyślnie włączony.<br />-   **szczegółowości**. Zastąp ustawienie **-verbose** dla tego rejestratora.<br /><br /> Użyj średnika do rozdzielenia wielu parametrów, jak pokazano w poniższym przykładzie:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`|
|-distributedFileLogger|-DFL|Rejestruj dane wyjściowe kompilacji każdego węzła programu MSBuild do własnego pliku. Początkowa lokalizacja tych plików jest bieżącym katalogiem. Domyślnie pliki mają nazwę *MSBuild\<NodeId >. log*. Aby określić lokalizację plików i innych parametrów dla fileLogger, można użyć przełącznika **-fileLoggerParameters** .<br /><br /> Jeśli nazwa pliku dziennika jest nadawana przy użyciu przełącznika **-fileLoggerParameters** , rejestrator rozproszony będzie używać tej nazwy jako szablonu i dołączać identyfikator węzła do tej nazwy podczas tworzenia pliku dziennika dla każdego węzła.|
|-distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|-DL:`central logger`*`forwarding logger`|Rejestruj zdarzenia z programu MSBuild, dołączając inne wystąpienie rejestratora do każdego węzła. Aby określić wiele rejestratorów, każdy Rejestrator należy określić osobno.<br /><br /> Aby określić rejestrator, należy użyć składni rejestratora. Aby zapoznać się ze składnią rejestratora, zobacz przełącznik **-Rejestrator** poniżej.<br /><br /> W poniższych przykładach pokazano, jak używać tego przełącznika:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-fileLogger<br /><br /> *Liczba*|-FL [`number`]|Rejestruj dane wyjściowe kompilacji do jednego pliku w bieżącym katalogu. Jeśli nie określisz `number`, plik wyjściowy ma nazwę *MSBuild. log*. Jeśli określisz `number`, plik wyjściowy ma nazwę *msbuild\<n >. log*, gdzie \<n > jest `number`. `Number` może być cyfrą od 1 do 9.<br /><br /> Aby określić lokalizację pliku i inne parametry dla fileLogger, można użyć przełącznika **-fileLoggerParameters** .|
|-fileLoggerParameters: [Number]<br /><br /> `parameters`|-FLP: [`number`] `parameters`|Określa wszelkie dodatkowe parametry rejestratora plików i rozproszonego rejestratora plików. Obecność tego przełącznika oznacza, że istnieje przełącznik odpowiadający**FileLogger [** `number` **]** . `Number` może być cyfrą od 1 do 9.<br /><br /> Można użyć wszystkich parametrów, które są wymienione dla parametru **-consoleloggerparameters**. Można również użyć co najmniej jednego z następujących parametrów:<br /><br /> -   **LogFile**. Ścieżka do pliku dziennika, w którym zapisano dziennik kompilacji. Rejestrator plików rozproszonych prefiksuje ścieżkę do nazw plików dziennika.<br />-   **dołączyć**. Określa, czy dziennik kompilacji jest dołączany do pliku dziennika, czy zastępuje go. Po ustawieniu przełącznika do pliku dziennika jest dołączany dziennik kompilacji. Gdy przełącznik nie jest obecny, zawartość istniejącego pliku dziennika jest zastępowana.<br />     Jeśli dołączysz przełącznik Append bez względu na to, czy jest ustawiony na wartość true lub false, dziennik jest dołączany. Jeśli przełącznik Dołącz nie zostanie uwzględniony, Dziennik zostanie nadpisany.<br />     W takim przypadku plik jest zastępowany: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     W takim przypadku plik jest dołączany: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     W takim przypadku plik jest dołączany: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />**kodowanie**-   . Określa kodowanie pliku (na przykład UTF-8, Unicode lub ASCII).<br /><br /> Poniższy przykład generuje osobne pliki dziennika dla ostrzeżeń i błędów:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> W poniższych przykładach pokazano inne możliwości:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|-binaryLogger [: [LogFile =]`output.binlog`[; ProjectImports = [None, embed, ZipFile]]]|-BL|Serializować wszystkie zdarzenia kompilacji do skompresowanego pliku binarnego. Domyślnie plik znajduje się w bieżącym katalogu i nosi nazwę *MSBuild. binlog*. Dziennik binarny jest szczegółowym opisem procesu kompilacji, który może być później używany do odbudowy dzienników tekstowych i używanych przez inne narzędzia do analizy. Rejestr binarny jest zwykle 10-20x mniejszy niż najbardziej szczegółowy dziennik na poziomie diagnostyki, ale zawiera więcej informacji.<br /><br />Rejestrator binarny domyślnie zbiera tekst źródłowy plików projektu, w tym wszystkie zaimportowane projekty i pliki docelowe napotkane podczas kompilacji. Opcjonalny przełącznik `ProjectImports` kontroluje następujące zachowanie:<br /><br /> -   **ProjectImports=None**. Nie Zbieraj importów projektu.<br /> -   **ProjectImports = Osadź**. Osadź Importy projektu w pliku dziennika (domyślnie).<br /> -   **ProjectImports=ZipFile**. Zapisz pliki projektu, aby *\<dane wyjściowe >. projectimports. zip* , gdzie \<output > jest taka sama jak nazwa pliku dziennika binarnego.<br /><br />Ustawieniem domyślnym dla ProjectImports jest osadzanie.<br />**Uwaga**: Rejestrator nie zbiera plików źródłowych innych niż MSBuild, takich jak *CS*, *CPP* itp.<br />Plik *. binlog* może być "odtwarzany" przez przekazanie go do programu *MSBuild. exe* jako argumentu zamiast projektu/rozwiązania. Inne rejestratory otrzymają informacje zawarte w pliku dziennika, tak jakby była wykonana oryginalna kompilacja. Więcej informacji na temat dziennika binarnego i jego użycia można znaleźć pod adresem: https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Przykłady**:<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|rejestratora<br /><br /> `logger`|-l:`logger`|Określa rejestrator, który ma być używany do rejestrowania zdarzeń z programu MSBuild. Aby określić wiele rejestratorów, każdy Rejestrator należy określić osobno.<br /><br /> Użyj następującej składni dla `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Użyj następującej składni dla `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nie trzeba określać klasy rejestratora, jeśli zestaw zawiera dokładnie jeden rejestrator.<br /><br /> Użyj następującej składni `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Parametry rejestratora są opcjonalne i są przesyłane do rejestratora dokładnie w miarę ich wprowadzania.<br /><br /> W poniższych przykładach użyto przełącznika **-rejestratora** .<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
|-noconsolelogger|-noconlog|Wyłącz domyślny Rejestrator konsoli i nie Rejestruj zdarzeń w konsoli programu.|

## <a name="example"></a>Przykład
 Poniższy przykład tworzy obiekt docelowy `rebuild` projektu Project *. proj* .

```cmd
MSBuild.exe MyProject.proj -t:rebuild
```

## <a name="example"></a>Przykład
 Aby wykonywać bardziej złożone kompilacje, można użyć programu *MSBuild. exe* . Na przykład można użyć go do kompilowania określonych elementów docelowych określonych projektów w rozwiązaniu. Poniższy przykład odbudowuje projekt `NotInSolutionFolder` i czyści `InSolutionFolder`projektu, który znajduje się w folderze rozwiązania *nowyfolder* .

```cmd
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="see-also"></a>Zobacz także
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Wspólne właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
