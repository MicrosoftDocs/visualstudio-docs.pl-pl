---
title: 'Instrukcje: Używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: fd7e091192e0111a9dcf0997af8316daef364adb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252329"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Instrukcje: Użyj kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio

Program Visual Studio umożliwia ładowanie pakietów VSPackage przy pewnych dobrze znanych <xref:Microsoft.VisualStudio.Shell.UIContext>s zostaną aktywowane. Jednak te konteksty interfejsu użytkownika nie są bardziej ziarniste, co pozostawia autorów rozszerzeń bez wyboru, ale do wybierania dostępnego kontekstu interfejsu użytkownika, który jest uaktywniany przed punktem, na który naprawdę chciał pakietu VSPackage. Aby uzyskać listę znanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Ładowanie pakietów może mieć wpływ na wydajność i ładowanie ich wcześniej, niż jest to konieczne, nie jest najlepszym rozwiązaniem. W programie Visual Studio 2015 wprowadzono koncepcję kontekstów interfejsu użytkownika opartych na regułach, mechanizm, który umożliwia autorom rozszerzeń Definiowanie precyzyjnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i są ładowane skojarzone pakietów VSPackage.

## <a name="rule-based-ui-context"></a>Kontekst oparty na regułach interfejsu użytkownika

"Reguła" składa się z nowym kontekście interfejsu użytkownika (GUID), a wyrażenie logiczne, które odwołuje się do co najmniej jeden "Terms" w połączeniu z logiczną "i", "or", "not" operacji. "Warunki" są oceniane dynamicznie w czasie wykonywania, a wyrażenie jest przeszacowana po każdej zmianie jego warunków. Jeśli wyrażenie ma wartość true, jest ono aktywowane skojarzonego kontekstu interfejsu użytkownika. W przeciwnym razie kontekstu interfejsu użytkownika jest wyłączony.

Kontekst interfejsu użytkownika oparty na regułach może być używany na różne sposoby:

1. Określ ograniczeń widoczność dla poleceń i okien narzędzi. Można ukryć polecenia/narzędzi systemu windows, dopóki nie zostanie spełniony reguły kontekstu interfejsu użytkownika.

2. Jako ograniczenia automatyczne ładowania: automatyczne ładowanie pakietów tylko po spełnieniu reguły.

3. Jako zadanie opóźnione: Opóźnij ładowanie do określonego interwału, a reguła jest nadal spełniona.

   Mechanizm, może być używany przez wszystkie rozszerzenia programu Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Tworzenie kontekstu interfejsu użytkownika opartego na regułach
 Załóżmy, że masz rozszerzenie o nazwie TestPackage, które oferuje polecenie menu, które ma zastosowanie tylko do plików z rozszerzeniem *. config* . Przed VS2015, najlepszym rozwiązaniem było załadować TestPackage podczas <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontekstu interfejsu użytkownika został aktywowany. Ładowanie TestPackage w ten sposób nie jest wydajne, ponieważ załadowane rozwiązanie może nie zawierać nawet pliku *. config* . W tych krokach pokazano, jak kontekstu interfejsu użytkownika opartego na regułach można użyć do aktywowania kontekstu interfejsu użytkownika tylko wtedy, gdy wybrano plik z rozszerzeniem *. config* , a następnie Ładuj TestPackage podczas aktywowania kontekstu interfejsu użytkownika.

1. Zdefiniuj nowy identyfikator GUID UIContext i Dodaj do klasy pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Załóżmy na przykład, że zostanie dodany nowy UIContext "UIContextGuid". Utworzony identyfikator GUID (można utworzyć identyfikator GUID, klikając pozycję **Narzędzia** > **Utwórz GUID**) to "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Następnie należy dodać następującą deklarację wewnątrz klasy pakietu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Dla atrybutów Dodaj następujące wartości: (Szczegóły tych atrybutów zostaną wyjaśnione później)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Te metadane określają nowy identyfikator GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) i wyrażenie odnoszące się do pojedynczego termin "DotConfig". Termin "DotConfig" daje w wyniku wartość true, gdy bieżący wybór w aktywnej hierarchii ma nazwę zgodną z wzorcem wyrażenia regularnego\\". config $" (kończy się rozszerzeniem *. config*). Wartość (wartość domyślna) Określa opcjonalną nazwę dla tej reguły, które są przydatne podczas debugowania.

    Wartości atrybutu są dodawane do pkgdef wygenerowane później w czasie kompilacji.

