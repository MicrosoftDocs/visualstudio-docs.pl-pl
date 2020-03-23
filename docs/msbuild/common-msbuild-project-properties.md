---
title: Typowe właściwości projektu MSBuild | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634425"
---
# <a name="common-msbuild-project-properties"></a>Typowe właściwości projektu MSBuild

W poniższej tabeli wymieniono często używane właściwości, które są zdefiniowane w plikach projektu programu Visual Studio lub zawarte w *plikach .targets,* które zapewnia MSBuild.

 Pliki projektu w programie Visual Studio (*.csproj*, *.vbproj*, *.vcxproj*i inne) zawierają kod XML MSBuild, który jest uruchamiany podczas tworzenia projektu przy użyciu IDE. Projekty zazwyczaj importują jeden lub więcej plików *obiektów .targets w* celu zdefiniowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [MSBuild .targets files](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Lista wspólnych właściwości i parametrów

| Nazwa właściwości lub parametru | Opis |
|------------------------------------| - |
| AdditionalLibPaths (Ścieżki dodatkowe liczą się) | Określa dodatkowe foldery, w których kompilatory powinny szukać zestawów odwołań. |
| Dodawaniemodule | Powoduje, że kompilator, aby wszystkie informacje o typie z określonych plików dostępne dla projektu, który są kompilowane. Ta właściwość jest `/addModules` odpowiednikiem przełącznika kompilatora. |
| ALToolPath (AlToolPath) | Ścieżka, w której można znaleźć *plik AL.exe.* Ta właściwość zastępuje bieżącą wersję *programu AL.exe,* aby umożliwić korzystanie z innej wersji. |
| ApplicationIcon (Formularz wniosku) | Plik *ikony .ico,* który ma być przekazywaniem do kompilatora w celu osadzania jako ikony Win32. Właściwość jest odpowiednikiem przełącznika kompilatora. `/win32icon` |
| AplikacjaManifest | Określa ścieżkę pliku używanego do generowania informacji manifestu kontroli konta użytkownika zewnętrznego. Dotyczy tylko projektów programu Visual Studio kierowanych na system Windows Vista.<br /><br /> W większości przypadków manifest jest osadzony. Jednak jeśli używasz rejestracji wolne COM lub ClickOnce wdrożenia, manifest może być plik zewnętrzny, który jest instalowany razem z zestawami aplikacji. Aby uzyskać więcej informacji, zobacz NoWin32Manifest właściwości w tym temacie. |
| Plik klawiszy AssemblyOriginator | Określa plik, który jest używany do podpisywania zestawu (*.snk* lub *.pfx*) i który jest przekazywany do [resolvekeysource zadanie](../msbuild/resolvekeysource-task.md) do generowania rzeczywistego klucza, który jest używany do podpisania zestawu. |
| Ścieżki wyszukiwania zestawu | Lista lokalizacji do wyszukiwania podczas rozpoznawania zestawu odwołań odniesienia w czasie kompilacji. Kolejność, w jakiej ścieżki pojawiają się na tej liście ma znaczenie, ponieważ ścieżki wymienione wcześniej mają pierwszeństwo przed późniejszymi wpisami. |
| Assemblyname | Nazwa końcowego zestawu wyjściowego po zbudowaniu projektu. |
| Baseaddress | Określa adres podstawowy głównego złożenia wyjściowego. Ta właściwość jest `/baseaddress` odpowiednikiem przełącznika kompilatora. |
| Ścieżka bazowa | Folder najwyższego poziomu, w którym tworzone są wszystkie pośrednie foldery wyjściowe specyficzne dla konfiguracji. Wartością domyślną jest `obj\`. Przykładem jest następujący kod:`<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| Ścieżka bazowa | Określa ścieżkę bazową dla pliku wyjściowego. Jeśli jest ustawiona, MSBuild użyje `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Przykładowa składnia:`<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| Buildinparallel | Wartość logiczna, która wskazuje, czy odwołania do projektu są budowane lub czyszczone równolegle, gdy używany jest Multi-Proc MSBuild. Wartością domyślną jest `true`, co oznacza, że projekty będą budowane równolegle, jeśli system ma wiele rdzeni lub procesorów. |
| BuildProjectReferences | Wartość logiczna, która wskazuje, czy odwołania do projektu są tworzone przez MSBuild. Automatycznie ustawia `false` się, jeśli budujesz projekt w zintegrowanym środowisku programistycznym Visual Studio (IDE), `true` jeśli jest inaczej. `-p:BuildProjectReferences=false`można określić w wierszu polecenia, aby uniknąć sprawdzania, czy projekty, do których istnieje odwołanie, są aktualne. |
| Plik CleanFile | Nazwa pliku, który będzie używany jako "czysta pamięć podręczna". Czysta pamięć podręczna to lista wygenerowanych plików do usunięcia podczas operacji czyszczenia. Plik jest umieszczany w ścieżce wyjściowej pośredniej przez proces kompilacji.<br /><br /> Ta właściwość określa tylko nazwy plików, które nie mają informacji o ścieżce. |
| Codepage | Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ta właściwość jest `/codepage` odpowiednikiem przełącznika kompilatora. |
| Plik Kompilacji | Opcjonalny plik odpowiedzi, który może być przekazywany do zadań kompilatora. |
| Konfigurowanie | Budowana konfiguracja ,albo "Debug" lub "Release". |
| CscToolPath (CscToolPath) | Ścieżka *csc.exe*, kompilator C#. |
| CustomBeforeMicrosoftCommonTargets | Nazwa pliku projektu lub pliku docelowego, który ma być importowany automatycznie przed importem wspólnych obiektów docelowych. |
| DebugSymbols | Wartość logiczna, która wskazuje, czy symbole są generowane przez kompilację.<br /><br /> Ustawienie **-p:DebugSymbols=false** w wierszu polecenia wyłącza generowanie plików symboli bazy danych programu (*pdb).* |
| Typ debugowania | Określa poziom informacji debugowania, które mają być generowane. Prawidłowe wartości to "full", "pdbonly", "portable", "embedded" i "none". |
| Zdefiniowanieconstants | Definiuje stałe kompilatora warunkowego. Pary symboli/wartości są oddzielone średnikami i są określane przy użyciu następującej składni:<br /><br /> *symbol1 = wartość1 ; symbol2 = wartość2*<br /><br /> Właściwość jest odpowiednikiem przełącznika kompilatora. `/define` |
| DefineDebug | Wartość logiczna, która wskazuje, czy ma być zdefiniowana stała DEBUG. |
| Definiujtracj | Wartość logiczna wskazująca, czy ma być zdefiniowana stała TRACE. |
| Delaysign | Wartość logiczna, która wskazuje, czy chcesz opóźnić znak złożenia, a nie go podpisać w pełnym podpisie. |
| Deterministyczne | Wartość logiczna, która wskazuje, czy kompilator powinien produkować identyczne zestawy dla identycznych danych wejściowych. Ten parametr odpowiada `/deterministic` przełącznikowi kompilatorów *vbc.exe* i *csc.exe.* |
| WyłączoneWarnings | Pomija określone ostrzeżenia. Należy określić tylko numeryczną część identyfikatora ostrzegawczego. Wiele ostrzeżeń są oddzielone średnikami. Ten parametr odpowiada `/nowarn` przełącznikowi kompilatora *vbc.exe.* |
| Sprawdzanie funkcji DisableFastUpToDateCheck | Wartość logiczna, która ma zastosowanie tylko do programu Visual Studio. Menedżer kompilacji programu Visual Studio używa procesu o nazwie FastUpToDateCheck, aby ustalić, czy projekt musi zostać przebudowany, aby był aktualny. Ten proces jest szybszy niż przy użyciu MSBuild, aby to ustalić. Ustawienie DisableFastUpToDateCheck właściwość pozwala pominąć `true` Menedżera kompilacji programu Visual Studio i wymusić go do korzystania z MSBuild, aby ustalić, czy projekt jest aktualny. |
| Plik dokumentacji | Nazwa pliku, który jest generowany jako plik dokumentacji XML. Ta nazwa zawiera tylko nazwę pliku i nie ma informacji o ścieżce. |
| Raport o błędach | Określa, jak zadanie kompilatora powinno zgłaszać błędy kompilatora wewnętrznego. Prawidłowe wartości to "monit", "wyślij" lub "brak". Ta właściwość jest `/errorreport` odpowiednikiem przełącznika kompilatora. |
| WykluczDeploymentUrl | [Zadanie GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md) dodaje tag deploymentProvider do manifestu wdrożenia, jeśli plik projektu zawiera którykolwiek z następujących elementów:<br /><br /> - AktualizacjaUrl<br />- InstallUrl<br />- PublishUrl<br /><br /> Za pomocą ExcludeDeploymentUrl, jednak można zapobiec deploymentProvider tag dodawany do manifestu wdrożenia, nawet jeśli którykolwiek z powyższych adresów URL są określone. Aby to zrobić, dodaj do pliku projektu następującą właściwość:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Uwaga:**  ExcludeDeploymentUrl nie jest narażony w programie Visual Studio IDE i można go ustawić tylko przez ręczną edycję pliku projektu. Ustawienie tej właściwości nie wpływa na publikowanie w programie Visual Studio; oznacza to, że tag deploymentProvider nadal będzie dodawany do adresu URL określonego przez PublishUrl. |
| Wyrównanie plików | Określa w bajtach, gdzie wyrównać sekcje pliku wyjściowego. Prawidłowe wartości to 512, 1024, 2048, 4096, 8192. Ta właściwość jest `/filealignment` odpowiednikiem przełącznika kompilatora. |
| RamówkaPathOverride | Określa lokalizację *pliku mscorlib.dll* i *pliku microsoft.visualbasic.dll*. Ten parametr jest `/sdkpath` odpowiednikiem przełącznika kompilatora *vbc.exe.* |
| Generowaniedokumentacji | (C#, Visual Basic) Parametr logiczny, który wskazuje, czy dokumentacja jest generowana przez kompilację. Jeśli `true`kompilacja generuje informacje o dokumentacji i umieszcza je w pliku *xml* wraz z nazwą pliku wykonywalnego lub biblioteki utworzonego przez zadanie kompilacji. |
| GenerateFullPaths (GenerowaniefullPaths) | (C#) Generuj pełne ścieżki dla nazwy plików w danych wyjściowych przy użyciu opcji kompilatora [-fullpaths.](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) |
| GenerowanieSerializationAssemblies | Wskazuje, czy zestawy serializacji XML powinny być generowane przez *SGen.exe*, które można ustawić na włączone, automatyczne lub wyłączone. Ta właściwość jest używana dla zestawów, które dotyczą tylko .NET Framework. Aby wygenerować zestawy serializacji XML dla zestawów .NET Standard lub .NET Core, należy odwołać się do pakietu *Microsoft.XmlSerializer.Generator* NuGet. |
| IntermediateOutputPath (Ścieżka pośredniej nieprzejście) | Pełna pośrednia ścieżka wyjściowa `BaseIntermediateOutputPath`wyprowadzce z , jeśli nie określono ścieżki. Na przykład *\obj\debug\\*. |
| Nazwa klucza | Nazwa kontenera klucza silnej nazwy. |
| KeyOriginatorFile | Nazwa pliku klucza o silnej nazwie. |
| ModułNagodna nazwa | Nazwa zestawu, do który ma zostać włączony skompilowany moduł. Właściwość jest odpowiednikiem przełącznika kompilatora. `/moduleassemblyname` |
| ŚCIEŻKA MSBuildProjectExtensionsPath | Określa ścieżkę, w której znajdują się rozszerzenia projektu. Domyślnie ma to taką `BaseIntermediateOutputPath`samą wartość jak . |
| NoLogo ( NoLogo ) | Wartość logiczna wskazująca, czy logo kompilatora ma być wyłączone. Ta właściwość jest `/nologo` odpowiednikiem przełącznika kompilatora. |
| NoStdLib ( NoStdLib ) | Wartość logiczna wskazująca, czy unikać odwoływania się do standardowej biblioteki (*mscorlib.dll*). Wartością domyślną jest `false`. |
| NoVBRuntimeReferencja | Wartość logiczna, która wskazuje, czy środowisko wykonawcze języka Visual Basic (*Microsoft.VisualBasic.dll*) powinny być uwzględnione jako odwołanie w projekcie. |
| NoWin32Manifest | Wartość logiczna wskazująca, czy informacje manifestu kontrola konta użytkownika (UAC) zostaną osadzone w pliku wykonywalnym aplikacji. Dotyczy tylko projektów programu Visual Studio kierowanych na system Windows Vista. W projektach wdrożonych przy użyciu ClickOnce i Rejestracja-Free COM, ten element jest ignorowany. `False`(wartość domyślna) określa, że informacje manifestu kontrola konta użytkownika (UAC) mają być osadzone w pliku wykonywalnym aplikacji. `True`określa, że informacje manifestu kontrola konta użytkownika nie są osadzane.<br /><br /> Ta właściwość dotyczy tylko projektów programu Visual Studio kierowanych na system Windows Vista. W projektach wdrożonych przy użyciu ClickOnce i Rejestracja-Free COM, ta właściwość jest ignorowana.<br /><br /> NoWin32Manifest należy dodać tylko wtedy, gdy program Visual Studio nie ma osadzić żadnych informacji manifestu w pliku wykonywalnym aplikacji; proces ten nazywany jest *wirtualizacją*. Aby użyć wirtualizacji, ustaw `<ApplicationManifest>` w połączeniu z `<NoWin32Manifest>` następującymi:<br /><br /> - W przypadku projektów `<ApplicationManifest>` języka Visual Basic usuń węzeł. (W projektach `<NoWin32Manifest>` języka Visual Basic `<ApplicationManifest>` jest ignorowany, gdy istnieje węzeł).<br />- W przypadku projektów `<ApplicationManifest>` `False` C#, ustaw do i `<NoWin32Manifest>` do `True`. (W projektach `<ApplicationManifest>` języka C# zastępuje `<NoWin32Manifest>`.)<br /> Ta właściwość jest `/nowin32manifest` odpowiednikiem przełącznika kompilatora *vbc.exe*. |
| Optymalizacja | Wartość logiczna, która `true`po ustawieniu na , umożliwia optymalizacje kompilatora. Ta właściwość jest `/optimize` odpowiednikiem przełącznika kompilatora. |
| OpcjaSkłasna | Określa sposób porównywania ciągów. Prawidłowe wartości to "binarny" lub "tekst". Ta właściwość jest `/optioncompare` odpowiednikiem przełącznika kompilatora *vbc.exe*. |
| OpcjaWydatk | Wartość logiczna, która `true`po ustawieniu na , wymaga jawnej deklaracji zmiennych w kodzie źródłowym. Ta właściwość jest `/optionexplicit` odpowiednikiem przełącznika kompilatora. |
| OpcjaInferuj | Wartość logiczna, która `true`po ustawieniu na , umożliwia wnioskowanie o typie zmiennych. Ta właściwość jest `/optioninfer` odpowiednikiem przełącznika kompilatora. |
| OptionStrict | Wartość logiczna, która `true`po ustawieniu na , powoduje, że zadanie kompilacji wymusza semantykę typu ścisłego, aby ograniczyć konwersje typów niejawnych. Ta właściwość jest `/optionstrict` odpowiednikiem przełącznika kompilatora *vbc.exe.* |
| Outdir | Wskazuje ostateczną lokalizację danych wyjściowych dla projektu lub rozwiązania. Podczas tworzenia rozwiązania OutDir może służyć do zbierania wielu wyjść projektu w jednej lokalizacji. Ponadto OutDir znajduje się w AssemblySearchPaths używane do rozpoznawania odwołań. Na przykład *bin\Debug*. |
| Outputpath | Określa ścieżkę do katalogu wyjściowego względem katalogu projektu, na przykład *bin\Debug*. |
| Outputtype | Określa format pliku wyjściowego. Ten parametr może mieć jedną z następujących wartości:<br /><br /> - Biblioteka. Tworzy bibliotekę kodu. (Wartość domyślna).<br />- Exe. Tworzy aplikację konsoli.<br />- Moduł. Tworzy moduł.<br />- Winexe. Tworzy program oparty na systemie Windows.<br /><br /> Ta właściwość jest `/target` odpowiednikiem przełącznika kompilatora *vbc.exe.* |
| Zastępowanie Pliku tylko do odczytu | Wartość logiczna wskazująca, czy chcesz włączyć kompilację, aby zastąpić pliki tylko do odczytu, czy wyzwolić błąd. |
| Mapa ścieżki | Określa sposób mapowania ścieżek fizycznych do nazw ścieżek źródłowych danych wyjściowych przez kompilator. Ta właściwość jest `/pathmap` odpowiednikiem przełącznika kompilatora *csc.exe.* |
| Plik Pdb | Nazwa pliku pdb emitującego *plik.pdb.* Ta właściwość jest `/pdb` odpowiednikiem przełącznika kompilatora *csc.exe.* |
| Platforma | System operacyjny, dla którego budujesz. Prawidłowe wartości to "Dowolny procesor", "x86" i "x64". |
| ProcessorArchitecture | Architektura procesora, która jest używana podczas rozwiązywania odwołań do zestawu. Prawidłowe wartości to "msil", "x86", "amd64" lub "ia64". |
| ProdukcjaOnowaReferasasu | Wartość logiczna, która nakazuje kompilatorowi emitować tylko zestaw odniesienia, a nie skompilowany kod. Nie można używać `ProduceReferenceAssembly`w połączeniu z .  Ta właściwość odpowiada `/refonly` przełącznikowi kompilatorów *vbc.exe* i *csc.exe.* |
| ProdukcjaReferencjasześci | Wartość logiczna, która `true` po ustawieniu umożliwia produkcję [zestawów referencyjnych](/dotnet/standard/assembly/reference-assemblies) dla bieżącego złożenia. `Deterministic``true` podczas korzystania z tej funkcji. Ta właściwość odpowiada `/refout` przełącznikowi kompilatorów *vbc.exe* i *csc.exe.* |
| Usuń sprawdzanie | Wartość logiczna wskazująca, czy wyłączyć sprawdzanie błędów przepełnienia liczby całkowitej. Wartością domyślną jest `false`. Ta właściwość jest `/removeintchecks` odpowiednikiem przełącznika kompilatora *vbc.exe.* |
| Rootnamespace | Główny obszar nazw używany podczas nadawanie nazwy osadzonemu zasobowi. Ta przestrzeń nazw jest częścią nazwy manifestu osadzonego zasobu. |
| Satellite_AlgorithmId | Identyfikator algorytmu mieszania *AL.exe* do użycia podczas tworzenia zestawów satelickich. |
| Satellite_BaseAddress | Adres podstawowy do użycia, gdy zestawy satelickiej `CreateSatelliteAssemblies` specyficzne dla kultury są budowane przy użyciu obiektu docelowego. |
| Satellite_CompanyName | Nazwa firmy, aby przejść do *AL.exe* podczas generowania montażu satelitarnego. |
| Satellite_Configuration | Nazwa konfiguracji do przekazania do *AL.exe* podczas generowania zestawu satelitarnego. |
| Satellite_Description | Tekst opisu do przekazania do *AL.exe* podczas generowania zestawu satelitarnego. |
| Satellite_EvidenceFile | Osadza określony plik w zestawie satelicie, który ma nazwę zasobu "Security.Evidence". |
| Satellite_FileVersion | Określa ciąg dla pola Wersja pliku w zestawie satelicie. |
| Satellite_Flags | Określa wartość pola Flagi w złożeniu satelicie. |
| Satellite_GenerateFullPaths | Powoduje, że zadanie kompilacji używać ścieżek bezwzględnych dla wszystkich plików zgłoszonych w komunikacie o błędzie. |
| Satellite_LinkResource | Łączy określone pliki zasobów z zestawem satelicie. |
| Satellite_MainEntryPoint | Określa w pełni kwalifikowaną nazwę (czyli class.method) metody, która ma być używana jako punkt wejścia, gdy moduł jest konwertowany na plik wykonywalny podczas generowania zestawu satelickiego. |
| Satellite_ProductName | Określa ciąg dla pola Produkt w zestawie satelicie. |
| Satellite_ProductVersion | Określa ciąg dla pola ProductVersion w zestawie satelicie. |
| Satellite_TargetType | Określa format pliku wyjściowego zestawu satelickiego jako "biblioteka", "exe" lub "win". Wartością domyślną jest "biblioteka". |
| Satellite_Title | Określa ciąg dla pola Tytuł w złożeniu satelicie. |
| Satellite_Trademark | Określa ciąg dla pola Znak towarowy w zestawie satelicie. |
| Satellite_Version | Określa informacje o wersji dla zestawu satelickiego. |
| Satellite_Win32Icon | Wstawia plik *ikony .ico* do zestawu satelickiego. |
| Satellite_Win32Resource | Wstawia zasób Win32 (plik *.res)* do zestawu satelickiego. |
| SGenToolPath (Szlak SGenToolPath) | Opcjonalna ścieżka narzędzia, która wskazuje, gdzie można uzyskać *SGen.exe,* gdy bieżąca wersja *SGen.exe* jest zastępowana. Ta właściwość jest używana tylko dla programu .NET Framework.|
| SGenUseProxyTypy | Wartość logiczna wskazująca, czy typy serwerów proxy powinny być generowane przez *plik SGen.exe*. Dotyczy to tylko wtedy, gdy *generateserializationAssemblies* jest ustawiona na i tylko dla programu .NET Framework.<br /><br /> Obiekt docelowy SGen używa tej właściwości, aby ustawić UseProxyTypes flagi. Ta właściwość domyślnie true i nie ma żadnego interfejsu użytkownika, aby to zmienić. Aby wygenerować zestaw serializacji dla typów innych niż webservice, dodaj tę właściwość do pliku projektu i ustaw ją na false przed zaimportowaniem *microsoft.common.targets* lub *C#/VB.targets*. |
| Projekt Startu | Określa klasę lub moduł zawierający metodę Main lub Procedurę Podnajm. Ta właściwość jest `/main` odpowiednikiem przełącznika kompilatora. |
| SubsystemVersion | Określa minimalną wersję podsystemu, z której może korzystać wygenerowany plik wykonywalny. Ta właściwość jest `/subsystemversion` odpowiednikiem przełącznika kompilatora. Aby uzyskać informacje o wartości domyślnej tej właściwości, zobacz [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) lub [/subsystemversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework (Zadanie kompaktuframework) | Wersja programu .NET Compact Framework, która jest wymagana do uruchomienia aplikacji, którą budujesz. Określenie tego umożliwia odwoływanie się do niektórych zestawów struktury, które mogą nie być w stanie odwołać się w inny sposób. |
| Targetframeworkversion | Wersja programu .NET Framework, która jest wymagana do uruchomienia aplikacji, którą budujesz. Określenie tego umożliwia odwoływanie się do niektórych zestawów struktury, które mogą nie być w stanie odwołać się w inny sposób. |
| TreatWarningsAsErrors | Parametr logiczny, który `true`jeśli powoduje, że wszystkie ostrzeżenia są traktowane jako błędy. Ten parametr jest `/nowarn` odpowiednikiem przełącznika kompilatora. |
| UseHostCompilerIfDostępne | Parametr logiczny, który `true`jeśli powoduje, że zadanie kompilacji powoduje użycie obiektu kompilatora w toku, jeśli jest dostępny. Ten parametr jest używany tylko przez program Visual Studio. |
| Utf8Output (Polski) | Parametr logiczny, który, jeśli `true`, rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr jest `/utf8Output` odpowiednikiem przełącznika kompilatora. |
| Ścieżka VbcToolPath | Opcjonalna ścieżka wskazująca inną lokalizację dla *programu vbc.exe,* gdy bieżąca wersja *programu vbc.exe* zostanie zastąpiona. |
| VbcWerbosity | Określa szczegółowość danych wyjściowych kompilatora języka Visual Basic. Prawidłowe wartości to "Cichy", "Normalny" (wartość domyślna) lub "Pełny". |
| Visualstudioversion | Określa wersję programu Visual Studio, w ramach której ten projekt należy uznać za uruchomiony. Jeśli ta właściwość nie jest określona, MSBuild ustawia ją na rozsądną wartość domyślną.<br /><br /> Ta właściwość jest używana w kilku typach projektu, aby określić zestaw obiektów docelowych, które są używane do kompilacji. Jeśli `ToolsVersion` jest ustawiona na 4.0 `VisualStudioVersion` lub wyższa dla projektu, służy do określenia, który zestaw narzędzi podrzędnych do użycia. Aby uzyskać więcej informacji, zobacz [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| OstrzeżeniaAsErrors | Określa listę ostrzeżeń, które należy traktować jako błędy. Ten parametr jest `/warnaserror` odpowiednikiem przełącznika kompilatora. |
| OstrzeżeniaNotAsErrors | Określa listę ostrzeżeń, które nie są traktowane jako błędy. Ten parametr jest `/warnaserror` odpowiednikiem przełącznika kompilatora. |
| Win32manifest | Nazwa pliku manifestu, który powinien być osadzony w zestawie końcowym. Ten parametr jest `/win32Manifest` odpowiednikiem przełącznika kompilatora. |
| Win32Źródło | Nazwa pliku zasobu Win32, który ma zostać osadzony w zestawie końcowym. Ten parametr jest `/win32resource` odpowiednikiem przełącznika kompilatora. |

## <a name="see-also"></a>Zobacz też

- [Typowe elementy projektu MSBuild](../msbuild/common-msbuild-project-items.md)
