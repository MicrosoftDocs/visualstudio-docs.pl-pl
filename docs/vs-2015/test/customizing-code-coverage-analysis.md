---
title: Dostosowywanie analizy pokrycia kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f6337c35-acae-4c5f-b5d9-ac5ff687ef18
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ef0a8d1867114cd655f1e361cf0401dab6bce1a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416644"
---
# <a name="customizing-code-coverage-analysis"></a>Dostosowywanie analizy pokrycia kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie narzędzie Visual Studio Code Coverage analizuje wszystkie zestawy rozwiązań (.exe/.dll), które są ładowane podczas testów jednostkowych. Zaleca się zachować to ustawienie domyślne, ponieważ w większości przypadków działa ono prawidłowo. Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu, aby określić, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Przed rozpoczęciem dostosowywania zachowania pokrycia kodu należy wziąć pod uwagę kilka alternatyw:  
  
- *Chcę Dołączanie i wykluczanie kod testu z wyników pokrycia kodu tylko kod aplikacji.*  
  
   Dodaj `ExcludeFromCodeCoverage Attribute` do klasy testowej.  
  
- *Chcę dołączyć zestawów, które nie są częścią Moje rozwiązanie.*  
  
   Uzyskaj pliki .pdb dla tych zestawów i skopiuj je do tego samego folderu, co pliki .dll zestawu.  
  
  Aby dostosować zachowanie pokrycia kodu, skopiuj [próbki na końcu tego tematu](#sample) i dodaj go do rozwiązania przy użyciu rozszerzenia pliku .runsettings. Edytuj go zgodnie z własnymi potrzebami, a następnie na **testu** menu, wybierz **ustawienia testu**, **wybierz ustawienia testu** pliku. W pozostałej części tego tematu opisano tę procedurę bardziej szczegółowo.  
  
## <a name="the-runsettings-file"></a>Plik .runsettings  
 Zaawansowane ustawienia pokrycia kodu są określone w pliku .runsettings. Jest to plik konfiguracji używany przez narzędzia do testowania jednostkowego. Zalecamy skopiowanie [próbki na końcu tego tematu](#sample) i dostosuj go do swoich potrzeb.  
  
- *Co się stało z plikiem .testsettings, używane w programie Visual Studio 2010?*  
  
   W programie Visual Studio 2010 plik .testsettings stosuje się jedynie do testów jednostkowych opartych na środowisku MSTest. Narzędzia do testowania w programie Visual Studio 2012 stosuje się nie tylko do środowiska MSTest, ale także do innych środowisk, takich jak NUnit i xUnit.net. Plik .testsettings nie będzie z nimi działać. Plik .runsettings ma na celu dostosowanie narzędzi testowych w sposób, który działa w przypadku wszystkich środowisk testowania.  
  
  Aby dostosować pokrycie kodu, należy dodać plik .runsettings do rozwiązania:  
  
1. Dodaj plik XML jako element rozwiązania z rozszerzeniem `.runsettings`:  
  
    W Eksploratorze rozwiązań w menu skrótów danego rozwiązania, wybierz **Dodaj**, **nowy element**i wybierz **pliku XML**. Zapisz plik pod nazwą kończącą `CodeCoverage.runsettings`  
  
2. Dodaj zawartość podaną w próbie na końcu tego tematu, a następnie dostosuj go do własnych potrzeb zgodnie z opisem w poniższych sekcjach.  
  
3. Na **testu** menu, wybierz **ustawienia testu**, **zaznacz plik ustawień testu** i wybierz plik.  
  
4. Teraz po uruchomieniu **Analizuj pokrycie kodu**ten `.runsettings` plików będzie kontrolować jego zachowanie. Nie zapomnij, że należy ponownie uruchomić pokrycie kodu: Twoje poprzednie wyniki pokrycia i kolorowanie kodu nie są automatycznie ukrywane podczas uruchamiania testów czy aktualizowania kodu.  
  
5. Aby włączyć ustawienia niestandardowe i wyłączonym, usuń zaznaczenie lub zaznacz plik w **testu**, **ustawienia testu** menu.  
  
   ![Menu Ustawienia testu przy użyciu pliku ustawień niestandardowych](../test/media/codecoverage-settingsfile.png "Plik_ustawień CodeCoverage")  
  
   Inne aspekty testów jednostkowych można skonfigurować w tym samym pliku .runsettings. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).  
  
### <a name="specifying-symbol-search-paths"></a>Określanie ścieżek wyszukiwania symbolu  
 Pokrycie kodu wymaga symboli (pliki .pdb), aby były obecne zestawy. Dla zestawów zbudowanych według rozwiązania pliki symboli są zwykle obecne obok plików binarnych, a pokrycie kodu działa automatycznie. Jednak w niektórych przypadkach można chcieć dołączyć odwołania do zestawów do analizy pokrycia kodu. W takich przypadkach pliki .pdb mogą nie być przylegającymi do plików binarnych, ale ścieżkę wyszukiwania symbolu można określić w pliku .runsettings.  
  
```xml  
<SymbolSearchPaths>                
      <Path>\\mybuildshare\builds\ProjectX</Path>  
      <!--More paths if required-->  
</SymbolSearchPaths>  
  
```  
  
> [!WARNING]
> Rozpoznawanie symboli może potrwać, szczególnie przy używaniu zdalnej lokalizacji pliku z wieloma zestawami. W związku z tym należy wziąć pod uwagę kopiowanie zdalnych plików .pdb do tej samej lokalizacji lokalnej co pliki binarne (.dll i .exe).  
  
### <a name="excluding-and-including"></a>Uwzględnianie i wykluczanie  
 Określone zestawy można wykluczyć z analizy pokrycia kodu. Na przykład:  
  
```minterastlib  
<ModulePaths>  
  <Exclude>  
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Exclude>  
</ModulePaths>  
```  
  
 Alternatywnie można określić zestawy, które powinny być włączone. Takie podejście ma tę wadę, że po dodaniu większej liczby zestawów do rozwiązania trzeba pamiętać, aby dodać je do listy:  
  
```minterastlib  
<ModulePaths>  
  <Include>  
   <ModulePath>Fabrikam.Math.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Include>  
</ModulePaths>  
```  
  
 Jeśli `<Include>` jest pusta, wówczas przetwarzanie pokrycia kodu obejmuje wszystkie zespoły (pliki .dll i .exe), które są ładowane i dla których **.pdb** można znaleźć pliki, z wyjątkiem elementów, które odpowiadają klauzuli na liście `<Exclude>` listy.  
  
 `Include` jest przetwarzana przed `Exclude`.  
  
### <a name="regular-expressions"></a>Wyrażenia regularne  
 Uwzględnij lub wyklucz węzły, używając wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Wyrażenia regularne nie są tym samym, co symbole wieloznaczne. W szczególności:  
  
1. **\.\\*** odpowiada ciągowi dowolnych znaków  
  
2. **\\.** odpowiada kropce ".")  
  