2. W pliku VSCT dla poleceń TestPackage Dodaj flagę "DynamicVisibility" do odpowiednich poleceń:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. W sekcji widoczności VSCT powiązanie odpowiednie polecenia, aby nowe UIContext zdefiniowane w #1 identyfikator GUID:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. W sekcji symbole Dodaj definicję UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Teraz polecenia menu kontekstowego dla  *\*plików. config* będą widoczne tylko wtedy, gdy wybrany element w Eksploratorze rozwiązań jest plikiem *. config* , a pakiet nie zostanie załadowany do momentu wybrania jednego z tych poleceń.

   Następnie użyj debugera, aby potwierdzić, że pakiet ładuje się tylko wtedy, gdy oczekiwano. Aby debugować TestPackage:

5. Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

6. Twórz TestPackage i Rozpocznij debugowanie.

7. Utwórz projekt lub otwórz je.

8. Wybierz dowolny plik z rozszerzeniem innym niż *. config*. Punkt przerwania powinien nie są osiągane.

9. Wybierz plik *App. config* .

   TestPackage ładuje i zatrzymuje się w punkcie przerwania.

## <a name="add-more-rules-for-ui-context"></a>Dodaj więcej reguł dla kontekstu interfejsu użytkownika
 Ponieważ wyrażenia logiczne dostępne są następujące reguły kontekstu interfejsu użytkownika, możesz dodać bardziej ograniczony reguły dla kontekstu interfejsu użytkownika. Na przykład w powyższej kontekstu interfejsu użytkownika, można określić czy reguła dotyczy tylko po załadowaniu rozwiązania z projektem. W ten sposób polecenia nie będą wyświetlane, jeśli otworzysz plik *. config* jako plik autonomiczny, a nie jako część projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Teraz wyrażenie odwołuje się do trzech warunków. Pierwsze dwa warunki "SingleProject" i "MultipleProjects" odnoszą się do innych dobrze znanych kontekstów interfejsu użytkownika (według ich identyfikatorów GUID). Trzeci termin "DotConfig" to kontekst interfejsu użytkownika oparty na regułach zdefiniowany wcześniej w tym artykule.

## <a name="delayed-activation"></a>Opóźniona aktywacja
 Reguły może mieć opcjonalny "opóźnienie". Opóźnienie jest wyrażona w milisekundach. Jeśli jest obecny, opóźnienie powoduje, że aktywacja i dezaktywacja kontekstu interfejsu użytkownika reguła opóźnionych tego przedziału czasu. Jeśli zmiany reguł kopię przed interwał opóźnienia, następnie nic się nie dzieje. Mechanizm ten może służyć do "przesunąć" Inicjowanie kroki — szczególnie jednorazowe inicjowanie bez polegania na czasomierzy lub rejestrowania powiadomień bezczynności.

 Na przykład można określić reguły testu obciążenia ma opóźnienie 100 milisekund:

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

Poniżej przedstawiono różne typy termin, które są obsługiwane:

