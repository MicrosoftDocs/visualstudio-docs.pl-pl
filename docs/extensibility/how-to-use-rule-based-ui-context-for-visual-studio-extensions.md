---
title: 'Jak: Używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710592"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Jak: Używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio

Visual Studio umożliwia ładowanie vspackages, <xref:Microsoft.VisualStudio.Shell.UIContext>gdy niektóre dobrze znane s są aktywowane. Jednak te konteksty interfejsu użytkownika nie są drobnoziarniste, co pozostawia autorów rozszerzenia nie ma wyboru, ale wybrać dostępny kontekst interfejsu użytkownika, który aktywuje przed punktem, który naprawdę chciał VSPackage załadować. Aby uzyskać listę dobrze znanych kontekstów <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>interfejsu użytkownika, zobacz .

Ładowanie pakietów może mieć wpływ na wydajność i ładowanie ich wcześniej niż jest to potrzebne nie jest najlepszym rozwiązaniem. Visual Studio 2015 wprowadzono pojęcie kontekstów interfejsu użytkownika opartych na regułach, mechanizm, który umożliwia autorom rozszerzenia do definiowania dokładnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i skojarzone VSPackages są ładowane.

## <a name="rule-based-ui-context"></a>Kontekst interfejsu użytkownika opartego na regułach

"Reguła" składa się z nowego kontekstu interfejsu użytkownika (guid) i wyrażenia logicznego, które odwołuje się do jednego lub więcej "Terms" w połączeniu z logicznymi operacjami "i", "lub", "nie". "Warunki" są oceniane dynamicznie w czasie wykonywania, a wyrażenie jest ponownie oceniane za każdym razem, gdy którykolwiek z jego warunków ulegnie zmianie. Gdy wyrażenie ma wartość true, jest aktywowany skojarzony kontekst interfejsu użytkownika. W przeciwnym razie kontekst interfejsu użytkownika jest deaktywowany.

Kontekst interfejsu użytkownika oparty na regułach może być używany na różne sposoby:

1. Określ ograniczenia widoczności dla poleceń i okien narzędzi. Można ukryć okna poleceń/narzędzi, dopóki nie zostanie spełniona reguła kontekstu interfejsu użytkownika.

2. Jako ograniczenia obciążenia automatycznego: automatyczne ładowanie pakietów tylko wtedy, gdy reguła jest spełniona.

3. Jako zadanie opóźnione: opóźnij ładowanie do upływu określonego interwału, a reguła jest nadal spełniona.

   Mechanizm może być używany przez każde rozszerzenie programu Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Tworzenie kontekstu interfejsu użytkownika opartego na regułach
 Załóżmy, że masz rozszerzenie o nazwie TestPackage, które oferuje polecenie menu, które ma zastosowanie tylko do plików z rozszerzeniem *.config.* Przed VS2015, najlepszym rozwiązaniem było załadować <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> TestPackage po uaktywnieniu kontekstu interfejsu użytkownika. Ładowanie TestPackage w ten sposób nie jest wydajne, ponieważ załadowane rozwiązanie może nawet nie zawierać pliku *.config.* Te kroki pokazują, jak kontekst interfejsu użytkownika oparty na regułach może służyć do aktywowania kontekstu interfejsu użytkownika tylko wtedy, gdy plik z rozszerzeniem *.config* jest zaznaczone i załadować TestPackage, gdy ten kontekst interfejsu użytkownika jest aktywowany.

1. Zdefiniuj nowy identyfikator GUID UIContext <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>i dodaj go do klasy VSPackage oraz .

    Załóżmy na przykład, że nowy UIContext "UIContextGuid" ma zostać dodany. Utworzony identyfikator GUID (można utworzyć identyfikator GUID, klikając **narzędzia** > **Tworzenie GUID)** to "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Następnie należy dodać następującą deklarację wewnątrz klasy pakietu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Dla atrybutów dodaj następujące wartości: (Szczegóły tych atrybutów zostaną wyjaśnione później)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Te metadane definiują nowy identyfikator GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) i wyrażenie odnoszące się do pojedynczego terminu "DotConfig". Termin "DotConfig" jest rozpoznawany jako true, gdy bieżące zaznaczenie w aktywnej\\hierarchii ma nazwę odpowiadającą wzorcowi wyrażenia regularnego " .config$" (kończy się na *.config*). Wartość (domyślna) definiuje opcjonalną nazwę reguły przydatnej do debugowania.

    Wartości atrybutu są dodawane do pkgdef generowane podczas kompilacji później.

