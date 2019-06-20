---
title: Live Unit Testing — często zadawane pytania
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 1ed80454f6a87047de9e338d26c749d3c27a98ea
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67258133"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing — często zadawane pytania

## <a name="latest-features"></a>Najnowsze funkcje

**Live Unit Testing ulepszone i rozszerzone regularnie. Jak znaleźć informacje o najnowszych nowych funkcjach i rozszerzeniach?**

Aby dowiedzieć się więcej na temat nowych funkcji i ulepszeń, które zostały wprowadzone do Live Unit Testing, zobacz [What's New in Live Unit Testing](live-unit-testing-whats-new.md).

## <a name="supported-frameworks-and-versions"></a>Obsługiwane platformy i wersje

**Jakie platformy testowe jest Live Unit Testing pomocy technicznej i jakie są minimalne obsługiwane?**

Live Unit Testing działa z trzech struktur testowania jednostek popularne, wymienione w tabeli poniżej. Minimalna obsługiwana wersja ich kart i struktur również znajduje się w tabeli. Struktur testowania jednostek są dostępne w witrynie NuGet.org.

|Struktury testowej  |Minimalna wersja programu Visual Studio karty  |Minimalna wersja Framework  |
|---------|---------|---------|
|xUnit.net |2.2.0-beta3-build1187 wersji xunit.Runner.VisualStudio |xunit 1.9.2 |
|Rozszerzenie NUnit |Wersja NUnit3TestAdapter numer 3.7.0 |Wersja 3.5.0 NUnit |
|MSTest |MSTest.TestAdapter 1.1.4-preview |1.0.5-preview rozwiązań MSTest.TestFramework |

Jeśli masz starszą test oparte na narzędziu MSTest projektów tego odwołania `Microsoft.VisualStudio.QualityTools.UnitTestFramework` i nie chcesz przejść do nowszych pakietów MSTest NuGet, przeprowadź uaktualnienie do programu Visual Studio 2017 w wersji 15.4 lub nowszej.

W niektórych przypadkach może być konieczne jawne Przywracanie pakietów NuGet, odwołują się projekty w rozwiązaniu aby Live Unit Testing do pracy. Te pakiety można przywrócić albo wykonaj jawną kompilację rozwiązania (wybierz **kompilacji**, **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio), lub przez kliknięcie prawym przyciskiem myszy rozwiązanie i Wybieranie **Przywróć pakiety NuGet** przed włączeniem życia Unit Testing.

## <a name="net-core-support"></a>Obsługa platformy .NET core

**Usługa Live Unit Testing? z platformą .NET Core**

Tak. Live Unit Testing działa przy użyciu platformy .NET Core i .NET Framework. Obsługa platformy .NET Core został dodany w programie Visual Studio 2017 w wersji 15.3. Jeśli chcesz, aby Live Unit Testing pomocy technicznej dla platformy .NET Core, należy uaktualnić do tej wersji programu Visual Studio lub nowszej.

## <a name="configuration"></a>Konfiguracja

**Dlaczego nie Live Unit Testing działa po jego włączeniu?**

**Dane wyjściowe** okna (po wybraniu Live Unit Testing listy rozwijanej) powinien poinformować Cię, dlaczego Live Unit Testing nie działa. Live Unit Testing może nie działać w jednej z następujących przyczyn:

- Jeśli pakiety NuGet, które odwołują się projekty w rozwiązaniu nie zostały przywrócone, Live Unit Testing nie będzie działać. Wykonując jawną kompilację rozwiązania lub przywracania pakietów NuGet dla rozwiązania przed włączeniem Live Unit Testing powinno rozwiązać ten problem.

- Jeśli używasz testów opartych na MSTest w projektach, upewnij się, że usuwa odwołanie do `Microsoft.VisualStudio.QualityTools.UnitTestFramework`i dodaj odwołania do najnowszych pakietów MSTest NuGet `MSTest.TestAdapter` (wymagana jest minimalną wersję 1.1.11) i `MSTest.TestFramework` (minimalna wersja 1.1.11 jest wymagane). Aby uzyskać więcej informacji, zobacz sekcję "Obsługiwane platformy testowe" [Użyj Live Unit Testing w programie Visual Studio](live-unit-testing.md#supported-test-frameworks) artykułu.

- Co najmniej jednego projektu w rozwiązaniu powinien mieć odwołania NuGet lub bezpośrednie odwołanie do xUnit, NUnit, lub struktury testów MSTest. Ten projekt również powinny odwoływać się do odpowiedniego pakietu NuGet adapterów testowych programu Visual Studio. Adapter testowy programu Visual Studio również mogą być przywoływane przez *.runsettings* pliku. *.Runsettings* plik musi istnieć wpis jak w poniższym przykładzie:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Nieprawidłowy zakres po uaktualnieniu

**Dlaczego Live Unit Testing uwzględnia pokrycia nieprawidłowe po uaktualnieniu adaptera testowego, do którego odwołuje się Twoja projektów programu Visual Studio do obsługiwanej wersji?**

- Jeśli wiele projektów w odwołaniu do rozwiązania NuGet test pakietu karty, każde z nich musi zostać uaktualniony do obsługiwanej wersji.

- Upewnij się, że program MSBuild *.props* pliku zaimportowanego z pakiet adapter testowy jest poprawnie aktualizowany także. Sprawdź NuGet w wersji/ścieżki pakietu importu, który zazwyczaj znajduje się w górnej części pliku projektu, jak pokazano poniżej:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Dostosowywanie kompilacji

**Czy mogę dostosować Moje kompilacje Live Unit Testing?**

Jeśli rozwiązanie wymaga niestandardowych kroków, aby uruchomić Instrumentacji (Live Unit Testing), które nie są wymagane dla "regularne" nieinstrumentowanego kompilacji, a następnie można dodać kod do projektu lub *.targets* pliki, które sprawdza, czy dla `BuildingForLiveUnitTesting` właściwości i wykonuje kroki procesu kompilacji niestandardowej pre lub używanego po nim. Możesz również usunąć niektórych kroków kompilacji (takich jak publikowanie lub generowania pakietów) lub dodać kroki procesu kompilacji (takich jak kopiowanie wymagania wstępne) do Live Unit Testing kompilacji, na podstawie tej właściwości projektu. Dostosowywanie kompilacji na podstawie tej właściwości nie zmienia regularnych kompilacji w dowolny sposób i ma wpływ tylko na funkcję Live Unit Testing kompilacji.

Na przykład może być obiekt docelowy, który tworzy pakiety NuGet podczas regularnego kompilacji. Prawdopodobnie nie ma pakietów NuGet zostanie wygenerowany po każdej modyfikacji, wprowadzone. Dlatego można wyłączyć obiektu docelowego w kompilacji Live Unit Testing w sposób podobny do poniższego:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Komunikaty o błędach z &lt;OutputPath&gt; lub &lt;OutDir&gt;

**Dlaczego otrzymuję następujący błąd podczas Live Unit Testing próbuje utworzyć Moje rozwiązanie: ".. .pojawia bezwarunkowo ustawić `<OutputPath>` lub `<OutDir>`. Live Unit Testing nie będą wykonywane testy z zestawu danych wyjściowych"?**

Ten błąd może wystąpić, jeśli proces kompilacji dla rozwiązania bezwarunkowo zastępuje `<OutputPath>` lub `<OutDir>` tak, aby nie jest to podkatalog `<BaseOutputPath>`. W takich przypadkach Live Unit Testing nie będzie działać, ponieważ zastępuje ona również tych wartości, aby upewnić się, że artefakty kompilacji są porzucane dla folderu, w obszarze `<BaseOutputPath>`. Jeśli konieczne jest przesłonięcie lokalizację, w którym swoje artefakty kompilacji, można usunąć w regularnych kompilacji, Zastąp `<OutputPath>` warunkowe na podstawie `<BaseOutputPath>`.

Na przykład, jeśli kompilacja zastępuje `<OutputPath>` jak pokazano poniżej:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

następnie można zastąpić go następujący kod XML:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Gwarantuje to, że `<OutputPath>` znajduje się w obrębie `<BaseOutputPath>` folderu.

Nie zastępują `<OutDir>` bezpośrednio w procesie kompilacji; należy zastąpić `<OutputPath>` zamiast tego można usunąć artefaktów kompilacji do określonej lokalizacji.

## <a name="set-the-location-of-build-artifacts"></a>Ustaw lokalizację artefaktów kompilacji

**Chcę, aby artefakty kompilacji Live Unit Testing można przejść do określonej lokalizacji, zamiast domyślnej lokalizacji, w obszarze *.vs* folderu. Jak zmienić który?**

Ustaw `LiveUnitTesting_BuildRoot` zmiennej środowiskowej poziomu użytkownika do ścieżki, którego Live Unit Testing artefakty kompilacji do go porzucić. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>Test Explorer programu vs. Przebiegi testów Live Unit Testing

**Jak działa testów z okna Eksploratora testów różni się od uruchamiania testów w Live Unit Testing?**

Istnieje kilka różnic:

- Działania lub debugowania testów z **Eksplorator testów** okno uruchamia regularne plików binarnych, a Live Unit Testing są uruchamiane instrumentowanych danych binarnych. Jeśli chcesz debugować instrumentowanych danych binarnych, dodając [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) wywołania metody w metodzie testowej powoduje, że debuger do uruchomienia w każdym przypadku, gdy czy metoda jest wykonywana (w tym gdy jest ono wykonywane przez funkcję Live Unit Testing), a następnie Dołącz i debugowanie można przeprowadzać instrumentowanego pliku binarnego. Mamy nadzieję, że nasze jest jednak, że Instrumentacja jest niewidoczne dla większości scenariuszy użytkowników i potrzebujesz do debugowania Instrumentacji danych binarnych.

- Live Unit Testing nie powoduje utworzenia nowej domeny aplikacji, aby uruchomić testy, ale testy uruchamiane z **Eksplorator testów** okna Tworzenie nowej domeny aplikacji.

- Live Unit Testing uruchamia testy w każdym zestawie testów sekwencyjnie, dlatego jeśli używasz wielu testów z **Eksploratora testów** okna i wybrano **Uruchom testy równolegle** przycisku będą odtwarzane równoległe.

- Odkrywania i wykonywania testów w Live Unit Testing korzysta z wersji 2 `TestPlatform`, podczas gdy **Eksplorator testów** okno używa wersji 1. Mimo że nie będą zauważyć różnicę w większości przypadków.

- **Eksplorator testów** obecnie domyślnie uruchamia testy w jednowątkowym (przedziale STA), natomiast Live Unit Testing uruchamia testy w wielowątkowych apartamentu (MTA). Do uruchomienia testów MSTest w STA w Live Unit Testing, dekoracji metody testowej lub klasa zawierająca z `<STATestMethod>` lub `<STATestClass>` atrybut, który można znaleźć w `MSTest.STAExtensions 1.0.3-beta` pakietu NuGet. Dla NUnit dekoracji metody testowej z `<RequiresThread(ApartmentState.STA)>` atrybutu i struktury xUnit, za pomocą `<STAFact>` atrybutu.

## <a name="exclude-tests"></a>Wyklucz testów

**Jak wyłączyć testy z uczestnictwa w Live Unit Testing?**

Zobacz sekcję "Dołączanie i wykluczanie projekty testowe i metod testowych" [Użyj Live Unit Testing w programie Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) artykuł, aby ustawienia specyficzne dla użytkownika. Uwzględniając lub wykluczając testów jest przydatne, gdy chcesz uruchomić określonego zestawu testów dla sesji edytowania określonego lub utrwalić osobistych preferencji.

W przypadku ustawienia specyficzne dla rozwiązania, można zastosować <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> atrybut programowo, aby wykluczyć metody, właściwości, klasy lub struktury z są instrumentowane przez funkcję Live Unit Testing. Ponadto można również ustawić `<ExcludeFromCodeCoverage>` właściwości `true` w pliku projektu, aby wykluczyć całego projektu z są instrumentowane. Live Unit Testing nadal odpowiedzialnej za przeprowadzanie testów, które nie zostały zinstrumentowane, ale ich zakres nie będzie wizualizowane.

Możesz również sprawdzić czy `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` jest ładowany w bieżącej domenie aplikacji i Wyłącz testy, w oparciu o tym, dlaczego. Na przykład zrobić coś podobnego do następujących w narzędziu xUnit:

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

## <a name="win32-pe-headers"></a>Nagłówki środowiska Preinstalacyjnego systemu Win32

**Nagłówki Win32 PE są inne w przypadku zestawów instrumentowanych utworzonych przez testy jednostkowe na żywo**

Ten problem zostanie rozwiązany i nie istnieje w Visual Studio 2017 w wersji 15.3 lub nowszej.

Dla starszych wersji programu Visual Studio 2017 ma to znana usterka, które mogą skutkować Live Unit Testing kompilacje awarie, aby osadzić następujące dane nagłówek PE Win32:

- Wersja pliku (określona przez @System.Reflection.AssemblyFileVersionAttribute w kodzie).

- Ikona Win32 (określony przez `/win32icon:` w wierszu polecenia).

- Win32 Manifest (określony przez `/win32manifest:` w wierszu polecenia).

Testy, które zależą od tych wartości może zakończyć się niepowodzeniem, gdy wykonana przez testy jednostkowe na żywo.

## <a name="continuous-builds"></a>Kompilacje ciągłe

**Dlaczego testowania Zachowaj tworzenia Moje rozwiązanie przez cały czas, nawet wtedy, gdy nie powoduję, że wszelkie zmiany jednostek na żywo?**

Można tworzyć rozwiązania, nawet wtedy, gdy nie jest wprowadzanie zmian, jeśli proces kompilacji rozwiązania generuje kod źródłowy, który jest częścią samego rozwiązania, a pliki docelowe kompilacji ma odpowiednie wejściami i wyjściami, określony. Obiekty docelowe powinien być podawany listy danych wejściowych i wyjściowych, aby program MSBuild mógł kontrole odpowiedniej aktualności i ustalić, czy wymagana jest nowa kompilacja.

Live Unit Testing uruchamia kompilację, gdy wykryje, że zostały zmienione pliki źródłowe. Ponieważ kompilacji rozwiązania generuje pliki źródłowe, Live Unit Testing zostanie wyświetlony w pętli nieskończonej kompilacji. Jeśli jednak dane wejściowe i wyjściowe, obiektu docelowego są zaznaczone rozpoczęciu Live Unit Testing drugą kompilację (po wykryciu nowo wygenerowanych plików źródłowych z poprzedniej kompilacji), spowoduje przerwanie dostęp do najaktualniejszych kompilacji, ponieważ będzie sprawdza dane wejściowe i wyjściowe Wskazuje, że wszystko jest aktualne.  

## <a name="new-process-coverage"></a>Nowy proces pokrycia

**Dlaczego nie Live Unit Testing przechwytuje pokrycie z nowego procesu utworzone za pomocą testu?**

Jest to znany problem i powinny być ustalone w późniejszych wersji.

## <a name="including-or-excluding-tests-doesnt-work"></a>Uwzględniając lub wykluczając testów nie działa

**Dlaczego nic nie odbywa się po I dołączania lub wykluczania testów z zestawu testów na żywo?**

Ten problem zostanie rozwiązany i nie istnieje w Visual Studio 2017 w wersji 15.3 lub nowszej.

W starszych wersjach programu Visual Studio 2017 jest to znany problem. Aby obejść ten problem, należy wprowadzić zmiany do każdego pliku, po mają być dołączone lub wykluczone testów.

## <a name="editor-icons"></a>Edytor ikon

**Dlaczego nie widzę żadnych ikon w edytorze, mimo że Live Unit Testing wydaje się działać testu, w zależności od komunikaty w oknie danych wyjściowych?**

Ikony w edytorze mogą być niewidoczne, jeśli nie są zestawy, które Live Unit Testing działa na dowolnej przyczyny. Na przykład Live Unit Testing nie jest zgodne z projektami, które ustawił `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. W takim przypadku Twój proces kompilacji musi zostać zaktualizowany, albo usuń to ustawienie lub zmień ją na `true` dla Live Unit Testing do pracy. 

## <a name="capture-logs"></a>Przechwytywanie dzienników

**Jak zbierania bardziej szczegółowych dzienników do pliku raportów usterek?**

Możesz wykonać kilka czynności w celu zbierania bardziej szczegółowych dzienników:

- Przejdź do **narzędzia** > **opcje** > **Live Unit Testing** i zmień opcję rejestrowania **pełne**. Pełne rejestrowanie powoduje, że bardziej szczegółowych dzienników, które mają być wyświetlane w **dane wyjściowe** okna.

- Ustaw `LiveUnitTesting_BuildLog` zmienną środowiskową na nazwę pliku, którego chcesz użyć do przechwycenia dziennika MSBuild. Następnie można pobrać szczegółowe komunikaty dziennika MSBuild z Live Unit Testing kompilacji z tego pliku.

- Ustaw `LiveUnitTesting_TestPlatformLog` użytkownika zmienną środowiskową, aby `1` do przechwycenia dziennika platformy testowej. Następnie można pobrać szczegółowe komunikaty dziennika platformy testowej z Live Unit Testing działa z `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Utwórz zmienną środowiska na poziomie użytkownika o nazwie `VS_UTE_DIAGNOSTICS` i ustaw ją na wartość 1 (lub dowolna wartość) i uruchom ponownie program Visual Studio. Powinien zostać wyświetlony mnóstwo zalogowaniu **dane wyjściowe — testy** kartę w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Testy jednostkowe na żywo](live-unit-testing.md)