3. **\\( \\)** odpowiada nawiasom ""  
  
4. **\\\\** odpowiada ścieżce pliku ogranicznika "\\"  
  
5. **^** odpowiada początkowi ciągu  
  
6. **$** Dopasowuje koniec ciągu  
  
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
> Jeśli występuje błąd w wyrażeniu regularnym, taki jak nawiasy niedopasowane lub o niezmienionym znaczeniu, analiza pokrycia kodu nie będzie działać.  
  
### <a name="other-ways-to-include-or-exclude-elements"></a>Inne sposoby, aby dołączyć lub wykluczyć elementy  
 Zobacz [próbki na końcu tego tematu](#sample) przykłady.  
  
- `ModulePath` — Zestawy określone przez ścieżkę pliku zestawu.  
  
- `CompanyName` — dopasowanie zestawów przez atrybut firmy.  
  
- `PublicKeyToken` — Dopasowuje zestawy podpisane przez token klucza publicznego. Na przykład dopasować wszystkie składniki programu Visual Studio i rozszerzenia, użyj `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.  
  
- `Source` — Dopasowuje elementy według nazwy ścieżki pliku źródłowego, w której są zdefiniowane.  
  
- `Attribute` — Dopasowuje elementy, do których dołączono określony atrybut. Podaj pełną nazwę atrybutu, łącznie z wyrazem „Atrybut” na końcu nazwy.  
  
- `Function` — Dopasowuje procedury, funkcji lub metody w pełni kwalifikowanej nazwy.  
  
  **Pasujące nazwy funkcji**  
  
  Dane wyrażenie regularne musi odpowiadać w pełni kwalifikowanej nazwie funkcji, łącznie z przestrzenią nazw, nazwą klasy, nazwą metody i listą parametrów. Na przykład  
  
- C# lub Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`  
  
- C++:  `Fabrikam::Math::LocalMath::SquareRoot(double)`  
  
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
  
## <a name="how-to-specify-runsettings-files-while-running-tests"></a>Jak określić pliki .runsettings podczas wykonywania testów  
  
### <a name="to-customize-runsettings-in-visual-studio-tests"></a>Aby dostosować ustawienia uruchamiania w testach programu Visual Studio  
 Wybierz **testu**, **ustawienia testu**, **zaznacz plik ustawień testu** i zaznacz plik .runsettings. Plik pojawi się w menu Ustawienia testu, gdzie można zaznaczyć go lub usunąć. Zaznaczona, plik .runsettings ma zastosowanie przy każdym użyciu **Analizuj pokrycie kodu**.  
  
### <a name="to-customize-run-settings-in-a-command-line-test"></a>Dostosowywanie ustawień uruchamiania w teście wiersza polecenia  
 Aby uruchomić testy z wiersza polecenia, należy użyć narzędzia vstest.console.exe. Plik ustawień jest parametrem tego narzędzia. Aby uzyskać więcej informacji, zobacz [korzystanie z VSTest.console z wiersza polecenia](http://msdn.microsoft.com/library/852812d8-b3bb-407e-bc43-04d511fcb27a).  
  
1. Uruchom wiersz polecenia programisty dla programu Visual Studio:  
  
     Na Windows **Start**, wybierz **wszystkie programy**, **programu Microsoft Visual Studio**, **Visual Studio Tools**, **dla deweloperów Wiersz polecenia**.  
  
2. Uruchom:  
  
     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`  
  
### <a name="to-customize-run-settings-in-a-build-definition"></a>Dostosowywanie ustawień wykonywania w definicji kompilacji  
 Dane pokrycia kodu można uzyskać z kompilacji zespołu.  
  
 ![Określanie runsettings w definicji kompilacji](../test/media/codecoverage-buildrunsettings.png "CodeCoverage buildRunsettings")  
  
1. Upewnij się, że plik .runsettings jest zaewidencjonowany.  
  
2. W programie Team Explorer Otwórz **kompilacje**, a następnie dodaj lub Edytuj definicję kompilacji.  
  
3. Na **procesu** rozwiń **testy automatyczne**, **źródła testów**, **parametrów uruchomieniowych**. Wybierz swoje **.runsettings** pliku.  
  
   - <em>Ale **zestawu testowego</em>* pojawia się zamiast **źródła testów**. Gdy próbuję ustawić **parametrów uruchomieniowych** pola można wybrać tylko pliki .testsettings.*  
  
      W obszarze **testy automatyczne**, wybierz opcję **zestawu testowego**i wybierz polecenie **[...]**  na końcu wiersza. W **Dodaj/Edytuj przebieg testowy** okno dialogowe, zestaw **Test Runner** do **Visual Studio Test Runner**.  
  
   Wyniki są widoczne w sekcji podsumowania raportu kompilacji.  
  
## <a name="sample"></a> Przykładowy plik .runsettings  
 Skopiuj ten kod i dostosuj go do swoich potrzeb. Jest to domyślny plik .runsettings.  
  
 (Do innych celów pliku .runsettings, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).)  
  
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
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.  
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
                <!—Don't forget "Attribute" at the end of the name -->  
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
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z pokrycia kodu, aby określić, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)   
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)
