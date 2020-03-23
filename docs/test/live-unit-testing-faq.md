---
title: Live Unit Testing — często zadawane pytania
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591544"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Często zadawane pytania dotyczące testowania jednostek na żywo

## <a name="supported-frameworks"></a>Obsługiwane struktury

**Jakie struktury testów obsługuje testowanie jednostek na żywo i jakie są minimalne obsługiwane wersje?**

Live Unit Testing współpracuje z trzech popularnych jednostek testowania struktur wymienionych w poniższej tabeli. Minimalna obsługiwana wersja ich kart i struktur jest również wymieniona w tabeli. Struktury testowania jednostkowego są dostępne od NuGet.org.

|Struktura testów  |Minimalna wersja karty programu Visual Studio  |Minimalna wersja ramowa  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio wersja 2.2.0-beta3-build1187 |xjedna 1.9.2 |
|Nunit |NUnit3TestAdapter wersja 3.7.0 |NUnit w wersji 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-podgląd |MSTest.TestFramework 1.0.5-podgląd |

Jeśli masz starsze projekty testowe `Microsoft.VisualStudio.QualityTools.UnitTestFramework` oparte na MSTest, które odwołują się do i nie chcesz przenieść do nowszych pakietów MSTest NuGet, uaktualnij do programu Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne przywrócenie pakietów NuGet, do których odwołuje się projekty w rozwiązaniu, aby testy jednostek na żywo działały. Pakiety można przywrócić, wykonując jawną kompilację rozwiązania (wybierz **build** > **rebuild solution** z menu programu Visual Studio najwyższego poziomu) lub klikając prawym przyciskiem myszy rozwiązanie i wybierając **przywróć pakiety NuGet** przed włączeniem testowania jednostek mieszkalnych.

## <a name="net-core-support"></a>Obsługa .NET Core

**Czy testowanie jednostek na żywo działa z programem .NET Core?**

Tak. Testowanie jednostek na żywo współpracuje z programem .NET Core i platformą .NET Framework.

## <a name="configuration"></a>Konfigurowanie

**Dlaczego testy jednostek na żywo nie działają po włączeniu?**

Okno Dane wyjściowe (po wybraniu listy rozwijanej Live Unit Testing) powinno być zaznaczone, dlaczego testowanie jednostek na żywo nie działa. Testy jednostkowe na żywo mogą nie działać z jednego z następujących powodów:

- Jeśli pakiety NuGet, do których odwołuje się projekty w rozwiązaniu, nie zostały przywrócone, testowanie jednostek na żywo nie będzie działać. Wykonanie jawnej kompilacji rozwiązania lub przywrócenie pakietów NuGet w rozwiązaniu przed włączeniem live unit testing należy rozwiązać ten problem.

