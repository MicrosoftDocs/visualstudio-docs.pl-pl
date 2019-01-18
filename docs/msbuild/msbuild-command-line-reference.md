---
title: Odwołanie do wiersza polecenia MSBuild | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7da4af86209d5e19f48eaf4f9d8e858fc1e54257
ms.sourcegitcommit: 8c4267540c0ac39664f6902c423516f408f3cbd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54380370"
---
# <a name="msbuild-command-line-reference"></a>Dokumentacja wiersza polecenia programu MSBuild
Kiedy używasz *MSBuild.exe* do tworzenia pliku projektu lub rozwiązania, mogą obejmować kilka przełączników, aby określić różne aspekty procesu.  

Każdy parametr jest dostępny w dwóch formach:-przełącznika i /switch. Wyświetla tylko dokumentacji formularza przełącznika. 
  
## <a name="syntax"></a>Składnia  
  
```cmd  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`ProjectFile`|Tworzy obiekty docelowe w pliku projektu, który określisz. Jeśli nie określisz pliku projektu MSBuild wyszukuje bieżący katalog roboczy dla rozszerzenia nazwy pliku, który kończy się *proj* i używa tego pliku. Można również określić plik rozwiązania Visual Studio dla tego argumentu.|  
  
## <a name="switches"></a>Przełączniki  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|-help|/? lub -h|Wyświetla informacje o składni. Następujące polecenie znajduje się przykład:<br /><br /> `msbuild.exe -?`|  
|-detailedsummary|-ds|Umożliwia wyświetlenie szczegółowych informacji na końcu dziennika kompilacji konfiguracji, które zostały utworzone i jak zostały zaplanowane dla węzłów.|  
|-ignoreprojectextensions: `extensions`|-Ignoruj: `extensions`|Ignoruj określonych rozszerzeń przy określaniu którego pliku projektu do kompilacji. Użyj średnikami lub przecinkami, aby oddzielić wiele rozszerzeń, co ilustruje poniższy przykład:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|  
|-maxcpucount [:`number`]|-m[:`number`]|Określa maksymalną liczbę współbieżnych procesów do użycia podczas tworzenia. Jeśli nie dodasz tego przełącznika, wartość domyślna to 1. Jeśli dodasz tego przełącznika bez określenia wartości, program MSBuild będzie używała liczby procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Poniższy przykład powoduje, że program MSBuild, aby tworzyć zawartość przy użyciu trzech procesów programu MSBuild, która umożliwia trzy projekty przeznaczone do kompilacji w tym samym czasie:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|  
|-noautoresponse|-noautorsp|Nie zawierają żadnego *MSBuild.rsp* pliki automatycznie.|  
|-nodeReuse:`value`|-nr:`value`|Włącza lub wyłącza ponowne używanie węzłów programu MSBuild. Można określić następujące wartości:<br /><br /> -   **Wartość true,**. Węzły pozostają po zakończeniu kompilacji, tak aby kolejnych kompilacjach korzystania z nich (ustawienie domyślne).<br />-   **FALSE**. Węzły nie pozostają po zakończeniu kompilacji.<br /><br /> Węzeł odnosi się do projektu, który jest wykonywany. Jeśli dołączysz **- maxcpucount** przełącznika wiele węzłów można wykonywać jednocześnie.|  
|-nologo||Nie wyświetlaj transparentu lub komunikat o prawach autorskich.|  
|<a name="preprocess"></a> -Przetwarzanie wstępne [:`filepath`]|-pp [:`filepath`]|Utwórz plik projektu w jednym, zagregowane przez wbudowanie wszystkie pliki, które zostaną zaimportowane podczas kompilacji z ich granice oznaczone. Można użyć tego przełącznika, aby łatwiej określić pliki, które są importowane, z której pliki są importowane i które plików przyczynia się do kompilacji. Korzystając z tego przełącznika, projekt nie jest kompilowany.<br /><br /> Jeśli określisz `filepath`, plik projektu zagregowane znajduje się dane wyjściowe do pliku. W przeciwnym razie dane wyjściowe pojawia się w oknie konsoli.<br /><br /> Aby uzyskać informacje o sposobie używania `Import` element, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — element (MSBuild)](../msbuild/import-element-msbuild.md) i [jak: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|-Właściwości:`name`=`value`|-p:.`name`=`value`|Ustawianie lub zastąpienie określonej właściwości na poziomie projektu, gdzie `name` jest nazwą właściwości i `value` jest wartość właściwości. Określ każdej właściwości w oddzielnie, lub użyj średnikami lub przecinkami aby oddzielić wiele właściwości, co ilustruje poniższy przykład:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|  
|-restore|-r|Przebiegi `Restore` docelowej przed utworzeniem rzeczywistych obiektów docelowych.|
|-target:`targets`|-u:.`targets`|Twórz określonych celów w projekcie. Określ każdy element docelowy oddzielnie, lub użyj średnikami lub przecinkami do rozdzielania wielu lokalizacjach docelowych oraz jak w poniższym przykładzie pokazano:<br /><br /> `-target:Resources;Compile`<br /><br /> Jeśli określisz obiektów docelowych, za pomocą tego przełącznika, są uruchamiane zamiast wszystkie obiekty docelowe w `DefaultTargets` atrybutu w pliku projektu. Aby uzyskać więcej informacji, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md) i [jak: Określ, która docelowa do tworzenia najpierw](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Obiekt docelowy jest grupą zadań. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).|  
|-toolsversion:`version`|-tv:`version`|Określa wersję zestawu narzędzi do użycia w celu skompilowania projektu, co ilustruje poniższy przykład: `-toolsversion:3.5`<br /><br /> Za pomocą tego przełącznika, skompilowania projektu i określ wersję, która różni się od wersji, który jest określony w [Project — element (MSBuild)](../msbuild/project-element-msbuild.md). Aby uzyskać więcej informacji, zobacz [ustawienia ToolsVersion zastępowanie](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Dla programu MSBuild 4.5, należy określić następujące wartości dla `version`: w wersji 2.0 i 3.5, 4.0. Jeśli określisz 4.0, `VisualStudioVersion` właściwość kompilacji Określa które podzestawu narzędzi korzystać. Aby uzyskać więcej informacji, zobacz sekcję zestawy narzędzi Sub [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Zestaw narzędzi zawiera zadania, celów i narzędzi, które są używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie jak *csc.exe* i *vbc.exe*. Aby uzyskać więcej informacji na temat zestawy narzędzi, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [konfiguracje standardowego i niestandardowego zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md), i [Wielowersyjność](../msbuild/msbuild-multitargeting-overview.md). **Uwaga:**  Narzędzi w wersji nie jest taka sama jak platformy docelowej, która jest wersją programu .NET Framework, na której projekt jest kompilowany do uruchomienia. Aby uzyskać więcej informacji, zobacz [platformy docelowej i platformy docelowej](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|— Sprawdzanie poprawności: [`schema`]|-val [`schema`]|Sprawdź poprawność pliku projektu i, jeśli weryfikacja zakończy się powodzeniem, skompiluj projekt.<br /><br /> Jeśli nie określisz `schema`, projekt jest sprawdzana domyślny schemat.<br /><br /> Jeśli określisz `schema`, projekt jest weryfikowane względem schematu, który określisz.<br /><br /> Następujące ustawienie znajduje się przykład: `-validate:MyExtendedBuildSchema.xsd`|  
|— poziom szczegółowości:`level`|-v.`level`|Określa ilość informacji do wyświetlenia w dzienniku kompilacji. Każdy rejestrator Wyświetla zdarzenia na podstawie poziomu szczegółowości, ustawionego dla tego rejestratora.<br /><br /> Można określić następujących poziomów szczegółowości: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.<br /><br /> Następujące ustawienie znajduje się przykład: `-verbosity:quiet`|  
|-Wersja|-ver|Wyświetl tylko informacje o wersji. Projekt nie jest kompilowany.|  
|@`file`||Wstaw przełączniki wiersza polecenia z pliku tekstowego. Jeśli masz wiele plików, możesz je określić osobno. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Przełączniki rejestratorów  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|-consoleloggerparameters:<br /><br /> `parameters`|-clp:`parameters`|Przekazać parametry, które można określić do rejestratora konsoli, która wyświetla informacje o kompilacji w oknie konsoli. Można określić następujące parametry:<br /><br /> -   **PerformanceSummary**. Pokaż czas spędzony w zadania, celów i projektów.<br />-   **Podsumowanie**. Pokaż błąd i ostrzeżenie podsumowanie na końcu.<br />-   **NoSummary**. Nie pokazuj więcej błędów i ostrzeżeń podsumowanie na końcu.<br />-   **ErrorsOnly**. Pokaż tylko błędy.<br />-   **WarningsOnly**. Pokaż tylko ostrzeżenia.<br />-   **NoItemAndPropertyList**. Nie pokazuj listę elementów i właściwości, które będą widoczne na początku każdej kompilacji projektu, jeśli ustawiono poziom szczegółowości `diagnostic`.<br />-   **ShowCommandLine**. Pokaż `TaskCommandLineEvent` wiadomości.<br />-   **ShowTimestamp**. Pokaż sygnatura czasowa jako prefiks każdej wiadomości.<br />-   **ShowEventId**. Pokaż identyfikator zdarzenia dla każdego uruchomionego zdarzenia, Zakończono zdarzeń i komunikatów.<br />-   **ForceNoAlign**. Nie Wyrównaj tekst, który ma rozmiar buforu konsoli.<br />-   **DisableConsoleColor**. Dla wszystkich wiadomości rejestrowania, należy używać domyślnych kolorów konsoli.<br />-   **DisableMPLogging**. Podczas pracy w trybie bez wieloprocesorowych, należy wyłączyć styl wieloprocesorowych rejestrowania danych wyjściowych.<br />-   **EnableMPLogging**. Włącz stylu rejestrowania wieloprocesorowych, nawet wtedy, gdy jest uruchomiona w trybie bez wieloprocesorowych. Ten styl rejestrowanie jest domyślnie włączone.<br />-   **Poziom szczegółowości**. Zastąp **— poziom szczegółowości** ustawienie dla tego rejestratora.<br /><br /> Użyj średnikami lub przecinkami, aby oddzielić wiele parametrów, co ilustruje poniższy przykład:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`|  
|-distributedFileLogger|-dfl|Zaloguj się dane wyjściowe kompilacji każdego węzła program MSBuild jej własnym pliku. Położenie początkowe dla tych plików jest bieżący katalog. Domyślnie pliki są nazywane *MSBuild\<NodeId > .log*. Możesz użyć **- fileLoggerParameters** przełącznika, aby określić lokalizację plików i inne parametry fileLogger.<br /><br /> Jeśli nazwa pliku dziennika przy użyciu **- fileLoggerParameters** przełącznika, rozproszonych rejestratora użyje nazwy jako szablonu i Dołącz identyfikator węzła tej nazwy, podczas tworzenia pliku dziennika dla każdego węzła.|  
|-distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|-dl:`central logger`*`forwarding logger`|Rejestruj zdarzenia z programu MSBuild, dołączanie wystąpienia różnych rejestratora do każdego węzła. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Składnia rejestratora umożliwia określenie rejestrator. Rejestrator składnię, zobacz **-rejestratora** poniższego przełącznika.<br /><br /> W poniższych przykładach pokazano, jak używać tego przełącznika:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|-fileLogger<br /><br /> *[liczba]*|-fl[`number`]|Zaloguj się dane wyjściowe kompilacji do jednego pliku w bieżącym katalogu. Jeśli nie określisz `number`, nosi nazwę pliku wyjściowego *msbuild.log*. Jeśli określisz `number`, nosi nazwę pliku wyjściowego *msbuild\<n > .log*, gdzie \<n > jest `number`. `Number` może być cyfrę z zakresu od 1 do 9.<br /><br /> Możesz użyć **- fileLoggerParameters** przełącznika, aby określić lokalizację pliku, a inne parametry fileLogger.|  
|-fileloggerparameters: [numer]<br /><br /> `parameters`|-flp: [ `number`] `parameters`|Określa wszelkie dodatkowe parametry dla rejestratora plików i rejestratora plików rozproszonych. Obecność tego parametru oznacza, że odpowiednie -**filelogger [**`number`**]** przełącznik jest obecny. `Number` może być cyfrę z zakresu od 1 do 9.<br /><br /> Można użyć wszystkich parametrów, które są wymienione **- consoleloggerparameters**. Można również użyć co najmniej jeden z następujących parametrów:<br /><br /> -   **LogFile**. Ścieżka do pliku dziennika, w którym są zapisywane w dzienniku kompilacji. Rejestrator plików rozproszonych prefiksy tę ścieżkę do nazwy jej pliki dziennika.<br />-   **Dołącz**. Określa, czy w dzienniku kompilacji jest dołączany do pliku dziennika lub zastępuje go. Po ustawieniu przełącznika dziennika kompilacji jest dołączany do pliku dziennika. Jeśli nie ma przełącznika, zawartość istniejącego pliku dziennika zostaną zastąpione.<br />     Jeśli dołączysz przełącznik dołączania, niezależnie od tego, czy jest ustawiona na wartość true lub false, dziennik jest dołączany. Jeśli nie zostanie uwzględniony przełącznik dołączania, dziennik jest zastępowany.<br />     W takim przypadku zostanie on zastąpiony: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     W tym przypadku jest dołączany plik: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     W tym przypadku jest dołączany plik: `msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **Kodowanie**. Określa kodowanie pliku (na przykład, UTF-8, Unicode i ASCII).<br /><br /> Poniższy przykład generuje oddzielnych plików dziennika dla ostrzeżeń i błędów:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> W poniższych przykładach pokazano innych możliwości:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|  
|-binaryLogger [: [LogFile =]`output.binlog`[; ProjectImports = [None, osadzać ZipFile]]]|-bl|Serializuje wszystkich zdarzeń kompilacji do skompresowanego pliku binarnego. Domyślnie plik znajduje się w bieżącym katalogu i o nazwie *msbuild.binlog*. Dziennik binarny jest szczegółowy opis procesu kompilacji, który później może być używany na rekonstrukcję dzienniki tekstowe i używane przez inne narzędzia do analizy. Dziennik binarny jest zwykle mniejsze niż najbardziej szczegółowy dziennik tekstowy w poziomie diagnostyczne x 10-20, ale zawiera więcej informacji.<br /><br />Binarny rejestratora domyślnie zbiera tekst źródłowy pliki projektu, w tym wszystkie zaimportowane projekty i pliki docelowe, podczas kompilacji. Opcjonalny `ProjectImports` przełącznika steruje tego zachowania:<br /><br /> -   **ProjectImports=None**. Nie zbieraj Importy projektu.<br /> -   **ProjectImports=Embed**. Osadź Importy projektu w pliku dziennika (ustawienie domyślne).<br /> -   **ProjectImports=ZipFile**. Zapisz pliki projektu do  *\<dane wyjściowe >. projectimports.zip* gdzie \<dane wyjściowe > jest taka sama jak nazwa pliku dziennik binarny.<br /><br />Ustawieniem domyślnym dla ProjectImports jest osadzania.<br />**Uwaga**: Rejestrator nie są zbierane pliki źródłowe niekorzystających z programu MSBuild takich jak *.cs*, *.cpp* itp.<br />A *.binlog* pliku może być "odtwarzane" przez przekazanie jej do *msbuild.exe* jako argument zamiast projekt/rozwiązanie. Inne rejestratorów otrzyma informacje zawarte w pliku dziennika, tak, jakby działo oryginalnego kompilacji. Możesz dowiedzieć się więcej o dziennik binarny i jego użycia na: https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Przykłady**:<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-rejestratora:<br /><br /> `logger`|-l:.`logger`|Określa Rejestrator służące do rejestrowania zdarzeń z programu MSBuild. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Należy użyć następującej składni dla `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Należy użyć następującej składni dla `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nie trzeba określić klasę rejestratora, jeśli zestaw zawiera dokładnie jeden rejestratora.<br /><br /> Należy użyć następującej składni dla `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Rejestrator parametry są opcjonalne i są przekazywane do rejestratora, dokładnie tak, jak wprowadzisz je.<br /><br /> W poniższych przykładach używane **-rejestratora** przełącznika.<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|-noconsolelogger|-noconlog|Wyłącz rejestratora konsoli do domyślnej, a nie Rejestruj zdarzenia do konsoli.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `rebuild` celem *MyProject.proj* projektu.  
  
```cmd  
MSBuild.exe MyProject.proj -t:rebuild  
```  
  
## <a name="example"></a>Przykład  
 Możesz użyć *MSBuild.exe* do wykonywania bardziej złożonych kompilacji. Na przykład służy do tworzenia określonych obiektów docelowych określonych projektów w rozwiązaniu. Poniższy przykład ponownie kompiluje projekt `NotInSolutionFolder` i czyści projektu `InSolutionFolder`, która znajduje się w *Nowyfolder* folderu rozwiązania.  
  
```cmd  
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
