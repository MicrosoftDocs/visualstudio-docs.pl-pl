---
title: Live Unit Testing — często zadawane pytania
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: jillre
ms.author: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8db8264268eb04edc3140d0e2a6ece5896692e38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653036"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing często zadawane pytania

## <a name="supported-frameworks"></a>Obsługiwane struktury

**Jakie platformy testowe Live Unit Testing obsługiwać i jakie są minimalne obsługiwane wersje?**

Live Unit Testing współpracuje z trzema popularnymi platformami testowania jednostkowego wymienionymi w poniższej tabeli. Minimalna obsługiwana wersja ich kart i struktur również znajduje się w tabeli. Struktur testowania jednostek są dostępne w witrynie NuGet.org.

|Struktury testowej  |Minimalna wersja programu Visual Studio karty  |Minimalna wersja Framework  |
|---------|---------|---------|
|xUnit.net |2\.2.0-beta3-build1187 wersji xunit.Runner.VisualStudio |xunit 1.9.2 |
|Rozszerzenie NUnit |NUnit3TestAdapter wersja 3.7.0 |Wersja 3.5.0 NUnit |
|MSTest |MSTest.TestAdapter 1.1.4-preview |1\.0.5-preview rozwiązań MSTest.TestFramework |

Jeśli masz starsze projekty testowe bazujące na MSTestach odwołujące się `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przenosić do nowszych pakietów NuGet MSTest, przeprowadź uaktualnienie do programu Visual Studio 2019 lub Visual Studio 2017.

W niektórych przypadkach może być konieczne jawne Przywracanie pakietów NuGet, odwołują się projekty w rozwiązaniu aby Live Unit Testing do pracy. Pakiety można przywrócić, wykonując jawną kompilację rozwiązania (wybierz opcję **kompiluj** > **Skompiluj ponownie rozwiązanie** z menu programu Visual Studio najwyższego poziomu) lub klikając rozwiązanie prawym przyciskiem myszy i wybierając pozycję **Przywróć pakiety NuGet** przed włączeniem testów jednostkowych.

## <a name="net-core-support"></a>Obsługa platformy .NET Core

**Czy Live Unit Testing współpracuje z platformą .NET Core?**

Tak. Live Unit Testing współpracuje z platformą .NET Core i .NET Framework.

## <a name="configuration"></a>Konfiguracja

**Dlaczego Live Unit Testing nie działa po włączeniu?**

Okno dane wyjściowe (po wybraniu listy rozwijanej Live Unit Testing jest zaznaczone) powinien poinformować, dlaczego Live Unit Testing nie działa. Live Unit Testing mogą nie funkcjonować z jednego z następujących powodów:

- Jeśli pakiety NuGet, do których odwołują się projekty w rozwiązaniu, nie zostały przywrócone, Live Unit Testing nie będą działały. Przed włączeniem Live Unit Testing należy rozwiązać ten problem, wykonując jawną kompilację rozwiązania lub przywracając pakiety NuGet w rozwiązaniu.

- Jeśli używasz testów opartych na MSTest w projektach, upewnij się, że usuniesz odwołanie do `Microsoft.VisualStudio.QualityTools.UnitTestFramework`i Dodaj odwołania do najnowszych pakietów NuGet MSTest, `MSTest.TestAdapter` (minimalna wersja 1.1.11 jest wymagana) i `MSTest.TestFramework` (wymagana jest minimalna wersja 1.1.11). Aby uzyskać więcej informacji, zobacz sekcję "obsługiwane struktury testów" [w artykule korzystanie Live Unit Testing w programie Visual Studio](live-unit-testing.md#supported-test-frameworks) .

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

Jeśli rozwiązanie wymaga niestandardowych kroków do kompilowania Instrumentacji (Live Unit Testing), które nie są wymagane dla kompilacji "regularna", wówczas można dodać kod do projektu lub plików *docelowych* , które sprawdzają Właściwość `BuildingForLiveUnitTesting` i wykonują niestandardowe kroki wstępnej kompilacji. Można również usunąć niektóre kroki kompilacji (na przykład Publikowanie lub generowanie pakietów) lub dodać kroki kompilacji (na przykład kopiowanie wymagań wstępnych) do kompilacji Live Unit Testing opartej na tej właściwości projektu. Dostosowanie kompilacji opartej na tej właściwości nie powoduje zmiany regularnej kompilacji w żaden sposób i ma wpływ tylko na kompilacje Live Unit Testing.

Na przykład może istnieć obiekt docelowy, który tworzy pakiety NuGet podczas zwykłej kompilacji. Prawdopodobnie nie chcesz generować pakietów NuGet po każdej edycji. Aby można było wyłączyć ten cel w ramach kompilacji Live Unit Testing, należy wykonać następujące czynności:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-or-outdir"></a>Komunikaty o błędach z \<OutputPath > lub \<OutDir >

**Dlaczego otrzymuję następujący błąd, gdy Live Unit Testing próbuje skompilować moje rozwiązanie: "... wydaje się, aby bezwarunkowo ustawić `<OutputPath>` lub `<OutDir>`. Live Unit Testing nie będzie wykonywać testów z zestawu wyjściowego "?**

Ten błąd może wystąpić, jeśli proces kompilacji niewarunkowo zastępuje `<OutputPath>` lub `<OutDir>`, tak że nie jest podkatalogiem `<BaseOutputPath>`. W takich przypadkach Live Unit Testing nie będzie działał, ponieważ również zastępuje te wartości, aby upewnić się, że artefakty kompilacji są upuszczane do folderu w obszarze `<BaseOutputPath>`. Jeśli musisz zastąpić lokalizację, w której artefakty kompilacji mają zostać porzucone w regularnej kompilacji, przesłonić `<OutputPath>` warunkowo na podstawie `<BaseOutputPath>`.

Na przykład jeśli kompilacja przesłania `<OutputPath>`, jak pokazano poniżej:

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

Dzięki temu `<OutputPath>` znajduje się w `<BaseOutputPath>` folderze.

Nie należy przesłaniać `<OutDir>` bezpośrednio w procesie kompilacji; Zamiast tego Przesłoń `<OutputPath>`, aby porzucić artefakty kompilacji do określonej lokalizacji.

## <a name="build-artifact-location"></a>Lokalizacja artefaktu kompilacji

**Chcę, aby artefakty Live Unit Testing kompilację przechodzą do określonej lokalizacji zamiast domyślnej lokalizacji w folderze *. vs* . Jak mogę to zmienić?**

Ustaw zmienną środowiskową na poziomie użytkownika `LiveUnitTesting_BuildRoot` na ścieżkę, w której mają zostać porzucone Live Unit Testing kompilacji. 

## <a name="test-explorer-versus-live-unit-testing"></a>Eksplorator testów a Live Unit Testing

**Jak uruchomione testy z okna Eksploratora testów różnią się od uruchamiania testów w Live Unit Testing?**

Istnieje kilka różnic:

- Uruchamianie lub debugowanie testów z okna **Eksploratora testów** powoduje uruchomienie zwykłych plików binarnych, podczas gdy Live Unit Testing uruchamia instrumentację plików binarnych. Jeśli chcesz debugować instrumentację plików binarnych, dodając [debuger. Uruchom](xref:System.Diagnostics.Debugger.Launch) wywołanie metody w metodzie testowej powoduje, że debuger uruchamia się za każdym razem, gdy ta metoda jest wykonywana (w tym gdy jest wykonywana przez Live Unit Testing), a następnie można dołączyć i debugować plik binarny Instrumentacji. Mamy nadzieję, że Instrumentacja jest niewidoczna dla większości scenariuszy użytkownika i nie ma potrzeby debugowania plików binarnych instrumentacji.

- Live Unit Testing nie tworzy nowej domeny aplikacji do uruchamiania testów, ale testy są uruchamiane z okna **Eksplorator testów** Utwórz nową domenę aplikacji.

- Live Unit Testing uruchamia testy w każdym zestawie testów po kolei. W **Eksploratorze testów**można wybrać uruchamianie wielu testów równolegle.

- Odnajdywanie i wykonywanie testów w Live Unit Testing używa wersji 2 `TestPlatform`, podczas gdy okno **Eksplorator testów** używa wersji 1. Nie zauważysz różnicy w większości przypadków, chociaż.

- **Eksplorator testów** uruchamia testy w jednowątkowym apartamentie (STA) domyślnie, a Live Unit Testing uruchamia testy w wielowątkowym apartamentie (MTA). Aby uruchomić testy MSTest w STA w Live Unit Testing, dekorować metodę testową lub klasy zawierającej z atrybutem `<STATestMethod>` lub `<STATestClass>`, który można znaleźć w pakiecie NuGet `MSTest.STAExtensions 1.0.3-beta`. Dla NUnit, dekorować metodę testową z atrybutem `<RequiresThread(ApartmentState.STA)>` i dla xUnit z atrybutem `<STAFact>`.

## <a name="exclude-tests"></a>Wyklucz testy

**Jak mogę wykluczyć testy z uczestnictwa w Live Unit Testing?**

Zobacz sekcję "Dołączanie i Wyklucz projekty testowe i metody testowe" [w artykule Live Unit Testing w programie Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) , aby zapoznać się z ustawieniami specyficznymi dla użytkownika. Włączenie lub wyłączenie testów jest przydatne, gdy chcesz uruchomić określony zestaw testów dla konkretnej sesji edytowania lub zachować własne preferencje osobiste.

W przypadku ustawień specyficznych dla rozwiązania można zastosować atrybut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> programowo, aby wykluczyć metody, właściwości, klasy lub struktury z Instrumentacji przez Live Unit Testing. Ponadto można również ustawić właściwość `<ExcludeFromCodeCoverage>` na `true` w pliku projektu, aby wykluczyć cały projekt z Instrumentacji. Live Unit Testing nadal będzie uruchamiać testy, które nie zostały instrumentacji, ale ich pokrycie nie zostanie wizualizacją.

Możesz również sprawdzić, czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` jest załadowana w bieżącej domenie aplikacji i wyłączyć testy w zależności od tego, dlaczego. Można na przykład wykonać następujące czynności w programie xUnit:

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