|Termin|Opis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identyfikator GUID odnosi się do kontekstu interfejsu użytkownika. Termin będzie mieć wartość true, zawsze wtedy, gdy kontekstu interfejsu użytkownika jest aktywna i wartość false w przeciwnym razie.|
|HierSingleSelectionName:\<wzorzec >|Termin będzie mieć wartość true, zawsze wtedy, gdy wybór w aktywnej hierarchii jest pojedynczy element i nazwę wybranego elementu odpowiada wyrażeniu regularnemu .net przez "wzorzec".|
|UserSettingsStoreQuery:\<zapytanie >|"Query" reprezentuje pełną ścieżkę do magazynu ustawień użytkownika, który musi mieć wartość różną od zera. Zapytanie jest dzielony na "collection" i "propertyName" w ostatnim ukośnika.|
|ConfigSettingsStoreQuery:\<zapytanie >|"zapytanie" reprezentuje pełną ścieżkę do magazynu ustawień konfiguracji, który musi mieć wartość różną od zera. Zapytanie jest dzielony na "collection" i "propertyName" w ostatnim ukośnika.|
|ActiveProjectFlavor:\<projectTypeGuid >|Termin będzie znajdował się w każdym przypadku, gdy aktualnie wybranego projektu jest składni (łącznie) i ma wersję, odpowiadał typowi danego projektu identyfikatora GUID.|
|ActiveEditorContentType:\<contentType >|Termin jest wartość true, jeśli wybrany dokument jest edytorem tekstu z danym typem zawartości.|
|ActiveProjectCapability:\<wyrażenia >|Warunek ma wartość true, jeśli aktywne funkcje projektu pasują do podanego wyrażenia. Wyrażenie może być takie samo jak VB &#124; CSharp.|
|SolutionHasProjectCapability:\<wyrażenia >|Podobny do powyższego, ale termin ma wartość true, jeśli rozwiązanie ma załadowanego projektu, który pasuje do wyrażenia.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Termin będzie mieć wartość true, zawsze wtedy, gdy to rozwiązanie ma projektu, który jest składni (łącznie), a wersja odpowiadał typowi danego projektu identyfikatora GUID.|
|ProjectAddedItem:\<wzorzec >| Termin ma wartość true, gdy plik zgodny ze specyfikatorem "wzorzec" zostanie dodany do projektu w otwartym soluion.|
|ActiveProjectOutputType:\<outputType>|Warunek ma wartość true, jeśli typ danych wyjściowych dla aktywnego projektu jest zgodny.  Element OutputType może być liczbą całkowitą lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> typem.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Warunek ma wartość PRAWDA, jeśli aktywny projekt ma określoną właściwość kompilacji i wartość właściwości jest zgodna z podanym filtrem wyrażeń regularnych. Zapoznaj się z [utrwalaniem danych w plikach projektów programu MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) , aby uzyskać więcej szczegółowych informacji na temat właściwości kompilacji.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Termin ma wartość true, jeśli rozwiązanie ma załadowany projekt z określoną właściwością kompilacji i wartością właściwości jest zgodny z podanym filtrem wyrażeń regularnych.|

## <a name="compatibility-with-cross-version-extension"></a>Zgodność z rozszerzeniem między wersjami

Konteksty interfejsu użytkownika oparte na regułach to nowa funkcja w programie Visual Studio 2015 i nie można jej przenieść do wcześniejszych wersji. Nie można przenieść do wcześniejszych wersji tworzy problem z rozszerzeniami/pakietami przeznaczonymi dla wielu wersji programu Visual Studio. Te wersje będą musiały być ładowane do Visual Studio 2013 i wcześniej, ale mogą korzystać z kontekstów interfejsu użytkownika opartych na regułach, aby uniemożliwić ich ładowanie do programu Visual Studio 2015.

W celu obsługi tych pakietów, AutoLoadPackages wpisów rejestru umożliwia teraz flagę w polu jego wartość w taki sposób, aby wskazać, że wpis ma być pomijana w programie Visual Studio 2015 i nowszych. Można to zrobić, dodając flagi opcję <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teraz można dodać pakietów VSPackage **SkipWhenUIContextRulesActive** opcji w celu ich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atrybutu, aby wskazać, zapis mają być ignorowane w programie Visual Studio 2015 i nowszych.
## <a name="extensible-ui-context-rules"></a>Rozszerzalne reguły kontekstu interfejsu użytkownika

Czasami pakietów nie można użyć statycznej reguły kontekstu interfejsu użytkownika. Na przykład załóżmy, że masz pakiet obsługi rozszerzalność w taki sposób, że stan polecenia opiera się na typy edytora, które są obsługiwane przez zaimportowane dostawców MEF. Polecenie jest włączone, jeśli plik ma rozszerzenia obsługi bieżącego typu edycji. W takich przypadkach pakiet nie może korzystać z statycznej reguły kontekstu interfejsu użytkownika, ponieważ terminy zmieniają się w zależności od tego, które rozszerzenia MEF są dostępne.

Aby można było obsługiwać takie pakiety, konteksty interfejsu użytkownika oparte na regułach obsługują wyrażenie stałe "*", które wskazuje, że wszystkie poniższe warunki zostaną dołączone do lub. Dzięki temu pakiet główny może zdefiniować znany kontekst interfejsu użytkownika oparty na regułach i powiązać jego stan poleceń z tym kontekstem. Później każde rozszerzenie MEF, przeznaczony dla pakietu głównego dodać przestrzegania postanowień edytory, obsługiwane bez wpływu na inne postanowienia lub wyrażenie wzorca.

Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentacji przedstawiono składnię rozszerzalnych zasad kontekstu interfejsu użytkownika.
