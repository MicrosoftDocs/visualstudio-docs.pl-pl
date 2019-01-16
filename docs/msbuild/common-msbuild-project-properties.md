---
title: Wspólne właściwości projektów MSBuild | Dokumentacja firmy Microsoft
ms.date: 01/18/2018
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 934615be23ebb025740521d35e31fee9f0a6ec47
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315582"
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektów MSBuild
W poniższej tabeli właściwości często używanych list, które są zdefiniowane w plikach projektu programu Visual Studio lub zawartych w *.targets* pliki, dostarczanych przez program MSBuild.  
  
 Pliki w programie Visual Studio projektu (*.csproj*, *.vbproj*, *.vcxproj*i inne) zawierają kod MSBuild XML, który jest uruchamiany, gdy tworzysz projekt za pomocą IDE. Projekty zazwyczaj importują jeden lub więcej *.targets* pliki, aby zdefiniować ich proces kompilacji. Aby uzyskać więcej informacji, zobacz [MSBuild — pliki .targets](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów  
  
| Nazwa właściwości lub parametru | Opis |
|------------------------------------| - |
| AdditionalLibPaths | Określa dodatkowe foldery, w których kompilatory mają szukać zestawów odwołań. |
| AddModules | Powoduje, że kompilator udostępnia wszystkie typy informacji z określonych plików kompilowanemu projektowi. Ta właściwość jest równoważna `/addModules` przełącznika kompilatora. |
| ALToolPath | Ścieżka gdzie *AL.exe* można znaleźć. Ta właściwość zastępuje bieżącą wersję *AL.exe* umożliwia korzystanie z innej wersji. |
| ApplicationIcon | *.Ico* plik ikony do przekazania do kompilatora w celu osadzenia jako ikona Win32. Właściwość jest równoważna `/win32icon` przełącznika kompilatora. |
| ApplicationManifest | Określa ścieżkę do pliku, który jest używany do generowania zewnętrznych informacji manifestu kontroli konta użytkownika (UAC). Ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> W większości przypadków manifest jest osadzony. Jednak jeśli używasz rejestracji wolnego modelu COM lub [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, a następnie manifest może być plik zewnętrzny, instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji zobacz Omówienie właściwości NoWin32Manifest w tym temacie. |
| AssemblyOriginatorKeyFile | Określa plik, który jest używany do podpisywania zestawu (*.snk* lub *PFX*) i który jest przekazywany do [resolvekeysource — zadanie](../msbuild/resolvekeysource-task.md) do wygenerowania klucza rzeczywistego, który jest używany do podpisywania zestaw. |
| AssemblySearchPaths | Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność wyświetlania ścieżek na tej liście ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami. |
| AssemblyName | Nazwa zestawu pliku wyjściowego po utworzeniu projektu. |
| BaseAddress | Określa adres bazowy głównego zestawu wyjścia. Ta właściwość jest równoważna `/baseaddress` przełącznika kompilatora. |
| BaseOutputPath | Określa podstawową ścieżkę dla pliku wyjściowego. Jeśli je skonfigurowano, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] użyje `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykład składni: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Folder najwyższego poziomu, w których wszystkie specyficznych dla konfiguracji pośrednie foldery wynikowe są tworzone. Wartość domyślna to `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | Wartość logiczna, która wskazuje, czy odwołania do projektu są wbudowane lub czyszczone równolegle, kiedy wieloprocesowym [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest używany. Wartość domyślna to `true`, co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów. |
| BuildProjectReferences | Wartość logiczna, która wskazuje, czy odwołania w projekcie są kompilowane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Automatycznie ustawiona na `false` Jeśli tworzysz projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE), `true` Jeśli inaczej. `-p:BuildProjectReferences=false` można określić w wierszu polecenia, aby uniknąć, sprawdzanie, czy przywoływane projekty są aktualne. |
| CleanFile | Nazwa pliku, który będzie używany jako "clean cache". Wyczyść pamięć podręczną znajduje się lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczony w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce. |
| CodePage | Określa stronę kodową dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna `/codepage` przełącznika kompilatora. |
| CompilerResponseFile | Opcjonalny plik odpowiedzi, który może być przekazywany do zadań kompilatora. |
| Konfiguracja | Konfiguracja, który jest kompilowany "Debug" lub "Wersja". |
| CscToolPath | Ścieżka *csc.exe*, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kompilatora. |
| CustomBeforeMicrosoftCommonTargets | Nazwa pliku projektu lub pliku obiektów docelowych, który ma być importowane automatycznie przed zaimportowaniem wspólnych obiektów docelowych. |
| DebugSymbols | Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **- p: DebugSymbols = false** w wierszu poleceń wyłącza Generowanie z bazy danych programu (*.pdb*) pliki symboli. |
| DebugType | Definiuje poziom informacji debugowania, które mają być generowane. Prawidłowe wartości to "full", "pdbonly" i "none". |
| DefineConstants | Definiuje stałe warunkowe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określane przy użyciu następującej składni:<br /><br /> *symbol1 = wartość1; Symbol2 = wartość2*<br /><br /> Właściwość jest równoważna `/define` przełącznika kompilatora. |
| DefineDebug | Wartość logiczna wskazująca, czy chcesz, aby stała DEBUG była zdefiniowana. |
| DefineTrace | Wartość logiczna wskazująca, czy chcesz, aby stała TRACE była zdefiniowana. |
| DelaySign | Wartość logiczna wskazująca, czy chcesz Opóźnij podpisanie zestawu zamiast pełnego podpisywania. |
| Deterministyczna | Wartość logiczna wskazująca, czy kompilator powinien wywoływać identycznych zestawów identycznych danych wejściowych. Ten parametr odnosi się do `/deterministic` przełączyć z *vbc.exe* i *csc.exe* kompilatory. |
| DisabledWarnings | Pomija określone ostrzeżenia. Musi być określona tylko część numeryczna identyfikatora ostrzeżenia. Wielokrotne ostrzeżenia są oddzielone średnikami. Ten parametr odnosi się do `/nowarn` przełączyć z *vbc.exe* kompilatora. |
| DisableFastUpToDateCheck | Wartość logiczna, która ma zastosowanie do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tylko. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kompilacji manager używa procesu o nazwie FastUpToDateCheck, aby ustalić, czy projekt musi zostać zrekompilowany, aby być na bieżąco. Ten proces jest szybszy niż używanie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Aby to ustalić. Ustawienie właściwości DisableFastUpToDateCheck na `true` pozwala ominąć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Menedżer kompilacji i wymusić użycie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do określenia, czy projekt jest aktualny. |
| DocumentationFile | Nazwa pliku, który zostanie wygenerowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie ma ścieżki informacji. |
| ErrorReport | Określa, jak zadanie kompilatora powinno zgłosić wewnętrzne błędy kompilatora. Prawidłowe wartości to "prompt", "Wyślij" lub "none". Ta właściwość jest równoważna `/errorreport` przełącznika kompilatora. |
| ExcludeDeploymentUrl | [Generatedeploymentmanifest — zadanie](../msbuild/generatedeploymentmanifest-task.md) spowoduje dodanie znacznika deploymentProvider do manifestu wdrażania, jeśli plik projektu zawiera któreś z następujących elementów:<br /><br /> -UpdateUrl<br />-InstallUrl<br />-PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl, jednak uniemożliwia znacznik deploymentProvider dodawane do pliku manifestu wdrożenia, nawet jeśli żadnego z powyższych adresów URL są określone. Aby to zrobić, dodaj następującą właściwość w pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Uwaga:**  ExcludeDeploymentUrl nie jest dostępny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE i można go ustawić tylko przez ręczną edycję pliku projektu. Ustawienie tej właściwości nie wpływa na publikowanie w ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; oznacza to, że znacznik deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl. |
| FileAlignment | Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096 i 8192. Ta właściwość jest równoważna `/filealignment` przełącznika kompilatora. |
| FrameworkPathOverride | Określa lokalizację *mscorlib.dll* i *microsoft.visualbasic.dll*. Ten parametr jest równoważny `/sdkpath` przełączyć z *vbc.exe* kompilatora. |
| GenerateDocumentation | (Tylko Visual Basic) Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true`, kompilacja generuje informacje o dokumentacji i umieszcza go w *.xml* plików wraz z nazwą pliku wykonywalnego lub biblioteki, utworzonego przez zadanie kompilacji. |
| IntermediateOutputPath | Pełna pośrednia ścieżka wyjściowa wyprowadzana z `BaseIntermediateOutputPath`, jeśli nie określono ścieżki. Na przykład *\obj\debug\\*. |
| KeyContainerName | Nazwa kontenera klucza silnej nazwy. |
| KeyOriginatorFile | Nazwa pliku klucza silnej nazwy. |
| MSBuildProjectExtensionsPath | Określa ścieżkę, gdzie znajdują się rozszerzenia projektu. Domyślnie ten ma taką samą wartość jak `BaseIntermediateOutputPath`. |
| Moduleassemblyname — | Nazwa zestawu, który skompilowanego modułu jest włączona do. Właściwość jest równoważna `/moduleassemblyname` przełącznika kompilatora. |
| NoLogo | Wartość logiczna, która wskazuje, czy logo kompilatora ma być wyłączona. Ta właściwość jest równoważna `/nologo` przełącznika kompilatora. |
| NoStdLib | Wartość logiczna, która wskazuje, czy unikać odwoływania się do biblioteki standardowej (*mscorlib.dll*). Wartość domyślna to `false`. |
| NoVBRuntimeReference | Wartość logiczna, która wskazuje, czy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] środowiska uruchomieniowego (*Microsoft.VisualBasic.dll*) powinny być zawarte jako odwołanie w projekcie. |
| NoWin32Manifest | Wartość logiczna, która wskazuje, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w aplikacji pliku wykonywalnym. Ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i rejestracji wolnego modelu COM ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) można osadzić w pliku wykonywalnym aplikacji. `True` Określa, że informacje manifestu kontroli konta użytkownika nie można osadzić.<br /><br /> Ta właściwość ma zastosowanie tylko do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i rejestracji wolnego modelu COM ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] celu osadzania manifestów wszelkie informacje zawarte w aplikacji pliku wykonywalnym; ten proces jest nazywany *wirtualizacji*. Aby korzystać z wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` w następujący sposób:<br /><br /> -Aby [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów, Usuń `<ApplicationManifest>` węzła. (W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów `<NoWin32Manifest>` jest ignorowany, kiedy `<ApplicationManifest>` istnieje węzeł.)<br />-Aby [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty, ustawiać `<ApplicationManifest>` do `False` i `<NoWin32Manifest>` do `True`. (W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów `<ApplicationManifest>` zastępuje `<NoWin32Manifest>`.)<br /> Ta właściwość jest równoważna `/nowin32manifest` przełącznika kompilatora *vbc.exe*. |
| Optymalizuj | Wartość logiczna, która po ustawieniu `true`, umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna `/optimize` przełącznika kompilatora. |
| OptionCompare | Określa, jak są wykonywane porównywania ciągów. Prawidłowe wartości to "binary" lub "text". Ta właściwość jest równoważna `/optioncompare` przełącznika kompilatora *vbc.exe*. |
| OptionExplicit | Wartość logiczna, która po ustawieniu `true`, wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna `/optionexplicit` przełącznika kompilatora. |
| Optioninfer — | Wartość logiczna, która po ustawieniu `true`, należy wpisać umożliwia zmiennym odwoływanie. Ta właściwość jest równoważna `/optioninfer` przełącznika kompilatora. |
| OptionStrict | Wartość logiczna, która po ustawieniu `true`, powoduje, że zadanie kompilacji wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna `/optionstrict` przełączyć z *vbc.exe* kompilatora. |
| OutputPath | Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład *bin\Debug*. |
| Atrybut OutputType | Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> — Biblioteka. Tworzy bibliotekę kodu. (Wartość domyślna).<br />-Exe. Tworzy aplikację konsoli.<br />-Moduł. Tworzy moduł.<br />-Winexe. Tworzy program oparty na Windows.<br /><br /> Ta właściwość jest równoważna `/target` przełączyć z *vbc.exe* kompilatora. |
| OverwriteReadOnlyFiles | Wartość logiczna wskazująca, czy chcesz włączyć kompilacji zastąpić pliki tylko do odczytu czy wyzwalała błąd. |
| Elemencie PathMap | Określa sposób mapowania ścieżek fizycznych na dane wyjściowe nazwy ścieżki źródłowej przez kompilator. Ta właściwość jest równoważna `/pathmap` przełączyć z *csc.exe* kompilatora. |
| PdbFile | Nazwa pliku *.pdb* pliku, który emitujesz. Ta właściwość jest równoważna `/pdb` przełączyć z *csc.exe* kompilatora. |
| Platforma | System operacyjny, który tworzysz. Prawidłowe wartości to "Any CPU", "x 86" i "x64". |
| ProduceReferenceAssembly | Wartość logiczna, która po ustawieniu `true` umożliwia produkcji [zestawów odwołań](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) dla bieżącego zestawu. `Deterministic` powinien być `true` podczas używania tej funkcji. Ta właściwość odnosi się do `/refout` przełączyć z *vbc.exe* i *csc.exe* kompilatory. |
| ProduceOnlyReferenceAssembly | Wartość logiczna, która instruuje kompilator, aby wyemitować tylko odwołanie do zestawu, a nie kod skompilowany. Nie można używać w połączeniu z `ProduceReferenceAssembly`.  Ta właściwość odnosi się do `/refonly` przełączyć z *vbc.exe* i *csc.exe* kompilatory. |
| RemoveIntegerChecks | Wartość logiczna, która wskazuje, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest równoważna `/removeintchecks` przełączyć z *vbc.exe* kompilatora. |
| SGenUseProxyTypes | Wartość logiczna, która wskazuje, czy typy serwerów proxy powinny być generowane przez *SGen.exe*.<br /><br /> Obiekt docelowy SGen używa tej właściwości można ustawić flagę UseProxyTypes. Ta właściwość jest domyślnie ustawiona na wartość true, a nie ma interfejsu użytkownika Aby to zmienić. Aby wygenerować zestawu serializacji dla typów innych niż Usługa sieci Web, Dodaj tę właściwość do pliku projektu i ustaw ją na false przed zaimportowaniem *Microsoft.Common.Targets* lub *C#/VB.targets*. |
| SGenToolPath | Opcjonalna ścieżka narzędzia wskazującą, skąd uzyskać *SGen.exe* podczas bieżącej wersji *SGen.exe* zostanie zastąpiona. |
| StartupObject | Określa klasę lub moduł, który zawiera element metodę Main lub procedurę Sub Main. Ta właściwość jest równoważna `/main` przełącznika kompilatora. |
| ProcessorArchitecture | Architektura procesora, który jest używany, gdy odwołania do zestawów są rozwiązane. Prawidłowe wartości to "msil", "x86", "amd64" lub "ia64". |
| RootNamespace | Główna przestrzeń nazw, używana przy nazywaniu zasobu osadzonego. Ta przestrzeń nazw jest częścią nazwy manifestu osadzonego zasobu. |
| Satellite_AlgorithmId | Identyfikator *AL.exe* algorytmu do użycia przy tworzeniu zestawów satelickich mieszania. |
| Satellite_BaseAddress | Adres podstawowy do użycia podczas specyficzne dla kultury zestawy satelickie są kompilowane przy użyciu `CreateSatelliteAssemblies` docelowej. |
| Satellite_CompanyName | Nazwa firmy przekazywana do *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_Configuration | Nazwa konfiguracji przekazywana do *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_Description | Tekst opisu przekazywany do *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_EvidenceFile | Osadza określony plik w zestawie satelickim o nazwie zasobu "Security.Evidence." |
| Satellite_FileVersion | Określa ciąg w polu File Version w zestawie satelickim. |
| Satellite_Flags | Określa wartość w polu Flags w zestawie satelickim. |
| Satellite_GenerateFullPaths | Powoduje, że zadanie kompilacji używa ścieżki bezwzględnej dla wszelkich plików zgłoszonych w komunikacie o błędzie. |
| Satellite_LinkResource | Łączy określone pliki zasobów zestawu satelickiego. |
| Satellite_MainEntryPoint | Określa w pełni kwalifikowaną nazwę (czyli class.method) metody do użycia jako punkt wejścia, gdy moduł jest konwertowany na plik wykonywalny podczas generowania zestawu satelickiego. |
| Satellite_ProductName | Określa ciąg w polu Product w zestawie satelickim. |
| Satellite_ProductVersion | Określa ciąg w polu ProductVersion w zestawie satelickim. |
| Satellite_TargetType | Określa format pliku wyjściowego zestawu satelickiego jako "library", "exe" lub "win". Wartość domyślna to "library". |
| Satellite_Title | Określa ciąg w polu Title w zestawie satelickim. |
| Satellite_Trademark | Określa ciąg w polu Trademark w zestawie satelickim. |
| Satellite_Version | Określa informacje o wersji dla zestawu satelickiego. |
| Satellite_Win32Icon | Wstawia *.ico* plik ikony w zestawie satelickim. |
| Satellite_Win32Resource | Wstawia zasób Win32 (*.res* plików) do zestawu satelickiego. |
| SubsystemVersion | Określa minimalną wersję podsystemu, którego wygenerowany plik wykonywalny może używać. Ta właściwość jest równoważna `/subsystemversion` przełącznika kompilatora. Aby uzyskać informacje o wartości domyślnej tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Wersja platformy .NET Compact Framework, która jest wymagana do uruchamiania aplikacji, który jest kompilowany. Określenie jej pozwala odwoływać się do niektórych zestawów systemu, nie można się odwoływać inaczej. |
| TargetFrameworkVersion | Wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , jest wymagana do uruchamiania aplikacji, który jest kompilowany. Określenie jej pozwala odwoływać się do niektórych zestawów systemu, nie można się odwoływać inaczej. |
| TreatWarningsAsErrors | Parametr logiczny który, jeśli `true`, powoduje, że wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny `/nowarn` przełącznika kompilatora. |
| UseHostCompilerIfAvailable | Parametr logiczny który, jeśli `true`, powoduje, że zadanie kompilacji używa obiektu wewnątrzprocesowego kompilatora, jeśli jest ona dostępna. Ten parametr jest używany tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8output — | Parametr logiczny który, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny `/utf8Output` przełącznika kompilatora. |
| VbcToolPath | Opcjonalna ścieżka wskazującą inną lokalizację dla *vbc.exe* podczas bieżącej wersji *vbc.exe* zostanie zastąpiona. |
| VbcVerbosity | Określa poziom szczegółowości [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] danych wyjściowych kompilatora. Prawidłowe wartości to "Quiet", "Normal" (wartość domyślna) lub "Verbose". |
| VisualStudioVersion | Określa wersję programu Visual Studio, w którym ten projekt powinien traktowane jako uruchomione. Jeśli ta właściwość nie jest określona, program MSBuild ustawia ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów, aby określić zestaw obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4.0 lub wyższą dla projektu, `VisualStudioVersion` służy do określania, którego podzestawu narzędzi do użycia. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Określa listę ostrzeżeń do traktowania jako błędy. Ten parametr jest równoważny `/warnaserror` przełącznika kompilatora. |
| WarningsNotAsErrors | Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny `/warnaserror` przełącznika kompilatora. |
| Win32Manifest | Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny `/win32Manifest` przełącznika kompilatora. |
| Win32Resource | Nazwa pliku zasobu Win32 osadzanego w końcowym zestawie. Ten parametr jest równoważny `/win32resource` przełącznika kompilatora. |
  
## <a name="see-also"></a>Zobacz także  
 [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
