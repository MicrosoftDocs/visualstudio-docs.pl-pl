---
title: Informacje w wierszu polecenia programu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181055"
---
# <a name="msbuild-command-line-reference"></a>Informacje w wierszu polecenia programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy używasz MSBuild.exe do kompilowania pliku projektu lub rozwiązania, możesz dołączyć kilka przełączników, aby określić różne aspekty procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`ProjectFile`|Kompiluje obiekty docelowe w pliku projektu, który określisz. Jeśli nie określisz pliku projektu, MSBuild przeszukuje bieżący katalog roboczy dla rozszerzenia nazwy pliku kończącego się na "proj" i używa tego pliku. Możesz również określić plik rozwiązania programu Visual Studio dla tego argumentu.|  
  
## <a name="switches"></a>Przełączniki  
  
|Przełącznik|Forma krótka|Opis|  
|------------|----------------|-----------------|  
|/help|/? lub/h|Wyświetla informacje o użyciu. Następujące polecenie jest przykładem:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ ds|Pokaż szczegółowe informacje na końcu dziennika kompilacji dotyczące konfiguracji, które zostały skompilowane i w jaki sposób zostały zaplanowane do węzłów.|  
|/ignoreprojectextensions: `extensions`|/Ignore `extensions`|Ignoruj określone rozszerzenia podczas określania pliku projektu do skompilowania. Użyj średnika lub przecinka do oddzielenia wielu rozszerzeń, jak pokazano na poniższym przykładzie:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount [: `number` ]|/m [: `number` ]|Określa maksymalną liczbę współbieżnych procesów, które mają być używane podczas kompilowania. Jeśli ten przełącznik nie zostanie uwzględniony, wartość domyślna to 1. Jeśli ten przełącznik zostanie uwzględniony bez określenia wartości, program MSBuild użyje do liczby procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> W poniższym przykładzie nakazuje programowi MSBuild Kompilowanie przy użyciu trzech procesów MSBuild, co umożliwia kompilowanie w tym samym czasie trzech projektów:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|Nie dołączaj żadnych plików MSBuild. rsp automatycznie.|  
|/nodeReuse:`value`|Nr`value`|Włącza lub wyłącza ponowne korzystanie z węzłów programu MSBuild. Można określić następujące wartości:<br /><br /> -   **Wartość true**. Węzły pozostają po zakończeniu kompilacji, tak aby kolejne kompilacje mogły ich używać (domyślnie).<br />-   **Wartość false**. Węzły nie pozostają po zakończeniu kompilacji.<br /><br /> Węzeł odpowiada projektowi, który jest wykonywany. Jeśli dołączysz przełącznik **/maxcpucount** , wiele węzłów może być wykonywanych współbieżnie.|  
|/nologo||Nie wyświetlaj transparentu startowego ani komunikatu o prawach autorskich.|  
|/preprocess [: `filepath` ]|/PP [: `filepath` ]|Utwórz pojedynczy, zagregowany plik projektu, określając wszystkie pliki, które zostaną zaimportowane podczas kompilacji, z oznaczeniem ich granic. Możesz użyć tego przełącznika, aby łatwiej określić, które pliki są importowane, skąd mają być importowane pliki, i które pliki współtworzą kompilację. Gdy używasz tego przełącznika, projekt nie jest skompilowany.<br /><br /> Jeśli określisz `filepath` , zagregowany plik projektu jest wyprowadzany do pliku. W przeciwnym razie dane wyjściowe pojawiają się w oknie konsoli.<br /><br /> Aby uzyskać informacje o sposobach używania `Import` elementu do wstawiania pliku projektu do innego pliku projektu, zobacz [Importowanie elementu (MSBuild)](../msbuild/import-element-msbuild.md) i [instrukcje: Użyj tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|wartość`name`=`value`|/p`name`=`value`|Ustaw lub Zastąp określone właściwości na poziomie projektu, gdzie `name` jest nazwą właściwości i `value` jest wartością właściwości. Określ każdą właściwość osobno lub Użyj średnika lub przecinka do oddzielenia wielu właściwości, jak pokazano na poniższym przykładzie:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/Target`targets`|/t`targets`|Kompiluj określone elementy docelowe w projekcie. Każdy element docelowy należy określić osobno lub użyć średnika lub przecinka do oddzielenia wielu elementów docelowych, jak pokazano na poniższym przykładzie:<br /><br /> `/target:Resources;Compile`<br /><br /> W przypadku określenia dowolnych elementów docelowych przy użyciu tego przełącznika są one uruchamiane zamiast jakichkolwiek obiektów docelowych w `DefaultTargets` atrybucie w pliku projektu. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md) i [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Obiekt docelowy jest grupą zadań. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md).|  
|ToolsVersion`version`|grań`version`|Określa wersję zestawu narzędzi do użycia w celu skompilowania projektu, jak pokazano w poniższym przykładzie: `/toolsversion:3.5`<br /><br /> Za pomocą tego przełącznika można skompilować projekt i określić wersję, która różni się od wersji określonej w [elemencie projektu (MSBuild)](../msbuild/project-element-msbuild.md). Aby uzyskać więcej informacji, zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Dla programu MSBuild 4,5 można określić następujące wartości dla `version` : 2,0, 3,5 i 4,0. Jeśli określisz 4,0, `VisualStudioVersion` Właściwość Build określa, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz sekcję podzestawy narzędzi zestawu [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Zestaw narzędzi składa się z zadań, obiektów docelowych i narzędzi, które są używane do kompilowania aplikacji. Narzędzia obejmują kompilatory, takie jak csc.exe i vbc.exe. Więcej informacji o zestawach narzędzi można znaleźć w temacie zestaw narzędzi [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardowa i niestandardowa konfiguracja zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)i wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md). **Uwaga:**  Wersja zestawu narzędzi nie jest taka sama jak platforma docelowa, która jest wersją .NET Framework, w której projekt został skompilowany do uruchomienia. Aby uzyskać więcej informacji, zobacz [Target Framework i Target platform](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/Validate: [ `schema` ]|/Val [ `schema` ]|Sprawdź poprawność pliku projektu i, jeśli Walidacja zakończyła się powodzeniem, Skompiluj projekt.<br /><br /> Jeśli nie określisz `schema` , projekt zostanie sprawdzony pod kątem domyślnego schematu.<br /><br /> Jeśli określisz `schema` , projekt zostanie sprawdzony pod kątem schematu, który określisz.<br /><br /> Oto przykład: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity.`level`|przełącznika`level`|Określa ilość informacji, które mają być wyświetlane w dzienniku kompilacji. Każdy Rejestrator wyświetla zdarzenia na podstawie poziomu szczegółowości ustawionych dla tego rejestratora.<br /><br /> Można określić następujące poziomy szczegółowości: `q[uiet]` , `m[inimal]` ,, `n[ormal]` `d[etailed]` i `diag[nostic]` .<br /><br /> Oto przykład: `/verbosity:quiet`|  
|/Version|/ver|Wyświetlaj tylko informacje o wersji. Projekt nie został skompilowany.|  
|@`file`||Wstaw przełączniki wiersza polecenia z pliku tekstowego. Jeśli masz wiele plików, należy je określić osobno. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Przełączniki rejestratorów  
  
|Przełącznik|Forma krótka|Opis|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Przekaż parametry, które określisz, do rejestratora konsoli, który wyświetla informacje o kompilacji w oknie konsoli. Można określić następujące parametry:<br /><br /> -   **PerformanceSummary**. Pokazuje czas spędzony w zadaniach, obiektach docelowych i projektach.<br />-   **Podsumowanie**. Pokaż na końcu podsumowanie błędu i ostrzeżenia.<br />-   **Nosummary**. Nie pokazuj więcej informacji na temat błędu i ostrzeżenia na końcu.<br />-   **ErrorsOnly**. Pokaż tylko błędy.<br />-   **WarningsOnly**. Pokaż tylko ostrzeżenia.<br />-   **NoItemAndPropertyList**. Nie pokazuj listy elementów i właściwości, które pojawią się na początku każdej kompilacji projektu, jeśli poziom szczegółowości jest ustawiony na `diagnostic` .<br />-   **ShowCommandLine**. Pokaż `TaskCommandLineEvent` komunikaty.<br />-   **ShowTimestamp**. Pokaż sygnaturę czasową jako prefiks do dowolnej wiadomości.<br />-   **ShowEventId**. Pokaż identyfikator zdarzenia dla każdego zdarzenia uruchomionego, gotowego zdarzenia i komunikatu.<br />-   **ForceNoAlign**. Nie Wyrównaj tekstu do rozmiaru buforu konsoli.<br />-   **DisableConsoleColor**. Użyj domyślnych kolorów konsoli dla wszystkich komunikatów rejestrowania.<br />-   **DisableMPLogging**. Wyłącz styl rejestrowania wieloprocesorowego danych wyjściowych podczas uruchamiania w trybie non-procesorowym.<br />-   **EnableMPLogging**. Włącz styl rejestrowania wieloprocesorowego nawet w przypadku uruchamiania w trybie innym niż tryb wieloprocesorowy. Ten styl rejestrowania jest domyślnie włączony.<br />-   **Poziom szczegółowości**. Zastąp ustawienie **/verbosity.** dla tego rejestratora.<br /><br /> Użyj średnika lub przecinka do oddzielenia wielu parametrów, jak pokazano na poniższym przykładzie:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Rejestruj dane wyjściowe kompilacji każdego węzła programu MSBuild do własnego pliku. Początkowa lokalizacja tych plików jest bieżącym katalogiem. Domyślnie pliki są nazywane "MSBuild*NodeId*. log". Aby określić lokalizację plików i innych parametrów dla fileLogger, można użyć przełącznika **/fileLoggerParameters** .<br /><br /> Jeśli nazwa pliku dziennika zostanie nadana przy użyciu przełącznika **/fileLoggerParameters** , program obsługujący Rejestrator będzie używać tej nazwy jako szablonu i dołączać identyfikator węzła do tej nazwy podczas tworzenia pliku dziennika dla każdego węzła.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|listy dystrybucyjnej`central logger`*`forwarding logger`|Rejestruj zdarzenia z programu MSBuild, dołączając inne wystąpienie rejestratora do każdego węzła. Aby określić wiele rejestratorów, każdy Rejestrator należy określić osobno.<br /><br /> Aby określić rejestrator, należy użyć składni rejestratora. Aby zapoznać się ze składnią rejestratora, zobacz przełącznik **/Logger** poniżej.<br /><br /> W poniższych przykładach pokazano, jak używać tego przełącznika:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *Liczba*|/FL [ `number` ]|Rejestruj dane wyjściowe kompilacji do jednego pliku w bieżącym katalogu. Jeśli nie zostanie określony `number` , plik wyjściowy ma nazwę MSBuild. log. Jeśli określisz `number` , plik wyjściowy ma nazwę MSBuild `n` . log, gdzie n to `number` . `Number` może być cyfrą od 1 do 9.<br /><br /> Możesz użyć przełącznika **/fileLoggerParameters** , aby określić lokalizację pliku i inne parametry dla FileLogger.|  
|/fileLoggerParameters: [Number]<br /><br /> `parameters`|/FLP: [ `number` ] `parameters`|Określa wszelkie dodatkowe parametry rejestratora plików i rozproszonego rejestratora plików. Obecność tego przełącznika oznacza, że istnieje przełącznik odpowiadający/**FileLogger [** `number` **]** . `Number` może być cyfrą od 1 do 9.<br /><br /> Można użyć wszystkich parametrów, które są wymienione dla **/consoleloggerparameters**. Można również użyć co najmniej jednego z następujących parametrów:<br /><br /> -   **Plik dziennika**. Ścieżka do pliku dziennika, w którym zapisano dziennik kompilacji. Rejestrator plików rozproszonych prefiksuje ścieżkę do nazw plików dziennika.<br />-   **Dołącz**. Określa, czy dziennik kompilacji jest dołączany do pliku dziennika, czy zastępuje go. Po ustawieniu przełącznika do pliku dziennika jest dołączany dziennik kompilacji. Gdy przełącznik nie jest obecny, zawartość istniejącego pliku dziennika jest zastępowana.<br />     Jeśli dołączysz przełącznik Append bez względu na to, czy jest ustawiony na wartość true lub false, dziennik jest dołączany. Jeśli przełącznik Dołącz nie zostanie uwzględniony, Dziennik zostanie nadpisany.<br />     W takim przypadku plik jest zastępowany: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     W takim przypadku plik jest dołączany: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     W takim przypadku plik jest dołączany: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kodowanie**. Określa kodowanie pliku (na przykład UTF-8, Unicode lub ASCII).<br /><br /> Poniższy przykład generuje osobne pliki dziennika dla ostrzeżeń i błędów:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> W poniższych przykładach pokazano inne możliwości:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|rejestratora<br /><br /> `logger`|przełącznika`logger`|Określa rejestrator, który ma być używany do rejestrowania zdarzeń z programu MSBuild. Aby określić wiele rejestratorów, każdy Rejestrator należy określić osobno.<br /><br /> Użyj następującej składni dla `logger` : `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Użyj następującej składni dla `LoggerClass` : `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nie trzeba określać klasy rejestratora, jeśli zestaw zawiera dokładnie jeden rejestrator.<br /><br /> Użyj następującej składni dla `LoggerAssembly` : `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Parametry rejestratora są opcjonalne i są przesyłane do rejestratora dokładnie w miarę ich wprowadzania.<br /><br /> W poniższych przykładach użyto przełącznika **/Logger** .<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Wyłącz domyślny Rejestrator konsoli i nie Rejestruj zdarzeń w konsoli programu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `rebuild` obiekt docelowy `MyProject.proj` projektu.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Przykład  
 Za pomocą MSBuild.exe można wykonywać bardziej złożone kompilacje. Na przykład można użyć go do kompilowania określonych elementów docelowych określonych projektów w rozwiązaniu. Poniższy przykład odbudowuje projekt `NotInSolutionFolder` i czyści projekt `InSolutionFolder` , który znajduje się w `NewFolder` folderze rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Wspólne właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