- Ikona Win32 (określona przez `/win32icon:` w wierszu polecenia).

- Manifest Win32 (określony przez `/win32manifest:` w wierszu polecenia).

Testy, które opierają się na tych wartościach, mogą zakończyć się niepowodzeniem podczas testów jednostkowych na żywo.

::: moniker-end

## <a name="continuous-builds"></a>Kompilacje ciągłe

**Dlaczego usługa Live Unit Testing kontynuuje Kompilowanie mojego rozwiązania przez cały czas, nawet jeśli nie wprowadzam żadnych zmian?**

Rozwiązanie może zostać skompilowane nawet wtedy, gdy nie wprowadzasz edycji, jeśli proces kompilacji generuje kod źródłowy, który jest częścią rozwiązania, a pliki docelowe kompilacji nie mają odpowiednich danych wejściowych i danych wyjściowych. Elementy docelowe powinny mieć listę danych wejściowych i wyjściowych, aby program MSBuild mógł wykonać odpowiednie aktualne sprawdzenia i określić, czy jest wymagana Nowa kompilacja.

Live Unit Testing uruchamia kompilację za każdym razem, gdy wykryje, że pliki źródłowe uległy zmianie. Ponieważ kompilacja rozwiązania generuje pliki źródłowe, Live Unit Testing pobiera w nieskończoną pętlę kompilacji. Jeśli jednak dane wejściowe i wyjściowe elementu docelowego są sprawdzane, gdy Live Unit Testing rozpoczyna drugą kompilację (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), spowoduje to przerwanie działania pętli kompilacji, ponieważ dane wejściowe i wyjściowe sprawdzają, że wszystko jest aktualne.

