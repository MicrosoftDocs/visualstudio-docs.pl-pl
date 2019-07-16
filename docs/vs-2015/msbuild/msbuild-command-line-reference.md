---
title: Odwołanie do wiersza polecenia MSBuild | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181055"
---
# <a name="msbuild-command-line-reference"></a>Informacje w wierszu polecenia programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia pliku projektu lub rozwiązania za MSBuild.exe, można dołączyć kilka przełączników, aby określić różne aspekty procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`ProjectFile`|Tworzy obiekty docelowe w pliku projektu, który określisz. Jeśli nie określisz pliku projektu MSBuild wyszukuje bieżący katalog roboczy dla rozszerzenia nazwy pliku, kończy się na "proj", która korzysta z tego pliku. Można również określić plik rozwiązania Visual Studio dla tego argumentu.|  
  
## <a name="switches"></a>Przełączniki  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|/help|/? lub/h|Wyświetla informacje o składni. Następujące polecenie znajduje się przykład:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|Umożliwia wyświetlenie szczegółowych informacji na końcu dziennika kompilacji konfiguracji, które zostały utworzone i jak zostały zaplanowane dla węzłów.|  
|/ignoreprojectextensions: `extensions`|/ ignore: `extensions`|Ignoruj określonych rozszerzeń przy określaniu którego pliku projektu do kompilacji. Użyj średnikami lub przecinkami, aby oddzielić wiele rozszerzeń, co ilustruje poniższy przykład:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/ maxcpucount [:`number`]|/m[:`number`]|Określa maksymalną liczbę współbieżnych procesów do użycia podczas tworzenia. Jeśli nie dodasz tego przełącznika, wartość domyślna to 1. Jeśli dodasz tego przełącznika bez określenia wartości, program MSBuild będzie używała liczby procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Poniższy przykład powoduje, że program MSBuild, aby tworzyć zawartość przy użyciu trzech procesów programu MSBuild, która umożliwia trzy projekty przeznaczone do kompilacji w tym samym czasie:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/ noautoresponse|/noautorsp|Wszystkie pliki MSBuild.rsp nie są automatycznie dołączane.|  
|/nodeReuse:`value`|/nr:`value`|Włącza lub wyłącza ponowne używanie węzłów programu MSBuild. Można określić następujące wartości:<br /><br /> -   **Wartość true,** . Węzły pozostają po zakończeniu kompilacji, tak aby kolejnych kompilacjach korzystania z nich (ustawienie domyślne).<br />-   **FALSE**. Węzły nie pozostają po zakończeniu kompilacji.<br /><br /> Węzeł odnosi się do projektu, który jest wykonywany. Jeśli dołączysz **/maxcpucount** przełącznika wiele węzłów można wykonywać jednocześnie.|  
|/nologo||Nie wyświetlaj transparentu lub komunikat o prawach autorskich.|  
|/ Przetwarzanie wstępne [:`filepath`]|/PP [:`filepath`]|Utwórz plik projektu w jednym, zagregowane przez wbudowanie wszystkie pliki, które zostaną zaimportowane podczas kompilacji z ich granice oznaczone. Można użyć tego przełącznika, aby łatwiej określić pliki, które są importowane, z której pliki są importowane i które plików przyczynia się do kompilacji. Korzystając z tego przełącznika, projekt nie jest kompilowany.<br /><br /> Jeśli określisz `filepath`, plik projektu zagregowane znajduje się dane wyjściowe do pliku. W przeciwnym razie dane wyjściowe pojawia się w oknie konsoli.<br /><br /> Aby uzyskać informacje o sposobie używania `Import` element, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md) i [jak: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/Property:`name`=`value`|/ p:`name`=`value`|Ustawianie lub zastąpienie określonej właściwości na poziomie projektu, gdzie `name` jest nazwą właściwości i `value` jest wartość właściwości. Określ każdej właściwości w oddzielnie, lub użyj średnikami lub przecinkami aby oddzielić wiele właściwości, co ilustruje poniższy przykład:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/ target:`targets`|t:`targets`|Twórz określonych celów w projekcie. Określ każdy element docelowy oddzielnie, lub użyj średnikami lub przecinkami do rozdzielania wielu lokalizacjach docelowych oraz jak w poniższym przykładzie pokazano:<br /><br /> `/target:Resources;Compile`<br /><br /> Jeśli określisz obiektów docelowych, za pomocą tego przełącznika, są uruchamiane zamiast wszystkie obiekty docelowe w `DefaultTargets` atrybutu w pliku projektu. Aby uzyskać więcej informacji, zobacz [kolejności kompilacji docelowej](../msbuild/target-build-order.md) i [jak: Określanie pierwszego obiektu docelowego do kompilacji](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Obiekt docelowy jest grupą zadań. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/tv:`version`|Określa wersję zestawu narzędzi do użycia w celu skompilowania projektu, co ilustruje poniższy przykład: `/toolsversion:3.5`<br /><br /> Za pomocą tego przełącznika, skompilowania projektu i określ wersję, która różni się od wersji, który jest określony w [Project — Element (MSBuild)](../msbuild/project-element-msbuild.md). Aby uzyskać więcej informacji, zobacz [zastępowanie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Dla programu MSBuild 4.5, należy określić następujące wartości dla `version`: w wersji 2.0 i 3.5, 4.0. Jeśli określisz 4.0, `VisualStudioVersion` właściwość kompilacji Określa które podzestawu narzędzi korzystać. Aby uzyskać więcej informacji, zobacz sekcję zestawy narzędzi Sub [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Zestaw narzędzi zawiera zadania, celów i narzędzi, które są używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie jak csc.exe i vbc.exe. Aby uzyskać więcej informacji na temat zestawy narzędzi, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardowego i niestandardowego zestawu narzędzi konfiguracji](../msbuild/standard-and-custom-toolset-configurations.md), i [Wielowersyjność](../msbuild/msbuild-multitargeting-overview.md). **Uwaga:**  Narzędzi w wersji nie jest taka sama jak platformy docelowej, która jest wersją programu .NET Framework, na której projekt jest kompilowany do uruchomienia. Aby uzyskać więcej informacji, zobacz [platformy docelowej i platformy docelowej](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/ validate: [`schema`]|/Val [`schema`]|Sprawdź poprawność pliku projektu i, jeśli weryfikacja zakończy się powodzeniem, skompiluj projekt.<br /><br /> Jeśli nie określisz `schema`, projekt jest sprawdzana domyślny schemat.<br /><br /> Jeśli określisz `schema`, projekt jest weryfikowane względem schematu, który określisz.<br /><br /> Następujące ustawienie znajduje się przykład: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|Określa ilość informacji do wyświetlenia w dzienniku kompilacji. Każdy rejestrator Wyświetla zdarzenia na podstawie poziomu szczegółowości, ustawionego dla tego rejestratora.<br /><br /> Można określić następujących poziomów szczegółowości: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.<br /><br /> Następujące ustawienie znajduje się przykład: `/verbosity:quiet`|  
|/ Version|/ VER|Wyświetl tylko informacje o wersji. Projekt nie jest kompilowany.|  
|@`file`||Wstaw przełączniki wiersza polecenia z pliku tekstowego. Jeśli masz wiele plików, możesz je określić osobno. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Przełączniki rejestratorów  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/CLP:`parameters`|Przekazać parametry, które można określić do rejestratora konsoli, która wyświetla informacje o kompilacji w oknie konsoli. Można określić następujące parametry:<br /><br /> -   **PerformanceSummary**. Pokaż czas spędzony w zadania, celów i projektów.<br />-   **Podsumowanie**. Pokaż błąd i ostrzeżenie podsumowanie na końcu.<br />-   **NoSummary**. Nie pokazuj więcej błędów i ostrzeżeń podsumowanie na końcu.<br />-   **ErrorsOnly**. Pokaż tylko błędy.<br />-   **WarningsOnly**. Pokaż tylko ostrzeżenia.<br />-   **NoItemAndPropertyList**. Nie pokazuj listę elementów i właściwości, które będą widoczne na początku każdej kompilacji projektu, jeśli ustawiono poziom szczegółowości `diagnostic`.<br />-   **ShowCommandLine**. Pokaż `TaskCommandLineEvent` wiadomości.<br />-   **ShowTimestamp**. Pokaż sygnatura czasowa jako prefiks każdej wiadomości.<br />-   **ShowEventId**. Pokaż identyfikator zdarzenia dla każdego uruchomionego zdarzenia, Zakończono zdarzeń i komunikatów.<br />-   **ForceNoAlign**. Nie Wyrównaj tekst, który ma rozmiar buforu konsoli.<br />-   **DisableConsoleColor**. Dla wszystkich wiadomości rejestrowania, należy używać domyślnych kolorów konsoli.<br />-   **DisableMPLogging**. Podczas pracy w trybie bez wieloprocesorowych, należy wyłączyć styl wieloprocesorowych rejestrowania danych wyjściowych.<br />-   **EnableMPLogging**. Włącz stylu rejestrowania wieloprocesorowych, nawet wtedy, gdy jest uruchomiona w trybie bez wieloprocesorowych. Ten styl rejestrowanie jest domyślnie włączone.<br />-   **Poziom szczegółowości**. Zastąp **/verbosity** ustawienie dla tego rejestratora.<br /><br /> Użyj średnikami lub przecinkami, aby oddzielić wiele parametrów, co ilustruje poniższy przykład:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Zaloguj się dane wyjściowe kompilacji każdego węzła program MSBuild jej własnym pliku. Położenie początkowe dla tych plików jest bieżący katalog. Domyślnie pliki są nazywane "MSBuild*NodeId*log". Możesz użyć **/fileLoggerParameters** przełącznika, aby określić lokalizację plików i inne parametry fileLogger.<br /><br /> Jeśli nazwa pliku dziennika przy użyciu **/fileLoggerParameters** przełącznika, rozproszonych rejestratora użyje nazwy jako szablonu i Dołącz identyfikator węzła tej nazwy, podczas tworzenia pliku dziennika dla każdego węzła.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/DL:`central logger`*`forwarding logger`|Rejestruj zdarzenia z programu MSBuild, dołączanie wystąpienia różnych rejestratora do każdego węzła. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Składnia rejestratora umożliwia określenie rejestrator. Rejestrator składnię, zobacz **/logger** poniższego przełącznika.<br /><br /> W poniższych przykładach pokazano, jak używać tego przełącznika:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[liczba]*|/fl[`number`]|Zaloguj się dane wyjściowe kompilacji do jednego pliku w bieżącym katalogu. Jeśli nie określisz `number`, plik wyjściowy nosi nazwę msbuild.log. Jeśli określisz `number`, plik wyjściowy nosi nazwę msbuild`n`.log, gdzie n to `number`. `Number` może być cyfrę z zakresu od 1 do 9.<br /><br /> Możesz użyć **/fileLoggerParameters** przełącznika, aby określić lokalizację pliku, a inne parametry fileLogger.|  
|/fileloggerparameters: [numer]<br /><br /> `parameters`|/FLP: [ `number`] `parameters`|Określa wszelkie dodatkowe parametry dla rejestratora plików i rejestratora plików rozproszonych. Obecność tego parametru oznacza, że odpowiednie /**filelogger [** `number` **]** przełącznik jest obecny. `Number` może być cyfrę z zakresu od 1 do 9.<br /><br /> Można użyć wszystkich parametrów, które są wymienione **/consoleloggerparameters**. Można również użyć co najmniej jeden z następujących parametrów:<br /><br /> -   **Plik dziennika**. Ścieżka do pliku dziennika, w którym są zapisywane w dzienniku kompilacji. Rejestrator plików rozproszonych prefiksy tę ścieżkę do nazwy jej pliki dziennika.<br />-   **Dołącz**. Określa, czy w dzienniku kompilacji jest dołączany do pliku dziennika lub zastępuje go. Po ustawieniu przełącznika dziennika kompilacji jest dołączany do pliku dziennika. Jeśli nie ma przełącznika, zawartość istniejącego pliku dziennika zostaną zastąpione.<br />     Jeśli dołączysz przełącznik dołączania, niezależnie od tego, czy jest ustawiona na wartość true lub false, dziennik jest dołączany. Jeśli nie zostanie uwzględniony przełącznik dołączania, dziennik jest zastępowany.<br />     W takim przypadku zostanie on zastąpiony: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     W tym przypadku jest dołączany plik: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     W tym przypadku jest dołączany plik: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kodowanie**. Określa kodowanie pliku (na przykład, UTF-8, Unicode i ASCII).<br /><br /> Poniższy przykład generuje oddzielnych plików dziennika dla ostrzeżeń i błędów:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> W poniższych przykładach pokazano innych możliwości:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/Logger:<br /><br /> `logger`|/ l: wyświetlenie`logger`|Określa Rejestrator służące do rejestrowania zdarzeń z programu MSBuild. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Należy użyć następującej składni dla `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Należy użyć następującej składni dla `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nie trzeba określić klasę rejestratora, jeśli zestaw zawiera dokładnie jeden rejestratora.<br /><br /> Należy użyć następującej składni dla `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Rejestrator parametry są opcjonalne i są przekazywane do rejestratora, dokładnie tak, jak wprowadzisz je.<br /><br /> W poniższych przykładach używane **/logger** przełącznika.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Wyłącz rejestratora konsoli do domyślnej, a nie Rejestruj zdarzenia do konsoli.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `rebuild` celem `MyProject.proj` projektu.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Przykład  
 MSBuild.exe służy do wykonywania bardziej złożonych kompilacji. Na przykład służy do tworzenia określonych obiektów docelowych określonych projektów w rozwiązaniu. Poniższy przykład ponownie kompiluje projekt `NotInSolutionFolder` i czyści projektu `InSolutionFolder`, która znajduje się w `NewFolder` folderu rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
