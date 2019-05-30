---
title: 'Instrukcje: Użyj kontekstu oparty na regułach interfejsu użytkownika dla rozszerzenia programu Visual Studio | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: madskristensen
ms.author: madsk
ms.workload:
- vssdk
ms.openlocfilehash: d9136268bf1bfb7ccebf79de035fb19f40223002
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324698"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Instrukcje: Użyj kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio

Program Visual Studio umożliwia ładowanie pakietów VSPackage przy pewnych dobrze znanych <xref:Microsoft.VisualStudio.Shell.UIContext>s zostaną aktywowane. Jednak tych kontekstach interfejsu użytkownika nie są poprawnie szczegółowej, dlatego twórcy rozszerzeń Brak wyboru, ale do wyboru dostępne kontekstu interfejsu użytkownika, który aktywuje przed punktem chcieli naprawdę pakietu VSPackage do załadowania. Aby uzyskać listę znanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.

Ładowanie pakietów może mieć negatywny wpływ na wydajność i szybciej, niż jest to potrzebne podczas ich ładowania nie jest najlepszym rozwiązaniem. Program Visual Studio 2015 wprowadzono pojęcie opartych na regułach kontekstów interfejsu użytkownika, mechanizm, który umożliwia twórcy rozszerzeń zdefiniować dokładne warunki kontekstu interfejsu użytkownika jest aktywowana i skojarzonych pakietach VSPackage są ładowane.

## <a name="rule-based-ui-context"></a>Kontekst oparty na regułach interfejsu użytkownika

"Reguła" składa się z nowym kontekście interfejsu użytkownika (GUID), a wyrażenie logiczne, które odwołuje się do co najmniej jeden "Terms" w połączeniu z logiczną "i", "or", "not" operacji. "Terms" są obliczane dynamicznie w czasie wykonywania, a wyrażenie jest ponownie oceniane zawsze wtedy, gdy jego zmiany warunków. Jeśli wyrażenie ma wartość true, jest ono aktywowane skojarzonego kontekstu interfejsu użytkownika. W przeciwnym razie kontekstu interfejsu użytkownika jest wyłączony.

Oparty na regułach kontekstu interfejsu użytkownika mogą służyć na różne sposoby:

1. Określ ograniczeń widoczność dla poleceń i okien narzędzi. Można ukryć polecenia/narzędzi systemu windows, dopóki nie zostanie spełniony reguły kontekstu interfejsu użytkownika.

2. Jak automatycznie załadować ograniczeń: automatyczne ładowanie pakietów tylko wtedy, gdy reguła jest spełniony.

3. Jako opóźnionego zadania: opóźnienie ładowania, dopóki nie został przekazany w określonych odstępach czasu i reguły nadal jest spełniony.

   Mechanizm, może być używany przez wszystkie rozszerzenia programu Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Utwórz kontekst interfejsu użytkownika opartego na regułach
 Załóżmy, że masz rozszerzenia o nazwie TestPackage, która zapewnia polecenia menu, dotyczy tylko plików za pomocą *.config* rozszerzenia. Przed VS2015, najlepszym rozwiązaniem było załadować TestPackage podczas <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontekstu interfejsu użytkownika został aktywowany. Nie jest efektywne, ładowanie TestPackage w ten sposób, ponieważ załadowanego rozwiązania nie mogą zawierać nawet *.config* pliku. Te kroki pokazują, jak zasady na podstawie kontekstu interfejsu użytkownika może służyć do aktywowania kontekstu interfejsu użytkownika, tylko wtedy, gdy plik z *.config* rozszerzenia jest zaznaczone, a następnie załadować TestPackage, po aktywowaniu tego kontekstu interfejsu użytkownika.

