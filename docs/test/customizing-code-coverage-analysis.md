---
title: Dostosowywanie analizy pokrycia kodu
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8749cd7757796a1b716b1ac9db086d3155f94694
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952492"
---
# <a name="customize-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu

Domyślnie pokrycie kodu analizuje wszystkie zestawy rozwiązań, które są ładowane podczas testów jednostkowych. Zalecamy użycie to zachowanie domyślne, ponieważ działa ona poprawnie przez większość czasu. Aby uzyskać więcej informacji, zobacz [użycie pokrycia kodu, aby ustalić, ile kodu jest testowana](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Aby wykluczyć kodu testowego z wyników pokrycia kodu i zawierać tylko kod aplikacji, Dodaj <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybutów do klasy testowej.

Aby umieścić zestawy, które nie należą do rozwiązania, uzyskać *.pdb* plików dla tych zestawów i skopiuj je do folderu, który zestaw *.dll* plików.

## <a name="run-settings-file"></a>Plik parametrów uruchomieniowych

[Plik parametrów uruchomieniowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) jest to plik konfiguracji używany przez narzędzia do testowania jednostki. Zaawansowane ustawienia pokrycia kodu są określone w *.runsettings* pliku.

Aby dostosować pokrycie kodu, wykonaj następujące kroki:

1. Dodaj plik parametrów uruchomieniowych do rozwiązania. W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj** > **nowy element**i wybierz **pliku XML**. Zapisz plik pod nazwą takich jak *CodeCoverage.runsettings*.

1. Dodaj zawartość z przykładowy plik na końcu tego artykułu, a następnie dostosować ją do swoich potrzeb zgodnie z opisem w kolejnych sekcjach.

1. Wybierz plik parametrów uruchomieniowych na **testu** menu, wybierz **ustawienia testu** > **zaznacz plik ustawień testu**. Aby określić plik parametrów uruchomieniowych do uruchamiania testów z wiersza polecenia lub w przepływie pracy kompilacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu *.runsettings* pliku](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Po wybraniu **Analizuj pokrycie kodu**, informacje o konfiguracji są odczytywane z pliku parametrów uruchomieniowych.

   > [!TIP]
   > Poprzednie wyniki pokrycia kodu i kolorowanie kodu nie są automatycznie ukrywane podczas uruchamiania testów czy aktualizowania kodu.

Aby włączyć ustawienia niestandardowe i wyłączonym, usuń zaznaczenie lub zaznacz plik w **testu** > **ustawienia testu** menu.

![Menu Ustawienia testu przy użyciu pliku ustawień niestandardowych](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Określ ścieżki wyszukiwania symboli

Pokrycie kodu wymaga plików symboli (*.pdb* plików) dla zestawów. Dla zestawów zbudowanych według rozwiązania pliki symboli są zwykle obecne obok plików binarnych, a pokrycie kodu działa automatycznie. Jednak w niektórych przypadkach można chcieć dołączyć odwołania do zestawów do analizy pokrycia kodu. W takich przypadkach *.pdb* plików mogą nie być w przylegającymi do plików binarnych ale można określić ścieżkę wyszukiwania symbolu w *.runsettings* pliku.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Rozpoznawanie symboli może potrwać, szczególnie przy używaniu zdalnej lokalizacji pliku za pomocą wielu zestawów. W związku z tym, należy wziąć pod uwagę kopiowanie *.pdb* pliki do tej samej lokalizacji lokalnej co plik binarny (*.dll* i *.exe*) plików.

### <a name="exclude-and-include"></a>Dołączanie i wykluczanie

Określone zestawy można wykluczyć z analizy pokrycia kodu. Na przykład:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Alternatywnie można określić zestawy, które powinny być włączone. Takie podejście ma tę wadę, że po dodaniu większej liczby zestawów do rozwiązania trzeba pamiętać, aby dodać je do listy:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Jeśli **Include** jest pusta, wówczas przetwarzanie pokrycia kodu obejmuje wszystkie zestawy, które są ładowane i dla których *.pdb* znajdują się pliki. Pokrycie kodu nie ma elementów, które odpowiadają klauzuli na liście **wykluczyć** listy.

**Obejmują** jest przetwarzana przed **wykluczyć**.

### <a name="regular-expressions"></a>Wyrażenia regularne

Uwzględnij lub wyklucz węzły, używając wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Wyrażenia regularne nie są takie same jak symbole wieloznaczne. W szczególności:

- **. \\** * odpowiada ciągowi dowolnych znaków

- **\\.** odpowiada kropce ".")

- **\\( \\)** odpowiada nawiasom ""

- **\\\\** odpowiada ścieżce pliku ogranicznika "\\"

- **^** odpowiada początkowi ciągu

- **$** Dopasowuje koniec ciągu

We wszystkich dopasowaniach rozróżniana jest wielkość liter.

Na przykład:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Jeśli występuje błąd w wyrażeniu regularnym, takich jak o niezmienionym znaczeniu lub niedopasowane nawiasy, analiza pokrycia kodu nie działa.

### <a name="other-ways-to-include-or-exclude-elements"></a>Inne sposoby, aby dołączyć lub wykluczyć elementy

- **ModulePath** — dopasowuje zestawy określone przez ścieżkę pliku zestawu.

- **Nazwa firmy** — dopasowanie zestawów przez **firmy** atrybutu.

- **PublicKeyToken** — dopasowuje zestawy podpisane przez token klucza publicznego.

- **Źródło** — dopasowuje elementy według nazwy ścieżki pliku źródłowego, w której są zdefiniowane.

- **Atrybut** — dopasowuje elementy, do których dołączono określony atrybut. Podaj pełną nazwę atrybutu, a zawierają "Atrybutu" na końcu nazwy.

- **Funkcja** — dopasowuje procedury, funkcji lub metody w pełni kwalifikowanej nazwy. Aby dopasować nazwę funkcji, wyrażenie regularne musi odpowiadać w pełni kwalifikowanej nazwy funkcji, łącznie z przestrzeni nazw, nazwa klasy, nazwy metody i listą parametrów. Na przykład:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>Przykładowy plik .runsettings

Skopiuj ten kod i dostosuj go do własnych potrzeb.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie testów jednostkowych przy użyciu pliku parametrów uruchomieniowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Użycie pokrycia kodu, aby ustalić, ile kodu jest testowana.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)