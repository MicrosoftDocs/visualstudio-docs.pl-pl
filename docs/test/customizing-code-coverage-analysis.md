---
title: Dostosowywanie analizy pokrycia kodu
description: Dowiedz się, jak używać atrybutu ExcludeFromCodeCoverageAttribute do wykluczenia kodu testowego z wyników pokrycia. Można dołączać zestawy poza rozwiązaniem.
ms.custom: SEO-VS-2020
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65044baf78e6f49e35f011a4853111063e82a192
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964410"
---
# <a name="customize-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu

Domyślnie pokrycie kodu analizuje wszystkie zestawy rozwiązań, które są ładowane podczas testów jednostkowych. Zalecamy korzystanie z tego zachowania domyślnego, ponieważ w większości przypadków działa ono dobrze. Aby uzyskać więcej informacji, zobacz [Korzystanie z pokrycia kodu w celu określenia, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Aby wykluczyć Kod testowy z wyników pokrycia kodu i zawierać tylko kod aplikacji, Dodaj <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atrybut do klasy testowej.

Aby dołączyć zestawy, które nie są częścią rozwiązania, należy uzyskać pliki *. pdb* dla tych zestawów i skopiować je do tego samego folderu, w którym znajdują się pliki Assembly *. dll* .

## <a name="run-settings-file"></a>Plik parametrów uruchomieniowych

[Plik parametrów uruchomieniowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) jest plikiem konfiguracji używanym przez narzędzia testowania jednostkowego. Zaawansowane ustawienia pokrycia kodu są określone w pliku *. runsettings* .

Aby dostosować pokrycie kodu, wykonaj następujące kroki:

1. Dodaj plik parametrów uruchomieniowych do rozwiązania. W **Eksplorator rozwiązań** w menu skrótów rozwiązania wybierz pozycję **Dodaj**  >  **nowy element** i wybierz pozycję **plik XML**. Zapisz plik z nazwą, taką jak *codecoverage. runsettings*.

2. Dodaj zawartość z przykładowego pliku na końcu tego artykułu, a następnie dostosuj ją do swoich potrzeb zgodnie z opisem w poniższych sekcjach.

::: moniker range="vs-2017"

3. Aby wybrać plik parametrów uruchomieniowych, w menu **test** wybierz polecenie **Ustawienia testu**  >  **Wybierz plik ustawień testu**. Aby określić plik parametrów uruchomieniowych do uruchamiania testów z wiersza polecenia, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Aby wybrać plik parametrów uruchomieniowych, w menu **test** wybierz polecenie **Wybierz plik ustawień**. Aby określić plik parametrów uruchomieniowych do uruchamiania testów z wiersza polecenia, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

   Po wybraniu opcji **Analizuj pokrycie kodu** informacje o konfiguracji są odczytywane z pliku parametrów uruchomieniowych.

   > [!TIP]
   > Wszystkie poprzednie wyniki pokrycia kodu i kolorowanie kodu nie są automatycznie ukrywane podczas uruchamiania testów lub aktualizowania kodu.

::: moniker range="vs-2017"

Aby wyłączyć ustawienia niestandardowe i włączać, usuń zaznaczenie lub wybierz plik w  > menu **Ustawienia testu** testowego.

![Menu ustawień testu z niestandardowym plikiem ustawień w programie Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Aby wyłączyć ustawienia niestandardowe i włączać, usuń zaznaczenie lub wybierz plik w menu **test** .

::: moniker-end

## <a name="symbol-search-paths"></a>Ścieżki wyszukiwania symboli

Pokrycie kodu wymaga plików symboli (plików *. pdb* ) dla zestawów. W przypadku zestawów skompilowanych w ramach rozwiązania pliki symboli są zwykle obecne obok plików binarnych, a pokrycie kodu działa automatycznie. W niektórych przypadkach może zajść potrzeba dołączenia przywoływanych zestawów do analizy pokrycia kodu. W takich przypadkach pliki *. pdb* mogą nie przylegać do plików binarnych, ale można określić ścieżkę wyszukiwania symboli w pliku *runsettings* .

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Rozpoznawanie symboli może zająć dużo czasu, szczególnie w przypadku używania zdalnej lokalizacji pliku z wieloma zestawami. W związku z tym należy rozważyć kopiowanie plików *. pdb* do tej samej lokalizacji lokalnej, co pliki binarne (*. dll* i *. exe*).

## <a name="include-or-exclude-assemblies-and-members"></a>Dołącz lub Wyklucz zestawy i członków

Można dołączać lub wykluczać zestawy lub określone typy oraz członków z analizy pokrycia kodu. Jeśli sekcja **include** jest pusta lub pominięta, zostaną uwzględnione wszystkie zestawy, które są załadowane i skojarzono SKOJARZONE pliki PDB. Jeśli zestaw lub element członkowski jest zgodny z klauzulą w sekcji **exclude** , jest on wykluczony z pokrycia kodu. Sekcja **exclude** ma pierwszeństwo przed sekcją **include** : Jeśli zestaw znajduje się na liście **include** i **exclude**, nie zostanie uwzględniony w pokryciu kodu.

Na przykład poniższy kod XML wyklucza pojedynczy zestaw, określając jego nazwę:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

W poniższym przykładzie określono, że tylko jeden zestaw powinien być uwzględniony w pokryciu kodu:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

W poniższej tabeli przedstawiono różne sposoby dopasowywania zestawów i członków do dołączenia lub wykluczania z pokrycia kodu.

| Element XML | Co pasuje |
| - | - |
| ModulePath | Dopasowuje zestawy określone przez nazwę zestawu lub ścieżkę pliku. |
| CompanyName | Dopasowuje zestawy według atrybutu **firmy** . |
| PublicKeyToken | Dopasowuje podpisane zestawy przez token klucza publicznego. |
| Element źródłowy | Dopasowuje elementy według nazwy ścieżki pliku źródłowego, w którym są zdefiniowane. |
| Atrybut | Dopasowuje elementy, które mają określony atrybut. Określ pełną nazwę atrybutu, na przykład `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>` .<br/><br/>Jeśli wykluczasz <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> atrybut, kod, który używa funkcji języka, takich jak `async` ,, `await` `yield return` , i zaimplementowane właściwości, jest wykluczony z analizy pokrycia kodu. Aby wykluczyć faktycznie wygenerowany kod, należy wykluczyć tylko <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atrybut. |
| Funkcja | Dopasowuje procedury, funkcje lub metody przez w pełni kwalifikowaną nazwę, łącznie z listą parametrów. Możesz również dopasować część nazwy przy użyciu [wyrażenia regularnego](#regular-expressions).<br/><br/>Przykłady:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` Znajd<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` Języków |

### <a name="regular-expressions"></a>Wyrażenia regularne

Węzły include i Exclude używają wyrażeń regularnych, które nie są takie same jak symbole wieloznaczne. We wszystkich dopasowaniach rozróżniana jest wielkość liter. Przykłady to:

- **.\*** dopasowuje ciąg znaków

- **\\.** dopasowuje kropkę "."

- **\\ ( \\ )** dopasowuje nawiasy "()"

- **\\\\** dopasowuje ogranicznik ścieżki pliku " \\ "

- **^** dopasowuje początek ciągu

- **$** dopasowuje koniec ciągu

Poniższy kod XML przedstawia sposób dołączania i wykluczania określonych zestawów przy użyciu wyrażeń regularnych:

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

Poniższy kod XML przedstawia sposób dołączania i wykluczania określonych funkcji przy użyciu wyrażeń regularnych:

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
> Jeśli wystąpi błąd w wyrażeniu regularnym, na przykład w niezmienionym lub niezgodnym nawiasie, Analiza pokrycia kodu nie zostanie uruchomiona.

Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Przykładowy plik .runsettings

Skopiuj ten kod i zmodyfikuj go zgodnie z potrzebami.

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

- [Konfigurowanie testów jednostkowych przy użyciu pliku parametrów uruchomieniowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Użyj pokrycia kodu, aby określić, ile kodu jest testowany](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
