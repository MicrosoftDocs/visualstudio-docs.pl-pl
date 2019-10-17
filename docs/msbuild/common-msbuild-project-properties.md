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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38da720b63c8f5ba6d2ceb89fe8b414c6700cbcd
ms.sourcegitcommit: e82baa50bf5a65858c410882c2e86a552c2c1921
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381359"
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
| ApplicationManifest | Określa ścieżkę pliku, który jest używany do generowania informacji manifestu kontroli konta użytkownika zewnętrznego (UAC). Dotyczy tylko projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].<br /><br /> W większości przypadków manifest jest osadzony. Jednak w przypadku korzystania z bezpłatnego wdrożenia modelu COM lub [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest może być plikiem zewnętrznym, który jest instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji, zobacz Właściwość NoWin32Manifest w tym temacie. |
| AssemblyOriginatorKeyFile | Określa plik, który jest używany do podpisywania zestawu ( *. snk* lub *. pfx*) i który jest przesyłany do [zadania ResolveKeySource —](../msbuild/resolvekeysource-task.md) w celu wygenerowania klucza, który jest używany do podpisywania zestawu. |
| AssemblySearchPaths | Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność, w jakiej ścieżki pojawiają się na tej liście, ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami. |
| AssemblyName | Nazwa końcowego zestawu wyjściowego po skompilowaniu projektu. |
| BaseAddress | Określa adres podstawowy głównego zestawu wyjściowego. Ta właściwość jest równoważna z przełącznikiem kompilatora `/baseaddress`. |
| BaseOutputPath | Określa ścieżkę podstawową dla pliku wyjściowego. Jeśli jest ustawiona, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] będzie używać `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykładowa składnia: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BaseIntermediateOutputPath | Folder najwyższego poziomu, w którym są tworzone wszystkie pośrednie foldery wyjściowe specyficzne dla konfiguracji. Wartość domyślna to `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BuildInParallel | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane lub czyszczone równolegle w przypadku użycia wieloetapowego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Wartość domyślna to `true`, co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów. |
| BuildProjectReferences | Wartość logiczna wskazująca, czy odwołania projektu są kompilowane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Automatycznie Ustaw `false`, jeśli tworzysz projekt w zintegrowanym środowisku projektowym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE), `true` w przeciwnym razie. `-p:BuildProjectReferences=false` można określić w wierszu polecenia, aby uniknąć sprawdzania, czy odwołania do projektów są aktualne. |
| CleanFile | Nazwa pliku, który będzie używany jako "czyszczenie pamięci podręcznej". Czyszczenie pamięci podręcznej to Lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczany w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce. |
| CodePage | Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna z przełącznikiem kompilatora `/codepage`. |
| CompilerResponseFile | Opcjonalny plik odpowiedzi, który można przesłać do zadań kompilatora. |
| Konfiguracja | Konfiguracja, którą tworzysz, albo "debug" lub "Release" (wydanie). |
| CscToolPath | Ścieżka do pliku *CSC. exe*, kompilatora [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. |
| CustomBeforeMicrosoftCommonTargets | Nazwa pliku projektu lub pliku docelowego, który ma zostać zaimportowany automatycznie przed importem wspólnych obiektów docelowych. |
| DebugSymbols | Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **-p:DebugSymbols = false** w wierszu polecenia wyłącza generowanie plików symboli bazy danych programu ( *. pdb*). |
| DebugType | Definiuje poziom informacji debugowania, które mają zostać wygenerowane. Prawidłowe wartości to "Full", "pdbonly", "" Portable "," Embedded "i" none ". |
| DefineConstants | Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1 = wartość1; symbol2 = wartość2*<br /><br /> Właściwość jest równoważna z przełącznikiem kompilatora `/define`. |
| DefineDebug | Wartość logiczna wskazująca, czy ma być zdefiniowana stała debugowania. |
| DefineTrace | Wartość logiczna wskazująca, czy ma być zdefiniowana stała śledzenia. |
| DelaySign | Wartość logiczna wskazująca, czy chcesz opóźnić podpisywanie zestawu, a nie pełnego podpisywania. |
| Deterministyczne | Wartość logiczna wskazująca, czy kompilator powinien generować identyczne zestawy dla identycznych danych wejściowych. Ten parametr odnosi się do przełącznika `/deterministic` w kompilatorach *VBC. exe* i *CSC. exe* . |
| DisabledWarnings | Pomija określone ostrzeżenia. Należy określić tylko część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do przełącznika `/nowarn` kompilatora *VBC. exe* . |
| DisableFastUpToDateCheck | Wartość logiczna, która ma zastosowanie tylko do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Menedżer kompilacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] używa procesu o nazwie FastUpToDateCheck, aby określić, czy projekt musi zostać odbudowany, aby był aktualny. Ten proces jest szybszy niż użycie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] w celu określenia tego procesu. Ustawienie właściwości DisableFastUpToDateCheck na wartość `true` umożliwia ominięcie Menedżera kompilacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i wymuszenie użycia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] w celu ustalenia, czy projekt jest aktualny. |
| DocumentationFile | Nazwa pliku, który jest generowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie zawiera informacji o ścieżce. |
| ErrorReport | Określa sposób, w jaki zadanie kompilatora powinno raportować wewnętrzne błędy kompilatora. Prawidłowe wartości to "Prompt", "Send" i "none". Ta właściwość jest równoważna z przełącznikiem kompilatora `/errorreport`. |
| ExcludeDeploymentUrl | [Zadanie GenerateDeploymentManifest —](../msbuild/generatedeploymentmanifest-task.md) dodaje tag deploymentProvider do manifestu wdrożenia, jeśli plik projektu zawiera dowolny z następujących elementów:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl można jednak zapobiec dodawaniu znacznika deploymentProvider do manifestu wdrożenia, nawet jeśli określono którykolwiek z powyższych adresów URL. Aby to zrobić, Dodaj następującą właściwość do pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Uwaga:**  ExcludeDeploymentUrl nie jest ujawniona w środowisku IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i może być ustawiana tylko przez ręczne edytowanie pliku projektu. Ustawienie tej właściwości nie ma wpływu na publikowanie w ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; oznacza to, że tag deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl. |
| FileAlignment | Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest równoważna z przełącznikiem kompilatora `/filealignment`. |
| FrameworkPathOverride | Określa lokalizację plików *mscorlib. dll* i *Microsoft. VisualBasic. dll*. Ten parametr jest równoważny z przełącznikiem `/sdkpath` kompilatora *VBC. exe* . |
| GenerateDocumentation | (C#, Visual Basic) Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true`, kompilacja generuje informacje o dokumentacji i umieszcza je w pliku *. XML* wraz z nazwą pliku wykonywalnego lub biblioteki utworzoną przez zadanie kompilacji. |
| GenerateSerializationAssemblies | Wskazuje, czy zestawy serializacji XML powinny być generowane przez *Sgen. exe*, które mogą być ustawione na wartość on, autolub off. Ta właściwość jest używana dla zestawów, które są przeznaczone tylko .NET Framework. Aby wygenerować zestawy serializacji XML dla .NET Standard lub zestawów .NET Core, odwołując się do pakietu NuGet *Microsoft. XmlSerializer. Generator* . |
| IntermediateOutputPath | Pełna pośrednia Ścieżka wyjściowa jako pochodna z `BaseIntermediateOutputPath`, jeśli nie określono ścieżki. Na przykład *\obj\debug @ no__t-1*. |
| NazwaKonteneraKlucza | Nazwa kontenera klucza o silnej nazwie. |
| KeyOriginatorFile | Nazwa pliku klucza o silnej nazwie. |
| MSBuildProjectExtensionsPath | Określa ścieżkę, w której znajdują się rozszerzenia projektu. Domyślnie ma to taką samą wartość jak `BaseIntermediateOutputPath`. |
| Moduleassemblyname — | Nazwa zestawu, do którego ma zostać dołączony skompilowany moduł. Właściwość jest równoważna z przełącznikiem kompilatora `/moduleassemblyname`. |
| NoLogo | Wartość logiczna wskazująca, czy logo kompilatora ma być wyłączone. Ta właściwość jest równoważna z przełącznikiem kompilatora `/nologo`. |
| NoStdLib | Wartość logiczna wskazująca, czy należy unikać odwoływania się do biblioteki standardowej (*mscorlib. dll*). Wartość domyślna to `false`. |
| NoVBRuntimeReference | Wartość logiczna wskazująca, czy środowisko uruchomieniowe [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] (*Microsoft. VisualBasic. dll*) powinno być dołączone jako odwołanie w projekcie. |
| NoWin32Manifest | Wartość logiczna wskazująca, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w pliku wykonywalnym aplikacji. Dotyczy tylko projektów programu Visual Studio przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrożonych przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestracji ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) są osadzone w pliku wykonywalnym aplikacji. `True` Określa, że informacje manifestu kontroli konta użytkownika nie są osadzone.<br /><br /> Ta właściwość dotyczy tylko projektów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przeznaczonych dla [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W projektach wdrożonych przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i COM bez rejestracji ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] osadzał informacje manifestu w pliku wykonywalnym aplikacji; Ten proces jest nazywany *wirtualizacją*. Aby używać wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` w następujący sposób:<br /><br /> -Dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów Usuń węzeł `<ApplicationManifest>`. (W projektach [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] `<NoWin32Manifest>` jest ignorowany, gdy istnieje węzeł `<ApplicationManifest>`).<br />— W przypadku projektów [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Ustaw `<ApplicationManifest>` na `False` i `<NoWin32Manifest>`, aby `True`. (W przypadku projektów [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] `<ApplicationManifest>` zastępuje `<NoWin32Manifest>`).<br /> Ta właściwość jest równoważna z przełącznikiem kompilatora `/nowin32manifest` programu *VBC. exe*. |
| Zoptymalizować | Wartość logiczna, która po ustawieniu na `true` umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optimize`. |
| OptionCompare | Określa sposób, w jaki są wykonywane porównania ciągów. Prawidłowe wartości to "Binary" lub "text". Ta właściwość jest równoważna z przełącznikiem kompilatora `/optioncompare` programu *VBC. exe*. |
| OptionExplicit | Wartość logiczna, która po ustawieniu na `true` wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optionexplicit`. |
| OptionInfer | Wartość logiczna, która po ustawieniu na `true` zezwala na wnioskowanie o typie zmiennych. Ta właściwość jest równoważna z przełącznikiem kompilatora `/optioninfer`. |
| OptionStrict | Wartość logiczna, która po ustawieniu na `true` powoduje, że zadanie kompilacji wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna z przełącznikiem `/optionstrict` kompilatora *VBC. exe* . |
| OutputPath | Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład *bin\Debug*. |
| OutputType | Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> Biblioteki. Tworzy bibliotekę kodu. (Wartość domyślna).<br />Exe. Tworzy aplikację konsolową.<br />Elementu. Tworzy moduł.<br />Winexe. Tworzy program oparty na systemie Windows.<br /><br /> Ta właściwość jest równoważna z przełącznikiem `/target` kompilatora *VBC. exe* . |
| OverwriteReadOnlyFiles | Wartość logiczna wskazująca, czy chcesz włączyć kompilację w celu zastąpienia plików tylko do odczytu, czy wyzwolenia błędu. |
| Elemencie pathmap | Określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych wyjściowych przez kompilator. Ta właściwość jest równoważna z przełącznikiem `/pathmap` kompilatora *CSC. exe* . |
| PdbFile | Nazwa pliku *. pdb* , który emituje. Ta właściwość jest równoważna z przełącznikiem `/pdb` kompilatora *CSC. exe* . |
| Platforma | System operacyjny, dla którego tworzysz. Prawidłowe wartości to "dowolny procesor CPU", "x86" i "x64". |
| ProduceReferenceAssembly | Wartość logiczna, która po ustawieniu na `true` włącza produkcję [zestawów referencyjnych](https://github.com/dotnet/roslyn/blob/master/docs/features/refout.md) dla bieżącego zestawu. w przypadku korzystania z tej funkcji `Deterministic` powinna być `true`. Ta właściwość odpowiada przełącznikowi `/refout` kompilatorów *VBC. exe* i *CSC. exe* . |
| ProduceOnlyReferenceAssembly | Wartość logiczna, która powoduje, że kompilator emituje tylko zestaw odniesienia zamiast skompilowanego kodu. Nie można używać w połączeniu z `ProduceReferenceAssembly`.  Ta właściwość odpowiada przełącznikowi `/refonly` kompilatorów *VBC. exe* i *CSC. exe* . |
| RemoveIntegerChecks | Wartość logiczna wskazująca, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest równoważna z przełącznikiem `/removeintchecks` kompilatora *VBC. exe* . |
| SGenUseProxyTypes | Wartość logiczna wskazująca, czy typy proxy powinny być generowane przez *Sgen. exe*. Ma to zastosowanie tylko wtedy, gdy *GenerateSerializationAssemblies* jest ustawiona na wartość on i tylko dla .NET Framework.<br /><br /> Obiekt docelowy SGen używa tej właściwości, aby ustawić flagę UseProxyTypes. Ta właściwość domyślnie ma wartość true, a nie ma interfejsu użytkownika umożliwiającego zmianę tego ustawienia. Aby wygenerować zestaw serializacji dla typów niezwiązanych z usługą WebService, należy dodać tę właściwość do pliku projektu i ustawić wartość false przed zaimportowaniem elementu *Microsoft. Common. targets* lub  *C#/VB.targets*. |
| SGenToolPath | Opcjonalna ścieżka narzędzia, która wskazuje, gdzie uzyskać *Sgen. exe* , gdy bieżąca wersja pliku *Sgen. exe* zostanie zastąpiona. Ta właściwość jest używana tylko dla .NET Framework.|
| StartupObject | Określa klasę lub moduł, który zawiera metodę Main lub Sub Main. Ta właściwość jest równoważna z przełącznikiem kompilatora `/main`. |
| ProcessorArchitecture | Architektura procesora, która jest używana podczas rozwiązywania odwołań do zestawów. Prawidłowe wartości to "MSIL", "x86", "amd64" lub "ia64". |
| RootNamespace | Główna przestrzeń nazw, która ma być używana przy nazwie zasobu osadzonego. Ta przestrzeń nazw jest częścią osadzonej nazwy manifestu zasobu. |
| Satellite_AlgorithmId | Identyfikator algorytmu wyznaczania wartości skrótu *Al. exe* do użycia podczas tworzenia zestawów satelickich. |
| Satellite_BaseAddress | Adres podstawowy, który ma być używany w przypadku kompilowania zestawów satelickich specyficznych dla kultury przy użyciu obiektu docelowego `CreateSatelliteAssemblies`. |
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
| SubsystemVersion | Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny. Ta właściwość jest równoważna z przełącznikiem kompilatora `/subsystemversion`. Aby uzyskać informacje o domyślnej wartości tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | Wersja .NET Compact Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TargetFrameworkVersion | Wersja .NET Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie. |
| TreatWarningsAsErrors | Parametr logiczny, który, jeśli `true`, powoduje, że wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/nowarn`. |
| UseHostCompilerIfAvailable | Parametr logiczny, który, jeśli `true`, powoduje, że zadanie kompilacji używa obiektu kompilatora w procesie, jeśli jest dostępny. Ten parametr jest używany tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Utf8output — | Parametr logiczny, który, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny z przełącznikiem kompilatora `/utf8Output`. |
| VbcToolPath | Opcjonalna ścieżka, która wskazuje inną lokalizację programu *VBC. exe* , gdy bieżąca wersja pliku *VBC. exe* zostanie zastąpiona. |
| VbcVerbosity | Określa poziom szczegółowości danych wyjściowych kompilatora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Prawidłowe wartości to "quiet", "normal" (wartość domyślna) lub "verbose". |
| VisualStudioVersion | Określa wersję programu Visual Studio, w ramach której ten projekt powinien być traktowany jako uruchomiony. Jeśli ta właściwość nie jest określona, MSBuild ustawi ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów do określenia zestawu obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4,0 lub wyższą dla projektu, `VisualStudioVersion` służy do określenia, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz zestaw [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | Określa listę ostrzeżeń, które mają być traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/warnaserror`. |
| WarningsNotAsErrors | Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny z przełącznikiem kompilatora `/warnaserror`. |
| Win32Manifest | Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny z przełącznikiem kompilatora `/win32Manifest`. |
| Win32Resource | Nazwa pliku zasobu Win32, który ma zostać osadzony w końcowym zestawie. Ten parametr jest równoważny z przełącznikiem kompilatora `/win32resource`. |

## <a name="see-also"></a>Zobacz także
- [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
