---
title: Wspólne właściwości projektów MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f5c7c2f587f4c2fb44ab56223dafa2f988c6103
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758473"
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektów MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Następująca tabela zawiera listę często używanych właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w plikach .targets, dostarczanych przez program MSBuild.  
  
 Pliki projektu w programie Visual Studio (.csproj, .vbproj, vcxproj i inne) zawierają kod MSBuild XML, który jest uruchamiany, gdy tworzysz projekt za pomocą IDE. Projekty zazwyczaj importują jeden lub więcej plików .targets, aby zdefiniować ich proces kompilacji. Aby uzyskać więcej informacji, zobacz [. Jest przeznaczony dla plików](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów  
  
|Nazwa właściwości lub parametru|Opis|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Określa dodatkowe foldery, w których kompilatory mają szukać zestawów odwołań.|  
|AddModules|Powoduje, że kompilator udostępnia wszystkie typy informacji z określonych plików kompilowanemu projektowi. Ta właściwość jest równoważna `/addModules` przełącznika kompilatora.|  
|ALToolPath|Ścieżka, gdzie można znaleźć AL.exe. Ta właściwość zastępuje bieżącą wersję programu AL.exe w celu umożliwienia korzystania z innej wersji.|  
|ApplicationIcon|Plik ikony .ico do przekazania do kompilatora w celu osadzenia jako ikona Win32. Właściwość jest równoważna `/win32icon` przełącznika kompilatora.|  
|ApplicationManifest|Określa ścieżkę do pliku, który jest używany do generowania zewnętrznych informacji manifestu kontroli konta użytkownika (UAC). Ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../includes/windowsver-md.md)].<br /><br /> W większości przypadków manifest jest osadzony. Jednak jeśli używasz rejestracji wolnego modelu COM lub [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia, a następnie manifest może być plik zewnętrzny, instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji zobacz Omówienie właściwości NoWin32Manifest w tym temacie.|  
|AssemblyOriginatorKeyFile|Określa plik, który jest używany do podpisywania zestawu (.snk lub pfx) i który jest przekazywany do [resolvekeysource — zadanie](../msbuild/resolvekeysource-task.md) do wygenerowania klucza rzeczywistego, który jest używany do podpisywania zestawu.|  
|AssemblySearchPaths|Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność wyświetlania ścieżek na tej liście ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami.|  
|AssemblyName|Nazwa zestawu pliku wyjściowego po utworzeniu projektu.|  
|BaseAddress|Określa adres bazowy głównego zestawu wyjścia. Ta właściwość jest równoważna `/baseaddress` przełącznika kompilatora.|  
|BaseOutputPath|Określa podstawową ścieżkę dla pliku wyjściowego. Jeśli je skonfigurowano, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] użyje `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykład składni: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Folder najwyższego poziomu, w których wszystkie specyficznych dla konfiguracji pośrednie foldery wynikowe są tworzone. Wartość domyślna to `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Wartość logiczna, która wskazuje, czy odwołania do projektu są wbudowane lub czyszczone równolegle, kiedy wieloprocesowym [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] jest używany. Wartość domyślna to `true`, co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów.|  
|BuildProjectReferences|Wartość logiczna, która wskazuje, czy odwołania w projekcie są kompilowane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Ustaw `false` Jeśli tworzysz projekt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE), `true` Jeśli inaczej.|  
|CleanFile|Nazwa pliku, który będzie używany jako "clean cache". Wyczyść pamięć podręczną znajduje się lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczony w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce.|  
|CodePage|Określa stronę kodową dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna `/codepage` przełącznika kompilatora.|  
|CompilerResponseFile|Opcjonalny plik odpowiedzi, który może być przekazywany do zadań kompilatora.|  
|Konfiguracja|Konfiguracja, który jest kompilowany "Debug" lub "Wersja".|  
|CscToolPath|Ścieżka csc.exe, [!INCLUDE[csprcs](../includes/csprcs-md.md)] kompilatora.|  
|CustomBeforeMicrosoftCommonTargets|Nazwa pliku projektu lub pliku obiektów docelowych, który ma być importowane automatycznie przed zaimportowaniem wspólnych obiektów docelowych.|  
|DebugSymbols|Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **/p:DebugSymbols = false** w wierszu poleceń wyłącza Generowanie plików symboli (.pdb) w bazie danych programu.|  
|DefineConstants|Definiuje stałe warunkowe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określane przy użyciu następującej składni:<br /><br /> *symbol1 = wartość1; Symbol2 = wartość2*<br /><br /> Właściwość jest równoważna `/define` przełącznika kompilatora.|  
|DefineDebug|Wartość logiczna wskazująca, czy chcesz, aby stała DEBUG była zdefiniowana.|  
|DefineTrace|Wartość logiczna wskazująca, czy chcesz, aby stała TRACE była zdefiniowana.|  
|DebugType|Definiuje poziom informacji debugowania, które mają być generowane. Prawidłowe wartości to "full", "pdbonly" i "none".|  
|DelaySign|Wartość logiczna wskazująca, czy chcesz Opóźnij podpisanie zestawu zamiast pełnego podpisywania.|  
|DisabledWarnings|Pomija określone ostrzeżenia. Musi być określona tylko część numeryczna identyfikatora ostrzeżenia. Wielokrotne ostrzeżenia są oddzielone średnikami. Ten parametr odnosi się do `/nowarn` przełącznika kompilatora vbc.exe.|  
|DisableFastUpToDateCheck|Wartość logiczna, która ma zastosowanie do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tylko. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kompilacji manager używa procesu o nazwie FastUpToDateCheck, aby ustalić, czy projekt musi zostać zrekompilowany, aby być na bieżąco. Ten proces jest szybszy niż używanie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Aby to ustalić. Ustawienie właściwości DisableFastUpToDateCheck na `true` pozwala ominąć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Menedżer kompilacji i wymusić użycie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do określenia, czy projekt jest aktualny.|  
|DocumentationFile|Nazwa pliku, który zostanie wygenerowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie ma ścieżki informacji.|  
|ErrorReport|Określa, jak zadanie kompilatora powinno zgłosić wewnętrzne błędy kompilatora. Prawidłowe wartości to "prompt", "Wyślij" lub "none". Ta właściwość jest równoważna `/errorreport` przełącznika kompilatora.|  
|ExcludeDeploymentUrl|[Generatedeploymentmanifest — zadanie](../msbuild/generatedeploymentmanifest-task.md) spowoduje dodanie znacznika deploymentProvider do manifestu wdrażania, jeśli plik projektu zawiera któreś z następujących elementów:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl, jednak uniemożliwia znacznik deploymentProvider dodawane do pliku manifestu wdrożenia, nawet jeśli żadnego z powyższych adresów URL są określone. Aby to zrobić, dodaj następującą właściwość w pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` **Uwaga:**  ExcludeDeploymentUrl nie jest dostępny w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE i można go ustawić tylko przez ręczną edycję pliku projektu. Ustawienie tej właściwości nie wpływa na publikowanie w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; oznacza to, że znacznik deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl.|  
|FileAlignment|Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192. Ta właściwość jest równoważna `/filealignment` przełącznika kompilatora.|  
|FrameworkPathOverride|Określa lokalizację mscorlib.dll i microsoft.visualbasic.dll. Ten parametr jest równoważny `/sdkpath` przełącznika kompilatora vbc.exe.|  
|GenerateDocumentation|Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true`, kompilacja generuje informacje o dokumentacji i umieszcza go w pliku XML wraz z nazwą pliku wykonywalnego lub biblioteki, utworzonego przez zadanie kompilacji.|  
|IntermediateOutputPath|Pełna pośrednia ścieżka wyjściowa wyprowadzana z `BaseIntermediateOutputPath`, jeśli nie określono ścieżki. Na przykład \obj\debug\\. Jeśli ta wartość zostanie zastąpiona, ustawienie `BaseIntermediateOutputPath` nie ma wpływu.|  
|KeyContainerName|Nazwa kontenera klucza silnej nazwy.|  
|KeyOriginatorFile|Nazwa pliku klucza silnej nazwy.|  
|NoWin32Manifest|Określa, czy kompilator generuje domyślny manifest Win32 w zestawie danych wyjściowych. Wartość domyślna `false` oznacza, że domyślny manifest Win32 jest generowany dla wszystkich aplikacji. Ta właściwość jest równoważna `/nowin32manifest` przełącznika kompilatora vbc.exe.|  
|Moduleassemblyname —|Nazwa zestawu, który skompilowanego modułu jest włączona do. Właściwość jest równoważna `/moduleassemblyname` przełącznika kompilatora.|  
|NoLogo|Wartość logiczna, która wskazuje, czy logo kompilatora ma być wyłączona. Ta właściwość jest równoważna `/nologo` przełącznika kompilatora.|  
|NoStdLib|Wartość logiczna, która wskazuje, czy unikać odwoływania się do biblioteki standardowej (mscorlib.dll). Wartość domyślna to `false`.|  
|NoVBRuntimeReference|Wartość logiczna, która wskazuje, czy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] środowiska uruchomieniowego (Microsoft.VisualBasic.dll) powinno być zawarte jako odwołanie w projekcie.|  
|NoWin32Manifest|Wartość logiczna, która wskazuje, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w aplikacji pliku wykonywalnym. Ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../includes/windowsver-md.md)]. W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i rejestracji wolnego modelu COM ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) można osadzić w pliku wykonywalnym aplikacji. `True` Określa, że informacje manifestu kontroli konta użytkownika nie można osadzić.<br /><br /> Ta właściwość ma zastosowanie tylko do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektów przeznaczonych dla [!INCLUDE[windowsver](../includes/windowsver-md.md)]. W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i rejestracji wolnego modelu COM ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] celu osadzania manifestów wszelkie informacje zawarte w aplikacji pliku wykonywalnym; ten proces jest nazywany *wirtualizacji*. Aby korzystać z wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` w następujący sposób:<br /><br /> -Aby [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów, Usuń `<ApplicationManifest>` węzła. (W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów `<NoWin32Manifest>` jest ignorowany, kiedy `<ApplicationManifest>` istnieje węzeł.)<br />-Aby [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty, ustawiać `<ApplicationManifest>` do `False` i `<NoWin32Manifest>` do `True`. (W [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów `<ApplicationManifest>` zastępuje `<NoWin32Manifest>`.)|  
|Optymalizuj|Wartość logiczna, która po ustawieniu `true`, umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna `/optimize` przełącznika kompilatora.|  
|OptionCompare|Określa, jak są wykonywane porównywania ciągów. Prawidłowe wartości to "binary" lub "text". Ta właściwość jest równoważna `/optioncompare` przełącznika kompilatora vbc.exe.|  
|OptionExplicit|Wartość logiczna, która po ustawieniu `true`, wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna `/optionexplicit` przełącznika kompilatora.|  
|Optioninfer —|Wartość logiczna, która po ustawieniu `true`, należy wpisać umożliwia zmiennym odwoływanie. Ta właściwość jest równoważna `/optioninfer` przełącznika kompilatora.|  
|OptionStrict|Wartość logiczna, która po ustawieniu `true`, powoduje, że zadanie kompilacji wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna `/optionstrict` przełącznika kompilatora vbc.exe.|  
|OutputPath|Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład "bin\Debug".|  
|Atrybut OutputType|Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> — Biblioteka. Tworzy bibliotekę kodu. (Wartość domyślna).<br />-Exe. Tworzy aplikację konsoli.<br />-Moduł. Tworzy moduł.<br />-Winexe. Tworzy program oparty na Windows.<br /><br /> Ta właściwość jest równoważna `/target` przełącznika kompilatora vbc.exe.|  
|OverwriteReadOnlyFiles|Wartość logiczna wskazująca, czy chcesz włączyć kompilacji zastąpić pliki tylko do odczytu czy wyzwalała błąd.|  
|PdbFile|Nazwa pliku pliku .pdb, który emitujesz. Ta właściwość jest równoważna `/pdb` przełącznika kompilatora csc.exe.|  
|Platforma|System operacyjny, który tworzysz. Prawidłowe wartości to "Any CPU", "x 86" i "x64".|  
|RemoveIntegerChecks|Wartość logiczna, która wskazuje, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest równoważna `/removeintchecks` przełącznika kompilatora vbc.exe.|  
|SGenUseProxyTypes|Wartość logiczna wskazująca, czy typy serwerów proxy powinny być generowane przez SGen.exe.<br /><br /> Obiekt docelowy SGen używa tej właściwości można ustawić flagę UseProxyTypes. Ta właściwość jest domyślnie ustawiona na wartość true, a nie ma interfejsu użytkownika Aby to zmienić. Aby wygenerować zestawu serializacji dla typów innych niż Usługa sieci Web, Dodaj tę właściwość do pliku projektu i ustaw ją na false przed zaimportowaniem do Microsoft.Common.Targets lub C#/VB.targets.|  
|SGenToolPath|Opcjonalna ścieżka narzędzia wskazującą, skąd pobierać plik SGen.exe po bieżącej wersji SGen.exe.|  
|StartupObject|Określa klasę lub moduł, który zawiera element metodę Main lub procedurę Sub Main. Ta właściwość jest równoważna `/main` przełącznika kompilatora.|  
|ProcessorArchitecture|Architektura procesora, który jest używany, gdy odwołania do zestawów są rozwiązane. Prawidłowe wartości to "msil", "x86", "amd64" lub "ia64".|  
|RootNamespace|Główna przestrzeń nazw, używana przy nazywaniu zasobu osadzonego. Ta przestrzeń nazw jest częścią nazwy manifestu osadzonego zasobu.|  
|Satellite_AlgorithmId|Identyfikator algorytmu mieszania AL.exe do użycia przy tworzeniu zestawów satelickich.|  
|Satellite_BaseAddress|Adres podstawowy do użycia podczas specyficzne dla kultury zestawy satelickie są kompilowane przy użyciu `CreateSatelliteAssemblies` docelowej.|  
|Satellite_CompanyName|Nazwa firmy do przekazania do AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_Configuration|Nazwa konfiguracji do przekazania do AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_Description|Tekst opisu przekazywany do AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_EvidenceFile|Osadza określony plik w zestawie satelickim o nazwie zasobu "Security.Evidence."|  
|Satellite_FileVersion|Określa ciąg w polu File Version w zestawie satelickim.|  
|Satellite_Flags|Określa wartość w polu Flags w zestawie satelickim.|  
|Satellite_GenerateFullPaths|Powoduje, że zadanie kompilacji używa ścieżki bezwzględnej dla wszelkich plików zgłoszonych w komunikacie o błędzie.|  
|Satellite_LinkResource|Łączy określone pliki zasobów zestawu satelickiego.|  
|Satellite_MainEntryPoint|Określa w pełni kwalifikowaną nazwę (czyli class.method) metody do użycia jako punkt wejścia, gdy moduł jest konwertowany na plik wykonywalny podczas generowania zestawu satelickiego.|  
|Satellite_ProductName|Określa ciąg w polu Product w zestawie satelickim.|  
|Satellite_ProductVersion|Określa ciąg w polu ProductVersion w zestawie satelickim.|  
|Satellite_TargetType|Określa format pliku wyjściowego zestawu satelickiego jako "library", "exe" lub "win". Wartość domyślna to "library".|  
|Satellite_Title|Określa ciąg w polu Title w zestawie satelickim.|  
|Satellite_Trademark|Określa ciąg w polu Trademark w zestawie satelickim.|  
|Satellite_Version|Określa informacje o wersji dla zestawu satelickiego.|  
|Satellite_Win32Icon|Wstawia plik ikony .ico w zestawie satelickim.|  
|Satellite_Win32Resource|Wstawia zasób Win32 (plik .res) do zestawu satelickiego.|  
|SubsystemVersion|Określa minimalną wersję podsystemu, którego wygenerowany plik wykonywalny może używać. Ta właściwość jest równoważna `/subsystemversion` przełącznika kompilatora. Aby uzyskać informacje o wartości domyślnej tej właściwości, zobacz [/subsystemversion (Visual Basic)](http://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) lub [/subsystemversion (opcje kompilatora C#)](http://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Wersja platformy .NET Compact Framework, która jest wymagana do uruchamiania aplikacji, który jest kompilowany. Określenie jej pozwala odwoływać się do niektórych zestawów systemu, nie można się odwoływać inaczej.|  
|TargetFrameworkVersion|Wersja [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , jest wymagana do uruchamiania aplikacji, który jest kompilowany. Określenie jej pozwala odwoływać się do niektórych zestawów systemu, nie można się odwoływać inaczej.|  
|TreatWarningsAsErrors|Parametr logiczny który, jeśli `true`, powoduje, że wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny `/nowarn` przełącznika kompilatora.|  
|UseHostCompilerIfAvailable|Parametr logiczny który, jeśli `true`, powoduje, że zadanie kompilacji używa obiektu wewnątrzprocesowego kompilatora, jeśli jest ona dostępna. Ten parametr jest używany tylko przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|Utf8output —|Parametr logiczny który, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny `/utf8Output` przełącznika kompilatora.|  
|VbcToolPath|Opcjonalna ścieżka wskazującą inną lokalizację VBC.exe, gdy zostanie zastąpiona bieżąca wersja vbc.exe.|  
|VbcVerbosity|Określa poziom szczegółowości [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] danych wyjściowych kompilatora. Prawidłowe wartości to "Quiet", "Normal" (wartość domyślna) lub "Verbose".|  
|VisualStudioVersion|Określa wersję programu Visual Studio, w którym ten projekt powinien traktowane jako uruchomione. Jeśli ta właściwość nie jest określona, program MSBuild ustawia ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów, aby określić zestaw obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4.0 lub wyższą dla projektu, `VisualStudioVersion` służy do określania, którego podzestawu narzędzi do użycia. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Określa listę ostrzeżeń do traktowania jako błędy. Ten parametr jest równoważny `/warnaserror` przełącznika kompilatora.|  
|WarningsNotAsErrors|Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny `/warnaserror` przełącznika kompilatora.|  
|Win32Manifest|Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny `/win32Manifest` przełącznika kompilatora.|  
|Win32Resource|Nazwa pliku zasobu Win32 osadzanego w końcowym zestawie. Ten parametr jest równoważny `/win32resource` przełącznika kompilatora.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
