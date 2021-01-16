---
title: Wspólne właściwości projektu MSBuild | Microsoft Docs
description: Dowiedz się więcej na temat typowych właściwości projektu MSBuild, które można zdefiniować lub użyć w plikach projektu lub zawartych w plikach. targets udostępnianych przez program MSBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 548116fc3c9b360a866f14e32074111dfdc872d9
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533878"
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektów MSBuild

W poniższej tabeli wymieniono często używane właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w plikach *. targets* udostępnianych przez program MSBuild.

 Pliki projektu w programie Visual Studio (*. csproj*, *. vbproj*, *. vcxproj* i inne) zawierają kod XML programu MSBuild, który jest uruchamiany podczas kompilowania projektu przy użyciu środowiska IDE. Projekty zwykle importują jeden lub więcej plików *. targets* , aby zdefiniować ich proces kompilacji. Aby uzyskać więcej informacji, zobacz [pliki MSBuild. targets](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów

| Nazwa właściwości lub parametru | Typy projektów | Opis |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Określa dodatkowe foldery, w których kompilatory powinny szukać zestawów referencyjnych. |
| AddModules | .NET | Powoduje, że kompilator udostępnia wszystkie informacje o typie z określonych plików dla kompilowanego projektu. Ta właściwość jest równoważna z `/addModules` przełącznikiem kompilatora. |
| ALToolPath | .NET | Ścieżka, w której można znaleźć *AL.exe* . Ta właściwość zastępuje bieżącą wersję *AL.exe* , aby umożliwić korzystanie z innej wersji. |
| ApplicationIcon | .NET | Plik ikony *. ico* do przekazania do kompilatora w celu osadzenia jako ikona Win32. Właściwość jest równoważna z `/win32icon` przełącznikiem kompilatora. |
| ApplicationManifest | Wszystko | Określa ścieżkę pliku, który jest używany do generowania informacji manifestu kontroli konta użytkownika zewnętrznego (UAC). Dotyczy tylko projektów programu Visual Studio przeznaczonych dla systemu Windows Vista.<br /><br /> W większości przypadków manifest jest osadzony. Jeśli jednak korzystasz z rejestracji bezpłatnej COM lub ClickOnce, manifest może być plikiem zewnętrznym, który jest instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji, zobacz Właściwość NoWin32Manifest w tym temacie. |
| AssemblyOriginatorKeyFile | .NET | Określa plik, który jest używany do podpisywania zestawu (*. snk* lub *. pfx*) i który jest przesyłany do [zadania ResolveKeySource —](../msbuild/resolvekeysource-task.md) w celu wygenerowania klucza, który jest używany do podpisywania zestawu. |
| AssemblySearchPaths | .NET | Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność, w jakiej ścieżki pojawiają się na tej liście, ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami. |
| AssemblyName | .NET | Nazwa końcowego zestawu wyjściowego po skompilowaniu projektu. |
| BaseAddress | .NET | Określa adres podstawowy głównego zestawu wyjściowego. Ta właściwość jest równoważna z `/baseaddress` przełącznikiem kompilatora. |
| BaseIntermediateOutputPath | Wszystko | Folder najwyższego poziomu, w którym są tworzone wszystkie pośrednie foldery wyjściowe specyficzne dla konfiguracji. Wartość domyślna to `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Wszystko | Określa ścieżkę podstawową dla pliku wyjściowego. Jeśli jest ustawiona, program MSBuild będzie używać `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Przykładowa składnia: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Wszystko | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane lub czyszczone równolegle, gdy jest używany wieloetapowy MSBuild. Wartość domyślna to `true` , co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów. |
| BuildProjectReferences | Wszystko | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane przez MSBuild. Automatycznie ustawiaj na `false` , jeśli tworzysz projekt w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, w `true` przeciwnym razie. `-p:BuildProjectReferences=false` można określić w wierszu polecenia, aby uniknąć sprawdzania, czy odwołania do projektów są aktualne. |
| CleanFile | Wszystko | Nazwa pliku, który będzie używany jako "czyszczenie pamięci podręcznej". Czyszczenie pamięci podręcznej to Lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczany w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce. |
| CodePage | .NET | Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna z `/codepage` przełącznikiem kompilatora. |
| CompilerResponseFile | .NET | Opcjonalny plik odpowiedzi, który można przesłać do zadań kompilatora. |
| Konfiguracja | Wszystko | Konfiguracja, którą tworzysz, ogólnie `Debug` lub `Release` , ale można ją skonfigurować na poziomie rozwiązania i projektu. |
| CscToolPath | C# | Ścieżka *csc.exe*, kompilator języka C#. |
| CustomBeforeMicrosoftCommonTargets | Wszystko | Nazwa pliku projektu lub pliku docelowego, który ma zostać zaimportowany automatycznie przed importem wspólnych obiektów docelowych. |
| DebugSymbols | Wszystko | Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **-p:DebugSymbols = false** w wierszu polecenia wyłącza generowanie plików symboli bazy danych programu (*. pdb*). |
| DebugType | Wszystko | Definiuje poziom informacji debugowania, które mają zostać wygenerowane. Prawidłowe wartości to "Full", "pdbonly", "" Portable "," Embedded "i" none ". |
| DefineConstants | .NET | Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1 = wartość1; symbol2 = wartość2*<br /><br /> Właściwość jest równoważna z `/define` przełącznikiem kompilatora. |
| DefineDebug | Wszystko |  Wartość logiczna wskazująca, czy ma być zdefiniowana stała debugowania. |
| DefineTrace | Wszystko | Wartość logiczna wskazująca, czy ma być zdefiniowana stała śledzenia. |
| DelaySign | .NET | Wartość logiczna wskazująca, czy chcesz opóźnić podpisywanie zestawu, a nie pełnego podpisywania. |
| Deterministyczne | .NET | Wartość logiczna wskazująca, czy kompilator powinien generować identyczne zestawy dla identycznych danych wejściowych. Ten parametr odnosi się do `/deterministic` przełącznika kompilatorów. |
| DisableFastUpToDateCheck | Wszystko | Wartość logiczna, która ma zastosowanie tylko do programu Visual Studio. Program Visual Studio Build Manager używa procesu o nazwie FastUpToDateCheck, aby określić, czy projekt musi zostać odbudowany, aby był aktualny. Ten proces jest szybszy niż użycie programu MSBuild do jego określenia. Ustawienie właściwości DisableFastUpToDateCheck `true` pozwala pominąć program Visual Studio Build Manager i wymusić użycie programu MSBuild do określenia, czy projekt jest aktualny. |
| DocumentationFile | .NET | Nazwa pliku, który jest generowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie zawiera informacji o ścieżce. |
| ErrorReport | .NET | Określa sposób, w jaki zadanie kompilatora powinno raportować wewnętrzne błędy kompilatora. Prawidłowe wartości to "Prompt", "Send" i "none". Ta właściwość jest równoważna z `/errorreport` przełącznikiem kompilatora. |
| ExcludeDeploymentUrl | .NET | [Zadanie GenerateDeploymentManifest —](../msbuild/generatedeploymentmanifest-task.md) dodaje tag deploymentProvider do manifestu wdrożenia, jeśli plik projektu zawiera dowolny z następujących elementów:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl można jednak zapobiec dodawaniu znacznika deploymentProvider do manifestu wdrożenia, nawet jeśli określono którykolwiek z powyższych adresów URL. Aby to zrobić, Dodaj następującą właściwość do pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Uwaga:**  ExcludeDeploymentUrl nie jest ujawniona w środowisku IDE programu Visual Studio i może być ustawiana tylko przez ręczne edytowanie pliku projektu. Ustawienie tej właściwości nie ma wpływu na publikowanie w programie Visual Studio; oznacza to, że tag deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl. |
| FileAlignment | .NET | Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest równoważna z `/filealignment` przełącznikiem kompilatora. |
| FrameworkPathOverride | Visual Basic | Określa lokalizację *mscorlib.dll* i *microsoft.visualbasic.dll*. Ten parametr jest równoważny z `/sdkpath` przełącznikiem kompilatora *vbc.exe* . |
| GenerateDocumentation | .NET | Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true` kompilacja generuje informacje o dokumentacji i umieszcza je w pliku *. XML* wraz z nazwą pliku wykonywalnego lub biblioteki utworzonej przez zadanie kompilacji. |
| GenerateFullPaths | C# | Generuj pełne ścieżki nazw plików w danych wyjściowych przy użyciu opcji kompilatora [-fullpaths —](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) . |
| GenerateSerializationAssemblies | .NET | Wskazuje, czy zestawy serializacji XML powinny być generowane przez *SGen.exe*, które mogą być ustawione na wartość włączone, automatycznie lub wyłączone. Ta właściwość jest używana dla zestawów, które są przeznaczone tylko .NET Framework. Aby wygenerować zestawy serializacji XML dla .NET Standard lub zestawów .NET Core, odwołuje się do pakietu NuGet *Microsoft.Xmlserializator. Generator* . |
| IntermediateOutputPath | Wszystko | Pełna pośrednia Ścieżka wyjściowa jako pochodna `BaseIntermediateOutputPath` , jeśli nie określono ścieżki. Na przykład *\obj\debug \\*. |
| NazwaKonteneraKlucza | Wszystko | Nazwa kontenera klucza o silnej nazwie. |
| KeyOriginatorFile | Wszystko | Nazwa pliku klucza o silnej nazwie. |
| Moduleassemblyname — | .NET | Nazwa zestawu, do którego ma zostać dołączony skompilowany moduł. Właściwość jest równoważna z `/moduleassemblyname` przełącznikiem kompilatora. |
| MSBuildProjectExtensionsPath | Wszystko | Określa ścieżkę, w której znajdują się rozszerzenia projektu. Domyślnie ma to taką samą wartość jak `BaseIntermediateOutputPath` . |
| NoLogo | Wszystko | Wartość logiczna wskazująca, czy logo kompilatora ma być wyłączone. Ta właściwość jest równoważna z `/nologo` przełącznikiem kompilatora. |
| NoStdLib | .NET | Wartość logiczna wskazująca, czy należy unikać odwoływania się do biblioteki standardowej (*mscorlib.dll*). Wartość domyślna to `false`. |
| NoVBRuntimeReference | Visual Basic | Wartość logiczna wskazująca, czy środowisko uruchomieniowe Visual Basic (*Microsoft.VisualBasic.dll*) powinno być dołączone jako odwołanie w projekcie. |
| Nowarn — | .NET | Pomija określone ostrzeżenia. Należy określić tylko część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do `/nowarn` przełącznika kompilatorów. |
| NoWin32Manifest | .NET | Wartość logiczna wskazująca, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w pliku wykonywalnym aplikacji. Dotyczy tylko projektów programu Visual Studio przeznaczonych dla systemu Windows Vista. W projektach wdrożonych przy użyciu technologii ClickOnce i Registration-Free COM ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) są osadzone w pliku wykonywalnym aplikacji. `True` Określa, że informacje manifestu kontroli konta użytkownika nie są osadzone.<br /><br /> Ta właściwość ma zastosowanie tylko do projektów programu Visual Studio przeznaczonych dla systemu Windows Vista. W projektach wdrożonych przy użyciu technologii ClickOnce i Registration-Free COM ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz, aby program Visual Studio osadzał żadnych informacji manifestu w pliku wykonywalnym aplikacji; Ten proces jest nazywany *wirtualizacją*. Aby używać wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu w `<NoWin32Manifest>` następujący sposób:<br /><br /> — W przypadku projektów Visual Basic Usuń `<ApplicationManifest>` węzeł. (W projektach Visual Basic `<NoWin32Manifest>` jest ignorowany, gdy `<ApplicationManifest>` węzeł istnieje).<br />— Dla projektów C#, ustaw `<ApplicationManifest>` na `False` i `<NoWin32Manifest>` `True` . (W projektach C#, `<ApplicationManifest>` zastąpienia `<NoWin32Manifest>` ).<br /> Ta właściwość jest równoważna z `/nowin32manifest` przełącznikiem kompilatora *vbc.exe*. |
| Optymalizacja | .NET | Wartość logiczna, która po ustawieniu na `true` , umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna z `/optimize` przełącznikiem kompilatora. |
| OptionCompare | VisualBasic | Określa sposób, w jaki są wykonywane porównania ciągów. Prawidłowe wartości to "Binary" lub "text". Ta właściwość jest równoważna z `/optioncompare` przełącznikiem kompilatora *vbc.exe*. |
| OptionExplicit | Visual Basic | Wartość logiczna, która po ustawieniu na `true` , wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna z `/optionexplicit` przełącznikiem kompilatora. |
| OptionInfer | Visual Basic | Wartość logiczna, która po ustawieniu na `true` , umożliwia wnioskowanie o typie zmiennych. Ta właściwość jest równoważna z `/optioninfer` przełącznikiem kompilatora. |
| OptionStrict | Visual Basic | Wartość logiczna, która po ustawieniu na `true` , powoduje, że zadanie kompilacji Wymuszaj semantykę typu ścisłego w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna z `/optionstrict` przełącznikiem kompilatora *vbc.exe* . |
| OutDir | Wszystko | Wskazuje końcową lokalizację wyjściową dla projektu lub rozwiązania. Podczas kompilowania rozwiązania OutDir można użyć do zebrania wielu danych wyjściowych projektu w jednej lokalizacji. Ponadto OutDir jest zawarty w AssemblySearchPaths używany do rozpoznawania odwołań. Na przykład *bin\Debug*. |
| OutputPath | Wszystko | Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład *bin\Debug*. |
| OutputType | Wszystko |  Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> Biblioteki. Tworzy bibliotekę kodu. (Wartość domyślna).<br />Exe. Tworzy aplikację konsolową.<br />Elementu. Tworzy moduł.<br />Winexe. Tworzy program oparty na systemie Windows.<br /><br /> Dla języków C# i Visual Basic ta właściwość jest równoważna z `/target` przełącznikiem. |
| OverwriteReadOnlyFiles | Wszystko | Wartość logiczna wskazująca, czy chcesz włączyć kompilację w celu zastąpienia plików tylko do odczytu, czy wyzwolenia błędu. |
| Elemencie pathmap | .NET | Określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych wyjściowych przez kompilator. Ta właściwość jest równoważna z `/pathmap` przełącznikiem kompilatora. |
| PdbFile | .NET | Nazwa pliku *. pdb* , który emituje. Ta właściwość jest równoważna z `/pdb` przełącznikiem kompilatora *csc.exe* . |
| Platforma | Wszystko | System operacyjny, dla którego tworzysz. Przykłady dla kompilacji .NET Framework to "dowolny procesor CPU", "x86" i "x64". |
| ProcessorArchitecture | .NET | Architektura procesora, która jest używana podczas rozwiązywania odwołań do zestawów. Prawidłowe wartości to "MSIL", "x86", "amd64" lub "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Wartość logiczna, która powoduje, że kompilator emituje tylko zestaw odniesienia zamiast skompilowanego kodu. Nie można używać w połączeniu z `ProduceReferenceAssembly` .  Ta właściwość odpowiada `/refonly` przełącznikowi *vbc.exe* i kompilatorów *csc.exe* . |
| ProduceReferenceAssembly | .NET | Wartość logiczna, która po ustawieniu `true` umożliwia tworzenie [zestawów odwołań](/dotnet/standard/assembly/reference-assemblies) dla bieżącego zestawu. `Deterministic``true`Ta funkcja powinna być używana. Ta właściwość odpowiada `/refout` przełącznikowi *vbc.exe* i kompilatorów *csc.exe* . |
| RemoveIntegerChecks | Visual Basic | Wartość logiczna wskazująca, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest równoważna z `/removeintchecks` przełącznikiem kompilatora *vbc.exe* . |
| RootNamespace | Wszystko | Główna przestrzeń nazw, która ma być używana przy nazwie zasobu osadzonego. Ta przestrzeń nazw jest częścią osadzonej nazwy manifestu zasobu. |
| Satellite_AlgorithmId | .NET | Identyfikator algorytmu wyznaczania wartości skrótu *AL.exe* , który ma być używany podczas tworzenia zestawów satelickich. |
| Satellite_BaseAddress | .NET | Adres podstawowy, który ma być używany w przypadku kompilowania zestawów satelickich specyficznych dla kultury przy użyciu `CreateSatelliteAssemblies` obiektu docelowego. |
| Satellite_CompanyName | .NET | Nazwa firmy do przekazania do *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_Configuration | .NET | Nazwa konfiguracji do przekazania do *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_Description | .NET | Tekst opisu do przekazania *AL.exe* podczas generowania zestawu satelickiego. |
| Satellite_EvidenceFile | .NET | Osadza określony plik w zestawie satelickim o nazwie zasobu "Security. dowód". |
| Satellite_FileVersion | .NET | Określa ciąg dla pola wersja pliku w zestawie satelickim. |
| Satellite_Flags | .NET | Określa wartość dla pola flags w zestawie satelickim. |
| Satellite_GenerateFullPaths | .NET | Powoduje, że zadanie kompilacji używa ścieżek bezwzględnych dla wszystkich plików zgłoszonych w komunikacie o błędzie. |
| Satellite_LinkResource | .NET | Łączy określone pliki zasobów z zestawem satelickim. |
| Satellite_MainEntryPoint | .NET | Określa w pełni kwalifikowaną nazwę (czyli Class. Method) metody do użycia jako punkt wejścia, gdy moduł jest konwertowany do pliku wykonywalnego podczas generowania zestawu satelickiego. |
| Satellite_ProductName | .NET | Określa ciąg dla pola Product w zestawie satelickim. |
| Satellite_ProductVersion | .NET | Określa ciąg dla pola ProductVersion w zestawie satelickim. |
| Satellite_TargetType | .NET | Określa format pliku wyjściowego zestawu satelickiego jako "Biblioteka", "exe" lub "win". Wartość domyślna to "Library". |
| Satellite_Title | .NET | Określa ciąg dla pola title w zestawie satelickim. |
| Satellite_Trademark | .NET | Określa ciąg dla pola znaku towarowego w zestawie satelickim. |
| Satellite_Version | .NET | Określa informacje o wersji dla zestawu satelickiego. |
| Satellite_Win32Icon | .NET | Wstawia plik ikony *. ico* w zestawie satelickim. |
| Satellite_Win32Resource | .NET | Wstawia zasób Win32 (plik *. res* ) do zestawu satelickiego. |
| SGenToolPath | .NET | Opcjonalna ścieżka narzędzia wskazująca, gdzie uzyskać *SGen.exe* , gdy bieżąca wersja *SGen.exe* zostanie zastąpiona. |
| SGenUseProxyTypes | .NET | Wartość logiczna wskazująca, czy typy proxy powinny być generowane przez *SGen.exe*. Ma to zastosowanie tylko wtedy, gdy *GenerateSerializationAssemblies* jest ustawiony na wartość włączone.<br /><br /> Obiekt docelowy SGen używa tej właściwości, aby ustawić flagę UseProxyTypes. Ta właściwość domyślnie ma wartość true, a nie ma interfejsu użytkownika umożliwiającego zmianę tego ustawienia. Aby wygenerować zestaw serializacji dla typów niezwiązanych z usługą WebService, należy dodać tę właściwość do pliku projektu i ustawić wartość false przed zaimportowaniem elementu *Microsoft. Common. targets* lub *C#/VB.targets*. |
| SkipInvalidConfigurations | Wszystko | `true`W przypadku wygenerowania ostrzeżenia dotyczącego nieprawidłowej platformy i kombinacji konfiguracji, ale kompilacja nie kończy się niepowodzeniem, gdy `false` lub niezdefiniowana (wartość domyślna), generuje błąd. |
| StartupObject | .NET | Określa klasę lub moduł, który zawiera metodę Main lub Sub Main. Ta właściwość jest równoważna z `/main` przełącznikiem kompilatora. |
| SubsystemVersion | .NET | Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny. Ta właściwość jest równoważna z `/subsystemversion` przełącznikiem kompilatora. Aby uzyskać informacje o domyślnej wartości tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Wersja .NET Compact Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TargetFrameworkVersion | .NET | Wersja .NET Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TreatWarningsAsErrors | .NET | Parametr logiczny, który powoduje, że `true` wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny z `/nowarn` przełącznikiem kompilatora. |
| UseHostCompilerIfAvailable | .NET | Parametr logiczny, który powoduje, że `true` zadanie kompilacji używa obiektu kompilatora w procesie, jeśli jest dostępny. Ten parametr jest używany tylko przez program Visual Studio. |
| Utf8output — | .NET | Parametr logiczny, który, jeśli `true` , rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny z `/utf8Output` przełącznikiem kompilatora. |
| VbcToolPath | Visual Basic | Opcjonalna ścieżka, która wskazuje inną lokalizację *vbc.exe* , gdy bieżąca wersja *vbc.exe* zostanie zastąpiona. |
| VbcVerbosity | Visual Basic | Określa poziom szczegółowości danych wyjściowych kompilatora Visual Basic. Prawidłowe wartości to "quiet", "normal" (wartość domyślna) lub "verbose". |
| VisualStudioVersion | Wszystko | Określa wersję programu Visual Studio, w ramach której ten projekt powinien być traktowany jako uruchomiony. Jeśli ta właściwość nie jest określona, MSBuild ustawi ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów do określenia zestawu obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4,0 lub wyższą dla projektu, służy `VisualStudioVersion` do określenia, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz zestaw [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Określa listę ostrzeżeń, które mają być traktowane jako błędy. Ten parametr jest równoważny z `/warnaserror` przełącznikiem kompilatora. |
| WarningsNotAsErrors | .NET | Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny z `/warnaserror` przełącznikiem kompilatora. |
| Win32Manifest | .NET | Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny z `/win32Manifest` przełącznikiem kompilatora. |
| Win32Resource | .NET | Nazwa pliku zasobu Win32, który ma zostać osadzony w końcowym zestawie. Ten parametr jest równoważny z `/win32resource` przełącznikiem kompilatora. |

## <a name="see-also"></a>Zobacz także

- [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
- [Wspólne metadane elementów programu MSBuild](common-msbuild-item-metadata.md)
- [Właściwości zarezerwowane i dobrze znane dla programu MSBuild](msbuild-reserved-and-well-known-properties.md)
- [Dokumentacja programu MSBuild dla projektów zestawu .NET SDK](/dotnet/core/project-sdk/msbuild-props)
