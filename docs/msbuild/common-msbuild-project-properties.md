---
title: Wspólne właściwości projektu MSBuild | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece57a102851efe0198f8993b60dba8e0eae6dec
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634425"
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektu MSBuild

W poniższej tabeli wymieniono często używane właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w plikach *. targets* udostępnianych przez program MSBuild.

 Pliki projektu w programie Visual Studio ( *. csproj*, *. vbproj*, *. vcxproj*i inne) zawierają kod XML programu MSBuild, który jest uruchamiany podczas kompilowania projektu przy użyciu środowiska IDE. Projekty zwykle importują jeden lub więcej plików *. targets* , aby zdefiniować ich proces kompilacji. Aby uzyskać więcej informacji, zobacz [pliki MSBuild. targets](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów

| Nazwa właściwości lub parametru | Opis |
|------------------------------------| - |
| AdditionalLibPaths | Określa dodatkowe foldery, w których kompilatory powinny szukać zestawów referencyjnych. |
| AddModules | Powoduje, że kompilator udostępnia wszystkie informacje o typie z określonych plików dla kompilowanego projektu. Ta właściwość jest równoważna z przełącznikiem kompilatora `/addModules`. |
| ALToolPath | Ścieżka, w której można znaleźć *Al. exe* . Ta właściwość zastępuje bieżącą wersję programu *Al. exe* , aby umożliwić korzystanie z innej wersji. |
| ApplicationIcon | Plik ikony *. ico* do przekazania do kompilatora w celu osadzenia jako ikona Win32. Właściwość jest równoważna z przełącznikiem kompilatora `/win32icon`. |
| ApplicationManifest | Określa ścieżkę pliku, który jest używany do generowania informacji manifestu kontroli konta użytkownika zewnętrznego (UAC). Dotyczy tylko projektów programu Visual Studio przeznaczonych dla systemu Windows Vista.<br /><br /> W większości przypadków manifest jest osadzony. Jeśli jednak korzystasz z rejestracji bezpłatnej COM lub ClickOnce, manifest może być plikiem zewnętrznym, który jest instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji, zobacz Właściwość NoWin32Manifest w tym temacie. |
| AssemblyOriginatorKeyFile | Określa plik, który jest używany do podpisywania zestawu ( *. snk* lub *. pfx*) i który jest przesyłany do [zadania ResolveKeySource —](../msbuild/resolvekeysource-task.md) w celu wygenerowania klucza, który jest używany do podpisywania zestawu. |
| AssemblySearchPaths | Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność, w jakiej ścieżki pojawiają się na tej liście, ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami. |
| AssemblyName | Nazwa końcowego zestawu wyjściowego po skompilowaniu projektu. |
| BaseAddress | Określa adres podstawowy głównego zestawu wyjściowego. Ta właściwość jest równoważna z przełącznikiem kompilatora `/baseaddress`. |
| BaseIntermediateOutputPath | Folder najwyższego poziomu, w którym są tworzone wszystkie pośrednie foldery wyjściowe specyficzne dla konfiguracji. Wartością domyślną jest `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Określa ścieżkę podstawową dla pliku wyjściowego. Jeśli jest ustawiona, MSBuild będzie używać `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykładowa składnia: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane lub czyszczone równolegle, gdy jest używany wieloetapowy MSBuild. Wartość domyślna to `true`, co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów. |
| BuildProjectReferences | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane przez MSBuild. Automatycznie Ustaw `false`, jeśli tworzysz projekt w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, `true` w przeciwnym razie. `-p:BuildProjectReferences=false` można określić w wierszu polecenia, aby uniknąć sprawdzania, czy odwołania do projektów są aktualne. |
| CleanFile | Nazwa pliku, który będzie używany jako "czyszczenie pamięci podręcznej". Czyszczenie pamięci podręcznej to Lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczany w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce. |
| CodePage | Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna z przełącznikiem kompilatora `/codepage`. |
| CompilerResponseFile | Opcjonalny plik odpowiedzi, który można przesłać do zadań kompilatora. |
| Konfiguracja | Konfiguracja, którą tworzysz, albo "debug" lub "Release" (wydanie). |
| CscToolPath | Ścieżka do pliku *CSC. exe*, C# kompilatora. |
| CustomBeforeMicrosoftCommonTargets | Nazwa pliku projektu lub pliku docelowego, który ma zostać zaimportowany automatycznie przed importem wspólnych obiektów docelowych. |
| DebugSymbols | Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **-p:DebugSymbols = false** w wierszu polecenia wyłącza generowanie plików symboli bazy danych programu ( *. pdb*). |
| DebugType | Definiuje poziom informacji debugowania, które mają zostać wygenerowane. Prawidłowe wartości to "Full", "pdbonly", "" Portable "," Embedded "i" none ". |
| DefineConstants | Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1 = wartość1; symbol2 = wartość2*<br /><br /> Właściwość jest równoważna z przełącznikiem kompilatora `/define`. |
| DefineDebug | Wartość logiczna wskazująca, czy ma być zdefiniowana stała debugowania. |
| DefineTrace | Wartość logiczna wskazująca, czy ma być zdefiniowana stała śledzenia. |
| DelaySign | Wartość logiczna wskazująca, czy chcesz opóźnić podpisywanie zestawu, a nie pełnego podpisywania. |
| Deterministyczne | Wartość logiczna wskazująca, czy kompilator powinien generować identyczne zestawy dla identycznych danych wejściowych. Ten parametr odnosi się do `/deterministic` przełącznika kompilatorów *VBC. exe* i *CSC. exe* . |
| DisabledWarnings | Pomija określone ostrzeżenia. Należy określić tylko część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odpowiada przełącznikowi `/nowarn` kompilatora *VBC. exe* . |
| DisableFastUpToDateCheck | Wartość logiczna, która ma zastosowanie tylko do programu Visual Studio. Program Visual Studio Build Manager używa procesu o nazwie FastUpToDateCheck, aby określić, czy projekt musi zostać odbudowany, aby był aktualny. Ten proces jest szybszy niż użycie programu MSBuild do jego określenia. Ustawienie właściwości DisableFastUpToDateCheck na `true` pozwala ominąć program Visual Studio Build Manager i wymusić użycie programu MSBuild do określenia, czy projekt jest aktualny. |
| DocumentationFile | Nazwa pliku, który jest generowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie zawiera informacji o ścieżce. |
| ErrorReport | Określa sposób, w jaki zadanie kompilatora powinno raportować wewnętrzne błędy kompilatora. Prawidłowe wartości to "Prompt", "Send" i "none". Ta właściwość jest równoważna z przełącznikiem kompilatora `/errorreport`. |
| ExcludeDeploymentUrl | [Zadanie GenerateDeploymentManifest —](../msbuild/generatedeploymentmanifest-task.md) dodaje tag deploymentProvider do manifestu wdrożenia, jeśli plik projektu zawiera dowolny z następujących elementów:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl można jednak zapobiec dodawaniu znacznika deploymentProvider do manifestu wdrożenia, nawet jeśli określono którykolwiek z powyższych adresów URL. Aby to zrobić, Dodaj następującą właściwość do pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Uwaga:**  ExcludeDeploymentUrl nie jest ujawniona w środowisku IDE programu Visual Studio i może być ustawiana tylko przez ręczne edytowanie pliku projektu. Ustawienie tej właściwości nie ma wpływu na publikowanie w programie Visual Studio; oznacza to, że tag deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl. |
| FileAlignment | Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest równoważna z przełącznikiem kompilatora `/filealignment`. |
| FrameworkPathOverride | Określa lokalizację plików *mscorlib. dll* i *Microsoft. VisualBasic. dll*. Ten parametr jest równoważny z przełącznikiem `/sdkpath` kompilatora *VBC. exe* . |
| GenerateDocumentation | (C#, Visual Basic) Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true`, kompilacja generuje informacje o dokumentacji i umieszcza je w pliku *. XML* wraz z nazwą pliku wykonywalnego lub biblioteki utworzoną przez zadanie kompilacji. |
| GenerateFullPaths | (C#) Generuj pełne ścieżki nazw plików w danych wyjściowych przy użyciu opcji kompilatora [-fullpaths —](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | Wskazuje, czy zestawy serializacji XML powinny być generowane przez *Sgen. exe*, które mogą być ustawione na wartość on, autolub off. Ta właściwość jest używana dla zestawów, które są przeznaczone tylko .NET Framework. Aby wygenerować zestawy serializacji XML dla .NET Standard lub zestawów .NET Core, odwołując się do pakietu NuGet *Microsoft. XmlSerializer. Generator* . |
| IntermediateOutputPath | Pełna pośrednia Ścieżka wyjściowa jako pochodna `BaseIntermediateOutputPath`, jeśli nie określono ścieżki. Na przykład *\obj\debug\\* . |
| KeyContainerName | Nazwa kontenera klucza o silnej nazwie. |
| KeyOriginatorFile | Nazwa pliku klucza o silnej nazwie. |
| Moduleassemblyname — | Nazwa zestawu, do którego ma zostać dołączony skompilowany moduł. Właściwość jest równoważna z przełącznikiem kompilatora `/moduleassemblyname`. |
| MSBuildProjectExtensionsPath | Określa ścieżkę, w której znajdują się rozszerzenia projektu. Domyślnie ma to taką samą wartość jak `BaseIntermediateOutputPath`. |
| NoLogo | Wartość logiczna wskazująca, czy logo kompilatora ma być wyłączone. Ta właściwość jest równoważna z przełącznikiem kompilatora `/nologo`. |
| NoStdLib | Wartość logiczna wskazująca, czy należy unikać odwoływania się do biblioteki standardowej (*mscorlib. dll*). Wartością domyślną jest `false`. |
| NoVBRuntimeReference | Wartość logiczna wskazująca, czy środowisko uruchomieniowe Visual Basic (*Microsoft. VisualBasic. dll*) powinno być dołączone jako odwołanie w projekcie. |
| NoWin32Manifest | Wartość logiczna wskazująca, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w pliku wykonywalnym aplikacji. Dotyczy tylko projektów programu Visual Studio przeznaczonych dla systemu Windows Vista. W projektach wdrożonych przy użyciu technologii ClickOnce i COM bez rejestracji ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) są osadzone w pliku wykonywalnym aplikacji. `True` określa, że informacje manifestu kontroli konta użytkownika nie są osadzone.<br /><br /> Ta właściwość ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla systemu Windows Vista. W projektach wdrożonych przy użyciu technologii ClickOnce i COM bez rejestracji ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz, aby program Visual Studio osadzał żadnych informacji manifestu w pliku wykonywalnym aplikacji; Ten proces jest nazywany *wirtualizacją*. Aby używać wirtualizacji, należy ustawić `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` w następujący sposób:<br /><br /> — W przypadku projektów Visual Basic Usuń węzeł `<ApplicationManifest>`. (W Visual Basic projekty `<NoWin32Manifest>` jest ignorowane, gdy istnieje węzeł `<ApplicationManifest>`).<br />— W C# przypadku projektów ustaw `<ApplicationManifest>` na `False` i `<NoWin32Manifest>` na `True`. (W C# projektach `<ApplicationManifest>` zastąpień `<NoWin32Manifest>`).<br /> Ta właściwość jest równoważna z przełącznikiem kompilatora `/nowin32manifest` *VBC. exe*. |
| Optymalizacja | Wartość logiczna, która po ustawieniu na `true`, umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optimize`. |
| OptionCompare | Określa sposób, w jaki są wykonywane porównania ciągów. Prawidłowe wartości to "Binary" lub "text". Ta właściwość jest równoważna z przełącznikiem kompilatora `/optioncompare` *VBC. exe*. |
| OptionExplicit | Wartość logiczna, która po ustawieniu na `true`wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optionexplicit`. |
| OptionInfer | Wartość logiczna, która po ustawieniu na `true`włącza wnioskowanie o typie zmiennych. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optioninfer`. |
| OptionStrict | Wartość logiczna, która po ustawieniu na `true`, powoduje, że zadanie kompilacji wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna z `/optionstrict`m przełącznikiem kompilatora *VBC. exe* . |
| OutDir | Wskazuje końcową lokalizację wyjściową dla projektu lub rozwiązania. Podczas kompilowania rozwiązania OutDir można użyć do zebrania wielu danych wyjściowych projektu w jednej lokalizacji. Ponadto OutDir jest zawarty w AssemblySearchPaths używany do rozpoznawania odwołań. Na przykład *bin\Debug*. |
| OutputPath | Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład *bin\Debug*. |
| OutputType | Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> Biblioteki. Tworzy bibliotekę kodu. (Wartość domyślna).<br />Exe. Tworzy aplikację konsolową.<br />Elementu. Tworzy moduł.<br />Winexe. Tworzy program oparty na systemie Windows.<br /><br /> Ta właściwość jest równoważna z `/target`m przełącznikiem kompilatora *VBC. exe* . |
| OverwriteReadOnlyFiles | Wartość logiczna wskazująca, czy chcesz włączyć kompilację w celu zastąpienia plików tylko do odczytu, czy wyzwolenia błędu. |
| Elemencie pathmap | Określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych wyjściowych przez kompilator. Ta właściwość jest równoważna z przełącznikiem `/pathmap` kompilatora *CSC. exe* . |
| PdbFile | Nazwa pliku *. pdb* , który emituje. Ta właściwość jest równoważna z przełącznikiem `/pdb` kompilatora *CSC. exe* . |
| Platforma | System operacyjny, dla którego tworzysz. Prawidłowe wartości to "dowolny procesor CPU", "x86" i "x64". |
| ProcessorArchitecture | Architektura procesora, która jest używana podczas rozwiązywania odwołań do zestawów. Prawidłowe wartości to "MSIL", "x86", "amd64" lub "ia64". |
| ProduceOnlyReferenceAssembly | Wartość logiczna, która powoduje, że kompilator emituje tylko zestaw odniesienia zamiast skompilowanego kodu. Nie można używać w połączeniu z `ProduceReferenceAssembly`.  Ta właściwość odnosi się do `/refonly` przełącznika kompilatorów *VBC. exe* i *CSC. exe* . |
| ProduceReferenceAssembly | Wartość logiczna, która po ustawieniu na `true` włącza produkcję [zestawów referencyjnych](/dotnet/standard/assembly/reference-assemblies) dla bieżącego zestawu. w przypadku korzystania z tej funkcji należy `true` `Deterministic`. Ta właściwość odnosi się do `/refout` przełącznika kompilatorów *VBC. exe* i *CSC. exe* . |
| RemoveIntegerChecks | Wartość logiczna wskazująca, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartością domyślną jest `false`. Ta właściwość jest równoważna z `/removeintchecks`m przełącznikiem kompilatora *VBC. exe* . |
| RootNamespace | Główna przestrzeń nazw, która ma być używana przy nazwie zasobu osadzonego. Ta przestrzeń nazw jest częścią osadzonej nazwy manifestu zasobu. |
| Satellite_AlgorithmId | Identyfikator algorytmu wyznaczania wartości skrótu *Al. exe* do użycia podczas tworzenia zestawów satelickich. |
| Satellite_BaseAddress | Adres podstawowy, który ma być używany w przypadku kompilowania zestawów satelickich specyficznych dla kultury przy użyciu elementu docelowego `CreateSatelliteAssemblies`. |
| Satellite_CompanyName | Nazwa firmy do przekazania do *Al. exe* podczas generowania zestawu satelickiego. |
| Satellite_Configuration | Nazwa konfiguracji do przekazania do *Al. exe* podczas generowania zestawu satelickiego. |
| Satellite_Description | Tekst opisu do przekazania do *Al. exe* podczas generowania zestawu satelickiego. |
| Satellite_EvidenceFile | Osadza określony plik w zestawie satelickim o nazwie zasobu "Security. dowód". |
| Satellite_FileVersion | Określa ciąg dla pola wersja pliku w zestawie satelickim. |
| Satellite_Flags | Określa wartość dla pola flags w zestawie satelickim. |
| Satellite_GenerateFullPaths | Powoduje, że zadanie kompilacji używa ścieżek bezwzględnych dla wszystkich plików zgłoszonych w komunikacie o błędzie. |
| Satellite_LinkResource | Łączy określone pliki zasobów z zestawem satelickim. |
| Satellite_MainEntryPoint | Określa w pełni kwalifikowaną nazwę (czyli Class. Method) metody do użycia jako punkt wejścia, gdy moduł jest konwertowany do pliku wykonywalnego podczas generowania zestawu satelickiego. |
| Satellite_ProductName | Określa ciąg dla pola Product w zestawie satelickim. |
| Satellite_ProductVersion | Określa ciąg dla pola ProductVersion w zestawie satelickim. |
| Satellite_TargetType | Określa format pliku wyjściowego zestawu satelickiego jako "Biblioteka", "exe" lub "win". Wartość domyślna to "Library". |
| Satellite_Title | Określa ciąg dla pola title w zestawie satelickim. |
| Satellite_Trademark | Określa ciąg dla pola znaku towarowego w zestawie satelickim. |
| Satellite_Version | Określa informacje o wersji dla zestawu satelickiego. |
| Satellite_Win32Icon | Wstawia plik ikony *. ico* w zestawie satelickim. |
| Satellite_Win32Resource | Wstawia zasób Win32 (plik *. res* ) do zestawu satelickiego. |
| SGenToolPath | Opcjonalna ścieżka narzędzia, która wskazuje, gdzie uzyskać *Sgen. exe* , gdy bieżąca wersja pliku *Sgen. exe* zostanie zastąpiona. Ta właściwość jest używana tylko dla .NET Framework.|
| SGenUseProxyTypes | Wartość logiczna wskazująca, czy typy proxy powinny być generowane przez *Sgen. exe*. Ma to zastosowanie tylko wtedy, gdy *GenerateSerializationAssemblies* jest ustawiona na wartość on i tylko dla .NET Framework.<br /><br /> Obiekt docelowy SGen używa tej właściwości, aby ustawić flagę UseProxyTypes. Ta właściwość domyślnie ma wartość true, a nie ma interfejsu użytkownika umożliwiającego zmianę tego ustawienia. Aby wygenerować zestaw serializacji dla typów niezwiązanych z usługą WebService, należy dodać tę właściwość do pliku projektu i ustawić wartość false przed zaimportowaniem elementu *Microsoft. Common. targets* lub  *C#/VB.targets*. |
| StartupObject | Określa klasę lub moduł, który zawiera metodę Main lub Sub Main. Ta właściwość jest równoważna z przełącznikiem kompilatora `/main`. |
| SubsystemVersion | Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny. Ta właściwość jest równoważna z przełącznikiem kompilatora `/subsystemversion`. Aby uzyskać informacje o domyślnej wartości tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Wersja .NET Compact Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TargetFrameworkVersion | Wersja .NET Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TreatWarningsAsErrors | Parametr logiczny, który, jeśli `true`, powoduje, że wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/nowarn`. |
| UseHostCompilerIfAvailable | Parametr logiczny, który, jeśli `true`, powoduje, że zadanie kompilacji używa obiektu kompilatora w procesie, jeśli jest dostępny. Ten parametr jest używany tylko przez program Visual Studio. |
| Utf8output — | Parametr logiczny, który, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny z przełącznikiem kompilatora `/utf8Output`. |
| VbcToolPath | Opcjonalna ścieżka, która wskazuje inną lokalizację programu *VBC. exe* , gdy bieżąca wersja pliku *VBC. exe* zostanie zastąpiona. |
| VbcVerbosity | Określa poziom szczegółowości danych wyjściowych kompilatora Visual Basic. Prawidłowe wartości to "quiet", "normal" (wartość domyślna) lub "verbose". |
| VisualStudioVersion | Określa wersję programu Visual Studio, w ramach której ten projekt powinien być traktowany jako uruchomiony. Jeśli ta właściwość nie jest określona, MSBuild ustawi ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów do określenia zestawu obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4,0 lub wyższą dla projektu, `VisualStudioVersion` służy do określenia, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz zestaw [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Określa listę ostrzeżeń, które mają być traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/warnaserror`. |
| WarningsNotAsErrors | Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/warnaserror`. |
| Win32Manifest | Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny z przełącznikiem kompilatora `/win32Manifest`. |
| Win32Resource | Nazwa pliku zasobu Win32, który ma zostać osadzony w końcowym zestawie. Ten parametr jest równoważny z przełącznikiem kompilatora `/win32resource`. |

## <a name="see-also"></a>Zobacz też

- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