2. W pliku VSCT dla poleceń TestPackage dodaj flagę "DynamicVisibility" do odpowiednich poleceń:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. W sekcji Visibilities w vsct, powiązać odpowiednie polecenia do nowego identyfikatora GUID UIContext zdefiniowane w #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. W sekcji Symbole dodaj definicję interfejsu użytkownika:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Teraz polecenia menu kontekstowego * \** dla plików .config będą widoczne tylko wtedy, gdy wybrany element w eksploratorze rozwiązań jest plikiem *.config,* a pakiet nie zostanie załadowany, dopóki nie zostanie wybrane jedno z tych poleceń.

   Następnie użyj debugera, aby potwierdzić, że pakiet ładuje się tylko wtedy, gdy oczekujesz, że. Aby debugować TestPackage:

5. Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> w metodzie.

6. Tworzenie TestPackage i rozpocząć debugowanie.

7. Utwórz projekt lub otwórz go.

8. Wybierz dowolny plik z rozszerzeniem innym niż *.config*. Punkt przerwania nie powinien zostać trafiony.

9. Wybierz plik *App.Config.*

   TestPackage ładuje i zatrzymuje się w punkcie przerwania.

## <a name="add-more-rules-for-ui-context"></a>Dodawanie kolejnych reguł dla kontekstu interfejsu użytkownika
 Ponieważ reguły kontekstu interfejsu użytkownika są wyrażeniami logicznymi, można dodać więcej reguł z ograniczeniami dla kontekstu interfejsu użytkownika. Na przykład w powyższym kontekście interfejsu użytkownika można określić, że reguła ma zastosowanie tylko wtedy, gdy rozwiązanie z projektem jest ładowane. W ten sposób polecenia nie będą wyświetlane, jeśli otworzysz plik *.config* jako plik autonomiczny, a nie jako część projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Teraz wyrażenie odwołuje się do trzech terminów. Pierwsze dwa terminy, "SingleProject" i "MultipleProjects", odnoszą się do innych dobrze znanych kontekstów interfejsu użytkownika (przez ich identyfikatory GUID). Trzeci termin "DotConfig" jest kontekst użytkownika oparty na regułach zdefiniowany wcześniej w tym artykule.

## <a name="delayed-activation"></a>Opóźniona aktywacja
 Reguły mogą mieć opcjonalne "Opóźnienie". Opóźnienie jest określone w milisekundach. Jeśli jest obecny, opóźnienie powoduje, że aktywacja lub dezaktywacja kontekstu interfejsu użytkownika reguły jest opóźniona o ten przedział czasu. Jeśli reguła zmieni się z powrotem przed interwałem opóźnienia, nic się nie dzieje. Mechanizm ten może służyć do "rozłamiania" kroki inicjowania — szczególnie jednorazowe inicjowanie bez polegania na czasomierze lub rejestrowania powiadomień bezczynnych.

 Na przykład można określić regułę obciążenia testowego, aby mieć opóźnienie 100 milisekund:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Typy terminów

Oto różne rodzaje terminów, które są obsługiwane:

|Termin|Opis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnnnnnn}|Identyfikator GUID odnosi się do kontekstu interfejsu użytkownika. Termin będzie true, gdy kontekst interfejsu użytkownika jest aktywny i false w przeciwnym razie.|
|HierSingleSelectionName:\<wzór>|Termin będzie spełniony za każdym razem, gdy zaznaczenie w aktywnej hierarchii jest pojedynczym elementem, a nazwa wybranego elementu jest zgodna z wyrażeniem regularnym .Net podanym przez "wzorzec".|
|UserSettingsStoreQuery:\<> zapytania|"query" reprezentuje pełną ścieżkę do magazynu ustawień użytkownika, który musi być oceniany do wartości niezerowej. Kwerenda jest podzielona na "collection" i "propertyName" w ostatnim ukośniku.|
|ConfigSettingsStoreQuery:\<> zapytania|"query" reprezentuje pełną ścieżkę do magazynu ustawień konfiguracji, który musi być oceniany na wartość niezerową. Kwerenda jest podzielona na "collection" i "propertyName" w ostatnim ukośniku.|
|ActiveProjectFlavor:\<projektTypeGuid>|Termin będzie true, gdy aktualnie wybrany projekt jest aromatyzowane (zagregowane) i ma smak pasujący do danego typu guid projektu.|
|ActiveEditorContentType:\<contentType>|Termin ten będzie spełniony, gdy wybrany dokument jest edytorem tekstu o danym typie zawartości. Uwaga: po zmianie nazwy wybranego dokumentu termin ten nie jest odświeżany, dopóki plik nie zostanie zamknięty i ponownie otwarty.|
|ActiveProjectCapability:\<wyrażenie>|Termin ten jest spełniony, gdy aktywne możliwości projektu są zgodne z podanym wyrażeniem. Wyrażenie może być coś vb &#124; CSharp.|
|SolutionHasProjectCapability:\<wyrażenie>|Podobnie jak powyżej, ale termin jest true, gdy rozwiązanie ma dowolny załadowany projekt, który pasuje do wyrażenia.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Termin będzie true, gdy rozwiązanie ma projekt, który jest aromatyzowane (zagregowane) i ma smak pasujący do danego typu guid projektu.|
|ProjectAddedItem:\<wzór>| Termin jest true, gdy plik pasujący do "wzorca" jest dodawany do projektu w soluion, który jest otwarty.|
|ActiveProjectOutputType:\<outputType>|Termin jest spełniony, gdy typ danych wyjściowych dla aktywnego projektu jest dokładnie zgodny.  Typ danych wyjściowych może być <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> całkowitej liczby lub typu.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Termin jest spełniony, gdy aktywny projekt ma określoną właściwość kompilacji i wartość właściwości pasuje do filtru regularnego pod warunkiem. Aby uzyskać więcej informacji na temat właściwości kompilacji, należy zapoznać się z informacjami dotyczącymi [utrwalania danych w plikach projektu MSBuild.](internals/persisting-data-in-the-msbuild-project-file.md)|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Termin jest spełniony, gdy rozwiązanie ma załadowany projekt z określoną właściwością kompilacji i wartością właściwości pasuje do filtru regularnego pod warunkiem.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatybilność z rozszerzeniem między wersjami

Konteksty interfejsu użytkownika oparte na regułach to nowa funkcja w programie Visual Studio 2015 i nie zostaną przeniesione do wcześniejszych wersji. Nie przenoszenie do wcześniejszych wersji tworzy problem z rozszerzeniami/pakietami, które są przeznaczone dla wielu wersji programu Visual Studio. Te wersje muszą być automatycznie ładowane w programie Visual Studio 2013 i wcześniejszych, ale mogą korzystać z kontekstów interfejsu użytkownika opartych na regułach, aby zapobiec automatycznemu ładowaniu w programie Visual Studio 2015.

Aby obsługiwać takie pakiety, AutoLoadPackages wpisy w rejestrze można teraz podać flagę w polu wartości, aby wskazać, że wpis powinien zostać pominięty w programie Visual Studio 2015 i powyżej. Można to zrobić, dodając opcję <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>flagi do . VSPackages można teraz dodać **SkipWhenUIContextRulesActive** opcji do ich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atrybutu, aby wskazać wpis powinien być ignorowany w programie Visual Studio 2015 i powyżej.
## <a name="extensible-ui-context-rules"></a>Rozszerzalne reguły kontekstu interfejsu użytkownika

Czasami pakiety nie można użyć statycznych reguł kontekstu interfejsu użytkownika. Załóżmy na przykład, że masz pakiet obsługujący rozszerzalność, tak aby stan polecenia był oparty na typach edytora obsługiwanych przez importowanych dostawców MEF. Polecenie jest włączone, jeśli istnieje rozszerzenie obsługujące bieżący typ edycji. W takich przypadkach sam pakiet nie może używać statycznej reguły kontekstu interfejsu użytkownika, ponieważ warunki będą się zmieniać w zależności od dostępnych rozszerzeń MEF.

Aby obsługiwać takie pakiety, konteksty interfejsu użytkownika oparte na regułach obsługują wyrażenie "*", które wskazuje wszystkie poniższe terminy, zostaną połączone z OR. Dzięki temu pakiet główny do definiowania znanego kontekstu interfejsu użytkownika opartego na regułach i powiązanie jego stanu polecenia z tym kontekstem. Następnie każde rozszerzenie MEF przeznaczone dla pakietu głównego można dodać jego warunki dla edytorów, które obsługuje bez wpływu na inne terminy lub wyrażenie główne.

Dokumentacja <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> konstruktora pokazuje składnię rozszerzalne reguły kontekstu interfejsu użytkownika.
