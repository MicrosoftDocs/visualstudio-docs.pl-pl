---
title: Dostosowywanie analizy pokrycia kodu
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bce7a6b9369f33e6fa5248821f58d9903172415c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918648"
---
# <a name="customize-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu

Domyślnie pokrycie kodu analizuje wszystkie zestawy rozwiązań, które są ładowane podczas testów jednostkowych. Zaleca się użycie tego domyślnego zachowania, ponieważ działa dobrze przez większość czasu. Aby uzyskać więcej informacji, zobacz [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Aby wykluczyć kod testowy z wyników pokrycia kodu <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> i uwzględnić tylko kod aplikacji, dodaj atrybut do klasy testowej.

Aby uwzględnić zestawy, które nie są częścią rozwiązania, należy uzyskać pliki *pdb* dla tych zestawów i skopiować je do tego samego folderu co pliki *.dll* zestawu.

## <a name="run-settings-file"></a>Uruchom plik ustawień

[Plik ustawień uruchamiania](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) jest plikiem konfiguracyjnym używanym przez narzędzia do testowania jednostek. Zaawansowane ustawienia pokrycia kodu są określone w pliku *runsettings.*

Aby dostosować pokrycie kodu, wykonaj następujące kroki:

1. Dodaj plik ustawień uruchamiania do rozwiązania. W **Eksploratorze rozwiązań**w menu skrótów rozwiązania wybierz polecenie **Dodaj** > **nowy element**i wybierz pozycję Plik **XML**. Zapisz plik o nazwie, takiej jak *CodeCoverage.runsettings*.

2. Dodaj zawartość z przykładowego pliku na końcu tego artykułu, a następnie dostosuj ją do swoich potrzeb, zgodnie z opisem w poniższych sekcjach.

::: moniker range="vs-2017"

3. Aby wybrać plik ustawień uruchamiania, w menu **Test** wybierz polecenie **Sprawdź ustawienia** > testu**Wybierz plik ustawień testu**. Aby określić plik ustawień uruchamiania do uruchamiania testów z wiersza polecenia, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby wybrać plik ustawień uruchamiania, w menu **Test** wybierz polecenie **Wybierz plik ustawień**. Aby określić plik ustawień uruchamiania do uruchamiania testów z wiersza polecenia, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

   Po **wybraniu opcji Analizuj pokrycie kodu**informacje o konfiguracji są odczytywane z pliku ustawień uruchamiania.

   > [!TIP]
   > Wszelkie poprzednie wyniki pokrycia kodu i kolorowanie kodu nie są automatycznie ukrywane po uruchomieniu testów lub aktualizacji kodu.

::: moniker range="vs-2017"

Aby wyłączyć i włączyć ustawienia niestandardowe, usuń zaznaczenie lub zaznacz plik w menu **Ustawienia** > **testu.**

![Menu ustawień testowania z plikiem ustawień niestandardowych w programie Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Aby wyłączyć i włączyć ustawienia niestandardowe, usuń zaznaczenie lub zaznacz plik w menu **Test.**

::: moniker-end

## <a name="symbol-search-paths"></a>Ścieżki wyszukiwania symboli

Pokrycie kodu wymaga plików symboli (pliki*pdb)* dla zestawów. W przypadku zestawów utworzonych przez rozwiązanie pliki symboli są zwykle obecne obok plików binarnych, a pokrycie kodu działa automatycznie. W niektórych przypadkach można dołączyć zestawy odniesienia w analizie pokrycia kodu. W takich przypadkach pliki *.pdb* mogą nie przylegać do plików binarnych, ale można określić ścieżkę wyszukiwania symboli w pliku *runsettings.*

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Rozpoznawanie symboli może zająć trochę czasu, szczególnie w przypadku korzystania ze zdalnej lokalizacji pliku z wieloma zestawami. W związku z tym należy rozważyć skopiowanie plików *pdb* do tej samej lokalizacji lokalnej co pliki binarne (*.dll* i *.exe).*

## <a name="include-or-exclude-assemblies-and-members"></a>Uwzględnianie lub wykluczanie zestawów i elementów członkowskich

Można dołączyć lub wykluczyć zestawy lub określone typy i elementy członkowskie z analizy pokrycia kodu. Jeśli sekcja **Dołącz** jest pusta lub pominięta, uwzględniane są wszystkie zestawy, które są ładowane i mają skojarzone pliki PDB. Jeśli zestaw lub element członkowski pasuje do klauzuli w sekcji **Wyklucz,** jest on wykluczony z zakresu kodu. **Sekcja Wyklucz** ma pierwszeństwo przed sekcją **Dołącz:** jeśli zestaw znajduje się na liście **Uwzględnij** i **Wyklucz,** nie zostanie uwzględniony w pokryciu kodu.

Na przykład następujący kod XML wyklucza pojedynczy zestaw, określając jego nazwę:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Poniższy przykład określa, że tylko jeden zestaw powinien być uwzględniony w pokryciu kodu:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

W poniższej tabeli przedstawiono różne sposoby, że zestawy i elementy członkowskie mogą być dopasowane do włączenia lub wykluczenia z zakresu kodu.

| Element XML | Co pasuje |
| - | - |
| Ścieżka modułu | Dopasowuje zestawy określone przez nazwę zestawu lub ścieżkę pliku. |
| CompanyName | Dopasowuje zestawy według atrybutu **Firma.** |
| Publickeytoken | Pasuje do podpisanych zestawów przez token klucza publicznego. |
| Element źródłowy | Dopasowuje elementy według nazwy ścieżki pliku źródłowego, w którym są zdefiniowane. |
| Atrybut | Dopasowuje elementy, które mają określony atrybut. Określ pełną nazwę atrybutu, `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`na przykład .<br/><br/>Jeśli zostanie <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> wykluczony atrybut, kod, który używa `async` `await`funkcji `yield return`języka, takich jak , i automatycznie zaimplementowane właściwości jest wykluczony z analizy pokrycia kodu. Aby wykluczyć prawdziwie wygenerowany <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> kod, należy wykluczyć tylko ten atrybut. |
| Funkcja | Dopasowuje procedury, funkcje lub metody według w pełni kwalifikowanej nazwy, w tym listy parametrów. Część nazwy można również dopasować za pomocą [wyrażenia regularnego](#regular-expressions).<br/><br/>Przykłady:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);`(C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)`(C++) |

### <a name="regular-expressions"></a>Wyrażenia regularne

Uwzględnij i wyklucz węzły używają wyrażeń regularnych, które nie są takie same jak symbole wieloznaczne. We wszystkich dopasowaniach rozróżniana jest wielkość liter. Przykłady to:

- **. \* ** dopasowuje ciąg dowolnych znaków

- **\\.** dopasowuje kropkę "."

- ( ) pasuje do nawiasów "( )" ** \\ \\**

- **\\\\**dopasowuje ogranicznik\\ścieżki pliku " "

- **^** dopasowuje początek ciągu

- **$** dopasowuje koniec ciągu

Poniższy kod XML pokazuje, jak dołączać i wykluczać określone zestawy przy użyciu wyrażeń regularnych:

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

Poniższy kod XML pokazuje, jak włączać i wykluczać określone funkcje przy użyciu wyrażeń regularnych:

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

> [!WARNING]
> Jeśli występuje błąd w wyrażeniu regularnym, takich jak nawiasy bez zmiany lub niedopasowane, analiza pokrycia kodu nie zostanie uruchomiony.

Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Przykładowy plik .runsettings

Skopiuj ten kod i edytuj go zgodnie z potrzebami.

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
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
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

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie testów jednostkowych przy użyciu pliku ustawień uruchamiania](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
