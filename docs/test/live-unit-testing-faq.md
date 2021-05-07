---
title: Live Unit Testing — często zadawane pytania
description: Przejrzyj te Live Unit Testing często zadawane pytania, w tym obsługiwane struktury, konfigurację i dostosowywanie.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800506"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing często zadawane pytania

## <a name="supported-frameworks"></a>Obsługiwane struktury

**Jakie struktury testowe Live Unit Testing i jakie są minimalne obsługiwane wersje?**

Live Unit Testing działa z trzema popularnymi platformami testowania jednostkowego wymienionymi w poniższej tabeli. W tabeli wymieniono również minimalną obsługiwaną wersję kart i platform. Wszystkie struktury testowania jednostkowego są dostępne w NuGet.org.

|Test Framework  |Visual Studio wersji karty sieciowej  |Minimalna wersja struktury  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio w wersji 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter w wersji 3.7.0 |NUnit w wersji 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Jeśli masz starsze projekty testowe oparte na testowania MSTest, do których się odwołują i nie chcesz przechodzić do nowszej wersji pakietów NuGet MSTest, przetestuj program do wersji `Microsoft.VisualStudio.QualityTools.UnitTestFramework` Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołują się projekty w rozwiązaniu, aby Live Unit Testing działać. Pakiety można przywrócić, wykonując jawną kompilację rozwiązania (wybierz pozycję Build Rebuild Solution (Sbuduj ponownie rozwiązanie) z menu najwyższego poziomu Visual Studio lub klikając rozwiązanie prawym przyciskiem myszy i wybierając polecenie Restore NuGet Packages (Przywróć pakiety  >  **NuGet)** przed włączeniem funkcji Living Unit **Testing.**

## <a name="net-core-support"></a>Obsługa .NET Core

**Czy Live Unit Testing z programem .NET Core?**

Tak. Live Unit Testing współpracuje z programem .NET Core i .NET Framework.

## <a name="configuration"></a>Konfigurowanie

**Dlaczego po włączeniu Live Unit Testing nie działa?**

Okno Dane wyjściowe (po Live Unit Testing listy rozwijanej) powinno poinformować, dlaczego Live Unit Testing nie działa. Live Unit Testing może nie działać z jednej z następujących przyczyn:

- Jeśli pakiety NuGet przywołyne przez projekty w rozwiązaniu nie zostały przywrócone, Live Unit Testing nie będzie działać. Wykonanie jawnej kompilacji rozwiązania lub przywrócenie pakietów NuGet w rozwiązaniu przed włączeniem Live Unit Testing rozwiązanie tego problemu.

- Jeśli używasz testów opartych na msTest w projektach, upewnij się, że usuwasz odwołanie do i dodajesz odwołania do najnowszych pakietów NuGet MSTest (wymagana jest minimalna wersja `Microsoft.VisualStudio.QualityTools.UnitTestFramework` `MSTest.TestAdapter` 1.1.11) i (wymagana jest minimalna wersja `MSTest.TestFramework` 1.1.11). Aby uzyskać więcej informacji, zobacz sekcję "Supported test frameworks" (Obsługiwane struktury testowe) artykułu [Use Live Unit Testing in Visual Studio](live-unit-testing.md#supported-test-frameworks) article (Używanie Live Unit Testing w Visual Studio testowania).

- Co najmniej jeden projekt w rozwiązaniu powinien mieć odwołanie NuGet lub bezpośrednie odwołanie do struktury testowej xUnit, NUnit lub MSTest. Ten projekt powinien również odwoływać się do odpowiadającego Visual Studio testowych NuGet. Do Visual Studio testowego można również odwoływać się za pośrednictwem *pliku .runsettings.* Plik *.runsettings* musi mieć wpis podobny do poniższego przykładu:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nieprawidłowe pokrycie po uaktualnieniu

**Dlaczego Live Unit Testing są wyświetlane niepoprawne pokrycie po uaktualnieniu adaptera testowego, do którego odwołuje się Visual Studio Projects do obsługiwanej wersji?**

- Jeśli wiele projektów w rozwiązaniu odwołuje się do pakietu adaptera testowego NuGet, każdy z nich musi zostać uaktualniony do obsługiwanej wersji.

- Upewnij się, że *plik props* programu MSBuild zaimportowany z pakietu adaptera testowego również został poprawnie zaktualizowany. Sprawdź wersję/ścieżkę pakietu NuGet importu, która zazwyczaj znajduje się w górnej części pliku projektu, jak podano poniżej:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Dostosowywanie kompilacji

**Czy mogę dostosować moje Live Unit Testing kompilacje?**

Jeśli rozwiązanie wymaga niestandardowych kroków kompilacji dla instrumentacji (Live Unit Testing), które nie są wymagane dla "zwykłej" kompilacji bez instrumentacji, możesz dodać kod do plików projektu lub *targets,* który sprawdza właściwość i wykonuje niestandardowe kroki `BuildingForLiveUnitTesting` przed/po kompilacji. Możesz również usunąć niektóre kroki kompilacji (takie jak publikowanie lub generowanie pakietów) lub dodać kroki kompilacji (takie jak kopiowanie wymagań wstępnych) do kompilacji Live Unit Testing na podstawie tej właściwości projektu. Dostosowanie kompilacji na podstawie tej właściwości nie zmienia zwykłej kompilacji w żaden sposób i ma wpływ tylko Live Unit Testing kompilacji.

Na przykład może być element docelowy, który tworzy pakiety NuGet podczas zwykłej kompilacji. Prawdopodobnie nie chcesz, aby pakiety NuGet były generowane po każdej edytowaniu. Możesz więc wyłączyć ten element docelowy w Live Unit Testing, wykonując czynności podobne do następujących:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Komunikaty o błędach z \<OutputPath> , \<OutDir> lub \<IntermediateOutputPath>

**Dlaczego otrzymuję następujący błąd, gdy Live Unit Testing próbuje skompilować rozwiązanie: "... wydaje się być ustawiony bezwarunkowo `<OutputPath>` lub `<OutDir>` . Live Unit Testing nie będą wykonywać testów z zestawu wyjściowego"?**

Ten błąd można uzyskać, jeśli proces kompilacji rozwiązania ma niestandardową logikę, która określa, gdzie mają być generowane pliki binarne. Domyślna lokalizacja plików binarnych zależy od `<OutputPath>` , lub , a także lub `<OutDir>` `<IntermediateOutputPath>` `<BaseOutputPath>` `<BaseIntermediateOutputPath>` .

Live Unit Testing te zmienne są zastępowane w celu zapewnienia, że artefakty kompilacji są porzucane do folderu artefaktów Live Unit Testing i nie powiedzie się, jeśli proces kompilacji również zastąpi te zmienne.

Istnieją dwa główne podejścia do pomyślnego Live Unit Testing kompilacji. Aby ułatwić konfiguracje kompilacji, ścieżki wyjściowe można opierać na `<BaseIntermediateOutputPath>` . W przypadku bardziej złożonych konfiguracji ścieżki wyjściowe można opierać na `<LiveUnitTestingBuildRootPath>` .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Warunkowe `<OutputPath>` / `<IntermediateOutputPath>` zastępowanie na podstawie `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` .

> [!NOTE]
> Aby użyć tego podejścia, każdy projekt musi być w stanie tworzyć niezależnie od siebie. Nie należy mieć jednego artefaktu odwołania do projektu z innego projektu podczas kompilacji. Nie ma jednego projektu dynamicznie ładuj zestawy z innego projektu podczas wykonywania (na przykład wywołania `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")` ).

Podczas kompilacji Live Unit Testing automatycznie przesłonić zmienne w celu ukierunkowania `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` Live Unit Testing artefaktów.

Jeśli na przykład kompilacja zastępuje metodę , <OutputPath> jak pokazano poniżej:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

Następnie można zastąpić go następującym kodem XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Gwarantuje to, że `<OutputPath>` znajduje się w `<BaseOutputPath>` folderze .

Nie przesłoń bezpośrednio w procesie kompilacji; zastąp zamiast tego, aby usunąć `<OutDir>` `<OutputPath>` artefakty kompilacji w określonej lokalizacji.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Zastępowanie właściwości na podstawie `<LiveUnitTestingBuildRootPath>` właściwości .

> [!NOTE]
> W tym podejściu należy zachować ostrożność w przypadku plików dodawanych w folderze artifacts, które nie są generowane podczas kompilacji. W poniższym przykładzie pokazano, co należy zrobić, umieszczając folder packages w artefaktach. Ponieważ zawartość tego folderu nie jest generowana podczas kompilacji, właściwość MSBuild **nie powinna być zmieniana.**

Podczas Live Unit Testing właściwość jest ustawiana na lokalizację folderu `<LiveUnitTestingBuildRootPath>` Live Unit Testing artifacts.

Załóżmy na przykład, że projekt ma strukturę pokazaną tutaj.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Podczas Live Unit Testing kompilacji właściwość `<LiveUnitTestingBuildRootPath>` jest ustawiana na pełną ścieżkę `.vs\...\lut\0\b` . Jeśli projekt definiuje właściwość, która mapuje na katalog rozwiązania, można zaktualizować projekt `<ArtifactsRoot>` MSBuild w następujący sposób:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Lokalizacja artefaktu kompilacji

**Chcę, aby artefakty kompilacji Live Unit Testing trafiały do określonej lokalizacji, a nie do lokalizacji domyślnej w *folderze .vs.* Jak mogę to zmienić?**

Ustaw zmienną środowiskową na poziomie użytkownika na ścieżkę, w `LiveUnitTesting_BuildRoot` Live Unit Testing artefakty kompilacji mają być porzucane. 

## <a name="test-explorer-versus-live-unit-testing"></a>Eksplorator testów a Live Unit Testing

**Czym różni się uruchamianie testów z okna Eksploratora testów od uruchamiania testów w Live Unit Testing?**

Istnieje kilka różnic:

- Uruchamianie lub debugowanie testów w **oknie Eksploratora testów** uruchamia zwykłe pliki binarne, podczas gdy Live Unit Testing instrumentowane pliki binarne. Jeśli chcesz debugować instrumentowane pliki binarne, dodanie wywołania metody [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) w metodzie testowej powoduje uruchomienie debugera za każdym razem, gdy ta metoda jest wykonywana (w tym gdy jest wykonywana przez program Live Unit Testing), a następnie można dołączyć i debugować instrumentowany plik binarny. Mamy jednak nadzieję, że instrumentacja będzie niewidoczna dla większości scenariuszy użytkownika i że nie trzeba debugować instrumentowanych plików binarnych.

- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów,  ale testy uruchamiane w oknie Eksplorator testów tworzą nową domenę aplikacji.

- Live Unit Testing uruchamia testy w każdym zestawie testowym sekwencyjnie. W **Eksploratorze** testów można uruchomić wiele testów równolegle.

- **Eksplorator testów** domyślnie uruchamia testy w jednowątkowym schłodniku (STA), natomiast Live Unit Testing uruchamia testy w wielowątkowej wersji typu (MTA). Aby uruchomić testy MSTest w stajni Live Unit Testing, udekoruj metodę testową lub klasę zawierającą za pomocą atrybutu lub , który można znaleźć w `<STATestMethod>` `<STATestClass>` `MSTest.STAExtensions 1.0.3-beta` pakiecie NuGet. W przypadku jednostki NUnit udekoruj metodę testową za pomocą atrybutu , a dla `<RequiresThread(ApartmentState.STA)>` jednostki xUnit `<STAFact>` atrybutem .

## <a name="exclude-tests"></a>Wykluczanie testów

**Jak mogę wykluczyć testy z uczestnictwa w Live Unit Testing?**

Zobacz sekcję "Dołączanie i wykluczanie projektów testowych i metod testowych" artykułu Use Live Unit Testing in Visual Studio (Dołączanie i wykluczanie projektów testowych oraz metod testowych) artykułu Use Visual Studio in Visual Studio (Używanie aplikacji testowych w programie [Visual Studio),](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) aby uzyskać informacje o ustawieniach specyficznych dla użytkownika. Do uwzględnienia lub wykluczenia testów przydaje się, gdy chcesz uruchomić określony zestaw testów dla określonej sesji edycji lub utrwalić własne preferencje osobiste.

W przypadku ustawień specyficznych dla rozwiązania atrybut można zastosować programowo, aby wykluczyć metody, właściwości, klasy lub struktury z instrumentowania przez <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> Live Unit Testing. Ponadto możesz również ustawić właściwość na w pliku projektu, aby wykluczyć cały `<ExcludeFromCodeCoverage>` `true` projekt z instrumentowanych. Live Unit Testing nadal będą uruchamiać testy, które nie zostały instrumentowane, ale ich pokrycie nie będzie wizualizowane.

Możesz również sprawdzić, czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` aplikacja jest ładowana w bieżącej domenie aplikacji, i wyłączyć testy w zależności od przyczyny. Za pomocą xUnit można na przykład wykonać czynności podobne do następujących:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Nagłówki Win32 PE

**Dlaczego nagłówki Win32 PE różnią się w zestawach instrumentowanych zbudowanych przez testy jednostkowe na żywo?**

Ten problem został rozwiązany i nie istnieje w programie Visual Studio 2017 w wersji 15.3 i nowszych.

W przypadku starszych wersji Visual Studio 2017 istnieje znana usterka, która może spowodować, że kompilacje Live Unit Testing nie będą osadzać następujących danych nagłówka Win32 PE:

- Wersja pliku (określona przez @System.Reflection.AssemblyFileVersionAttribute w kodzie).

- Ikona Win32 (określona `/win32icon:` przez w wierszu polecenia).

- Manifest Win32 (określony `/win32manifest:` przez w wierszu polecenia).

Testy, które opierają się na tych wartościach, mogą się nie powieść podczas wykonywania testów jednostkowych na żywo.

::: moniker-end

## <a name="continuous-builds"></a>Kompilacje ciągłe

**Dlaczego testy jednostkowe na żywo cały czas budować moje rozwiązanie, nawet jeśli nie wyeksumuję żadnych zmian?**

Rozwiązanie można skompilować, nawet jeśli nie są wprowadzane zmiany, jeśli proces kompilacji generuje kod źródłowy, który jest częścią samego rozwiązania, a pliki docelowe kompilacji nie mają określonych odpowiednich danych wejściowych i wyjściowych. Obiekty docelowe powinny mieć dostęp do listy danych wejściowych i wyjściowych, aby program MSBuild może przeprowadzać odpowiednie aktualne kontrole i określać, czy nowa kompilacja jest wymagana.

Live Unit Testing uruchamia kompilację za każdym razem, gdy wykryje, że pliki źródłowe zostały zmienione. Ponieważ kompilacja rozwiązania generuje pliki źródłowe, Live Unit Testing w nieskończoną pętlę kompilacji. Jeśli jednak dane wejściowe i wyjściowe obiektu docelowego są sprawdzane podczas uruchamiania drugiej kompilacji przez program Live Unit Testing (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), przerywa on pętlę kompilacji, ponieważ sprawdzanie danych wejściowych i wyjściowych wskazuje, że wszystko jest aktualne.

## <a name="editor-icons"></a>Ikony edytora

**Dlaczego nie widzę żadnych ikon w edytorze, Live Unit Testing wygląda na to, że testy są uruchomione na podstawie komunikatów w oknie Dane wyjściowe?**

Ikony mogą nie być widoczne w edytorze, jeśli zestawy, Live Unit Testing na których działa, nie są instrumentowane z jakiegokolwiek powodu. Na przykład Live Unit Testing jest zgodna z projektami, które ustawiają wartość `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` . W takim przypadku proces kompilacji musi zostać zaktualizowany, aby usunąć to ustawienie lub zmienić je na , aby Live Unit Testing `true` działało. 

## <a name="capture-logs"></a>Przechwytywanie dzienników

**Jak mogę zbierać bardziej szczegółowe dzienniki w celu zgłaszania błędów?**

Aby zebrać bardziej szczegółowe dzienniki, możesz wykonać kilka czynności:

- Przejdź do **opcji** narzędzia Live Unit Testing i zmień opcję  >    >   rejestrowania na **Pełne.** Pełne rejestrowanie powoduje, że bardziej szczegółowe dzienniki są wyświetlane w **oknie Dane** wyjściowe.

- Ustaw zmienną środowiskową użytkownika na nazwę pliku, którego chcesz użyć `LiveUnitTesting_BuildLog` do przechwycenia dziennika programu MSBuild. Szczegółowe komunikaty dziennika programu MSBuild Live Unit Testing kompilacji można następnie pobrać z tego pliku.

- Ustaw `LiveUnitTesting_TestPlatformLog` zmienną środowiskową użytkownika na `1` wartość , aby przechwycić dziennik platformy testów. Szczegółowe komunikaty dziennika platformy testów Live Unit Testing można pobrać z usługi `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` .

- Utwórz zmienną środowiskową na poziomie użytkownika o nazwie i ustaw ją na `VS_UTE_DIAGNOSTICS` wartość 1 (lub dowolną wartość), a następnie uruchom ponownie Visual Studio. Na karcie Dane wyjściowe —  testy na karcie Dane Visual Studio powinno być teraz Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Live Unit Testing](live-unit-testing.md)