- Jeśli używasz testów opartych na MSTest w projektach, `Microsoft.VisualStudio.QualityTools.UnitTestFramework`upewnij się, że usuniesz odwołanie `MSTest.TestAdapter` do , i dodaj odwołania do najnowszych pakietów MSTest NuGet (wymagana jest minimalna wersja 1.1.11) i `MSTest.TestFramework` (wymagana jest minimalna wersja 1.1.11). Aby uzyskać więcej informacji, zobacz sekcję "Obsługiwane struktury testów" artykułu [Użyj testowania jednostek na żywo w programie Visual Studio.](live-unit-testing.md#supported-test-frameworks)

- Co najmniej jeden projekt w rozwiązaniu powinien mieć odwołanie NuGet lub bezpośrednie odwołanie do struktury testów xUnit, NUnit lub MSTest. Ten projekt powinien również odwoływać się do odpowiednich kart testowych programu Visual Studio pakietu NuGet. Karta testowa programu Visual Studio można również odwoływać się za pośrednictwem pliku *runsettings.* Plik *runsettings* musi mieć wpis podobny do następującego przykładu:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nieprawidłowe pokrycie po uaktualnieniu

**Dlaczego testy jednostek na żywo wykazują niepoprawne pokrycie po uaktualnieniu karty testowej, do której odwołuje się w projektach programu Visual Studio do obsługiwanej wersji?**

- Jeśli wiele projektów w rozwiązaniu odwołuje się do pakietu karty testowej NuGet, każdy z nich musi zostać uaktualniony do obsługiwanej wersji.

- Upewnij się, że plik MSBuild *.props* zaimportowany z pakietu karty testowej również został poprawnie zaktualizowany. Sprawdź wersję pakietu NuGet/ścieżkę importu, który zwykle można znaleźć w górnej części pliku projektu, jak poniżej:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Dostosowywanie kompilacji

**Czy mogę dostosować kompilacje testów jednostek na żywo?**

Jeśli rozwiązanie wymaga niestandardowych kroków do tworzenia instrumentacji (Live Unit Testing), które nie są wymagane dla "regularnych" kompilacji nieprzyrządzowanego, następnie można dodać kod do projektu lub *.targets* plików, które sprawdza `BuildingForLiveUnitTesting` właściwości i wykonuje niestandardowe kroki kompilacji przed/post. Można również usunąć niektóre kroki kompilacji (takie jak publikowanie lub generowanie pakietów) lub dodać kroki kompilacji (takie jak wymagania wstępne kopiowania) do kompilacji testowania jednostek na żywo na podstawie tej właściwości projektu. Dostosowywanie kompilacji na podstawie tej właściwości nie zmienia regularne kompilacji w żaden sposób i wpływa tylko na kompilacje testowania jednostek na żywo.

Na przykład może istnieć obiekt docelowy, który produkuje pakiety NuGet podczas zwykłej kompilacji. Prawdopodobnie nie chcesz, aby pakiety NuGet były generowane po każdej edycji. Dlatego można wyłączyć ten cel w kompilacji Testowanie jednostek na żywo, wykonując następujące czynności:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Komunikaty \<o błędach z \<> OutputPath, OutDir> lub \<IntermediateOutputPath>

**Dlaczego pojawia się następujący błąd, gdy testy jednostek na żywo próbują zbudować moje rozwiązanie: "... wydaje się bezwarunkowo `<OutputPath>` `<OutDir>`ustawione lub . Live Unit Testing nie wykona testów z zestawu wyjściowego"?**

Ten błąd można uzyskać, jeśli proces kompilacji dla rozwiązania ma niestandardową logikę, która określa, gdzie powinny być generowane pliki binarne. Domyślnie lokalizacja plików binarnych `<OutputPath>` `<OutDir>` zależy `<IntermediateOutputPath>` od `<BaseOutputPath>` , `<BaseIntermediateOutputPath>`lub jak również lub .

Testowanie jednostek na żywo zastępuje te zmienne, aby upewnić się, że artefakty kompilacji są porzucone do folderu artefaktów testowania jednostek na żywo i zakończy się niepowodzeniem, jeśli proces kompilacji również zastępuje te zmienne.

Istnieją dwa główne podejścia, aby pomyślnie wykonać kompilację testowania jednostek na żywo. Aby ułatwić konfiguracje kompilacji, można oprzeć `<BaseIntermediateOutputPath>`ścieżki wyjściowe na programie . W przypadku bardziej złożonych konfiguracji można `<LiveUnitTestingBuildRootPath>`oprzeć ścieżki wyjściowe na programie .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Zastępowanie `<OutputPath>` / `<IntermediateOutputPath>` warunkowo na `<BaseOutputPath>` / `<BaseIntermediateOutputPath>`podstawie .

> [!NOTE]
> Aby korzystać z tego podejścia, każdy projekt musi być w stanie budować niezależnie od siebie. Nie ma jednego artefaktów odniesienia projektu z innego projektu podczas kompilacji. Nie ma jednego projektu dynamicznie załadować zestawy z innego `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`projektu w czasie wykonywania (na przykład wywołanie).

Podczas kompilacji live unit testing automatycznie `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` zastępuje zmienne do docelowego live unit testing artefaktów folderu.

Jeśli na przykład kompilacja zastąpi <OutputPath> poniższe informacje:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

następnie można go zastąpić następującym XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Dzięki temu `<OutputPath>` znajduje się `<BaseOutputPath>` w folderze.

Nie należy zastępować `<OutDir>` bezpośrednio w procesie kompilacji; zamiast tego `<OutputPath>` należy usunąć artefakty kompilacji do określonej lokalizacji.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Zastępowanie właściwości na podstawie `<LiveUnitTestingBuildRootPath>` właściwości.

> [!NOTE]
> W tym podejściu należy uważać na pliki dodane w folderze artefaktów, które nie są generowane podczas kompilacji. W poniższym przykładzie pokazano, co zrobić podczas umieszczania folderu pakietów w artefaktach. Ponieważ zawartość tego folderu nie są generowane podczas kompilacji, MSBuild właściwość **nie powinna być zmieniana**.

Podczas kompilacji testowania `<LiveUnitTestingBuildRootPath>` jednostek na żywo właściwość jest ustawiona na lokalizację live unit testing artefaktów folderu.

Załóżmy na przykład, że projekt ma strukturę pokazaną w tym miejscu.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Podczas live unit testing `<LiveUnitTestingBuildRootPath>` kompilacji, właściwość jest `.vs\...\lut\0\b`ustawiona na pełną ścieżkę . Jeśli projekt definiuje `<ArtifactsRoot>` właściwość, która jest mapowana do dir rozwiązania, można zaktualizować projekt MSBuild w następujący sposób:

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

## <a name="build-artifact-location"></a>Tworzenie lokalizacji artefaktów

**Chcę, aby artefakty kompilacji testowania jednostek na żywo przechodzili do określonej lokalizacji, a nie do domyślnej lokalizacji w folderze *.vs.* Jak mogę to zmienić?**

Ustaw `LiveUnitTesting_BuildRoot` zmienną środowiskową na poziomie użytkownika do ścieżki, w której chcesz artefakty kompilacji live unit testing, które mają zostać usunięte. 

## <a name="test-explorer-versus-live-unit-testing"></a>Eksplorator testów a testowanie jednostek na żywo

**Czym różni się uruchamianie testów z okna Eksploratora testów od uruchamiania testów w testach jednostkowych na żywo?**

Istnieje kilka różnic:

- Uruchamianie lub debugowanie testów z okna **Eksploratora testów** uruchamia regularne pliki binarne, podczas gdy testowanie jednostek na żywo uruchamia instrumentowane pliki binarne. Jeśli chcesz debugować instrumentowane pliki binarne, dodanie wywołania metody [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) w metodzie testowej powoduje, że debuger uruchamia się za każdym razem, gdy ta metoda jest wykonywana (w tym podczas wykonywania przez testowanie jednostek na żywo), a następnie można dołączyć i debugować instrumentowane binarne. Jednak mamy nadzieję, że instrumentacja jest przezroczyste dla większości scenariuszy użytkownika i że nie trzeba debugować instrumentowane pliki binarne.

- Testowanie jednostek na żywo nie tworzy nowej domeny aplikacji do uruchamiania testów, ale testy uruchamiane z okna **Eksploratora testów** tworzą nową domenę aplikacji.

- Live Unit Testing uruchamia testy w każdym zestawie testowym sekwencyjnie. W **Eksploratorze testów**można uruchomić wiele testów równolegle.

- **Eksplorator testów** domyślnie uruchamia testy w mieszkaniu jednowątkowym (STA), podczas gdy testy jednostek na żywo uruchamiają testy w mieszkaniu wielowątkowym (MTA). Aby uruchomić testy MSTest w STA w live unit testing, ozdobić `<STATestClass>` metodę testową lub `MSTest.STAExtensions 1.0.3-beta` zawierającą klasę z lub atrybut, `<STATestMethod>` który można znaleźć w pakiecie NuGet. Dla NUnit, udekoruj `<RequiresThread(ApartmentState.STA)>` metodę testową atrybutem i `<STAFact>` dla xUnit, za pomocą atrybutu.

## <a name="exclude-tests"></a>Wyklucz testy

**Jak wykluczyć testy z udziału w testach jednostkowych na żywo?**

Zobacz sekcję "Uwzględnij i wyklucz projekty testowe i metody testowe" artykułu [Użyj testowania jednostek na żywo w programie Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) dla ustawienia specyficznego dla użytkownika. Uwzględnienie lub wykluczenie testów jest przydatne, gdy chcesz uruchomić określony zestaw testów dla określonej sesji edycji lub utrwalić własne preferencje osobiste.

W przypadku ustawień specyficznych dla <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> rozwiązania można zastosować atrybut programowo, aby wykluczyć metody, właściwości, klasy lub struktury z instrumentów przez testowanie jednostek na żywo. Ponadto można również ustawić `<ExcludeFromCodeCoverage>` właściwość `true` w pliku projektu, aby wykluczyć cały projekt z instrumentów. Testy jednostkowe na żywo będą nadal uruchamiać testy, które nie zostały oprzyrządowane, ale ich zasięg nie zostanie wizualizowany.

Można również sprawdzić, czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` jest ładowany w bieżącej domenie aplikacji i wyłączyć testy na podstawie dlaczego. Na przykład można wykonać coś podobnego z xUnit:

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

**Dlaczego nagłówki Win32 PE różnią się w zespołach oprzyrządowanych zbudowanych w wyniku testowania jednostek na żywo?**

Ten problem został rozwiązany i nie istnieje w programie Visual Studio 2017 w wersji 15.3 i nowszych.

W przypadku starszych wersji programu Visual Studio 2017 istnieje znany błąd, który może spowodować, że kompilacje testów jednostek na żywo nie mogą osadzić następujących danych nagłówka win32 PE:

- Wersja pliku (określona w @System.Reflection.AssemblyFileVersionAttribute kodzie).

- Ikona Win32 `/win32icon:` (określona przez w wierszu polecenia).

- Manifest Win32 (określony przez `/win32manifest:` wiersz polecenia).

Testy, które opierają się na tych wartości może zakończyć się niepowodzeniem podczas wykonywania przez live unit testowania.

::: moniker-end

## <a name="continuous-builds"></a>Kompilacje ciągłe

**Dlaczego testy live unit cały czas budują moje rozwiązanie, nawet jeśli nie wprowadzam żadnych zmian?**

Rozwiązanie można utworzyć, nawet jeśli nie wprowadzasz zmian, jeśli proces kompilacji generuje kod źródłowy, który jest częścią samego rozwiązania, a pliki docelowe kompilacji nie mają odpowiednich danych wejściowych i wyjściowych określonych. Obiekty docelowe powinny mieć listę danych wejściowych i wyjściowych, tak aby MSBuild może wykonywać odpowiednie aktualne kontrole i określać, czy nowa kompilacja jest wymagana.

Live Unit Testing uruchamia kompilację za każdym razem, gdy wykryje, że pliki źródłowe uległy zmianie. Ponieważ kompilacja rozwiązania generuje pliki źródłowe, live unit testing dostaje się do nieskończonej pętli kompilacji. Jeśli jednak dane wejściowe i wyjściowe obiektu docelowego są sprawdzane podczas uruchamiania drugiej kompilacji podczas testowania jednostek na żywo (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), wypada ona z pętli kompilacji, ponieważ kontrole wejść i wyjść wskazują, że wszystko jest aktualne.

## <a name="editor-icons"></a>Ikony edytora

**Dlaczego nie widzę żadnych ikon w edytorze, mimo że live unit testing wydaje się być uruchomiony testy na podstawie komunikatów w oknie Dane wyjściowe?**

Ikony w edytorze mogą nie być widoczne, jeśli zestawy, na których działa testowanie jednostek na żywo, nie są instrumentowane z jakiegokolwiek powodu. Na przykład testowanie jednostek na żywo `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`nie jest zgodne z projektami, które są ustawione . W takim przypadku proces kompilacji musi zostać zaktualizowany, aby usunąć `true` to ustawienie lub zmienić je na do testowania jednostek na żywo do pracy. 

## <a name="capture-logs"></a>Przechwytywanie dzienników

**Jak zbierać bardziej szczegółowe dzienniki, aby zgłaszać błędy?**

Możesz wykonać kilka czynności, aby zebrać bardziej szczegółowe dzienniki:

- Przejdź do**pozycji Opcje** >  **narzędzi** > **Testowanie jednostek na żywo** i zmień opcję rejestrowania na **Pełne**. Pełne rejestrowanie powoduje, że bardziej szczegółowe dzienniki mają być wyświetlane w **output** okna.

- Ustaw `LiveUnitTesting_BuildLog` zmienną środowiskową użytkownika na nazwę pliku, którego chcesz użyć do przechwycenia dziennika MSBuild. Szczegółowe MSBuild komunikaty dziennika z live unit testing kompilacje można następnie pobrać z tego pliku.

- Ustaw `LiveUnitTesting_TestPlatformLog` zmienną środowiska `1` użytkownika do przechwytywania dziennika platformy testowej. Szczegółowe komunikaty dziennika platformy testowej z przebiegów `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`testowania jednostek na żywo można następnie pobrać z .

- Utwórz zmienną środowiskową `VS_UTE_DIAGNOSTICS` na poziomie użytkownika o nazwie i ustaw ją na 1 (lub dowolną wartość) i uruchom ponownie program Visual Studio. Teraz powinieneś zobaczyć wiele rejestrowania na dane **wyjściowe — testy** kartę w programie Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostek na żywo](live-unit-testing.md)