## <a name="editor-icons"></a>Ikony edytora

**Dlaczego nie widzę żadnych ikon w edytorze, mimo że Live Unit Testing wygląda na to, że testy są uruchamiane na podstawie komunikatów w oknie danych wyjściowych?**

W edytorze mogą nie być widoczne ikony, jeśli zestawy, na których działa Live Unit Testing, nie są z jakiegokolwiek powodu Instrumentacją. Na przykład Live Unit Testing nie jest zgodny z projektami ustawionymi `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. W takim przypadku należy zaktualizować proces kompilacji w celu usunięcia tego ustawienia lub zmiany na `true`, aby Live Unit Testing działał. 

## <a name="capture-logs"></a>Dzienniki przechwytywania

**Jak mogę zebrać więcej szczegółowych dzienników do raportów o błędach plików?**

Aby zebrać więcej szczegółowych dzienników, można wykonać kilka czynności:

- Przejdź do pozycji **narzędzia** > **Opcje** > **Live Unit Testing** i zmień opcję rejestrowania na **pełne**. Pełne rejestrowanie powoduje wyświetlenie bardziej szczegółowych dzienników w oknie **danych wyjściowych** .

- Ustaw zmienną środowiskową użytkownika `LiveUnitTesting_BuildLog` na nazwę pliku, który ma być używany do przechwytywania dziennika programu MSBuild. Szczegółowe komunikaty dziennika programu MSBuild z kompilacji Live Unit Testing można następnie pobrać z tego pliku.

- Ustaw zmienną środowiskową `LiveUnitTesting_TestPlatformLog` użytkownika na `1`, aby przechwycić dziennik platformy testowej. Szczegółowe komunikaty dziennika platformy testowej z przebiegów Live Unit Testing można następnie pobrać z `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Utwórz zmienną środowiskową na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS` i ustaw ją na 1 (lub dowolną wartość) i uruchom ponownie program Visual Studio. Teraz na karcie **testy danych wyjściowych** w programie Visual Studio powinna zostać wyświetlona duża liczba dzienników.

## <a name="see-also"></a>Zobacz także

- [Testy jednostkowe na żywo](live-unit-testing.md)