1. Zdefiniuj nowy identyfikator GUID UIContext i Dodaj do klasy pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.

    Na przykład, załóżmy, że nowe UIContext "UIContextGuid" ma zostać dodany. Utworzony identyfikator GUID (identyfikator GUID można utworzyć, klikając **narzędzia** > **Utwórz GUID**) jest "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Następnie należy dodać następującą deklarację wewnątrz klasy pakietu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    W przypadku atrybutów Dodaj następujące wartości: (Szczegółowe informacje o tych atrybutów zostaną wyjaśnione później)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Te metadane określają nowy identyfikator GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) i wyrażenie odnoszące się do pojedynczego termin "DotConfig". Termin "DotConfig" zwraca wartość true, gdy bieżące zaznaczenie w aktywnej hierarchii ma nazwę, która pasuje do wzorca wyrażenia regularnego "\\.config$" (kończy się *.config*). Wartość (wartość domyślna) Określa opcjonalną nazwę dla tej reguły, które są przydatne podczas debugowania.

    Wartości atrybutu są dodawane do pkgdef wygenerowane później w czasie kompilacji.

2. W pliku VSCT TestPackage poleceń Dodaj flagę "DynamicVisibility" do odpowiednich poleceń:

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

    Teraz, polecenia menu kontekstowe dla  *\*.config* pliki będą widoczne tylko wtedy, gdy wybrany element w Eksploratorze rozwiązań jest *.config* pliku i pakietu nie zostanie załadowany do jednego z tych Wybrano poleceń.

   Następnie użyj debugera, aby upewnić się, że pakiet ładuje, tylko jeśli oczekujesz. Aby debugować TestPackage:

5. Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.

6. Twórz TestPackage i Rozpocznij debugowanie.

7. Utwórz projekt lub otwórz je.

8. Wybierz dowolny plik z rozszerzeniem innych niż *.config*. Punkt przerwania powinien nie są osiągane.

9. Wybierz *App.Config* pliku.

   TestPackage ładuje i zatrzymuje się w punkcie przerwania.

## <a name="add-more-rules-for-ui-context"></a>Dodaj więcej reguł dla kontekstu interfejsu użytkownika
 Ponieważ wyrażenia logiczne dostępne są następujące reguły kontekstu interfejsu użytkownika, możesz dodać bardziej ograniczony reguły dla kontekstu interfejsu użytkownika. Na przykład w powyższej kontekstu interfejsu użytkownika, można określić czy reguła dotyczy tylko po załadowaniu rozwiązania z projektem. W ten sposób poleceń będzie pojawiało się Jeśli otworzysz *.config* pliku jako autonomiczny plik, a nie jako część projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Teraz wyrażenie odwołuje się do trzech warunków. Pierwsze dwa warunki "SingleProject" i "MultipleProjects" odnoszą się do innych dobrze znanych kontekstów interfejsu użytkownika (według ich identyfikatorów GUID). Trzeci termin "DotConfig" jest zdefiniowany wcześniej w tym artykule kontekstu interfejsu użytkownika opartego na regułach.

## <a name="delayed-activation"></a>Opóźnionej aktywacji
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

## <a name="term-types"></a>Określenie typów

Poniżej przedstawiono różne typy termin, które są obsługiwane:

|Termin|Opis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identyfikator GUID odnosi się do kontekstu interfejsu użytkownika. Termin będzie mieć wartość true, zawsze wtedy, gdy kontekstu interfejsu użytkownika jest aktywna i wartość false w przeciwnym razie.|
|HierSingleSelectionName:\<wzorzec >|Termin będzie mieć wartość true, zawsze wtedy, gdy wybór w aktywnej hierarchii jest pojedynczy element i nazwę wybranego elementu odpowiada wyrażeniu regularnemu .net przez "wzorzec".|
|UserSettingsStoreQuery:\<zapytanie >|"zapytanie" reprezentuje pełną ścieżkę w magazynie ustawień użytkownika, który musi zwrócić wartość różna od zera. Zapytanie jest dzielony na "collection" i "propertyName" w ostatnim ukośnika.|
|ConfigSettingsStoreQuery:\<zapytanie >|"zapytanie" reprezentuje pełną ścieżkę w magazynie ustawień konfiguracji, który musi zwrócić wartość różna od zera. Zapytanie jest dzielony na "collection" i "propertyName" w ostatnim ukośnika.|
|ActiveProjectFlavor:\<projectTypeGuid >|Termin będzie znajdował się w każdym przypadku, gdy aktualnie wybranego projektu jest składni (łącznie) i ma wersję, odpowiadał typowi danego projektu identyfikatora GUID.|
|ActiveEditorContentType:\<contentType >|Termin jest wartość true, jeśli wybrany dokument jest edytorem tekstu z danym typem zawartości.|
|ActiveProjectCapability:\<wyrażenia >|Wyrażenie ma wartość true, gdy możliwości projektów aktywnej pasują do podanego wyrażenia. Wyrażenie może być podobny do VB &#124; CSharp.|
|SolutionHasProjectCapability:\<wyrażenia >|Podobny do powyższego, ale termin ma wartość true, jeśli rozwiązanie ma załadowanego projektu, który pasuje do wyrażenia.|
|SolutionHasProjectFlavor:\<projectTypeGuid >|Termin będzie mieć wartość true, zawsze wtedy, gdy to rozwiązanie ma projektu, który jest składni (łącznie), a wersja odpowiadał typowi danego projektu identyfikatora GUID.|

## <a name="compatibility-with-cross-version-extension"></a>Zgodność z rozszerzeniem między wersjami

Konteksty interfejsu użytkownika opartego na regułach to nowa funkcja w programie Visual Studio 2015 i nie będzie można przenieść do wcześniejszych wersji. Nie przenoszenie do wcześniejszych wersji tworzy problem z rozszerzeń/pakietów przeznaczonych dla wielu wersji programu Visual Studio. Te wersje musiały być ładowane automatycznie w programie Visual Studio 2013 i starszych, ale może być korzystne oparty na regułach kontekstów interfejsu użytkownika, aby zapobiec auto ładowany w programie Visual Studio 2015.

W celu obsługi tych pakietów, AutoLoadPackages wpisów rejestru umożliwia teraz flagę w polu jego wartość w taki sposób, aby wskazać, że wpis ma być pomijana w programie Visual Studio 2015 i nowszych. Można to zrobić, dodając flagi opcję <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teraz można dodać pakietów VSPackage **SkipWhenUIContextRulesActive** opcji w celu ich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atrybutu, aby wskazać, zapis mają być ignorowane w programie Visual Studio 2015 i nowszych.
## <a name="extensible-ui-context-rules"></a>Rozszerzalne reguły kontekstu interfejsu użytkownika

Czasami pakietów nie można użyć statycznej reguły kontekstu interfejsu użytkownika. Na przykład załóżmy, że masz pakiet obsługi rozszerzalność w taki sposób, że stan polecenia opiera się na typy edytora, które są obsługiwane przez zaimportowane dostawców MEF. Polecenie jest włączone, jeśli plik ma rozszerzenia obsługi bieżącego typu edycji. W takich przypadkach pakietu nie można użyć statycznej regułę kontekstu interfejsu użytkownika, ponieważ warunki zmieniłby się w zależności od MEF, które są dostępne rozszerzenia.

W celu obsługi tych pakietów, oparty na regułach kontekstów interfejsu użytkownika obsługują wyrażenia zapisane na stałe "*" oznacza wszystkie poniższe warunki zostaną dołączone za pomocą lub. Dzięki temu główny pakietu Definiowanie znanych kontekstu interfejsu użytkownika opartego na regułach i powiązanie stanu polecenia dla tego kontekstu. Później każde rozszerzenie MEF, przeznaczony dla pakietu głównego dodać przestrzegania postanowień edytory, obsługiwane bez wpływu na inne postanowienia lub wyrażenie wzorca.

Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentacji przedstawiono składnię rozszerzalnych zasad kontekstu interfejsu użytkownika.
