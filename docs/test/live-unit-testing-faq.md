---
title: Live Unit Testing — często zadawane pytania
description: Zapoznaj się z tymi Live Unit Testing często zadawanymi pytaniami, w tym obsługiwanymi strukturami, konfiguracją i dostosowywaniem.
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
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329292"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing często zadawane pytania

## <a name="supported-frameworks"></a>Obsługiwane struktury

**Jakie platformy testowe Live Unit Testing obsługiwać i jakie są minimalne obsługiwane wersje?**

Live Unit Testing współpracuje z trzema popularnymi platformami testowania jednostkowego wymienionymi w poniższej tabeli. Minimalna obsługiwana wersja ich kart i struktur jest również wymieniona w tabeli. Platformy testów jednostkowych są dostępne z NuGet.org.

|Platforma testowa  |Minimalna wersja programu Visual Studio adapter  |Minimalna wersja platformy  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio w wersji 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter wersja 3.7.0 |NUnit wersja 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4 — wersja zapoznawcza |MSTest. TestFramework 1.0.5 — wersja zapoznawcza |

Jeśli masz starsze projekty testowe bazujące na MSTestach, których odwołuje się `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przejść do nowszych pakietów NuGet MSTest, przeprowadź uaktualnienie do programu Visual studio 2019 lub Visual studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołują się projekty w rozwiązaniu, aby Live Unit Testing działały. Pakiety można przywrócić, wykonując jawną kompilację rozwiązania (wybierz opcję **Kompiluj**  >  **ponownie rozwiązanie** z menu programu Visual Studio najwyższego poziomu) lub klikając rozwiązanie prawym przyciskiem myszy i wybierając pozycję **Przywróć pakiety NuGet** przed włączeniem testów jednostkowych.

## <a name="net-core-support"></a>Obsługa platformy .NET Core

**Czy Live Unit Testing współpracuje z platformą .NET Core?**

Tak. Live Unit Testing współpracuje z platformą .NET Core i .NET Framework.

## <a name="configuration"></a>Konfiguracja

**Dlaczego Live Unit Testing nie działa po włączeniu?**

Okno dane wyjściowe (po wybraniu listy rozwijanej Live Unit Testing jest zaznaczone) powinien poinformować, dlaczego Live Unit Testing nie działa. Live Unit Testing mogą nie funkcjonować z jednego z następujących powodów:

- Jeśli pakiety NuGet, do których odwołują się projekty w rozwiązaniu, nie zostały przywrócone, Live Unit Testing nie będą działały. Przed włączeniem Live Unit Testing należy rozwiązać ten problem, wykonując jawną kompilację rozwiązania lub przywracając pakiety NuGet w rozwiązaniu.

- Jeśli używasz testów opartych na MSTest w projektach, upewnij się, że usunięto odwołanie do `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i Dodaj odwołania do najnowszych pakietów NuGet MSTest, `MSTest.TestAdapter` (wymagana jest minimalna wersja 1.1.11) i `MSTest.TestFramework` (wymagana jest minimalna wersja 1.1.11). Aby uzyskać więcej informacji, zobacz sekcję "obsługiwane struktury testów" [w artykule korzystanie Live Unit Testing w programie Visual Studio](live-unit-testing.md#supported-test-frameworks) .

- Co najmniej jeden projekt w rozwiązaniu powinien mieć odwołanie do programu NuGet lub bezpośrednie odwołanie do platformy testowej xUnit, NUnit lub MSTest. Ten projekt powinien również odwoływać się do odpowiednich pakietów NuGet kart testowych programu Visual Studio. Do adaptera testowego programu Visual Studio można także odwoływać się za pomocą pliku *. runsettings* . Plik *. runsettings* musi mieć wpis podobny do następującego:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nieprawidłowe pokrycie po uaktualnieniu

**Dlaczego Live Unit Testing pokazać błędne pokrycie po uaktualnieniu adaptera testowego, do którego odwołuje się projekt programu Visual Studio, do obsługiwanej wersji?**

- Jeśli wiele projektów w rozwiązaniu odwołuje się do pakietu adaptera testowego NuGet, każdy z nich musi zostać uaktualniony do obsługiwanej wersji.

- Upewnij się, że plik MSBuild *. props* zaimportowany z pakietu adaptera testowego również został poprawnie zaktualizowany. Sprawdź wersję pakietu NuGet/ścieżkę importu, która zwykle znajduje się w górnej części pliku projektu, tak jak poniżej:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Dostosuj kompilacje

**Czy mogę dostosować kompilacje Live Unit Testing?**

Jeśli rozwiązanie wymaga niestandardowych kroków do kompilowania Instrumentacji (Live Unit Testing), które nie są wymagane dla "regularnej" kompilacji bez instrumentacji, wówczas można dodać kod do projektu lub plików *docelowych* , które sprawdzają `BuildingForLiveUnitTesting` Właściwość i wykonuje niestandardowe kroki kompilacji pre/post. Można również usunąć niektóre kroki kompilacji (na przykład Publikowanie lub generowanie pakietów) lub dodać kroki kompilacji (na przykład kopiowanie wymagań wstępnych) do kompilacji Live Unit Testing opartej na tej właściwości projektu. Dostosowanie kompilacji opartej na tej właściwości nie powoduje zmiany regularnej kompilacji w żaden sposób i ma wpływ tylko na kompilacje Live Unit Testing.

Na przykład może istnieć obiekt docelowy, który tworzy pakiety NuGet podczas zwykłej kompilacji. Prawdopodobnie nie chcesz generować pakietów NuGet po każdej edycji. Aby można było wyłączyć ten cel w ramach kompilacji Live Unit Testing, należy wykonać następujące czynności:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Komunikaty o błędach z \<OutputPath> , \<OutDir> lub \<IntermediateOutputPath>

**Dlaczego otrzymuję następujący błąd, gdy Live Unit Testing próbuje skompilować moje rozwiązanie: "... wydaje się ustawić bezwarunkowo `<OutputPath>` lub `<OutDir>` . Live Unit Testing nie będzie wykonywać testów z zestawu wyjściowego "?**

Ten błąd może wystąpić, jeśli proces kompilacji dla Twojego rozwiązania ma logikę niestandardową, która określa, gdzie powinny być generowane pliki binarne. Domyślnie lokalizacja plików binarnych zależy od systemu `<OutputPath>` , lub i `<OutDir>` `<IntermediateOutputPath>` `<BaseOutputPath>` `<BaseIntermediateOutputPath>` .

Live Unit Testing zastępuje te zmienne, aby upewnić się, że artefakty kompilacji są upuszczane do folderu Live Unit Testing artefakty i zakończą się niepowodzeniem, jeśli proces kompilacji również zastępuje te zmienne.

Istnieją dwa główne podejścia do pomyślnej kompilacji Live Unit Testing. Aby ułatwić konfigurację kompilacji, można oprzeć ścieżki wyjściowe na `<BaseIntermediateOutputPath>` . Aby uzyskać bardziej skomplikowane konfiguracje, można oprzeć ścieżki wyjściowe `<LiveUnitTestingBuildRootPath>` .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Zastępowanie `<OutputPath>` / `<IntermediateOutputPath>` warunkowo na podstawie `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` .

> [!NOTE]
> Aby skorzystać z tej metody, każdy projekt musi być w stanie niezależny od siebie. Podczas kompilowania nie ma jednego artefaktu odwołania do projektu z innego projektu. Nie ma możliwości dynamicznego ładowania zestawów z innego projektu w czasie wykonywania (na przykład wywołania `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")` ).

Podczas kompilacji Live Unit Testing automatycznie przesłania `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` zmienne do folderu Live Unit Testing artefaktów.

Na przykład, jeśli kompilacja zastępuje <OutputPath> poniższy sposób:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

następnie można zastąpić go następującym kodem XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Gwarantuje to, że `<OutputPath>` znajduje się w `<BaseOutputPath>` folderze.

Nie przesłonięcia `<OutDir>` bezpośrednio w procesie kompilacji; zamiast tego Przesłoń, `<OutputPath>` Aby porzucić artefakty kompilacji do określonej lokalizacji.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Zastępowanie właściwości na podstawie `<LiveUnitTestingBuildRootPath>` właściwości.

> [!NOTE]
> W tym podejściu należy zachować ostrożność w przypadku plików dodanych w folderze artefaktów, które nie są generowane podczas kompilacji. W poniższym przykładzie pokazano, co należy zrobić podczas umieszczania folderu Packages w obszarze artefakty. Ponieważ zawartość tego folderu nie jest generowana podczas kompilacji, właściwość MSBuild **nie powinna być zmieniana**.

Podczas kompilacji Live Unit Testing `<LiveUnitTestingBuildRootPath>` Właściwość jest ustawiana na lokalizację folderu Live Unit Testing artefaktów.

Załóżmy na przykład, że w projekcie znajduje się struktura.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Podczas kompilacji Live Unit Testing `<LiveUnitTestingBuildRootPath>` Właściwość jest ustawiona na pełną ścieżkę `.vs\...\lut\0\b` . Jeśli projekt definiuje `<ArtifactsRoot>` Właściwość, która jest mapowana na katalog rozwiązania, można zaktualizować projekt MSBuild w następujący sposób:

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

**Chcę, aby artefakty Live Unit Testing kompilację przechodzą do określonej lokalizacji zamiast domyślnej lokalizacji w folderze *. vs* . Jak mogę to zmienić?**

Ustaw `LiveUnitTesting_BuildRoot` zmienną środowiskową na poziomie użytkownika na ścieżkę, w której chcesz porzucić artefakty kompilacji Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Eksplorator testów a Live Unit Testing

**Jak uruchomione testy z okna Eksploratora testów różnią się od uruchamiania testów w Live Unit Testing?**

Istnieje kilka różnic:

- Uruchamianie lub debugowanie testów z okna **Eksploratora testów** powoduje uruchomienie zwykłych plików binarnych, podczas gdy Live Unit Testing uruchamia instrumentację plików binarnych. Jeśli chcesz debugować instrumentację plików binarnych, dodając [debuger.](xref:System.Diagnostics.Debugger.Launch) wywołanie metody uruchamiania w metodzie testowej powoduje, że debuger jest uruchamiany za każdym razem, gdy ta metoda jest wykonywana (w tym gdy jest wykonywane przez Live Unit Testing), a następnie można dołączyć i debugować plik binarny Instrumentacji. Mamy nadzieję, że Instrumentacja jest niewidoczna dla większości scenariuszy użytkownika i nie ma potrzeby debugowania plików binarnych instrumentacji.

- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale testy są uruchamiane z okna **Eksplorator testów** Utwórz nową domenę aplikacji.

- Live Unit Testing uruchamia testy w każdym zestawie testów sekwencyjnie. W **Eksploratorze testów** można wybrać uruchamianie wielu testów równolegle.

- **Eksplorator testów** uruchamia testy w jednowątkowym apartamentie (STA) domyślnie, a Live Unit Testing uruchamia testy w wielowątkowym apartamentie (MTA). Aby uruchomić testy MSTest w STA w Live Unit Testing, dekorować metodę testową lub klasy zawierającej z `<STATestMethod>` `<STATestClass>` atrybutem lub, który można znaleźć w `MSTest.STAExtensions 1.0.3-beta` pakiecie NuGet. Dla NUnit, dekorować metodę testową z `<RequiresThread(ApartmentState.STA)>` atrybutem i dla xUnit, z `<STAFact>` atrybutem.

## <a name="exclude-tests"></a>Wyklucz testy

**Jak mogę wykluczyć testy z uczestnictwa w Live Unit Testing?**

Zobacz sekcję "Dołączanie i Wyklucz projekty testowe i metody testowe" [w artykule Live Unit Testing w programie Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) , aby zapoznać się z ustawieniami specyficznymi dla użytkownika. Włączenie lub wyłączenie testów jest przydatne, gdy chcesz uruchomić określony zestaw testów dla konkretnej sesji edytowania lub zachować własne preferencje osobiste.

W przypadku ustawień specyficznych dla rozwiązania można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atrybut programowo, aby wykluczyć metody, właściwości, klasy lub struktury z instrumentacji Live Unit Testing. Ponadto można również ustawić `<ExcludeFromCodeCoverage>` Właściwość na `true` w pliku projektu, aby wykluczyć cały projekt z Instrumentacji. Live Unit Testing nadal będzie uruchamiać testy, które nie zostały instrumentacji, ale ich pokrycie nie zostanie wizualizacją.

Możesz również sprawdzić, czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` jest załadowany w bieżącej domenie aplikacji i wyłączyć testy na podstawie tego, dlaczego. Można na przykład wykonać następujące czynności w programie xUnit:

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

**Dlaczego nagłówki Win32 PE różnią się w zestawach Instrumentacji utworzonych przez testy jednostkowe na żywo?**

Ten problem został rozwiązany i nie istnieje w programie Visual Studio 2017 w wersji 15,3 lub nowszej.

W przypadku starszych wersji programu Visual Studio 2017 istnieje znany błąd, który może spowodować niepowodzenie Live Unit Testing kompilacje w celu osadzenia następujących danych nagłówka Win32 PE:

- Wersja pliku (określona przez @System.Reflection.AssemblyFileVersionAttribute w kodzie).

- Ikona Win32 (określona przez `/win32icon:` wiersz polecenia).

- Manifest Win32 (określony przez `/win32manifest:` wiersz polecenia).

Testy, które opierają się na tych wartościach, mogą zakończyć się niepowodzeniem podczas testów jednostkowych na żywo.

::: moniker-end

## <a name="continuous-builds"></a>Kompilacje ciągłe

**Dlaczego usługa Live Unit Testing kontynuuje Kompilowanie mojego rozwiązania przez cały czas, nawet jeśli nie wprowadzam żadnych zmian?**

Rozwiązanie może zostać skompilowane nawet wtedy, gdy nie wprowadzasz edycji, jeśli proces kompilacji generuje kod źródłowy, który jest częścią rozwiązania, a pliki docelowe kompilacji nie mają odpowiednich danych wejściowych i danych wyjściowych. Elementy docelowe powinny mieć listę danych wejściowych i wyjściowych, aby program MSBuild mógł wykonać odpowiednie aktualne sprawdzenia i określić, czy jest wymagana Nowa kompilacja.

Live Unit Testing uruchamia kompilację za każdym razem, gdy wykryje, że pliki źródłowe uległy zmianie. Ponieważ kompilacja rozwiązania generuje pliki źródłowe, Live Unit Testing pobiera w nieskończoną pętlę kompilacji. Jeśli jednak dane wejściowe i wyjściowe elementu docelowego są sprawdzane, gdy Live Unit Testing rozpoczyna drugą kompilację (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), spowoduje to przerwanie działania pętli kompilacji, ponieważ testy danych wejściowych i wyjściowych wskazują, że wszystko jest aktualne.

## <a name="editor-icons"></a>Ikony edytora

**Dlaczego nie widzę żadnych ikon w edytorze, mimo że Live Unit Testing wygląda na to, że testy są uruchamiane na podstawie komunikatów w oknie danych wyjściowych?**

W edytorze mogą nie być widoczne ikony, jeśli zestawy, na których działa Live Unit Testing, nie są z jakiegokolwiek powodu Instrumentacją. Na przykład Live Unit Testing nie jest zgodny z projektami, które ustawiono `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` . W takim przypadku należy zaktualizować proces kompilacji w celu usunięcia tego ustawienia lub zmiany go na `true` Live Unit Testing działać. 

## <a name="capture-logs"></a>Dzienniki przechwytywania

**Jak mogę zebrać więcej szczegółowych dzienników do raportów o błędach plików?**

Aby zebrać więcej szczegółowych dzienników, można wykonać kilka czynności:

- Przejdź do **Tools**  >  **opcji** narzędzia  >  **Live Unit Testing** i zmień opcję rejestrowania na **pełne**. Pełne rejestrowanie powoduje wyświetlenie bardziej szczegółowych dzienników w oknie **danych wyjściowych** .

- Ustaw `LiveUnitTesting_BuildLog` zmienną środowiskową użytkownika na nazwę pliku, który ma być używany do przechwytywania dziennika programu MSBuild. Szczegółowe komunikaty dziennika programu MSBuild z kompilacji Live Unit Testing można następnie pobrać z tego pliku.

- Ustaw `LiveUnitTesting_TestPlatformLog` zmienną środowiskową użytkownika, aby `1` przechwycić dziennik platformy testów. Szczegółowe komunikaty dziennika platformy testowej z przebiegów Live Unit Testing można następnie pobrać z programu `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` .

- Utwórz zmienną środowiskową na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS` i ustaw ją na 1 (lub dowolną wartość) i uruchom ponownie program Visual Studio. Teraz na karcie **testy danych wyjściowych** w programie Visual Studio powinna zostać wyświetlona duża liczba dzienników.

## <a name="see-also"></a>Zobacz też

- [Live Unit Testing](live-unit-testing.md)
