---
title: Wspólne właściwości projektu MSBuild | Microsoft Docs
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
ms.openlocfilehash: 1eb56d1334eb18dd5872457d032e5780a3f75eb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698720"
---
# <a name="common-msbuild-project-properties"></a>Wspólne właściwości projektów MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W poniższej tabeli wymieniono często używane właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w plikach. targets udostępnianych przez program MSBuild.  
  
 Pliki projektu w programie Visual Studio (. csproj,. vbproj, vcxproj i inne) zawierają kod XML programu MSBuild, który jest uruchamiany podczas kompilowania projektu przy użyciu środowiska IDE. Projekty zwykle importują jeden lub więcej plików. targets, aby zdefiniować ich proces kompilacji. Aby uzyskać więcej informacji, zobacz [. Pliki docelowe](../msbuild/msbuild-dot-targets-files.md).  
  
## <a name="list-of-common-properties-and-parameters"></a>Lista typowych właściwości i parametrów  
  
|Nazwa właściwości lub parametru|Opis|  
|--------------------------------|-----------------|  
|AdditionalLibPaths|Określa dodatkowe foldery, w których kompilatory powinny szukać zestawów referencyjnych.|  
|AddModules|Powoduje, że kompilator udostępnia wszystkie informacje o typie z określonych plików dla kompilowanego projektu. Ta właściwość jest równoważna z `/addModules` przełącznikiem kompilatora.|  
|ALToolPath|Ścieżka, w której można znaleźć AL.exe. Ta właściwość zastępuje bieżącą wersję AL.exe, aby umożliwić korzystanie z innej wersji.|  
|ApplicationIcon|Plik ikony. ico do przekazania do kompilatora w celu osadzenia jako ikona Win32. Właściwość jest równoważna z `/win32icon` przełącznikiem kompilatora.|  
|ApplicationManifest|Określa ścieżkę pliku, który jest używany do generowania informacji manifestu kontroli konta użytkownika zewnętrznego (UAC). Dotyczy tylko projektów programu Visual Studio przeznaczonych dla elementów docelowych [!INCLUDE[windowsver](../includes/windowsver-md.md)] .<br /><br /> W większości przypadków manifest jest osadzony. Jeśli jednak korzystasz z rejestracji bezpłatnej COM lub [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia, manifest może być plikiem zewnętrznym, który jest instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji, zobacz Właściwość NoWin32Manifest w tym temacie.|  
|AssemblyOriginatorKeyFile|Określa plik, który jest używany do podpisywania zestawu (. snk lub. pfx) i który jest przesyłany do [zadania ResolveKeySource —](../msbuild/resolvekeysource-task.md) w celu wygenerowania klucza, który jest używany do podpisywania zestawu.|  
|AssemblySearchPaths|Lista lokalizacji do przeszukania podczas rozpoznawania zestawu odwołania w czasie kompilacji. Kolejność, w jakiej ścieżki pojawiają się na tej liście, ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami.|  
|AssemblyName|Nazwa końcowego zestawu wyjściowego po skompilowaniu projektu.|  
|BaseAddress|Określa adres podstawowy głównego zestawu wyjściowego. Ta właściwość jest równoważna z `/baseaddress` przełącznikiem kompilatora.|  
|BaseOutputPath|Określa ścieżkę podstawową dla pliku wyjściowego. Jeśli jest ustawiona, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] będzie używać `OutputPath = $(BaseOutputPath)\$(Configuration)\` . Przykładowa składnia: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>`|  
|BaseIntermediateOutputPath|Folder najwyższego poziomu, w którym są tworzone wszystkie pośrednie foldery wyjściowe specyficzne dla konfiguracji. Wartość domyślna to `obj\`. Poniższy kod jest przykładem: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>`|  
|BuildInParallel|Wartość logiczna wskazująca, czy odwołania projektu są kompilowane lub czyszczone równolegle w przypadku użycia wieloetapowego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Wartość domyślna to `true` , co oznacza, że projekty będą kompilowane równolegle, jeśli system ma wiele rdzeni lub procesorów.|  
|BuildProjectReferences|Wartość logiczna wskazująca, czy odwołania projektu są kompilowane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Ustaw `false` , jeśli tworzysz projekt w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE), w `true` przeciwnym razie.|  
|CleanFile|Nazwa pliku, który będzie używany jako "czyszczenie pamięci podręcznej". Czyszczenie pamięci podręcznej to Lista wygenerowanych plików, które zostaną usunięte podczas operacji czyszczenia. Plik jest umieszczany w pośredniej ścieżce wyjściowej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce.|  
|CodePage|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest równoważna z `/codepage` przełącznikiem kompilatora.|  
|CompilerResponseFile|Opcjonalny plik odpowiedzi, który można przesłać do zadań kompilatora.|  
|Konfigurowanie|Konfiguracja, którą tworzysz, albo "debug" lub "Release" (wydanie).|  
|CscToolPath|Ścieżka csc.exe, [!INCLUDE[csprcs](../includes/csprcs-md.md)] kompilator.|  
|CustomBeforeMicrosoftCommonTargets|Nazwa pliku projektu lub pliku docelowego, który ma zostać zaimportowany automatycznie przed importem wspólnych obiektów docelowych.|  
|DebugSymbols|Wartość logiczna wskazująca, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **/p: DebugSymbols = false** w wierszu polecenia wyłącza generowanie plików symboli bazy danych programu (. pdb).|  
|DefineConstants|Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1 = wartość1; symbol2 = wartość2*<br /><br /> Właściwość jest równoważna z `/define` przełącznikiem kompilatora.|  
|DefineDebug|Wartość logiczna wskazująca, czy ma być zdefiniowana stała debugowania.|  
|DefineTrace|Wartość logiczna wskazująca, czy ma być zdefiniowana stała śledzenia.|  
|DebugType|Definiuje poziom informacji debugowania, które mają zostać wygenerowane. Prawidłowe wartości to "Full", "pdbonly" i "none".|  
|DelaySign|Wartość logiczna wskazująca, czy chcesz opóźnić podpisywanie zestawu, a nie pełnego podpisywania.|  
|DisabledWarnings|Pomija określone ostrzeżenia. Należy określić tylko część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do `/nowarn` przełącznika kompilatora vbc.exe.|  
|DisableFastUpToDateCheck|Wartość logiczna, która ma zastosowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tylko do. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Menedżer kompilacji używa procesu o nazwie FastUpToDateCheck, aby określić, czy projekt musi zostać odbudowany, aby był aktualny. Ten proces jest szybszy niż użycie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , aby to ustalić. Ustawienie właściwości DisableFastUpToDateCheck umożliwia `true` ominięcie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Menedżera kompilacji i wymuszenie użycia [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do określenia, czy projekt jest aktualny.|  
|DocumentationFile|Nazwa pliku, który jest generowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie zawiera informacji o ścieżce.|  
|ErrorReport|Określa sposób, w jaki zadanie kompilatora powinno raportować wewnętrzne błędy kompilatora. Prawidłowe wartości to "Prompt", "Send" i "none". Ta właściwość jest równoważna z `/errorreport` przełącznikiem kompilatora.|  
|ExcludeDeploymentUrl|[Zadanie GenerateDeploymentManifest —](../msbuild/generatedeploymentmanifest-task.md) dodaje tag deploymentProvider do manifestu wdrożenia, jeśli plik projektu zawiera dowolny z następujących elementów:<br /><br /> - UpdateUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl można jednak zapobiec dodawaniu znacznika deploymentProvider do manifestu wdrożenia, nawet jeśli określono którykolwiek z powyższych adresów URL. Aby to zrobić, Dodaj następującą właściwość do pliku projektu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>`**Uwaga:**  ExcludeDeploymentUrl nie jest ujawniona w środowisku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE i może być ustawiana tylko przez ręczne edytowanie pliku projektu. Ustawienie tej właściwości nie wpływa na publikowanie w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ; oznacza to, że tag deploymentProvider nadal zostanie dodany do adresu URL określonego przez PublishUrl.|  
|FileAlignment|Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest równoważna z `/filealignment` przełącznikiem kompilatora.|  
|FrameworkPathOverride|Określa lokalizację mscorlib.dll i microsoft.visualbasic.dll. Ten parametr jest równoważny z `/sdkpath` przełącznikiem kompilatora vbc.exe.|  
|GenerateDocumentation|Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true` kompilacja generuje informacje o dokumentacji i umieszcza je w pliku. XML wraz z nazwą pliku wykonywalnego lub biblioteki utworzonej przez zadanie kompilacji.|  
|IntermediateOutputPath|Pełna pośrednia Ścieżka wyjściowa jako pochodna `BaseIntermediateOutputPath` , jeśli nie określono ścieżki. Na przykład \obj\debug \\ . Jeśli ta właściwość jest zastępowana, ustawienie `BaseIntermediateOutputPath` nie będzie miało żadnego efektu.|  
|NazwaKonteneraKlucza|Nazwa kontenera klucza o silnej nazwie.|  
|KeyOriginatorFile|Nazwa pliku klucza o silnej nazwie.|  
|NoWin32Manifest|Określa, czy kompilator generuje domyślny manifest Win32 w zestawie danych wyjściowych. Wartość domyślna to `false` oznacza, że domyślny manifest Win32 jest generowany dla wszystkich aplikacji. Ta właściwość jest równoważna z `/nowin32manifest` przełącznikiem kompilatora vbc.exe.|  
|Moduleassemblyname —|Nazwa zestawu, do którego ma zostać dołączony skompilowany moduł. Właściwość jest równoważna z `/moduleassemblyname` przełącznikiem kompilatora.|  
|NoLogo|Wartość logiczna wskazująca, czy logo kompilatora ma być wyłączone. Ta właściwość jest równoważna z `/nologo` przełącznikiem kompilatora.|  
|NoStdLib|Wartość logiczna wskazująca, czy należy unikać odwoływania się do biblioteki standardowej (mscorlib.dll). Wartość domyślna to `false`.|  
|NoVBRuntimeReference|Wartość logiczna wskazująca, czy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] środowisko uruchomieniowe (Microsoft.VisualBasic.dll) powinno być dołączone jako odwołanie w projekcie.|  
|NoWin32Manifest|Wartość logiczna wskazująca, czy informacje manifestu kontroli konta użytkownika (UAC) będą osadzone w pliku wykonywalnym aplikacji. Dotyczy tylko projektów programu Visual Studio przeznaczonych dla elementów docelowych [!INCLUDE[windowsver](../includes/windowsver-md.md)] . W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i w modelu COM bez rejestracji ten element jest ignorowany. `False` (wartość domyślna) określa, że informacje manifestu kontroli konta użytkownika (UAC) są osadzone w pliku wykonywalnym aplikacji. `True` Określa, że informacje manifestu kontroli konta użytkownika nie są osadzone.<br /><br /> Ta właściwość ma zastosowanie tylko do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektów docelowych [!INCLUDE[windowsver](../includes/windowsver-md.md)] . W projektach wdrożonych za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i w modelu COM bez rejestracji ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodawać tylko wtedy, gdy nie chcesz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] osadzać żadnych informacji manifestu w pliku wykonywalnym aplikacji. ten proces jest nazywany *wirtualizacją*. Aby używać wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu w `<NoWin32Manifest>` następujący sposób:<br /><br /> — W przypadku [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów Usuń `<ApplicationManifest>` węzeł. (W [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektach `<NoWin32Manifest>` jest ignorowany w przypadku `<ApplicationManifest>` istnienia węzła).<br />— W przypadku [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów ustaw `<ApplicationManifest>` wartość `False` i `<NoWin32Manifest>` na `True` . (W [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektach, `<ApplicationManifest>` zastąpienia `<NoWin32Manifest>` ).|  
|Optymalizacja|Wartość logiczna, która po ustawieniu na `true` , umożliwia optymalizacje kompilatora. Ta właściwość jest równoważna z `/optimize` przełącznikiem kompilatora.|  
|OptionCompare|Określa sposób, w jaki są wykonywane porównania ciągów. Prawidłowe wartości to "Binary" lub "text". Ta właściwość jest równoważna z `/optioncompare` przełącznikiem kompilatora vbc.exe.|  
|OptionExplicit|Wartość logiczna, która po ustawieniu na `true` , wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest równoważna z `/optionexplicit` przełącznikiem kompilatora.|  
|OptionInfer|Wartość logiczna, która po ustawieniu na `true` , umożliwia wnioskowanie o typie zmiennych. Ta właściwość jest równoważna z `/optioninfer` przełącznikiem kompilatora.|  
|OptionStrict|Wartość logiczna, która po ustawieniu na `true` , powoduje, że zadanie kompilacji Wymuszaj semantykę typu ścisłego w celu ograniczenia niejawnych konwersji typów. Ta właściwość jest równoważna z `/optionstrict` przełącznikiem kompilatora vbc.exe.|  
|OutputPath|Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład "bin\Debug".|  
|OutputType|Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> Biblioteki. Tworzy bibliotekę kodu. (Wartość domyślna).<br />Exe. Tworzy aplikację konsolową.<br />Elementu. Tworzy moduł.<br />Winexe. Tworzy program oparty na systemie Windows.<br /><br /> Ta właściwość jest równoważna z `/target` przełącznikiem kompilatora vbc.exe.|  
|OverwriteReadOnlyFiles|Wartość logiczna wskazująca, czy chcesz włączyć kompilację w celu zastąpienia plików tylko do odczytu, czy wyzwolenia błędu.|  
|PdbFile|Nazwa pliku. pdb, który emituje. Ta właściwość jest równoważna z `/pdb` przełącznikiem kompilatora csc.exe.|  
|Platforma|System operacyjny, dla którego tworzysz. Prawidłowe wartości to "dowolny procesor CPU", "x86" i "x64".|  
|RemoveIntegerChecks|Wartość logiczna wskazująca, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ta właściwość jest równoważna z `/removeintchecks` przełącznikiem kompilatora vbc.exe.|  
|SGenUseProxyTypes|Wartość logiczna wskazująca, czy typy proxy powinny być generowane przez SGen.exe.<br /><br /> Obiekt docelowy SGen używa tej właściwości, aby ustawić flagę UseProxyTypes. Ta właściwość domyślnie ma wartość true, a nie ma interfejsu użytkownika umożliwiającego zmianę tego ustawienia. Aby wygenerować zestaw serializacji dla typów innych niż WebService, Dodaj tę właściwość do pliku projektu i ustaw dla niego wartość false przed zaimportowaniem elementu Microsoft. Common. targets lub C#/VB.targets.|  
|SGenToolPath|Opcjonalna ścieżka narzędzia wskazująca, gdzie uzyskać SGen.exe, gdy bieżąca wersja SGen.exe zostanie zastąpiona.|  
|StartupObject|Określa klasę lub moduł, który zawiera metodę Main lub Sub Main. Ta właściwość jest równoważna z `/main` przełącznikiem kompilatora.|  
|ProcessorArchitecture|Architektura procesora, która jest używana podczas rozwiązywania odwołań do zestawów. Prawidłowe wartości to "MSIL", "x86", "amd64" lub "ia64".|  
|RootNamespace|Główna przestrzeń nazw, która ma być używana przy nazwie zasobu osadzonego. Ta przestrzeń nazw jest częścią osadzonej nazwy manifestu zasobu.|  
|Satellite_AlgorithmId|Identyfikator algorytmu wyznaczania wartości skrótu AL.exe, który ma być używany podczas tworzenia zestawów satelickich.|  
|Satellite_BaseAddress|Adres podstawowy, który ma być używany w przypadku kompilowania zestawów satelickich specyficznych dla kultury przy użyciu `CreateSatelliteAssemblies` obiektu docelowego.|  
|Satellite_CompanyName|Nazwa firmy do przekazania do AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_Configuration|Nazwa konfiguracji do przekazania do AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_Description|Tekst opisu do przekazania AL.exe podczas generowania zestawu satelickiego.|  
|Satellite_EvidenceFile|Osadza określony plik w zestawie satelickim o nazwie zasobu "Security. dowód".|  
|Satellite_FileVersion|Określa ciąg dla pola wersja pliku w zestawie satelickim.|  
|Satellite_Flags|Określa wartość dla pola flags w zestawie satelickim.|  
|Satellite_GenerateFullPaths|Powoduje, że zadanie kompilacji używa ścieżek bezwzględnych dla wszystkich plików zgłoszonych w komunikacie o błędzie.|  
|Satellite_LinkResource|Łączy określone pliki zasobów z zestawem satelickim.|  
|Satellite_MainEntryPoint|Określa w pełni kwalifikowaną nazwę (czyli Class. Method) metody do użycia jako punkt wejścia, gdy moduł jest konwertowany do pliku wykonywalnego podczas generowania zestawu satelickiego.|  
|Satellite_ProductName|Określa ciąg dla pola Product w zestawie satelickim.|  
|Satellite_ProductVersion|Określa ciąg dla pola ProductVersion w zestawie satelickim.|  
|Satellite_TargetType|Określa format pliku wyjściowego zestawu satelickiego jako "Biblioteka", "exe" lub "win". Wartość domyślna to "Library".|  
|Satellite_Title|Określa ciąg dla pola title w zestawie satelickim.|  
|Satellite_Trademark|Określa ciąg dla pola znaku towarowego w zestawie satelickim.|  
|Satellite_Version|Określa informacje o wersji dla zestawu satelickiego.|  
|Satellite_Win32Icon|Wstawia plik ikony. ico w zestawie satelickim.|  
|Satellite_Win32Resource|Wstawia zasób Win32 (plik. res) do zestawu satelickiego.|  
|SubsystemVersion|Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny. Ta właściwość jest równoważna z `/subsystemversion` przełącznikiem kompilatora. Aby uzyskać informacje o domyślnej wartości tej właściwości, zobacz [/subsystemversion (Visual Basic)](https://msdn.microsoft.com/library/08be22b2-f447-4cd3-8203-120b1b920b54) lub [/subsystemversion (opcje kompilatora C#)](https://msdn.microsoft.com/library/a99fce81-9d92-4813-9874-bee777041445).|  
|TargetCompactFramework|Wersja .NET Compact Framework, która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie.|  
|TargetFrameworkVersion|Wersja programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , która jest wymagana do uruchomienia aplikacji, która jest tworzona. Określenie tej opcji pozwala odwoływać się do niektórych zestawów struktur, które mogą nie być w stanie odwołać się w przeciwnym razie.|  
|TreatWarningsAsErrors|Parametr logiczny, który powoduje, że `true` wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest równoważny z `/nowarn` przełącznikiem kompilatora.|  
|UseHostCompilerIfAvailable|Parametr logiczny, który powoduje, że `true` zadanie kompilacji używa obiektu kompilatora w procesie, jeśli jest dostępny. Ten parametr jest używany tylko przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|Utf8output —|Parametr logiczny, który, jeśli `true` , rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest równoważny z `/utf8Output` przełącznikiem kompilatora.|  
|VbcToolPath|Opcjonalna ścieżka, która wskazuje inną lokalizację vbc.exe, gdy bieżąca wersja vbc.exe zostanie zastąpiona.|  
|VbcVerbosity|Określa poziom szczegółowości [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] danych wyjściowych kompilatora. Prawidłowe wartości to "quiet", "normal" (wartość domyślna) lub "verbose".|  
|VisualStudioVersion|Określa wersję programu Visual Studio, w ramach której ten projekt powinien być traktowany jako uruchomiony. Jeśli ta właściwość nie jest określona, MSBuild ustawi ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektów do określenia zestawu obiektów docelowych, które są używane dla kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4,0 lub wyższą dla projektu, służy `VisualStudioVersion` do określenia, który podzestaw narzędzi ma być używany. Aby uzyskać więcej informacji, zobacz zestaw [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).|  
|WarningsAsErrors|Określa listę ostrzeżeń, które mają być traktowane jako błędy. Ten parametr jest równoważny z `/warnaserror` przełącznikiem kompilatora.|  
|WarningsNotAsErrors|Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest równoważny z `/warnaserror` przełącznikiem kompilatora.|  
|Win32Manifest|Nazwa pliku manifestu, który powinien być osadzony w końcowym zestawie. Ten parametr jest równoważny z `/win32Manifest` przełącznikiem kompilatora.|  
|Win32Resource|Nazwa pliku zasobu Win32, który ma zostać osadzony w końcowym zestawie. Ten parametr jest równoważny z `/win32resource` przełącznikiem kompilatora.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wspólne elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
